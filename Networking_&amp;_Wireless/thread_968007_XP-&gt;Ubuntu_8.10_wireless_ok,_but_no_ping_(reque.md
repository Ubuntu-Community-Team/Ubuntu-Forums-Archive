---
title: "XP-&gt;Ubuntu 8.10: wireless ok, but no ping (request timed out)"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by tintin1 on 2008-11-02
I have 2 machines:

XP (192.168.100.100) -> Ubuntu (192.168.100.1)

Ubuntu creates an ad-hoc wireless network.
XP connects to Ubuntu, strong signal, password accepted, its ok.

But I can't ssh or even ping XP->UBuntu, it says "Request timed out".

Ubuntu's /etc/network/interfaces:

auto eth1
iface eth1 inet static
address 192.168.100.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-essid secret
wireless-key XXXXXXXXXX

XP's ipconfig:

Ethernet adapter Wireless Network Connection:
Connection-specific DNS Suffix  . : 
IP Address. . . . . . . . . . . . : 192.168.100.100
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.100.1

Please, help.

---

