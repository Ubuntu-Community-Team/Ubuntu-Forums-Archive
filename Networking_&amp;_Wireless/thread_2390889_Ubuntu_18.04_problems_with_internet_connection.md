---
title: "Ubuntu 18.04 problems with internet connection"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by Chesslover on 2018-05-03
After upgrading from 17.10 (gnome fallback) to 18.04 my internet connection (almost) stopped working. In terminal I can not get ping 1.1.1.1 or 8.8.8.8 (unable to connect). In firefox I get few internet sites (like google), but mostly I just get error connecting. I suspect it is something to do with DNS settings, because I used to have systemd-resolved disabled and dnsmasq enabled. When I try to start dnsmasq I get error (failed to create listening socket for port 53: Address already in use.). There is process called dnsmasq listening on port 53 (other forum say it is probably dnsmasq-base from NetworkManager). I also tried to disable dnsmasq and enable systemd-resolved, but it doesn't work (I get no internet, even not google). My /etc/resolv.conf has no symbolic link in /run/resolvconf/resolv.conf (there is no such file). Can someone help me?

SOLVED: I deleted profile of ethernet connection in Network Manager and new connection worked:)

---

