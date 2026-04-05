# 🍋 Sweetwater Court — POS System

A modern, single-file point-of-sale system for Sweetwater Court — a boutique artisan lemonade bar. Built as a standalone HTML app with no server or dependencies required.

## Features

### Customer Kiosk (`/` — Order tab)
- Full menu with category filtering (Signature, Seasonal, Sparkling, Wellness, Add-ons)
- Item customization modal — sweetness, ice level, size, add-ons, staff note
- Live cart with quantity controls and tax calculation
- Order confirmation screen with ticket number

### Kitchen / Staff View (Kitchen tab)
- Kanban board: **New → In Progress → Ready**
- Live elapsed timers per ticket (amber at 5 min, red at 10 min)
- Allergy / special note callouts highlighted in amber
- **Sound alert** (Web Audio API chime) when a new order arrives
- Toggle to enable/disable sounds
- Live stats sidebar: queue, making, done today, revenue
- 🏷 Cup label button on every ticket

### Cup Labels (🏷 button on each ticket)
- Print-ready label for each drink in an order
- Shows: drink name, customer name, ticket number, modifiers, time
- Two-up layout when printing
- Browser print dialog (no printer driver needed — works with any printer including thermal label printers if configured as default)

### Pickup Board (Pickup tab)
- Large-format display for customers
- Ready orders shown as bold ticket number cards
- Being-made orders shown as subtle pills
- Auto-calculated estimated wait time

## Running Locally

No build step. Just open the file:

```bash
# Option 1 — open directly
open index.html

# Option 2 — serve with Python (recommended to avoid any CORS quirks)
python3 -m http.server 8080
# then visit http://localhost:8080

# Option 3 — serve with Node
npx serve .
```

## GitHub Pages Deployment

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your kiosk will be live at `https://yourusername.github.io/sweetwater-court/`

## Testing the Full Flow

1. Open **Order** tab — browse menu, add items with customizations
2. Enter a name and place the order
3. Switch to **Kitchen** tab — hear the chime, see the ticket in "New"
4. Click **Start** → ticket moves to "In Progress"
5. Click **🏷** on a ticket → preview the cup label, print it
6. Click **Ready ✓** → ticket moves to "Ready"
7. Switch to **Pickup** tab — see the ticket number in the ready grid
8. Back in Kitchen → click **Collected** to complete the order

## What to Add for Production

| Feature | Suggested Tool |
|---|---|
| Payments | Square Web Payments SDK or Stripe.js |
| Receipt printer | Star Micronics WebPRNT or Epson ePOS SDK |
| Persistent orders | Supabase (free tier) or Firebase Realtime DB |
| SMS pickup alerts | Twilio or Textbelt |
| Offline support | Service Worker + Cache API |
| Multi-device sync | BroadcastChannel API or WebSockets |

## File Structure

```
sweetwater-court/
├── index.html   ← entire app (no dependencies)
└── README.md
```

## License

MIT — free to use, modify, and deploy.
