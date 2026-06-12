---
title: "My wireless G card running at B speeds. What do i do?"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by WalmartSniperLX on 2006-08-18
Im connected to my network and everything works fine except that im only connected at 11mbs when I should get 54mbs. How do I get my wireless card working at its full speed (Wireless G)?

---

### Post by Dun on 2006-08-19
> **WalmartSniperLX said:**
> Im connected to my network and everything works fine except that im only connected at 11mbs when I should get 54mbs. How do I get my wireless card working at its full speed (Wireless G)?
Well it's kind of hard to say as you don't give any details of your wlan card or anything else for that matter. If you have bcm4318 with native kernel driver you should know that it only works at 11 Mb/s.

---

### Post by spd106 on 2006-08-20
It could also be that there is another wifi device nearby that's limited to 802.11b, which causes your card to step down for compatibility.

Or maybe you just need to move closer to the AP.

---

### Post by lupine_nickt on 2006-08-20
Assuming the router can cope with 802.11g speeds, the presence of a .b device  wouldn't affect a .g device's speed. It would adversely affect the .b device's speed, however.

Try running sudo iwconfig <interface> rate 54M

xF,

...Nick

---

