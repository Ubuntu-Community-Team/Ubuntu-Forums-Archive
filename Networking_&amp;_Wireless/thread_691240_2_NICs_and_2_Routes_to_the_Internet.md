---
title: "2 NICs and 2 Routes to the Internet"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by Spenzer4Hire on 2008-02-08
I have an Ubuntu 7.10 box connected to 2 different networks, both with internet access.  Both assign the box a "static" IP via DHCP.  ie:

eth0 192.168.10.10 netmask 255.255.255.0 gateway 192.168.10.254 dns 192.168.10.254

eth1 192.168.30.10 netmask 255.255.255.0 gateway 192.168.30.254 dns 192.168.30.254

This works just fine for a while, but then Firefox will stop connecting to websites, although nslookup and ping still work.  It is like Ubuntu (or Firefox) is getting confused about its routes.  Changing one of the NICs to static with no default gateway fixes the issue.  It would be nice to use DHCP on both interfaces.  Any ideas?

---

### Post by rvjcallanan on 2008-02-11
Your problem has certain similarities to mine at:

[http://ubuntuforums.org/showthread.php?t=691218]("http://ubuntuforums.org/showthread.php?t=691218")

Coincidently, both posts were submitted around the same time :-)

Solutions previously suggested to me include arp-filter and bonding. Arp-filter looks the most promising but suffers from the problem that ARP broadcasts are only transmitted on the first NIC in the routing table. What we need is a round-robin mechanism whereby, an attempt is made to connect to the destination address via each NIC in turn. Bonding may be the solution, but is it possible to "bond" at the IP layer in such a way that the NICs are otherwise isolated? Perhaps this is something you might investigate while I look at an ARP filter solution.

Here are some links to go on:

[http://linux-ip.net/html/ether-arp.html]("http://linux-ip.net/html/ether-arp.html")

[http://downloadmirror.intel.com/5154/ENG/e100.htm]("http://downloadmirror.intel.com/5154/ENG/e100.htm")

[http://ubuntuforums.org/archive/index.php/t-566908.html]("http://ubuntuforums.org/archive/index.php/t-566908.html")

[http://mailman.ds9a.nl/pipermail/lartc/2005q2/015790.html]("http://mailman.ds9a.nl/pipermail/lartc/2005q2/015790.html")

[http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding]("http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding")

I will post more info if I get a satisfactory solution

---

