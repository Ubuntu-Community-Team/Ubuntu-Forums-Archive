---
title: "Unable to boot ubuntu livecd or installation with WLAN"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by M&amp;SO on 2007-11-18
Hi,

I'm newbie with Linux/Ubuntu.

I have or had  little problem to boot Ubuntu 7.10 livecd or install it because it didn't boot if my wlan card was installed. The boot options -screen started and i was able to choose boot options. I choosed Start / Install -option. Then Ubuntu logo came to screen but it didn't go forward. It was freezing in 80%(about)

I removed the wlan card. Then Ubuntu livecd started and GUI install was possible. Now i have installed Ubuntu, but without wlan card. If i put my wlan card to my pc, Ubuntu won't boot. It freezes to boot screen.

My hardware:
- Asus P4C800 Deluxe Motherboard
- Pentium 4 2,8
- 1,5GB RAM
- **Zyxel G-302v3 Wlan card**
- 250GB SATA drive
- LG DVD drive

---

### Post by mouseboyx on 2007-11-18
Does the Wlan card work with any other computers/operating systems?

---

### Post by M&amp;SO on 2007-11-18
> **mouseboyx said:**
> Does the Wlan card work with any other computers/operating systems?

Yes, it does. I'm using it with Windows.

---

### Post by Blutack on 2007-11-18
Right, good news and bad...
the good is your card should work in ubuntu
the bad is that ubuntu is currently loading the wrong driver for it, hence the freezing.  Have a look 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309)
there for your answer, and hopefully wireless bliss.

---

### Post by mouseboyx on 2007-11-18
Im stumped but these threads describe a problem/instalation with the card too.

[http://ubuntuforums.org/archive/index.php/t-478605.html](http://ubuntuforums.org/archive/index.php/t-478605.html)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309)

It could possibly be a bad CD

Did you md5sum it?

---

### Post by Blutack on 2007-11-18
Mouseboyx, ubuntu is freezing because when the wireless card is plugged in a driver is loaded.  The driver was built for an older version of this wireless card and doesn't play nice, hence the kernel panics and ubuntu locks up.  The solution is to boot without the card plugged in, blacklist this driver in the /etc/modprobe.d/blacklist file to prevent it from loading and then use ndiswrapper to get it working properly.  He/she probably doesn't need to md5 the cd, although I would recommend checking cd's before you install.

---

### Post by M&amp;SO on 2007-11-18
> **mouseboyx said:**
> Im stumped but these threads describe a problem/instalation with the card too.

[http://ubuntuforums.org/archive/index.php/t-478605.html](http://ubuntuforums.org/archive/index.php/t-478605.html)
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=580309)

It could possibly be a bad CD

Did you md5sum it?

Yes i did and cd is ok. I will look those other threads...

---

### Post by M&amp;SO on 2007-11-18
Hi, 

Problem solved! 

- Thanks for mouseboyx and Blutack.

---

