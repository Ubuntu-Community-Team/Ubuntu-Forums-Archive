---
title: "WPA-PSK and TKIP"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by dgm on 2007-02-15
Finally got wireless internet working (for the most part) via ndiswrapper on my BCM4318 in Ubuntu Edgy 6.10. I can connect to most networks with ease. I do so via Wifi-Radar. Now I just need to figure out how to connect to my school's networks. I can connect to them easily in Windows, but when I try in Edgy, Wifi-Radar tries to "acquire the ip address" and then fails. I presume it has to do with the fact that the networks use WPA-PSK and TKIP encryption. Anybody know how I can get connected? Any help appreciated.

Regards,
dgm

---

### Post by maxamillion on 2007-02-15
if you are on gnome and using edgy:

```
sudo aptitude install network-manager-gnome
```

log out, log back in ... use the little network thing in the top right corner to config

I personally use Xubuntu, but a friend reported that this tool does WPA-PSK flawlessly (not sure about TKIP though) under his standard Ubuntu install using his broadcom 4306 card

... hope that helps

---

