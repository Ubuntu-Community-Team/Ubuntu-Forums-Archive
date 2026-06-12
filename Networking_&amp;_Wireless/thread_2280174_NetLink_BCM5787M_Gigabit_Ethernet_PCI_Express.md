---
title: "NetLink BCM5787M Gigabit Ethernet PCI Express"
date: 2015-05-28
forum: Networking &amp; Wireless
---

### Post by yannella on 2015-05-28
Update from a closed thread....
[http://ubuntuforums.org/showthread.php?t=975406](http://ubuntuforums.org/showthread.php?t=975406)

Thanks for all the posts in there.

I installed Ubuntu 14.04 LTS on a Lenovo R61 Thinkpad.
Legacy machine.  Everything installed great except for the on board Broadcom nic.

Ubuntu found the Intel wireless NIC just fine but the on board BCM5787M Lan 
would not work at all.

When I looked in /etc/network/interfaces there was only one entry:

auto lo 
iface lo inet loopback

The install did not see eth0 for whatever reason.
I used the following:

    sudo pico /etc/network/interfaces

added the following on the end:

auto eth0
iface eth0 inet dhcp


saved and rebooted and I had the on board nic running.

Hopefully this will save someone else that is running into the same issue.



Chris

---

