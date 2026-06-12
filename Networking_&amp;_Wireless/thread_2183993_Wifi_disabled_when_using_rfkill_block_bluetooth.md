---
title: "Wifi disabled when using rfkill block bluetooth"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by sakinyu on 2013-10-27
Hi! I'm using dell with ubuntu 12.04. I was looking around, but I cannot find the solution... When I lock bluetooth the wireless is also blocked... And when I use "rfkill unblock bluetooth", bluetooth is "hard block=yes". Unblock is supposed to unblock, no???

So rfkill list: Soft and hard are all = no.

rfkill block bluetooth :

wireless LAN
soft blocked= no
hard blocked = yes

bluetooth
softblocked=yes
hardblocked=no

And when using "rfkill unblock bluetooth":

wireless LAN
soft blocked= no
hard blocked = yes

bluetooth
softblocked=yes
hardblocked=YES

Somebody know how to fix it??? I just want to disable BLUETOOTH but NOT wireless!

thanksss!!

---

