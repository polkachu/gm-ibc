# GM IBC

Every day we wake up, we say "GM IBC". -Polkachu, probably

**THIS PRODUCT IS NOT READY FOR PUBLIC**

## Problem Statement

IBC is good but complex. Every relayer ends up maintaining their own infrastructure. Config file templates are shared everywhere such as GitHub Gist and Discord. There is no single point of reliable truth about canonical channels, gas prices, and various other config params. When a chain makes a change, every relayer scrabbles to update config files. Sometimes a channel can be broken for days before people realize it.

Chain Registry solves some problems, but it is not enough for IBC relayers. It is so decentralized that it is difficult to make opinionated and radical changes when situations emerge. It is maintained as many json files and updated via PRs. It is fully transparency, but can be at times brittle.

## What's GM-IBC?

GM IBC is to maintain a source of truth for IBC with an opinionated and centralized design. We will be inferior to Chain Registry when if you value openness and community participation, but we will make it up by offering better tools to make relayer's life easier. We dog-food these tools ourselves so it is a worthwhile effort even if we are the only users.

- A public API endpoint to fetch all IBC config data
- An open-sourced Ansible playbook to use the API data to compose and deploy a Hermes relayer in a few seconds.
- A frontend tool to help a relayer to generate Hermes config snippets on the fly.

## Design Philosophy

1. Support Hermes relayer only for now
1. Decouple data and config template
1. Data is stored in a structured database
1. Keep config template extremely simple but compose the Hermes config file with remote API data
1. API data can be called by any relayers regardless whether they choose to use Polkachu playbook
1. Offer a frontend tool for relayer to generate one-off config snippets manually

## How it works

First, copy inventory file and customize to suit your need.

```bash
cp inventory.ini.sample inventory.ini
```

Second copy mainnet group_vars file and customize to suit your need

```bash
cp group_vars/sample.yml group_vars/mainnet.yml
```

Finally run the playbook. If you make some minimum changes to the config files, you should have a relayer between CosmosHub and Osmosis running now.

```bash
ansible-playbook main.yml -e "target=mainnet"
```

# Conclusion

GM, IBC!
