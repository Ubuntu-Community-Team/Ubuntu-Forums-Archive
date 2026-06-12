---
title: "Kismet broke NetworkManager!"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by haxality on 2006-11-20
I recently installed Kismet, and learned that it had support for ipw2100 drivers, which I happened to have in my laptop. After configuring and running Kismet, I quit and attempted to re-enable my wireless card with NetworkManager. NM reported that it connected to my wireless network. However, I recieved an APIPA IP address and could not talk to any of the other computers on my home LAN. When I use network-admin to connect to the AP, it works fine. What gives? I've tried rebooting, modprobe -r ipw2100, restarting most of my network daemons, and nothing seems to work! Any help would be much appreciated.

---

