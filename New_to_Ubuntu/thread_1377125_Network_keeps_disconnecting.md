---
title: "Network keeps disconnecting"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by 12-1-50 on 2010-01-09
I am sorry, I don't know to much about networking but I'll try to be as specific as possible. I connect to my router, it works (very slow), I am disconnected, I am reconnected. Just like that disconnect,reconnect,disconnect,ect. The light on my laptop keeps flashing different colors when it should be continually blue.

---

### Post by spiderbatdad on 2010-01-09
Could you open your terminal Applications>>Accessories>>Terminal
Type in or copy/paste these two commands one at a time?
```
lspci | grep net
dmesg | tail
```
Paste the terminal output into a new post here, inside CODE tags by clicking the little # symbol in the editor menu of the reply window.

---

### Post by 12-1-50 on 2010-01-09
[CODE]william@laptop:~$ lspci | grep net
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
william@laptop:~$ dmesg | tail
[   50.146414] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   50.150920] i2c-adapter i2c-2: unable to read EDID block.
[   50.150923] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   52.268735] wlan0: authenticate with AP 00:17:3f:0c:ba:d2
[   52.273218] wlan0: authenticated
[   52.273222] wlan0: associate with AP 00:17:3f:0c:ba:d2
[   52.276684] wlan0: RX AssocResp from 00:17:3f:0c:ba:d2 (capab=0x411 status=0 aid=2)
[   52.276688] wlan0: associated
[   52.277085] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.892085] wlan0: no IPv6 routers present
[CODE]

---

### Post by spiderbatdad on 2010-01-09
Not familiar with this card myself nor its driver, but this blog here looks like it might get you rolling: [http://www.joewein.net/blog/2009/11/13/marvell-mc85-with-ndiswrapper-on-ubuntu-9-10/](http://www.joewein.net/blog/2009/11/13/marvell-mc85-with-ndiswrapper-on-ubuntu-9-10/)

---

