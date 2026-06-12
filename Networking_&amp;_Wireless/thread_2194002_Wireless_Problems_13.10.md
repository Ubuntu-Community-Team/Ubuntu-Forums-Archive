---
title: "Wireless Problems 13.10"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by ejroebuck on 2013-12-15
In Ubuntu 13.10 I can no longer connect to the internet server for neither my home internet nor the mobile hotspot from my Verizon phone. I however have no trouble connecting to wifi at my university, and my Windows 7 partition also has no trouble connecting. It acknowledges the signal and "connects" in both cases, but my browser will not connect to the server, nor does my Dropbox update, etc. Neither of my roommates (both Mac) have had trouble connecting to the wireless. The change was sudden, and didn't necessarily correspond to a recent update. My device is a Lenovo T420s, and Realtek 8188CE.
In attempt to troubleshoot I've tried...

Using the ethernet cable, no avail.
Hard resetting the router, turning off password restriction, etc., no avail.
Using a MediaLink USB wireless adapter, no avail.
Updating my Kernel from 13.11->13.12 (as suggested in a few forums), no avail.
Removing the suspect connections from NetworkManager, rebooting, etc., no avail.

I've since come across [http://ubuntuforums.org/showthread.php?t=2192496&page=2&highlight=wifi+13.10](http://ubuntuforums.org/showthread.php?t=2192496&page=2&highlight=wifi+13.10) and [http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571](http://ubuntuforums.org/showthread.php?t=2192555&p=12868571#post12868571) that seem to solve similar problems, however the solutions seem too specific to the hardware. My skill set is too lacking to generalize any of that, or to even tell if indeed we're having the same problem.

---

### Post by wildmanne39 on 2013-12-15
Please use normal fonts when posting.
Thanks

---

### Post by ejroebuck on 2013-12-26
So going with the links above it's not apparent that something has been blacklisted, there doesn't appear to be anything in the /etc/modprobe.d/ folder to suggest that.

I've also tried booting older Ubuntu settings upon start-up, 13.11, 13.10, 13.8, etc., and nothing.

The most curious thing to me is that one wireless network appears to connect without any trouble at all. I've tried removing this network from the saved list to see if it had inadvertently caused the problem, but this doesn't seem to solve the problem either. Any ideas anyone?

---

### Post by ejroebuck on 2013-12-28
Solution!

To troubleshoot I removed the only working wireless network from the stored wireless networks. I noticed however that in /etc/resolv.conf there still exisited a line that read...

search tufts.edu

despite me having removed this network. I assumed there might be trouble so I reconfigured resolveconf by typing the following...

sudo dpkg-reconfigure resolvconf

then rebooted and connected with no trouble.

---

