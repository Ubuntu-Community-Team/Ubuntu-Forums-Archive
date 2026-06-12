---
title: "rtl8811au errors on make after upgrade to 21.04"
date: 2021-06-11
forum: Networking &amp; Wireless
---

### Post by notgoingbackto_ms on 2021-06-11
I am trying to get my netgear a6100 working after upgrade to 21.04. Getting this on the make, need some help installing this again, as it was installed on 20.04 and worked. Thanks.

Leary/rtl8811au  modules
make[1]: Entering directory '/usr/src/linux-headers-5.11.0-18-generic'
  CC [M]  /home/leary/rtl8811au/core/rtw_cmd.o
In file included from /home/leary/rtl8811au/include/osdep_service.h:41,
                 from /home/leary/rtl8811au/include/drv_types.h:32,
                 from /home/leary/rtl8811au/core/rtw_cmd.c:22:
/home/leary/rtl8811au/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/leary/rtl8811au/include/osdep_service_linux.h:267:8: error: ‘_timer’ {aka ‘struct timer_list’} has no member named ‘data’
  267 |  ptimer->data = (unsigned long)cntx;
      |        ^~
/home/leary/rtl8811au/include/osdep_service_linux.h:268:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  268 |  init_timer(ptimer);
      |  ^~~~~~~~~~
      |  _init_timer
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:287: /home/leary/rtl8811au/core/rtw_cmd.o] Error 1
make[1]: *** [Makefile:1848: /home/leary/rtl8811au] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-18-generic'
make: *** [Makefile:1551: modules] Error 2
leary@ubuntu-upstairs:~/rtl8811au$

---

### Post by chili555 on 2021-06-11
Please run the terminal command:

```
lsusb
```

Is your device 0846:9052? If so, try this driver: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

Post back if you need a step-by-step.

If that is *not* your device, post it and we'll proceed.

---

### Post by notgoingbackto_ms on 2021-06-11
Yep that's it.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 003: ID 0846:9052 NetGear, Inc. A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
Bus 012 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1385:4250 Netgear, Inc WG111T
Bus 002 Device 002: ID 0d49:7310 Maxtor OneTouch 4
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0e8d:1806 MediaTek Inc. Samsung SE-208 Slim Portable DVD Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
leary@ubuntu-upstairs:~$

---

### Post by notgoingbackto_ms on 2021-06-11
That worked, more done than the other I tried, thanks.

Last bit of make and install:
 CC [M]  /home/leary/rtl8812au/hal/phydm/rtl8821a/phydm_rtl8821a.o
  CC [M]  /home/leary/rtl8812au/hal/phydm/halrf/rtl8821a/halrf_iqk_8821a_ce.o
  CC [M]  /home/leary/rtl8812au/platform/platform_ops.o
  CC [M]  /home/leary/rtl8812au/core/rtw_mp.o
  LD [M]  /home/leary/rtl8812au/88XXau.o
  MODPOST /home/leary/rtl8812au/Module.symvers
  CC [M]  /home/leary/rtl8812au/88XXau.mod.o
  LD [M]  /home/leary/rtl8812au/88XXau.ko
  BTF [M] /home/leary/rtl8812au/88XXau.ko
Skipping BTF generation for /home/leary/rtl8812au/88XXau.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-18-generic'
---------------------------------------------------------------------------
Visit [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au) for support/reporting issues
or check for newer versions (branches) of these drivers.                   
---------------------------------------------------------------------------
leary@ubuntu-upstairs:~/rtl8812au$ sudo make install
[sudo] password for leary: 
install -p -m 644 88XXau.ko  /lib/modules/5.11.0-18-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 5.11.0-18-generic
leary@ubuntu-upstairs:~/rtl8812au$

---

### Post by chili555 on 2021-06-11
After a reboot, does your wireless work?

Also, I suggest that you use the dkms process as described in the README. That way, you won't need to reinstall the driver after every kernel update.

---

### Post by notgoingbackto_ms on 2021-06-12
Yes, solved.

---

