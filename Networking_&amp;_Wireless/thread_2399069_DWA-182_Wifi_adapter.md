---
title: "DWA-182 Wifi adapter"
date: 2018-08-21
forum: Networking &amp; Wireless
---

### Post by dorforer on 2018-08-21
Hi. I've recenly purchase DWA-182 Wifi adapter and tried to install its drivers for awhile now.
I've downloaded the driver from D-link site and went through all the post from the forum and nothing succeeded.
My Linux machine details are:
Linux X3399 4.4.52 #2 SMP PREEMPT Sun Jun 24 08:48:39 IDT 2018 aarch64 aarch64 aarch64 GNU/Linux
When I try to to install the driver I get this:
make[1]: *** /lib/modules/4.4.52/build: No such file or directory. &nbsp;Stop.
Makefile:1350: recipe for target 'modules' failed</div><div>make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
####################################################################################################
And when I try to install those headers I get:
Reading package lists... Done
Building dependency tree &nbsp; &nbsp; &nbsp;&nbsp;
Reading state information... Done
E: Unable to locate package linux-headers-4.4.52
E: Couldn't find any package by glob 'linux-headers-4.4.52'
E: Couldn't find any package by regex 'linux-headers-4.4.52'

Thanks.

---

### Post by chili555 on 2018-08-21
Is this an official Ubuntu version? Please show us:```
lsb_release -a
```

---

### Post by dorforer on 2018-10-11
Here are the results:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial


I've now tried to install some generic headers, but when I try to install the drivers of some other usb wifi sticks I get the same errors.

It seems it may be some modified kernel, but maybe some kind of generic headers might work..

Any help?

---

### Post by chili555 on 2018-10-11
> It seems it may be some modified kernel,Yes, indeed. Only you or whoever sold you the computer knows where the kernel came from. Usually, there are accompanying header packages availble there, too.> maybe some kind of generic headers might work..Not that I'm aware of. In every case I'm aware of, in order to compile a driver or other package against kernel version 4.5.6-78-xy, you need the exact matching header version, i.e. 4.5.6-78-xy. 

Is there any reason that you can't or won't install a mainline Ubuntu kernel version?

**EDIT**: > Linux X3399 4.4.52 Is this a specialized kernel to run one of these or similar? [https://www.amazon.com/Six-Core-Performance-Platform-Android7-1-development/dp/B06ZXX1WPK](https://www.amazon.com/Six-Core-Performance-Platform-Android7-1-development/dp/B06ZXX1WPK)

We still need headers.

---

