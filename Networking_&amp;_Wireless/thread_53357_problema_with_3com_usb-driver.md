---
title: "problema with 3com usb-driver"
date: 2005-07-31
forum: Networking &amp; Wireless
---

### Post by dabear on 2005-07-31
I'm desperate to get my wlan drivers working, but I've got some problems with the deb created with checkinstall. How do I fix this error?
```

Selecting previously deselected package usbwlandrivere1.2.0.0-ubuntu1.
(Reading database ... 124004 files and directories currently installed.)
Unpacking usbwlandrivere1.2.0.0-ubuntu1 (from .../usbwlandrivere1.2.0.0-ubuntu1_1.2.0.0-ubuntu1-1_i386.deb) ...
dpkg: error processing /root/wlanusb/linuxdrivere/usbwlandrivere1.2.0.0-ubuntu1_1.2.0.0-ubuntu1-1_i386.deb (--install):
trying to overwrite `/lib/modules/2.6.10-5-686/modules.usbmap', which is also in package linux-image-2.6.10-5-686
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/root/wlanusb/linuxdrivere/usbwlandrivere1.2.0.0-ubuntu1_1.2.0.0-ubuntu1-1_i386.deb

```


The adapters name is **3Com® OfficeConnect® Wireless 54Mbps 11g Compact USB Adapter: 3CRUSB10075 ** and the drivers can be found here: [usb-drivers](http://webprd1.3com.com/swd/jsp/user/index.jsp?id=WUSBL1)
The customized Makefile I use (just changed the kernel source to the location of my
 kernel) is attached

---

### Post by dabear on 2005-07-31
Ok, its been a while, doesn't anyone know what this means, should I just delete the "linux-image-2.6.10-5-686" from synaptic, or what?

---

