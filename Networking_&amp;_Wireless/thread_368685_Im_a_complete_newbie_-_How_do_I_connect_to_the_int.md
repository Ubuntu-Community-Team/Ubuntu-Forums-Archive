---
title: "Im a complete newbie - How do I connect to the internet in ubuntu?"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by conn18 on 2007-02-23
Hey. I am COMPLETELY new to linux, and I'm not very good at computers or whatever.
I've just installed ubuntu on my other computer, and I need to conncet to the internet.
How do I do this? We have a wireless network in the house and my PC has like a little aerial in the back of it.. I hope you unerstand what I mean.. I'm really dumb.

---

### Post by chili555 on 2007-02-23
We've all been there, conn, so don't be shy, we'll get there together!

There are two possibilities: first that Ubuntu recognized your wireless card, loaded the driver and is just waiting for your command to connect (somewhat less likely) and, second, that we need to install a driver or a wrapper around the windows driver and *then* command it to connect (somewhat more likely).

First, let's see what we have and don't have. Open a terminal (Applications -> Accessories -> Terminal) and issue the command sudo iwconfig. You'll have to enter your password. If it kicks back an interface with lots of seemingly meaningless data, like mine: ```
wlan0     IEEE 802.11g  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:62:8D:F7   
          Bit Rate:48 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-61 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` then do a cartwheel because your wireless card is almost set! :) 

If it comes back " no wireless extensions" for *all* the interfaces, then we have a bit more work to do.

In that case, issue the command sudo lspci | grep Network. That means, roughly, "list all my devices but write only those with 'Network' in their description." That will tell you the particulars you need to know to find out how to configure your wireless card. 

It will tell you the chipset your wireless card uses, and you will find out there are only so many in the world. You can do a search on this forum for the chipset, say rt61 or bcm43xx or ipw2200 and see a few dozen posts about getting it going.

When (not if) you get stuck, post back and we'll get you unstuck. Good luck.

---

