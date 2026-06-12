---
title: "Wireless not turned on for other users"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by wiredrick on 2008-05-25
Hi am using ubuntu 8.04 and tp-link tl-wn322g. I have got my wireless working fine on my main user. Turn on, insert usb and browse.
I also have a user for my partner, but does not automatically work for her. 
to get it working for her I have to su to my user, sudo ifdown eth1, sudo ifup eth1.
once i have done this he wireless works fine. does anyone know how I can get it to load automatically.

---

### Post by mringer on 2008-05-27
I have the same problem. Dell Inspiron 1525, Broadcom 4310 card, X-Ub 8.04,
got the card to work (for the main user) by ndiswrapper, ref:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

other methods having failed.

If I can work out how, I hope to read the relevant syslogs if they exist.

---

### Post by mringer on 2008-05-28
I looked at syslogs and found

NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

This occurs when a user who cannot access the net logs in.  My guess 
is that  NM  is failing to read a config file, but the documents are 
so poor that I dont know what file (or it might be something else
altogether).

---

