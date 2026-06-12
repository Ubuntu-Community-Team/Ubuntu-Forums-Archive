---
title: "this .deb works for BRCM43xx in feisty"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2007-04-11
[http://ubuntu.cafuego.net/dists/edgy-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/edgy-cafuego/bcm43xx/)

Simply install this deb
reboot 
and it enables the networking card


Since it works so well, why cant this already be included with ubuntu when it is installed?

---

### Post by NullHead on 2007-04-11
Does this work with or for the bcm43xx driver... the one thats already loaded loaded into 6.06, 6.10, 7.04? 
And does this work with a bcm4318 chipset?

---

### Post by jbonll05 on 2007-04-11
NOTE: downloads are for i386 only at this time. My laptop is a 64bit and my 7.04 project machine is a 64bit. I will give this a workout  this weekend on an i386 machine using usb or pci wifi connectors. My laptop is has BMC4318 in it, running w/"wrapper".                                               This looks great, I read the "Front Page" and the page that came up from sdowneys post. There is authendication for these packares; that is, Dapper, Edgy, and Fiesty on the website. Almost certainly our repositories have taken care of this, if not the code and directions  is on the website.
    JB; Ubuntu since 4oct05.

---

### Post by ProMaster on 2007-04-13
Brilliant!!! Works like a charm on my ASUS WL-138g V2!!!:D

---

### Post by nanog on 2007-04-13
These tutorials both work in Feisty:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)
[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961)

Note that some cards *STILL* do not work well with the cafuego driver.

For more info on which bcm43xx cards are supported:

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

If you troll the berlios dev mailing list you can find out whether there are patches for your particular broadcom card. By upgrading my kernel to 2.6.21rc6 my dell 1390 4311 is now natively supported at ~54mb/s with a huge boost in transmission power. I may apply some additional patches as the tx power is still somewhat lower than ex pee.

---

### Post by wipeout140 on 2007-04-13
That .deb works fine but i some times only get 11mbs on wireless not 54mb

---

