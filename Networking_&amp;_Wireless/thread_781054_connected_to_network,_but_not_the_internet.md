---
title: "connected to network, but not the internet"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by LCollins on 2008-05-03
First - thanks for the help (in advance).

The issue - I have a Netgear WG511v2 (Made in China) wireless network card attached to an newly installed Ubuntu 8.04 system (didn't have this problem in 7.10 - everything worked). I have checked that the password, encryption type, ESSID, gateway IP address are all correct. I have also ensured that the router isn't filtering out my MAC address. Despite all this, and all the indications that I'm connected to the wireless network ('busy' lights on the card come on, 'iwconfig' lists both an ESSID and an access point).

I can ping myself but I cannot however ping the router. Also, the network manager icon in the tray doesn't change form to show signal strength. The instructions on how to install ndiswrapper and the appropriate driver (found at [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/) )
have been followed, and according to that, the driver is installed correctly.

Another point that may be relevant: there are other computers that can connect to the internet via the previously mentioned router. These systems all run Windows XP however. Nortons anti-virus is also used on the network.

I'm pretty new to linux but I can follow instructions, please keep responses in the form of easy to follow steps.

Once again, thankyou,
LCollins

---

### Post by bilal.17 on 2008-05-03
Try a different network manager such as wifi-radar, that solved my problem, as I was connected but I had no internet.

---

### Post by LCollins on 2008-05-04
Thankyou - will keep the thread posted.

---

### Post by LCollins on 2008-05-04
Unfortunately that did not work.

---

