---
title: "Ubuntu 19.04 kernel 5.0.0-15-lowlatency update rtl8812 adapter  no longer functions"
date: 2019-05-17
forum: Networking &amp; Wireless
---

### Post by kc10hydroman on 2019-05-17
After the kernel update my netis WF2190 adapter quit working.  Having this problem before reinstalling the driver has always worked.  This time I received errors when I tried to compile the driver.  Being ever resourceful, I downloaded the latest linux driver from the netis site and tried to compile that one too.  I received these errors.  Please help: 
 
/home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/osdep_service_linux.h:273:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/osdep_service_linux.h:274:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/drv_types.h:35,
                 from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/core/rtw_cmd.c:22:
/home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/wifi.h: At top level:
/home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/wifi.h:1009: warning: "IEEE80211_MAX_AMPDU_BUF" redefined
 #define IEEE80211_MAX_AMPDU_BUF 0x40
 
In file included from ./include/net/cfg80211.h:24,
                 from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/osdep_service_linux.h:87,
                 from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/osdep_service.h:41,
                 from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/include/drv_types.h:32,
                 from /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/core/rtw_cmd.c:22:
./include/linux/ieee80211.h:1444: note: this is the location of the previous definition
 #define IEEE80211_MAX_AMPDU_BUF  0x100
 
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:286: /home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108/core/rtw_cmd.o] Error 1
make[1]: *** [Makefile:1584: _module_/home/joseph/RTL8812AU_linux_v4.3.20_16317_20160108/driver/rtl8812AU_linux_v4.3.20_16317.20160108] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.0.0-15-lowlatency'
make: *** [Makefile:1656: modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg

---

### Post by chili555 on 2019-05-17
Please try:

```
sudo apt install rtl8812au-dkms
```

---

