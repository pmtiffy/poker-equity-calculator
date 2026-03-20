# Poker Equity Calculator

Single-file Texas Hold'em equity calculator. Open `index.html` and it works — no install, no build step, no internet required.

[**Live demo**](https://pmtiffy.github.io/poker-equity-calculator/)

---

## Features

- **2–9 players** with per-player equity badges on the felt
- **Exact enumeration** post-flop for all player counts; Monte Carlo preflop (50k–100k samples)
- Outs with precise turn/river hit probabilities, multiway-aware
- Hand strength breakdown — highlights which 5 cards form your best hand
- Pot odds calculator
- 13×13 hand range matrix with position presets and clipboard export
- Odds & matchup reference table
- Undo (Ctrl+Z), random deal, interactive tutorial
- EN / 繁中 / 日本語 / 한국어, dark/light theme

---

## Usage

```bash
open index.html
# or serve locally
npx serve .
```

---

## Deployment

**GitHub Pages** — push the repo, go to Settings → Pages, pick `main / (root)`. Done in 60 seconds.

**Netlify** — drag `index.html` to [app.netlify.com/drop](https://app.netlify.com/drop).

**Embed**

```html
<iframe
  src="https://your-domain.com/poker-equity-calculator.html?theme=dark&lang=auto"
  width="100%" height="800"
  style="border:none;border-radius:12px"
  loading="lazy"
></iframe>
```

URL params: `theme=dark|light`, `lang=en|zh|ja|ko|auto`

---

## Equity calculation

Cards are integers 0–51. `rank = card >> 2`, `suit = card & 3`. Hand strength collapses to one integer for O(1) comparison.

| Street | Method |
|--------|--------|
| River | Direct comparison |
| Turn | Full deck enumeration |
| Flop | Exhaustive C(n,2) — max 1,128 combos, exact for all player counts |
| Preflop | Monte Carlo — 50k (HU), 100k (3+) |

Preflop reference values are from PokerStove/Equilab.

---

## License

MIT
