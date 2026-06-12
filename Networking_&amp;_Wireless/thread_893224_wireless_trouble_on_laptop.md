---
title: "wireless trouble on laptop"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by dm29 on 2008-08-18
Hi, I'm a newbie and pretty new to Linux. I bought a HP Pavilion tx1000 (service: tx1115nr) and it came with Vista. I hated it, and decided to install Ubuntu (Hardy Heron) on it. 

The installation was fine, even audio works, but I'm having trouble picking up my wireless network. My network card (built-in) picked up my wireless network without a problem in Vista, but Ubuntu doesn't even seem to pick up the router at all. I tried manually putting in the 128bit WEP key and SSID but it still doesn't pick up the signal.

Please... someone help!

---

### Post by dm29 on 2008-08-18
Did I not provide enough details? bumping

---

### Post by Ayuthia on 2008-08-18
> **dm29 said:**
> Hi, I'm a newbie and pretty new to Linux. I bought a HP Pavilion tx1000 (service: tx1115nr) and it came with Vista. I hated it, and decided to install Ubuntu (Hardy Heron) on it. 

The installation was fine, even audio works, but I'm having trouble picking up my wireless network. My network card (built-in) picked up my wireless network without a problem in Vista, but Ubuntu doesn't even seem to pick up the router at all. I tried manually putting in the 128bit WEP key and SSID but it still doesn't pick up the signal.

Please... someone help!
Can you go into the terminal and post the results of:
```
lspci -nn
```This will help us see what your wireless card is so that we can determine what you might need to do.

---

### Post by dm29 on 2008-08-18
Broadcom Corpration BCM94311MCG wlan mini-PC I [14e4:4311] (rev 01)


I think that's it. That's what it listed.

---

### Post by Ayuthia on 2008-08-18
> **dm29 said:**
> Broadcom Corpration BCM94311MCG wlan mini-PC I [14e4:4311] (rev 01)


I think that's it. That's what it listed.

You can start with this:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Your card seems to be the same as mine.

---

