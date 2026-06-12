---
title: "Wireless network card not turned on by default"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by matthedane on 2007-04-26
My wireless network card (Intel 3945) doesn't turn on during start up. There is a led indicator and a manual wireless switch on the computer, but I can't turn on the led by pressing the button like in windows. I can get around the problem by booting in windows (which will make the led indicator turn on) and then reboot into Ubuntu Fiesty, but I would like to find a more permanent solution. I hope someone can help...

Matt

---

### Post by zooooz on 2007-06-09
what kernel version are you on. i have the same problem since version 2.6.21.1, while it still works in 2.6.20-16.
i can't load the module ipw3945 by running "sudo modprobe ipw3945". there is supposed to be a kernel patch to make the ipw3945 compile, but i haven't tried it yet.
still hoping for a how-to on making this work.

---

### Post by matthedane on 2007-09-23
This command turns on the network card (on my laptop):

sudo modprobe fsam7400 radio=1

Matt

---

