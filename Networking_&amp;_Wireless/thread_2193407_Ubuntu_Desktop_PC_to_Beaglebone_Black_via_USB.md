---
title: "Ubuntu Desktop PC to Beaglebone Black via USB"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by csnyder1 on 2013-12-12
I have installed the latest version of Ubuntu (64bit) in a VirtualBox on my pc.  As far as I can tell everything is connected and working as expected.  I connected a Beaglebone Black board to the USB port on the PC.  When I ran ifconfig, I expected to see the USB port show up as usb0, but instead only saw the Ethernet ports (2) and the loopback.  Is there something else I need to configure as I want to ssh into the Beaglebone and need to know the IP address?

---

### Post by bashiergui on 2013-12-13
Install the guest additions and set the usb port to pass through to the VM.

[https://www.virtualbox.org/manual/ch03.html#idp57413136](https://www.virtualbox.org/manual/ch03.html#idp57413136)

---

