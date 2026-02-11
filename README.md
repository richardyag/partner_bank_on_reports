# Partner Bank on Reports

## Description

Odoo 19.0 Enterprise module that displays the customer's primary bank account
information on **Sale Order** and **Invoice** PDF reports, printed right after
the terms and conditions section.

The module reads the first record from `res.partner.bank_ids` and renders:

| Field            | Source                          |
|------------------|---------------------------------|
| Bank             | `partner.bank_ids[0].bank_id.name` |
| Account Number   | `partner.bank_ids[0].acc_number`   |
| BIC / SWIFT      | `partner.bank_ids[0].bank_id.bic`  |
| Account Holder   | `partner.bank_ids[0].acc_holder_name` |

Fields are conditionally displayed — only those with a value will appear.

## Dependencies

| Module    | Purpose                          |
|-----------|----------------------------------|
| `sale`    | Sale order report inheritance    |
| `account` | Invoice report inheritance      |

## Installation

1. Copy the `partner_bank_on_reports` folder into your Odoo custom addons path.
2. Update the addons list: **Settings > Technical > Update Apps List**.
3. Search for *Partner Bank on Reports* and click **Install**.

## Usage

1. Ensure the customer (`res.partner`) has at least one bank account configured
   under **Sales & Purchases > Bank Accounts**.
2. Print or preview a **Sale Order** or **Invoice** — the bank details will
   appear after the terms and conditions block.

## Technical Details

- **Reports extended:**
  - `sale.report_saleorder_document` — Sale Order / Quotation
  - `account.report_invoice_document` — Customer Invoice
- **XPath targets:** `//div[@name='note']` (sale) and `//div[@name='comment']` (invoice)
- **Position:** `after` — the bank info block is inserted immediately after the
  terms and conditions section.

## License

LGPL-3
