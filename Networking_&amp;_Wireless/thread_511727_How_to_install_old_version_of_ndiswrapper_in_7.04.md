---
title: "How to install old version of ndiswrapper in 7.04 ?"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by samuliri on 2007-07-28
I need to install old ndiswrapper version (version 1.20 or older) for BCM4210 iLine10 HomePNA 2.0.

I have downloaded ndiswrapper 1.12 package from here:
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243)

1) When I try to install ndiswrapper with commands:
make distclean
make
sudo make install

"make distclean" goes ok, but "make" gives following error:

samuliri@samuliri-desktop:~/ndiswrapper-1.12rc1$ make
make -C driver
make[1]: Entering directory `/home/samuliri/ndiswrapper-1.12rc1/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/samuliri/ndiswrapper-1.12rc1/driver \
                DRIVER_VERSION=1.12rc1
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/samuliri/ndiswrapper-1.12rc1/driver/built-in.o
  CC [M]  /home/samuliri/ndiswrapper-1.12rc1/driver/hal.o
  CC [M]  /home/samuliri/ndiswrapper-1.12rc1/driver/iw_ndis.o
  CC [M]  /home/samuliri/ndiswrapper-1.12rc1/driver/loader.o
  CC [M]  /home/samuliri/ndiswrapper-1.12rc1/driver/misc_funcs.o
  CC [M]  /home/samuliri/ndiswrapper-1.12rc1/driver/ndis.o
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c:44:41: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c: In function ‘ndis_init’:
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c:44: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c:44: error: (Each undeclared identifier is reported only once
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c:44: error: for each function it appears in.)
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c: In function ‘NdisMRegisterInterrupt’:
/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.c:1863: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[3]: *** [/home/samuliri/ndiswrapper-1.12rc1/driver/ndis.o] Error 1
make[2]: *** [_module_/home/samuliri/ndiswrapper-1.12rc1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/samuliri/ndiswrapper-1.12rc1/driver'
make: *** [all] Error 2


What should I do?



2) And if I alternatively try to build deb packages and install according to these link:
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=167243)
see: "5.4. Build deb packages and install" 

I get this error:

samuliri@samuliri-desktop:~/ndiswrapper-1.12rc1$ fakeroot debian/rules binary-modules
sed -e 's/#KVERS#/2.6.20-16-generic/g' \
                -e 's/#DRIVER_VERSION#/1.12rc1/g' \
                -e 's/#UTILS_VERSION#/1.8/g' \
                -e 's/#DATE#/'"`date --rfc-822`"'/g' \
                -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
                debian/changelog.modules > debian/changelog
sed -e 's/#KVERS#/2.6.20-16-generic/' \
                -e 's/#DRIVER_VERSION#/1.12rc1/' \
                -e 's/#UTILS_VERSION#/1.8/' \
                debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.20-16-generic/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
                module=ndiswrapper.o; \
        else \
                module=ndiswrapper.ko; \
        fi; \
        echo "driver/$module /lib/modules/2.6.20-16-generic/misc" \
                > debian/ndiswrapper-modules-2.6.20-16-generic.install
[: 7: ==: unexpected operator
dh_testdir
make: dh_testdir: Command not found
make: *** [common-prolog] Error 127


What should I do?

---

