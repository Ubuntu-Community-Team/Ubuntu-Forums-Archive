---
title: "Intel Ipw2200: How To Make It Work"
date: 2005-05-11
forum: Networking &amp; Wireless
---

### Post by ifrflyer on 2005-05-11
After putting Ubuntu 5.04 on my Compaq Presario 4020US Centrino notebook, everything worked pretty much out of the box. Except the wireless. It was buggy and unpredictable. Many - not just me - complain about this. I have written a How To  on my website with a solution. Hope it helps. Tell me either way.

Problem:
Users of Ubuntu 5.04 with computers which use the Intel® Pro/Wireless 2200 802.11B/G WLAN experience troubles including:

    * Intermittent connectivity
    * Inability to switch between networks or regain a lost network connection without rebooting
    * Inability to configure wireless connection using Network Connection GUI 

Cause:
Ubuntu 5.04 Hoary Hedgehog ships with version 0.19 of the driver for this card. The current version is 1.0.3. The stable version is 1.0.0, and this is the version it is recommended to use with Ubuntu. Of course, you can try any version you like!

Solution:
Remove completely version 0.19 and upgrade to version 1.0.*


HOW TO:
[http://nickselby.com/articles/technology/index.htm?a=1807](http://nickselby.com/articles/technology/index.htm?a=1807)

---

### Post by luca_linux on 2005-05-12
In fact I wrote this howto 1 month ago: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

