# FStopPizza Calculator — PWA

Installable Progressive Web App version of the FStopPizza dough & pizza calculator.

## Files
- `index.html` — the app (slimmed from the original single-file build; inline logo replaced with icon refs)
- `manifest.webmanifest` — install metadata (name, icons, standalone display)
- `sw.js` — service worker (offline caching of the app shell)
- `icons/` — app icons (152–512 px + maskable)

## Important: PWAs need to be served over HTTPS
The service worker and "Add to Home Screen → standalone app" behavior only work
from `https://` (or `http://localhost` during development). Opening `index.html`
directly from the filesystem (`file://`) will **not** register the service worker.

### Local test
```bash
cd pwa
python3 -m http.server 8000
# then open http://localhost:8000 in a browser
```

### Hosting (free options)
Drop this folder onto any static host that serves over HTTPS:
- GitHub Pages, Netlify, Cloudflare Pages, or Vercel — just upload the `pwa/` contents.

## Install on iPhone
1. Open the hosted `https://…` URL in **Safari** (iOS only installs PWAs from Safari).
2. Tap the **Share** button → **Add to Home Screen**.
3. It launches full-screen with its own icon, no Safari chrome — like a native app.
4. After the first online load, the service worker caches the app so it also works offline.

## Updating
Bump the `CACHE` version string in `sw.js` (e.g. `fstoppizza-v1` → `v2`) whenever you
change the app, so clients fetch the new files instead of the cached ones.
