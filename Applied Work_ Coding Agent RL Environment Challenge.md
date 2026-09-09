# Applied Work: Coding Agent RL Environment Challenge

# 1\. Objective

Develop a production-grade, reproducible Reinforcement Learning (RL) environment designed to evaluate AI coding agents on realistic, complex software engineering tasks.

Unlike standard competitive programming tasks (LeetCode-style), your goal is to construct a **synthetic software lifecycle** where an AI agent must inspect a codebase, diagnose an issue, propose a non-trivial fix, and verify its impact through an automated pipeline. We are looking for environment designs that exhibit **high-fidelity realism**, **adversarial robustness**, and **objectively measurable success**.

# 2\. Engineering Requirements

Your submission must be fully containerized, deterministic, and self-contained. The environment should be capable of running on a clean Linux-based host using standard Docker tooling.  
*Note: Candidates are free to use frameworks like Harbor or any other framework of their choice for building or evaluating the environment.*

## 2.1 Required Directory Structure

All submissions must adhere to the following file architecture to ensure consistent evaluation:

* 

```
ccoding-rl-environment/
├── task/
│   ├── instruction.md          # User-facing prompt for the agent
│   └── task.yaml               # Metadata: difficulty, scope, required tool usage
├── environment/
│   ├── Dockerfile              # Fully pinned dependencies/environment
│   └── repo/                   # Starting codebase state
├── solution/
│   └── reference_solution/     # The "Gold Standard" implementation
├── tests/
│   └── verifier/               # Deterministic test suites (oracle-based)
├── analysis/
│   ├── grader_attacks.md       # Analysis of grader vulnerabilities
│   └── model_runs.md           # Logs/Trace of an actual agent run
└── README.md                   # Engineering Design Document (EDD)

```

# 3\. Specialist Tasks

You must implement a task that requires genuine engineering reasoning. Areas of focus include:

* **Repository-Level Debugging:** Resolving dependency conflicts or build-system failures.  
* **API/Service Integration:** Implementing a feature that requires cross-service coordination.  
* **Infrastructure/DevOps:** Automating a workflow (e.g., CI/CD hardening, Docker/K8s configuration).  
* **Multi-file Implementation:** Modifying system logic across non-contiguous files.

# 4\. Evaluation Standards

We evaluate based on the rigor of your engineering, not just the complexity of the problem.

| Area | Weight | Description |
| ----- | :---: | ----- |
| **Engineering Realism** | 20% | Does the problem mimic real-world software maintenance or development? |
| **Verifier Integrity** | 30% | Is the oracle/test suite deterministic? Does it accurately grade outcomes? |
| **Adversarial Robustness** | 20% | Have you documented and mitigated "grader-hacking"? |
| **Reproducibility** | 15% | Are dependencies pinned, and environment setup idempotent? |
| **Documentation (EDD)** | 15% | Clarity of the README and the reasoning behind environment design. |

# 5\. Required Submission Components

## 5.1 The Engineering Design Document (README.md)

Your README must function as an EDD. It must explicitly answer:

* **1\. Capability Mapping:** What specific engineering capability does this measure?  
* **2\. Environment Logic:** How did you handle stochasticity?  
* **3\. Oracle Strategy:** How does the verifier distinguish between "correct behavior" and "correct output"?  
* **4\. Adversarial Analysis:** What are the most likely ways an agent will try to "game" your grader, and how did you prevent this?

## 5.2 Deterministic Verification

Your verifier must be "difficult to fool":

* **Negative Testing:** The grader must correctly reject "partial successes" or attempts that break unrelated system components.  
* **Oracle Validation:** Implement an oracle-based verifier that checks the *state of the system* after the fix, rather than just grepping for specific text output.

## 5.3 Adversarial Analysis (grader\_attacks.md)

Active red-teaming of your own grader is mandatory. Document at least three attack vectors (e.g., modifying the test suite, hardcoding output). For each attack, describe the technical fix implemented to negate it.

## 5.4 Model Evaluation & Analysis

You must conduct a rigorous model evaluation as part of your analysis:

* **Model Comparison:** Evaluate performance across at least two distinct models using the *pass@k* metric.  
* **Stump Percentage:** Analyze and report the stump percentage (the frequency at which models fail to initiate or get "stumped" on the task).  
* **Results Analysis:** Provide a detailed qualitative and quantitative analysis explaining the observed performance results and failure modes.

# 6\. Submission Guidelines

* **Integrity:** The work must be original. Do not copy tasks or graders from existing public benchmarks.  
* **Process:** Email your submission to **raja@appliedwork.ai**.  
* **Required Inclusions:**  
  * Full Name & Phone Number.  
  * Link to a GitHub repository or a ZIP archive.  
  * A 3–5 line executive summary of the engineering challenge you built.  
  * Submit the assignment in 3 working days 

**Subject Line:** Coding RL Environment Assignment | \[Your Name\]