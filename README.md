# ♿ Accessible Public Space Finder

A simple, searchable directory of **parks, libraries, community centres and public toilets** in Mandya, Karnataka.
Search by name or area, then filter by the accessibility features a person needs:
**ramp, wheelchair access, lighting, seating and toilet**. Results show as a list **and** on a map.

**Live site:** `https://USERNAME.github.io/accessible-space-finder/` *(replace after setting up GitHub Pages)*

> ⚠️ **Sample data for a college project.**
> - Places marked **“On OpenStreetMap”** exist on OpenStreetMap (name and approximate position).
> - Places marked **“Sample place”** are made up for the demo.
> - **Every** ramp / wheelchair / lighting / seating / toilet value and every opening time is **made up**. Nothing was surveyed.

---

## ✨ Features

| Feature | How it works |
|---|---|
| Search box | Matches the English **or** Kannada name, area and type. Every typed word must match. |
| Type of place | Buttons: All, Parks & grounds, Libraries, Community centres, Public toilets |
| Accessibility filters | 5 tick boxes. A place must have **every** ticked feature (AND, not OR). |
| Wheelchair access | 3 levels, the same words OpenStreetMap uses: **yes / limited / no**. Only “yes” passes the filter. |
| Accessibility score | Each card shows **x/5 features**. Sort by **Most accessible** to see the best first. |
| Nearest to me | **Use my location** sorts places by distance and shows “1.2 km away”. |
| Map | Coloured pins for each type. **Show on map** zooms to a place; clicking a pin highlights its card. |
| Directions | Opens OpenStreetMap directions to the place in a new tab. |
| Kannada / English | One button switches every word on the page. |
| Accessible website | High-contrast mode (remembered), “Skip to results” link for keyboard users, big buttons, screen-reader labels. |

---

## 🛠️ Built with

- **HTML** – the structure of the page
- **CSS** – the look, phone layout and high-contrast mode
- **JavaScript** – no frameworks; plain JS does the searching, filtering, sorting and drawing
- **Leaflet + OpenStreetMap** – the free, open-source map
- **GitHub Pages** – free hosting

---

## 📁 Files

| File | What it does |
|---|---|
| `index.html` | The **structure**: header, filters, results list, map box |
| `css/style.css` | The **look**: colours, layout, high-contrast mode, phone layout |
| `js/data.js` | The **data**: 4 categories and 24 places (sample) |
| `js/i18n.js` | All text in **English and Kannada** |
| `js/search.js` | The **brain**: filters, searches, scores and sorts the places |
| `js/app.js` | Connects everything: builds the buttons, draws the cards and map pins |
| `js/config.js` | Optional database (Supabase) settings. Empty = use `data.js` |
| `README.md` | This file |

---

## ▶️ Run it on your computer

1. Download or unzip the project folder.
2. **Double-click `index.html`**. It opens in your browser.
3. Try it: click **Public toilets**, then tick **Ramp** and **Wheelchair access**. You should see 2 places.

> The map needs an internet connection. **“Use my location”** works only on the live site (https),
> not when the file is opened by double-clicking.

---

## 🐙 Put it on GitHub

1. Go to **https://github.com** and sign in (or **Sign up**, free).
2. Click **+** (top right) → **New repository**.
3. **Repository name:** `accessible-space-finder` → choose **Public** → leave **Add a README file** unticked → **Create repository**.
4. On the next page click the link **uploading an existing file**.
5. Open the project folder, select **everything inside it** (`index.html`, `README.md`, `css`, `js`) with **Ctrl+A**,
   and **drag it** into the browser window.
   - ⚠️ Drag the **contents**, not the outer folder. `index.html` must be at the top level of the repository.
6. Wait until all the files are listed, then click **Commit changes**.

## 🌐 Make it a live website (GitHub Pages, free)

1. In the repository, click **Settings** (top tab, gear icon).
2. In the left menu, click **Pages**.
3. Under **Build and deployment**:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main` and `/ (root)` → **Save**
4. Wait 1–2 minutes and refresh. A box shows **“Your site is live at …”** with your link.
5. Copy that link into the **Live site** line at the top of this README.

**To change something later:** open the file on GitHub → click the ✏️ pencil → edit → **Commit changes**.
The live site updates in about a minute.

---

## ➕ Add or change a place

Open `js/data.js` and copy one line inside `places: [ … ]`. Change the values and keep the commas.

| Field | Allowed values |
|---|---|
| `category` | `park`, `library`, `community`, `toilet` |
| `wheelchair` | `yes`, `limited`, `no` |
| `has_ramp`, `has_lighting`, `has_seating`, `has_toilet`, `accessible_toilet` | `true` or `false` |
| `source` | `osm` (place is on OpenStreetMap) or `sample` (made up) |
| `lat`, `lng` | Map position. Right-click the place on openstreetmap.org → **Show address** to see it. |

---

## 🎤 Viva questions

| Question | Short answer |
|---|---|
| How does the filter work? | `search.js` keeps a place only if it passes 3 checks: type, search words, and **every** ticked feature (`Array.every`). |
| Why doesn’t “limited” wheelchair access count? | Someone who needs step-free access can’t rely on “limited”. It still shows on the card in yellow. |
| How is the nearest place found? | The browser gives your latitude/longitude; the **haversine formula** gives the straight-line km to each place; then we sort. |
| How is the site made accessible? | Labels on every input, a skip link, keyboard focus outline, 44 px buttons, high-contrast mode, and features shown with ✓/✗ and words, not colour alone. |
| Why is the data “sample”? | No public accessibility survey of Mandya was available. The next step would be a field survey or reports from users. |
| What would you add next? | A database (Supabase), a “report a problem” form, photos of entrances, and syncing with OpenStreetMap’s `wheelchair=*` tags. |

---

*College project · Map data © OpenStreetMap contributors*
