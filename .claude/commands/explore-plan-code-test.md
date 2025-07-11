## Legend

| Symbol | Meaning  |     | Abbrev | Meaning                |
| ------ | -------- | --- | ------ | ---------------------- |
| →      | leads to |     | EPCT   | Explore-Plan-Code-Test |
| &      | and/with |     | impl   | implementation         |
| ‖      | parallel |     | UX     | user experience        |

@include shared/command-templates.yml#Command_Header

Systematic development workflow: Explore → Plan → Code → Test for any task.

@see shared/mcp-flags.yml ∀ MCP controls
@see shared/research-first.yml ∀ exploration patterns

Examples:

- `/user:explore-plan-code-test "Add dark mode toggle"` - Full EPCT workflow
- `/user:explore-plan-code-test --skip-explore "Refactor auth module"` - Skip exploration if familiar
- `/user:explore-plan-code-test --ultrathink "Redesign payment system"` - Deep planning mode

## Workflow Stages

### 1. EXPLORE [Parallel Discovery]

```yaml
Purpose: Discover all relevant context before planning
Execution: ‖ subagents for parallel file discovery
Outputs: File paths, patterns, examples, constraints

Activities:
  - Find implementation examples ‖
  - Identify edit targets ‖
  - Discover test patterns ‖
  - Analyze dependencies ‖
  - Review similar features ‖

Flags:
  --skip-explore: Skip if already familiar w/ codebase
  --deep-explore: Include indirect dependencies & patterns
```

### 2. PLAN [Strategic Thinking]

```yaml
Purpose: Create detailed implementation strategy
Execution: Sequential deep thinking + ‖ web research if needed
Outputs: Step-by-step plan w/ tests, docs, components

Activities:
  - Analyze exploration findings
  - Design implementation approach
  - Plan test strategy
  - Consider edge cases
  - Research unknowns ‖
  - Ask clarifying questions (pause if needed)

Flags:
  --think: Standard planning depth
  --think-hard: Complex architectural planning
  --ultrathink: Critical system redesign
```

### 3. CODE [Implementation]

```yaml
Purpose: Execute plan w/ quality & consistency
Execution: Sequential implementation following plan
Outputs: Working code, tests, documentation

Activities:
  - Follow existing code style
  - Implement features incrementally
  - Write/update tests
  - Create/update documentation
  - Run autoformatting
  - Fix reasonable linter warnings

Standards:
  - Clear naming > extensive comments
  - Consistency w/ codebase patterns
  - Test coverage for new code
  - Documentation for public APIs
```

### 4. TEST [Validation]

```yaml
Purpose: Ensure quality & correctness
Execution: ‖ subagents for parallel testing
Outputs: Test results, UX validation, issue reports

Activities:
  - Run unit tests ‖
  - Run integration tests ‖
  - Execute E2E tests ‖
  - Validate UX if applicable
  - Performance testing if relevant

UX Testing:
  - Create test checklist
  - Use browser automation
  - Verify user workflows
  - Check edge cases

Failure Mode:
  - Return to PLAN stage
  - Think ultrahard about issues
  - Adjust approach
```

### 5. WRITE-UP [Documentation]

```yaml
Purpose: Create PR-ready description
Execution: Summarize work & decisions
Outputs: PR description template

Contents:
  - Objective & approach
  - Key implementation choices
  - Justification for decisions
  - Commands run (for future reference)
  - Test coverage summary
  - Breaking changes (if any)
```

## Mode Variations

**--minimal:** Quick EPCT for simple tasks

- Light exploration
- Basic planning
- Standard testing

**--comprehensive:** Full EPCT for complex features

- Deep exploration w/ indirect deps
- Detailed planning w/ alternatives
- Extensive testing including performance

**--emergency:** Fast-track critical fixes

- Focused exploration on issue area
- Rapid planning
- Targeted testing

## Integration Patterns

```yaml
Personas:
  - analyzer → EXPLORE phase
  - architect → PLAN phase
  - frontend/backend → CODE phase
  - qa → TEST phase
  - mentor → WRITE-UP phase

MCP Usage:
  - Context7 → exploration & research
  - Sequential → planning & analysis
  - Puppeteer → UX testing
  - Magic → rapid prototyping
```

## Quality Gates

```yaml
Explore: Found all relevant files? | Understood patterns?
Plan: Addressed all requirements? | Considered edge cases? | Questions answered?
Code: Tests pass? | Linter clean? | Style consistent?
Test: All tests green? | UX validated? | Performance acceptable?
Write-up: Clear description? | Decisions documented? | Future-friendly?
```

## Failure Recovery

```yaml
Explore Failed: Use broader search terms | Check different directories
Plan Unclear: Research more ‖ | Ask user for clarification
Code Errors: Debug systematically | Check assumptions
Test Failures: Return to PLAN | Think ultrahard | Adjust approach
```

Workflow: EXPLORE(‖) → PLAN(seq+‖) → CODE(seq) → TEST(‖) → WRITE-UP

Deliverables: Implementation, tests, documentation, PR description.
