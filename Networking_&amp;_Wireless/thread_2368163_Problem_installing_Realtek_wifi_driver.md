---
title: "Problem installing Realtek wifi driver"
date: 2017-08-07
forum: Networking &amp; Wireless
---

### Post by dapada on 2017-08-07
I got a usb wifi adapter that uses RTL8811AU. I followed the instructions from this thread [https://ubuntuforums.org/showthread.php?t=2306417](https://ubuntuforums.org/showthread.php?t=2306417) but I get an error on the last step 
```
sudo modprobe 8812au.
``` 

gives this error 

```
modprobe: FATAL: Module 8812au not found in directory /lib/modules/4.10.0-27-generic
```

---

### Post by Hadaka on 2017-08-07
Hi, please see post # 6
[https://ubuntuforums.org/showthread.php?t=2340769](https://ubuntuforums.org/showthread.php?t=2340769)
Thanks.

---

### Post by dapada on 2017-08-07
Most of the commands worked from that but I still got some errors.

```
sudo make -f Makefile.dkms install
```

gave this results

```
make clean
make[1]: Entering directory '/home/tasneeem/rtl8812au'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-27-generic/build M=/home/tasneeem/rtl8812au clean
make[2]: Entering directory '/usr/src/linux-headers-4.10.0-27-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.10.0-27-generic'
make[1]: Leaving directory '/home/tasneeem/rtl8812au'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true

Creating symlink /var/lib/dkms/rtl8812au/4.3.14/source ->
                 /usr/src/rtl8812au-4.3.14

DKMS: add completed.
dkms build -m rtl8812au -v 4.3.14

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=4.10.0-27-generic KVER=4.10.0-27-generic.......................................................
cleaning build area....

DKMS: build completed.
dkms install -m rtl8812au -v 4.3.14

rtl8812au:
Running module version sanity check.
Error! Module version v4.3.14_13455.20150212_BTCOEX20150128-51 for rtl8812au.ko
is not newer than what is already found in kernel 4.10.0-27-generic (v4.3.14_13455.20150212_BTCOEX20150128-51).
You may override by specifying --force.

depmod..........

DKMS: install completed.


```

and 

```
sudo modprobe rtl8812au
```

gave this error

```
modprobe: ERROR: could not insert 'rtl8812au': Required key not available
```

---

### Post by Hadaka on 2017-08-07
Hi, this link..
[https://ubuntuforums.org/showthread.php?t=2340769](https://ubuntuforums.org/showthread.php?t=2340769)
is pretty much a carbon copy of your thread including
the exact error...please read the entire linked thread,
especially post # 8.
Thanks.

---

