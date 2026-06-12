---
title: "webcam not working in ubuntu 10.10"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by mayank4j on 2010-10-05
Unable to use inbuilt webcam after i installed ubuntu 10.10.

Cheese hangs up.
gstreamer pops up Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'

The output of lsusb is  

Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I am clueless pls help!!

---

### Post by mayank4j on 2010-10-05
stumbled on the script...[http://ubuntuforums.org/showthread.php?t=1479638](http://ubuntuforums.org/showthread.php?t=1479638)

			 				#!/bin/sh

# A script to re-enable OmniVision OV2640 Webcam

# Unload the modules first
rmmod uvcvideo gspca_ov519 gspca_main vloopback videodev v4l1_compat v4l2_common

# Reload the required modules
modprobe gspca_ov519
modprobe v4l1_compat
modprobe v4l2_common
modprobe uvcvideo

# Exit

exit 0 			 		


How can i make sure that it automatically executes itself once i login ..?
or if any driver update is available with which i could avoid this reloading of kernel module please share..

Thanks

---

### Post by svega85 on 2010-10-17
> **mayank4j said:**
> stumbled on the script...[http://ubuntuforums.org/showthread.php?t=1479638](http://ubuntuforums.org/showthread.php?t=1479638)

			 				#!/bin/sh

# A script to re-enable OmniVision OV2640 Webcam

# Unload the modules first
rmmod uvcvideo gspca_ov519 gspca_main vloopback videodev v4l1_compat v4l2_common

# Reload the required modules
modprobe gspca_ov519
modprobe v4l1_compat
modprobe v4l2_common
modprobe uvcvideo

# Exit

exit 0 			 		


How can i make sure that it automatically executes itself once i login ..?
or if any driver update is available with which i could avoid this reloading of kernel module please share..

Thanks
go to system > Preferences > Startup Applications then click the add button and for name type "uvc script", then for command type "gksudo rmmod uvcvideo && gksudo modprobe uvcvideo" that should fix it

---

