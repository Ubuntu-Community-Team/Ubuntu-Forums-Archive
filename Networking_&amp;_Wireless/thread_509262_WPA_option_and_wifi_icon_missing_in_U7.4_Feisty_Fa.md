---
title: "WPA option and wifi icon missing in U7.4 Feisty Fawn"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by raevsky.andrei on 2007-07-25
Hi,

I have installed Ubuntu for the first time and, using the book "Ubuntu Unleashed" I have tried to connect my computer to my home wifi (which is secured by WPA).  First, at least according to the book, I should have a wifi icon in the pannel, but I don't.  I have a network monitor icon, but not the progressive ("5 bar") icon shown in the book (and in some online documentation).  Then, when I try to configure the network manually, I do have an option for WEP (ascii or hex) but nothing in the combo box to choose WPA (unlike the book which says it should be there).

I did 'apt-get update && apt-get dist-upgrade' and I installed every single package listed in 'apt-cache search wpa'.  But still no WPA option in that combo box...

While I am asking for help with wifi, can anybody also reccommend a USB wifi card which would work "out of the box"?

Any suggestions would be most welcome!

Cheers,

Andrei

Sorry for the primitive question

---

### Post by ugm6hr on 2007-07-25
The network manager icon (2 computers) changes to the progressive 5 bars if it is connecting via wifi.  First thing to try is reboot with the ethernet cable unplugged (if it isn't already).  If that doesn't work, it is likely that NM hasn't detected your wifi card properly - try this in Terminal:
```
lspci
```
Look for Ethernet / Network Controller - it will tell you what wifi (and lan) chipset you have.

Other useful info from:
```
ifconfig
iwconfig
lshw
```

---

