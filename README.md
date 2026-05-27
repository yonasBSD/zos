# Zero-OS ![Tests](https://github.com/threefoldtech/zos/workflows/Tests%20and%20Coverage/badge.svg) [![Go Report Card](https://goreportcard.com/badge/github.com/threefoldtech/zos)](https://goreportcard.com/report/github.com/threefoldtech/zos)

Zero-OS is an autonomous operating system designed to expose raw compute, storage, and network capacity. It is a lightweight, stateless OS that runs on nodes and manages workloads without requiring traditional system administration.

## What this is

This repository hosts V2 of Zero-OS, a complete rewrite of the autonomous node operating system. Zero-OS handles provisioning, networking, and storage automatically through built-in protocols. It does not expose a traditional management interface; instead, it waits for reservations from a trusted source and applies them to reality. This design eliminates the need for interactive administration and reduces the attack surface of deployed nodes.

If you want to know about the history and decisions that motivated the creation of V2, you can read [this article](https://github.com/threefoldtech/zosbase/blob/main/docs/internals/history/readme.md).

## What this repository contains

- **Node daemon and services** — the core runtime that manages node lifecycle
- **Provisioning subsystem** — workload reservation, validation, and deployment logic
- **Networking stack** — overlay networking, wireguard, and public IP management
- **Storage subsystem** — volume management, cache, and persistent storage handling
- **Identity and cryptography** — node identification, secure bootstrapping, and upgrade mechanisms
- **Resource monitoring and capacity reporting**
- **Integration tests and development tooling** (QEMU-based testing environment)

## Role in the stack

ZOS / Zero-OS is the operating system layer that runs directly on bare-metal nodes. It sits above the hardware and below user workloads, providing:

- Automated workload provisioning from trusted grid sources
- Overlay and direct networking via Mycelium and other network layers
- Storage abstraction and management
- Capacity reporting and resource accounting

ZOS nodes coordinate with higher-level grid infrastructure to receive reservations and report status, while internally using Zinit for service supervision and zosbase libraries for shared primitives.

## ZOS / Zero-OS

ZOS, also known as Zero-OS, is the operating system layer used to run and manage nodes. It provides the low-level runtime environment for workloads, networking, storage, and automation.

## Mycelium

Mycelium is the network layer used to provide secure, peer-to-peer connectivity between nodes, services, and users. It enables decentralized networking across the infrastructure stack and is used as part of the ThreeFold Grid deployment.

## Relation to ThreeFold

This technology is used within the ThreeFold ecosystem and was first deployed on the ThreeFold Grid. The component itself is designed as reusable infrastructure technology and should be understood by its technical function first, independent of any specific deployment.

## Ownership

This repository is owned and maintained by TF-Tech NV, a Belgian company responsible for the development and maintenance of this technology.

## Documentation

Start exploring the codebase by first checking the [documentation](https://github.com/threefoldtech/zosbase/tree/main/docs) and [specification documents](/specs).

An [FAQ](https://github.com/threefoldtech/zosbase/blob/main/docs/faq/readme.md) is also available for common questions.

## Setting up your development environment

If you want to contribute, read the [contribution guideline](CONTRIBUTING.md) and the documentation to set up your [development environment](qemu/README.md).

## Grid Networks

Zero-OS is deployed on several network environments:

- **production network**: Released stable versions. Used to run the real grid. Cannot be reset. Only stable and battle-tested features reach this level. [Dashboard](https://dashboard.grid.tf/)
- **test network**: Mostly stable features that need to be tested at scale. Can be reset occasionally. [Dashboard](https://dashboard.test.grid.tf/)
- **QA network**: Internal testing of new features. Can be behind development. [Dashboard](https://dashboard.qa.grid.tf/)
- **dev network**: Ephemeral network for developing and testing new features. Can be created and reset at any time. [Dashboard](https://dashboard.dev.grid.tf/)

Learn more about the different networks by reading the [upgrade documentation](https://github.com/threefoldtech/zosbase/blob/main/docs/internals/identity/upgrade.md#philosophy).

### Provisioning of workloads

Zero-OS does not expose an interface. Instead, it waits for reservations to happen on a trusted source, and once a reservation is available, the node applies it to reality. You can start reading about [provisioning](https://github.com/threefoldtech/zosbase/tree/main/docs/internals/provision) in this document.

## Community

If you have questions or want to connect, you can find the community on:

- Telegram: <https://t.me/zero_os_tech>
- Matrix: #zero-os:matrix.org

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
Copyright (c) TF-Tech NV.
