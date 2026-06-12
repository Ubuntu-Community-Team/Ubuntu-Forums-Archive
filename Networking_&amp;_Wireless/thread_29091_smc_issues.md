---
title: "smc issues"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by somuchfortheafter on 2005-04-22
well i have googled and I am almost ready to switch back to warty where i had kismet working, anyway I have an SMC2532W-B wireless card that normally used the eth2 interface and the orinoco drivers. Anyway I could not get the monitor mode patch to work on the drivers so I decided to try the wlan-ng drivers, After installing these drivers whenever I insert the card into the pcmcia slot i hear the normal beep then a lower toned beep that reeeks of having some cryptic error message encoded. Anyway  I unintsalled the linux-wlan-ng package as I figured it broke somthing. So how can I:
A. Go back to using the orinoco drivers and having peace and harmony
B. Start using the prism2_cs driver that linux wlan-ng supports

Also this card does not show up in the network card list under the network admin gnome thing, ifconfig in a terminal, or even in device manager. So umm I basically need help, lastly lspci does not list the card as existing either.

---

### Post by jshein on 2005-04-24
see my other thread here and see if this information helps you out.

[http://ubuntuforums.org/showthread.php?t=23596&highlight=monitor+kismet](http://ubuntuforums.org/showthread.php?t=23596&highlight=monitor+kismet)

---

### Post by zencoder on 2005-08-17
Answers in your other thread about this card, [here](http://www.ubuntuforums.org/showpost.php?p=306491&postcount=4).

---

