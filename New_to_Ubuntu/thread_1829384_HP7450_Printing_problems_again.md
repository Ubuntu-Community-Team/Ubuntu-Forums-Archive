---
title: "HP7450 Printing problems again"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by woody1 on 2011-08-20
Hi all,
 I am running 10.04LTS on a netbook and trying to print to an HP Photosmart 7450. Having printed one picture I now get a message in the General tab of the Print dialogue "usr/lib/cups/backend/hp failed"

lsusb gives
colin@netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 052: ID 03f0:b802 Hewlett-Packard PhotoSmart 7400 series
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 13fe:3100 Kingston Technology Company Inc. 
Bus 001 Device 005: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 004: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

,so I presume that it's still seeing the printer,and according to synaptic I am running the latest version of cups and HPLIP, any suggestions as to what to try next would be greatly appreciated.

Regards, Colin

---

