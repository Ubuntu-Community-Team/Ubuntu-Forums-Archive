---
title: "Wireless won't stay disabled"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Tanker Bob on 2007-02-08
I have both a wired network connection to a Lynksys WRT54G router and a Linksys WMP54G wireless card in my PC.  Every time I reboot my Kubuntu 6.10, both network connections activate even though the wireless connection is not set to activate at startup.  This conflict causes no IP address to be assigned to the computer.  I fix this by deactivating both network connections, then reactivating the wired connection.

However, the wireless connection keeps activating on its own, even after repeatedly deactivating it in System Settings.  The deactivation finally takes after 8-10 attempts.  What's up with this?  Why won't it obey the System Settings?  How can I solve this without removing the network card?  Thanks!

---

### Post by tturrisi on 2007-02-08
/etc/network/interfaces
put # preceding amy lines for the wifi device.
example:
#iface ath0 inet dhcp
#wireless-essid Linksys
#wireless-key xxxxxxxxxx

---

### Post by Tanker Bob on 2007-02-08
Thanks.  I just tried that, but it didn't work.  In fact I commented out all other connections except the wired one, then rebooted.  Same problem.  Any other ideas?

---

### Post by Tanker Bob on 2007-02-08
Well, I finally solved it.  I took the engineering approach and pulled the wireless card out of my computer.  I'm not using it at the moment anyway.

I do appreciate your taking the time to try and help.

---

