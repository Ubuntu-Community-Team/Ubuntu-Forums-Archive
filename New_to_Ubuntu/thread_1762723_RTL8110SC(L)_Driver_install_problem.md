---
title: "RTL8110SC(L) Driver install problem"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by for-loop on 2011-05-19
Hi
My problem is that a couple of days ago i installed Ubuntu 11.04 and now my computer wont connect to the internet
it will not connect to a wire network and it doesn't detect any wireless networks

Using the command lspci -nn i found out that my NIC was a Realtek RTL-8110SC/8169SC

I have found this driver from the Realtek website: RTL8110SC(L)
and I think its the right one
i downloaded it the file was called: r8169-6.014.00.tar.bz2

i extracted the file to my home directory
the readme file that came with this file told me to:

ReadMefile: # lsmod | grep r8169
my output: r8169 48022 0

ReadMefile: # rmmod r8169
my output: N/A Ran successfully

ReadMefile: cd r8169-6.014.00
my output: N/A changed directory

ReadMefile: sudo make clean modules
my output: and heres where i get I get an error at this point:
```

make -C src/ clean
make[1]: Entering directory `/home/ryan/r8169-6.014.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/ryan/r8169-6.014.00/src'
make -C src/ modules
make[1]: Entering directory `/home/ryan/r8169-6.014.00/src'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'. Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ryan/r8169-6.014.00/src'
make: *** [modules] Error 2

```

Im pretty new to Linux so i don't have a clue what Im doing wrong
any help with this would be great

---

### Post by for-loop on 2011-05-19
bump

please need help with is

---

### Post by gandaran on 2011-05-19
try posting or search for RTL8110 solved threads in the [networking and wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") section, you'll get quicker support there.

---

### Post by gandaran on 2011-05-19
> Realtek RTL-8110SC/8169SC
isn't this the ethernet controller?
post the full output of 
```
lspci
```
and
```
lsusb
```

---

### Post by for-loop on 2011-05-19
lspci:```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:02.0 Network controller: Ralink corp. Device 3060
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

lsusb:```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by gandaran on 2011-05-20
hi,
> 02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
ethernet should be working fine on your computer, no need to install any realtek drivers, if you are experiencing problems then maybe there are network problems not drivers.
> 02:02.0 Network controller: Ralink corp. Device 3060
this is the wireless controller, I'm not sure if this ralink chip works out of the box in ubuntu, see this thread
[http://ubuntuforums.org/showthread.php?t=1712443](http://ubuntuforums.org/showthread.php?t=1712443)
hope it helps.

---

### Post by for-loop on 2011-05-20
Thanks for the help 
I installed the driver for Ralink corp. Device 3060
without too much trouble

---

