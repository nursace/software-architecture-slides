# Software Architecture / Архитектура ПО — Course Plan (3–4 months)

**Audience:** college students, ages 16–18 (originally Russian/Kyrgyz speakers)  
**Materials language:** **English** (slides and labs in English for a RU/KY audience; technical terms may need an occasional bilingual glossary later)  
**Pace:** 1 lecture (80 min) + 1 practice (80 min) per week  
**Length:** **16 weeks** (~4 months). A **14-week** cut is noted at the end.  
**Tone:** practical and intuition-first; diagrams and trade-offs over heavy formal methods / deep math.  
**Stack (suggested, open):** diagramming (draw.io *or* Mermaid — lecturer choice) · optional small code labs in a language the cohort already knows · case-study walkthroughs of familiar apps

---

## Learning goals (end of course)

Students should be able to:

1. Explain what **software architecture** is and how it differs from detailed design and code  
2. Name common **quality attributes** (performance, reliability, security, maintainability, usability) and relate them to design choices  
3. Compare **monolith vs modular** systems and sketch **client–server**, **layered**, and high-level **MVC/MVP** styles  
4. Describe what an **API** is for and sketch simple request/response flows  
5. Talk about **data stores** at a glance (files vs relational DB vs “cache” idea) without deep DB theory  
6. Draw a **simple architecture diagram** (C4-lite: context + containers/components) that a teammate can understand  
7. Argue **trade-offs** (“good for X, costly for Y”) instead of “the best architecture”  
8. Complete a small **architecture mini-project** (problem → qualities → sketch → short rationale)  
9. Discuss **reliability, responsibility, and ethics** (what breaks when systems fail; who is affected)

**Out of scope (for this age / duration):** formal architecture description languages, ATAM-style rigorous evaluation math, microservices orchestration depth, distributed-systems proofs, enterprise TOGAF/Zachman frameworks, deep UML modeling courses.

---

## Weekly rhythm

| Block | Time | Role |
|-------|------|------|
| **Lecture** | 80 min | Concepts, live diagrams, short quizzes / polls, mini case studies |
| **Practice** | 80 min | Guided sketching, pair critique, checklists, project checkpoints |

Each practice ends with a **done checklist** (3–5 concrete tasks) so progress is visible.

---

## Module map

| Weeks | Module | Theme |
|------:|--------|--------|
| 1–2 | A | What architecture is; quality attributes |
| 3–5 | B | Building blocks: monolith/modular, client–server, layers |
| 6–8 | C | Patterns & interfaces: MVC/MVP, APIs, data stores |
| 9–11 | D | Diagrams, deployment basics, trade-offs |
| 12–13 | E | Case studies + ethics / reliability |
| 14–15 | F | Mini-project |
| 16 | G | Showcase + wrap-up |

---

## Week-by-week plan

### Module A — Foundations

#### Week 1 — What is software architecture?
**Lecture**
- Architecture vs design vs code (building / city metaphor; “structure that is hard to change later”)
- What this course *will* and *won’t* cover
- Stakeholders: who cares about architecture (users, developers, operators, business)
- Everyday systems as examples (messaging app, school portal, online shop)

**Practice**
- Pick a familiar app; list “parts” and “connections” in plain language
- Sort statements: architecture / design / implementation
- Course norms: English materials; keep a personal glossary of key terms

**Keywords:** architecture, design, code, stakeholders

---

#### Week 2 — Quality attributes (what “good” means)
**Lecture**
- Quality attributes: performance, reliability, security, maintainability, usability, scalability (intuition + examples)
- Qualities conflict (fast vs cheap; secure vs convenient)
- Scenarios in plain language (“when 1000 students open the portal at once…”)
- Non-goals: not everything needs to be “enterprise grade”

**Practice**
- For a given product brief, pick top 3 qualities and justify
- Rewrite vague goals (“make it fast”) into checkable scenarios
- Peer swap: does your partner’s scenario make sense?

