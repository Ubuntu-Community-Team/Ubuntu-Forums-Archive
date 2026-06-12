---
title: "Wireless not working after windows - ubuntu switch"
date: 2014-05-28
forum: Networking &amp; Wireless
---

### Post by koos3 on 2014-05-28
My laptop often will not connect via wifi , the adapter appears to be blocked. Even after several restarts, until it suddenly works in ubuntu. After using both ubuntu and windows once, the adapter does not work anymore in either system. This is continuously after the first use of windows that is does not work in ubuntu. Once I've tried ubuntu, the adapter dors not work in windows either. I have been through this cycle several times, but so far I have not been able to find out why it works or not.
Wired internet does not have this problem though. but unfortunately I often rely on wifi.

Hardware: 
HP EliteBook 8530w ( TU/e 2009 laptop ) with windows 7 ultimate and ubuntu 12.04 (both x64 ) in dual boot on GRUB.
Wireless: Intel (R) WiFi Link 5300 AGN
 
Some of the things I have already tried :
 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
-> Displays error , something with rfkill
 
-adapter Reinstall Windows .. ( afterward it worked in linux, after a couple of windows reboots)
-numerous restarts
-WLAN/LAN Automatic switch off in BIOS (which is on again )
-Just before shutting down windows with working wifi in CMD: ipconfig / release ( for releasing MAC address)
 
iwconfig in ubuntu shows; 
Soft blocked : no 
hard blocked : yes (for the wlan adapter)
 
If I have to post some extra info / try out something out, please tell.

thanks in advance, Koos

---

### Post by koos3 on 2014-05-30
Please does anyone have an idea? It looks like a low level problem but its holding me back in using ubuntu since wifi is now working in windows..

---

