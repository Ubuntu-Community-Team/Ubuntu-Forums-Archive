---
title: "Linksys WPC54G v5 Installed but not connecting.."
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by pagangeek on 2008-07-30
Hail!
I've followed instructions for getting this particular card working using ndiswrapper, however, after configuring using nm-applet it seems unable to connect to the internet.

The card detects my network, my wpa key works fine, but netstat -rn returns:

```
Kernal IP routing table
Destination     Gateway     Genmask     Flags     MSS   Window   irtt    Iface
169.254.0.0     0.0.0.0     255.255.0.0 U         0     0    0 wlan0
0.0.0.0      0.0.0.0     0.0.0.0     U     0     0     0 wlan0
```

I've tried setting up an IP manually, but it doesn't seem to work. I'd greatly appreciate any help or pointers!
Thank you in advance :-)

---

### Post by pagangeek on 2008-08-02
following various guides in the wifidocs, ive managed to get to a different stage.

My card is now recognized, the driver works.. I can run iwlist and can see my router.. but.. attempting to connect to any wireless network results in failure. Even completely open unseccured ones.

Please advise :-D

---