**Keywords:** quality attributes, scenarios, trade-offs (intro)

---

### Module B — Styles & structures

#### Week 3 — Monolith vs modular systems
**Lecture**
- Monolith: one deployable unit; when it is fine
- Modular monolith: modules with clearer boundaries inside one app
- “Big ball of mud” as anti-pattern (recognize, don’t shame)
- Change impact: “touch one place vs many”

**Practice**
- Split a messy feature list into modules (names + responsibilities)
- Mark likely “pain points” if everything is one blob
- Short reflection: when would you *keep* a simple monolith?

**Keywords:** monolith, modularity, cohesion, coupling (plain language)

---

#### Week 4 — Client–server & the network in the picture
**Lecture**
- Client, server, request/response
- Thin vs thick client (intuition)
- Latency, offline, “server is down” as architectural concerns
- Multi-tier idea without jargon overload

**Practice**
- Draw a client–server sketch for a chat or homework app
- Label: who holds data? who does business rules?
- Failure story: what does the user see if the server fails?

**Keywords:** client–server, request/response, latency

---

#### Week 5 — Layered architecture
**Lecture**
- Layers: presentation → application/logic → data (classic picture)
- Why layers help (change UI without rewriting storage)
- Leaky layers and “shortcuts that become traps”
- Layered + client–server together (typical web app sketch)

**Practice**
- Assign features to layers for a small system
- Find a “layer violation” in a provided bad sketch; propose a fix
- Done checklist: named layers + 5 components placed

**Keywords:** layered architecture, presentation, domain/logic, data layer

---

### Module C — Patterns, APIs, data

#### Week 6 — MVC / MVP at a high level
**Lecture**
- MVC as a way to separate UI, data, and “glue” (pictures, not framework deep-dives)
- MVP / similar ideas as “same family” (roles, not dogma)
- Why UI patterns matter for testability and team work
- Map MVC onto a layered sketch (don’t force a perfect fit)

**Practice**
- Label Model / View / Controller (or Presenter) on a simple screen flow
- Redesign a “god class UI” sketch into MVC-ish roles
- Optional: peek at one framework folder structure *as archaeology*, not coding marathon

**Keywords:** MVC, MVP, separation of concerns

---

#### Week 7 — APIs: talking between parts
**Lecture**
- API as a contract (“what you can ask for, what you get back”)
- Public vs internal APIs; versioning idea (“don’t break callers”)
- REST-ish HTTP at a glance (resources, GET/POST intuition) — no protocol deep dive
- Errors, auth as architecture concerns (who is allowed?)

**Practice**
- Design a tiny API for a library or cafeteria app (5 endpoints in words + example payloads)
- Partner plays “client”: which calls are unclear?
- Break-the-contract game: change a response shape and discuss impact

**Keywords:** API, contract, HTTP (intro), versioning

---

#### Week 8 — Data stores at a glance
**Lecture**
- Where state lives: memory, files, databases
- Relational DB idea: tables + relations (intuition only)
- Cache / “fast copy” idea; consistency in plain words
- Choosing storage from quality attributes (not from fashion)

**Practice**
- For a system, decide: file vs DB vs “just keep in memory” (and why)
- Sketch entities for a simple domain (students, courses, enrollments)
- Discuss: what happens if two users update the same record?

**Keywords:** data store, database (intro), cache, consistency (intro)

---

### Module D — Diagrams, deployment, decisions

#### Week 9 — Diagrams (C4-lite / simple component views)
**Lecture**
- Why diagrams exist: shared mental model
- C4-lite: Context → Containers → Components (stop before code-level class soup)
- What to leave out; legend and naming discipline
- Anti-patterns: wallpaper diagrams nobody reads

**Practice**
- Draw Context + Container for a chosen system (paper or tool)
- Peer review: can a stranger explain the system from your diagram?
- Standardize symbols as a class (boxes, arrows, trust boundaries)

