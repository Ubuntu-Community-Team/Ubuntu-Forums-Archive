---
title: "VPN between FreeBSD and Ubuntu"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by wahonez on 2007-02-09
Had a FreeBSD server die on me ](*,) , and happened to have a ubuntu box around to replace it for NAT / DHCP, but am a little lost on how i would go about connecting it to the existing VPN.

Configuration on the Freebsd boxes was as follows:
> FREEBSD connection on Local server
ifconfig gif0 create
gifconfig gif0 external.ip.of.local external.ip.of.remote
ifconfig gif0 10.0.0.1 192.168.7.1 netmask 255.255.255.0
route add 192.168.7.0  192.168.7.1

FREEBSD connection on Remote server
ifconfig gif0 create
gifconfig gif0 external.ip.of.remote external.ip.of.local
ifconfig gif0 192.168.7.1 10.0.0.1 netmask 255.255.255.0
route add 10.0.0.0 10.0.0.1

The Remote server is the one that i'm replacing.
Barring putting together another FreeBSD box is there a simple way for me to do the above on ubuntu?

---

