---
title: "wifi will not connect"
date: 2013-10-17
forum: Networking &amp; Wireless
---

### Post by boyo1991 on 2013-10-17
I've done some looking and none of the ideas have worked. I've tried turning on and off the wireless, and when I try:

Sudo iwconfig wlan0 channel 03

I get device or recourcse busy.

So I've tried the command with networking off, same deal.

I want to change channels because every other device in the house seems to connect to the network just fine, except my lubuntu machine. My ubuntu machine, windows 8 machine and android devices work just fine.

Sensativity is forced auto on my card so I cannon set sens...

Thanks guys!

Boyo

---

### Post by Hadaka on 2013-10-17
Hi,, the channel selection/setting is done at the router.
Not the wlan0 settings. Your other machines will auto/adjust
to the channel change. Generally chan 1 or 11 seem to work best
with Ubuntu, and also set to wpa2. Hope that helps.

---

### Post by boyo1991 on 2013-10-17
Well its not a channel change problem I've discovered as my ubuntu (12.04) machine works fine in the same place, same with my android device.

This is exactly what happens:

-I boot the machine up
-it connects to the network for about a minute
-it all of a sudden seems to not find the network, even though the machine right next to it shows full strength along with previously showing full strength on my "problem" system.

Lshw -C network shows:

*-network
Description:wireless interface
Product: RT3290 wireless 802.11 1T/1R PCIe
Vendor: Ralink corp.
Physical I'd: 0
Bus info: PCI@0000:02:0.0
Logical name: WLAN0
Version: 00
Serial: f4:b7:e2:32:9
Width: 32 bits
Clock: 33mhz
Capabilities: bus_master cap_list Ethernet physical wireless
Configuration: broadcast=yes driver=rt2800pci driverversion~3.11.0-12-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
Recources: irq:53 memory:f0210000-f021ffff

Sorry if that doesn't make sense. I had to take type it from my phone as well I'm or able to connect with the machine right now lol

Help would be fantastic :(

---

### Post by boyo1991 on 2013-10-18
new update!

the wifi seems to stay connected until I use it. When I use firefox it automaticly disconnects, but if I dont use the internet, it stays connected, until in use.

this happens about one boot per day. other than that, it auto disconnects.

thanks!
boyo

---

### Post by wildmanne39 on 2013-10-20
Bump after a title change.

---

