---
title: "A Broadcom BCM4318 Problem"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by whizzlegear on 2008-09-11
Hi All,

I am new to ubuntu and linux in general. I have just installed ubuntu hardy on my acer aspire 3000. I seem to be having difficulties with getting the wireless connection to work. I have tried searching these and other forums and trying various solutions but nothing has worked so far.

When I first installed unbuntu it offered me the choice of downloading a driver for the card, something along the lines of fw-cutter which I did.

The wireless card appears to be working as the wireless LED on the front is solidly illuminated and it can detect mine and other networks in range. If I try to connect to my network however it just tries for a bit and then fails but doesnt give any feedback as to why it has failed.

The network is running WPA security, but I have tried disabling wireless security altogether and connecting but it still did not work.

Any help you can offer to get me up and running would be appreciated. Please bear in mind that I am a complete beginner to linux so if you need any more information about my system please give instructions on how I can obtain it!!!


Output from lspci:
> 00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by superprash2003 on 2008-09-11
does it connect when you disable the security??i mean to say it connects but nothing works??... if it doesnt connect at all, then you may want to try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by whizzlegear on 2008-09-11
It doesnt connect at all, again it just tries for about 30 seconds then fails without any output or feedback.

---

### Post by lavinog on 2008-09-11
Which version of Ubuntu are you using?
What is the model number of the router?

I would avoid following that guide since it is outdated.

Have you tried connecting via command line?
```
sudo iwconfig <interface> essid <ssid>
sudo dhclient <interface>

```
<interface> would be your wireless interface. Mine usually is eth1.
you can type iwconfig to figure out what your interface is.

NOTE: I am not at my laptop on the moment so I am going from memory.

---

### Post by Ayuthia on 2008-09-11
> **lavinog said:**
> Which version of Ubuntu are you using?
What is the model number of the router?

I would avoid following that guide since it is outdated.

Have you tried connecting via command line?
```
sudo iwconfig <interface> essid <ssid>
sudo dhclient <interface>

```
<interface> would be your wireless interface. Mine usually is eth1.
you can type iwconfig to figure out what your interface is.

NOTE: I am not at my laptop on the moment so I am going from memory.

The [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that was posted is actually up to date.  It is just the title that is not up to date.

---

### Post by whizzlegear on 2008-09-11
The router is a netgear wpn82v3.

I tried the guide that was posted but that didn't work.

I tried connecting via the terminal, here is the output from that attempt:

```
There is already a pid file /var/run/dhclient.pid with pid 6134
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0e:9b:d6:da:90
Sending on   LPF/wlan0/00:0e:9b:d6:da:90
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

The ubuntu version I am using is...

Ubuntu 8.04   - the Hardy Heron

---

### Post by whizzlegear on 2008-09-12
Bump

---

### Post by TSupra88 on 2008-09-12
try this: [http://tsupra88.blogspot.com](http://tsupra88.blogspot.com)

(I've written a quick, but clear tutorial that will help you install broadcom cards and I've provided links to the necessary drivers/firmware.)

---

### Post by whizzlegear on 2008-09-12
Unfortunately that guide did nothing for me. Still not working :(

---

### Post by TSupra88 on 2008-09-12
The guide has worked well for many, I believe your problem is not with the driver/card, it could be with your router. Did you enable mac address filter on your router? It may be blocking out your card, or maybe the router/card is set to a different wireless band than the router?

---

