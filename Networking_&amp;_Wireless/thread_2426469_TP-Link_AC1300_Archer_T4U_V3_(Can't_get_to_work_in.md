---
title: "TP-Link AC1300 Archer T4U V3 (Can't get to work in linux)"
date: 2019-09-09
forum: Networking &amp; Wireless
---

### Post by madscintist on 2019-09-09
Hi Ubuntu guys need some help with this wireless adapter. I have searched and searched google and tried with friend to get this to work and can't seem too

If anybody has this wireless adapter and has it working please let me know or if you know how?


[LIST]
[*]**TP-Link |1300Mbps USB Wifi Adapter | Dual Band MU-MIMO Wireless Network Dongle with Foldable High Gain Antenna for PC | Works with Windows and Mac OS (Archer T4U V3**
[/LIST]
[https://www.tp-link.com/us/home-networking/usb-adapter/archer-t4u/](https://www.tp-link.com/us/home-networking/usb-adapter/archer-t4u/)


I tried getting the linux file from them and also from github and tried to complie with

[HTML]make
[/HTML]

it spits out error. here's the error

[HTML]make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.2.11-050211-generic/build M=/home/tj/Downloads/rtl8822bu modules
make[1]: Entering directory '/usr/src/linux-headers-5.2.11-050211-generic'
  CC [M]  /home/tj/Downloads/rtl8822bu/core/rtw_cmd.o
In file included from /home/tj/Downloads/rtl8822bu/include/osdep_service.h:41:0,
                 from /home/tj/Downloads/rtl8822bu/include/drv_types.h:32,
                 from /home/tj/Downloads/rtl8822bu/core/rtw_cmd.c:22:
/home/tj/Downloads/rtl8822bu/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/tj/Downloads/rtl8822bu/include/osdep_service_linux.h:257:8: error: ‘_timer {aka struct timer_list}’ has no memb
er named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/tj/Downloads/rtl8822bu/include/osdep_service_linux.h:258:2: error: implicit declaration of function ‘init_timer
’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/tj/Downloads/rtl8822bu/include/drv_types.h:35:0,
                 from /home/tj/Downloads/rtl8822bu/core/rtw_cmd.c:22:
/home/tj/Downloads/rtl8822bu/include/wifi.h: At top level:
/home/tj/Downloads/rtl8822bu/include/wifi.h:1005:0: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
  
In file included from /home/tj/Downloads/rtl8822bu/include/osdep_service_linux.h:84:0,
                 from /home/tj/Downloads/rtl8822bu/include/osdep_service.h:41,
                 from /home/tj/Downloads/rtl8822bu/include/drv_types.h:32,
                 from /home/tj/Downloads/rtl8822bu/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1441:0: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
  
cc1: some warnings being treated as errors
scripts/Makefile.build:278: recipe for target '/home/tj/Downloads/rtl8822bu/core/rtw_cmd.o' failed
make[2]: *** [/home/tj/Downloads/rtl8822bu/core/rtw_cmd.o] Error 1
Makefile:1603: recipe for target '_module_/home/tj/Downloads/rtl8822bu' failed
make[1]: *** [_module_/home/tj/Downloads/rtl8822bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.2.11-050211-generic'
Makefile:1318: recipe for target 'modules' failed
make: *** [modules] Error 2

[/HTML]



Anybody can help me install this ? Thank you

---

### Post by jeremy31 on 2019-09-10
Post results for ```
lsusb
```

---

### Post by madscintist on 2019-09-10
here you go. Thanks for reply

```

[FONT=monospace][COLOR=#000000]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 1a2c:b51f China Resource Semico Co., Ltd  
Bus 005 Device 002: ID 1532:0c00 Razer USA, Ltd  
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 152d:1561 JMicron Technology Corp. / JMicron USA Technology Corp.  
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 005: ID 2516:1011   
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 258a:1007   
Bus 003 Device 005: ID 2357:0115   
Bus 003 Device 002: ID 046d:082d Logitech, Inc. HD Pro Webcam C920
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
```

The tplink is this one
```
[FONT=monospace]Bus 003 Device 005: ID 2357:0115[/FONT]
```

---

### Post by pcfan1234 on 2019-09-10
Look here: [https://askubuntu.com/questions/1164054/cant-install-tp-link-archer-t4u-v3-driver-on-19-04/1164080](https://askubuntu.com/questions/1164054/cant-install-tp-link-archer-t4u-v3-driver-on-19-04/1164080)

---

### Post by madscintist on 2019-09-10
> **pcfan1234 said:**
> Look here: [https://askubuntu.com/questions/1164054/cant-install-tp-link-archer-t4u-v3-driver-on-19-04/1164080](https://askubuntu.com/questions/1164054/cant-install-tp-link-archer-t4u-v3-driver-on-19-04/1164080)

i tried that and gave me the error. I posted at the top

---

### Post by chili555 on 2019-09-10
This compiles on my 5.0-xx kernel. I don't know about your non-standard  5.2.11-xx. You'll have to try it and tell us: [https://github.com/jeremyb31/rtl8822bu](https://github.com/jeremyb31/rtl8822bu)

---

### Post by madscintist on 2019-09-10
> **chili555 said:**
> This compiles on my 5.0-xx kernel. I don't know about your non-standard  5.2.11-xx. You'll have to try it and tell us: [https://github.com/jeremyb31/rtl8822bu](https://github.com/jeremyb31/rtl8822bu)

I tired it @chli555 and got that error up top with 5.2 kernel? is there something i have to do extra

---

### Post by chili555 on 2019-09-10
> **madscintist said:**
> I tired it @chli555 and got that error up top with 5.2 kernel? is there something i have to do extraEither go back to a 5.0 kernel or ask @jeremy31 to try to fix it. [https://ubuntuforums.org/private.php?do=newpm&u=1924242](https://ubuntuforums.org/private.php?do=newpm&u=1924242)

---

### Post by madscintist on 2019-09-10
isn''t there way to fix it using dkms? build for newer kernel

---

### Post by jeremy31 on 2019-09-10
The source code would need to be patched to support 5.2 for even dkms to work.  Right now I don't have the time to figure out what changed in 5.2 that is causing the issues

---

### Post by madscintist on 2019-09-10
Well thank you that makes total sense to me. so if i where running Arch based distro it wouldn't work seeing how kernels update as its rolling OS. Do you know what best wirless adpater to run the newest kernel every time comes out. This my not be best adpater to use or it is if staying on stable kernel and not bleeding edge. If you know of adpater i can buy for bleeding egde kernels please let me know. thanks for your help Linux still the best to me :popcorn:

---

### Post by jeremy31 on 2019-09-10
It is likely best to stay with kernel 5.0 or older if your hardware works
I use a Edimax EW-7833UAC AC1750 using source code from github but I don't know if it would even work on 5.2 even with [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

---

### Post by madscintist on 2019-10-03
I just want to state that if anybody is looking for this to work on Kernel 5.3.2 NEW. I got it working with this [https://github.com/EntropicEffect/rtl8822bu](https://github.com/EntropicEffect/rtl8822bu)

Works with my TP-Link AC1300 Archer T4U V3.

---

