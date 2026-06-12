---
title: "hardy wireless"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by oldjudithp on 2008-05-13
I have dual boot of XPPro and Hardy on an Asus F5RL laptop with extra 1Gig memory. I connect through Eth0 by cable to a wireless modem to the net - it works perfectly. Using Win I can disconnect the cable from the modem and have internet connection via wireless. The wireless card and its Win driver must thus be OK.
Problem is that I need to connect via wireless in Hardy.
All 3 ndis apps are loaded.
"iwconfig" gives 
lo   no wireless extensions
eth0 no wireless extension
The ftted ethernet controller is Atheros AR242x 802.11a/b/g wireless PCI Express Adapter (Rev 01)
"cat /etc/network/c/interfaces" gives
auto lo
iface lo inet loopback
"lshw -C network" gives details of both but shows the wireless network as UNCLAIMED.
I thus assume i need to install a Lnux driver but a)Which one b) where do I get it and c) How do I install it?

---

### Post by Me! on 2008-07-18
Hi

I Install my wireless driver from by this page:

[http://www.lucioalbenga.com/2008/06/11/asus-f5-laptop-with-ubuntu/](http://www.lucioalbenga.com/2008/06/11/asus-f5-laptop-with-ubuntu/)

it is work fine !

I can not use my wireless before this driver , but now I thanked god for this driver

I found this page also here:

[http://ubuntuforums.org/showthread.php?t=816780&highlight=asus+f5rl](http://ubuntuforums.org/showthread.php?t=816780&highlight=asus+f5rl)

I hope that help you

---

