---
title: "Trouble giving LAN clients access to remote network via pptp"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by obrienmd on 2008-09-04
Hello - I have a remote network (3 computers, 192.168.0.0/24), which I'd like to give my local network (5 computers, 10.0.0.0/24) access to via my ubuntu 8.04.1 server gateway.

My local network ubuntu gateway computer is connected to the internet via a ppp0 interface.  My remote network gateway is connected to the internet on a public eth0 interface, both have no firewalls for testing's sake.

I've correctly configured routing on my local network gateway, as clients (10.0.0.199, for example), can reach normal web sites.

When I start pptp, my local network gateway can ping 192.168.0.0/0 computers (for instance, 192.168.0.2), and can use their services (for instance, http over telnet port 80).  However, none of my local network clients can reach 192.168.0.0/24 computers.

Any ideas?

---

