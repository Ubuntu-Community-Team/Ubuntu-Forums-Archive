---
title: "Wake-on-LAN not working under Dapper with Asus A8V Deluxe motherboard"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by jmcarter on 2007-08-29
Hi,

I'm having a problem with getting wake-on-lan to function on my Ubuntu (Dapper Drake) PC - it simply will not wake up. 

I have confirmed the integrated NIC has wol ability, and have made sure it is enabled by adding 'up ethtool -s eth0 wol g' to /etc/network/interfaces'.

There seems to be a lack of an option in the BIOS to enable it, so I presume it only needs to be enabled in the driver.

Any ideas?  Thanks in advance.

Jacob

---

