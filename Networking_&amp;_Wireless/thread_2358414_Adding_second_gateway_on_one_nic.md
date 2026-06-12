---
title: "Adding second gateway on one nic"
date: 2017-04-13
forum: Networking &amp; Wireless
---

### Post by fvdberghe on 2017-04-13
Hi, im not newto ubuntu.
Is it possible to add a second gateway to one NIC

This is my config for the moment with one nic
Need to add seconde gateway =192.168.1.71
auto lo
iface lo inet loopback
auto em1
iface em1 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.250
dns-nameservers 192.168.1.250

Thanks in advance

---

