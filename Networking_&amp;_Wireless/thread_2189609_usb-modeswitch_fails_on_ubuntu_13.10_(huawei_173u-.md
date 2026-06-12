---
title: "usb-modeswitch fails on ubuntu 13.10 (huawei 173u-2)"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by czwarta30 on 2013-11-23
Hi,
I have fresh ubuntu 13.10. On my lapop with older suse linux I use huawei 173 and it works with modeswitch.
 When I plug modem to the other laptop, the one with ubuntu, nothing happens.
lsusb returns:

Bus 003 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)

and modems is in storage mode.

Manual commands also don't work:
 sudo usb_modeswitch -W -c 12d1:1446

[COLOR=#008080]Read config file: 12d1:1446

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.0.1 (C) Josua Dietze 2013
 * Based on libusb1/libusbx

 ! PLEASE REPORT NEW CONFIGURATIONS !

TargetVendor=   0x12d1
TargetProductList="1001,1406,140b,140c,1412,141b,1432,1433,1436,14ac,1506,150c,1511"
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
NeedResponse=0

InquireDevice enabled (default)

No default vendor/product ID given. Abort
[/COLOR]
and the same command with my suse configuration file:

[COLOR=#008080]Read config file: 12d1:1446

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 2.0.1 (C) Josua Dietze 2013
 * Based on libusb1/libusbx

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x12d1
DefaultProduct= 0x1446
TargetVendor=   0x12d1
TargetProductList="1001,1406,140b,140c,1412,141b,1433,14ac,1506,1436"
MessageContent="55534243123456780000000000000011060000000100000000000000000000"
NeedResponse=0

InquireDevice enabled (default)
Success check enabled, max. wait time 20 seconds

Look for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 No devices in target mode or class found
Look for default devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
   product ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Found devices in default mode (1)
Access device 007 on bus 003
Get the current device configuration ...
 OK, got current device configuration (1)
Use interface number 0
Use endpoints 0x01 (out) and 0x81 (in)
Inquire device details; driver will be detached ...
Looking for active driver ...
 No active driver found. Detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Set up interface 0
Use endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Reset response endpoint 0x81
Reset message endpoint 0x01
 Device is gone, skip any further commands

Check for mode switch (max. 20 times, once per second) ...
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 Search for target devices ...
  found USB ID 8087:8000
  found USB ID 1d6b:0002
  found USB ID 8087:8008
  found USB ID 1d6b:0002
  found USB ID 1d6b:0003
  found USB ID 8087:07dc
  found USB ID 12d1:1446
   vendor ID matched
  found USB ID 046d:c045
  found USB ID 13d3:5170
  found USB ID 1d6b:0002
 No new devices in target mode or class found

Mode switch has failed. Bye!
[/COLOR]
Anyone knows how to make it works?

---

### Post by varunendra on 2013-11-26
Welcome to the forums czwarta30 !

Not sure why the command failed, but try this-
```
sudo usb_modeswitch -v 0x12d1 -p 0x1446 -M "55534243123456780000000000000011062000000100000000000000000000"
```
Does it work? If yes, you can write a udev rule to make it run automatically whenever the modem is plugged in.

---

### Post by Bucky Ball on 2013-11-26
*Thread moved to **Networking & Wireless**.*

---

