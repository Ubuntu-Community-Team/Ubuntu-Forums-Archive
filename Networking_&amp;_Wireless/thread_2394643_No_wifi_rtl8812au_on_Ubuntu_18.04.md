---
title: "No wifi rtl8812au on Ubuntu 18.04"
date: 2018-06-19
forum: Networking &amp; Wireless
---

### Post by jcasasruiz on 2018-06-19
Hi!
I've installed Ubuntu 18.04 after several years with 16.04.
I've got a Wifi USB with chip Realtek rtl8812au that I can't use now. 
I try this tutorial: [https://ubuntuforums.org/showthread.php?t=2368840&highlight=8812](https://ubuntuforums.org/showthread.php?t=2368840&highlight=8812)
sudo apt purge rtl8812au-dkms
sudo apt install git
git clone [https://github.com/gnab/rtl8812au.git](https://github.com/gnab/rtl8812au.git)
sudo cp -r rtl8812au  /usr/src/rtl8812au-4.2.2
sudo dkms add -m rtl8812au -v 4.2.2
sudo dkms build -m rtl8812au -v 4.2.2
sudo dkms install -m rtl8812au -v 4.2.2

but I only have this message error:
Error! Bad return status for module build on kernel: 4.15.0-23-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.2.2/build/make.log for more information.

In the file appear this message:

DKMS make.log for rtl8812au-4.2.2 for kernel 4.15.0-23-generic (x86_64)
mar jun 19 17:24:20 CEST 2018
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-23-generic/build M=/var/lib/dkms/rtl8812au/4.2.2/build  modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /var/lib/dkms/rtl8812au/4.2.2/build/core/rtw_cmd.o
In file included from /var/lib/dkms/rtl8812au/4.2.2/build/include/osdep_service.h:41:0,
                 from /var/lib/dkms/rtl8812au/4.2.2/build/include/drv_types.h:32,
                 from /var/lib/dkms/rtl8812au/4.2.2/build/core/rtw_cmd.c:22:
/var/lib/dkms/rtl8812au/4.2.2/build/include/osdep_service_linux.h: In function ‘_init_timer’:
/var/lib/dkms/rtl8812au/4.2.2/build/include/osdep_service_linux.h:257:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/var/lib/dkms/rtl8812au/4.2.2/build/include/osdep_service_linux.h:258:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/var/lib/dkms/rtl8812au/4.2.2/build/core/rtw_cmd.o' failed
make[2]: *** [/var/lib/dkms/rtl8812au/4.2.2/build/core/rtw_cmd.o] Error 1
Makefile:1552: recipe for target '_module_/var/lib/dkms/rtl8812au/4.2.2/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8812au/4.2.2/build] Error 2
make[1]: se sale del directorio '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:1052: recipe for target 'modules' failed
make: *** [modules] Error 2

I also try another solutions but failed. Any suggestion?

Thanks!

---

### Post by chili555 on 2018-06-19
Version 4.2.2 of the driver doesn't compile correctly on 18.04. Try this instead: [https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927](https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927)

You can safely skip these steps:```
sudo dkms remove rtl8812au/5.2.9 --all
sudo rm /usr/src/rtl8812au-5.2.9
```

---

### Post by jcasasruiz on 2018-06-20
> **chili555 said:**
> Version 4.2.2 of the driver doesn't compile correctly on 18.04. Try this instead: [https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927](https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927)

You can safely skip these steps:```
sudo dkms remove rtl8812au/5.2.9 --all
sudo rm /usr/src/rtl8812au-5.2.9
```

Thank you very much. 
I will try it this afternoon.

---

### Post by jcasasruiz on 2018-06-20
> **chili555 said:**
> Version 4.2.2 of the driver doesn't compile correctly on 18.04. Try this instead: [https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927](https://askubuntu.com/questions/1045765/usb-antenna-not-working-on-dell-optiplex-760-desktop/1045927#1045927)

You can safely skip these steps:```
sudo dkms remove rtl8812au/5.2.9 --all
sudo rm /usr/src/rtl8812au-5.2.9
```

Ok, I've follow those instructions and it works!. Even without reboot!

Thank you again!

---

### Post by chili555 on 2018-06-20
Awesome! Glad it’s working.

---

