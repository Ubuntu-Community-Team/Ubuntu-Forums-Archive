---
title: "Routing static IP on server 14.04.1"
date: 2014-11-12
forum: Networking &amp; Wireless
---

### Post by cocolino2 on 2014-11-12
Hello,

I need help with routing static ip addresses for web hosting.

I have one static ip witch is direct connected on server witch is setup as p1p1 and i need to setup another subnet class of 16 IP's on server.


so...

on /etc/network/interfaces must to add..

auto lo
iface lo inet loopback

auto p1p1
iface p1p1 inet static
address xxx.xxx.xxx.190
netmask 255.255.255.224
network xxx.xxx.xxx.160
broadcast xxx.xxx.xxx.191
gateway xxx.xxx.xxx.161

and for another subet class of 16 zzz.zzz.zzz.80/28 IP's is ok if i add..

auto p2p1
iface p2p1 inet static
address zzz.zzz.zzz.80
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

auto p3p1
iface p3p1 inet static
address zzz.zzz.zzz.81
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

auto p4p1
iface p4p1 inet static
address zzz.zzz.zzz.82
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

and so until p17p1 zzz.zzz.zzz.96

Thanks!

---

### Post by bab1 on 2014-11-13
> **cocolino2 said:**
> Hello,

I need help with routing static ip addresses for web hosting.

I have one static ip witch is direct connected on server witch is setup as p1p1 and i need to setup another subnet class of 16 IP's on server.


so...

on /etc/network/interfaces must to add..

auto lo
iface lo inet loopback

auto p1p1
iface p1p1 inet static
address xxx.xxx.xxx.190
netmask 255.255.255.224
network xxx.xxx.xxx.160
broadcast xxx.xxx.xxx.191
gateway xxx.xxx.xxx.161

and for another subet class of 16 zzz.zzz.zzz.80/28 IP's is ok if i add..

auto p2p1
iface p2p1 inet static
address zzz.zzz.zzz.80
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

auto p3p1
iface p3p1 inet static
address zzz.zzz.zzz.81
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

auto p4p1
iface p4p1 inet static
address zzz.zzz.zzz.82
netmask 255.255.255.240
gateway xxx.xxx.xxx.190

and so until p17p1 zzz.zzz.zzz.96

Thanks!

Why do you *need * to use multiple IP addresses with your web server?  I only use Apache and use virtual hosts (one IP address --> multiple virtual domains).  IMHO it's easier to maintain website separation by domain name rather than having multiple IP addresses for one host that has only one interface.

If you want a server to appear to have multiple IP addresses you create IP address aliases of your single network interface IP address.  

For more info see [here]("https://www.google.com/search?q=multiple+ip+addresses+per+interface+linux&btnG=Go!&gws_rd=ssl#q=multiple+ip+addresses+per+interface+ubuntu").

---

