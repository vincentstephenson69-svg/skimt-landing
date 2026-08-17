# skimt.app landing page — deploy guide (23 Jul 2026)

One self-contained file: `index.html` (~430 KB — real UI screenshots embedded, no other assets, no build step).

## 1. Wire the waitlist (2 min — do this first)
1. Sign up free at **formspree.io** → New form → name it "skimt waitlist".
2. Copy the form ID (looks like `mqkrzvab`).
3. In `index.html`, replace **both** occurrences of `YOUR_FORM_ID` with it.
Submissions land in your Formspree dashboard + email. (Free tier: 50/month — fine for now; export to CSV anytime.)

## 2. Deploy on Render (free static site)
1. Put `index.html` in a new GitHub repo (e.g. `skimt-landing`) — or a `web-landing/` repo of its own; root of the repo is fine.
2. Render dashboard → **New → Static Site** → connect the repo.
3. Build command: *(leave empty)* · Publish directory: `.`
4. Deploy — you'll get `something.onrender.com`. Check it.

## 3. Point skimt.app at it (Porkbun DNS)
1. Render → your static site → **Settings → Custom Domains → Add** `skimt.app` (and `www.skimt.app`).
2. Render shows the DNS targets. At Porkbun → skimt.app → DNS:
   - **ALIAS/ANAME** record, host blank (apex), answer = the `onrender.com` hostname Render gives you.
   - **CNAME** record, host `www`, answer = same hostname.
3. Wait for DNS (minutes–an hour). Render auto-issues TLS — required for .app, automatic here.

## 4. Later, when the pilot goes public on the same domain
The giver links (`skimt.app/g/…`) will eventually need the apex pointed at the *app* service instead, with the landing page served by it or moved to `www`. Zero urgency — decide at launch. (`GIVER_LINK_BASE_URL` stays whatever you set it to.)

## Notes
- Screenshots are the REAL product (web pilot) with the skimt wordmark applied, seeded with demo data ("Alex Marsh") — regenerable anytime from a session; ask and I'll reshoot after UI changes.
- Copy follows `Design/Piper_Marketing_Starter.md` §2–3: locked hero verbatim, approved support lines, banned phrases avoided. Price shown as "£2.99 a month at launch".
- Footer Privacy/Terms/Giver-FAQ links are placeholders (`#`) — they go live with launch materials.
- The three tier one-liners (Teamworker/Manager/Leader) are new copy written for this page — flag if you want them changed.
