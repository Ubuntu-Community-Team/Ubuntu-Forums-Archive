---
title: "IEEE802.11b+WLAN CardBus Card+driver+TROUBLE!!!"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by Capt_Zaphod on 2008-08-09
Hello,

  I installed Ubuntu today.  Much of this was fairly intuitive, as I have some basic knowledge of AIX UNIX.
  
  I can't seem to install the driver for my wireless card though.

  I downloaded a copy from Driver Guide: [http://members.driverguide.com/driver/detail.php?driverid=211797](http://members.driverguide.com/driver/detail.php?driverid=211797)

  And tried to install it.  I got an error message stating that it wasn't valid.

  Any ideas of what I can do next?

Thank you

---

### Post by Capt_Zaphod on 2008-08-10
Anyone?

Please?

I'm really stuck...

Thanks.

---

### Post by Ayuthia on 2008-08-10
Can you provide the following information from the Terminal:
```
lspci -nn
lshw -C network
```
This will help us get some information about your wireless card.

---

### Post by Capt_Zaphod on 2008-08-11
Thank you for your assistance Ayuthia, here's the results:

**lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
02:04.1 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)

**lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:80:e3:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

---

### Post by dacorr on 2008-08-11
iwconfig from terminal?

---

### Post by Capt_Zaphod on 2008-08-11
> **dacorr said:**
> iwconfig from terminal?
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

---

### Post by dacorr on 2008-08-11
there you go no wireless card installed/recognised

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L **802.11b** MAC [10ec:8180] (rev 20)

that would be the PCMCIA card as the driver you pointed to was a) PCMCIA and b) win 2000 driver.

well good news is it sees it.

Driver

[http://www.gigafast.com/products/product_drivers/WF721-AEX_drivers.htm](http://www.gigafast.com/products/product_drivers/WF721-AEX_drivers.htm)

Install with

[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

the other option is to see if the ubuntu drivers will work,

use this to confiure your wireless networks, i found it easier

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Dac

---

### Post by Capt_Zaphod on 2008-08-11
Well...I got the driver and it installed fine, and installed WicD.

It still won't connect though.  Here's the info:

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
02:04.1 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)

lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:80:e3:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 20
       serial: 00:01:36:0f:ff:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netr8180 driverversion=1.52+Realtek,03/12/2003,5.129.03 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11

---

### Post by Capt_Zaphod on 2008-08-12
Anyone else have any ideas, please?

Thank you

---

### Post by Capt_Zaphod on 2008-08-12
Drat...

---

### Post by Capt_Zaphod on 2008-09-14
Still really, really need help on this, please.

---

### Post by Capt_Zaphod on 2009-01-04
Still really, really need help on this, please.

---

