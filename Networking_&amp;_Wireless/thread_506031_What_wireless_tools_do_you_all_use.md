---
title: "What wireless tools do you all use?"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by subaruwrx on 2007-07-21
Currently, I am using the wifi-radar.

However, I am unable to set priorities of which network to connect to. Hence it would always connect to the wrong network.

Is there one tool whereby it can auto connect to the network I selected for it on startup?

Thanks.

---

### Post by djdicbob on 2007-07-21
I am not sure of a tool that will choose for you, however refer to this file ....
```
/etc/networks/interfaces
```
as root or sudo add these lines...
```
auto eth1
iface eth1 inet dhcp 
  wireless-essid MyESSID 
  wireless-key 12345678
```
whereas eth1 = your specific interface.  You then need to reboot and test!   Depending on your security setup you may need some extra steps.  Look here ---->[Debian_rt2500_Howto]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")

---

### Post by subaruwrx on 2007-07-21
> **djdicbob said:**
> I am not sure of a tool that will choose for you, however refer to this file ....
```
/etc/networks/interfaces
```
as root or sudo add these lines...
```
auto eth1
iface eth1 inet dhcp 
  wireless-essid MyESSID 
  wireless-key 12345678
```
whereas eth1 = your specific interface.  You then need to reboot and test!   Depending on your security setup you may need some extra steps.  Look here ---->[Debian_rt2500_Howto]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")

THanks I was looking for some graphical tool actually.

---

### Post by djdicbob on 2007-07-21
Have you tried the Kwifimanage from KDE????

---

### Post by subaruwrx on 2007-07-21
> **djdicbob said:**
> Have you tried the Kwifimanage from KDE????

I'm using Gnome. Is that okay?

---

