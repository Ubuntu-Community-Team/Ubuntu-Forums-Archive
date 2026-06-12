---
title: "Can't get my zd1211b based USB wireless device working.  Ideas?"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Taxi on 2008-04-23
I've got a USB wireless device I'm having trouble with in Xubuntu 7.10.  It's based on the zd1211b chipset, so I believe it should be supported in the zd1211rw module, but so far I haven't been able to get any results.  The system acknowledges that the USB device has been attached and appears to recognize it correctly, but doesn't seem to know that it's a networking device or that it should be associated with the driver.  I'd appreciate any help I can get!  Here's some terminal output:

------------------------------------------------
$ lsusb
Bus 001 Device 002: ID 0cde:001a Z-Com 
Bus 001 Device 001: ID 0000:0000  
$ lsmod | grep zd1211rw
$ sudo modprobe -v zd1211rw
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko 
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko 
insmod /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko 
insmod /lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko 
$ iwconfig
lo        no wireless extensions.
 
$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
 
$ lsmod | grep zd1211rw
zd1211rw               53508  0 
ieee80211softmac       31360  1 zd1211rw
ieee80211              35656  2 zd1211rw,ieee80211softmac
usbcore               138632  3 zd1211rw,uhci_hcd
------------------------------------------------

---

### Post by kevdog on 2008-04-24
The module is loaded as per your lsmod statement, however after loading the module did you check dmesg after loading the module with the usb wireless device plugged in?

---

### Post by Taxi on 2008-04-25
Yeah, I had checked dmesg but it wasn't really giving anything useful.  No errors, no "trying to load device", or anything like that.  The good news is that it works out of the box with Hardy, which I installed yesterday.  I wish I had been able to get it running under Gutsy, because I was actually working on it for quite some time, but having it working in Hardy is probably good enough.

To give a little bit more information, I had also been taking the device to a local LUG to try to get it working.  We were mainly trying it on someone else's laptop running Fedora.  We couldn't get it going with FC6, but we did get it working after upgrading to FC8.  It didn't work in the original install, or after upgrading the kernel, but after updating some other networking-related packages it started working automatically.  So it seems like the issue is not so much a problem with the kernel or the driver, but with some other part of the equation relating to associating the USB ID with the driver with networking, etc.  Maybe we'll screw around with it more in Fedora next week and see what actually did it and how that would translate to the *buntus.

Anyway, thanks for the input!

---

