---
title: "RT73 stopped working after update to 8.04"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by wzwilliam on 2008-04-27
Hi there. I have just upgraded to Hardy Heron and my laptop's wireless card, Ralink RT73 chipset, stopped working, the led doesn't even lights on. It was working normally with the serialmonkey drivers until during the update process i was asked if i wanted to change my /etc/modprobe.d/blacklist to the installation's default and i chose "no". Since then, my wireless card stopped working. Any ideas?

---

### Post by mrbuntuman on 2008-04-27
i had the same problem couldnt figured out, so i tryed to re-install the driver and i've got ::ur current kernel link does not match ur current running version 2.**** vs 2.*** u may exepreince problem while installing driver ....

i was thinking to myself ..... You Think!!!

---

### Post by chronographer on 2008-04-30
try editing the blacklist file, to comment out rt73usb and add rt73, if that doesn't work, change it back and install serial monkey drivers again.

---

### Post by epee on 2008-04-30
Follow the instructions for installing the RT73 driver which you will find elsewhere on this forum - it works, mostly. I had troubles after the move to Heron too and even after re-installing the RT73 driver.

I did a small tweak to my /etc/network/interfaces file and then it started to work again (I posted the details in another thread - should be easy to find.)

---

