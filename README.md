# Google Workspace list prices in euros — open data

Two small, sourced datasets about Google Workspace licensing, published by
[WorkspaceRadar](https://workspaceradar.com/) under **CC BY 4.0**. Every row names the
Google page it was read from and the date it was last checked. The live, explained version is
<https://workspaceradar.com/google-workspace-pricing>; this repository is the citable snapshot.

*Deutsch:* Google-Workspace-Listenpreise in Euro (Business Starter, Standard, Plus; Jahres- und
Flexible-Tarif) und die SKU-IDs der Licensing API, jede Zeile mit Quelle und Prüfdatum. Lizenz
CC BY 4.0. Erklärte Fassung: <https://workspaceradar.com/de/google-workspace-preise>.

## Datasets

| File | What | Rows | Source per row |
|---|---|---|---|
| `data/google-workspace-list-prices-eur.csv` / `.json` | Google's published standard list price per user per month in EUR for Business Starter, Business Standard and Business Plus, on the annual-commitment plan and on the Flexible plan, with the derived per-year figure | 6 | workspace.google.com/intl/en_ie/pricing.html |
| `data/google-workspace-skus.csv` / `.json` | The product and SKU identifiers the Enterprise License Manager API uses for the Google Workspace editions, and whether Google publishes a per-seat price for each | 8 | developers.google.com (Licensing API products) |

### Columns

**google-workspace-list-prices-eur** — `sku_id` (Licensing API SKU); `edition`; `plan`
(`ANNUAL` = one-year commitment, `FLEXIBLE` = month to month); `currency` (EUR only);
`price_per_user_month`; `price_per_user_year` (month × 12, derived); `effective_from` (first
date the figure was captured); `checked_on` (last date a person re-read it on the page);
`source_url`; `source_note` (which toggle state was read, and that the standard price was taken,
not the time-limited introductory one).

**google-workspace-skus** — `product_id`; `sku_id`; `sku_name`; `published_price` (`yes`, or
why not); `source_url`.

CSV files use `,` as separator, UTF-8, no BOM. JSON files wrap the same rows in `rows`.

## Provenance and limits

- Prices are read by a person from Google's pricing page for Ireland (`intl/en_ie`), which shows
  EUR. Google's page is geo-localised; a figure seen in one region does not hold in another, so
  only EUR is included.
- The **standard** price is recorded, never the introductory discount Google shows beside it
  ("20–30% off for 3 months"). The figures include the January 2025 Gemini bundling.
- Enterprise and Frontline editions are listed in the SKU table but carry **no price**: Google
  publishes none ("contact sales"). No figure here is estimated or interpolated.
- These are list prices, not invoices. Reseller discounts and older contracts differ.
- When Google reprices, a new row with a later `effective_from` is added; old rows stay, so a
  historical figure still explains itself.
- This is data, not advice. Google Workspace is a trademark of Google LLC; WorkspaceRadar is
  not affiliated with or endorsed by Google.

## How to cite

WorkspaceRadar (2026). *Google Workspace list prices in euros and Licensing API SKUs — open
data.* <https://github.com/tony158/workspaceradar-open-data>. CC BY 4.0. See `CITATION.cff`.

## Licence

[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) —
use it freely, name "WorkspaceRadar, workspaceradar.com" as the source.
