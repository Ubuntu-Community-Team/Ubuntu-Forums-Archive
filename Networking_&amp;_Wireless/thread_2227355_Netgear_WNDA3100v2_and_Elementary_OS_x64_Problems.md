---
title: "Netgear WNDA3100v2 and Elementary OS x64 Problems"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by mbermel7 on 2014-06-01
So I've done quite a bit of reading in regards to how I should go about installing this adapter, and the consensus seems to be:
1.) Use the latest ndiswrapper utils, kernel module (dkms), and core application
2.) Use the Windows XP x64 drivers, which man be obtained by installing the drivers onto a Windows system, then extracting the folder from Program Files/yada yada

However, that hasn't worked for me. ndiswrapper -l indicates that the driver is installed and the device is present, but I am unable to use it. I've tried other drivers too, but nothing seems to work.

I was wondering if anyone had any suggestions?

Thanks

---

### Post by praseodym on 2014-06-01
Please run
```

sudo ndiswrapper -ma
```
Replug it and check
```

dmesg | grep ndis
lsmod
iwconfig
```

---

### Post by mbermel7 on 2014-06-01
Both of those commands returned no output

---

### Post by praseodym on 2014-06-02
Maybe this Win driver is not working (firmware missing?!). Try this one:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Unpack the 64bit driver into a new directory, install it via
```

gksudo ndisgtk
```
and chose the 64bit *.INF file there

---

