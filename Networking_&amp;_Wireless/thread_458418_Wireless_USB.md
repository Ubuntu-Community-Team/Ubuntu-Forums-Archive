---
title: "Wireless USB"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by ivesjd on 2007-05-29
I recived an Ashton Digital USB wireless dongle. I first got it working in windows to make sure it worked at all. Then it was to linux. After some research I discovered that it had been set-up using ndiswrapper. So I installed ndis wrapper, and then the drivers. After a few frusterating hours it finally seemed like I had gotten it. Network Manager says that wireless is enabled. I can click the connect button and type in the network, but it just says "wireless network connection to 'XXXX' (0%)". My laptop is right next to it with a 70-80% connection (with ubunutu). I would just use a network cable but the router is on the other side of a block wall (i think) and I dont have access to it (university houseing). Any help would be greatly appreciated.
Need anymore info? Just ask.

lsusb =
Bus 001 Device 006: ID 124a:4017 AirVast PC-Chips 802.11b Adapter

lshw =
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: wlan0
capabilites: ethernet physical
configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes

ndiswrapper -l =
   avwlpnic : driver installed      
    device (124A:4017) present (alternate driver: prism2_usb)

iwconfig =
wlan0      no wireless extensions

---

### Post by ivesjd on 2007-06-15
[http://ubuntuforums.org/showthread.php?t=458570](http://ubuntuforums.org/showthread.php?t=458570) heres another thread with some help

---

