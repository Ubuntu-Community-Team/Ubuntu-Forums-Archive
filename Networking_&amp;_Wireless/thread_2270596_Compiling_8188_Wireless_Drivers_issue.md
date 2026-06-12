---
title: "Compiling 8188 Wireless Drivers issue"
date: 2015-03-24
forum: Networking &amp; Wireless
---

### Post by rogerthis on 2015-03-24
Greetings,

I've been trying to install my ASUS N10 Nano wireless pen, it comes with a CD containing some old realtek drivers (RTL8188C_8192C_USB_linux_v4.0.1-1_6911.20130308), and i went to the realtek webpage to get the latest ones (rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911).
After doing dist-update and proper update of the OS, im getting the following errors while compiling with make:

```
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.18.0-kali3-amd64/build M=/root/WRLS  modules
make[1]: Entering directory `/usr/src/linux-headers-3.18.0-kali3-amd64'
  CC [M]  /root/WRLS/os_dep/linux/os_intfs.o
/root/WRLS/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/root/WRLS/os_dep/linux/os_intfs.c:313:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
/root/WRLS/os_dep/linux/os_intfs.c:313:11: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:320:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
/root/WRLS/os_dep/linux/os_intfs.c:320:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:326:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:332:8: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:348:21: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:379:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:385:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:387:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:393:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:396:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:404:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:412:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:420:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:427:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:441:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:448:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:455:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:462:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:469:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:476:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:483:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:490:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:497:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:504:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:511:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:520:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:527:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:537:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:555:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:561:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:564:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:570:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:572:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:578:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:580:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:586:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:588:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:594:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:596:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:602:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:605:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:608:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:615:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:622:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:628:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c:631:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:637:7: error: dereferencing pointer to incomplete type
/root/WRLS/os_dep/linux/os_intfs.c: At top level:
/root/WRLS/os_dep/linux/os_intfs.c:999:2: warning: initialization from incompatible pointer type [enabled by default]
/root/WRLS/os_dep/linux/os_intfs.c:999:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
cc1: some warnings being treated as errors
make[4]: *** [/root/WRLS/os_dep/linux/os_intfs.o] Error 1
make[3]: *** [_module_/root/WRLS] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.18.0-kali3-amd64'
make: *** [modules] Error 2
```

Are the latest drivers working on latest OS updates? is create_proc_entry deprecated?
Kind Regards

---

