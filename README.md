# Monexa

**Clarity for every dollar.**

Monexa is a free, private, no-signup personal finance dashboard. Track income and spending, plan with proven budgeting models, set savings goals, and project long-term growth, all in your browser. There is no backend and no account. Your data stays on your device.

Created and engineered by **Sumit Rajbanshi**.

---

## Features

**Ledger**
- Add, edit, delete and search transactions across income and expense categories
- Month selector with an "All time" view
- CSV export of the filtered view
- Investments count as saving, not spending

**Budget models**
- 50/30/20, Pay Yourself First, 60/20/20, Zero-Based and Custom splits
- Budget vs actual for the selected month, with side-by-side comparison

**Goals**
- Savings goals with progress bars and optional target dates
- Shows the monthly amount needed to hit each target

**Projections**
- Compound growth simulator with initial capital, monthly contributions, return rate and years
- Inflation-adjusted value ("today's dollars") and low / base / high scenarios (±3%)

**Safety and data**
- Goals and transactions are locked by default; deleting or editing needs an unlock code
- JSON backup and restore (validated and sanitised on import)
- User text is HTML-escaped, and CSV exports guard against formula injection

**Experience**
- Fully responsive: fluid root font size, rem-based sizing, touch-friendly controls, safe-area support
- Fast: deferred scripts, batched renders, in-place chart updates, reduced-motion support

## Project structure

```
.
├── index.html   # Landing page (hero, features, live 50/30/20 widget, frameworks)
├── app.html     # Dashboard (Overview, Ledger, Budget Models, Goals, Projections)
└── README.md
```

## Tech stack

- HTML5 and vanilla JavaScript (no build step)
- [Tailwind CSS](https://tailwindcss.com/) via CDN
- [Chart.js](https://www.chartjs.org/) 4.4.1
- [Lucide](https://lucide.dev/) icons
- Plus Jakarta Sans (Google Fonts)
- `localStorage` for persistence (key: `monexa_v1`; older `tallyra_v1`, `finora_v1` and `aurawealth_v1` data is migrated automatically)

## Getting started

Clone the repo and open the landing page. No install is needed.

```bash
git clone https://github.com/<your-username>/monexa.git
cd monexa
open index.html        # macOS; on Linux use xdg-open, on Windows use start
```

An internet connection is required on first load, because Tailwind, Chart.js, Lucide and the font load from CDNs.

To serve it locally instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Push the files to a GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

Any static host works too, such as Netlify, Vercel or Cloudflare Pages.

## Configuration

- **Unlock code:** set by the `LOCK_CODE` constant in `app.html`. Change it before you deploy.
- **Currency:** AUD is set in the labels and in `formatAUD()` in `app.html`. Change the locale and currency symbol there for other regions.
- **Categories and budget buckets:** edit `CATEGORIES`, `BUCKET` and `MODELS` in `app.html`.

## Privacy

Monexa makes no network requests with your financial data. Everything is stored in your browser's `localStorage`. Clearing site data erases it, so use **Export Backup (JSON)** regularly.

## Known limitations

- The unlock code is client-side, so it prevents accidental changes, not determined access. Anyone with access to the browser or page source can read it.
- Tailwind runs from its CDN script, which compiles styles in the browser. For production, consider the Tailwind CLI.
- Data is per browser and per device. There is no sync.
- Projections are illustrative, based on constant rates, and ignore tax and fees.

## Roadmap ideas

- Bank CSV import with auto-categorisation
- Recurring transactions
- Assets and liabilities for true net worth
- Per-category budget limits and trend charts
- Debt payoff planner (snowball and avalanche)
- Installable offline app (PWA) and light theme

## Disclaimer

Monexa provides general information and calculators only. It is not financial advice. Projections are illustrative and not guaranteed.

## License

Add a license before publishing, for example [MIT](https://choosealicense.com/licenses/mit/). Until then, all rights are reserved by the author.

---

Created and Engineered by **Sumit Rajbanshi**
