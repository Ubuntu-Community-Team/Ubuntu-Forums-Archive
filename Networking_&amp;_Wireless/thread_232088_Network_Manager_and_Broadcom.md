---
title: "Network Manager and Broadcom"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by jkh107 on 2006-08-08
I have a Broadcom wireless card that I managed to get working using the bcm43xx driver. When I set it up using System >Administration >Networking it worked fine. However, when I try to use network-manager-gnome instead (commenting out everything except lo in /etc/network/interfaces) nothing happens - it doesn't detect any networks at all. I've noticed that the power light on the card itself isn't coming on when the computer starts, so I assume the card isn't getting picked up when the system starts. Please help!

---

### Post by jeff_ on 2006-08-08
First of all tintin rocks.

Second, I too have a broadcom wireless card supported by the bcm43xx driver. My card works fine through ndiswrapper. Why do you want to use network-manager-gnome? What's your ifconfig and iwconfig output when the card does not work?

---

### Post by KevinDM on 2006-08-08
I have the same problem, ndiswrapper will show the card as detected and working, but I get no connection. The network-manager won't let me input static ip (throws an error)and DHCP does nothing at all. iwconfig shows nothing woking too. Is there another way to configure the card besides with net-manager in gnome?

---

### Post by jkh107 on 2006-08-09
Glad someone else appreciates Tintin!

I want to use network-manager-gnome so that I can take my laptop around with me, detect and connect to wireless networks, so I'm not restricted to just one. It seems the card isn't being activated when the system starts, so the network-manager-gnome program can't use it to connect to anything.

---

### Post by jeff_ on 2006-08-09
Both of you should try this HOWTO. It is honestly the easiest HOWTO for wireless setup I've ever seen and worked for me after much else failed.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

