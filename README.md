# radiantrtapp-site

Static site for Radiant RT. Hosts:

- `/` — marketing landing (`index.html`)
- `/privacy-policy.html` — privacy policy
- `/terms-of-use.html` — terms of use
- `/support.html` — support + FAQ
- `/delete-account.html` — account deletion instructions (required by Google Play Data Safety)

## Hosting on GitHub Pages

1. Create a new **public** repository on GitHub (e.g., `radiantrtapp-site`).
2. Push this folder:
   ```bash
   git init
   git add .
   git commit -m "feat: initial site (privacy, terms, support, marketing)"
   git branch -M main
   git remote add origin https://github.com/<YOUR-USERNAME>/radiantrtapp-site.git
   git push -u origin main
   ```
3. On GitHub: repo → **Settings** → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/ (root)` → **Save**.
4. Pages will publish at `https://<YOUR-USERNAME>.github.io/radiantrtapp-site/` within ~1 minute.

## URLs to use in App Store Connect / Play Console

Temporary (while on github.io):

| Store field | URL |
|---|---|
| Privacy Policy URL | `https://<YOUR-USERNAME>.github.io/radiantrtapp-site/privacy-policy.html` |
| Support URL | `https://<YOUR-USERNAME>.github.io/radiantrtapp-site/support.html` |
| Marketing URL | `https://<YOUR-USERNAME>.github.io/radiantrtapp-site/` |

Later (after pointing `radiantrtapp.com` at GitHub Pages):

| Store field | URL |
|---|---|
| Privacy Policy URL | `https://radiantrtapp.com/privacy-policy.html` |
| Support URL | `https://radiantrtapp.com/support.html` |
| Marketing URL | `https://radiantrtapp.com/` |

You can update the URLs in App Store Connect anytime — they're metadata, no new binary required.

## Custom domain (do this whenever you're ready)

1. Create a `CNAME` file in this repo with one line:
   ```
   radiantrtapp.com
   ```
2. At your domain registrar, create a CNAME record for `radiantrtapp.com` (or `www`) pointing to `<YOUR-USERNAME>.github.io`.
3. GitHub Pages → Settings → Pages → **Custom domain** → enter `radiantrtapp.com` → **Enforce HTTPS** after the certificate provisions (~1 hour).

## Keeping the files in sync with the app

The source of truth for legal copy lives in the mobile app repo:
- `.radiant-docs/launch/legal/privacy-policy.html`
- `.radiant-docs/launch/legal/terms-of-use.html`
- `.radiant-docs/launch/support-pages/index.html`
- `.radiant-docs/launch/support-pages/support.html`

When those change, copy them here and push. Also update `src/constants/legal-content.ts` in the app if user‑facing legal text changes materially, and bump the disclaimer acceptance key (`V1` → `V2`) so returning users re‑accept.
