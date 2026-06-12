---
title: "linksys wmp54g v2"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Lexus Dominus on 2008-02-18
Ive just installed the newest ubunto & am trying to get connected. when i click on network connections it asks me if i want to create new nework/manually connect, but shows me none of the wireless networks in the area or my own. ndisgtk program supports my card, so i installed the packages & booted it up from the terminal. when i try to install the driver for my card (bcmwl5.inf) the terminal returns "module configuration already contains alias directive" & doesnt do anything else. i can only assume the driver is already installed however it doesnt appear on the ndisgtk gui. any ideas why this is happening to me? i cant stand coming back into windows to use the internet. any help would be much appreciated.

---

### Post by Lexus Dominus on 2008-02-18
this was my reply from lshw if it helps:

 *-network:0 DISABLED
  description: Wireless interface
  product: BCM4306 802.11b/g Wireless LAN Controller
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:02:00.0
  logical name: eth1
  version: 03
  serial: 00:0f:66:1b:55:2d
  width: 32 bits
  clock: 33MHz
  capabilities: bus_master ethernet physical wireless
  configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22

---

### Post by Lexus Dominus on 2008-02-18
Problem solved... 
you have to install firmware for the bcm43xx family chipset using the bcm-fwcutter tool found here- [http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/dapper/utils/bcm43xx-fwcutter). the firmware itself is found here-http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o

go to system>admin>restricted drivers & enable it. 
bingo

---

