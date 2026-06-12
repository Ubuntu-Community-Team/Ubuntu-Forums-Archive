---
title: "wakeonlan - having trouble getting it working..."
date: 2022-08-21
forum: Networking &amp; Wireless
---

### Post by JimLS on 2022-08-21
Wanting to use wake on lan on an old Ubuntu 14.04 box.  Checked the MAC address to make sure I have that right.  Checked the bios and it has wake on lan enabled.  I can see some flashing of the network led on the connector when the box is off so the ethernet port seems to still be active.  
sudo ethtool eth0

Shows:
        Supports Wake-on: g
        Wake-on: g

But running from another machine (20.04):
 sudo /usr/bin/wakeonlan XX:XX:XX:XX:XX:XX   (with the actual mac address!)
Yields:
 Sending magic packet to 255.255.255.255:9 with XX:XX:XX:XX:XX:XX

But the machine does not start.  Not sure what else I should be looking at to find the issue.  Both machines are wired connections to the router and on the same local network.

---

