---
title: "Intrepid - can't switch to wired network"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by GrumpyBob on 2008-11-03
Since upgrading to 8.10, I've had no problem connecting to wireless networks, or using my 3G USB modem.  However, I'm at work, and I'd like to used the wired ethernet in preference to the wireless network.
With 8.04, I just used network manager to turn off wireless, and a wired connection was automatically established.  This doesn't happen in 8.10.  Network manager says "Wired Networks device is unmanaged"
I'd be grateful for pointers either to how to do this in network manager, or to finding out where the problem lies.

Robert

---

### Post by superprash2003 on 2008-11-03
please post output of ifconfig when connnected only via wire.d.

---

### Post by ffchaves on 2008-11-03
Apparently, there is a NetworkManager issue regarding static IP on wired connections, if this is your case.

[http://ubuntuforums.org/showthread.php?t=964192](http://ubuntuforums.org/showthread.php?t=964192)

Regards

---

