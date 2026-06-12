---
title: "Issue Installing Edimax N150"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by ash25 on 2016-06-23
Hi, Linux newbie here...

Purchased the Edimax N150, extracted the relevant files and attempted to run install.sh, however it just throws this back at me:

```
cc1: some warnings being treated as errors
scripts/Makefile.build:258: recipe for target '/home/notfreshprince/Downloads/Software/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o' failed
make[2]: *** [/home/notfreshprince/Downloads/Software/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o] Error 1
Makefile:1402: recipe for target '_module_/home/notfreshprince/Downloads/Software/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911' failed
make[1]: *** [_module_/home/notfreshprince/Downloads/Software/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-24-generic'
Makefile:584: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

I've looked through countless articles on how to fix it, but I keep getting the same error.
Thanks!

---

### Post by QIII on 2016-06-23
Hello!

Many Edimax products "just work" with Linux, so I would test that before trying to compile the driver from source.

Let us know what happens.

---

### Post by ash25 on 2016-06-23
It doesn't appear as a device when I attempt to select it in the bar at the top, however it is recognised when I use the lsusb command:
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 010: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by kurt18947 on 2016-06-24
Here is a fix that seems to be working. Different brand device but same chipset:

[http://ubuntuforums.org/showthread.php?t=2328635](http://ubuntuforums.org/showthread.php?t=2328635)

---

