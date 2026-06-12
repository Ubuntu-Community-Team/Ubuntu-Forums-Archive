---
title: "Linksys WPC54G-EU wireless card"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by robfranssen on 2008-08-19
Hi,
I'am new to linux and installed Xubuntu 8.04 on a Compaq Armada 1700 with aand tried to get a Pentium II, 166 MB and 3 GB HD 
In an effort to get a Linksys WPC54G-EU wireless card working, i installed ndiswrapper 

'sudo lshw -C network' showed:
*-network
  describtion: Network controller
  product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:01:00.0
  version: 02
  widt: 32 bits
  clock: 33MHz
  capabilities: bus_master
  configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network DISABLED
  describtion: Wireless interface
  physical id: 1
  logical name: wlan0
  serial: 00:16:7e:e7:52:3e
  capabilities: ethernet physical wireless
  configuration: broadcast=yes ip=192.168.2.210 multicast=yes wireless=IEEE 802.11g

'sudo ndiswrapper -v' showed:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.52
vermagic: 2.6.24-19-generic SMP mod_unload 586

'sudo ndiswrapper -l' showed:
bcmwl5 : driver installed
              device (14E4:4318) present (alternative driver: ssb)

Following intructions on [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926) , the command
'sudo dmesg' showed lots of things, but also:
[  114.222529] b43-phy0: Broadcom 4318 WLAN found
[  114.266510] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[  114.266565] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[  114.295613] phy0: Selected rate control algorithm 'simple'
[  115.386978] input: b43-phy0 as /devices/virtual/input/input4
[  115.553673] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed
[  115.553714] b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4).

The error-messages in the last two lines are repeated 9 times for various reasons. The webpage shown says, "This page does not exist yet." 

I'm afraid this is all gibberish to me and i would appreciate if somebody could ' give me a hand'

---

### Post by robfranssen on 2008-08-19
Using the intructions fromhttps://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix
and the driver-inf file, supplied with the wireless card on CD, i got to the point, that - after a reboot - 'sudo lshw -C network' now responds with:

configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,02/ latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

However, Wireless Networks doesn't show any wireless network, although there ara plenty around

---

