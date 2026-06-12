---
title: "[SOLVED] Yet another slow wireless connection after Gutsy upgrade"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by namko on 2007-12-06
Hello,
Just upgraded to Gutsy. Wired Internet connection is fine, but using wireless (2200BG) connection, pages take forever to load (Konqueror, Firofox, etc.). I think the problem is with KNetworkManager. Have disabled IPV6 with no help. The following two solutions did not work for me:

[http://ubuntuforums.org/showthread.php?t=604323&highlight=slow+wireless+gutsy]("http://ubuntuforums.org/showthread.php?t=604323&highlight=slow+wireless+gutsy")

[http://ubuntuforums.org/showthread.php?t=616744]("http://ubuntuforums.org/showthread.php?t=616744")

Wireless worked OK in Feisty.  Any help greatly appreciated.

---

### Post by namko on 2007-12-08
The solution to the above problem was to manually disable eth0 (wired interface) in KNetworkManager when using eth1 (wireless interface). Everything is now back to normal. I must do this every time I reconnect as eth0 gets re-enabled automatically. I wonder why this is required in Gutsy and not in Feisty?

---

### Post by sanantone on 2008-02-09
Along similar lines, if you disable roaming mode on eth0 (I set mine to dhcp) wireless speed is restored...

---

