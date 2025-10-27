# Contacts — iOS-style Phonebook (CSV → Web App)

A tiny, front-end–only phonebook you can host anywhere (e.g., GitHub Pages). Drop in a **Google Contacts CSV** (or pick one from your device) and get an iOS-style contacts UI with search, A–Z index, favorites, groups, per-number Call/SMS/Copy actions, add/edit/delete (local), and vCard export. Works offline as a PWA. 

---

## Features

* **Zero backend**: Everything runs in the browser; no data leaves your device unless you host the CSV yourself. 
* **CSV loader with fallback**: Tries to load `contacts.csv` by default, supports `?src=your.csv`, and gracefully falls back to a file picker if fetching fails. 
* **Smart CSV detection**: Auto-detects name/phone/email/group columns, supports multiple numbers/emails per contact (comma/semicolon), and merges group values. 
* **Clean iOS-style UI** with A–Z jump list, sticky section headers, and contact detail sheet. 
* **Search** across name, numbers, and emails; quick “/” focuses the search box. 
* **Favorites & Groups** filters; “All / Favorites” tabs and a group dropdown. 
* **Per-number actions**: Call, SMS, Copy; plus single-contact or bulk **vCard (.vcf)** export. 
* **Local edits**: Add/Edit/Delete and Favorites persist in `localStorage` (doesn’t modify your CSV). 
* **Dark/Light theme** with a toggle; remembers your choice. 
* **PWA + offline**: Install to home screen; service worker caches and enables offline viewing. 

---

## Quick start (GitHub Pages)

1. **Export from Google Contacts**: Go to Google Contacts → **Export** → choose **CSV**.
2. **Name the file** `contacts.csv`.
3. **Put files in your repo**: Add this project’s `index.html` (and the `icons/` if you want custom app icons) to your repo root, alongside `contacts.csv`.
4. **Enable GitHub Pages** for the repo. Visit your site—your contacts should appear automatically. Use **Reload CSV** anytime. 

> Don’t want to publish your contacts? Keep the repo **private**, or **don’t commit the CSV**—the app can load a local CSV via the built-in file picker when fetch fails. 

---

## Using your own CSV path

You can point the app at any CSV URL with a query param:

```
https://your-domain.example/?src=https://path/to/your.csv
```

The **Reload CSV** button re-fetches the current source with cache-busting. 

---

## CSV format tips

* **Columns**: The app auto-detects name/phone/email/group columns (common Google Contacts headers work out-of-the-box). 
* **Multiple values**: Put multiple numbers/emails in one cell separated by commas/semicolons; groups can be comma-separated. The parser also understands `:::` joins. 
* Contacts without a name but with a phone/email are still shown. 

---

## Local edits & persistence

* **Add/Edit/Delete** and **Favorites** are stored in `localStorage` and merged on top of the CSV each load. Your CSV file is never modified by the app. 
* Use **Delete** to hide a CSV-sourced contact locally; you can always re-merge by clearing browser storage. 

---

## vCard export

* **Export All (.vcf)** creates a vCard containing the currently filtered list.
* In the contact sheet, **vCard** exports just that one contact. 

---

## Keyboard & accessibility niceties

* Press **/** to jump to search.
* List items are keyboard focusable; **Enter** opens the contact sheet. 

---

## PWA notes

The app registers a manifest and a minimal service worker so you can **install** it and **use offline** (it caches the shell and last-viewed content). You can replace icons in `icons/` for your own branding. 

---

## Privacy

This is a static, client-side app. If you host `contacts.csv` publicly, the data will be public. Prefer a **private repo**, or load your CSV locally via the file picker. 

---

## Development

* Single-file app: everything (HTML/CSS/JS) is in `index.html`. Tweak the palette via the CSS variables in `:root`/`.dark`. 
* No build step required—just edit and refresh.

---

## License

MIT (or your preferred license).

---

**Credits**
UI and functionality implemented in a single page with plain JavaScript, inspired by the iOS Contacts look & feel. 
