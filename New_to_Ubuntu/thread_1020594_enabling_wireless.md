---
title: "enabling wireless"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by ianmaxwell on 2008-12-24
i just installed ubuntu on an old acer travelmate 290E.
wireless doesn't work at all, and being a complete novice i have no idea of how to set up a driver for the wireless card (which is built into the computer)

i've done a little searching and i can't find anything closely releated to my problem and easy enough for me to follow.

please help:)

thanks,

ian

---

### Post by st33med on 2008-12-24
Post the output here:
```
lspci | grep Network
```

---

### Post by ianmaxwell on 2008-12-24
oh and i believe the wireless chip to be a broadcom BCM4306 b/g
(hope this helps)

---

### Post by ibizatunes on 2008-12-24
Broadcom you need restrcited drivers to run it? What version of ubuntu have you install 8.10 or 8.04,  
8.10 has alot better wireless support

---

### Post by ianmaxwell on 2008-12-24
rev 3

---

### Post by ianmaxwell on 2008-12-24
sorry, how do i tell which version i am running.

i am absolute beginner

---

### Post by deputy on 2008-12-24
I would say the first thing to do is to try to figure out what kind of wireless card you have, and then from there you can look for the drivers. Try:
```
sudo lspci -v
```
And post back the results.

---

### Post by st33med on 2008-12-24
Here ya go, follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by ibizatunes on 2008-12-24
system > admin > system monitor > and it say ubuntu release xxxxx

---

### Post by ianmaxwell on 2008-12-24
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, fast devsel, latency 0
	Memory at <unassigned> (32-bit, prefetchable)
	Capabilities: [40] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, fast devsel, latency 0

00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at b0000000 (32-bit, prefetchable) [size=128M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at e000 [size=8]
	Capabilities: [d0] Power Management version 1
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, fast devsel, latency 0
	Memory at 10000000 (32-bit, prefetchable) [size=128M]
	Memory at 18000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1200 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1600 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 1700 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	Memory at f0080000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=05, sec-latency=32
	I/O behind bridge: 0000c000-0000dfff
	Memory behind bridge: e0000000-efffffff
	Prefetchable memory behind bridge: a0000000-afffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: intel-rng, iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1100 [size=16]
	Memory at 18080000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: medium devsel, IRQ 255
	I/O ports at 1400 [size=32]
	Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0021
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at e100 [size=256]
	I/O ports at e200 [size=64]
	Memory at f0080400 (32-bit, non-prefetchable) [size=512]
	Memory at f0080600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: medium devsel, IRQ 10
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Capabilities: [50] Power Management version 2
	Kernel modules: snd-intel8x0m

01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 128, IRQ 10
	I/O ports at c000 [size=256]
	Memory at e0002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

01:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Wistron NeWeb Corp. Device 1220
	Flags: bus master, fast devsel, latency 128, IRQ 10
	Memory at e0000000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

01:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 003d
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at e0003000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: a0000000-a3fff000 (prefetchable)
	Memory window 1: e4000000-e7fff000
	I/O window 0: 0000c400-0000c4ff
	I/O window 1: 0000c800-0000c8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
this is what i got when i typed sudo lspci -v

---

### Post by ianmaxwell on 2008-12-24
> **st33med said:**
> Here ya go, follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

i'm following these instructions but keep getting errors when installing ndiswrapper. also, the page which contains the necessary drivers is a 404. what should i do? is there a simpler method of enabling my wireless?

thanks for your help guys

---

### Post by ibizatunes on 2008-12-24
Looks like you have a broadcom wireless card
01:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Subsystem: Wistron NeWeb Corp. Device 1220
Flags: bus master, fast devsel, latency 128, IRQ 10
Memory at e0000000 (32-bit, non-prefetchable) [size=8K]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

Go to system > admin > restricted drivers and see if you have enabled them there?

---

### Post by ianmaxwell on 2008-12-24
i don't see an option to click on restricted drivers in the administration section???

---

### Post by ibizatunes on 2008-12-24
sorry hardware drivers

---

### Post by ianmaxwell on 2008-12-24
i'm convinced it'll never work for me

---

### Post by ianmaxwell on 2008-12-24
> **ibizatunes said:**
> sorry hardware drivers
i've enabled the broadcom b43 driver but to no change in internet success

---

### Post by ianmaxwell on 2008-12-24
this is the error i'm getting (or part of it atleast)

/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/ian/ndiswrapper/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/ian/ndiswrapper/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ian/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [install] Error 2
ian@ian-laptop:~/ndiswrapper/ndiswrapper-1.53$ 
ian@ian-laptop:~/ndiswrapper/ndiswrapper-1.53$ 
ian@ian-laptop:~/ndiswrapper/ndiswrapper-1.53$

---

### Post by ibizatunes on 2008-12-24
have u rebooted? U may need to do a bit more funky stuff to get it to work, broadcom until very recently have offered no support to linux so wireless is not well supported.....

---

### Post by ibizatunes on 2008-12-24
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom)
may work

