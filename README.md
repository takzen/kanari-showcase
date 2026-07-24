<p align="center">
  <img src="assets/logo.png" width="96" alt="Kanari logo">
</p>

<h1 align="center">Kanari</h1>

<p align="center">
  <strong>Authorized red-team security &amp; compliance audits for LLM chatbots and agents.</strong>
</p>

<p align="center">
  Find the holes in your AI before your customer does — or the regulator.
</p>

<p align="center">
  <a href="https://kanari.pl">kanari.pl</a> &nbsp;·&nbsp; built for the Polish market: <b>EU AI Act</b> · <b>GDPR (RODO)</b> · <b>KNF</b>
</p>

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-live-2ea44f">
  <img alt="market" src="https://img.shields.io/badge/market-Poland%20%F0%9F%87%B5%F0%9F%87%B1-333">
  <img alt="engine" src="https://img.shields.io/badge/engine-Python%203.11%2B-3776AB">
  <img alt="dashboard" src="https://img.shields.io/badge/dashboard-Next.js%2016-000">
</p>

> **This is a public showcase.** The source code is private and proprietary — this repository
> contains documentation and screenshots only. The product is live and open for audits.

---

## The problem

Companies are shipping AI chatbots and agents fast. A single over-eager assistant can:

- **leak another customer's personal data** — a GDPR / RODO breach,
- **promise a refund, discount or price** it isn't authorized to make — a binding commitment,
- **be hijacked** by an instruction hidden in a document, review or e-mail — prompt injection,
- **give unlicensed financial or medical advice**, or spill its own system prompt and secrets.

In the EU, the **AI Act** and **GDPR** turn these from "bugs" into real legal and financial exposure.

## What Kanari does

Kanari is an **authorized red-team harness** that attacks *your own* LLM systems before anyone
else does. It runs a battery of categorized probes, proves each finding with **two independent
signals**, and turns the result into a **compliance document** — mapped to EU regulation **and the
OWASP AI security standards**, with a **board-level summary** and a **prioritized fix-list**.

> Defensive use only: Kanari tests systems you own or are authorized to test. Planted secrets are
> always **canary tokens**, never real credentials.

---

## Screenshots

