---
title: "Not Wireless Networking --  lshw -C network - BCM4311 802.11b/g WLAN"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by FrozenLinux on 2010-07-26
I tried this [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=HowTos#Ubuntu](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=HowTos#Ubuntu) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
 and then I did the following and I still cannot get it right! What else do I need to do?

I am only using ubuntu on my Gateway Laptop now. Thank you.
 

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c3:84:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.65 latency=0 multicast=yes
       resources: irq:27 memory:d4000000-d4003fff ioport:2000(size=256)
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d6000000-d6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1c:24:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by FrozenLinux on 2010-07-26
More :

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)

---

### Post by FrozenLinux on 2010-07-26
More info about my laptop:

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
04:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
04:09.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
04:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]

---

### Post by vikas.sood on 2010-07-26
> **FrozenLinux said:**
> I tried this [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=HowTos#Ubuntu](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=HowTos#Ubuntu) and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
 and then I did the following and I still cannot get it right! What else do I need to do?

I am only using ubuntu on my Gateway Laptop now. Thank you.
 

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:c3:84:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.65 latency=0 multicast=yes
       resources: irq:27 memory:d4000000-d4003fff ioport:2000(size=256)
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:d6000000-d6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1c:24:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Check this out

[http://ubuntuforums.org/showthread.php?t=1317801](http://ubuntuforums.org/showthread.php?t=1317801)

---

### Post by lkraemer on 2010-07-26
Your problem is you are mixing and matching drivers for your Wifi.
You need to settle on one method and keep following a guide to get your
Wifi working.

From what you have posted you have Ndiswrapper and some Windows driver
installed, along with bcm43xx and ssb.

What about a decision on what method you really want?  If you are unsure,
then I'd recommend using the default drivers for Ubuntu 10.04, and
following this guide.  But, you are going to have to UN-DO (REMOVE) the
already installed Modules & Drivers.  That's not too hard, assuming you 
can read and follow directions.

REMEMBER: You can always run the LiveCD, and try the 10.04 Default Drivers
and this method before you try it on an installed version.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

lk

---

