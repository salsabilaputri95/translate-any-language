# AGENTS.md — Document Translation Guidelines

This document is the mandatory guideline for any AI Agent translating documents in this project. Every translation task **must** follow all the rules, workflow, and provisions below without exception, unless the user explicitly requests otherwise.

---

## 0. Scope

- These guidelines apply to **every translation request** for documents in this project, especially Markdown (`.md`) documents.
- Source documents are usually located in the `docs/` folder, but these rules apply to documents anywhere in the project.
- This `AGENTS.md` file **must not be translated or modified** as part of a translation task.
- If the user does not specify a target language, **ask first**. Do not guess.

### Quick Definitions

| Term | Meaning |
| --- | --- |
| **Source document** | The original file to be translated. It is read-only. |
| **Target document** | The new file containing the translation. |
| **Source language** | The language used in the source document. |
| **Target language** | The language the user requests for the translation. |
| **Protected element** | A part of the document that must be copied exactly, without translation (see [Section 7](#7-additional-rules)). |

---

## 1. Format Consistency

The structure of the target document must be **identical** to the source document. Only natural-language text changes.

- Preserve the **number, order, and level** of all headings and subheadings (`#` through `######`).
- Preserve tables: number of columns, number of rows, separator rows (`| --- |`), and column alignment (`:---`, `:---:`, `---:`).
- Preserve labels, numbering (`1.`, `1)`, `a.`, `i.`), and the original numbering style.
- Preserve symbols, emoji, icons, and special characters (`→`, `©`, `✓`, `⚠️`, etc.).
- Preserve the bullet type (`-`, `*`, `+`) and its indentation level.
- Preserve blank lines, horizontal rules (`---`, `***`), and line breaks in the same positions.
- Adjust punctuation to target-language conventions **only when** required for grammatical correctness (for example, quotation marks or the space before punctuation in French). Punctuation that is part of syntax or structure must not be changed.

---

## 2. Translation Accuracy

- Preserve the **meaning, context, tone, and level of formality** of the source document.
- **Do not add** information, explanations, examples, or notes that are not in the source document.
- **Do not remove** any sentence, paragraph, point, or detail, including sections that appear repetitive.
- Keep all **numbers, units, dates, percentages, and data** exactly as in the original. Do not convert units or currencies.
- Translate by meaning, not word for word. Translated sentences must read naturally in the target language without shifting the meaning.
- Translate idioms and expressions into equivalent expressions in the target language. If no suitable equivalent exists, use a meaning-based translation and flag it for review (see [Section 7](#7-additional-rules)).

---

## 3. Grammar & Spelling Check

Every translation must be checked for:

- **Grammar**: subject–verb agreement, tense, singular/plural forms, and sentence structure.
- **Spelling**: according to the standard conventions of the target language. For Indonesian, use **EYD Edisi V** and **KBBI**. For English, use one variant consistently (*US* or *UK*), following the source document's variant if any, or *US English* if unspecified.
- **Punctuation**: placement of commas, periods, colons, quotation marks, and hyphens according to target-language conventions.
- **Sentence structure**: no sentences that are confusing, overly long, or rigidly follow the source-language word order.
- **Fluency**: the result must read naturally to native speakers of the target language.

---

## 4. Terminology

- Use **one consistent equivalent** for each term throughout the document, and across all project documents translated into the same language.
- Before translating, build a **working glossary** of technical and academic terms with their equivalents. Use this glossary consistently throughout the translation.
- If the project already has a glossary file or previous translations in the same target language, **follow the terms already used** there.
- Technical terms that are commonly left untranslated in the target language (e.g., *framework*, *API*, *deployment*, *machine learning*) may be kept in their original language. If kept, italicize them where target-language conventions require it (e.g., Indonesian), and do so consistently.
- If a term needs clarification, use the pattern **equivalent (original term)** on the **first occurrence only**, for example: *pembelajaran mesin (machine learning)*, then use the same equivalent thereafter. Do not add any other explanation.
- Abbreviations and acronyms (e.g., `API`, `HTTP`, `ISO`) are not translated.

---

## 5. Markdown Preservation

All Markdown syntax must remain **valid** and produce the same rendering as the source document.

| Element | Rule |
| --- | --- |
| Heading (`#`) | The `#` symbols and level stay the same. Translate the heading text. |
| Bold / Italic (`**text**`, `*text*`, `_text_`) | Markers stay the same. Translate the text inside; markers must still wrap the phrase with the equivalent meaning. |
| Strikethrough (`~~text~~`) | Markers stay the same; text is translated. |
| Link (`[text](url "title")`) | Translate the **link text** and **title**. **The URL must not be changed**. |
| Reference link (`[text][ref]` and `[ref]: url`) | The `ref` label and URL stay the same. Translate the link text only. |
| Image (`![alt](path)`) | Translate the `alt` text. The image path/URL stays the same. |
| Inline code (`` `code` ``) | **Not translated**. Copy exactly. |
| Code block (```` ``` ````, `~~~`, or indentation) | **The entire content is not translated**, including comments and strings inside the code. The language identifier (e.g., `python`) stays the same. |
| Diagram (e.g., `mermaid` block) | Treated like a code block: **not translated**, unless the user requests it. |
| Table | Structure stays the same. Translate natural-language cell content. Ensure each row has the same number of `\|`. |
| Blockquote (`>`) | The `>` marker and nesting level stay the same. Text is translated. |
| Alert/Admonition (`> [!NOTE]`, `> [!WARNING]`, etc.) | The keyword inside `[! ]` is **not translated**. The content is translated. |
| Task list (`- [ ]`, `- [x]`) | Checkbox markers stay the same. Text is translated. |
| Footnote (`[^1]`) | The footnote label stays the same. The footnote content is translated. |
| YAML front matter (`---` at the top of the file) | **Keys are not translated**. Only human-readable text values (e.g., `title`, `description`) are translated. Technical values (dates, slugs, tags, paths, booleans) stay the same. |
| HTML inside Markdown | Tags, attributes, and technical attribute values stay the same. Only reader-facing text (and `alt`/`title` attributes) is translated. |
| HTML comment (`<!-- ... -->`) | Not translated, unless the user requests it. |
| Math (`$...$`, `$$...$$`) | **Not translated**. Copy exactly. |
| Escaped characters (`\*`, `\_`, `\|`) | Keep as is. |

### Internal Anchor Links

Links to headings within the same document (e.g., `[see](#installation)`) depend on the heading text. If the target heading is translated, **update the anchor** to match the slug of the translated heading so the link keeps working. This is the only exception to the "URLs must not be changed" rule, and every anchor change must be recorded in the final report.

---

## 6. Quality Assurance

After translation is complete, compare the source and target documents using the checklist below. Every item must pass before the task is considered complete.

### 6.1 Completeness and Structure Check

The count of the following elements in the target document must **exactly match** the source document:

- [ ] Headings per level (`#`, `##`, `###`, etc.)
- [ ] Paragraphs
- [ ] List items (bulleted and numbered), including indentation levels
- [ ] Tables, with the number of rows and columns in each table
- [ ] Code blocks and inline code (content identical byte for byte)
- [ ] Links and images (identical URLs/paths)
- [ ] Blockquotes, alerts, footnotes, and horizontal rules

### 6.2 Meaning Check

- [ ] No sentence, point, or table cell is missing.
- [ ] No added information that is not in the source.
- [ ] Numbers, dates, units, and data are identical to the source.
- [ ] The meaning of each paragraph is equivalent to its source paragraph.

### 6.3 Language and Terminology Check

- [ ] Grammar, spelling, and punctuation comply with [Section 3](#3-grammar--spelling-check).
- [ ] Every term in the working glossary is used consistently.
- [ ] No source-language text is unintentionally left behind (other than protected elements).

### 6.4 Technical Check

- [ ] Markdown syntax is valid and renders equivalently to the source document.
- [ ] Internal anchor links work.
- [ ] File encoding is **UTF-8**, with line endings matching the source document.

> [!TIP]
> For check 6.1, the agent may count elements in both files (e.g., by searching for patterns such as `^#`, `^\s*[-*+] `, `^\s*\d+\. `, `^\|`, `` ^``` ``) for a more accurate comparison. This is only a verification aid; do not add script files to the project.

---

## Translation Workflow

Follow these steps **in order** for every document.

### Step 1 — Identify

- Determine the **source language** from the document content.
- Confirm the **target language** from the user's request. If unclear, ask.
- Determine the **document format** (Markdown, Markdown with front matter, MDX, etc.) and the file location.

### Step 2 — Read and Analyze

- Read the **entire** source document from start to finish before you begin translating.
- Understand its topic, purpose, audience, tone, and level of formality.

### Step 3 — Identify Structure and Special Elements

- Map the headings, structure, tables, lists, and other Markdown elements.
- Mark all **protected elements** (code, URLs, variables, names, etc.).
- Build a **working glossary** of technical and academic terms (see [Section 4](#4-terminology)).
- Note any terms or sentences that may be ambiguous.

### Step 4 — Translate Incrementally

- Translate section by section (e.g., per heading) in the order of the source document.
- Do not change the structure, order, or layout of the document.
- For long documents, make sure the **entire** content is translated. Do not truncate, summarize, or write placeholders such as "(and so on)" or "...rest of the document...".

### Step 5 — Check the Language

- Check grammar, spelling, punctuation, and fluency according to [Section 3](#3-grammar--spelling-check).
- Make sure all terms match the working glossary.

### Step 6 — Compare with the Source Document

- Run the full checklist in [Section 6](#6-quality-assurance).
- Detect any parts that are missing, changed, added, or inaccurate.

### Step 7 — Revise

- Fix every finding from Steps 5 and 6.
- Repeat Steps 5–6 until **every** checklist item passes.

### Step 8 — Save

- Save the target document as a **new file**, with the same format and extension as the source document.
- Use the following naming convention, unless the user specifies a different name or location:

  ````text
  <file-name>.<language-code>.<extension>
  ````

  Language codes follow the **ISO 639-1** standard (e.g., `en`, `id`, `ja`, `ar`), or BCP 47 codes when a variant must be distinguished (e.g., `pt-BR`, `zh-CN`).

  | Source document | Target language | Target document |
  | --- | --- | --- |
  | `docs/panduan.md` | English | `docs/panduan.en.md` |
  | `docs/guide.md` | Indonesian | `docs/guide.id.md` |
  | `docs/api/intro.md` | Japanese | `docs/api/intro.ja.md` |

- Save the target document in the **same folder** as the source document so the folder structure stays consistent.
- If a target file with that name **already exists**, do not overwrite it without the user's confirmation.
- Use **UTF-8** encoding.

### Step 9 — Report

When finished, give the user a short report containing:

1. The source document, source language, target language, and target document location.
2. QA checklist results (source vs. target element counts).
3. A list of key terms and the equivalents used.
4. A list of sections flagged for review (if any), with the reasons.
5. A list of updated internal anchor links (if any).

---

## 7. Additional Rules

### 7.1 Elements That Must Not Be Translated

Copy the following elements exactly, without changes:

- Names of people, organizations, products, brands, projects, and other proper nouns.
- Code, commands, function names, classes, variables, parameters, and constants.
- URLs, email addresses, file paths, file names, and folder names.
- Technical identifiers: versions (`v2.1.0`), IDs, configuration keys, package names, tags, and error codes.
- Terms the source author intentionally wrote in their original language.
- Titles of works (books, articles, standards) that have no official translation.

### 7.2 Source File Protection

- **Do not modify, move, rename, or delete** the source document under any circumstances.
- Always create the target document as a **separate file** (see [Step 8](#step-8--save)).
- Do not modify other project documents that are not part of the translation request.

### 7.3 No Summarizing or Interpreting

- **Do not summarize**, simplify, or freely paraphrase the content.
- **Do not interpret**, comment on, correct the content, or add opinions. If the source document contains factual errors or typos, translate them as they are and mention them in the final report.

### 7.4 Handling Ambiguous Terms

- Choose the translation that best fits the document's **contextual meaning**.
- Flag it with an HTML comment **immediately after** the related sentence or element. HTML comments are not displayed when rendered, so they do not break the document's formatting:

  ````markdown
  Sistem akan melakukan *rollback* jika proses gagal. <!-- REVIEW: "rollback" dipertahankan; alternatif padanan: "pemulihan ke kondisi sebelumnya". -->
  ````

- Do not place `REVIEW` comments inside code blocks, inline code, URLs, or table cells if doing so could break the syntax. In those cases, include the finding only in the final report.
- List every `REVIEW` flag in the final report (see [Step 9](#step-9--report)).

### 7.5 Ongoing Consistency

- Apply all rules in this document consistently to **every** subsequent translation.
- When translating a new document into a language that has been used before, check previous translations and **use the same terminology**.

---

## Summary of Key Rules

| # | Rule | Essence |
| --- | --- | --- |
| 1 | Format Consistency | The target document's structure is identical to the source. |
| 2 | Translation Accuracy | Meaning is preserved; nothing is added or removed. |
| 3 | Grammar & Spelling Check | The target language is correct, standard, and fluent. |
| 4 | Terminology | One term, one equivalent, consistent across the project. |
| 5 | Markdown Preservation | Valid syntax; code, URLs, and technical elements are unchanged. |
| 6 | Quality Assurance | Compare source and target before declaring completion. |
| 7 | Additional Rules | Source files are untouched; no summarizing; flag ambiguity. |
