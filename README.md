# BRACKEN Network Engine

**Network configuration, routing, and forwarding services for BRACKEN.**

The BRACKEN Network Engine is intended to manage node networking and provide the routing and configuration functions needed by BRACKEN services. It connects operator intent from the control plane with the host's network interfaces and the packet-processing data plane.

> **Project status:** Early-stage project. Routing protocols, supported topologies, and interface contracts have not yet been finalized.

## Responsibilities

- Model and apply network interface configuration.
- Manage routes and forwarding state.
- Define support for VLANs, tunnels, NAT, and connection tracking as capabilities are designed.
- Coordinate network configuration with the data plane and report resulting state.
- Provide validation and diagnostics for network changes.
- Keep host connectivity and recovery behavior visible during configuration updates.

## Architecture boundary

This repository owns network configuration and routing behavior. The [data plane](https://github.com/vayun-networks/bracken-data-plane) handles high-rate packet processing and enforcement. The [control plane](https://github.com/vayun-networks/bracken-control-plane) owns management APIs, desired state, and orchestration. Virtual machine network attachment is integrated with [bracken-virtualization](https://github.com/vayun-networks/bracken-virtualization).

## Design principles

- Validate proposed changes before applying them.
- Avoid locking operators out during remote network reconfiguration.
- Make route and interface changes observable and reversible where feasible.
- Keep protocol support modular and document its prerequisites.
- Separate configuration intent from the underlying Linux mechanisms.

## Planned milestones

Begin with a supported interface and route model, then implement a testable single-node configuration path. Add VLAN and tunnel support only with documented behavior and integration tests. Advanced routing protocols, distributed traffic engineering, and multi-region operation are future directions rather than current capabilities.

## Development

No build or runtime commands are defined yet. Contributions should document the topology and environment used for validation, expected kernel features, and behavior when a change partially fails. Network experiments should run in an isolated lab or on infrastructure the operator controls.

## Related components

- [bracken-control-plane](https://github.com/vayun-networks/bracken-control-plane)
- [bracken-data-plane](https://github.com/vayun-networks/bracken-data-plane)
- [bracken-virtualization](https://github.com/vayun-networks/bracken-virtualization)
- [bracken-observability](https://github.com/vayun-networks/bracken-observability)