---
title: "asus WL167G fails DHCP with 8.10"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by jdspence on 2008-11-18
My asus WL167G (RT73 chip?) does not work with 8.04 Hardy Heron (unless I disable security) on my Shuttle XPC G2 desktop.  I tried the 8.10 Intrepid Ibex live CD, and it seems to work with the wifi end of my WPA2-AES setup (Linksys WRT54GL, Tomato 1.19), but DHCP doesn't work.  In my router logs I see a DHCPDISCOVER (but with no hostname), a DHCPOFFER response, but no DHCPREQUEST or DHCPACK.  Everything works fine in Win XP and with 8.04 with ethernet.

Any known solutions to this?  

Also, if anyone is in the mood for answering, is there an "official" way to get Ralink chips working with Hardy Heron?  I've found a few driver install scripts on forums, but I'm a little reluctant to get my system butchered.  Any way to contribute to a bounty or otherwise encourage true out of the box operation with these popular wifi dongles (since coding device drivers is beyond my ability)?

Thanks!

---

### Post by eric stockman on 2008-12-26
Got the same problem with Ibex .
Added the following lines to /etc/network/interfaces :
iface wlan0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key ( same WEP-key as in ADSL-router )
wireless-essid ( same as in router )
auto wlan0

--> no change ??
Connected to router directly with Ethernet cable
changed 'enable  broadcast' to NO 
disconnected   cable
did a sudo ifdown wlan0
      sudo ifup wlan0  
bingo : we were in business ! Don't ask me why or how ????

---

### Post by jdspence on 2009-01-12
Found a work-around.  This is bizarre.
A fresh install of Intrepid Ibex 8.10 works perfectly out of the box with WPA2-AES.  But it stops working after using Windows XP.  But, if I switch USB ports, then it works fine.  So the WL167G has to be in one USB port for XP and a different one for Ubuntu.  XP works fine regardless; it's only Ubuntu that has the problem.

---

