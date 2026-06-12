---
title: "RealTek wifi card  problem"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by jaybee99 on 2008-02-24
I used ndiswrapper to configure a PCI bus wifi card that uses RealTek drivers on a laptop running gutsy -- it works a treat if I insert the card after booting, but if I boot the laptop with the card already in, the boot process seems to get almost all the way then hangs with caps lock blinking.

I think I need to blacklist some kernel module that is being loaded in error when the card is detected. How do I find out which?

Thanks!

---

### Post by alan34 on 2008-02-24
In a terminal 

lsmod

or

lspci

or

ndiswrapper -l 

will give something like this

net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)

so I know to blacklist the r8180 driver

gksudo gedit /etc/modprobe.d/blacklist

add at the bottom

blacklist rXXXX

Good Luck

---

### Post by jaybee99 on 2008-02-24
Thanks a million, that fixes the problem. Your thanks rate is 5 for 5 :-)

---

