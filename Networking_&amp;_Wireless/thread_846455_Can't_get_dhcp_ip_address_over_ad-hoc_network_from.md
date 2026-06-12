---
title: "Can't get dhcp ip address over ad-hoc network from XP box sharing internet connection"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by mn_monkey on 2008-07-01
I'm frustrated.  I have a Dell Latitude D620.  My wife has her XP box with our mobile broadband from sprint.  She is able to share her connection through an ad-hoc network with another xp (and my palm TX).  But when I try to connect on my hardy box I never get a DHCP IP address.  My hardy box works fine on all other networks.

I've tried the network-manager.  I've tried wicd.  I've tried command line.  Is there a bug in hardy that won't let me connect to an ad-hoc network with dhcp?

Seems like this should work :

sudo ifconfig eth1 down
sudo iwconfig eth1 essid BB2 mode ad-hoc
sudo ifconfig eth1 up
sudo dhclient eth1

But no luck.  Help.

If this helps lshw -C network
 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:a5:dd:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by pytheas22 on 2008-07-01
I'm not positive, but I think that it may be because the driver that you're using (iwl3945) doesn't support ad-hoc mode, as this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/201597") seems to confirm.  Luckily, there's an older version of the Intel wireless drivers (ipw3945) that should support ad-hoc; as someone in the bug report says:

> 
As excepted, ad-hoc works perfectly with ipw3945.

You can replace the new driver with the older version by following instructions [here]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html").  I'd give that a try and see if it solves the problem.

A lot of wireless drivers are being rewritten now and pushed out even though in many cases they still lack the functionality of the legacy drivers that they're supposed to replace.  I don't own any Intel cards, but I had this issue with an Ralink device: ad-hoc was impossible using the "next-generation" driver that ships with Ubuntu, but by blacklisting that and using the older driver, things worked great.  Also note that my Ralink card would say it was in ad-hoc mode but really wasn't, so don't believe what iwconfig tells you.

---

