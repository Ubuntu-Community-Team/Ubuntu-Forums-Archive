---
title: "WiFi AP on RasPi"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by emueyes on 2016-01-05
Hi

I have a WiPi USB dongle connected to a Pi2, one of the white "official" ones. It works fine to connect to my home WiFi network, but I can't get it to act as an access point.

lsmod shows its drivers and dependencies as


```
rt2800usb              26349  0
rt2800lib              81400  1 rt2800usb
rt2x00usb              17747  1 rt2800usb
rt2x00lib              42044  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              451264  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              376661  2 mac80211,rt2x00lib
crc_ccitt              12350  1 rt2800lib
```


I'm thinking that my [COLOR=#333333][FONT=monospace]hostapd.conf is the problem, I don't know what driver name/string to enter there, rt2800lib, rt2800usb...

[/FONT][/COLOR]I've also seen and have the DPO_RT5572 package, should I be using this instead ? The adapter seems to work fine with the rt2800 drivers even though lsusb says it's an Ralink Technology, Corp. RT5370 Wireless Adapter

I'm running Ubuntu 14.04 LTS with kernel 3.18.0-25-rpi2

Thanks for any help, or a pointer to a good guide to setting up an AP as I'm trying to do.

---

