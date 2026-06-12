---
title: "DWL-G650 Wireless on 8.10 not working"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Joe2Shoe on 2008-11-03
I am using a D-Ling DWL-G650 AirPlus ExtremeG PCMCIA Card with Ubuntu 8.10, and the card shows 4 bars at the top-right of the screen where the 'network' monitors are.
But, I cannot visit any websites; it says "cannot find server".
Can anyone please help me, I am at my wits end!  I'm about to loose it.

Here is my Wireless Card info
D-Link DWL-G650 AirPlus ExtremeG PCMCIA Card


WLAN connection information

Interface: 802.11 WiFi (ath0)
Hardware Address: 00:xx:xx:xx:xx:xx (changed here for security reasons)
Driver: ath_pci
Speed: 54 Mb/s
Security: WPA/WPA2

IP Address: 192.168.11.3
Broadcast Address: 192.168.11.255
Subnet Mask: 255.255.255.0
Primary DNS: 192.168.11.1
---

Under "Edit Connections"
Connect automatically: is Checked
System setting: is not Checked

Wireless tab
SSID: name of network
Mode: Infrastructure
BSSID: blank
MAC address: blank
MTU: automatic

Wireless Security tab
Security: WPA & WPA2 Personal
Password: xxxx

IPv4 Settings tab
Method: Manual

Addresses section
Address: 192.168.11.3
Netmask: 24
Gateway: 0.0.0.0

DNS Servers: 192.168.11.1
Search Domains: blank
---

---

### Post by Joe2Shoe on 2008-11-03
To answer my own inquiry:

So, I uninstalled 8.10, then reinstalled 8.04 Hardy Heron.
Now, my D-Link DWL-G650 AirPlus ExtremeG PCMCIA card works using the ath_pci driver.
But, my Broadcom BCM4306 internal wireless adapter does NOT work, period!
The DWL-G650 only costs $13.38 on amazon...that includes shipping...what a cheap fix!
I guess I will stick with this setup on this laptop for awhile.
And, NO, NDISwrapper does NOT work with the Broadcom BCM4306 chip in 8.10 or 8.04. I tried so many variations attempting to get it to work, that I forgot why I got up this morning. I finally threw the towel in!
Best wishes to all, and a good night.
Joe2Shoe.
I am online right now using the D-Link DWL-G650 and 8.04 Hardy Heron.
Joe2Shoe is online now Report Post   	Edit/Delete Message

---

