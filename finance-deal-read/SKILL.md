---
name: deal-read
description: Read a deal situation and produce a practitioner-level commentary — entry price sanity check, capital structure stress, value creation thesis, and red flags. Use when someone pastes deal terms, CIM highlights, or a set of financials and asks for a read, a view, or a quick take on a transaction.
argument-hint: "<company or deal name> [deal type: LBO | M&A | minority | recap]"
---

# Deal Read

**Important**: This skill produces analytical commentary for professional discussion purposes only. It does not constitute financial advice, a fairness opinion, or investment recommendation. All deal decisions should be reviewed by qualified advisors.

This skill exists because Claude's default response to deal numbers is textbook — it computes ratios and lists them. That is not what a senior practitioner does. A practitioner reads the situation: is the entry price defensible? Does the capital structure survive a downside? Is there a real value creation story or just financial engineering? Where is the deal fragile?

This skill forces that discipline.

---

## Step 1 — Orient to the Deal Type

Before anything else, establish what kind of transaction this is. The read changes completely by deal type.

| Deal Type | Primary Lens | What Can Kill It |
|-----------|-------------|-----------------|
| LBO | Debt serviceability + exit multiple | EBITDA deterioration, rate spike, no exit |
| Strategic M&A | Synergy credibility + integration risk | Overpayment, culture mismatch, synergy miss |
| Minority / Growth | Valuation vs growth rate, governance | Dilution mechanics, founder control, exit rights |
| Recapitalization | Leverage headroom + covenant risk | Cyclicality, covenant breach, refi wall |
| Distressed / Carve-out | Asset value vs liability stack | Hidden liabilities, customer concentration, TSA risk |

If deal type is not stated, infer it from the numbers provided.

---

## Step 2 — Entry Price Sanity Check

### 2a. Anchor the Entry Multiple

EV / LTM EBITDA, EV / NTM EBITDA, EV / Revenue. Compare to public comps median and precedent transaction median. Calculate premium or discount.

### 2b. Is the Premium Justified?

A premium to comps is defensible only if one or more of these is true:
- Control premium (standard 20-30%)
- Synergy-adjusted multiple brings effective entry below comps
- Scarcity value: irreplaceable asset, licence, or market position
- Proprietary deal: no auction, no competing bids

Flag any deal where the premium exceeds 30% without a clear synergy or scarcity argument.

### 2c. Implied Growth to Justify Entry

Back into what growth rate the deal implicitly assumes:

Required CAGR = (Implied EBITDA at exit / LTM EBITDA) ^ (1 / Hold Period) - 1

If Required CAGR > Historical CAGR x 1.5: valuation is optimistic — flag it.

---

## Step 3 — Capital Structure Stress

### 3a. Leverage Snapshot

Total Debt / EBITDA, Net Debt / EBITDA, Interest Coverage (EBITDA / Cash Interest).

Benchmarks:
- Investment grade: < 2.0x Net Debt / EBITDA
- LBO typical: 4.0x - 6.5x Total Debt / EBITDA
- Stress threshold: > 7.0x is high; above 8.0x is aggressive

### 3b. Downside Serviceability Test

Downside assumption: EBITDA declines 20% from base case.

Downside FCF = Downside EBITDA - Cash Interest - Capex - Cash Taxes

If Downside FCF < 0: deal requires equity cure or refi in a downturn — flag this.
If Downside FCF > 0: debt is serviceable even in stress — note the cushion.

### 3c. Covenant and Maturity Risk

Flag if applicable:
- Springing leverage covenant headroom at entry
- Near-term debt maturity or refi wall
- Floating rate debt (rate risk)
- PIK toggle or amend-and-extend history (signals prior stress)

---

## Step 4 — Value Creation Thesis

### 4a. Classify the Thesis

| Thesis Type | What It Requires to Be Real | Common Failure Mode |
|-------------|---------------------------|---------------------|
| Revenue synergies | Joint customers, cross-sell pipeline | Almost always overestimated |
| Cost synergies | Headcount, real estate, G&A overlap | 70-80% achievable in 2 years is benchmark |
| Multiple expansion | Buy low, sell high | Requires market timing — not a thesis |
| Organic growth | New product, geography, pricing power | Requires addressable market proof |
| Operational improvement | Margin expansion via process | Most credible in PE |
| Financial engineering | Leverage + cash distribution | Dangerous in cyclical businesses |

### 4b. Stress-Test Synergies

Apply standard haircut: 70% for cost synergies, 40% for revenue synergies.
Time to realize: cost synergies 12-24 months, revenue synergies 24-48 months.
If PV of synergies < synergy premium paid: buyer is overpaying.

---

## Step 5 — Red Flag Scan

Financial:
- EBITDA margin significantly above sector median
- High add-backs to EBITDA (>15% of reported EBITDA)
- Revenue concentrated in top 3 customers (>40%)
- Declining gross margin trend while EBITDA is flat
- Negative FCF despite positive EBITDA
- Capex presented entirely as growth with minimal maintenance disclosure
- Cash conversion cycle lengthening

Structural:
- Seller retaining equity without clear reason
- No management rollover or management leaving post-close
- Earn-out comprising >20% of deal consideration
- TSA longer than 18 months in a carve-out

Market:
- Secular headwinds ignored in model
- Single-product or single-geography concentration
- Customer contracts shorter than hold period
- Key man dependency

---

## Step 6 — Deal Commentary Output Format

DEAL READ: [Company / Transaction Name]
Deal Type: [LBO / M&A / Minority / Recap / Distressed]

ENTRY PRICE
Entry multiple, vs comps, assessment, key dependency.

CAPITAL STRUCTURE
Entry leverage, interest coverage, downside FCF, assessment, key risk.

VALUE CREATION THESIS
Stated thesis, credibility (High/Medium/Low), basis, risk-adjusted view.

RED FLAGS
List only flags that actually apply with brief explanation.

OVERALL READ
2-4 sentences. An actual MD-level view — not a list of considerations. What is this deal's core bet? Is the price right for the risk? What would make you walk away?

---

## Calibration Notes

Be more skeptical when:
- Sponsor-to-sponsor deal
- Auction with 10+ bidders
- Management team with no prior PE experience
- Business never through a recession

Give more credit when:
- Proprietary deal
- Management rollover >30% of equity
- Contracted recurring revenue with low churn
- Motivated seller in a carve-out (strategic refocus)
