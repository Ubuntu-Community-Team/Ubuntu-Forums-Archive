---
title: "Belkin BCM4323 050d:615a USB wifi not detected"
date: 2017-04-01
forum: Networking &amp; Wireless
---

### Post by rex1232 on 2017-04-01
Hi! First post. Tried countless ways/examples but inability to connect wi-fi persists. Did full Ubuntu install (16.04 Xenial... impressed live usb saved other dying pc’s data, love interface open sourced nature etc). Wifi device worked running on live USB, and on PC before clean full install.

Device: Belkin BCM4323 050d:615a (USB wifi, F9L1101v1). Tried many things, including Broadcom bcm43xx (although device 4323 not mentioned).  Currently using bcmwlhigh5.inf and .sys files from original WindowsXP driver .exe file (device listed as working on ndiswrapper wiki), among many tried.

To help others... Good starting points for other noobs to linux like me:

Good guide/intro to understanding troubleshooting ndiswrapper:
[https://ubuntuforums.org/showthread.php?t=885847](https://ubuntuforums.org/showthread.php?t=885847)

definitive Broadcom guide:
[https://ubuntuforums.org/showthread.php?t=1368699](https://ubuntuforums.org/showthread.php?t=1368699)

driver bcm43xx specific:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

ndiswrapper wiki:
[http://ndiswrapper.sourceforge.net/wiki/index.php/Belkin_F9L1101v1](http://ndiswrapper.sourceforge.net/wiki/index.php/Belkin_F9L1101v1)

Don't see this model yet listed:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB)

Not sure where going wrong. Thanks for any help I'm not sure what to do

My system info:
[http://paste.ubuntu.com/24296168/](http://paste.ubuntu.com/24296168/)

---

### Post by jeremy31 on 2017-04-02
Strange, post results for ```
dmesg | grep ndis
```

---

### Post by rex1232 on 2017-04-02
fyr@oasis:~$ dmesg | grep ndis
[   40.404568] ndiswrapper: loading out-of-tree module taints kernel.
[   40.404790] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[   40.404805] ndiswrapper: module license taints kernel.
[   40.405967] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   41.063144] Modules linked in: ndiswrapper(OE+) parport_pc ppdev lp parport autofs4 algif_skcipher af_alg dm_crypt uas usb_storage hid_microsoft hid_generic e1000e i915 usbhid psmouse hid pata_acpi video floppy i2c_algo_bit drm_kms_helper syscopyarea ptp sysfillrect sysimgblt pps_core fb_sys_fops drm fjes
[   41.063492] CPU: 0 PID: 412 Comm: loadndisdriver Tainted: P           OE   4.8.0-45-generic #48~16.04.1-Ubuntu
[   41.064335]  [<f86935e7>] ? wrapper_ioctl+0x947/0xbc0 [ndiswrapper]
[   41.064638]  [<f8692ca0>] ? unload_wrap_driver+0x140/0x140 [ndiswrapper]
[   41.081341] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[   41.081390] usbcore: registered new interface driver ndiswrapper


Thanks for help! BTW this was with bcmn43xx32.sys and bcmn43xx32.inf loaded in NDISwrapper

---

### Post by jeremy31 on 2017-04-02
Lets see ```
dpkg -l | grep ndis; ndiswrapper -l
```

---

### Post by rex1232 on 2017-04-02
fyr@oasis:~$ dpkg -l | grep ndis
ii  ndisgtk                                   0.8.5-1ubuntu1                                i386         graphical frontend for ndiswrapper (installation of Windows WiFi drivers)
ii  ndiswrapper                               1.60-3~ubuntu16.04.1                          i386         Userspace utilities for the ndiswrapper Linux kernel module
ii  ndiswrapper-dkms                          1.60-3~ubuntu16.04.1                          all          Source for the ndiswrapper Linux kernel module (DKMS)
ii  ndiswrapper-source                        1.60-3~ubuntu16.04.1                          all          Source for the ndiswrapper Linux kernel module
fyr@oasis:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (050D:615A) present
fyr@oasis:~$

---

### Post by jeremy31 on 2017-04-02
Did you get the windows driver from [http://askubuntu.com/a/557042/300665](http://askubuntu.com/a/557042/300665)

---

### Post by rex1232 on 2017-04-02
Not sure, I've tried so many over days lol, but love ubuntu too much to give up
wouldn't mind re download/install to be sure.

in above link i scroll down and see:
 [URL="https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip"]https://dl.dropboxusercontent.com/u/58267392/Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip

[/URL]but "404 file not found"

---

### Post by rex1232 on 2017-04-02
i believe it was from here:
[https://ubuntuforums.org/showthread.php?t=2052594](https://ubuntuforums.org/showthread.php?t=2052594)

---

### Post by rex1232 on 2017-04-02
I might have been following your link as guide, then searched for same driver elsewhere since dead link. Did I pick the wrong one? 
(Same driver name: Broadcom_bcm43xx_USB_32_64bit_v2_amended.zip)
Custom amendments perhaps?
I&#8217;m not sure what driver I should use

---

### Post by jeremy31 on 2017-04-02
I am sure it was the same file from chili555 and it worked then so it must be an issue with ndiswrapper.  The easiest way to fix is to get a TP-Link TL-WN722N 150 Mbps wireless adapter as they work using the modules that are part of the kernel

Anything that needs ndiswrapper never seems to work as well as a device that is supported by the kernel

---

