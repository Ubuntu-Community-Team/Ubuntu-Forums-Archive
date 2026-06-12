---
title: "DNS unavalaible without reasons !!"
date: 2017-11-20
forum: Networking &amp; Wireless
---

### Post by Vincen_PUJOL on 2017-11-20
Hi

I run an Ubuntu Server 16.04.2 server (for a multimedia storage, plex server). That server is behind a regular Fiber internet connection. The router supplies DNS service for all computers on LAN without problems.
My server refuses to work for dns resolution. If I check content on resolv.conf it contains well just the IP of my router.
Gateway is also well defined and route too. If I do a traceroute on external ip it goes out without problems !!

Any ideas what's the problem there ?? 

Confused also about syntax of resolv.conf as some indicates you just have to list IP of DNS server(s) and some others with nameserver word in front ???

Thanks

Vincèn

---

### Post by SeijiSensei on 2017-11-20
If the machine gets its address via DHCP, it should also retrieve the nameserver's address during that transaction.

However servers usually have statically-assigned addresses via entries in /etc/network/interfaces.  In that file you need a "dns-nameservers" line that points to the server address(es) you want to use. See: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution)

---

