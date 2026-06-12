---
title: "device installed, yet no connection"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by jdemarco on 2007-08-12
I am very close to having my device installed, I think I am missing something small.

I have successfully installed my device (zyxel g-302) using ndiswrapper and added it to the modlist.
ndiswrapper is active after boot and my device is present in the network manager.

When I i do 'iwconfig'

wlan0 IEE802.11g ESSID: off/any Access point:not associated ..etc

The channel is correct and the other settings (WEP ESSID) are configured correctly in 
etc/network/interfaces

I have tried to connect with WEP off and still no dice.

When I use 'ndiswrapper -l' i get: driver installed device (10EC:8185) present (alternate driver: r818x)

r818x is not listed after running 'lsmod' 
I put it on the blacklist to be sure, but it still appears when I run the command above.

I have a wired connection also. Could there be a conflict with the wired card?

Please let me know id there is anything I am missing. This is making me crazy!

---

### Post by jdemarco on 2007-08-12
I used 'iwconfig' to change my key to open, and now when I run iwconfig, the access point ESSID and channel are all correct, However I cannot connect to the internet and my computer is not displayed on the list of wireless connections on the routers config page.

I can ping the router.

EDIT 

Ok, I restarted my modem (not sure why that would make and difference) and now I have connection but only for a few seconds at a time.

My computer is on the list of connected wireless machines and persists.

When I try to ping the modem sometimes it pings then sometimes I get Destination Host Unreachable, yet the modem config page still shows the connection as active.

---

