# UPS Store Team Tools — Box Finder (PWA)

An installable, offline-capable web app for The UPS Store, Belgrade MT. Hosting it
on GitHub Pages gives you a real `https://` link, so saving settings on the phone
works, installs behave like a native app, and you can update it without AirDropping.

## What's in this folder (upload ALL of these)

| File | Purpose |
|------|---------|
| `index.html` | The app itself (Box Finder + Settings). **This is the home page.** |
| `manifest.json` | Tells the phone the app's name, colors, and icons. |
| `sw.js` | Service worker — makes the app work offline once loaded. |
| `icon-192.png`, `icon-512.png` | App icons (Android / install prompt). |
| `icon-180.png` | Home-screen icon for iPhone/iPad. |
| `README.md` | This file (optional to upload). |

> You can ignore/skip `box-finder.html` and the planning files (`*.md`, `*.csv`,
> `*.pdf`) — they aren't needed for the app to run.

---

## Option A — Upload through the GitHub website (no software to install)

**1. Make a free GitHub account**
Go to <https://github.com> and sign up (skip if you already have one).

**2. Create a new repository**
- Click the **+** (top right) → **New repository**.
- **Repository name:** `ups-team-tools` (or anything you like).
- Set it to **Public** (required for free GitHub Pages — see the privacy note below).
- Leave everything else as-is and click **Create repository**.

**3. Upload the files**
- On the new repo page, click **uploading an existing file** (the link in the
  "Quick setup" box), or go to **Add file → Upload files**.
- Drag in: `index.html`, `manifest.json`, `sw.js`, `icon-180.png`,
  `icon-192.png`, `icon-512.png`.
- Click **Commit changes**.

**4. Turn on GitHub Pages**
- In the repo, go to **Settings** (top tab) → **Pages** (left sidebar).
- Under **Build and deployment → Source**, choose **Deploy from a branch**.
- **Branch:** `main`, **Folder:** `/ (root)`. Click **Save**.
- Wait ~1 minute. The page will show your live link:
  `https://YOUR-USERNAME.github.io/ups-team-tools/`

That link is your app. Open it in any browser.

---

## Option B — Command line (if you use Git)

```bash
cd "UPS Store App"
git init
git add index.html manifest.json sw.js icon-180.png icon-192.png icon-512.png
git commit -m "UPS Store Team Tools PWA"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/ups-team-tools.git
git push -u origin main
```
Then enable Pages as in **Option A, step 4**.

---

## Install it on your iPhone / iPad

1. Open the GitHub Pages link in **Safari**.
2. Tap the **Share** button (the square with the up-arrow).
3. Tap **Add to Home Screen** → **Add**.
4. Launch it from the new icon — it runs full-screen like an app and works offline.

(On Android, open the link in Chrome and tap **Install app** / **Add to Home screen**.)

---

## Updating the app later

When you have a new version of `index.html` (or icons):

1. In the repo, click the file → the **pencil** (Edit) → paste the new contents →
   **Commit**. (Or use **Add file → Upload files** to replace icons.)
2. **Important:** open `sw.js`, change the version line near the top —
   `const CACHE = 'ups-team-tools-v1';` → `...-v2`, then commit. This makes
   already-installed phones pick up the new version on next open.
3. On the phone, open the app while online once; it will refresh.

---

## Privacy note

A **public** GitHub repo means anyone who knows (or guesses) the URL can view the
files — including your box list and packing prices. For an internal tool that's
usually fine, and the URL isn't advertised anywhere. If you'd rather keep pricing
private, ask and I'll point you to a free private option (e.g. Cloudflare Pages or
Netlify with access protection).

---

## Notes

- The app stores your settings (inventory, packing prices, cushions) **on each
  device** in the browser. Use **Settings → Export Backup** to copy them to
  another phone via **Import Backup**.
- It works offline after the first load, thanks to the service worker.
