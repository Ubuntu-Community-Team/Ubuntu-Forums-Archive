---
title: "Compex WLU11A causes kernel panic."
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by sepultura on 2007-07-14
The OS is Ubuntu 7.04 desktop, running on a Dell P3 system. I use a compex WLU11A wireless-B USB adapter with this. I believe Ubuntu automatically loads the berlios/ATMEL drivers for this device, since it works out of the box. 

The problem is that this often causes kernel panics and the system freezes with the caps-lock + num-lock LED's blinking on my keyboard. After this happens, I don't see any relevant error messages in syslog or any of the other log files in /var/log/* which would help troubleshoot.

I know this device is the culprit... when I use good old ethernet, everything is rock stable. 

The kernel panics are not predictable. I've got some when the system is booting, and many when I logout of my Gnome session. It's probably nothing related to Gnome either, I've got this freeze when exiting KDE too.

Any suggestions? Do I need to throw out the compex and get something else? Get a PCI wireless card? Anything else I can do?

Thanks!

Edit: All packages and the kernel are up to date. apt-get update / dist-upgrade is done regularly.

---

