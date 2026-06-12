---
title: "Wifi on Macbook Pro (Ubuntu 12.04 LTS)"
date: 2014-01-10
forum: Networking &amp; Wireless
---

### Post by gaf1610 on 2014-01-10
Hi Everyone,

I recently switched from Mac OS X to Ubuntu and cannot seem to connect to wifi - ethernet works though. I heard that you have to install the broadcom driver however, it won't install. I am an absolute beginner with Ubuntu so forgive me if I don't understand you reply fully.

Mainly, I want to know if this is a software fix or a hardware compatibility issue.

Thank you

---

### Post by hansdown on 2014-01-10
Welcome to the forum, gaf1610.

could you please post your hardware specs?

Thanks.

---

### Post by gaf1610 on 2014-01-11
> **hansdown said:**
> Welcome to the forum, gaf1610.

could you please post your hardware specs?

Thanks.

Thanks!

My computer is running Linux 12.04 LTS (as I said, was running OS X 10.8 before the swap.) Regarding the hardware, it has an Intel Core 2 Duo clocked at 2.66 GHz, 6 Gb's of 1067 MHz RAM and a 320 GB HDD (it is 13 inch.) The model name/version is MacBook Pro 7,1 (it is from 2010 but has been slightly updraded.)

Edit: It's 64 bit by the way.

Thank you in advance.

---

### Post by hansdown on 2014-01-11
The broadcom driver is not recommended for your macbook.

[http://askubuntu.com/questions/252958/broadcom-driver-woes](http://askubuntu.com/questions/252958/broadcom-driver-woes)

---

### Post by gaf1610 on 2014-01-12
So... How do I connect to wifi?

---

### Post by praseodym on 2014-01-12
Please open a terminal with CTRL+ALT+T and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

