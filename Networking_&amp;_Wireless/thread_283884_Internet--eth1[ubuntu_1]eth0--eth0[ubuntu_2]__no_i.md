---
title: "Internet--eth1[ubuntu_1]eth0--eth0[ubuntu_2] : no internet for ubuntu2"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by Andrea_44 on 2006-10-24
Hi,

My network topology:
Internet----eth1[ubuntu_1]eth0----eth0[ubuntu_2]

Issue:
What other routes I need to add to the routing table in order for ubuntu_2 to have internet connection?

ubuntu_1 - Kernel IP routing table(route -n) 
Destination    Gateway        Genmask         Flags Metric Ref Use Iface
172.19.96.0    0.0.0.0        255.255.254.0   U     0      0     0 eth1
169.254.0.0    0.0.0.0        255.255.0.0     U     0      0     0 eth0
0.0.0.0        172.19.96.1    0.0.0.0         UG    0      0     0 eth1
ubuntu_1 - eth0 : 169.254.4.217 
ubuntu_1 - eth1 : 172.19.97.127

ubuntu_2 - Kernel IP routing table
Destination    Gateway        Genmask         Flags Metric Ref Use Iface
169.254.0.0    0.0.0.0        255.255.0.0     U     0      0     0 eth0
0.0.0.0        169.254.4.218  0.0.0.0         UG    0      0     0 eth1
ubuntu_2 - eth0 : 169.254.4.218

Destination Unreachable when ubuntu_2 try to ping the gateway in ubuntu_1(172.19.96.1) and ubuntu_1 eth1(172.19.96.127).

Many thx,

Andrea

---

### Post by komputes on 2007-12-13
I would like to know the same thing, I have the following set-up at home, but I can't get the ip route command to work. This is my network topology.

Modem ---> eth0 (PC1) eth1 ---crossover_cable--->eth0(pc2)

PC1 gets internet access but I'm not sure how to share it with PC2.

Help is appreciated.

---

