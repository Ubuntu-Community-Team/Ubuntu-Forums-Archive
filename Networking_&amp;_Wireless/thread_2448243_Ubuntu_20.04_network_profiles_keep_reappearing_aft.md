---
title: "Ubuntu 20.04 network profiles keep reappearing after deletion"
date: 2020-08-04
forum: Networking &amp; Wireless
---

### Post by zme-ul on 2020-08-04
this is driving me nuts

> nmclienp0s25: connected to enp0s25
        "Intel 82579LM"
        ethernet (e1000e), , hw, mtu 1500
        ip4 default, ip6 default
        inet4 192.168.1.6/24
**        inet4 192.168.1.168/24**
        route4 0.0.0.0/0
        route4 169.254.0.0/16
        route4 192.168.1.0/24
        route4 192.168.1.0/24
        inet6 2a02:2f0e:7316:5600:2bd:ec9b:c1dd:b305/64
        inet6 2a02:2f0e:7316:5600:69e1:d4c4:c401:550e/64
        inet6 fe80::8488:e3c1:1638:ef84/64
        route6 fe80::f68c:ebff:fe1b:7b44/128
        route6 fe80::/64
        route6 ff00::/8
        route6 2a02:2f0e:7316:5600::/64
        route6 ::/0


enp1s0f0: connected to enp1s0f0
        "Intel 82571EB/82571GB D0/D1"
        ethernet (e1000e), , hw, mtu 1500
        inet4 192.168.1.7/24
**        inet4 192.168.1.6/24**
        route4 192.168.1.0/24
        route4 0.0.0.0/0
        inet6 2a02:2f0e:7316:5600:669e:5863:3aec:449b/64
        inet6 fe80::/64
        route6 ff00::/8
        route6 2a02:2f0e:7316:5600::/64
        route6 ::/0
        route6 fe80::/64


each network interface has two IPs after each reboot, even if I remove them
I tried manually removing them with ```
nmcli con delete uuid
```

this started happening today out of nowhere, I think there was an update or something

I also _had_ installed pihole on the dual NIC card with 192.168.1.6 - if it matters
pihole was not installed with a DHCP server

---

installed fresh on a new SSD ):P

---

