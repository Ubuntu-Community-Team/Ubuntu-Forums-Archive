---
title: "Strange interface issue"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by akane on 2008-07-08
I have a HP DL380 that has a fresh install of Ubuntu 6.06.2 LTS.  I've run into a strange issue with the network interfaces.  

During the actual installation, a dhcp address was acknowledge and picked up by the box.  After installation, the machine was unable to grab a DHCP address after many attempts, on both eth0 and eth1.  

Further, I have tried setting the IP to static, and what is really strange is that when I initially set the static IP, I can't ping anything, it's like there is no connection.  So I bring the interface down - ```
/sbin/ifconfig eth0 down
``` and then ```
/sbin/ifconfig eth0 up
``` and all of the sudden I can ping.  

This same thing happens if I set up the static IP in /etc/network/interfaces and reboot.  Initially once the box boots up, it has the static IP and all of the correct information, but no connection.  I bring the interface down, then back up, and then the connection works.

Any help on how to resolve this is greatly appreciated.

Thanks!

---

