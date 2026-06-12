---
title: "I need help with getting wlan0 to work"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by geezas on 2006-12-17
Help me with wireless setup, thanks
Hey, everybody, it's me again...
I have dapper drake.
I am using the internet through a cable from my router now (eth0)...
Didn't need to configure anything, it worked after installing ubuntu.

However, I also have a wireless option, since my router is wireless, and there's a wireless network card in the computer.
System > Administration > Networking
I activated the wlan0 and entered the WEP key but I can only get internet to work through the cable...

Tell me what to do, check, change...

---

### Post by Doug11 on 2006-12-17
> **geezas said:**
> Help me with wireless setup, thanks
Hey, everybody, it's me again...
I have dapper drake.
I am using the internet through a cable from my router now (eth0)...
Didn't need to configure anything, it worked after installing ubuntu.

However, I also have a wireless option, since my router is wireless, and there's a wireless network card in the computer.
System > Administration > Networking
I activated the wlan0 and entered the WEP key but I can only get internet to work through the cable...

Tell me what to do, check, change...

Try to completely disable your wired connection first. Then enable your wireless. The two won't run enabled at the same time. Your wired connection will take priority if you do. You may also want to have a look at this if that doesn't work.
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by Jose Catre-Vandis on 2006-12-17
Also, try setting up wireless without WEP enabled to start off with, once you have that working then go for WEP. Or better still, tie things down with mac address filtering in your router, if it supports it!

---

