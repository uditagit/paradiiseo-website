# Proposed Maintenance Tasks

## Typo Fix
- **Location:** `index.html`, hero section paragraph (~lines 32-35).
- **Issue:** The sentence "earn more than months of subscription churn" mixes metaphors and reads like a typo; "subscription churn" cannot be something you "earn more than".
- **Task:** Update the copy to say something like "earn more than months of subscription revenue" so the value proposition reads correctly.

## Bug Fix
- **Location:** `index.html`, `calculateEarnings()` implementation (~lines 187-207).
- **Issue:** All numeric inputs are parsed with `parseInt`, so any decimal values (e.g., $299.99 ticket price) are silently truncated. This underreports potential revenue.
- **Task:** Switch to `parseFloat` (with proper NaN handling) and ensure currency output is rounded to two decimals so fractional values are preserved end-to-end.

## Documentation Discrepancy
- **Location:** `index.html`, fallback copy inside the results container (~lines 166-171).
- **Issue:** The placeholder text says "Enter your numbers to see the comparison," but the script immediately populates results on `DOMContentLoaded`, so the message never reflects actual behavior.
- **Task:** Either adjust the script to wait for user input before rendering results or update the placeholder copy to match the auto-calculation behavior.

## Test Improvement
- **Location:** Project root (no automated tests currently present).
- **Issue:** There is no automated coverage ensuring the earnings calculator produces expected numbers. A regression (like the truncation bug above) would go unnoticed.
- **Task:** Introduce a lightweight automated test (e.g., with Jest + jsdom or a headless browser check) that loads the calculator logic and asserts the computed annual subscription, experience revenue, and difference for representative inputs.
