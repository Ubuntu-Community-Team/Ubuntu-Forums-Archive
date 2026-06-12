---
title: "USB Sagem XG-760N (driver 'zd1211rw')"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by juannm on 2008-04-27
Hello all, I'm trying to make my wifi USB dongle work, but I have stuck on the first step :D

A search on [http://www.linuxwireless.org/en/users/Devices/USB](http://www.linuxwireless.org/en/users/Devices/USB) shows me the needed info:
```
Driver: zd1211rw
Vendor: Sagem
Product: XG76NA
USB Vendor: 079b
USB Product: 0062
```

I am using the last Ubuntu version (8.04), cleanly installed this morning. The problem is that the USB device is not recognized at all, so I have no idea about what could be done. At this moment these have been my efforts:

```
# rmmod zd1211rw && modprobe zd1211rw && dmesg | tail
[ 7815.895491] usbcore: deregistering interface driver zd1211rw
[ 7815.913911] usbcore: registered new interface driver zd1211rw
```

I unplug & plug the usb again:
```
# dmesg | tail
[ 7868.575887] usb 5-7: new high speed USB device using ehci_hcd and address 15
```

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

The weirdest thing, it doesn't even show up in lsusb:
```
# lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

Of course I have checked and it works without a problem under Windows, so the hardware is working properly. What confuses me is the fact that lsusb doesn't 'see' the device, because if it did, at least I would have a point to start trying to make the driver recognize it. 

Any help would be appreciated, thank you very much!
If I manage to make this work, I will write a report on the hardware wiki.

---

