---
title: "Can Ubuntu pick up networks in your area?"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Heyholetsgogrant on 2006-11-12
Can ubuntu pick up wirless networks in your area automatically? if so how? is their a way to select them from a list?

thanks,

Grant

---

### Post by towsonu2003 on 2006-11-13
I use ```
sudo iwlist eth1 scan
``` to get a list of available wireless networks and use iwconfig to connect to one. My usual steps to connect to one are as follows:
```

sudo dhclient -r eth0 && sudo ifconfig eth0 down #take down wired device
sudo ifconfig eth1 up
sudo iwlist eth1 scan
sudo iwconfig eth1 essid myessidhere
sudo iwconfig eth1 ap th:em:ac:ad:dr:es:si:fn:ee:de:db:la #the mac address of the wireless access point that is
sudo iwconfig eth1 key ifyouhaveakeyitgoeshere
sudo dhclient eth1

```
then I start the firestarter (firewall). 

eth0 is ethernet card; eth1 is wireless card.

ps. I have a script to do all this stuff :)

---