**Keywords:** C4, context diagram, container, component

---

#### Week 10 — Deployment basics
**Lecture**
- Running software: laptop vs server vs “cloud” as someone else’s computers
- Environments: development / test / production (why separate)
- Config, secrets, and “it works on my machine”
- Simple hosting picture: web app + database

**Practice**
- Annotate last week’s diagram with *where* each part runs
- Write a 5-line “deploy checklist” for a toy app
- Failure drill: disk full / DB unreachable — what do we monitor?

**Keywords:** deployment, environments, hosting, configuration

---

#### Week 11 — Trade-offs & architectural decisions
**Lecture**
- No free lunch: every choice has costs
- Decision records (light ADR idea): context, options, decision, consequences
- Reversible vs hard-to-reverse decisions
- “Good enough” architecture for school projects vs production

**Practice**
- Mini ADR: pick between monolith vs split services *for a given brief*
- Debate pairs: one argues for Option A, one for B; class votes with reasons
- Update diagrams to reflect the decision

**Keywords:** trade-offs, ADR, decision making

---

### Module E — Cases & responsibility

#### Week 12 — Case study lab (familiar systems)
**Lecture**
- Walkthrough of 1–2 public/familiar systems (e.g. messaging, e-commerce, school LMS) at architecture level
- Spot quality attributes and styles we already named
- What would you change if users grew 10×?

**Practice**
- Team case brief: reverse-engineer a plausible architecture from a product’s public behavior
- Produce Context + Container + top 3 risks
- Gallery walk: sticky-note feedback

**Keywords:** case study, reverse engineering (architecture)

---

#### Week 13 — Reliability, ethics, and responsible architecture
**Lecture**
- Reliability: failure is normal; graceful degradation
- Security & privacy as architectural (data location, access, logging)
- Ethics: dark patterns, surveillance, accessibility, who gets locked out when systems fail
- When *not* to add complexity

**Practice**
- “What could go wrong?” critique on a case diagram
- Write one mitigation per high risk (backup, auth, rate limits — conceptual)
- Short ethics memo (½ page): affected users + your design stance

**Keywords:** reliability, security, privacy, ethics

---

### Module F — Mini-project

#### Week 14 — Mini-project kickoff
**Lecture**
- Project brief: propose architecture for a small but real-feeling product
- Deliverables: quality scenarios, C4-lite diagrams, ADR (1–2 decisions), short rationale
- Team roles optional; individual OK

**Practice**
- Problem statement + target users + top qualities
- First Context diagram + module/container candidates
- Lecturer checkpoint sign-off

**Keywords:** project workflow, proposal

---

#### Week 15 — Mini-project studio
**Lecture**
- Workshop: common diagram mistakes; strengthening trade-off write-ups
- Optional guest / alumni “how we sketch at work” (if available)
- Rehearsal tips for Week 16 talks

**Practice**
- Complete Container/Component views; finish ADRs
- Peer critique with rubric (clarity, qualities, trade-offs)
- Polish ethics/reliability paragraph

**Keywords:** studio, peer review

---

### Module G — Close

#### Week 16 — Showcase & wrap-up
**Lecture**
- Student lightning talks (diagram + one hard decision)
- Map of what we learned; paths next (backend courses, databases, DevOps intro, security)
- Honest careers note: architecture is a skill grown with experience

**Practice**
- Finalize packet: diagrams + ADRs + 1-page summary
- Rubric self-check; celebrate clarity over buzzwords

**Keywords:** portfolio piece, reflection

---

## Suggested mini-project arc

Students (solo or pairs) architect **one** small system end-to-end at the sketching level, for example:

- Campus event board / club signup  
- Mini online shop or cafeteria ordering  
- Study-group matcher / tutoring scheduler  
- Simple library / inventory app  

**Arc across weeks:**

