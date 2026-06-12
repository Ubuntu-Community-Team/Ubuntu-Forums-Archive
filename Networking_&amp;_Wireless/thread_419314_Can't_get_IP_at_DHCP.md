---
title: "Can't get IP at DHCP"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by minavana on 2007-04-22
SMC2835W wireless card and D-Link AP-router.
Wireless card seem to work well - I see all WiFi networks arround and AP shows my laptop like connected. But I can't get any IP at DHCP. When I give IP, gatewy and DNS manually, no internet connection to. Network is opened, no any WEP key. IPv6 is disabled. Two other laptops, XP and SUSE are connected and works well. What I had better to do?

---

### Post by spd106 on 2007-04-24
I suggest that you examine your /var/log/syslog file for any errors or sticking points. If you are unsure then please post it here and we will take a look.

Common problems are a failure to associate, failure to complete handshake (authenticate) or DHCP times out and avahi-autoip kicks in.

---

