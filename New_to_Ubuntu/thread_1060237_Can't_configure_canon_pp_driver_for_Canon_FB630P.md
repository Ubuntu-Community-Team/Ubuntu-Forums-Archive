---
title: "Can't configure canon_pp driver for Canon FB630P"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by llogan on 2009-02-04
Hi,

First I'd like to say what a joy Ubuntu 8.10 is!  I am a Linux newbie and Intrepid has been working hassle-free ever since I installed it about a month ago.

I am now tryng to get my Canon FB630P flatbed scanner working.  'scanimage -L' doesn't detect my scanner.  So I went to the Sane Project, discovered that the Canon FB630P is supported, and downloaded the appropriate driver for my scanner (canon_pp).  My problem is that I can't get the driver to configure.  

llogan@alpha:~/Scan/scan-6.0-2$ sudo ./configure
[sudo] password for llogan: 
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for ieee1284_wait_status in -lieee1284... no
Get the latest libieee1284 from [http://cyberelk.net/tim/data/libieee1284/](http://cyberelk.net/tim/data/libieee1284/)
configure: error: FATAL: Failed to find required libieee1284 version (0.1.5 or newer).

It can't seem to find 'libieee1284', yet:

llogan@alpha:~$ locate libieee1284
/usr/lib/libieee1284.so.3
/usr/lib/libieee1284.so.3.2.2
/usr/share/doc/libieee1284-3
/usr/share/doc/libieee1284-3/README
/usr/share/doc/libieee1284-3/TODO
/usr/share/doc/libieee1284-3/changelog.Debian.gz
/usr/share/doc/libieee1284-3/changelog.gz
/usr/share/doc/libieee1284-3/copyright
/var/cache/apt/archives/libieee1284-3_0.2.11-4_i386.deb
/var/lib/dpkg/info/libieee1284-3.list
/var/lib/dpkg/info/libieee1284-3.md5sums
/var/lib/dpkg/info/libieee1284-3.postinst
/var/lib/dpkg/info/libieee1284-3.postrm
/var/lib/dpkg/info/libieee1284-3.shlibs

Can anyone tell me what I can do to move forward with this? I've been googling all the keywords for days with no luck. Any comments, suggestions or advice would be greatly appreciated.

---

### Post by petervk on 2009-02-04
try installing the -dev package for libieee1284-3

```
sudo apt-get install libieee1284-3-dev
```

For ubuntu/debian if you ever trying to compile something you usuallly need the -dev version of the dependancies. The non -dev version only includes the already compiled files and not the headers/source the application needs to compile.

---

### Post by llogan on 2009-02-04
Thanks for the quick reply, Peter. I was able to ./configure, make, install the canon_pp driver.  Unfortunately, Intrepid still can't see my scanner.  Any suggestions?  (Should I repost this as a new question?)

---

### Post by petervk on 2009-02-04
There is a README file in the tar archive. Did you follow it's directions for use?

---

### Post by llogan on 2009-02-05
Hi,

Thanks again for your help.  Yes, I read the READMEs and made the necessary changes to /etc/sane.d/canon_pp.conf and /etc/sane.d/dll.conf.  I have tried it with 'force nibble' both commented and uncommented.  I try both 'scanimage -L' and 'xsane'as root (so I know it's not a permissions issue) and am told that no scanner is detected.  But when I run both 'scanimage -L' and 'xsane', my scanner makes a sound like the reader head (?) is moving and it is beginning to scan.  This lasts about two seconds then nothing.  I've uninstalled Xsane and disconnected my scanner and then reinstalled/reconnected and ran 'dmesg | grep port' and recieved... 

llogan@alpha:~$ sudo dmesg | grep port
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.427713] ACPI: (supports S0 S1 S4 S5)
[    0.434957] pci 0000:00:01.0: supports D1
[    0.435017] PCI: 0000:00:10.0 reg 20 io port: [e400, e41f]
[    0.435039] pci 0000:00:10.0: supports D1
[    0.435041] pci 0000:00:10.0: supports D2
[    0.435045] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435093] PCI: 0000:00:10.1 reg 20 io port: [e800, e81f]
[    0.435115] pci 0000:00:10.1: supports D1
[    0.435118] pci 0000:00:10.1: supports D2
[    0.435120] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435168] PCI: 0000:00:10.2 reg 20 io port: [ec00, ec1f]
[    0.435189] pci 0000:00:10.2: supports D1
[    0.435192] pci 0000:00:10.2: supports D2
[    0.435194] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435264] pci 0000:00:10.3: supports D1
[    0.435266] pci 0000:00:10.3: supports D2
[    0.435268] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435402] PCI: 0000:00:11.1 reg 20 io port: [fc00, fc0f]
[    0.435455] PCI: 0000:00:11.5 reg 10 io port: [e000, e0ff]
[    0.435495] pci 0000:00:11.5: supports D1
[    0.435497] pci 0000:00:11.5: supports D2
[    0.435529] PCI: 0000:00:12.0 reg 10 io port: [dc00, dcff]
[    0.435571] pci 0000:00:12.0: supports D1
[    0.435573] pci 0000:00:12.0: supports D2
[    0.435576] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.435667] pci 0000:01:00.0: supports D1
[    0.435669] pci 0000:01:00.0: supports D2
[    0.453640] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.460302] system 00:05: ioport range 0x295-0x296 has been reserved
[    0.460307] system 00:05: ioport range 0x3f0-0x3f1 has been reserved
[    0.460311] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.460315] system 00:05: ioport range 0x400-0x40f has been reserved
[    0.460318] system 00:05: ioport range 0x800-0x87f has been reserved
[    0.495834] bus: 00 index 0 io port: [0, ffff]
[    1.768606] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.773865] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.773876] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.071443] hub 1-0:1.0: 6 ports detected
[    3.277688] hub 2-0:1.0: 2 ports detected
[    3.485300] hub 3-0:1.0: 2 ports detected
[    3.694234] hub 4-0:1.0: 2 ports detected
[    4.505430] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.505660] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.732173] parport_pc 00:03: reported by Plug and Play ACPI
[   17.732273] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   23.367942] lp0: using parport0 (interrupt-driven).
[   28.586753] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   28.943388] ppdev: user-space parallel port driver
[  177.880152] Somebody wants the port
[  183.916162] Somebody wants the port
[  183.948155] Somebody wants the port

