# Lisk Core Documentation

## Table of contents

- [Introduction](#lisk-core-documentation)
  - [Versions](#versions)
  - [Versioning Schemes](#versioning-schemes)
  - [What is Lisk Core?](#what-is-lisk-core)
    - [Networks](#networks)
    - [Components](#components)
  - [Contribute to Codebase](#contribute-to-the-codebase)
- [Setup](setup/setup.md)
  - [Binary](setup/binary/binary.md)
  - [Docker](setup/docker/docker.md)
  - [Source](setup/source/source.md)
- [Upgrade](upgrade/upgrade.md)
  - [Binary](upgrade/binary/upgrade-binary.md)
  - [Docker](upgrade/docker/upgrade-docker.md)
  - [Source](upgrade/source/upgrade-source.md)  
  - [Migration](upgrade/migration/migration.md)
- [User Guide](user-guide/user-guide.md)
  - [Administration](user-guide/administration/admin.md)
    - [Binary](user-guide/administration/binary/admin-binary.md)
    - [Docker](user-guide/administration/docker/admin-docker.md)
    - [Source](user-guide/administration/source/admin-source.md)
  - [Configuration](user-guide/configuration/configuration.md)
  - [API](user-guide/api/api.json)
[Troubleshooting](troubleshooting/troubleshooting.md)

## Versions

We release new versions of Lisk Core regularly. Documentation on [lisk.io](https://lisk.io/documentation) will keep up to date with version updates. The Lisk Core version reference below provides an overview about the former releases and documentation versions of Lisk Core.

Software Version | Protocol Version | Release date <br> (yy/mm/dd)| Documentation reference
---     | ---       | ---         | ---
[v1.5.0](https://github.com/LiskHQ/lisk/releases/tag/v1.5.0) | 1.0 | 19/mm/dd | *Current version, live on lisk.io/documentation*
[v1.4.0](https://github.com/LiskHQ/lisk/releases/tag/v1.4.0) | 1.0 | 19/01/07 | [Lisk Core 1.4 docs](https://github.com/LiskHQ/lisk-docs/blob/core-1.4.0/introduction.md)
[v1.3.0](https://github.com/LiskHQ/lisk/releases/tag/v1.3.0) | 1.0 | 18/11/19 | [Lisk Core 1.3 docs](https://github.com/LiskHQ/lisk-docs/blob/core-1.3.0/introduction.md)
[v1.2.1](https://github.com/LiskHQ/lisk/releases/tag/v1.2.1) | 1.0 | 18/11/10 | [Lisk Core 1.2 docs](https://github.com/LiskHQ/lisk-docs/blob/core-1.2.0/introduction.md)
[v1.1.1](https://github.com/LiskHQ/lisk/releases/tag/v1.1.1) | 1.0 | 18/10/23 | [Lisk Core 1.1 docs](https://github.com/LiskHQ/lisk-docs/blob/core-1.1.0/introduction.md)
[v1.0.3](https://github.com/LiskHQ/lisk/releases/tag/v1.0.3) | 1.0 | 18/08/17 | [Lisk Core 1.0 docs](https://github.com/LiskHQ/lisk-docs/blob/core-1.0.0/introduction.md)

## Versioning schemes

Lisk Core is decribed in 2 different versioning schemes. The **Software Implementation Version** and the **Protocol Version**.

### Software implementation versioning

Any Lisk Core software changes, except for the logging system, are communicated following the exact rules specified by [SemVer](https://semver.org/).

Software implementation versioning has a version prefix `v` followed by a 3 digit notation `<MAJOR>.<MINOR>.<PATCH>` , where the individual digits represent the following types of software changes:

```
v<MAJOR>.<MINOR>.<PATCH> 

v     - Version prefix
MAJOR - Breaking change
MINOR - New feature
PATCH - Bug fix
```

The *software implementation version* follows the popular SemVer scheme and gives a quick overview for developers about breaking and non-breaking changes in the software.

### Protocol versioning

The *protocol version* is denoted by two digits, `H.S.`.
The first digit, `H`, depends on the number of hard forks and is incremented with every hard fork.
`S` represents the number of soft forks since the last hard fork.

> The initial protocol version 1.0 is defined to be the one that was implemented by Lisk Core v1.0.0.

The *protocol version* is used e.g. in P2P Communication between Lisk Core nodes, in order to determine, if the nodes have compatible versions of the Lisk protocol implemented.

## What is Lisk Core?

[![What is Lisk Core?](https://img.youtube.com/vi/RfF9EPwQDOY/0.jpg)](https://www.youtube.com/watch?v=RfF9EPwQDOY)

Lisk Core is the program that implements the [Lisk Protocol](/lisk-protocol/introduction.md). Every machine must set it up in order to run a node that allows for participation in the network. Setting up Lisk Core enables a user to:
- Contribute to the decentralisation of the Lisk network
- Explore data recorded on the Lisk blockchain
- Post transactions to the Lisk blockchain
- Enable/Disable forging for a registered delegate
- Configure Lisk Core to specific needs, as required

An instance of Lisk Core is generally detailed in two different ways: 

> A Lisk Core instance connected to a network is referred to as a Lisk **Node**. 
> A Lisk Node connected to other Lisk Nodes is referred to as a Lisk **Peer**.

Both meanings refer to a machine which, after installing and executing Lisk Core, become a server. The server participates in the network and provides blockchain data to its clients.

### Networks

Lisk Core can be connected to different networks. There are two key public networks, entirely independent of each other, that are always accessible: **Mainnet** and **Testnet**. 

#### Mainnet
Mainnet is where the true Lisk economy exists. On this network, Lisk users are able to transfer LSK tokens from one account to another, register accounts as delegates, vote for another delegates or register dApps. It can be explored via the [Lisk Explorer](https://explorer.lisk.io).

#### Testnet
Testnet is an independent replica of the Lisk Mainnet intended as an area to rehearse upgrades before they take place on the Lisk Mainet. This is where new versions and fixes of Lisk Core are tested. It can be explored via [Lisk Testnet Explorer](https://testnet-explorer.lisk.io).

Each connects to a network specified in the config file [`config.json`](https://github.com/LiskHQ/lisk/blob/development/config.json#L2). 
When a user decides which network they wish to connect to, they must follow the correspondent tutorial in the [Setup](setup/setup.md) section.

### Components
The Lisk Core consists of 4 main components:

[![Node.js](nodejs.png "Node.js")](https://nodejs.org)

[Node.js](https://nodejs.org/) serves as the underlying engine for code execution in Lisk Core. Node.js is an open-source, cross-platform JavaScript run-time environment that executes JavaScript code server-side. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.

[![Swagger](swagger-logo.png "Swagger")](https://swagger.io)

[Swagger](https://swagger.io) is an open source software framework backed by a large ecosystem of tools that helps developers design, build, document, and consume RESTful Web services. As part of the Lisk Core documentation, the whole API specification can be explored interactively via the Swagger-UI interface.

[![PostgreSQL](postgresql.png "PostgreSQL")](https://www.postgresql.org)

[PostgreSQL](https://www.postgresql.org) is a powerful, open source object-relational database system with over 30 years of active development which has earned it a strong reputation for reliability, feature robustness, and performance. All Information on the Lisk mainchain is stored inside of PostgreSQL databases.

[![Redis](redis.png "Swagger")](https://redis.io)

[Redis](https://redis.io) is an open source, in-memory data structure store. Lisk Core mainly uses it to cache API responses. This prevents performance drops in the application, for example when the same API request is sent repeatedly.

## Contribute to the Codebase

Everyone is invited to contribute to the Lisk Core project. We welcome and appreciate all contributions. 

### Github
All necessary information can be found on our [Lisk Core Github](https://github.com/LiskHQ/lisk).

### Contribution Guidelines
Please be sure to read and follow our [Contribution Guidelines](https://github.com/LiskHQ/lisk/blob/development/docs/CONTRIBUTING.md).

### Gitter
If you have any further questions please join our [Gitter](https://gitter.im/LiskHQ/lisk).

