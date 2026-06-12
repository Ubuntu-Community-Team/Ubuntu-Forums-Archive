---
title: "WiFi Card Sees Networks But Cant Connect"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by _JeK_ on 2008-07-08
Hey Everyone. I'm just a Linux noob seeking some help.

I installed Xubuntu hardy about a week ago and wireless was working perfectly on my Thinkpad X61s. I'm not sure exactly what happened but now when my wireless card is set to roam, the network manager app doesn't show up on my taskbar and show the dropdown with available networks like it did before.
Also, after finding my way into system => networks, when I disable roaming, I can see my ssid and signal strength from surrounding networks. When I try to select my ssid, enter my wep key (hex), and set the network to dhcp, it updates the network settings but i'm still unable to get online or ping. 
I am positive the card is functioning because I have it dual boot with vista and no wireless issues there. 
I'm going to emphasize again that i'm an utter noob with linux haha :) . Any help would be greatly appriciated.

-Joe

---

### Post by rlzyoner on 2008-07-08
To get the network manager applet icon back, run the command 

*nm-applet*

To get it back permanently, System -> Preferences -> Sessions 

Now under the startup tab, enter nm-applet.

Regarding the wireless, 
Please post the output of *iwconfig*, *ifconfig* and also if you are using ndiswrapper, post output from *ndiswrapper -l*

---

### Post by _JeK_ on 2008-07-08
Running nm-applet just seems to hang up terminal. I also couldn't find the direct pathway to sessions but I found sessions and startup under settings. The only problem is that there is no option for enabling and disabling start up items from this menu.

iwconfig output looks as follows

lo - no wireless extensions
eth0 - no wireless extensions
wifi0 - no wireless extensions
ath0 - IEEE 802.11g ESSID: "my ssid" Nickname ""
  Mode: Managed Frequency:2.437GHz Access point: not associated
  Bit Reate: 0kbps Tx-Power: 8dBm Sensitivity: 1/1
  Retry: off RTS thr:off Fragment thr: off
  Power Management: off
  Link quality: 0/70 Signal level=-90 dBm Noise level=-90dBm
  Rx invalid nwid: 3993074 Rx invalid crypt:0 Rx invalid frag:0
  Tx excessive retries:0 Invalid Misc:0 Missed beacon:0

By the way thanks for the reply

---

### Post by sfarber53 on 2008-09-07
I think my problem is similar so I'll post it here.

My Xubuntu system is able to access the internet via Firefox, but it cannot see the other computers on my network (wired and wireless), which can see the Xubuntu box and each other.  Anyway, I'm a bit mystified by this and could use some advice as to how to rectify the situation.

I've installed Nautilus to try to solve the problem, but no luck.

Any suggestions?

Thanks in advance.

---

