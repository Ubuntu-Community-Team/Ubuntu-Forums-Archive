---
title: "USB720 KPPP doesnt create dev ttyACM0"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by compdat on 2008-01-30
Using Verizon USB720.  hwinfo | grep usb  shows vendor: usb 0x1410 "Novatel Wireless Inc."  and also shows Device: ... We did modprobe usbserial vendor= ... product=... etc, but it did not create /dev/ttyACM0.  Apparently there must be a ttyACM0 dev to be able to dial out in Linux.  There is no way to configure KPPP without a device.  Could it have used a different name?  Is modprobe not way to create it?  Note, /dev/ shows hundreds of devices, but no ttyACM0 or ttyACMO.  Suse Enterprise Linux Server10 support doesn't support Verizon USB720, so we're not getting anywhere.  Surely with one of most powerful Linux systems around, there has got to be a way.  Verizon USB720 is our only option here, so without it we cannot get our Linux on the internet.  Is anyone familiar with this?
Thank you,
compdat

---

