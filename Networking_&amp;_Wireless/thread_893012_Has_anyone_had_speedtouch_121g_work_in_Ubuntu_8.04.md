---
title: "Has anyone had speedtouch 121g work in Ubuntu 8.04"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Mr. Qualm on 2008-08-17
I thought I'd make a new thread as my last one got completely ignored. I'm sincerely losing any patience I had with Linux. I did have the sp121g working in 7.10 and in 8.04 - NOTHING. I really don't want to go back to Windows as apart from this one (significant) problem I love the distro. Can someone either offer me some remedy for my problem or recommend to me a Linux distro that will allow the Speedtouch 121g to function correctly?

Thanks in advance.

---

### Post by Mr. Qualm on 2008-08-17
Ok, I think I've narrowed the problem down to the modprobe command.

****@ubuntu:~/Installer/Driver$ sudo ndiswrapper -i BT4501G.inf
[sudo] password for kristofer: 
installing bt4501g ...
****@ubuntu:~/Installer/Driver$ ndiswrapper -l
bt4501g : driver installed
	device (06B9:0121) present

****@ubuntu:~/Installer/Driver$ **sudo modprobe ndiswrapper**
****@ubuntu:~/Installer/Driver$ sudo dmesg | tail
[  725.967449] ndiswrapper (NdisWriteErrorLogEntry:191): log: C000138A, count: 3, return_address: e0e0cfac
[  725.967459] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xc0000001
[  725.967462] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x6d695442
[  725.967465] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x37
[  736.064404] ndiswrapper (mp_init:216): couldn't initialize device: C0010006
[  736.064418] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[  736.064433] ndiswrapper (mp_halt:259): device ddd2e480 is not initialized - not halting
[  736.064436] ndiswrapper: device eth%d removed
[  736.064461] ndiswrapper: probe of 4-2:1.0 failed with error -22
[  736.064481] usbcore: registered new interface driver ndiswrapper

kristofer@ubuntu:~/Installer/Driver$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Does anyone know of why this might be happening??

---

### Post by jstoffels on 2009-06-01
Hi Mr.Qualm,
Experience with the 121g and ndiswrapper has shown me that you can get it to work, but Ubuntu may crash up to the point you need to reinstall.
As 121g does not come with Linux native drivers, I guessed that the only way around is to use another USB dongle. I now use the Linksys WUSB54GC, which indeed does not require ndiswrapper or indeed any other extra installation. This seems to work OK.
Before that I used Netgear XE102 power line connection, which gives you a 13.5Mbps or so ethernet connection via the mains powerline.
I finished trying to use 121g as this appears to be a very frustrating waste of time.
Hope this helps!

---

