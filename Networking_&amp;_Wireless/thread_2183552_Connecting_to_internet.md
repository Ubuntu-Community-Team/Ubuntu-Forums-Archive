---
title: "Connecting to internet"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by Phil's Dad on 2013-10-25
Hi, I have recently installed Ubuntu 12.10 on my ageing desktop. The desktop worked wirelessly with a Belkin SURF N300 network adaptor. When I boot up, I see a "Talktalk connection established" message and if I click on the network icon at top right, I get the option to disconnect so I assume the device is connected.

I ran the nm-tool in a terminal and got the following:

Device:  wlan0 (Talktalk)
Type:    802.11 WiFi
Driver:   rtl8192cu
State:  connected
HW address:  EC::1A:59:64:63:BF

So it all seems to be OK but I can't access a web page through my browser. The router is working because my laptop works fine.

Any ideas, please?

---

### Post by Phil's Dad on 2013-10-25
Just checked with Belkin and they say the device I have will only work with Windows. Does anybody know of a suitable replacement?

---

### Post by BBQdave on 2013-10-25
> **Phil's Dad said:**
> Just checked with Belkin and they say the device I have will only work with Windows. Does anybody know of a suitable replacement?

OK, wait a second :D

I am still researching your exact model, but you can use any system, osX, Windows, Linux with a web router - sometimes you have to use your browser to configure the router, if your system is not Windows.

In brief: your router works with osX, Windows, Android - which is Linux. Your router will work with Linux. There is a default network name and password that is on the router - to connect wireless devices. I would highly recommend that when you have time, you enter into the routers admin application - should be able to do that through your browser - and change your router's password from the default it was shipped with.

You may want to connect directly to the modem, to make sure you have an internet connection, then proceed with the router and router configuration :)

---

### Post by Johan De Cauwer on 2013-10-25
Actually the good news is that the driver for rtl8192cu exists and the bad news is that solutions like [http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver](http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver) are not exactly meant for beginners. There exists a link to a compatibility list of usb wireless adapters on this forum: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) so if you want to buy a new one there is all the info.

---

### Post by grahammechanical on 2013-10-25
You are right when you see this and say all seems to be OK. It is as far as Ubuntu recognising the N300 and installing a driver for it.

> [COLOR=#000000]Device: wlan0 (Talktalk)[/COLOR]
[COLOR=#000000]Type: 802.11 WiFi[/COLOR]
[COLOR=#000000]Driver: rtl8192cu[/COLOR]
[COLOR=#000000]State: connected[/COLOR]
[COLOR=#000000]HW address: EC::1A:59:64:63:BF[/COLOR]

The driver is installed and the N300 is connected to something. And that seems to be the Talk Talk wireless access point or router. But you are not getting Internet access. Are you getting page not found error messages from the browser? Double check that the router is actually connected to Talk Talk. Ubuntu will connect to a router that is switched on but if the router is not connected to the ISP we will not get Internet access. We should get a message that avhi has been disabled because we are on a local network (if I remember it correctly).

Regards.

---

### Post by Phil's Dad on 2013-10-26
Thanks for your replies,guys. I think I need to clarify. I have a Talktalk router connected to fibre and my Windows 7 laptop sitting next to my desktop works just fine using it's own in-built wireless card. My desktop does not have a wireless card and I used a USB wireless adapter to do the job. That was OK with Windows but I can't get internet access with Ubuntu.

When I start Firefox, I get "Server not found. Firefox can't find the server at start.ubuntu.com" It's not a router problem  -  is it? The laptop's OK. Is it just Ubuntu for some reason unable to communicate with the wireless adapter?

Regards

---

### Post by wildmanne39 on 2013-10-26
*Thread moved to **Networking & Wireless**.*

---