| Phase | Weeks | Outcome |
|-------|------:|---------|
| Qualities & problem | 2, 14 | Scenarios + problem statement |
| Style & modules | 3–5, 14 | Monolith/modular + layers choice |
| Interfaces & data | 6–8, 15 | API sketch + data-store choice |
| Diagrams & deploy | 9–10, 15 | C4-lite + where it runs |
| Decisions & ethics | 11–13, 15 | ADRs + risk/ethics note |
| Showcase | 16 | Talk + final packet |

Code is **optional**; architecture clarity is graded first.

---

## Suggested assessment (light)

| Item | When | Weight (example) |
|------|------|------------------|
| Practice sketches / checklists | weekly | 40% |
| Two short quizzes (concepts + reading diagrams) | ~Wk 7 & 12 | 20% |
| Mini-project packet + talk | Wk 14–16 | 30% |
| Participation / peer feedback | ongoing | 10% |

---

## Prerequisites

- Comfortable using a computer (files, browser, basic typing)
- Some prior programming exposure helpful (variables, functions, “an app has parts”) — **not** assumed expert
- No prior formal architecture or UML course required
- English reading for slides; lecturer may clarify terms in RU/KY as needed

---

## Diagram & formality policy (explicit)

| Allowed | Avoid |
|---------|--------|
| Boxes-and-arrows with clear names | Formal ADL / heavy UML certification tracks |
| C4-lite (context → containers → components) | Class diagrams for every entity |
| Quality scenarios in sentences | Quantitative queueing theory |
| One-page ADRs | Enterprise framework ceremony |
| Trade-off tables | “Always microservices” dogma |

Show a pattern name only if students can redraw it from memory in 2 minutes.

---

## 14-week compression (if you need ~3.5 months)

Merge / drop:

- Fold **Week 6** MVC into Week 5 practice (layers + UI separation together)  
- Merge **Week 10** deployment into Week 9 (annotate diagrams with runtime)  
- Shorten ethics to half of Week 13; keep case study; project still Weeks 14–15 (renumber) or 13–14  

Keep: architecture vs design, qualities, monolith/modular, client–server, layers, APIs, data stores glance, C4-lite, trade-offs, project, ethics bite.

---

## Proposed Beamer lecture series (after you approve this plan)

Files would live under:

`/cursor/stores/bc-d98d1767-292f-493b-b2bd-02f918cc25e2/docs/software-architecture-lectures/`

Suggested deck IDs (1:1 with lecture weeks), e.g.:

| ID | Title |
|----|--------|
| 01 | What is software architecture? |
| 02 | Quality attributes |
| 03 | Monolith vs modular |
| 04 | Client–server |
| 05 | Layered architecture |
| 06 | MVC / MVP (high level) |
| 07 | APIs & contracts |
| 08 | Data stores at a glance |
| 09 | Diagrams (C4-lite) |
| 10 | Deployment basics |
| 11 | Trade-offs & decisions |
| 12 | Case studies |
| 13 | Reliability, ethics & responsibility |
| 14 | Project workshop |
| 15 | Project studio |
| 16 | Showcase & wrap-up |

Practice materials can follow as lab sheets or sketch templates in a `practices/` subfolder later. **Plan first — no Beamer yet.**

---

## Decisions for you (please confirm)

1. **16 weeks** as default, or **14-week** cut?  
2. Diagramming tool: **draw.io / diagrams.net**, **Mermaid** (in Markdown), paper-first, or mix?  
3. Optional code labs: **none**, **light** (read existing small projects), or **build a tiny layered demo** — and in which language (Java / Python / JS)?  
4. Case-study apps: any local/familiar products you prefer (or avoid)?  
5. Course name on slides: **“Software Architecture”**, **“Архитектура ПО”**, or bilingual title?  
6. After approval: generate **Beamer `.tex` for weeks 1–4 first**, or wait?

This plan is the source of truth until you ask for changes or for lecture generation to start.
