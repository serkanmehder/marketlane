# MarketLane

A research platform for studying AI shopping decisions.

MarketLane combines an online shopping environment with an experimental framework for examining how AI agents evaluate products, compare prices, and make decisions on behalf of users. Agents interact with product offers, baskets, and checkout pages while the platform records their observable actions.

The aim is to study the decision process as well as the final choice: what information an agent encounters, whether it explores alternatives, and whether it revises an earlier selection when new information becomes available.

## A/B testing and experimental design

The platform includes an A/B testing framework and supports studies with more than two conditions.

- **Server-side assignment:** Sessions are assigned to experimental conditions, with balanced allocation within a batch.
- **Stable conditions:** A session keeps its assignment as the agent navigates between offers, the basket, and checkout.
- **Controlled comparisons:** Researchers can vary price presentation, fee disclosure, and comparison information while holding product characteristics constant.
- **Presentation randomization:** Seller identity and offer position can be randomized independently of the treatment assignment.
- **Separate experiment batches:** Each set of runs has its own identifier, keeping results from different studies and pilot sessions separate.

Supported study designs examine upfront versus delayed fee disclosure, partitioned versus all-in price presentation, fee magnitude, information about alternatives, and the convenience of switching between offers. Assignment timing depends on the study design; some conditions are assigned at entry, while others are assigned after an eligible checkout is reached.

## Clickstream and behavioral tracking

MarketLane records timestamped events throughout the shopping journey, including:

- Product and offer selections.
- Basket and checkout visits.
- Comparison-link clicks and changes of selection.
- Recorded display of fee information and checkout summaries.
- Reviewed checkout totals and order confirmations, where applicable.

These events help distinguish an initial choice, an attempt to explore alternatives, an actual switch, and a reviewed final selection. A comparison click is not treated as a completed switch, and a displayed fee is not assumed to have been understood.

## Results dashboard

A research dashboard organizes results by experiment batch, condition, and model. Researchers can inspect individual session timelines and export records for further analysis.

Depending on the study, the dashboard reports product-choice rates, comparison clicks, switching behavior, checkout review, and order completion. It includes confidence intervals and exploratory statistical comparisons, with multiple-comparison adjustments for designated sets of contrasts. Sessions with missing outcomes remain visible rather than being silently discarded.

## Automated agent runs

Experiment runners support repeated sessions with fresh agent context and configurable batch sizes and concurrency. Run records include model identifiers, prompt fingerprints, session identifiers, and task metadata so that observed website events can be linked to the corresponding agent run.

Tasks can end at different stages, such as adding an item to the basket, reviewing checkout, or completing an order. A runner reporting that a session ended is kept distinct from evidence that the requested shopping task was completed.

## Research questions

- How does the timing and presentation of price information affect AI shopping decisions?
- Do agents reconsider an initial choice after learning its final cost?
- Does explicit information about alternatives change exploration and switching?
- How do fee magnitude and switching convenience affect observed behavior?
- How do decisions differ across models, task instructions, and browser configurations?

## Interpretation

MarketLane studies agent behavior under specified tasks and interfaces. Observed actions and final selections do not directly establish an agent's internal reasoning or predict human consumer behavior. Comparisons across models also require attention to differences in browser tools, available information, and operational settings.

## About this repository

This repository provides a public overview of the project. The application code, experiment runners, prompts, and research data are maintained privately.
