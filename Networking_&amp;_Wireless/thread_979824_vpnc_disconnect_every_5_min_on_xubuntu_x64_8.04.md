---
title: "vpnc disconnect every 5 min on xubuntu x64 8.04"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by lnthai2002 on 2008-11-12
Hi guys,

I am running xubuntu 8.04 64bit. I need to connect to my company vpn (cisco vpn server) so i use vpnc with networkmanager. I get disconnected from VPN network every 5 min, i was wondering if this problem is known before and how can i fix this. I was thinking about installing vpnclient from cisco but it seems that alot of people getting error during installation process.

Hope to get some help

Thai

---

### Post by Cone Basher on 2009-04-01
I don't know about using it via the network manager.  I use it from the command line. I had to hunt around a bit to find a switch to turn the idle time off.  It's --dpd-idle=0

For example:

sudo vpnc-connect --dpd-idle=0
sudo vpnc-disconnect

Cheers!

---

