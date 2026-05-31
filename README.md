# Tab Swift Hub

**A clean new-tab dashboard for your browser tabs.**

Tab Swift Hub replaces your new tab page with a smart dashboard that groups all open tabs by domain — with a bento-style card layout, custom groups, save-for-later, and satisfying close animations.

No server. No account. No external API calls. Pure Chrome extension.

---

## Features

- **Bento/masonry layout** — card heights adapt to content instead of fixed row heights, giving a natural staggered grid
- **Custom group rules** — merge subdomains or split domains by URL path into separate cards, configured in `config.local.js`
- **Personal config** (`config.local.js`, gitignored) — define your own landing page patterns with exact hostname or `hostnameEndsWith` wildcard matching, without touching committed code
- **Environment color labels** — tabs on Kuaishou domains get a colored left border: green for staging, brown for prt, red for production, so you can tell environments apart at a glance

- **Homepages group** — pulls Gmail, X, YouTube, LinkedIn, GitHub homepages into one card
- **Close with style** — swoosh sound + confetti burst on close
- **Duplicate detection** — flags duplicate tabs with one-click cleanup
- **Click any tab to jump to it** — works across windows, no extra tab opened
- **Save for later** — bookmark tabs to a checklist before closing them
- **Localhost grouping** — shows port numbers so you can tell your dev projects apart
- **Expandable groups** — shows first 8 tabs with a "+N more" toggle
- **100% local** — your data never leaves your machine

---

## Install

**1. Clone the repo**

```bash
git clone <your-repo-url>
cd tab-swift-hub
```

**2. Load the Chrome extension**

1. Go to `chrome://extensions` in Chrome
2. Enable **Developer mode** (top-right toggle)
3. Click **Load unpacked**
4. Select the `extension/` folder inside the cloned repo

**3. Open a new tab**

Tab Swift Hub will appear as your new tab page.

---

## Personal Config

To customize landing page patterns or group rules without committing them, create `extension/config.local.js`:

```js
// extension/config.local.js  (gitignored)
const LOCAL_LANDING_PAGE_PATTERNS = [
  // add your own patterns here
];
```

This file is optional — if it doesn't exist, sensible defaults apply.

---

## How it works

```
You open a new tab
  -> Tab Swift Hub queries all open tabs via chrome.tabs API
  -> Groups them by domain (custom rules applied first)
  -> Homepages get their own group at the top
  -> Click any tab title to switch to it
  -> Close groups you're done with (swoosh + confetti)
  -> Save tabs for later before closing
```

Saved tabs are stored in `chrome.storage.local` and persist across sessions.

---

## Tech Stack

| What | How |
|------|-----|
| Extension | Chrome Manifest V3 |
| Storage | chrome.storage.local |
| Sound | Web Audio API (synthesized, no audio files) |
| Animations | CSS transitions + JS confetti |
| Fonts | Newsreader + DM Sans (Google Fonts) |

---

## Update

```bash
git pull
```

Then go to `chrome://extensions` and click the reload icon on Tab Swift Hub.

---

## License

MIT — see [LICENSE](LICENSE).

> This project is derived from [Tab Out](https://github.com/zarazhangrui/tab-out), used under the MIT License.
