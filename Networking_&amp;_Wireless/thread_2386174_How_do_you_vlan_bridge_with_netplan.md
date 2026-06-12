---
title: "How do you vlan bridge with netplan?"
date: 2018-03-01
forum: Networking &amp; Wireless
---

### Post by nbritton on 2018-03-01
How do you create a vlan on a bridge connected to a tap interface with netplan?

I need:

tap1 / br3: VLAN 10
tap2 / br4: VLAN 20

Here is my current netplan config file:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno3:
      dhcp4: no
      dhcp6: no
    eno4:
      dhcp4: no
      dhcp6: no
    tap0:
      dhcp4: no
      dhcp6: no
    tap1:
      dhcp4: no
      dhcp6: no
    tap2:
      dhcp4: no
      dhcp6: no




  bonds:
    bond1:
      interfaces: [eno3, eno4]
      #parameters:
      #  mode: 802.3ad


  bridges:
    br1:
      interfaces: [bond1]
      dhcp4: no
      addresses: [192.168.1.186/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.1]
    br2:
      interfaces: [tap0]
      addresses: [10.0.0.2/24]
    br3:
      interfaces: [tap1]
      addresses: [10.0.1.2/24]
    br4:
      interfaces: [tap2]
      addresses: [10.0.2.2/24]

```

---

