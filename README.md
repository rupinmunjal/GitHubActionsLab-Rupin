# 🧾 GitHub Actions Workflows – Lab 4

This repository contains three GitHub Actions workflows demonstrating **job dependencies**, **environment variables and secrets**, and **multi-platform testing**.  
These workflows showcase key CI/CD concepts such as `needs`, `env`, and `runs-on`.

---

## ⚙️ Workflow 1 – Job Dependencies
**File:** `.github/workflows/dependent-jobs.yml`

### 🔍 Purpose
This workflow demonstrates how to control job execution order using the `needs` keyword.  
It defines three jobs that run in sequence:
1. **build** → simulates building the application  
2. **test** → runs after the build job  
3. **deploy** → runs after the test job  

### 🧠 Key Concepts
- **`needs`** → Specifies job dependencies, ensuring jobs execute in order.  
- **`runs-on`** → Defines the operating system used (`ubuntu-latest`).  
- **Job Dependency Visualization** → Clearly shows sequential execution in the Actions UI.

### 💬 Challenges & Resolutions
- **Challenge:** Understanding how to connect jobs without triggering parallel runs.  
- **Resolution:** Used `needs` to enforce the correct sequence: `build → test → deploy`.

---

## 🔐 Workflow 2 – Environment Variables and Secrets
**File:** `.github/workflows/env-secrets.yml`

### 🔍 Purpose
This workflow demonstrates the use of environment variables at multiple levels and secure handling of GitHub secrets.  
It prints environment variable values defined globally, per job, and per step.

### 🧠 Key Concepts
- **`env` (Global/Job/Step Level)** → Defines variables at different scopes.  
- **`secrets`** → Securely injects sensitive information such as API keys.  
- **`runs-on`** → Ensures consistent environment setup (`ubuntu-latest`).  

### 💬 Challenges & Resolutions
- **Challenge:** Understanding the precedence of environment variables (global vs job vs step).  
- **Resolution:** Tested variables at all three levels to confirm that step-level variables override others.

---

## 🖥️ Workflow 3 – Multi-Platform Testing
**File:** `.github/workflows/multi-platform.yml`

### 🔍 Purpose
This workflow tests a project across **multiple operating systems** to ensure cross-platform compatibility.  
It runs three independent jobs simultaneously on:
- Ubuntu  
- Windows  
- macOS  

### 🧠 Key Concepts
- **`runs-on`** → Specifies the target OS (`ubuntu-latest`, `windows-latest`, `macos-latest`).  
- **Parallel Execution** → Each job runs independently with no dependencies.  
- **Cross-Platform Testing** → Confirms consistent behavior across OS environments.

### 💬 Challenges & Resolutions
- **Challenge:** Using OS-specific commands (e.g., `uname -a`, `systeminfo`).  
- **Resolution:** Added platform-specific commands for each OS and tested file creation within each job.

---

## ✅ Summary of Key Learnings

| Concept | Description |
|----------|--------------|
| **needs** | Controls job dependencies and execution order |
| **env** | Defines and manages environment variables |
| **runs-on** | Specifies the OS environment for each job |
| **Parallel Execution** | Achieved with independent jobs across platforms |
| **Secrets Management** | Demonstrated secure variable handling |
