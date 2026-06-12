---
title: "Troubles with Asus N13 vA1 WiFi USB Card"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by dpak0n4ik on 2013-12-06
Hi,


Note: This is a cross post from a Debian forum as I was using Debian before. I had to ask it again since I wasn't getting any replies on my post there.


I'm having troubles with my wifi usb card. It works with open source drivers fine but I can't get speeds faster than 25mbit/s. Therefore, I downloaded rt3573sta drivers ([https://github.com/ashaffer/rt3573sta](https://github.com/ashaffer/rt3573sta)) and successfully compiled and installed them using dkms (this driver package suppose to work with 64bits OS and it has support for my WiFi card).


The problem is that after 2-3 reboots Wicd (I'm using Wicd-gtk) is unable to connect to WiFi and only shows 2 surrounding networks out of 15. I suspect that there is something wrong with the way my driver loaded onto the system. If I enable the open source drivers (unmask them in blacklist.conf) and reboot, WiFi works. I can then blacklist open source drivers and use compiled ones for 2-3 reboots, after that I no longer able to connect.


I'm using Ubuntu 12.04 64bit server edition (3.8.0-34-generic). This machine also has Windows 7 64bit (not sure if this is relevant...). 

**lsusb**
```

Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter [Ralink RT3072]

```



**lsmod | grep rt3**
```

rt3573sta             721035  1 

```


**part of kernel.log command**

```

Dec  6 12:38:18 dbserver kernel: [    8.322650] rtusb init rt2870 --->
Dec  6 12:38:18 dbserver kernel: [    8.323802] usbcore: registered new interface driver rt2870
Dec  6 12:38:18 dbserver kernel: [    9.228147] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec  6 12:38:18 dbserver kernel: [    9.228148] [drm] Driver supports precise vblank timestamp query.
Dec  6 12:39:15 dbserver kernel: [   72.958865] phy mode> Error! The chip does not support 5G band 8!
Dec  6 12:39:15 dbserver kernel: [   73.023546] <==== rt28xx_init, Status=0
Dec  6 12:39:16 dbserver kernel: [   73.290703] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 360
Dec  6 12:39:17 dbserver kernel: [   74.667979] MainVirtualIF_close 
Dec  6 12:39:17 dbserver kernel: [   74.667984] calling rt28xx_close from CMD_RTPRIV_IOCTL_VIRTUAL_INF_DOWN!
Dec  6 12:39:17 dbserver kernel: [   74.667985] ===> rt28xx_close
Dec  6 12:39:18 dbserver kernel: [   75.304615] phy mode> Error! The chip does not support 5G band 8!
Dec  6 12:39:18 dbserver kernel: [   75.370801] <==== rt28xx_init, Status=0
Dec  6 12:39:18 dbserver kernel: [   75.460128] MainVirtualIF_close 
Dec  6 12:39:18 dbserver kernel: [   75.460133] calling rt28xx_close from CMD_RTPRIV_IOCTL_VIRTUAL_INF_DOWN!
Dec  6 12:39:18 dbserver kernel: [   75.460135] ===> rt28xx_close
Dec  6 12:39:19 dbserver kernel: [   76.190492] phy mode> Error! The chip does not support 5G band 8!
Dec  6 12:39:19 dbserver kernel: [   76.255919] <==== rt28xx_init, Status=0
Dec  6 12:39:21 dbserver kernel: [   78.325234] rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8401    KeyIdx: 0
Dec  6 12:39:21 dbserver kernel: [   78.325492] RtmpIoctl_rt_ioctl_siwencodeext, 0rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8402    KeyIdx: 1
Dec  6 12:39:21 dbserver kernel: [   78.325990] RtmpIoctl_rt_ioctl_siwencodeext, 1rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8403    KeyIdx: 2
Dec  6 12:39:21 dbserver kernel: [   78.327490] RtmpIoctl_rt_ioctl_siwencodeext, 2rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8404    KeyIdx: 3
Dec  6 12:39:21 dbserver kernel: [   78.328218] RtmpIoctl_rt_ioctl_siwencodeext, 3rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8405    KeyIdx: 4
Dec  6 12:39:21 dbserver kernel: [   78.328987] RtmpIoctl_rt_ioctl_siwencodeext, 4
Dec  6 12:39:21 dbserver kernel: [   78.329366] /var/lib/dkms/rt3573sta/master/build/os/linux/../../common/cmm_asic.c:2583 assert KeyIdx < 4failed
Dec  6 12:39:21 dbserver kernel: [   78.329373] rt_ioctl_siwencodeext, alg: 0    encoding->flags: 0x8406    KeyIdx: 5
Dec  6 12:39:21 dbserver kernel: [   78.329676] RtmpIoctl_rt_ioctl_siwencodeext, 5
Dec  6 12:39:21 dbserver kernel: [   78.330115] /var/lib/dkms/rt3573sta/master/build/os/linux/../../common/cmm_asic.c:2583 assert KeyIdx < 4failed
Dec  6 12:39:21 dbserver kernel: [   78.341469] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Dec  6 12:39:23 dbserver kernel: [   80.266939] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 2450
Dec  6 12:39:23 dbserver kernel: [   80.267129] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Dec  6 12:39:25 dbserver kernel: [   82.369212] rt_ioctl_siwencodeext, alg: 3    encoding->flags: 0x401    KeyIdx: 0
Dec  6 12:39:25 dbserver kernel: [   82.372375] rt_ioctl_siwencodeext, alg: 3    encoding->flags: 0x403    KeyIdx: 2
Dec  6 12:39:26 dbserver kernel: [   83.528384] Start Seq = 00000000
Dec  6 12:49:06 dbserver kernel: [  665.120872] Start Seq = 00000000
Dec  6 12:49:50 dbserver kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec  6 12:59:00 dbserver kernel: [ 1259.382855] Start Seq = 00000000
Dec  6 13:14:17 dbserver kernel: [ 2176.863519] rt_ioctl_siwencodeext, alg: 3    encoding->flags: 0x402    KeyIdx: 1

```

Any help would be really appreciated as I'm fighting with this usb adapter or a long time...

---

### Post by praseodym on 2013-12-08
Try the driver rt5370sta, installation with dkms here:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=0b05%3A1784#Installation-ueber-DKMS](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=0b05%3A1784#Installation-ueber-DKMS)

---

### Post by dpak0n4ik on 2013-12-08
Unfortunately, I was unable to compile this driver on my current system.

---

