---
title: "network manager broken?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by dimeotane on 2007-10-21
I upgraded to Gusty  (from feisty) and it detected my broadcom internal wireless card on my Dell XPS M1210, so I removed ndiswrapper.  I needed to use my eth0 hard line to download and set up the restricted driver for the ethernet card.

lspci shows it as: 
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Here's the problem... nm-applet and network-admin both aren't working to get me on the net.  I have to do it manally in the terminal.  I used to get the wireless menu in the nm-applet.  What's going on? 

I know for sure that my broadcom 43xx card works great,&  am using it right now. I can connect through the terminal using:

sudo ifconfig eth1 up; sudo iwconfig eth1 essid <WIRELESS NETWORK NAME>; sudo dhclient eth1 

both iwconfig and ifconfig show my eth1 wireless

What's broken and how do I fix it.

---

