---
title: "install rtl8812AU_8821AU_linux on ubuntu"
date: 2015-08-09
forum: Networking &amp; Wireless
---

### Post by abb3 on 2015-08-09
Hi, 
I  followed the instruction here: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)
I've been installed the driver successfully according to the system

but after I Pluged the device the USB and run:
sudo lshw -C network
I can't see any info about the wirless NIC. so what's wrong?

---

### Post by chili555 on 2015-08-10
May we have a look at:```
lsusb

```Thanks.

---

### Post by abb3 on 2015-08-15
thanks, sorry for the delay.
sudo lsusb:

Bus 001 Device 005 ID 2001:3101 D-link Corp.
Bus 001 Device 001 ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 006 ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005 ID 1d6b:0001 Linux Foundation 1.1 root hub
.
.
.

---

### Post by chili555 on 2015-08-15
rtl8812au is incorrect for this device.

I refer you to this: [https://wikidevi.com/wiki/D-Link_DWA-182_rev_A1](https://wikidevi.com/wiki/D-Link_DWA-182_rev_A1) As you see, it refers specifically to your 2001:3101 device. They say:> Probable Linux driver
noneAlso see: [http://ubuntuforums.org/showthread.php?t=2102085](http://ubuntuforums.org/showthread.php?t=2102085)> There seems to be no linux support as yet And also: [http://ubuntuforums.org/showthread.php?t=2147033](http://ubuntuforums.org/showthread.php?t=2147033)

Even the prospects for ndiswrapper are grim:> Have you had any success? I've been able to get the XP driver working on NDISWRAPPER. I can put up some instructions if you like. I am having some interesting things happen though. It works fine for a while but then appears to stop communicating. It still has an IP address and shows as connected but i can't ping the gateway or anything. I've found only a reboot fixes it. I'd be interested to see how you go.I'm sorry. I wish there was better news.

---

### Post by abb3 on 2015-08-15
oh, ok. I tried more without any success. But thank you very much!

---

