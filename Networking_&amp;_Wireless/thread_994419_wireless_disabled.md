---
title: "wireless disabled"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by newojade on 2008-11-26
MY friend just switched my windows xp to ubuntu and my wireless wasn't working so I did whatever command and found out that it is disabled and the help topics say that I have to turn it on through windows.  I don't know how to do that.  Can somebody help me?

I have a DELL Latitude D900.

---

### Post by h4v0k_d0m on 2008-11-26
There should be a icon next to your battery indicator on the top right corner of your desktop shows there is no connection click it to run the wireless and connect to your essid

---

### Post by rlzyoner on 2008-11-27
//Bring up the interface
sudo ifconfig [wirelessAdaptorName] up
//Scan for available wireless networks
iwlist [wirelessAdaptorName] scan

[wirelessAdaptorName] may be something link ath0, wlan0, eth0, eth1 or something similar

---

