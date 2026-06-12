---
title: "Server 20.04 netplan for static route and static ip"
date: 2020-12-12
forum: Networking &amp; Wireless
---

### Post by charlesw23 on 2020-12-12
So I read through quite a few documentation pages and nothing had the right format for setting up a netplan with a static route correctly for ubuntu 20.04.  Here is what I came up with that worked

In this setup I have 2 interfaces.  1 DHCP assigned ipv4 and a fiber backplane running on two different subnets with a static route between the two.


```
network:
  ethernets:
    eth0:
      dhcp4: true
    eth1:
      dhcp4: false
      addresses:
        - 10.10.10.8/24
      routes:
        - to: 10.10.11.0/24
          via: 10.10.10.1
  version: 2
```

---

