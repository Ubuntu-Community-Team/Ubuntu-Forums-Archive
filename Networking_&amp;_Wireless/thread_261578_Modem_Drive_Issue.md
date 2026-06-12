---
title: "Modem Drive Issue"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by kingfish on 2006-09-20
david@ubuntu:~$ make clean
cd coredrv; make clean
make[1]: Entering directory `/home/david/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/david/coredrv'
rm -f *.o *.ko
david@ubuntu:~$ make 536
   Module precompile check
   Current running kernel is: 2.6.15-27-686
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.15-27-686
make[1]: Entering directory `/home/david/coredrv'
make -C /lib/modules/2.6.15-27-686/build SUBDIRS=/home/david/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-686'
  CC [M]  /home/david/coredrv/coredrv.o
/home/david/coredrv/coredrv.c:70: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/david/coredrv/coredrv.c:70: warning: parameter names (without types) in function declaration
/home/david/coredrv/coredrv.c:70: warning: data definition has no type or storage class
/home/david/coredrv/coredrv.c: In function ‘power_callback’:
/home/david/coredrv/coredrv.c:295: error: ‘PM_SAVE_STATE’ undeclared (first use in this function)
/home/david/coredrv/coredrv.c:295: error: (Each undeclared identifier is reported only once
/home/david/coredrv/coredrv.c:295: error: for each function it appears in.)
/home/david/coredrv/coredrv.c: In function ‘close’:
/home/david/coredrv/coredrv.c:418: warning: implicit declaration of function ‘pm_unregister’
/home/david/coredrv/coredrv.c: In function ‘hamproc_write’:
/home/david/coredrv/coredrv.c:662: warning: ignoring return value of ‘copy_from_user’, declared with attribute warn_unused_result
/home/david/coredrv/coredrv.c: At top level:
/home/david/coredrv/coredrv.c:756: warning: initialization from incompatible pointer type
/home/david/coredrv/coredrv.c:757: warning: initialization from incompatible pointer type
/home/david/coredrv/coredrv.c: In function ‘kScheduleDPC’:
/home/david/coredrv/coredrv.c:863: warning: implicit declaration of function ‘pm_access’
/home/david/coredrv/coredrv.c: In function ‘dspdrv_CommRamISR’:
/home/david/coredrv/coredrv.c:879: warning: function declaration isn’t a prototype
make[3]: *** [/home/david/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/david/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-686'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/david/coredrv'
2.6.15-27-686
Failed to build driver

---

