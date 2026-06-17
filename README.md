# su26-ai301-contribution
Contribution 26: Add an extra exercise test scenario for an existing pattern

Contribution Number: 1
Student: Prableen Kakar
Issue: https://github.com/Totoro-jam/battle-tested-patterns/issues/26
Status: Phase I In Progress

Why I Chose This Issue

# Contribution 26: Add an extra exercise test scenario for an existing pattern

**Contribution Number:** 1  
**Student:** Prableen Kakar 
**Issue:** https://github.com/Totoro-jam/battle-tested-patterns/issues/26
**Status:** Phase II

---

## Why I Chose This Issue

I chose this issue because it felt like a manageable way to actually get into the codebase without being thrown into the deep end. The task is adding one edge case test to an existing pattern exercise, which is specific enough that I know exactly what I need to do and where to look. Since it is scoped to one pattern and one language to start with, I felt like I could complete it without needing to understand every part of the project first.

I also picked this because I want to get better at writing tests that actually catch real problems, not just the happy path. Edge cases like empty input or boundary values are the kinds of things that trip up real code, and thinking through those scenarios will help me understand the design patterns more deeply. I figured this would be a good way to learn how the project is structured while contributing something genuinely useful at the same time.

## Understanding the Issue
### Problem Description

The repo has TypeScript exercise files for each pattern, but none of them include an edge-case test. The issue asks contributors to add one new edge-case test (e.g., empty input, boundary value) to an existing pattern's exercise file.

### Expected Behavior

Each pattern exercise should have at least one edge-case test so a learner's implementation has to handle boundary conditions, not just the typical use case.

### Current Behavior

The existing exercise test files only test standard usage. No test targets an edge case like empty input, a single-element structure, or capacity limits.

### Affected Components

- `exercises/typescript/<pattern>/` -- the exercise test files where the new test case goes
- `exercises/answers/<lang>/<pattern>/` -- the reference answer implementations that must still pass

## Reproduction Process
### Environment Setup

Clone the fork, run `pnpm install`, and confirm the test runner works before making changes. Node 18+ and pnpm are required. The repo uses Vitest for TypeScript tests.

### Steps to Reproduce

1. Fork the upstream repo at https://github.com/Totoro-jam/battle-tested-patterns and clone your fork: `git clone https://github.com/prableenkaurr/battle-tested-patterns.git && cd battle-tested-patterns`
2. Install dependencies: `pnpm install`
3. Run the test suite to confirm everything passes before any changes: `pnpm test:exercises`
4. Open an exercise file, for example `exercises/typescript/bloom-filter/01-basic.test.ts`, and read through the existing tests to see how they are structured (each test is an `it(...)` block with a TODO stub).
5. Note that no test in `01-basic.test.ts` or `02-intermediate.test.ts` covers an edge case like querying an empty filter or adding zero items before a lookup.
6. Add a new `it(...)` block for the edge case to the exercise file without filling in the answer.
7. Run `pnpm test:exercises` again -- the new test will fail for any learner who has not handled that edge case, confirming the gap exists.
8. Open the matching answer file at `exercises/answers/typescript/bloom-filter/` and verify the reference implementation already handles the edge case so `pnpm test` still passes with the new test in place.

### Reproduction Evidence
Branch: https://github.com/prableenkaurr/battle-tested-patterns/tree/add-exercise-test-scenario
Commit showing reproduction: [Link to commit -- to be added after first push to branch]
Screenshots/logs: Tests pass on the unmodified fork. New test causes the expected failure before the answer implementation is verified.
My findings: Exercise files follow a consistent `it('...', () => { /* TODO */ })` pattern. The answers directory already handles most edge cases, so adding an edge-case test to the exercise file is low-risk.

## Solution Approach
### Analysis

This is a content gap, not a bug. The exercise files were written to cover core pattern mechanics and skipped boundary behavior. The reference answer already handles the edge case, so no changes to the answer are needed.

### Proposed Solution

Pick one pattern (Bloom Filter in TypeScript), add one edge-case `it(...)` test block to `exercises/typescript/bloom-filter/01-basic.test.ts`, and confirm the answer at `exercises/answers/typescript/bloom-filter/` still passes `pnpm test:exercises`.

### Implementation Plan

- Pick the Bloom Filter pattern and the edge case: calling `has()` on a newly constructed `BloomFilter` with nothing added should return `false` for any key.
- Add a new `it('returns false for any key when the filter is empty', () => { /* TODO */ })` block to `exercises/typescript/bloom-filter/01-basic.test.ts`, matching the style of existing tests.
- Run `pnpm test:exercises` on the answers directory to confirm the reference implementation passes the new test without changes.
- Push the branch `add-exercise-test-scenario` to the fork and open a PR against `Totoro-jam/battle-tested-patterns:main` referencing Issue #26.

## Testing Strategy
### Unit Tests
- Test case 1: Empty filter -- `has(key)` returns `false` on a fresh `BloomFilter` with no items added
- Test case 2: Single-item filter -- after `add('x')`, `has('x')` returns `true` and `has('y')` returns `false`
- Test case 3: Filter at capacity -- insert items up to the declared capacity and check `has()` still returns `true` for all inserted items

### Integration Tests
- Integration scenario 1: Run `pnpm test:exercises` across all TypeScript exercises after adding the new test to confirm nothing else breaks
- Integration scenario 2: Run `pnpm test` on the answers directory to confirm the reference answer passes all exercise tests including the new one

### Manual Testing

Cloned the fork, ran `pnpm install`, executed `pnpm test:exercises`, and confirmed all existing tests pass. Reviewed the bloom-filter exercise and answer files to check the new test fits the existing structure.

## Implementation Notes
### Week 1 Progress

Set up the local environment, explored the repo structure, found the `exercises/typescript/` and `exercises/answers/typescript/` directories, and picked the Bloom Filter pattern. Created the `add-exercise-test-scenario` branch. Confirmed `pnpm test:exercises` passes on the unmodified fork.

## Code Changes
Files modified: `exercises/typescript/bloom-filter/01-basic.test.ts`
Key commits: [To be added as work progresses on branch `add-exercise-test-scenario`]
Approach decisions: Chose Bloom Filter because it has a simple, testable edge case (empty filter query) and the existing answer already handles it, so the PR is low-risk.

## Pull Request

PR Link: [To be submitted -- branch: https://github.com/prableenkaurr/battle-tested-patterns/tree/add-exercise-test-scenario]

PR Description: Adds one edge-case test to the Bloom Filter TypeScript exercise. Querying an empty filter should return `false`. The reference answer passes without changes. Closes #26.

Maintainer Feedback:

[Date]: [Summary of feedback received]
[Date]: [How you addressed it]

Status: In Progress

## Learnings & Reflections
### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

## Resources Used
- https://github.com/Totoro-jam/battle-tested-patterns/issues/26
- https://vitest.dev/guide/
- https://github.com/prableenkaurr/battle-tested-patterns/blob/add-exercise-test-scenario/exercises/typescript/bloom-filter/01-basic.test.ts
