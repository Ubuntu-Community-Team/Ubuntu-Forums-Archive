---
title: "Wired connection (wlan0)"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by covert215 on 2007-06-20
For some reason, my DWL-122 USB wireless adaptor is registering as being a wired device in the network manager.

This is what returns whenever I run "ndiswrapper -l"
```
netprism : driver installed
        device (2001:3700) present (alternate driver: prism2_usb)

```

My /etc/network/interfaces look like:
```
auto lo
iface lo inet loopback

auto etho0
iface eth0 inet dhcp


iface wlan0 inet dhcp

auto eth0
```

I'm pretty sure it SHOULD look like (this doesn't work though):
```
auto lo
iface lo inet loopback

auto etho0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXXXX
wireless-key XXXXXXXXX

```

---

### Post by rcsarver on 2007-06-20
I have the same problem! please keep me posted if you figure out what is causing it. I will do the same.

---

### Post by rcsarver on 2007-06-20
My problem has been fixed. Maybe it will help you, too.

[thread]2884268[/thread]

It fixed my connection and the "wired" wireless connection was changed to "wireless" in network-admin.

---

### Post by fragilerus on 2007-07-15
rcsarver, can you post another means of getting to that discussion (such as title)? i am having the exact same problem and the link you supplied is dead. much appreciated.

---

### Post by MyR on 2007-07-15
Install the linux-wlan-ng package. See
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122](https://help.ubuntu.com/community/WifiDocs/Device/DWL-122)

---

