---
title: "Packet sniffer?"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by atsab on 2007-09-21
I have been using Ubuntu a wile now but i have never until recently thought much about how secure it was. Recently new people have moved into the same building as me (where all residents shear a wireless network) and there behaviour has prompted me to secure up my installation. I visited this site and followed there advice [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

on this site it recommends a root kit checker (i don't know what a root kit is so but i thought i should check for them anyway)

i ran chkrootkit and i think everything was ok but i did notice these two lines:

eth0:avahi: PACKET SNIFFER(/sbin/dhclient3[5652], /usr/sbin/avahi-autoipd[5571])
wlan0: PACKET SNIFFER(/sbin/dhclient3[5141])

is there anything sinister here or am i being paranoid.

---

### Post by mills on 2007-09-21
iam not an expert on avahi but i would say your ok, avahi's a netwoking thing so i guess it has an excuse to sniff frames/packets

```
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[5097], /usr/sbin/snort[4701])
```

thats what i get when i run chkrootkit but snort is something i installed so its legit, are you geting the first line?

you might want to double check with rkhunter which apparently gives fewer false positives

---

### Post by lepus on 2007-12-16
I suggest you have a look at [http://ubuntuforums.org/showthread.php?t=270340](http://ubuntuforums.org/showthread.php?t=270340)

---

