---
title: "Dapper Drake 6.06 &amp; RTL8187L"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Kapalua on 2007-07-23
Ok...i have been trying to get a USB network adapter with the RTL8187L chipset to work under Dapper Drake 6.06.
With the ndiswrapper and the Win98 driver i have managed to get the card talking to the computer. At least at some level....
When doing iwlist wlan0 scanning it finds networks(including my own), but when trying to connect to the network it's just not able to.
The network manager says the device is idle when trying to connect with it.


It shows up like this with ifconfig:
wlan0  Link encap:Ethernet  HWaddr 00:00:00:00:00:00 * Removed
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:109 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

On the adapter there is a led which only blink green sometimes.
Tried the adapter with XP, works just fine.


Don't know what kind of information that is important about this issue so i guess this is what i know for sure. If you can help me just ask for it. :)

Thanks in advance.

---

