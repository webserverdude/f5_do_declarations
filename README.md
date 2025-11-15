# F5 Declarative Onboarding (DO) Declarations

## Overview
This repository contains **F5 BIG-IP Declarative Onboarding (DO) JSON declarations** used to automate the initial configuration of BIG-IP devices.  
Declarative Onboarding is part of the **F5 Automation Toolchain** and enables you to configure BIG-IP systems using a **declarative model** rather than imperative commands.

With DO, you define the desired state of your BIG-IP device in a single JSON declaration and send it via a REST API call. DO then applies the configuration automatically.

---

## What is Declarative Onboarding?
**Declarative Onboarding (DO)** simplifies the initial setup of BIG-IP devices by allowing you to specify:
- **System settings**: Licensing, provisioning, hostname, users
- **Network settings**: VLANs, Self IPs, routes
- **Clustering settings**: Device Service Clustering (DSC) for HA pairs or groups

Instead of running multiple CLI commands, you provide a **JSON declaration** that represents the target configuration. DO validates and applies this configuration to the BIG-IP system.

For application and service configuration after onboarding, use **F5 Application Services 3 (AS3)**.

---

## Key Features
- **Declarative model**: Define *what* you want, not *how* to do it.
- **Single REST API call**: Send the JSON declaration to `/mgmt/shared/declarative-onboarding`.
- **Supports standalone and clustered BIG-IP systems**.
- **Schema validation**: Ensures declarations are syntactically correct.

---

## Repository Structure
```
├── declarations/
│   ├── standalone/
│   │   └── example.json
│   ├── cluster/
│   │   └── example.json
└── README.md
```

- **declarations/**: Contains JSON files for different onboarding scenarios.
- **standalone/**: Examples for single BIG-IP devices.
- **cluster/**: Examples for HA pairs or clusters.

---

## How to Use
1. **Install DO** on your BIG-IP device.  
   Refer to [F5 Declarative Onboarding Installation Guide](https://clouddocs.f5.com/products/extensions/f5-declarative-onboarding/latest/).

2. **Send a declaration**:
   ```bash
   curl -sk -u admin:password      -X POST https://<BIG-IP>/mgmt/shared/declarative-onboarding      -H "Content-Type: application/json"      -d @declarations/standalone/example.json
   ```

3. **Validate your declaration** using tools like:
   - [VS Code JSON schema validation](https://clouddocs.f5.com/products/extensions/f5-declarative-onboarding/latest/).

---

## Examples
- **Standalone BIG-IP**: Basic system setup with VLANs and Self IPs.
- **Clustered BIG-IP**: Device Service Clustering configuration.

---

## Resources
- [Official F5 Declarative Onboarding Documentation](https://clouddocs.f5.com/products/extensions/f5-declarative-onboarding/latest/)
- [F5 Automation Toolchain Overview](https://clouddocs.f5.com/cloud/public/v1/)
- [AS3 Extension for Application Services](https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/)

---

## License
This repository contains configuration examples and is provided under the MIT License. See [LICENSE](LICENSE) for details.
