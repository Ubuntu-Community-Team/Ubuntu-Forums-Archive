---
title: "Tenda U12 on Ubuntu 21.04"
date: 2021-07-31
forum: Networking &amp; Wireless
---

### Post by linub2 on 2021-07-31
Hello
I was using ubuntu 20.04 and after i upgraded to Ubuntu 21.04 my wifi adapter Tenda U12 isn't working, the  wireless icon in top right it is not showing up when i plug the adapter. In 20.04 i have installed this adapter with this tutorial [https://medium.com/@manuelmauriciozamarrn/tenda-u12-wireless-usb-and-kali-linux-2a5796decb81](https://medium.com/@manuelmauriciozamarrn/tenda-u12-wireless-usb-and-kali-linux-2a5796decb81)  , now when i'm trying to run the first command it gives > fatal: destination path 'rtl8812au-5.6.4.2' already exists and is not an empty directory.  then ```
cd rtl8812au-5.6.4.2
``` and ```
make
``` it gaves this
 
> /home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2203:11: error: implicit declaration of function ‘get_fs’; did you mean ‘get_sa’? [-Werror=implicit-function-declaration] 2203 |   oldfs = get_fs();
      |           ^~~~~~
      |           get_sa
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2203:11: error: incompatible types when assigning to type ‘mm_segment_t’ from type ‘int’
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2205:3: error: implicit declaration of function ‘set_fs’; did you mean ‘sget_fc’? [-Werror=implicit-function-declaration]
 2205 |   set_fs(KERNEL_DS);
      |   ^~~~~~
      |   sget_fc
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2205:10: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2205 |   set_fs(KERNEL_DS);
      |          ^~~~~~~~~
      |          KERNFS_NS
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2205:10: note: each undeclared identifier is reported only once for each function it appears in
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c: In function ‘retriveFromFile’:
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2245:12: error: incompatible types when assigning to type ‘mm_segment_t’ from type ‘int’
 2245 |    oldfs = get_fs();
      |            ^~~~~~
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2247:11: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2247 |    set_fs(KERNEL_DS);
      |           ^~~~~~~~~
      |           KERNFS_NS
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c: In function ‘storeToFile’:
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2284:12: error: incompatible types when assigning to type ‘mm_segment_t’ from type ‘int’
 2284 |    oldfs = get_fs();
      |            ^~~~~~
/home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.c:2286:11: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2286 |    set_fs(KERNEL_DS);
      |           ^~~~~~~~~
      |           KERNFS_NS
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:287: /home/ld/rtl8812au-5.6.4.2/os_dep/osdep_service.o] Error 1
make[1]: *** [Makefile:1848: /home/ld/rtl8812au-5.6.4.2] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-22-generic'
make: *** [Makefile:2271: modules] Error 2




I must say that i'm new and i don't know what to do to fix?

---

### Post by linub2 on 2021-07-31
Solved 

i run ```
[COLOR=#000000][FONT=&amp]sudo apt dist-upgrade[/FONT][/COLOR]
``` after i run Software Updater app and it requires restart i restarted and wireless icon shows up in the corner.

---

