---
title: "ATMEL Wireless USB device nightmare!"
date: 2005-09-13
forum: Networking &amp; Wireless
---

### Post by samkivi on 2005-09-13
I've been on other old threads to figure this out but noone is reading it or replying so here goes:
I have a Belkin F5D6050 USB Wireless device and am tryin to install it with Hoary and amtel at76c503a drivers.
I run
```
 uname -r
```
and get 2.6.10-5-386

I will try to include as much info as I can find about the problem:

I have installed: according to this thread
[http://www.ubuntuforums.org/showthread.php?t=5164&highlight=f5d6050](http://www.ubuntuforums.org/showthread.php?t=5164&highlight=f5d6050)

linux-headers-k7
gcc
gcc-3.3

then using a working eth0 link i ran:
```
apt-get install at76c503a-source atmel-firmware
```
all ok.
then:
 ```
 # cd /usr/src
  # tar xvzf at76c503a.tar.gz
  # cd modules/at76c503a
  # debian/rules binary-modules KVERS=2.6.10-5-k7
```
this is where i get errors:
```
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/at76c503a'
mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-k7/build/.tmp_versions/*.mod /usr/src/modules/at76c503a /.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-k7/build/.tmp_versions/*.mod': No such fi le or directory
make[1]: [modules] Error 1 (ignored)
/usr/bin/make -C /lib/modules/2.6.10-5-k7/build SUBDIRS=/usr/src/modules/at76c50 3a MODVERDIR=/usr/src/modules/at76c503a/.tmp_versions \
EXTRA_CFLAGS="" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-k7'
  CC [M]  /usr/src/modules/at76c503a/at76c503-i3861.o
  CC [M]  /usr/src/modules/at76c503a/at76c503-rfmd.o
  CC [M]  /usr/src/modules/at76c503a/at76c503-rfmd-acc.o
  CC [M]  /usr/src/modules/at76c503a/at76c505-rfmd.o
  CC [M]  /usr/src/modules/at76c503a/at76c503-i3863.o
  CC [M]  /usr/src/modules/at76c503a/at76c505-rfmd2958.o
  CC [M]  /usr/src/modules/at76c503a/at76c505a-rfmd2958.o
  CC [M]  /usr/src/modules/at76c503a/at76c503.o
/usr/src/modules/at76c503a/at76c503.c: In function `ieee80211_to_eth':
/usr/src/modules/at76c503a/at76c503.c:3922: warning: assignment from incompatible pointer type
  CC [M]  /usr/src/modules/at76c503a/at76_usbdfu.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/modules/at76c503a/at76_usbdfu.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76_usbdfu.ko
  CC      /usr/src/modules/at76c503a/at76c503-i3861.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c503-i3861.ko
  CC      /usr/src/modules/at76c503a/at76c503-i3863.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c503-i3863.ko
  CC      /usr/src/modules/at76c503a/at76c503-rfmd-acc.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c503-rfmd-acc.ko
  CC      /usr/src/modules/at76c503a/at76c503-rfmd.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c503-rfmd.ko
  CC      /usr/src/modules/at76c503a/at76c503.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c503.ko
  CC      /usr/src/modules/at76c503a/at76c505-rfmd.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c505-rfmd.ko
  CC      /usr/src/modules/at76c503a/at76c505-rfmd2958.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c505-rfmd2958.ko
  CC      /usr/src/modules/at76c503a/at76c505a-rfmd2958.mod.o
  LD [M]  /usr/src/modules/at76c503a/at76c505a-rfmd2958.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
make[1]: Leaving directory `/usr/src/modules/at76c503a'
for i in control changelog; do                                          \
    sed 's/#KVERS#/2.6.10-5-k7/g' debian/$i.template                    \
        | sed 's/#KVERS#/2.6.10-5-k7/g' | sed 's/#KMAINT#//g'   \
        | sed 's/#KEMAIL#//g' | sed "s/#DEBDATE#/Tue, 13 Sep 2005 16:36:35 +1200/g"     \
        | sed 's/#KDREV#/unknown/g' > /usr/src/modules/at76c503a/debian/$i;             \
done
/usr/bin/make  DESTDIR=/usr/src/modules/at76c503a/debian/tmp install-modules
make[1]: Entering directory `/usr/src/modules/at76c503a'
mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-k7/build/.tmp_versions/*.mod /usr/src/modules/at76c503a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-k7/build/.tmp_versions/*.mod': No such file or directory
make[1]: [modules] Error 1 (ignored)
/usr/bin/make -C /lib/modules/2.6.10-5-k7/build SUBDIRS=/usr/src/modules/at76c503a MODVERDIR=/usr/src/modules/at76c503a/.tmp_versions \
EXTRA_CFLAGS="" modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-k7'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
mkdir -p /usr/src/modules/at76c503a/debian/tmp/lib/modules/2.6.10-5-k7/kernel/drivers/net/wireless/at76c503
install -m 644 -o 0 -g 0 at76c503-i3861.ko at76c503-rfmd.ko at76c503-rfmd-acc.ko at76c505-rfmd.ko at76c503-i3863.ko at76c505-rfmd2958.ko at76c505a-rfmd2958.ko at76c503.ko at76_usbdfu.ko /usr/src/modules/at76c503a/debian/tmp/lib/modules/2.6.10-5-k7/kernel/drivers/net/wireless/at76c503
make[1]: Leaving directory `/usr/src/modules/at76c503a'
dh_testdir
dh_testroot
dh_installdirs
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installchangelogs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb --destdir=/usr/src/modules/at76c503a/..
dpkg-deb: building package `at76c503a-modules-2.6.10-5-k7' in `/usr/src/modules/at76c503a/../at76c503a-modules-2.6.10-5-k7_0.10.99.beta5+unknown_i386.deb'.
```

so i continue with:

```
# cd ..
# dpkg -i at76c503a-modules-2.6.10-5-k7_0.10.99.beta5+unknown_i386.deb
# depmod -a
# modprobe -v at76c503-rfmd-acc
```

and i get
```

FATAL: Module at76c503_rfmd_acc not found.
```

I also tried adding the "a" on the end as in at76c503a.

I have a feeling this is to do with the 2.6.10-5-k7 versus 2.6.10-5-386
when i plug/unplug the device and read the dmesg readout, it shows:

```
usb 1-1: new full speed USB device using uhci_hcd and address 7
usb 1-1: USB disconnect, address 7
usb 1-1: new full speed USB device using uhci_hcd and address 8
usb 1-1: USB disconnect, address 8
usb 1-1: new full speed USB device using uhci_hcd and address 9
  
```

but I know nearly NOTHING about linux so I cannot play around much to fix this
PLEASE can someone help? I'm at my wits end!

also, I'm looking at ndiswrapper for other setups, and find that all the windows drivers are .sys files not .inf! what's the difference? i CANNOT find inf's anywhere! all the inf's are "autorun.inf"!!!

thankyou so much if you can help - the other thread i tried is being ignored!!

---

