---
title: "How do I install the netgear wireless usb driver from A flashdrive?"
date: 2015-06-30
forum: Networking &amp; Wireless
---

### Post by kylesmail80 on 2015-06-30
I just installed ubuntu 14.04 on my main desktop and have already encountered a problem. My netgear wireless usb has no driver and I lost the install disc. Is it possible to download the driver file onto a flashdrive and bring it to the desktop? If so, how? Please keep in mind I'm still relativley new to linux so you may have to simplify things for me. 

EDIT: I tried following this thread: [http://ubuntuforums.org/showthread.php?t=2221251&page=3](http://ubuntuforums.org/showthread.php?t=2221251&page=3) and i downloaded the file provided in the thread: [http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz) but after reading the thread i realize i need the "ndiswrapper" thingy to install the driver.

EDIT 2: this is the result i got from using "lsusb"
```
 NetGear , Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323] 
```

when i tried ```
 sudo lshw -C network 
``` the result mentioned nothing about my wireless usb and only mentioned my ethernet in my pci slot, and ethernet isn't excactly an option for me (otherwise I wouldn't be posting here)

---

### Post by Bucky Ball on 2015-06-30
Are you sure you need to? Plug in the USB, open a terminal and copy/paste this:

```
sudo lshw -C network
```

Also, post us the results of this:

```
lsusb
```

Ubuntu is not like Windows in that a lot of the drivers for wireless and graphics are already in the kernel, you don't need to install. Have you tried just plugging the device in? Thanks.

---

### Post by kylesmail80 on 2015-06-30
I'll try lsusb tomorrow when I'm home. I've had my USB plugged in the entire time and I've gotten no wireless options.

---

### Post by kylesmail80 on 2015-06-30
I just did lsusb and I assume this is the wireless [code] NetGear , Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323] [code/]

---

### Post by lukes2 on 2015-08-02
Has this been solved yet? I'm having this exact same problem.

When I do lsusb:
Bus 001 Device 009: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

When I do the "sudeo lshw -C network":
PCI (sysfs)

Please help someone. Thanks!!!

Oh yea, the desktop has no internet, and I can only do stuff via a thumbdrive.

---

