# ASL Flashcards

Flip cards with an English word on one side and an ASL sign video on the other. The sign videos come from [ASL Signbank](https://aslsignbank.com).

## Adding a sign (no downloading)

Videos stream straight from ASL Signbank. Each card only needs the word, the Signbank entry link, and the sign's **gloss** (its label on Signbank, like `THINK`). The app works out the video address from those:

```
.../dictionary/protected_media/glossvideo/ASL/TH/THINK-398.mp4
                                              ^^ ^^^^^ ^^^
                        first 2 letters of gloss, gloss, entry number
```

**In the app:** click **Deck**, type the word, and paste either:
- the entry page link (`.../dictionary/gloss/398.html`) plus the gloss, or
- the video address itself. On Signbank, right-click the video and choose **Copy video address**. The app gets the gloss and entry from that, so you don't need to type the gloss.

Cards added in the app are saved only in that browser. To make them permanent on your GitHub site, click **Export deck** and commit the downloaded file as `deck.json`:

```json
[
  { "word": "think", "gloss": "THINK",
    "entry": "https://aslsignbank.haskins.yale.edu/dictionary/gloss/398.html" }
]
```

If a video won't load, the app also tries Signbank's other domain (`aslsignbank.com`). If that fails too, the card shows a link to the entry page. To use your own clip in place of Signbank's, add `"video": "videos/think.mp4"` to that card.

The app looks for cards in this order: cards you edited in the browser, then `deck.json`, then the starter deck built into `index.html`.

## Hosting on GitHub Pages

1. Create a repo and push `index.html` (and `deck.json` once you have one).
2. In the repo, go to **Settings → Pages**, set the source to **Deploy from a branch**, and choose `main` and `/ (root)`.
3. Your site will be live at `https://<username>.github.io/<repo>/`.

**Testing locally:** run `python3 -m http.server` in this folder and open `http://localhost:8000`. If you double-click `index.html` instead, the app can't read `deck.json` and falls back to the starter deck.

## Studying

- **Word → Sign:** you see the word, recall the sign, then flip to check.
- **Sign → Word:** you watch the sign and name the word.
- **Again / Got it:** "Again" puts the card back a few cards later. Each "Got it" moves the card up a level. After 4 in a row it counts as mastered.
- **Weak only:** skips mastered cards.
- **0.5× / 0.75×:** slow motion, which helps for catching handshape changes.
- **Keyboard:** `Space` flips, `1` is again, `2` is got it, `S` toggles slow-mo.

Your progress is saved in your browser.

## License and credit

ASL Signbank shares its videos under CC BY-NC-SA 4.0. Their conditions are that you:
- credit ASL Signbank (the app's footer already does this),
- link to each video's Signbank entry (each card links to its entry), and
- use them non-commercially.

> Hochgesang, J. A., Crasborn, O., & Lillo-Martin, D. (2017–2026). *ASL Signbank*. https://aslsignbank.com. https://doi.org/10.6084/m9.figshare.9741788
