---
title: "netplan with bond, bridge and vlan, error: bond already has a primary slave"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by Tim_Banchi on 2018-08-23
Hello,

On a fresh Ubuntu 18.04 server, I have a working netplan configuration with bond and bridging (for KVM):
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp5s0:
      dhcp4: no
      dhcp6: no
    enp11s6f1:
      dhcp4: no
      dhcp6: no
    enp11s6f0:
      addresses: [XX.XX.XX.XX/24]
  bonds:
    bond-lan:
      dhcp4: no
      dhcp6: no
      interfaces: [enp5s0, enp11s6f1]
      parameters:
        mode: active-backup
        mii-monitor-interval: 1
        primary: enp5s0
  bridges:
    br-kvm:
      addresses: [XX.XX.XX.12/24]
      gateway4: XX.XX.XX.254
      nameservers:
        addresses: [XX.XX.XX.18, XX.XX.XX.19]
        search: [XXXX]
        interfaces: [bond-lan]

```
Bond is working, and looking at networkctl list and ip link show also bridging should work (I haven't setup KVM yet).

When I add a vlan for KVM guests:
```
      ....
      nameservers:
        addresses: [XX.XX.XX.18, XX.XX.XX.19]
        search: [XXXX]
      interfaces: [vlan-kvm] #<-- this changed here
  vlans:
    vlan-kvm:
      accept-ra: no
      link: bond-lan
      id: 15

```
I get the following error:
netplan generate --debug
Error in network definition //etc/netplan/01-netcfg.yaml line 22 column 17: bond-lan: bond already has a primary slave: enp5s0

Removing "primary: enp5s0" solves the error and netplan can be applied. But I think I should have a primary device in bonding, right?
Can somebody explain me what is wrong?

---

