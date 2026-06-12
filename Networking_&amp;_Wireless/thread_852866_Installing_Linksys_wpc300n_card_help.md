---
title: "Installing Linksys wpc300n card help"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by qsilvertwo on 2008-07-08
First off, I am new to linux and basically do not understand much about it so any responses should be simplified as much as possible.  That would be appreciated, thanks!  Okay so I'm trying to install the Linksys wpc300n wireless card on my dell running hardy heron 8.04.  I also bought a pci cardbus adapter slot for it.  THe problem is Ubuntu does not recognize/detect the wireless card at all even after I attempted to use ndiswrapper to load the latest driver.  Ndiswrapper lists the driver as installed but detects no hardware.  I blacklisted the bcm43 or whatever drivers you're supposed to too but no luck.  The card's power light doesn't even come on when I insert it either if that means anything.  Please, please help! Thanks!

---

### Post by grausch on 2008-07-09
I also need to install this card on my Dell.

This is the best link I found so far.

[http://madwifi.org/wiki/Compatibility/Linksys](http://madwifi.org/wiki/Compatibility/Linksys)

It appears that the card can work in a,b and g and that the LEDs do not work under Linux.

---

### Post by grausch on 2008-07-09
You could try this link:

[http://meandubuntu.wordpress.com/2008/05/09/dual-booting-ubuntu-and-winxp-on-my-laptop/#more-75](http://meandubuntu.wordpress.com/2008/05/09/dual-booting-ubuntu-and-winxp-on-my-laptop/#more-75)

The blogger used Wi-Fi Radar and needed to turn off wireless N.

It appears that at the most you will only have g speeds on the card.

---

