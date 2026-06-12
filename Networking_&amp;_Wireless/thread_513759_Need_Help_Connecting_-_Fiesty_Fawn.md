---
title: "Need Help Connecting - Fiesty Fawn"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by TheManOfSeveralHats on 2007-07-30
Hello, 

I just upgraded from Ubuntu 6.06 Dapper to Ubuntu 7.04 Fiesty.

When I first installed Dapper, it located my wireless network card, but when I upgraded to Fiesty it was not on the list of available connections and could not be located.

Is it a driver problem, or somthing else?

Please help and Thanks ;D!

P.S: If I need anything that came with the Wireless Card, like CDs or somthing, I know longer have those.

---

### Post by kevdog on 2007-07-30
What type of network card do you have?? If you could list the following it would be of great help:

lspci -nn
lshw -C network

---

### Post by TheManOfSeveralHats on 2007-07-31
All I know is that:
Linksys Wireless-B Model No WPC11

---

### Post by kevdog on 2007-07-31
Great, but if you could post the info above, that would help me a lot!

---

### Post by TheManOfSeveralHats on 2007-07-31
When I entered lspci -nn I got:
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)


When I got lshw -C network I got:

  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b0:15:dc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:fcffe000-fcffffff irq:7
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@03:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:f8000000-f80001ff irq:11

---

### Post by TheManOfSeveralHats on 2007-07-31
Sorry for the Double Post but I really need help, without it I wont be able to connect to the internet and then there will be no point in the upgrade

---

### Post by noob12 on 2007-07-31
In Feisty the r818x driver is blacklisted by default because it triggers a kernel bug.  See the comment in **/etc/modprobe.d/blacklist**.

I'd recommend using the Windows driver with ndiswrapper.  There is a generic HOWTO at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).  If you need help navigating that people on the forum can guide you through.

---

### Post by kevdog on 2007-07-31
I believe actually the wirless card is a broadcom, not a realtek, but the solution is the same.  You need to install ndiswrapper and find the winxp drivers for your card.  Please post back if you need instructions.

---

### Post by noob12 on 2007-07-31
Note two interfaces.  It looks like he's talking about the wireless one (UNCLAIMED).  The wired Broadcom seems to be bound with b44 already.  The Wireless is Realtek RTL8180L 802.11b.

---

### Post by TheManOfSeveralHats on 2007-07-31
Thank you all, im going to look at the HOWTO, if I still have problems Ill reply back.

EDIT: Thank You All, The HOWTO really helped and now its working.

---

### Post by kevdog on 2007-07-31
Yea you are right about the realtek.  Guess thats what happens when I try to blow through too many posts at once.  Basically you want ndiswrapper and the Win98 driver for the wireless card to make this work.

---

