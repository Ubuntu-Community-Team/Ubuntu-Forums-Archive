---
title: "Trying to Compile Driver for Panda Wifi Adapter"
date: 2019-10-20
forum: Networking &amp; Wireless
---

### Post by fahrbach on 2019-10-20
Hi, apologies if this is the wrong forum.  I'm getting the following errors when I compile for the Panda PAU05 wifi driver (why in the hell don't they just supply the driver?).  Can someone tell me what is going wrong?  I am running 16.04 LTS and using "make" command. I am by not stretch a linux pro but will understand if you tell me!  Thanks!

```
/tftpboot/os/linux/../../sta/sta_cfg.c:4941:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/tftpboot/os/linux/../../sta/sta_cfg.c:4941:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 , size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                     ^
cc1: some warnings being treated as errors
scripts/Makefile.build:330: recipe for target '/tftpboot/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/tftpboot/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1571: recipe for target '_module_/tftpboot/os/linux' failed
make[1]: *** [_module_/tftpboot/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-65-generic'
Makefile:356: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
```

---

### Post by QIII on 2019-10-20
Thread moved to Networking & Wireless.

---

### Post by Holger_Gehrke on 2019-10-20
If the driver you're trying to compile is the one provided on the [Panda wireless]("http://www.pandawireless.com/Drivers%20|%20Panda%20Wireless.html") site, then I've got good news and bad news for you. 

Bad news first: that driver is from 2012 and meant for kernel 2.4.x or 2.6.x - we are currently on 4.15.x. Not surprising this thing fails to compile, since it would try to include files from the kernel-headers ...

The good news: according to the README and comments in the code it should be a Ralink RT2870 chip, support for which is in the kernel module rt2800usb, which you've already got (it's part of the package linux-modules-extra-(append your kernel-version) which is installed by default). So in theory it should be plug and play. If it doesn't play when you plug it in, then you're either missing the firmware that should be uploaded to the adapter when it' s plugged in, which should be in the package linux-firmware (which also should be installed by default) or the manufacturer has given his adapter a new USB-ID (a number the adapter sends to the computer over USB to tell it who made it and what it is) which isn't in the database the system uses for these or there's something wrong with the adapter.

Holger

---

### Post by fahrbach on 2019-10-20
Thank you!!  I was able to stop the built-in adapter prior to boot but when I plugged in the Panda nothing happened.  Now for the record, I had plugged in the Panda before and the Ubuntu did recognize it.  When I tried to use it instead of the built in adapter it didn't work but perhaps that's because I hadn't stopped the built-in.  So perhaps the Panda is no good.

---

### Post by chili555 on 2019-10-21
Let's find out more details about the Panda. Please run and post:```
lsusb
```

---

### Post by fahrbach on 2019-10-21
Plug and play did work!  Thank you!!

---

