---
title: "1 NIC assigned to VLAN via netplan"
date: 2021-09-25
forum: Networking &amp; Wireless
---

### Post by rrioux on 2021-09-25
I have a host with 1 nic, and would like it to be assigned to vlan 10. Previously this was done by added vlan to the device. EG eth0 to eth0.10. With netplan, i have tried adding a vlan and address for that vlan. when i do that it now makes both addresses pingable. but it seems like the routing is off, i would like to just be able to use 1 address and have everything work as expectied.

this is the current config that allows connectivity... but network connections out dont really work...

```
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
      addresses:
      - 10.0.10.20/24
      gateway4: 10.0.10.1
      nameservers:
        addresses:
        - 10.0.10.1
        search:
        - breachhq.com
  vlans:
    vlan.10:
      id: 10
      link: enp3s0
      addresses: [10.0.10.21/24]
  version: 2
```

any help on this would be great .. thanks.

---

### Post by rrioux on 2021-09-25
I solved my issue with the following netplan:

```
# This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
      dhcp4: false
  vlans:
    enp3s0.10:
      id: 10
      link: enp3s0
      addresses: 
      - 10.0.10.20/24
      gateway4: 10.0.10.1
      nameservers:
        addresses:
        - 10.0.10.1
        search:
        - xxxxx.com
  version: 2
```

---

