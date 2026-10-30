# Income vs Cost of Living in Ireland, 2023 to 2024

**Did Irish earnings keep pace with inflation? Statistical analysis of CSO data in Excel**

![Excel](https://img.shields.io/badge/Excel-217346?style=flat-square&logo=microsoftexcel&logoColor=white)
![Statistics](https://img.shields.io/badge/Statistics-t--tests%20%7C%20CI%20%7C%20correlation-4B8BBE?style=flat-square)
![Data](https://img.shields.io/badge/Data-CSO%20Ireland-00843D?style=flat-square)

---

## The answer

> **Yes.** Total regular earnings in Ireland rose **8.18%** in 2024 while prices rose **2.12%**, so the wage bill grew **5.93% in real terms**.
> Part of that came from more hours being worked. **Per paid hour, real earnings rose 3.19%.**

| | 2023 | 2024 | Change |
|---|---|---|---|
| Regular earnings, all sectors | €96.92bn | €104.85bn | **+8.18%** |
| Consumer Price Index, all items (Dec 2001 = 100) | 148.89 | 152.05 | **+2.12%** |
| Real earnings | | | **+5.93%** |
| Regular paid hours | 3,669m | 3,767m | +2.65% |
| Real earnings per paid hour | | | **+3.19%** |

---

## Questions and findings

### 1. Did earnings beat inflation in every sector?

**In 12 of 13 sectors.** Only Administrative and support services saw earnings fall (−0.5%).

| Sector | Nominal earnings growth |
|---|---|
| Professional, scientific and technical | +15.6% |
| Public administration and defence | +11.1% |
| Construction | +11.0% |
| Industry | +9.0% |
| Information and communication | +8.7% |
| Human health and social work | +8.6% |
| Education | +8.5% |
| Accommodation and food services | +7.6% |
| Transportation and storage | +5.6% |
| Financial, insurance and real estate | +5.5% |
| Wholesale and retail trade | +3.9% |
| Arts, entertainment and other services | +2.5% |
| Administrative and support services | −0.5% |

A one-sample t-test of sector growth against 2.12% inflation gives **t = 4.65, p = 0.0003**. Earnings growth across sectors was significantly higher than inflation.

Sector earnings in 2023 and 2024 are almost perfectly correlated (**r = 0.998**). Sectors kept the same pay ranking, and growth was broad rather than concentrated in a few sectors.

### 2. Was inflation above the 2% target?

**No evidence that it was.** Inflation across the 12 CPI spending categories averaged 1.65%, with a 95% confidence interval of −0.21% to 3.51%. A one-sample t-test against 2% gives **p = 0.657**.

The experience varied a lot by category:

| Lowest | | Highest | |
|---|---|---|---|
| Clothing and footwear | −6.1% | Restaurants and hotels | +4.7% |
| Furnishings and household | −0.8% | Recreation and culture | +4.5% |
| Housing, water, energy | +0.3% | Alcohol and tobacco | +3.7% |

So how much the cost of living rose depends on what a household spends its money on.

---

## Method

| Step | Detail |
|---|---|
| Data | CSO tables **EHA04** (earnings and labour costs by NACE sector) and **CPM01** (Consumer Price Index by commodity group) |
| Cleaning | Regular earnings only, excluding irregular payments like bonuses. The "All NACE sectors" total is kept for the headline and excluded from sector tests. Monthly CPI averaged to annual values. |
| Real growth | (1 + nominal growth) / (1 + inflation) − 1 |
| Per-hour growth | Earnings divided by regular paid hours, to separate pay rises from growth in hours worked |
| Inflation test | One-sample t-test, H₀: mean category inflation = 2%, H₁: > 2%, with a 95% confidence interval |
| Sector test | One-sample t-test, H₀: mean sector earnings growth = CPI inflation, H₁: greater |
| Stability | Pearson correlation of sector earnings, 2023 vs 2024 |

Every result in the workbook is a live Excel formula (`AVERAGE`, `STDEV`, `TINV`, `TDIST`, `CORREL`, `COUNTIF`), so you can trace each number back to the CSO values.

## The workbook

[`Income_vs_Cost_of_Living_Ireland.xlsx`](Income_vs_Cost_of_Living_Ireland.xlsx)

| Sheet | Contents |
|---|---|
| Summary | Key results, linked to the analysis sheets |
| CPI_Data | CPI for 12 commodity groups and all items, 2023 and 2024, with inflation rates |
| Earnings_Data | Regular earnings and paid hours for 13 sectors, with nominal and real growth |
| Real_Earnings | Headline real earnings and per-hour calculations |
| Inflation_Test | Confidence interval and t-test for inflation against 2% |
| Sector_Analysis | Sector t-test, beat-inflation count and correlation |

Colour key: blue = CSO data or input, black = formula, green = link to another sheet, shaded = key result.

## Limitations

- **Two years only.** One year of change can't show a trend.
- **Totals, not individual pay.** EHA04 reports the total wage bill, so a rise can come from more workers as well as higher pay. The per-hour measure partly corrects for this.
- **Unweighted categories.** The category t-test treats every spending category equally, while the official CPI weights them by household spending. That's why the category average (1.65%) differs from all-items inflation (2.12%).
- **National averages.** Results can differ by region, age, household type or contract type.

## Notes

- Completed for MIS41130 Statistical Methods at UCD Michael Smurfit Graduate Business School.
- This version rebuilds the submitted analysis. The original confidence interval and t-test mistakenly treated six rebased versions of the same CPI index as monthly observations. The sector ANOVA was replaced with a t-test, because EHA04 gives one total per sector per year, which leaves no within-sector variation for ANOVA to use. The headline real earnings figure (5.93%) is unchanged.
- Data: Central Statistics Office Ireland, licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

---

**Sudarshan Ellora** · [Portfolio](https://www.sudarshanellora.com/) · [LinkedIn](https://linkedin.com/in/sudarshane) · [GitHub](https://github.com/sudarshanellora)
