---
title: "ubuntu 14 vlan tagged interface"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by dave219 on 2016-02-05
hi all:

what is proper way to make my ethernet interface vlan tagged? here is what i have and i suspect it is not properly configured since my box would not put packets out of the interface:

auto lo

auto eth0
iface lo inet loopback
iface eth0 inet static
address 10.0.0.10
netmask 255.255.255.128
up route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.0.0.1


auto eth1.10
iface lo inet loopback
iface eth1.10 inet static
address 100.0.0.10
netmask 255.255.255.0
gateway 100.0.0.1


root@host:~# ping 100.0.0.1
PING 100.0.0.1 (100.0.0.1) 56(84) bytes of data.
From 100.0.0.10 icmp_seq=1 Destination Host Unreachable
From 100.0.0.10 icmp_seq=2 Destination Host Unreachable
From 100.0.0.10 icmp_seq=3 Destination Host Unreachable
^C
--- 100.0.0.1 ping statistics ---
18 packets transmitted, 0 received, +15 errors, 100% packet loss, time 17094ms
pipe 3

Linux lab-vm10 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

thanks

_dave

---

