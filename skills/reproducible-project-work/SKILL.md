---
name: reproducible-project-work
description: Reproducible execution workflow for file-based coding, data analysis, scientific analysis, reports, figures, pipelines, and research artifacts. Use when Codex needs to create or modify scripts, analyze datasets, generate figures, update reports, manage packages or environments, run downstream analyses, log operations, preserve session information, set random seeds, or maintain project memory.
---

# Reproducible Project Work

Make file-based work reproducible by default. Prefer scripts, explicit directories, logged operations, and refreshable outputs over ad hoc manual steps.

## Project Layout

- Create a designated task folder in the current directory or user-designated directory unless the existing project structure already provides a better location.
- Use clear subfolders when they fit the task: `data/`, `scripts/`, `results/`, `figures/`, `reports/`, `logs/`, and `env/`.
- Keep generated outputs separate from raw inputs. Do not overwrite user-provided source files unless explicitly asked.
- Maintain a `memory.md` file in the task folder. Record durable project context, decisions, assumptions, file meanings, unresolved issues, and next steps. Update it when important state changes.

## Scripts And Execution

- Write scripts for repeatable tasks instead of relying only on shell history or notebook state.
- Keep scripts in `scripts/`, name them by function, and execute them to produce the requested outputs.
- Make scripts runnable from a clean shell where practical. Include relative paths or configurable input/output paths.
- Add concise but sufficient comments, section headers, and function/docstring annotations in R, Python, and other programming-language scripts so another person can understand the purpose, inputs, outputs, assumptions, and non-obvious logic without reading the whole workflow line by line.
- Set and record random seeds for stochastic work. Make the seed visible in scripts, logs, and reports.
- Before finalizing, rerun or smoke-test the main script or workflow target, inspect outputs for obvious failure, and mention any command that could not be run.

## Environments And Packages

- Resolve missing packages, version conflicts, and runtime incompatibilities proactively.
- Prefer project-local or named conda environments for nontrivial scientific or analytical work. Use existing project environment files when present.
- Record package installs, version choices, and environment changes in `logs/` and environment files when possible.
- For R work, save `sessionInfo()` or equivalent package/runtime metadata. For Python, record Python version and key package versions.

## Dependency Refresh

- Update downstream analyses, reports, summaries, tables, and figures when input or upstream files change.
- Use explicit dependency tracking when the project is complex enough: Makefile, Snakemake, Nextflow, Quarto/R Markdown dependencies, or a simple scripted manifest.
- Prefer one command that rebuilds the relevant outputs. Document that command in `memory.md` or the task log.

## Logs And Outputs

- Record operations in log files under `logs/`. Include commands run, timestamps when practical, errors, fixes, input paths, output paths, and environment changes.
- Save figures as PDF by default when publication/report quality matters.
- Ensure figure text is readable, aspect ratios are appropriate, labels are not clipped, legends are legible, and plots remain interpretable in grayscale when relevant.
- Keep reports connected to their generating scripts so they can be regenerated after upstream changes.
