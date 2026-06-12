---
title: "Not detecting my wireless card"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by lightofflash on 2007-10-21
I'm sure This question has been asked many times, but I lurked the forums and couldn't find much help. I'm using Ubuntu 7.04 on my Acer Aspire 5570-2067. When I googled the name for the specs, all it gave me was 10/100 BT & 802.11g. I have no clue what that means, so I don't know which driver/ if there is a driver for my laptop. Any idea how I can find out which wireless card I have, then get the correct driver?

Thanks in advance

Lightofflash

---

### Post by noob12 on 2007-10-22
You can start by posting the output of these commands
```

lspci -nn

sudo lshw -C network

```

---

### Post by lightofflash on 2007-10-22
For the first one,
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller [11ab:4352] (rev 14)
03:00.0 Ethernet controller [0200]: Atheros Communications, Inc. Unknown device [168c:001c] (rev 01)
0a:09.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0a:09.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]


And the second, 

  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:41:2a:3b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:54000000-54003fff ioport:2000-20ff irq:16
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:54100000-5410ffff irq:17

---

### Post by amphet on 2007-10-22
From your output you have an Atheros card, you need the madwifi drivers, they come in the restricted modules.

```

uname -r

```

this will bring up your kernel version

then

```

sudo apt-get install linux-restricted-modules-YOURKERNELVERSIONHERE

```

or check out this other post
[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

---

### Post by noob12 on 2007-10-22
OK.  Here's your wifi device
```

03:00.0 Ethernet controller [0200]: Atheros Communications, Inc. Unknown device [168c:001c] (rev 01)

```
which is an AR5007EG according to the madwifi site.

The **ath_pci** driver in Gutsy (7.10) says that it covers this device id (168c:001c).  There's a somewhat dated link ([http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)) out on the madwifi site (origin of this driver) that indicates it wasn't supported by the ath_hal module (hardware abstraction layer) as late as 4/28/07.

What I'd suggest is trying the Gutsy LiveCD and see if it works with that.  Otherwise you may be able to build more recent versions of the madwifi drivers and use Feisty if you must stay on Feisty.  You can also try ndiswrapper + the Windows driver on Feisty.

---

### Post by lightofflash on 2007-10-22
I tried the how-to, yet no success. Is there a way to put 7.10 on my laptop without having to order/ burn a cd?

---

### Post by noob12 on 2007-10-23
Yes if you can plug in wired you can just run the update manager.  Check for updates and you should get a button allowing you to upgrade to 7.10.

---

