---
title: "537ep not compiling under edgy"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by anon32 on 2006-11-06
I've installed build-essential and linux-headers-generic, but when I try to compile the Intel 2.7.0.95 - SUSE9.3 drivers mentioned in chuckman's howto for dapper, I get the build error listed below:

   Module precompile check
   Current running kernel is: 2.6.17-10-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
2.6.17-10-generic
make[1]: Entering directory `/home/shawn-admin/Intel-537/coredrv'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/shawn-admin/Intel-537/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/shawn-admin/Intel-537/coredrv/coredrv.o
/home/shawn-admin/Intel-537/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/shawn-admin/Intel-537/coredrv/coredrv.c:73: warning: type defaults to â€˜intâ€™ in declaration of â€˜EXPORT_SYMBOL_NOVERSâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜softcore_init_structâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜openâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:397: warning: implicit declaration of function â€˜pm_registerâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:398: warning: assignment makes pointer from integer without a cast
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜closeâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:427: warning: implicit declaration of function â€˜pm_unregisterâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜send_data_to_userâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:574: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:579: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:580: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:582: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:583: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c:584: error: â€˜struct tty_structâ€™ has no member named â€˜flipâ€™
/home/shawn-admin/Intel-537/coredrv/coredrv.c: At top level:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:652: error: expected â€˜)â€™ before string constant
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜hamproc_writeâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:671: warning: ignoring return value of â€˜copy_from_userâ€™, declared with attribute warn_unused_result
/home/shawn-admin/Intel-537/coredrv/coredrv.c: At top level:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:867: warning: initialization makes integer from pointer without a cast
/home/shawn-admin/Intel-537/coredrv/coredrv.c: In function â€˜kScheduleDPCâ€™:
/home/shawn-admin/Intel-537/coredrv/coredrv.c:872: warning: implicit declaration of function â€˜pm_accessâ€™
make[3]: *** [/home/shawn-admin/Intel-537/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/shawn-admin/Intel-537/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [537core_26] Error 2
make[1]: Leaving directory `/home/shawn-admin/Intel-537/coredrv'
2.6.17-10-generic
Failed to build driver

Reverting to the 2.60.80.1 drivers, the compile finishes, but I get the error

rm -f /etc/hamregistry.bin
bash 537_inst
running kernel 2.6.17-10-generic
installing hamregistry, used for persistant storage
installing usrsound, a soft buzzer
installing 537 module
install DEBIAN 537 boot script and links
starting module and utilities
FATAL: Error inserting Intel537 (/lib/modules/2.6.17-10-generic/kernel/drivers/char/Intel537.ko): Invalid module format
insmod: can't read 'Intel537': No such file or directory
error loading Intel537
ERROR: Module Intel537 does not exist in /proc/modules
done

any help?

---