---

### Post by ianmaxwell on 2008-12-24
any ideas what this means?


ndiswrapper-1.53/
ndiswrapper-1.53/README
ndiswrapper-1.53/loadndisdriver.8
ndiswrapper-1.53/ndiswrapper.spec
ndiswrapper-1.53/INSTALL
ndiswrapper-1.53/ChangeLog
ndiswrapper-1.53/ndiswrapper.8
ndiswrapper-1.53/utils/
ndiswrapper-1.53/utils/ndiswrapper
ndiswrapper-1.53/utils/loadndisdriver.c
ndiswrapper-1.53/utils/ndiswrapper-buginfo
ndiswrapper-1.53/utils/Makefile
ndiswrapper-1.53/driver/
ndiswrapper-1.53/driver/mkexport.sh
ndiswrapper-1.53/driver/wrapmem.c
ndiswrapper-1.53/driver/pnp.h
ndiswrapper-1.53/driver/longlong.h
ndiswrapper-1.53/driver/rtl.c
ndiswrapper-1.53/driver/ntoskernel.c
ndiswrapper-1.53/driver/loader.h
ndiswrapper-1.53/driver/iw_ndis.c
ndiswrapper-1.53/driver/win2lin_stubs.S
ndiswrapper-1.53/driver/wrapper.c
ndiswrapper-1.53/driver/winnt_types.h
ndiswrapper-1.53/driver/wrapndis.h
ndiswrapper-1.53/driver/usb.h
ndiswrapper-1.53/driver/pe_linker.h
ndiswrapper-1.53/driver/ndis.h
ndiswrapper-1.53/driver/divdi3.c
ndiswrapper-1.53/driver/ndiswrapper.h
ndiswrapper-1.53/driver/hal.c
ndiswrapper-1.53/driver/wrapndis.c
ndiswrapper-1.53/driver/ntoskernel.h
ndiswrapper-1.53/driver/crt.c
ndiswrapper-1.53/driver/workqueue.c
ndiswrapper-1.53/driver/ntoskernel_io.c
ndiswrapper-1.53/driver/lin2win.h
ndiswrapper-1.53/driver/pnp.c
ndiswrapper-1.53/driver/loader.c
ndiswrapper-1.53/driver/ndis.c
ndiswrapper-1.53/driver/iw_ndis.h
ndiswrapper-1.53/driver/pe_linker.c
ndiswrapper-1.53/driver/wrapmem.h
ndiswrapper-1.53/driver/mkstubs.sh
ndiswrapper-1.53/driver/usb.c
ndiswrapper-1.53/driver/wrapper.h
ndiswrapper-1.53/driver/Makefile
ndiswrapper-1.53/driver/proc.c
ndiswrapper-1.53/AUTHORS
ndiswrapper-1.53/Makefile
ian@ian-laptop:~/ndiswrapper$

---

### Post by ianmaxwell on 2008-12-24
i think i'll be able to do this but i can't find the driver for my card as the web-link given in the tutorial no longer works. 
does anyone know a link to a similar list or a link to the specific driver i need?

please...

---

### Post by ianmaxwell on 2008-12-24
once again, this is the wireless controller i have

01:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by ianmaxwell on 2008-12-24
c'mon, somebody must know where to download the .inf and .sys files

---

### Post by ianmaxwell on 2008-12-24
i have the windows wireless drivers option on the administration list.
all i need to do now is find the inf and sys files right?
or no?

---

### Post by neu2buntu on 2008-12-24
in firefox goto >tools>addons>and in the search bar type: "404 not found" and install the program , hopefully the page you are looking will be archived and you can download your drivers.............oh and just search the page again in firefox after restarting the browser

---

### Post by ianmaxwell on 2008-12-24
thanks but sorry that didn't work. (useful app tho')
anyone else got ideas?

---

