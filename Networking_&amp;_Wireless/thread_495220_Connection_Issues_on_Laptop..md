---
title: "Connection Issues on Laptop."
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Rbrewer19 on 2007-07-07
I have a Gateway MT6456 Notebook and I have recently installed Ubuntu and connect seem to detect my wireless network. I use a Linksys WRT54G V5 Router and my other laptop is running Windows XP Pro which is the laptop which I configured my router and network on.

I have tried in the Terminal using iwconfig and the result was:

lo no wireless extensions

eth0 no wireless extensions

Help please?

P.S. hardware is.

AMD Turion 64X2 Processor
1024MB DDR2 Dual Channel
ATI Radeon Xpress 1150M Graphics
802.11 Draft. N Wireless LAN
10/100 Mbps Ethernet LAN

---

### Post by fredj on 2007-07-07
Open a terminal and type 'sudo lshw -class network' (without the quote marks) and post the result here.

---

### Post by Rbrewer19 on 2007-07-07
*-network
      description: Ethernet interface
      product: 88E8038 PCI-E Fast Ethernet Controller
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@02:00.0
      logical name: eth0
      version: 14
      serial: 00:e0:b8:d3:a5:e0
      capacity: 1GB/s
      width: 64 bits
      clock: 33MHz
      capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd
100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=sky2
driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted
pair
      resources: iomemory:c0200000-c0203fff ioport:a000-a0ff irq:16
 *-network UNCLAIMED
      description: Ethernet controller
      product: Marvell Technology Group Ltd.
      vendor: Marvell Technology Group Ltd.
      physical id: 0
      bus info: pci@05:00.0
      version: 03
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list
      configuration: latency=0
      resources: iomemory:c0310000-c031ffff iomemory:c0300000-c030ffff
irq:11
 *-network
      description: AR5001-0000-0000
      product: Wireless LAN Reference Card
      vendor: Atheros Communications, Inc.
      physical id: 0
      version: 00
      slot: Socket 0
      resources: irq:20
 *-network
      description: Wireless interface
      product: AR5006X 802.11abg NIC
      vendor: Atheros Communications, Inc.
      physical id: 1
      bus info: pci@09:00.0
      logical name: wifi0
      version: 01
      serial: 00:14:a5:0d:46:dc
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master cap_list logical ethernet physical wireless
      configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (
0.9.3) ip=192.168.2.102 latency=168 maxlatency=28 mingnt=10 multicast=yes
wireless=IEEE 802.11g
      resources: iomemory:54000000-5400ffff irq:20

---

### Post by Rbrewer19 on 2007-07-07
I'd like to note in the above that is with my External card put in which works fine..however I'd like to use my internal card on the laptop. The internal card is through Marvell which should be the first card listed in that report.

---

### Post by Rbrewer19 on 2007-07-08
Just a friendly bump :)

---

### Post by Rbrewer19 on 2007-07-08
Still no luck. Did some digging and atleast have this to give:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
09:00.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)

Also whenever I log in to KDE I cannot get anything at all to connect.

---

### Post by Rbrewer19 on 2007-07-08
Ran lspci -v | less and got the following (Trying to give as much info as I can):

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
        Subsystem: Gateway 2000 Unknown device 0367
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c0200000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
        Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0310000 (32-bit, non-prefetchable) [size=64K]
        Memory at c0300000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

thats just on the section about the card. I see <access denied> on several other things as well..dont know if that means anything at all.

---

