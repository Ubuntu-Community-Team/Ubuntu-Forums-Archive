---
title: "Abandoned Madwifi for Ndiswrapper and it works!  But..."
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by kpjoyce on 2007-05-03
Something, somewhere still wants to call my wireless network interface 'ath0'.  Ndiswrapper uses wlan0, and the rest of my system is set up accoringly.  When I boot, I get an error message that says something called rename_netif (or similar) is unable to change the device name from wlan0 to ath0 because the device is busy.

When I resume from hibernation or suspend, the name is changed to 'ath0', causing headaches.

I've blacklisted all the madwifi modules, and they are not running.  All references to 'ath0' have been removed from /etc/network/interfaces.

Where else can I look?

Thanks for the help.

---

### Post by kpjoyce on 2007-05-03
Found it.

I also needed to update /etc/iftab.

---

