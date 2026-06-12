---
title: "Webcam ZC0305 doesn't work and gspca doesn't build"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by meindian523 on 2008-12-18
As title says,I tried building the gspca-source package as mentioned in a thread I searched out here in Ubuntuforums,but the package doesn't build despite following ```
m-a prepare
``` which finishes successfully,albeit with a failed attempt at creating a symlink,but ```
m-a a-i gspca
``` errors out,despite those being the exact steps described in the readme.debian.What should I do?If required,I can provide the logs created by module-assistant.Can the error be due to > This package provides the gspca source code that can be used to build
modules that work with your **custom built linux kernel**.?:confused::shock::(

---

### Post by meindian523 on 2008-12-19
bump?

---

### Post by meindian523 on 2008-12-19
After I autoremoved linux-headers,the m-a prepare could also create the symlink successfully,but m-a a-i gspca errors out as usual.And,I'm trying to install on a 64-bit system,can that be a problem.
No one knows??
Log file:
```

dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
    .gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
    *.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g ; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##/2.6.27-9.19/g ; s/#KDREV#/2.6.27-9.19/g ; s/_KDREV_/2.6.27-9.19/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-9-generic KERNELDIR=/usr/src/linux
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2604: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2

```

---

### Post by y-u-h on 2009-11-01
error in your log file is errors in my log..... one by one
I'm asking for help here [http://ubuntuforums.org/showthread.php?p=8215015](http://ubuntuforums.org/showthread.php?p=8215015)
Lets's try to solve this little trouble :p

---

