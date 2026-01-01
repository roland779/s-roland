# Research Profile — Static Academic Website

This repository contains a minimal, multilingual (EN/DE) static personal profile website intended for academic use.

**Repository contents**
- Main page: `index.html`
- Static assets: `academic_website/assets/` (images, CSS)
- Translations: `academic_website/data/i18n.json`
- Publications data: `academic_website/data/publications.json`
- Utility scripts: `academic_website/tools/` (e.g. `sync_publications.py`)

## Local preview
To preview the site locally from the project folder, start a simple HTTP server. Example with Python:

```bash
python -m http.server 8000
# then open http://localhost:8000 in your browser
```

Open `index.html` in the browser or navigate to the desired subpath.

## Language switching (EN/DE)
Use the EN/DE buttons in the header to switch languages. The selection is stored locally in your browser (`localStorage`). Translation strings are stored in `academic_website/data/i18n.json`.

## Publications
Publications are loaded from `academic_website/data/publications.json`.

### Syncing publications (semi-automatic)
This repository includes a helper script to semi-automatically generate or update `publications.json` from an external author page (for example SSRN). External services often employ CORS or bot protection; the script runs locally and scrapes the provided URL.

Steps:
1) Install required Python packages:

```bash
pip install requests beautifulsoup4
```

2) Run the sync script (example):

```bash
python academic_website/tools/sync_publications.py --ssrn "<SSRN-AUTHOR-URL>" --out academic_website/data/publications.json --merge
```

Notes:
- External site markup can change. If parsing fails, adapt the selectors inside `academic_website/tools/sync_publications.py`.
- For Google Scholar it is usually preferable to export BibTeX and import it locally instead of scraping.

## Customization
- Update links and contact information in `index.html`.
- Add a profile picture to `academic_website/assets/images/` (e.g. `profile.jpg`).
- Edit translation strings in `academic_website/data/i18n.json`.
- Maintain publications in `academic_website/data/publications.json` or update them with the sync script.

## Development
- Make changes locally and test with the simple HTTP server above.
- Optionally use a live-reload tool such as `live-server` for faster iteration.

## License
This project is released under the MIT License — see `LICENSE`.

## Contact
If you have questions or find issues, please open an issue or contact the maintainer via the address provided in the project.
