---
title: "how do I set default ESSID on WiFi???"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by altgrrr on 2007-10-06
Using: Ubuntu Feisty


I use Roaming Mode for my wireless connection but that usually ends up connecting me to my neighbor's router instead of my own. I solved that by editing /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid MYESSID

#auto ath0
#iface ath0 inet dhcp
#wireless-essid MYESSID
```


Ok, now this works fine, I get connected to MYESSID but I do use my laptop at home AND in school, which means I could really use Roaming Mode, right???

**So, now for the question:**
Can I use roaming mode and still have some kind of priority list of which network I preferr to connect to?

And another thing: Do I really need all those lines in my interfaces file??? I really only have the eth0 and wlan0, and the loopback also I guess. What are those other eth2 etc doing there?

---

### Post by kevdog on 2007-10-06
You can delete all those extra interfaces in the interfaces file since you dont need them.  It should make the booting process faster.

I dont think there is a way with network manager to specify a default preference list. Sorry.  I think with WICD this is possible however.

---

