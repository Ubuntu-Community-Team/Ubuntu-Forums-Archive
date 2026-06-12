---
title: "wifi led c700"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by amattheson on 2008-07-20
i just got a c751nr presario and cant seem to get the wifi led to turn blue(enabled), all it does is stay orange(disabled). the button still changes if wifi enabled or disabled but the led just stays orange. If anyone can help that would be great?????

---

### Post by agentphish on 2008-07-20
I have the c762nr, very similar model. I've been looking around and reading about Ubuntu on these because I've been considering trying it out.

No one has gotten anywhere with it to my knowledge.

---

### Post by jeffegg2 on 2008-07-21
I have the compaq persario c700, got the wifi working, but button still stays orange.... who cares, my wifi works!!

---

### Post by d_exter on 2008-07-24
I had to install Ubuntu Hardy on C751NR (Atheros wireless chipset) recently.
I have found a windows xp driver that works with ndiswrapper [>here<]("http://www.mmoogle.org/compaqc751nrwindowsxpdrivershowto"). The driver is modified in order to make the LED work.

---

### Post by amattheson on 2008-08-07
> **d_exter said:**
> I had to install Ubuntu Hardy on C751NR (Atheros wireless chipset) recently.
I have found a windows xp driver that works with ndiswrapper [>here<]("http://www.mmoogle.org/compaqc751nrwindowsxpdrivershowto"). The driver is modified in order to make the LED work.

how did you get it to work in Ndiswrapper??? every time i try to install it in ndiswrapper my c751nr freezes.

---

### Post by d_exter on 2008-08-07
- disable the restricted drivers
- blacklist the ath_pci module as described in [this]("http://ubuntuforums.org/showthread.php?t=512828") thread

My experience was, that if the wireless card is detected and already dealt with by those drivers, the ndiswrapper won't be able to activate the card anymore.

Good luck!

---

### Post by amattheson on 2008-08-07
i still cant get it to work i installed the drivers but now i cant connect to my wpa network

---

