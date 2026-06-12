---
title: "feisty rt2500 - connection but no internet"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by vaskeli on 2007-04-21
Another RT2500 problem. upgrading to feisty broke network manager, but I can connect to my network by:

ifconfig ra0 down
iwconfig ra0 essid myessidname
ifconfig ra0 up

after this, "iwconfig" shows me connected to the proper essid, with a decent bit rate and link quality. i can access the local network, but I can't connect to the internet. "ping google.com", for example, returns "unknown host".

checkng /var/log/daemon.log, I can see some Permission denied errors:

Apr 21 02:17:36 avahi-autoipd(ra0)[6636]: S?IOCSIFFLAGS failed: Permission denied

Apr 21 02:24:39 avahi-autoipd(ra0)[6654]: Successfully called chroot().
Apr 21 02:24:39 avahi-autoipd(ra0)[6654]: Successfully dropped root privileges.
Apr 21 02:24:39 avahi-autoipd(ra0)[6654]: fopen() failed: Permission denied.

but I don't know what any of it means. Help!

---

