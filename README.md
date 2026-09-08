# Flipkart Laptop Scraper

Standalone Python ETL that discovers Flipkart laptops, reads product details,
validates 19 required fields, and writes a formatted Excel workbook.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
```

## Run

Balanced run with a one-hour resume cache:

```bash
python3 flipkart_laptop_scraper_exact.py
```

Fast fresh run:

```bash
python3 flipkart_laptop_scraper_exact.py --workers 10 --cache-hours 0
```

Small smoke run:

```bash
python3 flipkart_laptop_scraper_exact.py --pages 2
```

The default workbook is written to `output/flipkart_laptops.xlsx`.

## Test

```bash
python3 -m unittest -v test_flipkart_laptop_scraper_exact.py
```

See [docs/FLIPKART_LAPTOP_SCRAPER_FIX_GUIDE.md](docs/FLIPKART_LAPTOP_SCRAPER_FIX_GUIDE.md)
for the field-by-field root-cause and repair explanation.

For complete architecture, boxed execution diagrams, internal data contracts,
failure paths, and every function, read
[docs/TECHNICAL_ARCHITECTURE_AND_EXECUTION_FLOW.md](docs/TECHNICAL_ARCHITECTURE_AND_EXECUTION_FLOW.md).

Editable diagrams are available in [`diagrams/`](diagrams/). Each flow includes
Excalidraw, Mermaid, SVG, and PNG formats.

## GitHub

This directory is an independent Git repository. Generated data and local
caches are ignored. To publish it with GitHub CLI:

```bash
git add .
git commit -m "Initial Flipkart laptop scraper"
gh repo create flipkart-laptop-scraper --public --source=. --remote=origin --push
```

Review Flipkart's current terms and applicable rules before scheduled or
high-volume collection.