...and least the last three lines look promising.  Anything else you could suggest?  I have googled similiar scanning problems, including Ubuntu forums, and have not found a solution.  Any advice, suggestions or comments would be appreciated.

---

### Post by llogan on 2009-02-05
Hi, 

Update: I power cycled and rebooted and ran 'scan -C'...

llogan@alpha:~/Scan/scan-6.0-2$ sudo scan -C
[sudo] password for llogan: 
Canon CanoScan(tm) Scanner Driver 6.00. Copyright (C) 2001 Simon Krix et al.
This driver comes with ABSOLUTELY NO WARRANTY; for details
please see [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html)
This is free software, and you are welcome to redistribute
it under certain conditions.
See the GNU General Public License for details.

Finding IEEE1284 ports...
    parport0 (0x378): <raw><cpt><nbl><byt><ecp><swe><irq><dma>... OK (ecp).

Detecting scanner:
Scanner not ready (0xb). Attempting to reset...
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 2 (0x03 in 0x1f) - Status = 0x1f
Timeout: Scanner wakeup reply 1 (0x03 in 0x1f) - Status = 0x1f
Had to reset scanner, waiting for the head to get back.
 ID:	"CANON   IX-06075E       1.00"
 Model:	FB630P   (600x600dpi,  5104x7016 pixels)
Calibrating 5104x6 pixels calibration image (38280 bytes each scan).
Step 1/3: Calibrating black level...
  * Black scan number 1/3.

		...and it just hung like this for over an hour. I didn't hear the scanner calibrating or see any light so I did 'CTL-C'.  At least it's progess!

---

### Post by llogan on 2009-02-11
Hi,

I decided to give up on the CanoScan FB60P and pick up an inexpensive HP ScanJet G3010 ($50 Cdn new).  Worked just fine after downloading and configuring the proper driver from the SANE Project. The ScanJet just wasn't worth the hassle...

---

