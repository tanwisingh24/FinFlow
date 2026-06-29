# FinFlow — Smart Financial Tracker

A single-file, browser-based personal finance tracker. No backend, no build step — just open the HTML file and start logging income and expenses.

## Features

- **Add Income / Expense** — Toggle between two modes via tabs, each with its own color theme (green for income, red for expense). Every entry captures a description, amount (₹), date, and category.
- **Summary Cards** — Live totals for Net Balance, Total Income, and Total Expenses, with transaction counts and a balance status (Positive / Deficit / Break even).
- **Monthly Budget Overview** — Preset budget caps for 5 categories (Food, Transport, Entertainment, Shopping, Utilities). Progress bars change color as spending approaches the cap (green → yellow → red).
- **Transaction List** — Scrollable, filterable feed of all entries (filter by "All", "Income only", "Expenses only", or any specific category). Each row can be deleted individually.
- **Spending by Category (Pie Chart)** — A hand-drawn canvas donut chart breaking down expenses by category, with a matching color-coded legend.
- **Savings Goal Tracker** — Set a target amount; a progress bar shows how much of it your current balance (income − expenses) covers.
- **Toast Notifications** — Lightweight success/error feedback for actions like adding, deleting, or setting a goal.
- **Persistent Storage** — All transactions and the savings goal are saved to the browser's `localStorage`, so data survives page reloads.

## How to Use

1. Open `smart_financial_tracker.html` in any modern browser (Chrome, Firefox, Edge, Safari).
2. Choose **Income** or **Expense** mode using the tabs at the top of the form.
3. Fill in description, amount, date, and category, then click **Add**.
4. Watch the summary cards, budget bars, pie chart, and savings goal update instantly.
5. Use the dropdown above the transaction list to filter entries.
6. Click the **✕** next to any transaction to delete it.
7. Set a savings target in the "Savings Goal" section to track progress toward it.

## Categories

| Income | Expense |
|---|---|
| Salary 💰 | Food 🍛 |
| Freelance 💻 | Transport 🚌 |
| Investment 📈 | Shopping 🛍️ |
| Gift 🎁 | Rent 🏠 |
| Bonus ⭐ | Utilities ⚡ |
| Other Income 🪙 | Entertainment 🎮 |
| | Health 💊 |
| | Education 📚 |
| | Other 📦 |

## Tech Stack

- **HTML5 / CSS3** — single-file layout, custom properties (CSS variables) for theming, responsive grid (stacks to single column under 820px).
- **Vanilla JavaScript** — no frameworks or build tools.
- **Canvas API** — used to draw the category breakdown pie/donut chart.
- **localStorage** — client-side persistence (keys: `finflow_tx` for transactions, `finflow_goal` for the savings target).
- **Google Fonts** — DM Serif Display, DM Sans, JetBrains Mono.

## Data Model

Each transaction is stored as:

```json
{
  "id": 1719950400000,
  "type": "income | expense",
  "desc": "Salary",
  "amount": 50000,
  "date": "2026-06-29",
  "cat": "Salary"
}
```

## Notes & Limitations

- **Local only**: data is stored per-browser via `localStorage` — it won't sync across devices and will be lost if browser storage is cleared.
- **Budget caps are hardcoded** in `renderBudget()` (Food ₹5,000, Transport ₹3,000, Entertainment ₹2,000, Shopping ₹4,000, Utilities ₹2,000). Edit the `budgets` object in the script to change these.
- **No authentication or multi-user support** — this is a personal, single-user tool.
- **Currency is fixed to ₹ (INR)** with `en-IN` locale formatting.

## File Structure

```
smart_financial_tracker.html   # everything — markup, styles, and logic in one file
```

## Possible Future Enhancements

- Export/import transactions as CSV or JSON
- Editable/custom budget limits per category via the UI
- Monthly/yearly view toggles instead of all-time totals
- Recurring transactions (e.g. monthly rent, salary)
- Multi-currency support
