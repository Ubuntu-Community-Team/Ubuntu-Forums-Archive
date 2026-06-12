---
title: "ADDON AWU680 drivers"
date: 2018-02-11
forum: Networking &amp; Wireless
---

### Post by 700 on 2018-02-11
Hi,

I try to install drivers for Addon AWU680 Wi-Fi USB Adapter on Ubuntu 16.04 LTS and it looks like their instructions contain different file names what makes instructions not clear to understand.
All necessary drivers and manuals are available on the producers website, here:
[http://www.addon-tech.com/new_/down/html/?147.html](http://www.addon-tech.com/new_/down/html/?147.html)

BTW: I'm not able to use the CD attached to this product.

---

### Post by jeremy31 on 2018-02-11
*Thread moved to **Networking & Wireless**.*
Please post results from terminal for ```
lsusb
```

---

### Post by 700 on 2018-02-11
> ~$ lsusb
Returns:
> Bus 001 Device 005: ID 0bda:a811 Realtek Semiconductor Corp. 

---

### Post by jeremy31 on 2018-02-11
To get that one going
```
sudo apt-get install git build-essential dkms
git clone https://github.com/gnab/rtl8812au.git
sudo dkms add ./rtl8812au
sudo dkms install -m 8812au -v 4.2.2
```
Reboot

---

### Post by 700 on 2018-02-11
&#10004; It works, thank you :)

---

### Post by 700 on 2018-07-21
Same hardware, but today it doesn't work.  
This:
> [COLOR=#000000][FONT=&amp]sudo dkms install -m 8812au -v 4.2.2[/FONT][/COLOR]
returns:
> (bad exit status: 2)ERROR (dkms apport): binary package for 8812au: 4.2.2 not found
Error! Bad return status for module build on kernel: 4.15.0-29-generic (i686)
Consult /var/lib/dkms/8812au/4.2.2/build/make.log for more information.
And make.log returns:
> DKMS make.log for 8812au-4.2.2 for kernel 4.15.0-29-generic (i686)Sat 21 Jul 20:41:45 CEST 2018
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/4.15.0-29-generic/build M=/var/lib/dkms/8812au/4.2.2/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-29-generic'
  CC [M]  /var/lib/dkms/8812au/4.2.2/build/core/rtw_cmd.o
In file included from /var/lib/dkms/8812au/4.2.2/build/include/osdep_service.h:41:0,
                 from /var/lib/dkms/8812au/4.2.2/build/include/drv_types.h:32,
                 from /var/lib/dkms/8812au/4.2.2/build/core/rtw_cmd.c:22:
/var/lib/dkms/8812au/4.2.2/build/include/osdep_service_linux.h: In function ‘_init_timer’:
/var/lib/dkms/8812au/4.2.2/build/include/osdep_service_linux.h:257:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^
/var/lib/dkms/8812au/4.2.2/build/include/osdep_service_linux.h:258:2: error: implicit declaration of function ‘init_timer’ [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/8812au/4.2.2/build/core/rtw_cmd.o' failed
make[2]: *** [/var/lib/dkms/8812au/4.2.2/build/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/var/lib/dkms/8812au/4.2.2/build' failed
make[1]: *** [_module_/var/lib/dkms/8812au/4.2.2/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-29-generic'
Makefile:1052: recipe for target 'modules' failed
make: *** [modules] Error 2

---

### Post by chili555 on 2018-07-21
Please try:```
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
sudo modprobe rtl8812au
```You should be all set.

---

### Post by 700 on 2018-07-23
[COLOR=#000000]&#10004; I am all set, thank you [/COLOR]:smile:

---

### Post by chili555 on 2018-07-23
Glad it's working. Please use thread tools at the top of the thread to mark Solved. The searchers will appreciate it.

---

