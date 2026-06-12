---
title: "connection loss in Ubuntu"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by dujlinvik on 2006-12-27
Hi, i'm newbie in Linux and confused about some things which aren't suppose to happen... Namely, i have a wireless connection to the net (pppoe via a wireless network), i've configured my connection (IP assigned by DHCP, no encryption, DNS servers added), everything is workig fine for some time (10 minutes, half an hour, 2 hours...), but then for some reason i simply lose the connection.... then i have to "go" to the Networking tab and to select my saved connection every time when this happens...
Any ideas?

---

### Post by maxamillion on 2006-12-27
I could be completely off on this, but it sounds like when the ip address is re-leased from the wifi access point your machine isn't picking up on the need to renew its ip lease or retrieve a new one. Next time it happens try opening a terminal and typing ```
sudo dhclient
```
I can't promise much, networking problems like this are generally "fun" to diagnose and that is just the first thing that came to mind.

---

