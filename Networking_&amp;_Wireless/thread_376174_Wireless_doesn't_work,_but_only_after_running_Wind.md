---
title: "Wireless doesn't work, but only after running Windows"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by fearpi on 2007-03-04
I am dual booting Ubuntu Edgy and Windows XP. Normally, my wireless works without a hitch on both systems. I have noticed, however, that when I have been running Windows and reboot into Ubuntu, often I can not connect to the internet using my wireless device. I can see all the access points using **iwlist eth1 scan**, but when I try to connect by doing **iwconfig eth1 essid <essid>**, I get no connection.

My device is an Intel Corporation PRO/Wireless 3945ABG.

Any ideas on why this is, or how to get any data that would help in diagnosing the problem?

---

### Post by maddog39 on 2007-03-04
Have you tried using a WiFi manager such as Wifi-radar (availible in the repositories) to connect and disconnect a few times. That usually works for me when I have this problem. Even if I do it from System > Adminstration > Networking

---

### Post by fearpi on 2007-03-05
Well, it's a bit tricky because the network I connect to is hidden. I see in the list "GTwireless", the name of the network that my card is configured to be connected to. GTwireless is supposed to be hidden though, and I also see a network named <hidden>. I'm not sure if they both represent detected networks, or if GTwireless is there just because the card is currently set to connect to that one. Anyway, I can't connect to either, until I reboot.

---

