---
title: "BCM4312 + STA Driver + HP2133 + Intrepid = Latency"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by slipdipper on 2008-11-16
Im seeing some latency when using the broadcom sta wireless driver (wl). this happens when using both 802.11a and 802.11g. Within windows on the same system, i do not see any latency

I've noticed that the drivers may have been compiled for a 64bit system, can anyone confirm this, i'm assuming thats what the "64-bit" in the lspci output and the "width: 64 bits" in the lshw output means. These were the drivers installed via System -> Administration -> Hardware Drivers. 

Additionally, the gnome-networkmanager app does correctly read the signal strength when using 802.11a. i dont know if that matters at all

Could using a 64-bit driver on a 32-bit system cause strange behaviour (i.e latency)? Anyone else see these issues? any other ideas?  

/proc$ lspci -v -s 02:00.0
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
	Subsystem: Hewlett-Packard Company Device 1370
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: ssb, wl

:/proc$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:21:00:13:9c:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=10.219.1.204 latency=0 module=wl multicast=yes wireless=IEEE 802.11a

/proc$ uname -a
Linux system 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

### Post by Marcus Derekus on 2008-11-16
Check this thread out. [http://ubuntuforums.org/showthread.php?t=982155](http://ubuntuforums.org/showthread.php?t=982155)

Maynot be the same error but the solution still might work

---

### Post by slipdipper on 2008-11-16
nope, that post is to install the broadcom sta driver which is what i already have installed and expect the problem is.

---

### Post by Marcus Derekus on 2008-11-16
Yeah but the link given has the 32-bit drivers.

If you follow the instructions of the read me
it will tell you how to set it up

readme is downloaded seperately

plus after you install the driver you may wnatto add this command to local.rc

```

sudo insmod /path/to/driver

```

Also this driver does not come with ubuntu.

It's Seperate

---

### Post by slipdipper on 2008-11-18
so as per your request i downloaded an reinstalled the driver from: [http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32_5_10_27_6.tar.gz](http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32_5_10_27_6.tar.gz) when i compiled and inserted the module it still shows a width of 64 and says 64bit in the output. are we sure that this actually means 64 bit drivers? does that mean broadcom's site is wrong? any ideas?


```
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ patch -p1 < hybrid_wl-5.10.27.6_patch-2.6.27 
patching file src/wl/sys/wl_iw.c
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ make -C /lib/modules/`uname -r`/build M=`pwd` clean
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/slip/Documents/hybrid-portsrc-x86_32/built-in.o
  CC [M]  /home/slip/Documents/hybrid-portsrc-x86_32/src/wl/sys/wl_linux.o
  CC [M]  /home/slip/Documents/hybrid-portsrc-x86_32/src/wl/sys/wl_iw.o
  CC [M]  /home/slip/Documents/hybrid-portsrc-x86_32/src/shared/linux_osl.o
/home/slip/Documents/hybrid-portsrc-x86_32/src/shared/linux_osl.c: In function ‘osl_printf’:
/home/slip/Documents/hybrid-portsrc-x86_32/src/shared/linux_osl.c:456: warning: format not a string literal and no format arguments
  LD [M]  /home/slip/Documents/hybrid-portsrc-x86_32/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/slip/Documents/hybrid-portsrc-x86_32/wl.o
see include/linux/module.h for more information
  CC      /home/slip/Documents/hybrid-portsrc-x86_32/wl.mod.o
  LD [M]  /home/slip/Documents/hybrid-portsrc-x86_32/wl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ sudo rmmod wl
[sudo] password for slip: 
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ sudo insmod `pwd`/wl.ko
slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ lspci -v -s 02:00.0
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
	Subsystem: Hewlett-Packard Company Device 1370
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: ssb, wl

slip@dipdadooken:~/Documents/hybrid-portsrc-x86_32$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: 00:21:00:13:9c:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=10.219.1.204 latency=0 module=wl multicast=yes wireless=IEEE 802.11a

```

---

### Post by Marius Derekus on 2008-11-18
Don't think that is wut it means cuz myne sez it 2

---

### Post by slipdipper on 2008-12-05
UPDATE:
played around with the drivers a bunch, with no fix. 


bought a atheros minipci-express adapter, blacklisted the ath9k (mac80211) drivers, went back to good old madwifi-ng (ath_pci) and sure enough, no latency, no problems.

---

### Post by silvari on 2009-03-05
I've run into the same latency problem, with a BCM4312 Rev 01, using out-of-the-box  "Restricted" / proprietary driver, with Ubuntu 8.10 on my HP Mini 1030NR. When looking at ifconfig I'm seeing a very high number of frame errors - sometimes more frame errors that packets received. This is seen regardless of the wifi network connected to - work, home, cafe, etc. 

Anyone else finding latency & seeing framing errors?

---

