# Axis — marketing site

One dependency-free static page: a short landing page with the privacy policy
as its final section. No build step, no framework. Open `index.html` in a
browser to preview it.

## Contents

- `index.html` — the whole site. The privacy policy is the last section,
  anchored at `#privacy`; the nav and footer links scroll to it.
- `privacy.html` — a redirect stub to `index.html#privacy`, so the site still
  has a clean `/privacy.html` URL. It holds no policy text of its own, so the
  two can never disagree.
- `styles.css` — shared palette, type, and layout.

Fonts come from Google Fonts; every other asset (logo, icons, favicon) is
inline SVG, so the folder is self-contained.

## Deploying

Any static host works. For GitHub Pages, from the repo this folder ends up in:

    Settings → Pages → Source: "Deploy from a branch"
    Branch: main   Folder: /web        (or move index.html to the repo root)

## Using it for App Store Connect

Two required fields are satisfied by this page:

- **Privacy Policy URL** → `https://<your-domain>/privacy.html`
  (or `https://<your-domain>/#privacy` — both land on the policy)
- **Support URL** → `https://<your-domain>/`

Apple requires the policy to be visible when that URL loads. That is why it is
a real section on the page and not a modal or an accordion — anything that
needs a click to reveal the policy is a rejection.

## Keeping it honest

The policy text mirrors `src/screens/PrivacyPolicyScreen.tsx` in the app, with
three web-only additions (data security, children, changes to this policy).
App Review compares the two — when one changes, change the other.
