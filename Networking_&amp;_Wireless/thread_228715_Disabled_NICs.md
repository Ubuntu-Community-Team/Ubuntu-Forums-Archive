---
title: "Disabled NICs"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by cltrenholm on 2006-08-03
Hi,

I have a server with two NICs and the OS appears to be seeing them and they are apparently functioning however when I attempt to enable them they come up for a split-second and then go back into a disabled state. This is all being done from the GUI.

From a command line I have attempted to use the mii-tool to force the NICs to 100-FD but only eth1 takes the setting, eth0 will revert back to 100-HD.

From the GUI I have attempted to set the IP address, etc. manually and this seems to take but the when I attempt to enable the NICs they still won't come up. For eth0 I left it at dhcp and it won't connect to the network and eth1, I set manually and enable it but still no luck; it goes back to disabled.

From the command line I have manually edited the following, all with the correct settings and have even attempted setting the ports on my switch to 100HD with no luck.:
etc/network/interfaces
etc/resolv.conf
etc/networks

It is running on a Dell PE1800 with a Broadcom NetXtreme 10/100/1000 NIC PCI Express.

The system was purchased and turned over to a developement group that was working on an application for us. They have since turned it back over to us for integration into our LAN.

All I am trying to do is configure the IP stack, should it be this difficult? What am I missing? Someone please tell me I'm a simpleton and that I have missed something obvious.  ](*,)

BTW, the dev group is not returning my calls or emails on this matter; or any other for that fact.

Please help or give my guidance.

cT

P.S.- Send me some patience as well, lacking that rum will suffice.

---

