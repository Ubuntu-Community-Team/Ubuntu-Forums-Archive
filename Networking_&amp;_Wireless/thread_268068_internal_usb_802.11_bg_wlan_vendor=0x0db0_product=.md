---
title: "internal usb 802.11 b/g wlan vendor=0x0db0 product=0x6877"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by philetusx on 2006-09-29
I recently purchased a new averatec 2260 and installed ubuntu 6.06.1 amd64 desktop.

the device manager recognizes that there is a "802.11 bg WLAN" product attached to the usb system, but does not load a driver.

lsusb shows the following (internal) usb device attached:
```
Bus 005 Device 002: ID 0db0:6877 Micro Star International
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

device manager lists the vendor as "Microstar International" and I posted to their forum asking for specs on the device here:
[http://forum.msi.com.tw/index.php?topic=101433.0](http://forum.msi.com.tw/index.php?topic=101433.0)

lshw gives the following output:
```
...
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: 802.11 bg WLAN
                   vendor: Ralink
                   physical id: 6
                   bus info: usb@5:6
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: maxpower=300mA speed=480.0MB/s
...
```
which seems to suggest that it uses the ralink chipset. I installed the rt2570 (ralink usb) driver following the instructions here:
[http://www.ubuntuforums.org/showthread.php?t=106846](http://www.ubuntuforums.org/showthread.php?t=106846)

and I am able to load the module but it doesn't seem to recognize the device, here is the output of 'lsmod | grep rt2570':
```
rt2570                214720  0
usbcore               147132  4 rt2570,ehci_hcd,uhci_hcd
```
I added the following line to /etc/modules to try to force the rt2570 module to recognize the device, but it doen't seem to be working:
```
rt2570 vendor=0x0db0 product=0x6877
```
of course, I am only guessing that the chipset is really the ralink usb.

any suggestions?

---

### Post by FRuMMaGe on 2007-06-04
same problem as you.  Please help!

---

### Post by tturrisi on 2007-06-04
all you need to know about averatecs here:
[http://ubuntuforums.org/showthread.php?t=308152](http://ubuntuforums.org/showthread.php?t=308152)

---

