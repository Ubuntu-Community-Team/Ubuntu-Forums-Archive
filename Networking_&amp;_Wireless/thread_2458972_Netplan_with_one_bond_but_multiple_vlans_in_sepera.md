---
title: "Netplan with one bond but multiple vlans in seperate file"
date: 2021-03-08
forum: Networking &amp; Wireless
---

### Post by ducan on 2021-03-08
Hi

Installed ubuntu 20.04 and tried to understand the past few days the netplan configurations. The basic settings I can get to work but I am unable to achieve the below.
Would be great if you can guide me into the right directions?

Various VLAN's with separate IP's and bridges need to be configured using the same bonding.

Problem:  If I change the configuration to the below in two seperate yaml files the ping fails.

Questions: Can I have various yaml files to achieve this? E.g. bond0.yaml, 01-managementport.yaml, 01-vlan1.yaml, 01-valn2.yaml etc. all using the bond0.yaml file Reason for this is that we add or new vlans we do not need to work on existing files which reduces configuration errors.

The bonding on the switch is configured correctly.

Thank you in advance for your feedback.

As soon as I move the vlan to a new yaml file all fails. Not sure why

Setup: server with 6 network ports

Bond file:

# Bonding only.
network:
  renderer: networkd
  bonds:
    bond0:
      dhcp4: false
      dhcp6: false
      interfaces:
      - eno1
      - eno2
      - eno3
      - eno4
      - ens6f0
      - ens6f1
      parameters:
        lacp-rate: fast
        mode: 802.3ad
        transmit-hash-policy: layer3+4
  ethernets:
    eno1: {}
    eno2: {}
    eno3: {}
    eno4: {}
    ens6f0: {}
    ens6f1: {}
  version: 2
new vlan yaml file

#Create new VLAN
 network:
  renderer: networkd
  vlans:
     vlan172:
            id: 172
            link: bond0
            addresses: [172.16.2.13/24]
            gateway4: 172.16.2.254
  version: 2

---

