---
title: "Netplan Bridge 2 Ethernet Interfaces"
date: 2020-07-10
forum: Networking &amp; Wireless
---

### Post by jomausiu on 2020-07-10
Hi,

I would like to know if possible to create a bridge with 2 ethernet interfaces?
- eno1 LAN
- eno2 WAN

```

network:  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
      dhcp6: no
      addresses: [10.6.0.200/24]
      gateway4: 10.6.0.2
      nameservers:
        addresses: [10.6.0.2]
    eno2:
      dhcp4: no
      dhcp6: no
      addresses: [191.102.89.156/30]
      gateway4: 191.102.89.155
      nameservers:
        addresses: [9.9.9.9]

```

So ENO2 can see LAN ping -I eno2 10.6.0.100 for example, any advice or recommendation with Netplan will be really appreciate it!

Thank in advance for your help

---

