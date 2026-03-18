# CLAUDE.md — AI Assistant Guide for `training`

## Repository Overview

This is a **DC/OS and container training materials repository** containing hands-on lab guides, configuration examples, and exercises from multiple conference workshops (2015–2016). It is a purely documentation-focused repo with no application code, build system, or automated tests.

## Repository Structure

```
training/
├── README.md                          # Master index linking all training events
├── CLAUDE.md                          # This file
├── .gitignore                         # Ignores IntelliJ .idea/ directories
├── dcos-bootcamp-04-2016/             # April 2016 — Mesosphere HQ bootcamp
│   ├── docker/                        # Container fundamentals
│   ├── dcos/                          # DC/OS + Marathon JSON app specs
│   ├── ci-cd/                         # CI/CD practices
│   └── big-data/                      # Big Data on DC/OS
├── velocity-training-06-2016/         # June 2016 — Velocity Santa Clara
│   ├── container101/                  # Container fundamentals
│   ├── containerops/                  # Marathon JSON app specs (nginx, mattermost, etc.)
│   ├── monitoring/                    # Prometheus & Grafana configs
│   ├── ci-cd/                         # CI/CD workflows
│   └── troubleshooting/               # Debugging techniques
├── velocity-training-09-2016/         # September 2016 — Velocity NYC (most complete)
│   ├── docker-101.md … docker-102.md  # Docker fundamentals + example app
│   ├── dcos-101.md … dcos-106.md      # DC/OS GUI through advanced topics
│   ├── jenkins-101.md … jenkins-106.md# Jenkins quickstart through advanced
│   ├── setup.md                       # Environment prerequisites
│   └── images/                        # Screenshots and diagrams
├── velocity-training-10-2015/         # October 2015 — Velocity NYC
│   ├── docker/                        # Docker fundamentals
│   ├── mesos-marathon/                # Mesos/Marathon configs + gen.sh script
│   ├── kubernetes/                    # Kubernetes pod/service JSON specs
│   └── piat/                          # Putting It All Together exercises
└── velocity-training-11-2016/         # November 2016 — Velocity Amsterdam
    ├── DAY1/                          # Container fundamentals (101–103)
    ├── DAY2/                          # DC/OS (101–106) + Jenkins (101–103)
    ├── setup.md                       # Tooling setup
    └── resources.md                   # Background reading
```

## Content Conventions

### Markdown Files
- All lab guides are written in **GitHub-flavored Markdown**
- Code blocks use fenced triple backticks with language identifiers (` ```bash `, ` ```json `)
- Command examples use `$` prefix for shell commands students run
- Steps are numbered sequentially; sub-steps use lettered bullets
- Screenshots are stored in `images/` subdirectories and referenced with relative paths

### JSON Configuration Files
- **Marathon app specs** follow the [Marathon REST API](https://mesosphere.github.io/marathon/docs/rest-api.html) schema
- All JSON files are standalone (no references to other files)
- Naming convention: `marathon-<service-name>.json`
- Common fields: `id`, `cmd`, `cpus`, `mem`, `instances`, `container`, `healthChecks`, `labels`

### Directory/File Naming
- Training event directories: `<event-name>-<MM>-<YYYY>/`
- Lab modules use zero-padded numbers: `docker-101.md`, `dcos-102.md`
- Day-based subdirectories use all caps: `DAY1/`, `DAY2/`

## Development Workflow

### Branch Strategy
- `master` — stable, published training content
- Feature branches follow the pattern `claude/<description>-<id>` for AI-assisted changes

### Making Changes
1. Work on the designated feature branch (never push directly to `master`)
2. Edit Markdown files and JSON configs directly — no build step required
3. Commit with clear, descriptive messages referencing the training module (e.g., `fix jenkins lab 4 in AMS training`)
4. Push with: `git push -u origin <branch-name>`

### Commit Message Style
Based on the existing commit history, messages are short and imperative:
- `fixes <thing> in <location>`
- `cleanup`
- `moar fixes <location>`
- `add <feature/content>`

## Key Technologies Covered

| Technology | Where Covered |
|---|---|
| Docker | All events; most detailed in `velocity-training-09-2016/docker-*.md` |
| DC/OS | All events; most detailed in `velocity-training-09-2016/dcos-*.md` |
| Marathon | `dcos-bootcamp-04-2016/dcos/`, `velocity-training-06-2016/containerops/` |
| Jenkins | `velocity-training-09-2016/jenkins-*.md`, `velocity-training-11-2016/DAY2/` |
| Mesos | `velocity-training-10-2015/mesos-marathon/` |
| Kubernetes | `velocity-training-10-2015/kubernetes/` |
| Prometheus/Grafana | `velocity-training-06-2016/monitoring/` |

## What's Not in This Repo

- No build system (no `package.json`, `Makefile`, `pyproject.toml`)
- No automated tests
- No CI/CD pipeline configuration
- No application source code
- No Docker images or Dockerfiles (only instructions referencing public images)

## Notes for AI Assistants

- When editing lab guides, preserve the existing step-by-step structure and numbered format
- Marathon JSON files must remain valid JSON — validate after edits
- The `velocity-training-09-2016/` directory is the most complete and polished training event; use it as a reference for style and depth
- Images in `images/` directories are referenced by relative paths from their parent README — keep paths consistent when moving files
- There is no linter or formatter to run; review changes manually for Markdown correctness
