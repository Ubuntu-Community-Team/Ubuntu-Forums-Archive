---
title: "Ad-hoc wireless networking"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by waster on 2007-04-21
Does anyone have trouble with ad-hoc netorking?

Network Manager doesn't support it, so I am using static IP addresses. Everything looks connected from the wireless side: Mode is ad-hoc, Cell is filled in, essid is correct, but I cannot ping in either direction.

I understand there are two different ad-hoc modes: demo and one other. How can I tell which computer is using which protocol?

---

### Post by spd106 on 2007-04-22
I haven't tried adhoc on feisty yet so forgive me if I'm in error. As far as I know Network Manager is capable of connecting to adhoc networks and avahi-autoip should make this much easier. You might want to install the avahi-utils and avahi-discover.

---

### Post by waster on 2007-04-26
My problem is bcm43xx which does not seem to do ad-hoc correctly. I will file a bug. Using ndiswrapper gives a perfectly working ad-hoc connection. I'm using an awful Broadcom 4306 card.

---

### Post by pgilmon on 2007-04-29
I was having problems to connect to an ad-hoc network with feisty (WEP-enabled). In order to get it to work I just set it up with Network-manager (I disabled roaming mode). Then, I entered the ESSID and password and I chose DHCP. After that, I opened a console and typed:
```
sudo iwconfig wlan0 mode ad-hoc
sudo ifdown wlan0
sudo ifup wlan0
```

and now it works OK

I'm using a Zyxel B-220 usb dongle, that I got to work by following instructions that I found [here]("http://ubuntuforums.org/showthread.php?t=256025").

---

