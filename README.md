# Barba prev / next transition

Four static pages in a loop. PREV and NEXT slide between them without a full reload.

Live: https://noowxela.github.io/barba_trasition_prenext/

## Pages

| Page | Title | Prev | Next |
| --- | --- | --- | --- |
| `index.html` | This is a title. | `4.html` | `2.html` |
| `2.html` | Flowers, Why not? | `index.html` | `3.html` |
| `3.html` | The sky. | `2.html` | `4.html` |
| `4.html` | ROAD + ICE | `3.html` | `index.html` |

Each page is a cover image (`images/1.jpg`–`4.jpg`) plus the same placeholder text. PREV sits on the left, NEXT on the right.

## How the transition works

**Barba.js** (`barba.js`, v1.0.0) intercepts the PREV / NEXT click, fetches the next HTML, and swaps only `.barba-container`. The address bar updates. The two buttons stay, because they sit outside that container. `nextprev.js` then rewrites their `href` from the new container’s `data-prev` and `data-next`.

**GSAP** (`TweenMax` 1.18.1, from the CDN) only draws the motion: scroll back to the top, then slide. Forward comes in from the right. Backward comes in from the left. Direction is decided by comparing the new filename with the old container’s `data-prev`.

GSAP cannot load another HTML file. A tween dies as soon as the browser navigates. Barba keeps both containers in the page for the 0.6s slide.

## Run locally

Open it through a local server. `file://` makes Barba’s page request fail.

```bash
python3 -m http.server 8080
```

Then open http://localhost:8080.
