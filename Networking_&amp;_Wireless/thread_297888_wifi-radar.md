---
title: "wifi-radar"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by chajuram on 2006-11-11
Hi,

I installed wifi-radar. At some point of time in the process of setting up my wireless card it was called eth1. Now when I run wifi-radar I get the message

> 
ritwik@ritwik-laptop:~$ sudo wifi-radar
dhclient3 --version 2>&1
eth1      Interface doesn't support scanning.

eth1: error fetching interface information: Device not found
eth1      No such device


I tried a reinstall but it did not help. Any help is appreciated. 

Chajuram.

---

### Post by FrodoB on 2006-11-12
I may be misinformed, but if your device does not support scanning, and not all do, then wifi-radar will not work for you.

Maybe someone can chime in with better news?

---

### Post by chajuram on 2006-11-14
I don't exactly know what you mean by scanning. But it did work for some time. I am now using NetworkManager with reasonable success. 

I still don't know what the deal is with eth1 and wlan0, my wireless card is called eth1 or wlan0 with every other reboot. It really confuses me. 

Chajuram.

---

