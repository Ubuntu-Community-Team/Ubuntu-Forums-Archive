---
title: "Ubuntu 14.04 Wifi won't Authenticate"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by alex339 on 2015-03-01
Just switched over to Ubuntu today kind of out of necessity. Only have wifi as an option, bought a Linksys AE1200 and followed this guide [http://ubuntuforums.org/showthread.php?t=2223902](http://ubuntuforums.org/showthread.php?t=2223902)


Driver is installed and computer is detecting the card and seeing Wifi networks. When I try to connect to my WPA personal wifi it fails to authenticate/connect. Keeps popping up asking me to enter the key. 

Any solutions? Please help!

---

### Post by jeremy31 on 2015-03-01
> **alex339 said:**
> Just switched over to Ubuntu today kind of out of necessity. Only have wifi as an option, bought a Linksys AE1200 and followed this guide [http://ubuntuforums.org/showthread.php?t=2223902](http://ubuntuforums.org/showthread.php?t=2223902)


Driver is installed and computer is detecting the card and seeing Wifi networks. When I try to connect to my WPA personal wifi it fails to authenticate/connect. Keeps popping up asking me to enter the key. 

Any solutions? Please help!

Can you change the wifi router settings to WPA2 only?  A better USB option would be the [COLOR=#444444][FONT=UbuntuRegular]TP-Link TL-WN821N as it has kernel in-tree drivers where your AE1200 relies on ndiswrapper[/FONT][/COLOR]

---

### Post by alex339 on 2015-03-01
WIll do, it is currently set to WPA2 PSK, actually, will configure it now and report back. 

AE1200 is my only option, but I did get driver installed through ndiswrapper

---

