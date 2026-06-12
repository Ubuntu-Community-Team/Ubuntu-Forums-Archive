---
title: "RTL8812AU - Not working with 18.10"
date: 2018-11-21
forum: Networking &amp; Wireless
---

### Post by ggsinclair on 2018-11-21
Hi.

I have been using my wireless dongle with Linux for a while now and it has always been problematic, but I have always found a workaround.

I have just upgraded to 18.10 and it has stopped working again.  All of the previous fixes were from previous Kernel versions.

lsusb output:

Bus 001 Device 008: ID 0bda:b812 Realtek Semiconductor Corp. 

Does anyone have a workaround for 18.10?

Many thanks.

Gordon

---

### Post by SeijiSensei on 2018-11-21
Did you run the "Additional Drivers" app that Ubuntu provides?

---

### Post by chili555 on 2018-11-21
I believe your device in an 88x2bu device, not rtl8812au.

Reference:```

$ modinfo 88x2bu.ko | grep 812
alias:          usb:v0B05p1812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]B812[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApB812d*dc*dsc*dp*icFFiscFFipFFin*

```

Please try:```
sudo apt update
sudo apt install build-essential git
git clone https://github.com/MeissnerEffect/rtl8822bu.git
cd rtl8822bu
make
sudo make install
sudo modprobe 88x2bu
```

---

### Post by ggsinclair on 2018-11-23
Hi.

Thanks for your help.

When I run make it throws up the following error:

> "In file included from ./include/linux/list.h:9:0,
                 from ./include/linux/module.h:9,
                 from /home/gordon/rtl8822bu/include/basic_types.h:76,
                 from /home/gordon/rtl8822bu/include/drv_types.h:26,
                 from /home/gordon/rtl8822bu/core/rtw_cmd.c:17:
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
          ^~~~~~~~~~
compilation terminated.

I have had a lot of problems with this dongle so I think it is maybe time to buy something a little less problematic!

Thanks again.

Gordon

---

### Post by jeremy31 on 2018-11-23
First try ```
cd rtl8822bu
make clean
rm .cache.mk
make
sudo make install
sudo modprobe 88x2bu
```

---

### Post by SeijiSensei on 2018-11-23
Looks like you don't have the kernel headers installed.

Use "uname -r" to determine your kernel version, e.g. 4.15.0-39-generic.  Then run 
```
sudo apt install linux-headers-4.15.0-39-generic
```
with the version of the kernel you have. Then try compiling again.

Frankly, I don't know why you would upgrade to 18.10.  It will reach end of life next summer.  Most users should stick to versions with "long-term support" like 18.04.

---

### Post by jeremy31 on 2018-11-23
> **SeijiSensei said:**
> Looks like you don't have the kernel headers installed.

Use "uname -r" to determine your kernel version, e.g. 4.15.0-39-generic.  Then run 
```
sudo apt install linux-headers-4.15.0-39-generic
```
with the version of the kernel you have. Then try compiling again.

Frankly, I don't know why you would upgrade to 18.10.  It will reach end of life next summer.  Most users should stick to versions with "long-term support" like 18.04.

That is what I thought at first, but my results were similar
```
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-39-generic'
  CC [M]  /home/jeremy/Pictures/rtl8822bu/core/rtw_cmd.o
In file included from ./include/linux/list.h:9:0,
                 from ./include/linux/module.h:9,
                 from /home/jeremy/Pictures/rtl8822bu/include/basic_types.h:76,
                 from /home/jeremy/Pictures/rtl8822bu/include/drv_types.h:26,
                 from /home/jeremy/Pictures/rtl8822bu/core/rtw_cmd.c:17:
./include/linux/kernel.h:6:10: fatal error: stdarg.h: No such file or directory
 #include <stdarg.h>
```

If you get rid of .cache.mk, then it compiles nicely

---

### Post by ggsinclair on 2018-11-24
Hi.

Thanks all.

Its now working properly!

Thanks again.

Gordon

---

