---
title: "xen networking issues (LTS)"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by ludder on 2008-11-01
Im running LTS and trying to get my xen going.

The problem is:

I get LAN access, but no WAN access.

If i ping a local adress i get reply, if i try a internett address i get no reply. What is wrong with my config? I just apt-get install ubuntu-xen-server.

my route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 peth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 peth0
0.0.0.0         10.0.0.138      0.0.0.0         UG    100    0        0 eth0

---

