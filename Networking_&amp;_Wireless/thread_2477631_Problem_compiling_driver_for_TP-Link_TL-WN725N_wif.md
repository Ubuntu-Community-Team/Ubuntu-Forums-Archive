---
title: "Problem compiling driver for TP-Link TL-WN725N wifi dongle"
date: 2022-08-01
forum: Networking &amp; Wireless
---

### Post by porphyry52 on 2022-08-01
On my Asus L210 running Lubuntu 20.04 linux 5.15.0-41 I use a TP-Link TL-WN725N dongle for wifi access.
 It has worked well until the most recent linux update, but with 5.15 has difficulty connecting. 
So I downloaded the only linux driver offered by Tp-link for this dongle, rtl8188EUS_linux_v5.2.2.4_25483.20171222.zip. 
The compile had errors, which I do not know how to deal with. The driver refers to linux 5.2.2.4, which I assume is earlier than 5.15. 
The compile produced the following output:

```
~/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222 $ make clean
#make -C /lib/modules/5.15.0-41-generic/build M=/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222 clean
cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
~/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222 $ makemake ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-41-generic/build M=/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-41-generic'
  CC [M]  /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/core/rtw_cmd.o
In file included from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service.h:46,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/drv_types.h:32,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/core/rtw_cmd.c:22:
/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service_linux.h:288:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  288 |  ptimer->data = (unsigned long)cntx;
      |        ^~
/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service_linux.h:289:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  289 |  init_timer(ptimer);
      |  ^~~~~~~~~~
      |  _init_timer
In file included from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/drv_types.h:35,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/core/rtw_cmd.c:22:
/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/wifi.h: At top level:
/home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/wifi.h:1012: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 1012 | #define IEEE80211_MAX_AMPDU_BUF 0x40
      | 
In file included from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service_linux.h:86,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/osdep_service.h:46,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/include/drv_types.h:32,
                 from /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1703: note: this is the location of the previous definition
 1703 | #define IEEE80211_MAX_AMPDU_BUF  0x100
      | 
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:285: /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222/core/rtw_cmd.o] Error 1
make[1]: *** [Makefile:1875: /home/q/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-41-generic'
make: *** [Makefile:1911: modules] Error 2
~/Downloads/tp-link/rtl8188EUS_linux_v5.2.2.4_25483.20171222 $ 
```

---

### Post by jeremy31 on 2022-08-01
Post results from terminal for ```
lsusb
```

---

### Post by porphyry52 on 2022-08-01
```
~ $ lsusb
Bus 002 Device 002: ID 0781:5583 SanDisk Corp. Ultra Fit
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 13d3:3529 IMC Networks Bluetooth Radio 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 13d3:5a11 IMC Networks USB2.0 VGA UVC WebCam
Bus 001 Device 007: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

