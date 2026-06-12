---
title: "Realtek USB wireless adapter"
date: 2019-04-27
forum: Networking &amp; Wireless
---

### Post by mpm1164 on 2019-04-27
Hello, I am a newbie to Ubuntu. I purchased a Realtek USB wireless adapter. The Make has repeatedly failed. I did some searching on the web and found a number of articles mentioning certain libs that need to be installed for the Make to work, which I did. The Make is still failing. I literally have zero experience building a Makefile. Below is the output of the failed Make.

```
sudo make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.0-17-generic/build M=/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.0-17-generic'
  CC [M]  /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/core/rtw_cmd.o
In file included from /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h:42:0,
                 from /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/drv_types.h:27,
                 from /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/core/rtw_cmd.c:17:
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service_linux.h: In function &#8216;_init_timer&#8217;:
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service_linux.h:282:8: error: &#8216;_timer {aka struct timer_list}&#8217; has no member named &#8216;data&#8217;
  ptimer->data = (unsigned long)cntx;
        ^~
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service_linux.h:283:2: error: implicit declaration of function &#8216;init_timer&#8217;; did you mean &#8216;_init_timer&#8217;? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/drv_types.h:27:0,
                 from /home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/core/rtw_cmd.c:17:
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h:355:2: error: implicit declaration of function &#8216;allow_signal&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h:392:6: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
  if (signal_pending(current))
      ^~~~~~~~~~~~~~
      timer_pending
/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/include/osdep_service.h:393:3: error: implicit declaration of function &#8216;flush_signals&#8217;; did you mean &#8216;do_signal&#8217;? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
cc1: some warnings being treated as errors
scripts/Makefile.build:325: recipe for target '/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/core/rtw_cmd.o' failed
make[2]: *** [/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/core/rtw_cmd.o] Error 1
Makefile:1534: recipe for target '_module_/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044' failed
make[1]: *** [_module_/home/mpm1164/RTL88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044/driver/rtl88x2BU_WiFi_linux_v5.2.4.4_25643.20171212_COEX20171012-5044] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.18.0-17-generic'
Makefile:1795: recipe for target 'modules' failed
make: *** [modules] Error 2
```

---

### Post by jeremy31 on 2019-04-27
Try ```
sudo apt install git dkms
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git
cd rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
```
Reboot, please check BIOS for Secure Boot setting as it will need to be disabled

Thread moved to Networking & Wireless

---

### Post by praseodym on 2019-04-28
Sure, it is this driver? Please show
```

lsusb
```

---

