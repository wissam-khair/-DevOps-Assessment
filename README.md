# DevOps Assessment — HashiCorp Stack Setup

### 🎯 Objective

Prepare a working setup of **Nomad**, **Consul**, and **Vault** on Ubuntu 24.04 using the latest stable releases.

You’ll demonstrate your ability to:
- Deploy and configure these services
- Integrate Consul with Vault for authentication
- Connect Nomad with Consul for service discovery
- (Bonus) Integrate Nomad with Vault for secret management

---

## 🧱 Requirements

### 1. Environment
- OS: Ubuntu 24.04 LTS
- Tools allowed: shell scripts, Docker, Vagrant, or local install
- Use official HashiCorp binaries (Nomad, Consul, Vault)

### 2. Services Setup
| Service | Purpose |
|----------|----------|
| **Vault** | Secret management, authentication backend |
| **Consul** | Service discovery, KV store; uses Vault for ACL token management |
| **Nomad** | Workload orchestration; integrated with Consul (and optionally Vault) |

### 3. Integrations
1. **Consul ↔ Vault**
   - Enable the Vault Consul Secrets Engine
   - Configure Consul to use Vault-issued tokens for ACLs
   - Create minimal Vault policies for Consul

2. **Nomad ↔ Consul**
   - Nomad registers with Consul for service discovery

3. **Nomad ↔ Vault** *(bonus)*
   - Use Vault integration in Nomad jobs for dynamic secrets

---

## ⚙️ Deliverables

1. **Documentation**
   - Detailed setup guide in this README
   - Include all commands, configuration notes, and reasoning

2. **Configuration Files**
   - All `.hcl` and `.sh` files under `configs/` and `scripts/`

3. **Validation**
   - Provide screenshots or CLI outputs for:
     - `vault status`
     - `consul members`
     - `nomad node status`
   - Demonstrate Consul ACL token issued by Vault (output proof)

---

## 💡 Bonus (Optional)

- Secure traffic between services with TLS  
- Add a sample Nomad job using Vault secrets
- Configure Vault Agent or auto-auth method (e.g. AppRole)

---

## 🧠 Evaluation Criteria

| Area | What we evaluate |
|------|------------------|
| Setup Accuracy | Services work correctly, integrations functional |
| Configuration Quality | Security, clarity, and best practices |
| Documentation | Clear, reproducible instructions |
| Automation | Reusability and scripting quality |
| Bonus | Vault + Nomad integration, TLS |

---

## 🕒 Time Expectation
- **Core setup:** ~3–4 hours  
- **With bonus features:** up to 1–2 days

---

## 🚀 Getting Started (Candidate Instructions)

1. Fork this repository
2. Complete your setup under `configs/` and `scripts/`
3. Update this `README.md` with your steps and notes
4. Submit your fork link or tarball when done

---

## 🧾 Example Validation Commands

```bash
# Verify Consul members
consul members

# Check Vault status
vault status

# Login to Vault (root token or AppRole)
vault login <token>

# Verify Consul secret engine
vault secrets list | grep consul

# Verify Nomad connected to Consul
nomad server members
