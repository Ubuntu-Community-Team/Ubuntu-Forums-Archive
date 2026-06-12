---
title: "Wifi problems - iwconfig"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by bplus on 2009-07-19
Hi,
I have just installed ubuntu 9.04 amd64-bit edition on my laptop.
The little wifi icon in the top right of the screen is showing "no network connection" when I however over it.

However iwconfig seems to be showing my wifi network, i.e. its managed to find the name of my network so I'm assuming it is connected some how:

```
wlan0 IEEE 802.11bg ESSID:"**MyWiFiNetworkName**"
Mode: Managed Frequency:2.462 GHz Access Point 00:18:4D:96:0A:3E
Bit Rate=1Mb/s Tx=Power=27 dBm
Retry min limit:7 RTS thr:off Fragment thr=2352 B
Power Management: Off
Link Quality=94/100 Signal Level:29/100
Rx invalid nwid:0 Rx invliad crypt:0 Rx Invalid Frag:0
Tx excessive retries:0 Invalid misc:0 Missed Beacon:0
```

Anybody got any ideas on how I should proceed?

Thanks in advance!

---

### Post by LewRockwell on 2009-07-19
these issues are sometimes resolved by simply rebooting your router and other assorted equipment

.

---

### Post by grappler on 2009-07-19
I have  a feeling you're connected. I've just done iwconfig on my machine - which is certainly connected - and there's nothing significantly different from yours. I think it would say "Not associated" if you weren't connected. What does ifconfig tell you?

---

