---
title: "[SOLVED] IPW2200 firmware"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by Nirva on 2006-11-05
Hay,

I am trying to install IPW2200 v1.2 because I want to be able to use monitor mode.  I followed those manuals : 

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)
[http://doc.gwos.org/index.php/Install_ipw2200](http://doc.gwos.org/index.php/Install_ipw2200)

The last step in both the manuals is copying the firmware to /usr/lib/hotplug/firmware

But in Ubuntu 6.10 this directory doesn't exist anymore.  Does anyone knows where I should copy the firmware to?

Thanks

---

### Post by wieman01 on 2006-11-05
This is the guide I used for Dapper:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200")

---

### Post by tdn on 2007-10-22
How do I enable ipw2200 monitor mode in Feisty?

---

### Post by wieman01 on 2007-10-22
> **tdn said:**
> How do I enable ipw2200 monitor mode in Feisty?
Start up airodump-ng and it should work with no further input. It should start up automatically.

---

### Post by tdn on 2007-10-23
Ok. Thanks.

---

### Post by Nirva on 2007-11-12
Hay,

I followed this guide 

[http://ubuntuforums.org/showthread.php?t=501148&highlight=crack+wep]("http://ubuntuforums.org/showthread.php?t=501148&highlight=crack+wep")

but with a little changes : 

- Because i have kernel 2.6.22-14, ieee 1.2.17 and ipw2200 1.2.1 didn't compiled, so I had to use
IEEE 1.2.18 and ipw2200 1.2.2.
I found the patches here : 
[http://ubuntuforums.org/showthread.php?p=3737266]("http://ubuntuforums.org/showthread.php?p=3737266")

But I had to edit the patches because the top lines where as following :

```
diff -ur ipw2200-1.2.1/ipw2200.c ipw2200-1.2.1-inject/ipw2200.c
--- ipw2200-1.2.1/ipw2200.c	2006-08-21 04:38:32.000000000 +0200
+++ ipw2200-1.2.1-inject/ipw2200.c	2006-08-23 14:20:31.000000000 +0200
```

So I changed every 1.2.1 in 1.2.2
This is one of the parts I am unsure about, because I did it myself and it wasn't mentioned in any howto I found.

Anyway, I did so, and continued with the HOWTO.

Everything went fine untill : 

```

sudo modprobe ipw2200 rtap_iface=1
FATAL: Error inserting ipw2200 (/lib/modules/2.6.22-14-386/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

filip@filip:~$ dmesg | grep ipw2200
[   26.564000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[   26.564000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.564000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.248000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[  182.876000] ipw2200: Unknown parameter `rtap_iface'


```

Any help would be very very welcome

---

### Post by Nirva on 2007-11-13
It's OK, I solved it myself.

I had to edit the makefile  as mentioned in this topic : [http://ubuntuforums.org/showthread.php?p=2576816#post2576816](http://ubuntuforums.org/showthread.php?p=2576816#post2576816)

---

