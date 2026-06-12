---
title: "Realtek 8180L Wireless Chipset Disabled by Default in 7.04"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by captainskyhawk on 2007-04-24
So, [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255") is the reason why my darn wireless card was disabled by default when I upgraded to 7.04, eh?  

Just posted this in case anyone else was having the same problem their wireless card based on this chipset -- check the blacklist file at /etc/modprobe.d/blacklist -- it's disabled by default.  

You have to use ndiswrapper, which actually isn't all that hard.  [ This]("https://help.ubuntu.com/community/WifiDocs/Device/RTL8180L?highlight=%28WifiDocs%2FDevice%29") tutorial helps a LOT -- just read it and follow the instructions, from top to bottom.

---

