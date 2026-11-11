# Raju Gari Biryani — Hyderabad · Day-Level Performance Tracker

Live dashboard: **https://shuttle-ci-user1.github.io/raju-gari-biryani-dashboard/**

Day-level metrics (Nov 1, 2026 onwards) for all 27 live Raju Gari Biryani outlets
in Hyderabad (parent ID 165947):

- Orders, GMV, RDPO, RDGMV, AOV
- Top-7 discount coupon burn per day
- CBA Impressions, CPC Clicks Delivered
- Swiggy vs Toing breakup for every metric
- Growth vs same day last week (WoW) on every value

## Data sources (Snowflake, ANALYTICS.PUBLIC)

| Table | Used for |
|---|---|
| `SUPPLY_CENTRAL_FACT_TABLE_RX_DT_LEVEL` | Swiggy app orders/GMV/RDGMV/CBA/CPC |
| `SUPPLY_CENTRAL_FACT_TABLE_RX_DT_LEVEL_TOING` | Toing app orders/GMV/RDGMV/CPC |
| `CP_ORDER_OFFER` | Coupon burn (completed, non-shadow coupon offers) |
| `RESTAURANT_ATTRIBUTES` | Outlet names & areas |

Derived metrics: RDPO = RDGMV / Completed Orders, AOV = GMV / Completed Orders.

## Refreshing

To refresh with the latest data, ask the assistant session to
"refresh the Raju Gari Biryani dashboard" — it re-runs the pipeline
(`pull_data.py` → `build_metrics.py` → `build_dashboard.py`) and pushes
the regenerated HTML to this repo.
