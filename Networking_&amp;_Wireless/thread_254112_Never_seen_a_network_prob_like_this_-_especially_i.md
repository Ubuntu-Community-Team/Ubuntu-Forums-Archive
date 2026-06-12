---
title: "Never seen a network prob like this - especially in Linux"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by 0be1 on 2006-09-09
This one has me puzzled beyond belief. I start my ubuntu 6.06 server and receive a DHCP server assigned ip address and I only have conectivity for approx. 3-5 to the internet. I have seen another post to turn off IPV6 (why its on by default is beyond me). Rebooted, still have the same problem. Disconnect cable from the router and go directly to the cable modem, now I get an IPV6 address assigned to the computer but cannot get connectiviy at all.

All of my winblows boxes are working fine and no interuption in service. I am trying to run apt-get update right now and the only way I can get it to do it is to unplug the net cable and plug back in until I get connectivity again for 3-5 minutes and repeat the procedure.

Anyone have any ideas on this one? btw, using comcast for internet.

tia...

Shawn

---

### Post by 0be1 on 2006-09-09
I see there are a lot of posts suddenly coming up about network issues. Is there possibly another bad patch release from he ubuntu community like a few weeks ago that broke the gui?

My output from looking at another post of lspci is:

02:0a.0 ethernet controller: Davicom Semiconductor 21x4x DEC-Tulip compatible 10/100 ethernet

02:0b:0 communication controller: conexant HSF 56 Data/Fax modem

dmesg | grep eth0 outputs:

[42949388.890000] etho: davicom dm9102/dm9102a rev 49 at 0001d800, 00:08:a1:03:58:99, irq 185

[42949392.680000] eth0: setting full duplex based on MII#1 link partner capability of 41e1

I also loaded two other comps. two weeks ago and have not done any updates for a week, and am not having any problems. I am just including this to say that other comps in other locations are fine, but ae not patched either in case there is an association.

thanks...

Shawn

---

### Post by deleted1028 on 2006-09-10
today I connect with any thing related to "ubuntu" the cd's the operating system or anything but I can with osX and Gentoo.
scott

---

### Post by deleted1028 on 2006-09-10
The only way I can connect is osx or Gentoo..Can't connect on the live cd's or ubuntu?....scott

---

