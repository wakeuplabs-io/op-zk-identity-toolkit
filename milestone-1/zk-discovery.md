<div style="text-align: right;">
    <img style="width: 200px" src="./assets/wakeup-logo.png" width="200">
</div>

# Analysis of current ZK Identity tools

## Context and Problem Statement

The objective is to develop a Zero-Knowledge (ZK) Identity toolkit for application developers on the Superchain.

The toolkit should facilitate trusted and secure relationships between applications and users, prioritizing self-sovereign identity and privacy. It should allow application developers to use ZK proofs in their applications, unlocking a huge design space of applications that can only be built using crypto.

## Decision Drivers

* Simplicity to build ZK identity
* Simplicity on implementation by developers
* Maturity of the solution
* Currently more comprehensible structure

## Considered Options

* Web5
* Privado ID
* Quark ID
* PSE - ZK Kit

## Decision Outcome

Chosen option: Privado ID, because it already provides an integral solution to the infrastructure required to manage credentials, schemas and validations. It exposes an API and a UI to interact with. It's also the most mature solution with an almost plug & play capability. The software licenses are appropriate to enable the use of the tool's open-source code.

### Positive Consequences

* Most of the path has already been paved by Privado ID's solution; however, changes are expected to be required to make it compatible with the Optimism network and, in general, with the Superchain.
* Documentation is very clear
* Offchain validation is a good checkpoint on progress
* Wallet is ready to work on different chains

### Negative Consequences 

* DID & credential issuing isn't natively chain interoperable

## Pros and Cons of the Options

### Web5

#### Pros

* It offers an SDK that allows for any action related to Decentralized Identity
* It's simplified way of using DWNs

#### Cons

* It's not focused on a credential flow
* It lacks a straightforward way to implement ZK queries 
* It's just the fundamental stone for more real world advanced implementations

### Quark ID

#### Pros

* It's an implementation of DIDs & Decentralized Data Storage through DWNs
* It's designed for interoperability with multiple blockchains

#### Cons

* Heavily relies on ZKSync
* It doesn't support ZK Query language out of the box, neither it's specified
* Documentation, examples and configuration aren't as clear as Privado ID's

### Privado ID

#### Pros

* Its infrastructure is ready to deploy
* APIs have their own UI, which may help with management and visual understanding
* It allows for a mid-check offchain verification
* Live demo to try it out, including ZK Query Language UI
* Iden3 ZK Circuits available to deploy on any EVM-compatible network

#### Cons

* It is currently tied just to Polygon Network

### PSE - ZK KIT

#### Pros

* Great abstraction of tools required for ZK development, simplifying their usage

#### Cons

* It's only a portion of the tools required on the infrastructure of identity
* It still requires to put them all together

## Infrastructure, Architecture and Functionalities

Infrastructure and Architecture are defined by Privado ID's integral solution since it has what's required to implement Decentralized Identity, including credential management and verification. Since each piece provides a set of functionalities, we adopt their architecture.

### [Issuer Node](https://docs.privado.id/docs/category/issuer)
The Issuer node is composed of an API with the core functionalities related to Identity and Claims.
On top of it, there's a UI with its own API available to interact with more real-world operations, such as:

* Create Issuer Identities
* Issue/Revoke/Fetch VCs
* Transit Issuer's state
* Create Issuer-User connections

Both APIs expose their endpoints in an interactive way.

### [Schemas](https://docs.privado.id/docs/category/schemas)
Privado ID offers a [Schema Building UI](https://tools.privado.id/) to guide not only on the creation and hosting of custom schemas, but also to explore other public schemas and to build your custom queries based on a schema!

If at some point Privado ID's tool stopped being available, custom schemas may be hosted outside, as their documentation stands, a github repository is 
a good place.

### [Verifier](https://docs.privado.id/docs/category/verifier)
As mentioned before, Privado ID offers a [Query Building Tool](https://tools.privado.id/query-builder) to make custom queries (including ZK queries) and generate the required payload/QR to execute such verification.

The Verifier is capable of on-chain and off-chain verifications. 
They also provide all the documentation and SDKs required to achieve your own verifier.

### [Browser wallet - JS SDK](https://docs.privado.id/docs/js-sdk/js-sdk-overview)
This SDK gives access to the required functions for a user's browser-based wallet to interact in the identity ecosystem, including issuer-node, holder and verifier functionalities:

- Create and manage Identity wallet
- Issue and manage credentials
- Generate zero-knowledge proofs after credential issuance
- Publish the updated state of the Issuer once a credential is added to the claims - Merkle tree
- Handle authorization requests

## Links

* [Privado ID Docs](https://docs.privado.id/docs/introduction)
* [TBD Docs](https://developer.tbd.website/docs/)
* [Quark ID Docs](https://docs.quarkid.org/)
* [PSE ZK Kit docs](https://zkkit.pse.dev/)
