---
title: "Ubuntu 8.10 Webcam help!"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by wadi5636 on 2009-03-23
I have a creative PD0040 webcam that just wont work on Ubuntu!
The drivers out of the box wont work and I tried ov51x and still unsuccessful.

This is my dmesg:

13.261951] Linux video capture interface: v2.00
[ 13.448568] ov51x_jpeg: USB OV518 video device found
[ 13.450803] ov51x_jpeg: Device revision 9
[ 13.462880] ov51x_jpeg: Compression required with OV518…enabling
[ 13.482770] input: PC Speaker as /devices/platform/pcspkr/input/input5
[ 13.539661] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 13.542369] NVRM: loading NVIDIA Linux x86 Kernel Module 96.43.09 Mon Oct 27 14:23:30 PST 2008
[ 13.606260] input: GenPS/2 Genius Mouse as /devices/platform/i8042/serio1/input/input6
[ 13.614882] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 13.615057] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[ 13.905235] phy0: Selected rate control algorithm ‘pid’
[ 14.126533] Registered led device: rt2500usb-phy0:radio
[ 15.616561] ov51x_jpeg: Sensor is an OV66308AE
[ 15.991834] ov51x_jpeg: Device at usb-0000:00:10.1-1 registered to minor 0
[ 15.991893] usbcore: registered new interface driver ov51x
[ 15.991929] usbcore: registered new interface driver rt2500usb
[ 15.992628] ov51x_jpeg: 1.5.9 : ov51x USB Camera Driver
[ 17.151656] lp: driver loaded but no devices found

And my lusb:

Bus 004 Device 003: ID 13b1:000d Linksys WUSB54G Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Please help!

---

### Post by picturefreedom on 2009-03-23
what ubuntu version do you run?

---

### Post by wadi5636 on 2009-03-23
From the help file states as Intrepid Ibex version 8.10

---

### Post by aikiwolfie on 2009-03-23
Have you tried installing Cheese? It's the default Gnome web cam app.

---

### Post by wadi5636 on 2009-03-23
Cheese reports with no camera found.:(

---

### Post by aikiwolfie on 2009-03-23
Seems like this has been an issue for a while. This launchpad bug report provides a possible solution. But it requires a bit of work.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/37739]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/37739")

---

