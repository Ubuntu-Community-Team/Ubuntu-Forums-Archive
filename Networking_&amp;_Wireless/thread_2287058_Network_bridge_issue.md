---
title: "Network bridge issue"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by Gonalo_Miguel on 2015-07-16
Hi,


I would like to share with you a question about a network configuration issue on ubuntu 14.04.2 LTS.


I've a server with two network interfaces (eth0 and eth1). This server has a bridge configured to be used by QEMU-KVM that runs on it.


Bridge interface (br0) is configured with DHCP on eth1, which is the interface for internall IPs (192.168.88.0/24).


Interface eth0 is used for public access (IP: AAA.BBB.CCC.DDD)



*---*
*br0       Link encap:Ethernet  HWaddr 2c:41:38:7d:62:a5  *
*          inet addr:192.168.88.111  Bcast:192.168.88.255  Mask:255.255.255.0*
*          inet6 addr: fe80::2e41:38ff:fe7d:62a5/64 Scope:Link*
*          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1*
*          RX packets:48517917 errors:0 dropped:0 overruns:0 frame:0*
*          TX packets:26832760 errors:0 dropped:0 overruns:0 carrier:0*
*          collisions:0 txqueuelen:0 *
*          RX bytes:2709980196 (2.7 GB)  TX bytes:133635694032 (133.6 GB)*

*eth0      Link encap:Ethernet  HWaddr 2c:41:38:7d:62:a4  *
*          inet addr:AAA.BBB.CCC.DDD  Bcast:14.136.207.47  Mask:255.255.255.240*
*          inet6 addr: fe80::2e41:38ff:fe7d:62a4/64 Scope:Link*
*          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1*
*          RX packets:3384807 errors:0 dropped:0 overruns:0 frame:0*
*          TX packets:3686296 errors:0 dropped:0 overruns:0 carrier:0*
*          collisions:0 txqueuelen:1000 *
*          RX bytes:378936764 (378.9 MB)  TX bytes:691509228 (691.5 MB)*
*          Interrupt:16 *

*eth1      Link encap:Ethernet  HWaddr 2c:41:38:7d:62:a5  *
*          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1*
*          RX packets:48532220 errors:0 dropped:4573 overruns:0 frame:0*
*          TX packets:91860291 errors:0 dropped:0 overruns:0 carrier:0*
*          collisions:0 txqueuelen:1000 *
*          RX bytes:3585574384 (3.5 GB)  TX bytes:138295042214 (138.2 GB)*
*          Interrupt:17 *
*---*






*/etc/network/interfaces*
*---*
*auto lo*
*iface lo inet loopback*


*auto eth0*
*iface eth0 inet static*
*	address AAA.BBB.CCC.DDD*
*	netmask 255.255.255.240*
[I]	gateway EEE.FFF.GGG.HHH

[/I]*auto eth1*
*iface eth1 inet manual*



*auto br0*
*iface br0 inet dhcp*
*	bridge_ports eth1*
*	bridge_stp off*
*	bridge_fd 0*
*	bridge_maxwait 0*
*---*




Due to a monitoring tool, i need an internall static ip (192.168.88.0/24) on this server (DCHP will cause troubles on monitoring when the interfaces or machine were restarted) and dhcp (for KVM) on bridge (br0) at the same time.


I tried to create two bridges using interface eth1 (DHCP for one and STATIC for the other) but it not solve because both bridges used the same interface and it caused conflicts.


I don't know how to solve this issue.


Can somebody help me?


Cheers,
Gonçalo

---

