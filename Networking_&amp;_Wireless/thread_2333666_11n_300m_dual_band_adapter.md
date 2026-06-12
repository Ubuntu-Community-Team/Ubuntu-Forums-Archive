---
title: "11n 300m dual band adapter"
date: 2016-08-11
forum: Networking &amp; Wireless
---

### Post by jtmedin on 2016-08-11
got a usb 2 dongle to do my wifi. Loaded the driver for windows & that works ok. 
Now the driver for linux is another problem. Would like some novice advice on generating the driver for ubuntu. 
Looked @ the configuration & noticed the changes they recommended, now there is the 'make'. Used to do things like that with unix. However, its been 20 years +/- so now how do i proceed? TIA

---

### Post by chili555 on 2016-08-12
It is quite likely that the driver for Linux on the install CD that came with the device is too old. As well, these are usually one-size-usually-maybe-fits-all packages.> Would like some novice advice on generating the driver for ubuntu. I'll describe my process which you or anyone can follow. If, at any time, you get stuck, post back and I'll be very happy to help.

First, the device ID is the key to everything in Linux wireless. For USB devices, you can find it with a terminal command:```
lsusb
```Here is an example output:```
$ lsusb
Bus 002 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 005: ID 045e:0719 Microsoft Corp. Xbox 360 Wireless Adapter
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID [COLOR="#FF0000"]2001:3c15[/COLOR] **D-Link Corp. DWA-140 RangeBooster N Adapter(rev.B3) [Ralink RT5372]**
Bus 001 Device 003: ID 13fd:2040 Initio Corporation 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I've highlighted the device ID; in this example, 2001:3c15.

Next, Google the device ID and see that there are many posts as to the correct driver. I particularly favor posts from this forum and askubuntu.com. Look for recent [SOLVED] and you'll probably find the answer. By recent, I mean that whatever the answer was more than 2-3 years ago is probably not how we do things today. As well, the way those crazy kids do things in Arch or Fedora or PCLinuxOS is not how we do things!

Let us know how its going and feel free to post back if you need a helping hand.

---

