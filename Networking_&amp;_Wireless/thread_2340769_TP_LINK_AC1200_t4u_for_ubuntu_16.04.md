---
title: "TP LINK AC1200 t4u for ubuntu 16.04"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by ashish.patel11ee211 on 2016-10-21
I would like to say that I tried a lot for this USB adapter installation.

Here I put every single link. From where I took references. 

First I tried: ```
http://www.tp-link.com/en/download/Archer-T4U.html
```

second I tried: ```
https://www.amazon.com/product-reviews/B00JBJ6VG8
``` on this page one comment is *[Linux Installation for this device is not trivial, needs work.]("https://www.amazon.com/gp/customer-reviews/R1KU16HJPYL0O4/ref=cm_cr_arp_d_rvw_ttl?ie=UTF8&ASIN=B00JBJ6VG8")*

third I tried: ```
https://ubuntuforums.org/showthread.php?t=2264741
```

then I tried: ```
https://github.com/ptpt52/rtl8812au
```


Still, I don't get the satisfied answer. Please help me and give me step by step answer if possible.

---

### Post by howefield on 2016-10-22
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by chili555 on 2016-10-22
Let's start by identifying your exact device. Please open a terminal and run and post here:```
lsusb
uname -r
```

---

### Post by ashish.patel11ee211 on 2016-10-22
Oh finally!! Thanks chili

```
root@Xman:~# lsusb
Bus 002 Device 004: ID 2357:0101  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0cf3:3121 Atheros Communications, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b40d Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0eef:a103 D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Xman:~# uname -r
4.4.0-42-generic
root@Xman:~# 
```

---

### Post by jeremy31 on 2016-10-22
So what are the results from ```
lsusb
``` with the device not plugged in?

---

### Post by chili555 on 2016-10-22
With a working internet connection, please do:```
sudo apt-get purge rtl8812au-dkms
```If it isn't installed, that's fine; just continue:```
sudo apt-get update
sudo apt-get install git dkms
git clone  https://github.com/ptpt52/rtl8812au.git
cd rtl8812au
sudo make -f Makefile.dkms install
sudo modprobe rtl8812au
```You should be all set.

---

### Post by ashish.patel11ee211 on 2016-10-22
I followed every step but then I got this error:

```
root@Xman:~/rtl8812au# sudo make -f Makefile.dkms install
make clean
make[1]: Entering directory '/home/a/rtl8812au'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-42-generic/build M=/home/a/rtl8812au clean
make[2]: Entering directory '/usr/src/linux-headers-4.4.0-42-generic'
make[2]: Leaving directory '/usr/src/linux-headers-4.4.0-42-generic'
make[1]: Leaving directory '/home/a/rtl8812au'
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
make KERNELRELEASE=4.4.0-42-generic KVER=4.4.0-42-generic.............................
cleaning build area....

DKMS: build completed.
dkms install -m rtl8812au -v 4.3.14

rtl8812au:
Running module version sanity check.

Good news! Module version v4.3.14_13455.20150212_BTCOEX20150128-51 for rtl8812au.ko
exactly matches what is already found in kernel 4.4.0-42-generic.
DKMS will not replace this module.
You may override by specifying --force.

depmod....

DKMS: install completed.

root@Xman:~/rtl8812au# sudo modprobe rtl8812au
modprobe: ERROR: could not insert 'rtl8812au': Required key not available


```

---

### Post by chili555 on 2016-10-22
> modprobe: ERROR: could not insert 'rtl8812au': Required key not availablePlease see: [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

The quick and easy way is to disable secure boot in the BIOS.> You can disable Secure Boot (UEFI) in the BIOS with the following steps:

1. Reboot your machine and enter the BIOS Menu (In my case pressing F2)
2. Search for Secure Boot and change to Legacy


---

### Post by ashish.patel11ee211 on 2016-10-22
It's working. Thanks, man. I didn't try on legacy mode. Thanks once again

---

### Post by chili555 on 2016-10-22
Glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

