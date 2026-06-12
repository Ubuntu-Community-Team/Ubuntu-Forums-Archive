---
title: "Wireless broke during attempt at internet forwarding"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Ozenbac on 2008-02-17
In an attempt for forward my wireless internet though my ubuntu box I broke something.  I was following this post [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) but I did not RTFM and put wlan0 in for all of the commands.  I find and connect to my wireless but no hostnames resolve.

---

### Post by Ozenbac on 2008-02-18
Fixed it, I reset /etc/network/interfaces, restarted ipmasq and flushed the iptable rules and it worked.

---

