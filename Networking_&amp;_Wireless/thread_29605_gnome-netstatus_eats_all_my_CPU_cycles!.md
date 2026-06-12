---
title: "gnome-netstatus eats all my CPU cycles!"
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by ozE on 2005-04-25
```
top
%CPU	%MEM	TIME+		COMMAND            
99.4	3.3	10:31.37	gnome-netstatus..
```
This is a brand-new Hoary install, the very first thing I did was follow [QUOTE=pdaliu]Hi:
  I've just made my DWL-122 work on Ubuntu (Hoary PowerPC) without any other outside package or driver input.  I hope it helps.

0) Make sure your linux-wlan-ng package is installed.

1) Try plug your DWL-122 and use lsmod to see if prism2_usb is appropriately loaded.  If no, your kernel has something wrong.  The module is even bundled in Warty.

2) Find the follwing line in /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

    And let this line executed TWICE.  Yes, twice.  It seems successful initiation needs two visits.

3) My wireless network is simple, i.e. MAC filter without any WEP.  So I added the following to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
        wireless_essid  your_essid
        wireless_mode   infrastructure

4) ifup wlan0

Then it should work![/QUOTE] and it worked for about 20 seconds, or so, before everything slowed to a crawl...Since I had a terminal window open, I was able to 
```
top > wtf    
kill 7820
```
(I got the above line from top from the wtf file :D) so at least the system was usable, again, but since killing gnome-netstatus also killed the wireless adaptor, usable is a relative term...  ;-)  

After rebooting the system, WiFi is available, again, and gnome-netstatus is no longer active. ( I assume this is the windows-esque icon in the top corner which displays the flashing PC icons?)   

Any suggestions?

---

