---
title: "Why this chain to enable yahoo messenger?"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by arsham on 2007-11-26
Hi there
I have a LAN here :

laptop ]--------[ desktop ] ---------[ internet
..................eth1.........eth0

and a ppp0 interface is my pppoe account :

Laptop :
eth0 :192.168.1.5

desktop :
eth1 :192.168.1.10
eth0 : 192.168.1.9
ppp0 : dynamic IP from DHCP server


I have enabled masquerading to enable my laptop to use the internet :

iptables -A POSTROUTING -o ppp0 -j MASQUERADE

but my yahoo messneger ( pidgin ) is not signing up , unless I add this to my iptables :

iptables -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

Why is that?
How to claim my problem without that?

---

