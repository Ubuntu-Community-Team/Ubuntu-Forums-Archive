---
title: "wireless connect/vpn client"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by hal729 on 2006-09-28
I'm completely new to Linux and Ubuntu, but this seems like a more proper place for my question.

My school uses the Cisco VPNClient, so I've downloaded it, and this guy I know managed to get it installed.  But now I have the following difficulties.
Also, I've used my wireless card before on Ubuntu (with an encripted network that didn't require a vpnclient).

When I set the name to eth1 in the connection properties window, it says the status is disconnected, and the bar along the bottom shows zero signal strength.  Up at the top next to the volume I see the wireless scale, with one bar in yellow.  I have no concept of how to actually connect to the wireless network however.

I know I need the vpn client to actually use it, so here's my other difficulty.  When I do the following command, which should make me connect to the uvm server, it doesn't.

hal@hal-owns-me:~$ sudo vpnclient connect uvm
Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.

I don't really know how to proceed, so any help is gratefully received.

---

### Post by hal729 on 2006-09-28
And I figured it out.  I hadn't set the network name.

---

