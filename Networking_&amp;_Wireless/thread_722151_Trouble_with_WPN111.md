---
title: "Trouble with WPN111"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by gianchi on 2008-03-12
Hello there.

I have installed roughly 1 month ago Gutsy desktop 32-bit on my pc (you can see main specs in my signature). 

Since then, it's been hell to have a working net. I have a Netgear WPN111 wireless adapter. I managed to have it working with ndiswrapper, but it seems it's not stable.

When Network Manager isn't freezing the system, the net works only for a variable amount of time, from 5 minutes to 8 hours, but, eventually and unavoidably, it stops working.

I have tried some of the howtos of the forums (like Kevdog's and Wieman's), but, not really knowing what the problem is, I'm just taking shots in the dark. And I'm a totally Linux newbie, so I don't even know if I'm doing things right or how to correct mistakes....

In conclusion, please, help me fix this issue. Tell me what you need to know and how I can get the informations, I'll gladly do.

---

### Post by kevdog on 2008-03-12
Ok, we need to determine whether its a driver problem or Network Manager problem (NM).  

I disconnect from the network using NM, and then bring the interface up using the command line.  Wait a while and see if it disconnects.  The command line usage is in my signature -- its meant only for testing and not long term use.

---

### Post by gianchi on 2008-03-13
Hi Kevdog, 

thanks for your reply. Unfortunately, I'm afraid I have not enough info to proceed. And something strange is going on on this pc.... this is going to be a long post, sorry.

Anyway... first thing I did, was to disable network by right-clicking on NM icon and selecting "disable network" (not sure about the translation, I'm using Italian as language). Then, from console, I typed
```
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

getting this output:

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/wlan0/00:14:6c:5d:1e:1e
Sending on   LPF/wlan0/00:14:6c:5d:1e:1e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

But I'm not sure I did it right, I'm not sure this is what you meant when you wrote:

> **I disconnect from the network using NM, and then bring the interface up using the command line. Wait a while and see if it disconnects.**

However, after doing this, I tried to run again the howto linked in your signature, about manually connecting without NM. I restarted the system, turned the network down in the same way I did above, and followed the tutorial. When I run this line:

```
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
```

it started something, but it never ended, it kept trying to connect, I think, I had to close the terminal via GUI (I don't even know how to stop it! :p)

At that point I tried to restart the network from NM to make this post, no joy, while it could still see the SSID, it didn't connect.

At this point, something strange happened. I restarted the box, selecting WinXP pro as OS, it loaded, but after the splash screen I had about 10 second of black screen, then the login screen. Logged in, network not working, despite the light on the WPN told me that the USB adapter is fine. The Netgear network wizard didn't work (I had the WPN111.exe in the task manager, though), and Windows didn't recognize any wireless network (meaning there wasn't any wireless connection in the "All network connections" window)..... I've always thought the OS's on the same box couldn't influence each other, but I'm afraid I'm wrong....

So, the question is: what's going on?

---

### Post by gianchi on 2008-03-15
BUMPed for Kevdog.

---

