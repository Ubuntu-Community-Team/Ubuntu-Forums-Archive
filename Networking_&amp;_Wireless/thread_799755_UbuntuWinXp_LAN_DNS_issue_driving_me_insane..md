---
title: "Ubuntu/WinXp LAN DNS issue driving me insane."
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Feendish on 2008-05-19
Hi all,

I'm having major DNS troubles with my Gutsy server and WinXP clients. The server can ping the clients by IP and vice versa. The clients can ping each other by name but not the server by name. The server cannot ping the clients by name either. The server and clients are connected together via a Belkin router and Linksys switch which is extending the router ports. Some of the clients are assigned IPs via DHCP from the router, one is assigned a static IP and the server is assigned a static IP. All machines have access to the external Internet without any issue. I've tried loads of tutorials from here to try and fix this including Bind9, removing IPv6, dnsmasq and Winbind. Does anyone have any ideas? It was working fine up to the point where I tried removing IPv6 via the /etc/modprobe/aliases file as it was suggested this may solve some ssh issues I was having.

---

