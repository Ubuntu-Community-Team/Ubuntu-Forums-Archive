---
title: "Problems with WiFi Radar"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-05-13
Check this out. When I use WiFi Radar away from the house to connect to other networks, it works fine. Then I get home. NO-GO! I do have WEP setup in the network panel. How do I remedy this? One of two ways. Either I can restart networking by running sudo /etc/init.d/networking restart everytime that I boot or set a static ip for one boot, reboot, then reset to DHCP.

Has anyone else come across something similar?

---

### Post by cwmaxson on 2007-05-13
Try using this connection manager instead:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
I think it works better.

---

### Post by lsutiger on 2007-05-13
I get an error when trying to install via package installer :
Conflicts with the installed package 'network-manager'

---

### Post by Skidpad on 2007-05-13
What do you use for a wireless card (brand)?

---

