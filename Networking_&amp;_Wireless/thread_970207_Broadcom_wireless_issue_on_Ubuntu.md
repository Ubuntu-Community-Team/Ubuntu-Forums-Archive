---
title: "Broadcom wireless issue on Ubuntu"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Prime 360 on 2008-11-04
I'm new to Ubuntu/Linux, but been into computers since the MS-DOS days.

I installed Intrepid on my laptop last week and got my wireless working great after installing the b43-fwcutter files.  It would connect at 54 Mbps to my home router with WPA.

I had some problems yesterday connecting, but now I'm able to again. Strange thing though, before whenever I would check the connect speed, it was always 54 Mbps. Now it is sometimes, but I see it drop quite a bit, sometimes as low as 1 Mbps, although web browsing still seems to be normal.

On top of that, when I click the bars in the top toolbar and look at Connection Information, for "Driver:", it now says "NULL(info.linux.driver) and I could swear that it wasn't always like that.  

The last system updates before my connect problem were at least 12 hours earlier.  The only thing I did more recently was install the ubuntu-restricted files for audio and video codecs, and installed Real Player for Linux and Firefox Media Connectivity extension in an attempt to get BBC streaming audio to work (which didn't).  Could that have borked something with my wireless drivers by chance?

Here's my lshw -C Network in case that helps:

>   *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:6d:d6:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b6:08:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 62:a7:f0:78:cc:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Any advice would be apprciated. I've looked through numerous threads on here, but haven't found anything that's sounded close to this.

---

