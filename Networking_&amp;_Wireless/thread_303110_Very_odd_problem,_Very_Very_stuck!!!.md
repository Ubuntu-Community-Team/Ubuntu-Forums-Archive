---
title: "Very odd problem, Very Very stuck!!!"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Courior on 2006-11-19
Hello everyone. I'm (yet another) newbie but im learning fast and i wanna be a linux guru! maybe... one day!. 

my problem is this.. i have a DLINK G122 usb wireless card. I plug it in and boot up ubuntu and once logged in the green "link" light stays solid. in windows this means its connected and working. however its most definatly not working. the activity light hasnt blinked once! This is why its an odd one. When i go to network setting and untick WLAN0 the link light goes off, and it comes on again when i re tick the box. This tells me the drivers are installed (i am on UB 6.10 FYI). It just will not send or recieve traffic. and my router is not showing it as a connected device via DHCP. I do have a network key which i have filled in the "properties" box of the WLAN0 profile.

A Little note, whether or not its useful im not sure. In network connections i have 2 wireless connections WMASTER0 and WLAN0. the master one has no effect on my DLinks lights, and i have only one wireless device attached to my pc. 
pleeeeeeeeease help!!!! Thanks soooooo much in advance!! ](*,)

---

### Post by FrodoB on 2006-11-19
The group need at least the following to understand enough to comment:

1) The exact model and version of your device

2) the devices identification using one of the following:

If it is a USB device:

lsusb

If it is a PCI device:

lspci

If it is a PC Card (PCMCIA):

cardctl ident

3) The output of iwconfig
iwconfig


4) Contents of /etc/network/interfaces:

cat /etc/network/interfaces

---

### Post by Courior on 2006-11-20
HI, Thanks for the fast reply. Here is the info that you wanted:

1) The exact model and version of your device
D-LINK DWL-G122 Rev: C1 F/W Vers: 3.00

2) the devices identification using one of the following:

If it is a USB device:
lsusb gives me this:
Bus 001 Device 002: ID 07d1:3c03 D-Link System
Bus 001 Device 001: ID 0000:0000



3) The output of iwconfig
iwconfig:
lo no wireless extensions

eth0 no wireless extensions

wmaster0 IEEE 802.11g Frequency:2.412Ghz
         RTS thr: off  Fragment thr= 2346 B

wlan0 IEEE 802.11g ESSID:"Mayom"
      Mode: Managed Frequency:2.412Ghz Access Point: Not -Associated
      RTS thr: off Fragment thr=2346 B

sit0 no wiress extensions


4) Contents of /etc/network/interfaces:

cat /etc/network/interfaces:

auto lo

iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2 
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Mayom
wireless-key ****MYKEY****

auto wlan0

Thats the end of the command. Just as a note. "Mayom" is what my network is called.

This means nothing to me... but hopefully it will to you and you can help me :) thanks!!!!

---

### Post by FrodoB on 2006-11-20
OK, from your USB ID I can see by looking on the we that your device is an rt73 decice. 

Follow these instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

Good Luck

---

