---
title: "&quot;Location&quot; change: dhcp versus static ip"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by stijngysemans on 2008-06-11
ubuntu 8:04
location A is configured with a dhcp
location B is configured with a static ip
When changing the location from B to A, i do not get an ip assigned automatically from my dhcp server. I must manually go to the terminal and type sudo /etc/init.d/networking restart.

Is this a bug, because in windows, changing from static to dhcp (not in location, but in the configuraiton itself) invokes a dhcp/renew.

---

