# Five websites, built by Claude Opus 5

Five fictional brand websites, each designed and built end to end: brand, copy, layout, interaction and code. The last two model their products in 3D in the browser.

| # | Site | Folder | What makes it different |
|---|------|--------|--------------------------|
| 01 | Morrow Salt Works | `morrow-salt-works/` | Layered photo hero, live tide clock, scroll floods and drains the salt pans |
| 02 | Nightjar Sleeper Co. | `nightjar-sleeper/` | Split-flap departures board, canvas train window that stops at every station |
| 03 | Overprint | `overprint/` | Whole site reprints in any two of twelve risograph inks, scroll-driven print run |
| 04 | Verre 50/1.2 | `verre-50-12/` | 3D camera lens that separates into ten glass elements and traces light |
| 05 | Fieldnote K65 | `fieldnote-k65/` | 3D keyboard you can type on, comes apart into seven layers |

## Running locally

No build step and no dependencies. Serve the folder with any static server:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Opening the HTML files directly with `file://` also works, apart from the web fonts.

## Structure

```
.
├── index.html              # hub page linking to all five
├── <site>/index.html       # one self-contained page per site
└── <site>/images/          # photography for that site
```

Each site is a single HTML file with its CSS and JavaScript inline. The only external requests are Google Fonts and, for sites 04 and 05, three.js r128 from cdnjs.

## Deploying to Vercel

**Five separate URLs (recommended).** Create one Vercel project per site from this repo. In each project, set **Settings → General → Root Directory** to that site's folder (for example `overprint`), leave the framework as **Other**, and leave the build and output settings empty. Each project then deploys only its own folder on every push.

**One URL.** Import the repo once with the root directory left as `/`. The hub page is served at `/` and each site at `/<folder>/`.

## Editing

- The banner across the top of each site reads its values from `const GEN = {...}` near the start of that page's script. Change the model name, cost and time there, or delete the `.genbar` block to remove it.
- Photography lives in `<site>/images/`. Filenames are referenced from the `IMAGES` object (sites 01 to 05) near the start of each script.

## Notes

- Every site supports light and dark system themes, reduced motion, keyboard navigation and screen readers.
- Sites 04 and 05 need WebGL. They fall back to a static diagram or plain page if it is unavailable.
- All five companies, products, prices and people are invented.
