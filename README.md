# 🧊 Locus Arca

**A free, offline lab sample management tool — one HTML file, no installation, no cloud.**

> Built for labs that are tired of spreadsheets named `FINAL_v3_USE_THIS_ONE.xlsx`.

![Screenshot placeholder — main view with storage tree, sample list and detail panel](docs/screenshot-main.png)

---

## What it does

Locus Arca lets you map your entire freezer infrastructure and track exactly where every sample is stored — down to the individual grid position in a box. It runs as a **single HTML file** in your browser. No server. No account. No internet connection needed. No admin rights required. All data is saved in a JSON file you control.

---

## Features

### Storage structure
- Five-level hierarchy: **Freezer unit → Compartment → Rack → Drawer → Box**
- Not all levels are required — a box can sit directly inside a unit or compartment
- **Location field** per freezer unit (room number, building, external storage provider)
- **Visual groups** for freezer units (e.g. "-20°C devices", "4°C devices") — display only, not part of the sample path
- Three box types: **Grid** (A1, B2…), **Numbered** (1, 2, 3…), **Freeform** (text note)
- Grid boxes: visual position picker, occupied slots marked, no double-booking
- Samples can be stored without a box, or without any storage location at all
- Sidebar shows **📂 Not stored** entries automatically when relevant
- Right-click context menu on any tree item: **rename, resize, move, delete**
- Move an entire rack, drawer, or box — all contents and samples move with it
- Drag & drop reordering within the same level

### Sample management
- **Sample ID is optional** — the system auto-assigns an internal ID (S-00001, S-00002…) if left blank
- All fields optional: sample type, project, subject ID, collection date, volume, remarks
- Status: Available / Removed / Consumed / Reserved / Disposed
- **Multi-position selection** in grid boxes (Ctrl+Click) — creates one sample per position with shared metadata
- **Autocomplete** in all text fields — learns from your own data
- Move samples between locations without re-entering all data
- Full audit log of all create / edit / move / delete / bulk actions

### Multi-select & bulk actions
- Checkbox per row — select any number of samples
- **Edit selection** — update type, status, project or remarks; only checked fields are overwritten
- **Move selection** — reassign all selected samples to the same new location
- **Delete selection** — delete all selected samples after confirmation

### Search & filter
- Search across all fields simultaneously (ID, system ID, type, project, subject, location, notes)
- Filter by sample type and status
- Sidebar tree acts as an additional location filter — combine all three

### CSV Import & Export
- **CSV export** with selectable columns — 17 fields, choose exactly what you need
- **CSV import** with template download — missing structure elements (racks, boxes etc.) are created automatically on import; box type auto-detected from position format
- UTF-8 BOM + semicolon separator — opens directly in Excel
- Headers switch with language setting (DE/EN)

### Storage & backup
- Save directly to file (Chrome/Edge/Opera) or download (Firefox/Safari)
- **Backup** always opens a Save As dialog
- Confirmation prompt before overwriting an existing file
- Filename shown in title bar

### UI & usability
- Dark theme
- German / English language toggle (including CSV headers)
- No admin rights required — runs directly from a local HTML file
- Resizable sidebar

---

## Getting started

1. Download `locus-arca.html`
2. Open it in Chrome or Edge
3. Click **Demo** to explore with example data — or click **Lager** to set up your own storage structure
4. Click **+ Neue Probe** to add your first sample
5. Click **Speichern** to save — choose a location on a shared network drive if multiple people use it

> **Tip:** Drop the HTML file and the JSON database on a shared network drive so the whole team can access it. Only one person should edit at a time — there's no conflict resolution for simultaneous edits.

---

## Screenshots

| Main view | Storage structure | Sample form |
|-----------|------------------|-------------|
| ![Main view](docs/screenshot-main.png) | ![Storage structure](docs/screenshot-structure.png) | ![Sample form](docs/screenshot-form.png) |

---

## File format

Everything is stored in a single `.json` file:

```json
{
  "meta": { "appName": "Locus Arca", "sampleCounter": 42 },
  "storage": { "freezers": [ ... ], "groups": [ ... ] },
  "samples": [ { "_uid": "S-00001", "id": "PR-2026-001", ... } ],
  "history": [ ... ]
}
```

Each sample has an internal `_uid` assigned by the system (never changes) and an optional user-visible `id`. The file is human-readable plain JSON.

---

## Browser compatibility

| Browser | Save to file | Notes |
|---------|-------------|-------|
| Chrome | ✅ Direct save | Recommended |
| Edge | ✅ Direct save | Recommended |
| Opera | ✅ Direct save | Chromium-based |
| Brave | ✅ Direct save | Chromium-based |
| Vivaldi | ✅ Direct save | Chromium-based |
| Firefox | ⬇️ Download only | Fully functional |
| Safari | ⬇️ Download only | Fully functional |

---

## License

MIT License — free to use, modify and distribute.

---

*Feedback and issues welcome via GitHub Issues.*