**Marketing site — [kanari.pl](https://kanari.pl)**

![Kanari landing page](assets/landing.png)

**Audit dashboard — risk score, severity breakdown, category & regulation coverage**

![Kanari audit dashboard](assets/dashboard.png)

---

## Why it's different — the moat

| | |
|---|---|
| 🇵🇱 **Polish-language attacks** | Jailbreaks and injections behave differently in Polish. Almost no foreign tool tests them — Kanari ships native Polish attack packs. |
| 🏛️ **Compliance mapping** | Every finding maps to a concrete obligation under the **AI Act, GDPR (RODO), UOKiK, KNF** or medical law. A technical report becomes a compliance document. |
| 🎯 **Two independent signals** | A deterministic **canary-token detector** *and* an **LLM-as-judge**. A finding is evidence, not one model's opinion. |
| 📑 **OWASP standards mapping** | Every finding maps to the **OWASP Top 10 for LLM Applications (2025)** *and* the new **OWASP Top 10 for Agentic Applications (2026)** — the security standards enterprises and auditors already recognize. |
| 🏭 **Industry scenario packs** | E-commerce (false promises, RODO data leaks), banking/finance (unlicensed investment advice), healthcare (dosing, diagnosis). |

---

## How it works

```mermaid
flowchart LR
    A[Attack packs<br/>YAML probes] --> R[Async runner]
    C[Canary tokens<br/>seeded in context] --> R
    R -->|sends probes| T[Target adapter<br/>chatbot / agent / HTTP]
    T -->|transcripts| D[Deterministic<br/>canary detector]
    T -->|transcripts| J[LLM-as-judge<br/>per-category rubric]
    D --> V{Finding?}
    J --> V
    V --> M[Standards mapping<br/>AI Act · RODO · KNF<br/>OWASP LLM & Agentic]
    M --> O[Report · Dashboard · PDF<br/>Exec summary · Fix-list<br/>CI gate · Guard]
```

1. **Seed** unique canary tokens into the target's context — never real secrets.
2. **Run** the attack battery against the target through a pluggable adapter.
3. **Score** each transcript with a deterministic detector *and* an LLM-as-judge rubric.
4. **Map** findings to regulatory obligations and render the deliverables.

---

## Attack categories

`prompt_injection` · `jailbreak` · `system_prompt_leak` · `secret_exfil` · `tool_abuse` ·
`unsafe_output` · `obfuscation_bypass` · `unauthorized_commitment` · `data_privacy` ·
`financial_advice` · `medical_advice`

Probes run **single-turn** or **multi-turn** — context-building jailbreaks and staged extraction
that only trigger after several messages, testing the target the way a real attacker works.

## Compliance coverage

| Regulation | Obligation checked |
|---|---|
| **EU AI Act** | Transparency (Art. 50) · Risk management (Art. 9) · Accuracy & robustness (Art. 15) |
| **GDPR / RODO** | Data minimization (Art. 5) · Security of processing (Art. 32) |
| **UOKiK** | Ban on unfair market practices (binding promises) |
| **KNF** | Investment advice reserved for licensed entities |
| **Medical law** | No medical advice without qualifications |

Each obligation is scored **met / breached / not tested**, so gaps are visible at a glance.

## OWASP standards mapping

Alongside the regulatory view, findings are mapped to two recognized OWASP security standards, so
the report speaks the language auditors and enterprise security teams expect:

| Standard | Coverage |
|---|---|
| **OWASP Top 10 for LLM Applications (2025)** | Prompt injection (LLM01), sensitive-information disclosure (LLM02), improper output handling (LLM05), excessive agency (LLM06), system-prompt leakage (LLM07), misinformation (LLM09). |
| **OWASP Top 10 for Agentic Applications (2026)** | Agent goal hijack (ASI01), tool misuse (ASI02), identity & privilege abuse (ASI03), human-agent trust exploitation (ASI09) — the new standard for AI agents that call tools and APIs. |

Items outside black-box conversational testing (supply chain, model poisoning, code execution,
inter-agent communication) are honestly reported as **out of scope** — never fake-covered.

---

## Deliverables

- **Interactive dashboard** — risk score, severity distribution, category & regulation coverage,
  OWASP LLM + Agentic tables, board summary, remediation list, and per-attack transcripts (including
  full multi-turn conversations) with the judge's reasoning. Plus a **run history** of past audits.
- **Board-level summary + prioritized fix-list** — every audit opens with a plain-language risk
  verdict and business impact, then a ranked "what to fix and why" remediation list. The part a
  non-technical decision-maker actually reads.
- **Print-ready audit report** (HTML → PDF) — cover, executive summary, regulation & OWASP coverage,
  findings with evidence, remediation, methodology, appendix. Client branding configurable.
- **Retest certificate** — a before/after delta with a `PASS` / `FAIL` stamp after remediation.
- **CI gate** — a GitHub Action that fails a build when a change introduces a new HIGH/CRITICAL
  finding (regression mode), turning a one-off audit into continuous protection.
- **Guard (continuous monitoring)** — scheduled re-runs that e-mail you the moment a change to your
  bot introduces a *new* vulnerability. A one-off audit becomes an ongoing safety net.

---

## Tech

**Engine:** Python 3.11+ · pydantic v2 · async runner · LLM-as-judge (Gemini / Anthropic) ·
deterministic canary detector · YAML attack packs · self-contained HTML/PDF reports.
**Frontend:** Next.js 16 · React 19 · Tailwind CSS v4 · TypeScript.

---

## Status

**Live — v1.0, open for audits.** The engine, marketing site, audit dashboard, Polish + industry
attack packs, single- and multi-turn probes, compliance mapping, OWASP LLM (2025) + Agentic (2026)
mapping, board summary + remediation fix-list, HTML/PDF audit reports, retest certificate, CI gate
and Guard continuous monitoring are built and working end-to-end against live models.

## Contact

Interested in an audit or a demo?

📧 **kontakt@kanari.pl** &nbsp;·&nbsp; 🌐 **[kanari.pl](https://kanari.pl)**

---

<sub>© 2026 TAKZEN. "Kanari", the logo and this documentation are proprietary. Screenshots show the
Polish-language product. Source code is not included in this repository.</sub>
