# Smart C Lab website

**Live site:** https://smartclab.netlify.app/

The public website for **Smart C Lab**, a student research lab in Nashville, TN working on drone and UAV security, wireless protocol analysis, zero trust architecture, AI defense, and cybersecurity education.

Designed by Tioluwanimofe Adesanya (Lead Researcher, UAV Security & Cyber Education).

## What's on the site

| Page | Path | What it covers |
| --- | --- | --- |
| Home | `/` | The lab's four research tracks ("Four fronts, one core") and an interactive research-journey timeline |
| Research | `/research` | Wireless vulnerabilities, AI security, zero trust (ZTA), and cybersecurity education, plus the starting reading list |
| Projects | `/projects` | Current and upcoming work: wireless protocol interception, firmware and sensor vulnerabilities, AI-based intrusion detection, smart cities and UAV interaction, student lab exercises, the weekly paper pipeline |
| Team | `/team` | Principal investigator, faculty mentor, researchers, and open undergraduate roles |
| Contact | `/contact` | How to reach the lab and how undergraduates can join |

It also links out to related efforts ([SmartSEAT](https://smartseat.org/), [CyberDataCon](https://cyberdatacon.com/)) and the lab's GitHub organization. The site has a light/dark theme toggle.

## What's in this repo

This is the **compiled, ready-to-deploy build** of the site (a React single-page app), exported from the Runable site builder. The editable source code is not included.

```
index.html            entry page
assets/               bundled JavaScript and CSS
favicon*, apple-touch-icon.png, logo-mark.png
runable.js            Runable's page-view analytics script
```

To change the content, edit the site in the builder and export a new build into this repo, or ask for the original source.

## Run it locally

Any static file server works. Serve from the repo root so the absolute `/assets/...` paths resolve:

```bash
npx serve -s .
# or
python3 -m http.server 8000
```

`npx serve -s` also sends every route back to `index.html`, so `/team` and the other pages work on refresh. With the Python server, start at `/` and navigate from there.

## Deploy

Drop the folder on any static host. Because it's a single-page app, configure the host to rewrite unknown paths to `index.html`:

- **Netlify:** this is how the live site at [smartclab.netlify.app](https://smartclab.netlify.app/) is hosted. For a new deploy, add a `_redirects` file containing `/*  /index.html  200`
- **Vercel:** add a rewrite from `/(.*)` to `/index.html`
- **GitHub Pages:** works at a custom domain or `<user>.github.io` root; copy `index.html` to `404.html` so deep links load

## Notes

- `runable.js` sends page-view events to Runable's analytics collector. Delete the `<script src="/runable.js">` line in `index.html` if you don't want that.
- The contact email in the build is a placeholder (`smartclab@university.edu`); swap in the real address before going live.
- The asset filenames were renamed to match the casing `index.html` uses, so the site loads on case-sensitive hosts (Linux, GitHub Pages, Netlify).
