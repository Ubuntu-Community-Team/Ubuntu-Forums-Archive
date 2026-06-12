---
title: "us robotics wireless usb adaptor 5421a"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by strakaram on 2007-08-29
It seems that ndiswrapper-1.47 cannot work properly with the usr stick I have got. 
I have followed the instructions on the ndiswrapper site thoroughly but the stick does not work. 
The command "ndiswrapper -l" lists both the driver and the device present and when I "modprobe ndiswrapper" I got no error message, but the drivers for the usb stick are not loaded. 
The system log ("dmesg") shows that the ndiswrapper driver is loaded but this is not the case for the device drivers too, as it should be. 
Can anybody help please ?

---

