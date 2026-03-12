# LP Blueprint — Technical Architecture Overview

Production infrastructure powering an institutional investor relations platform. 121,500+ institutional subscribers. Three live applications. One engineer.

---

## The Stack

**Core:** Node.js · Vanilla JS · TypeScript · Next.js
**Cloud:** Google Cloud Platform · Cloud Run · BigQuery · Data Science / NLP
**Data:** Automated CRON pipelines · Multi-source Regulatory Ingestion · Automated Verification
**Infra:** Vercel · Cloudflare · Stripe Telemetry · Webhook Orchestration

---

## Live Production Applications

### 1. LP Blueprint — Core Platform
**[app.lpblueprint.com](https://app.lpblueprint.com)**

Institutional-grade SaaS platform offering a highly curated matching engine for fund managers and LP allocators.

- Multi-tier algorithmic matching engine connecting users based on strict structural and mandate-driven constraints
- Automated data trains running on Google Cloud Run — ingesting global regulatory filings, cross-referencing public entity data, and executing algorithmic entity scoring via BigQuery
- High-volume verified database with an automated, multi-stage validation pipeline (<0.3% bounce rate)
- Cloudflare graceful degradation architecture for seamless bot protection without UX friction
- High-throughput data processing handling millions of rows with sub-second querying

### 2. Non-Anchor LP Directory
**[nonanchorlps.lpblueprint.com](https://nonanchorlps.lpblueprint.com)**

Curated directory of high-net-worth and family office entities serving the private equity and venture capital markets.

- Next.js application with secure authentication routing
- Complex dataset processing, normalization, and filtering
- Designed to solve early-stage capital formation constraints for institutional managers

### 3. Narrative Builder
**[story.lpblueprint.com](https://story.lpblueprint.com)**

Interactive application for fund managers to workshop, iterate, and refine their institutional data presentation.

- Data-driven narrative construction — users rebuild their data structure from the ground up
- Iterative refinement loop: draft, test, modify, repeat

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                    DISTRIBUTION LAYER                    │
│         121,500+ institutional subscribers               │
│         Newsletter · Platform · Directory                │
├─────────────────────────────────────────────────────────┤
│                   APPLICATION LAYER                      │
│  app.lpblueprint.com    nonanchorlps.lpblueprint.com    │
│  story.lpblueprint.com  adammetz.com                    │
├─────────────────────────────────────────────────────────┤
│                    DATA PIPELINE LAYER                   │
│  Regulatory Scrapers → Entity Normalization → DB         │
│  Algorithmic Scoring → CRM Webhook Routing               │
│  Continuous Data Validation → Stale Record Pruning       │
├─────────────────────────────────────────────────────────┤
│                  INFRASTRUCTURE LAYER                    │
│  GCP Cloud Run · BigQuery · Vercel CDN                   │
│  Stripe Telemetry · Cloudflare · Node.js CRON Trains     │
└─────────────────────────────────────────────────────────┘
```

---

## Why This Exists

I built an automated infrastructure that does the work of a 50-person data team.

Most companies in the institutional data space hire a 10-person engineering team and a massive sales org to do what this platform does automatically. LP Blueprint processes regulatory data, scores entities algorithmically, verifies contacts through automated pipelines, and distributes intelligence to 121,500+ users — running on infrastructure I deployed and maintain entirely solo.

The proprietary application code, algorithms, and data schemas are strictly private. The scale and infrastructure capabilities are not.

---

**Contact:** [adam@lpblueprint.com](mailto:adam@lpblueprint.com) · [adammetz.com](https://adammetz.com) · [LinkedIn](https://linkedin.com/in/adammetz)
