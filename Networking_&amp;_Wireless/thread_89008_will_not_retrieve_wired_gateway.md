---
title: "will not retrieve wired gateway"
date: 2005-11-11
forum: Networking &amp; Wireless
---

### Post by dannemil on 2005-11-11
This has driven me nuts for weeks on end. I have two network configurations - one wired (eth0) and one wireless (eth1). The wired one uses a static IP address. In the /etc/network/interfaces file under the eth0 section

iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx

It has the correct entries for this connection including the default gateway (I substituted xxx above for the actual values). Yet every time I switch to this connection in the Network Manager, it gets the correct IP address and netmask, but the default gateway entry is blank, and I have to type it in to get it to work. If it is reading the correct ip address and netmaks from  this file, why does it ignore the gateway?

---

### Post by Gcool on 2005-11-12
Perhaps try this (i'm using a 192.168 range as an example):

auto eth0
iface eth0 inet static
address 192.168.1.2
network 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255

---

### Post by Matchless on 2005-11-12
[QUOTE=dannemil]This has driven me nuts for weeks on end. I have two network configurations - one wired (eth0) and one wireless (eth1). The wired one uses a static IP address. In the /etc/network/interfaces file under the eth0 section

iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx

It has the correct entries for this connection including the default gateway (I substituted xxx above for the actual values). Yet every time I switch to this connection in the Network Manager, it gets the correct IP address and netmask, but the default gateway entry is blank, and I have to type it in to get it to work. If it is reading the correct ip address and netmaks from  this file, why does it ignore the gateway?[/QUOTE]

Hi this is a bug report that may help you.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=9871](https://bugzilla.ubuntu.com/show_bug.cgi?id=9871)

---

