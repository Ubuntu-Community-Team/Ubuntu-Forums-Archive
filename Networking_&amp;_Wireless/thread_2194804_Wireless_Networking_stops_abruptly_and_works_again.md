---
title: "Wireless Networking stops abruptly and works again for sometime after restart?"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by nsteja1 on 2013-12-20
[COLOR=#333333][FONT=UbuntuRegular]I have been working on Ubuntu (12.04) for ages now but all of a sudden I have been facing this problem for two weeks now.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I start my laptop, ubuntu connects to a wireless network and I browse for a couple of minutes on Chrome and all of a sudden the network stops responding - it shows "**Resolving host**" or "**Connecting...**" and nothing comes up. I cannot even ping any other machine or do an "nslookup" - everything fails. The wireless is still connected to AP but everything stops responding.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I have to put the system to sleep and open it again to browse for another couple of minutes and then this happens again.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any help on this is appreciated! It has been a great pain for weeks now.[/FONT][/COLOR]

---

### Post by tfrue on 2013-12-21
Unplug the router, let it sit for a bit, then plug it back in and try that on for size.

If that doesn't help, will you post  the output of the commands:
```
sudo nm-tool
```
```
cat /etc/network/interfaces
```
```
dmesg | grep wlan
```
```
ifconfig -a 
```

Please and thank you!

---

