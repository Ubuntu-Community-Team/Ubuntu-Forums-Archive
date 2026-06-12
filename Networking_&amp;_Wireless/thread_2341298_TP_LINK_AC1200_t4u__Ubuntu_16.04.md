---
title: "TP LINK AC1200 t4u / Ubuntu 16.04"
date: 2016-10-26
forum: Networking &amp; Wireless
---

### Post by balazsfeher on 2016-10-26
@chili555 Thanks, I followed the steps you suggested, however I get the following error message at: sudo make -f Makefile.dkms install
```
make clean
make[1]: Entering directory `/home/balazs/Downloads/rtl8812au'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-040400-generic/build M=/home/balazs/Downloads/rtl8812au clean
make[2]: Entering directory `/usr/src/linux-headers-4.4.0-040400-generic'
make[2]: Leaving directory `/usr/src/linux-headers-4.4.0-040400-generic'
make[1]: Leaving directory `/home/balazs/Downloads/rtl8812au'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
make KERNELRELEASE=4.4.0-040400-generic KVER=4.4.0-040400-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8812au: 4.3.14 not found
Error! Bad return status for module build on kernel: 4.4.0-040400-generic (x86_64)
Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.
make: *** [build] Error 10

```

---

### Post by QIII on 2016-10-26
Moved to its own post from [https://ubuntuforums.org/showthread.php?t=2340769](https://ubuntuforums.org/showthread.php?t=2340769)

Hello!

Hijacking threads is generally considered poor netiquette.  Hijacking one that is marked "solved" is a good way for your question to be missed.

This should improve your chances of getting help.

Cheers!

---

### Post by chili555 on 2016-10-26
> Consult /var/lib/dkms/rtl8812au/4.3.14/build/make.log for more information.So what does it say?```
cat  /var/lib/dkms/rtl8812au/4.3.14/build/make.log 
```

---

