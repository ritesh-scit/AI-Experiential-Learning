# T40 – Resume Screener with Bias Check

**AI-Powered Tools · Mini project (30 marks) · MBA DSDA, SCIT Pune**

| | |
|---|---|
| Student | Ritesh |
| Number | 26030242053 |
| Task ID | T40 – Resume screener with bias check |
| Theme | C. AI text analytics |
| Roles screened | JD3 Financial Analyst, JD5 Product Manager – Fintech |
| AI tool used | Claude (claude.ai) with file upload and code execution |

---

## Repository contents

| File | What it is |
|---|---|
| `[MainAssessment]Resume_screener_with_bias_check.xlsx` | The working build. It is the provided dataset workbook with my outputs added as new sheets, plus the completed AI Use Log. |
| `[Report]AI-Assisted Resume Screening for Hiring Managers.docx` | The report (recommendation, verification, bias test, guidelines, limitations, reflection). |
| `README.md` | This guide. |

**Links**
- AI chat evidence (share link): `<paste chat share link here>`
- Report (online version): `<paste report link here>`

---

## Quick start for the assessor (about 5 minutes)

1. Open the workbook in Microsoft Excel. It opens on **Shortlist Summary**, which shows the result for each role.
2. **Test that the build works.** Go to **Scoring Prompt**, change cell **B15** (Shortlist cut-off, currently 60) to 55. Go back to **Shortlist Summary**: the counts, decisions and fairness ratios all update. Set it back to 60.
3. **Check accuracy.** Go to **Verification**, section B: 200 of 200 AI score sets are reproduced by independent Excel formulas.
4. **Check the bias test.** Go to **Bias Test**: 0 of 20 scores changed after the name/gender swap (result: PASS).
5. **Check the AI Use Log.** It has 17 entries (#2–#18), including 4 rejected outputs.

**Colour key used in all new sheets**
- **Blue text** = AI output (pasted from the scoring prompt).
- **Black text** = Excel formula.
- **Yellow cells** = settings you can change.

---

## Where to find evidence for each rubric criterion

| Criterion (marks) | Where to look | Key evidence |
|---|---|---|
| **1. Working build (8)** | *Scoring Prompt*, *Scored Shortlist*, *Shortlist Summary* | All 100 resumes scored for 2 roles = 200 pairs. Each has 4 component scores, a written reason and interview probes. Totals, decisions and ranks are live formulas. Cut-offs are editable cells. |
| **2. Correctness and verification (7)** | *Rule Check*, *Verification* | 200/200 rows match an independent formula re-computation. 20/20 reasons correct in a manual spot-check. 0 reasons mention tier, gender, career gap or the candidate's name. 6 errors found and fixed (Verification section E). |
| **3. Prompting and iteration (5)** | *Prompt Iterations*, *AI Use Log* | 4 prompt versions (v1 → v2 → v3 → v3.1) = 3 improvement rounds, each triggered by a measured failure. Rejected v1 outputs are kept word for word. The guidelines also went through 2 rounds. |
| **4. Business insight and recommendation (6)** | Report section 8, *Shortlist Summary* | 7 candidates shortlisted per role (12 people), 23 sent to recruiter review. Role-specific skills tests recommended. Tier/gap filters rejected with numbers. Estimated ~78% saving in screening time (assumption stated). |
| **5. Documentation and reflection (4)** | *AI Use Log*, *Guidelines*, report sections 10–11 | Complete AI Use Log with disclosure note. 12 fairness guidelines, each with evidence, owner and frequency. Limitations, responsible-AI notes and a personal reflection. |

---

## Guide to the workbook sheets

| Sheet | Purpose |
|---|---|
| **Task Brief** | Original brief and rubric (unchanged). |
| **Shortlist Summary** | Decision counts per role, top 20 candidates per role with reasons, gender ratios. Start here. |
| **Scored Shortlist** | All 200 resume–role pairs: component scores, total, decision, rank, partial credit, AI reason, interview probes. Filter column J. |
| **Scoring Prompt** | Final prompt (v3.1, exact text in 7 parts), decision cut-offs, and all rubric tables used by the formulas. |
| **Prompt Iterations** | v1 to v3.1: exact prompts, what failed with numbers, what changed. Also the rejected v1 outputs and the rejected first draft of the guidelines. |
| **Rule Check** | Independent formula re-computation of every AI score from the raw *Resumes* sheet (INDEX/MATCH, SEARCH, MID/FIND). |
| **Verification** | Data integrity checks, rule-check results, leakage check, 20-row manual spot-check, errors found and fixed. |
| **Bias Test** | Name/gender swap on 10 resumes × 2 roles, with the swapped resume text. |
| **Fairness Audit** | Selection rates and four-fifths ratios by gender, plus the proxy experiment (effect of tier and career-gap rules). |
| **Guidelines** | 12 guidelines for fair AI-assisted screening. |
| **AI Use Log** | Every prompt used, with outcome, change made and kept/rejected status. |
| **Resumes, Job Descriptions, Data Dictionary** | Original dataset (unchanged). |

---

## Headline results

| Result | JD3 Financial Analyst | JD5 PM – Fintech |
|---|---|---|
| Shortlist (interview) | 7 | 7 |
| Review by recruiter | 12 | 11 |
| Not shortlisted | 81 | 82 |
| Top candidate | CV051, score 73 | CV086, score 82 |
| Mean score: women / men | 44.9 / 45.0 | 43.2 / 43.1 |
| Gender ratio at shortlist | 0.81 | 0.37 (not significant, Fisher p = 0.26) |
| Gender ratio at shortlist + review | 0.98 | 0.92 |

- **Swap test:** 0 of 20 scores changed; 0 decisions changed.
- **Proxy experiment:** adding +5/−5 for institute tier and −5 for career gaps changed 23 of 200 decisions and halved the JD3 female shortlist rate (7.7% → 3.8%), even though gender was never an input. These rules are excluded from the final prompt.
- **JD5 gender ratio:** the low ratio at the shortlist line comes from two women scoring 59 against a man at 60. Both are first in the recruiter review queue. Scores were not adjusted by group.

---

## How the screening was done

1. The scoring prompt asks the AI for four component scores on a fixed 100-point rubric: qualification 25, experience 25, skills 40, achievement 10. It also asks for partial credit (from 5 written rules), a reason and interview probes.
2. The AI is told to ignore name, gender, age, religion, caste, region, family status, institute tier, career gaps and employer prestige.
3. Excel adds up the components and makes the decision. Shortlist needs a total of 60+ and at least 12 skill points. Review needs 55+ and at least 8 skill points.
4. Claude applied the prompt to all 200 pairs. To give every pair identical treatment, the rubric was run as a script in Claude's code-execution sandbox, reading the same resume text a chatbot would see.
5. Every AI number was then checked with independent Excel formulas (*Rule Check*).

---

## AI use disclosure

- Claude (claude.ai) was used to profile the data, score the 200 pairs, build the verification formulas and draft the report.
- Every number in the report was checked against live formulas in the workbook.
- AI Use Log entries #2–#3 are my own prompts. Entries #4–#18 are the step prompts run within the same chat session to build, test and fix the screener. The note at the bottom of the log explains this.
- Row 4 of the AI Use Log is the template example and was not part of this project.

## Responsible AI

- Only the synthetic dataset provided with the task was used. No real personal data was entered into any AI tool.
- Gender, institute tier and career gap are joined back only in *Fairness Audit*, after scoring, for audit purposes.

## Known limitations

- There is no gold-label sheet in the dataset. Accuracy is therefore measured as agreement with the rubric plus a manual spot-check, not against real hiring outcomes.
- The swap test is expected to pass because the screener is name-blind by design. It should be repeated in any free-form chatbot before that tool is used.
- Only gender could be tested. Caste, religion, region and age are not in the data.
- With 7 shortlisted per role, ratios move a lot with one candidate, so they are read together with a significance test.# T40 – Resume Screener with Bias Check

**AI-Powered Tools · Mini project (30 marks) · MBA DSDA, SCIT Pune**

| | |
|---|---|
| Student | Ritesh |
| Number | 26030242053 |
| Task ID | T40 – Resume screener with bias check |
| Theme | C. AI text analytics |
| Roles screened | JD3 Financial Analyst, JD5 Product Manager – Fintech |
| AI tool used | Claude (claude.ai) with file upload and code execution |

---

## Repository contents

| File | What it is |
|---|---|
| `T40_Resume_screener_with_bias_check_Ritesh.xlsx` | The working build. It is the provided dataset workbook with my outputs added as new sheets, plus the completed AI Use Log. |
| `T40_Report_Ritesh.pdf` | The report (recommendation, verification, bias test, guidelines, limitations, reflection). |
| `README.md` | This guide. |

**Links**
- AI chat evidence (share link): `<paste chat share link here>`
- Report (online version): `<paste report link here>`

---

## Quick start for the assessor (about 5 minutes)

1. Open the workbook in Microsoft Excel. It opens on **Shortlist Summary**, which shows the result for each role.
2. **Test that the build works.** Go to **Scoring Prompt**, change cell **B15** (Shortlist cut-off, currently 60) to 55. Go back to **Shortlist Summary**: the counts, decisions and fairness ratios all update. Set it back to 60.
3. **Check accuracy.** Go to **Verification**, section B: 200 of 200 AI score sets are reproduced by independent Excel formulas.
4. **Check the bias test.** Go to **Bias Test**: 0 of 20 scores changed after the name/gender swap (result: PASS).
5. **Check the AI Use Log.** It has 17 entries (#2–#18), including 4 rejected outputs.

**Colour key used in all new sheets**
- **Blue text** = AI output (pasted from the scoring prompt).
- **Black text** = Excel formula.
- **Yellow cells** = settings you can change.

---

## Where to find evidence for each rubric criterion

| Criterion (marks) | Where to look | Key evidence |
|---|---|---|
| **1. Working build (8)** | *Scoring Prompt*, *Scored Shortlist*, *Shortlist Summary* | All 100 resumes scored for 2 roles = 200 pairs. Each has 4 component scores, a written reason and interview probes. Totals, decisions and ranks are live formulas. Cut-offs are editable cells. |
| **2. Correctness and verification (7)** | *Rule Check*, *Verification* | 200/200 rows match an independent formula re-computation. 20/20 reasons correct in a manual spot-check. 0 reasons mention tier, gender, career gap or the candidate's name. 6 errors found and fixed (Verification section E). |
| **3. Prompting and iteration (5)** | *Prompt Iterations*, *AI Use Log* | 4 prompt versions (v1 → v2 → v3 → v3.1) = 3 improvement rounds, each triggered by a measured failure. Rejected v1 outputs are kept word for word. The guidelines also went through 2 rounds. |
| **4. Business insight and recommendation (6)** | Report section 8, *Shortlist Summary* | 7 candidates shortlisted per role (12 people), 23 sent to recruiter review. Role-specific skills tests recommended. Tier/gap filters rejected with numbers. Estimated ~78% saving in screening time (assumption stated). |
| **5. Documentation and reflection (4)** | *AI Use Log*, *Guidelines*, report sections 10–11 | Complete AI Use Log with disclosure note. 12 fairness guidelines, each with evidence, owner and frequency. Limitations, responsible-AI notes and a personal reflection. |

---

## Guide to the workbook sheets

| Sheet | Purpose |
|---|---|
| **Task Brief** | Original brief and rubric (unchanged). |
| **Shortlist Summary** | Decision counts per role, top 20 candidates per role with reasons, gender ratios. Start here. |
| **Scored Shortlist** | All 200 resume–role pairs: component scores, total, decision, rank, partial credit, AI reason, interview probes. Filter column J. |
| **Scoring Prompt** | Final prompt (v3.1, exact text in 7 parts), decision cut-offs, and all rubric tables used by the formulas. |
| **Prompt Iterations** | v1 to v3.1: exact prompts, what failed with numbers, what changed. Also the rejected v1 outputs and the rejected first draft of the guidelines. |
| **Rule Check** | Independent formula re-computation of every AI score from the raw *Resumes* sheet (INDEX/MATCH, SEARCH, MID/FIND). |
| **Verification** | Data integrity checks, rule-check results, leakage check, 20-row manual spot-check, errors found and fixed. |
| **Bias Test** | Name/gender swap on 10 resumes × 2 roles, with the swapped resume text. |
| **Fairness Audit** | Selection rates and four-fifths ratios by gender, plus the proxy experiment (effect of tier and career-gap rules). |
| **Guidelines** | 12 guidelines for fair AI-assisted screening. |
| **AI Use Log** | Every prompt used, with outcome, change made and kept/rejected status. |
| **Resumes, Job Descriptions, Data Dictionary** | Original dataset (unchanged). |

---

## Headline results

| Result | JD3 Financial Analyst | JD5 PM – Fintech |
|---|---|---|
| Shortlist (interview) | 7 | 7 |
| Review by recruiter | 12 | 11 |
| Not shortlisted | 81 | 82 |
| Top candidate | CV051, score 73 | CV086, score 82 |
| Mean score: women / men | 44.9 / 45.0 | 43.2 / 43.1 |
| Gender ratio at shortlist | 0.81 | 0.37 (not significant, Fisher p = 0.26) |
| Gender ratio at shortlist + review | 0.98 | 0.92 |

- **Swap test:** 0 of 20 scores changed; 0 decisions changed.
- **Proxy experiment:** adding +5/−5 for institute tier and −5 for career gaps changed 23 of 200 decisions and halved the JD3 female shortlist rate (7.7% → 3.8%), even though gender was never an input. These rules are excluded from the final prompt.
- **JD5 gender ratio:** the low ratio at the shortlist line comes from two women scoring 59 against a man at 60. Both are first in the recruiter review queue. Scores were not adjusted by group.

---

## How the screening was done

1. The scoring prompt asks the AI for four component scores on a fixed 100-point rubric: qualification 25, experience 25, skills 40, achievement 10. It also asks for partial credit (from 5 written rules), a reason and interview probes.
2. The AI is told to ignore name, gender, age, religion, caste, region, family status, institute tier, career gaps and employer prestige.
3. Excel adds up the components and makes the decision. Shortlist needs a total of 60+ and at least 12 skill points. Review needs 55+ and at least 8 skill points.
4. Claude applied the prompt to all 200 pairs. To give every pair identical treatment, the rubric was run as a script in Claude's code-execution sandbox, reading the same resume text a chatbot would see.
5. Every AI number was then checked with independent Excel formulas (*Rule Check*).

---

## AI use disclosure

- Claude (claude.ai) was used to profile the data, score the 200 pairs, build the verification formulas and draft the report.
- Every number in the report was checked against live formulas in the workbook.
- AI Use Log entries #2–#3 are my own prompts. Entries #4–#18 are the step prompts run within the same chat session to build, test and fix the screener. The note at the bottom of the log explains this.
- Row 4 of the AI Use Log is the template example and was not part of this project.

## Responsible AI

- Only the synthetic dataset provided with the task was used. No real personal data was entered into any AI tool.
- Gender, institute tier and career gap are joined back only in *Fairness Audit*, after scoring, for audit purposes.

## Known limitations

- There is no gold-label sheet in the dataset. Accuracy is therefore measured as agreement with the rubric plus a manual spot-check, not against real hiring outcomes.
- The swap test is expected to pass because the screener is name-blind by design. It should be repeated in any free-form chatbot before that tool is used.
- Only gender could be tested. Caste, religion, region and age are not in the data.
- With 7 shortlisted per role, ratios move a lot with one candidate, so they are read together with a significance test.
