---
title: "D-Link 120+ issues"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Ouoertheo on 2007-09-10
I've been trying to get the d-link dwl120+ wireless usb adapter to work in Ubuntu 7.04 64 bit, but have'nt had much luck at all.

I've been able to get the drivers installed and the device to be recognized by both the open source acx100 drivers and using ndiswrapper on the manufacturer's drivers, but it never recognizes the device in the network manager. 

First I tried downloading and building the open source acx100/111 module (the dwl120+ is acx and dwl120 is prism), but wlan0 was always set to avahi or nothing in the network manager.

I did get it to read once, but then it restarted after downloading all the updates and never came back.

Then I tried the following:

lsusb lists the following:
Bus 002 Device 004: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 011: ID 2001:3b01 D-Link Corp. [hex] 
Bus 001 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  

Make and install ndiswrapper
blacklist acx and remove it using: 
$ sudo rmmod acx

load windows driver:
$ sudo ndiswrapper -i tiacxusb.inf

$ sudo ifup wlan essid NETGEAR
Ignoring unknown interface wlan=wlan.
Ignoring unknown interface essid=essid.
Ignoring unknown interface NETGEAR=NETGEAR.

After all that and much more, I still can't get the wireless adapter to work.

Does anyone have any ideas, tips, or resources on how to get Ubuntu to use the card. I've gone through almost every post here...

---

