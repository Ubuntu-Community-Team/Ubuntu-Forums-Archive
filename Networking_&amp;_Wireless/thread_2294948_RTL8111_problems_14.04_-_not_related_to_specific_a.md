---
title: "RTL8111 problems 14.04 - not related to specific adapter?"
date: 2015-09-14
forum: Networking &amp; Wireless
---

### Post by jim119 on 2015-09-14
I just changed motherboards on an old 14.04 server install. After boot up, the ethernet wasn't working. After finally getting the drivers 8.0.40 or whatever is the latest, installed, I checked lspci -v to see that kernel driver in use was r8168.

The adapter is still unlisted in ifconfig unless I do ifconfig -a, however. I've rebooted multiple times and at boot ubuntu is always waiting for the network adapter on boot and never seems to enable it. When I attempt to bring it up manually, I get "SIOCSIFFLAGS: Operation not permitted." Trying to restart the networking service results in "job failed while stopping." ifup eth1 results in "ignoring unknown interface eth1=eth1

Any help or suggestions would be much appreciated. I don't particularly want to have to do a complete reinstall.

For reference it's a sabertooth 990FX. In an act of despiration, I tried adding in several old PCI cards I had lying around to at least get it online. But I experienced the same issue with one card and the other two didn't show up in lspci -v

Edit: solved but still questioning. I put in the command sudo dhclient eth1 and suddenly everything was working. Of course, upon reboot, I have to do this again, which is rather inconvenient as I intend to put this server back soon as it is supposed to be headless. I could add the command to startup but the underlying issue remains and there's that annoying 1-2 minutes you have to wait on boot while ubuntu figures out it can't make the ethernet work.

**Edit edit: for anyone who runs into this in the future, you're issue is likely the /etc/network/interfaces file. For me, after the board change, my new interface was eth1 for some reason even though there is no eth0. But the file still only had entries for the loopback and eth0. I changed eth0 to eth1 for all instances in the entry and everything is now good.**

---

