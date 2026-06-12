---
title: "Noob needs help with Acer WiFi"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by SyntaxMage on 2008-10-28
Alright, I'm still new to ubuntu. Running 8.4 and I've been searching all over the boards for a solution to my problem. I'm not sure what type of card I have, don't know much about it or how to find that stuff out. All I know is I DO have a wifi card in my Acer Laptop and it is not working at all. The switch to turn the card on and off is not lighting up or working as far as I can tell. All I know for sure about the computer is that it's an Acer Aspire 4720z and this is the last bit of technical help that it really needs. Can anyone help? much appreciated.

---

### Post by DFlame on 2008-10-29
I've done some digging for you. From [http://www.scottro.net/rhwireless.html#5007](http://www.scottro.net/rhwireless.html#5007) ...

> Ubuntu's Hardy also seems to now support the card without using the MadWifi drivers described below. As of 26 October, 2008 doing *(NOTE: use sudo prior to commands here)*

aptitude install linux-backports-modules-hardy

(or possibly hardy-generic rather than hardy), worked for me. Although a reboot might be necessary, the card should then be seen as wlan0. (If you have the ath_pci module installed, remove and blacklist it. Add the line "blacklist ath_pci" without quotes to the end of /etc/modprobe.d/blacklist). In theory, one should be able to do

ifconfig ath0 down
modprobe -r ath_pci
modprobe ath5k
ifconfig wlan0 up

and have the card working, but in practice, it is usually simplest to add the blacklist line for the ath_pci and reboot. 

You might wish to wait a day or so for Intrepid (the latest ubuntu distro) to be released. Looking at the page up there, it looks like it could have out of the box support for the card. There's also some more useful info here: [http://www.scottro.net/acer4720z.html](http://www.scottro.net/acer4720z.html)

DFlame

---

### Post by xnerdx on 2008-10-29
[http://ubuntuforums.org/showthread.php?t=739998](http://ubuntuforums.org/showthread.php?t=739998)

---

