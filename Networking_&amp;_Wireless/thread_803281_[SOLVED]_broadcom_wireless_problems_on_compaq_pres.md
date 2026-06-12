---
title: "[SOLVED] broadcom wireless problems on compaq presario f700"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by kofoworola on 2008-05-22
hi guys! just installed hardy (on my compaq presario f700) and its really cool. everything works xcept the wireless driver. i really need help with this cos its the only thing that takes me back to windows. if a thread like this already exists with a solution, please post the links here if not, :(help!

---

### Post by lswest on 2008-05-22
what broadcom card exactly is it?  what have you tried to use to get it working?

Also - this is probably not the best place to post requests for help, there are other forum areas for that (where you're more likely to find an answer).

---

### Post by kofoworola on 2008-05-22
Broadcom 802.11b/g WLAN. i'll try somewhere else. thanks anyway and if u got something on it please let me know. thanks

---

### Post by lswest on 2008-05-22
> **kofoworola said:**
> Broadcom 802.11b/g WLAN.

that's not the model of the card, and doesn't help you figure out which drivers you need.  Post back the output of ```
lspci
``` from the terminal, and i would suggest using ndiswrapper to install the windows driver for it, and there are a number of how-tos on these forums on installing braodcom drivers via ndiswrapper on hardy.

Example:
```
lswest@lswest-laptop:~$ lspci|grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
``` is my card, and i run it using the bcmwl5 drivers via ndiswrapper ```
lswest@lswest-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
```

Also, you may find my post on [this thread]("http://ubuntuforums.org/showthread.php?t=780212") useful (it's post #5)

---

### Post by kofoworola on 2008-05-22
Broadcom Corporation BCM94311MCG wlan mini-PCI

---

### Post by kofoworola on 2008-05-22
lswest, u r the man! works like a charm! wow! thanks a bunch man, appreciate:)

---

### Post by bigbrovar on 2008-05-22
@ lswest mehn u are a soooooooooo cool .. am with kofoworola here in Nigeria .. ur guide worked like a charm ..  its awesome .. he is using his wireless right now.. thanks .. u are a true ubuntan .. :)

---

### Post by lswest on 2008-05-22
Haha, great, i'm glad i was able to help, and you give me waaaaaaaayyyyyyyyyyy too much praise :P

---

### Post by K.Mandla on 2008-05-22
Moved to Networking and Wireless.

---

### Post by Scortech on 2008-06-16
I am a noobie at ubuntu so I don't even know what this ndiswrapper is or how it works..

I can't get my wireless to work on my compaq presario F700

---

### Post by Ayuthia on 2008-06-16
> **Scortech said:**
> I am a noobie at ubuntu so I don't even know what this ndiswrapper is or how it works..

I can't get my wireless to work on my compaq presario F700

You could try this link:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
It is a good step by step guide for NDISwrapper.

---

### Post by Scortech on 2008-06-16
> **Ayuthia said:**
> You could try this link:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
It is a good step by step guide for NDISwrapper.

Thank you so much..
Solution found on your link..

Thanks again

---

### Post by Blarney08 on 2008-09-18
I am brand new to ubuntu having problems getting wireless working
have compaq f730us with broadcom 802.11b/g wlan please help.

---

### Post by Alex7000 on 2010-08-17
I have a presario f700 as well. lspci does not report a wireless device. I have the model number read off the card is BCM94311MCG HP. So, it seems the issue is that my[FONT=monospace] Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5 [/FONT]doesn't see the wireless hardware?

---

