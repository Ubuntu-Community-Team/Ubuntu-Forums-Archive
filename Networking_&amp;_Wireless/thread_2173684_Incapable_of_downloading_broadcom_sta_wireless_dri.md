---
title: "Incapable of downloading broadcom sta wireless driver"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by innocent-devil85 on 2013-09-10
So far I've tried uninstalling and reinstalling that bwmrl kernel source package via terminal. I also tried instaling ndiswrapper and I'm still not sure if I did that correctly. I searched for how to videos and posts regarding this topic; Almost all of them have been telling me to do the same thing. I've also looked at numerouse step by step guides and they haven't been much help either. I have a bcm 4322. Please understand that I am brand new and I need you to simplify everything and not assume that I understand any jargon relating to command lines or whatever. Can someone please help me? Some useful information I have a macbook pro (snow leopard). 
I thought this would be helpful as well :P

```
00:00.0 Host bridge [0600]: NVIDIA Corporation MCP89 HOST Bridge [10de:0d60] (rev a1)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.1 RAM memory [0500]: NVIDIA Corporation MCP89 Memory Controller [10de:0d68] (rev a1)
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:01.0 RAM memory [0500]: NVIDIA Corporation Device [10de:0d6d] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.1 RAM memory [0500]: NVIDIA Corporation Device [10de:0d6e] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.2 RAM memory [0500]: NVIDIA Corporation Device [10de:0d6f] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:01.3 RAM memory [0500]: NVIDIA Corporation Device [10de:0d70] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.0 RAM memory [0500]: NVIDIA Corporation Device [10de:0d71] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:02.1 RAM memory [0500]: NVIDIA Corporation Device [10de:0d72] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.0 ISA bridge [0601]: NVIDIA Corporation MCP89 LPC Bridge [10de:0d80] (rev a2)
    Subsystem: Apple Inc. Device [106b:cb89]
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: I/O ports at 2100 [size=256]

00:03.1 RAM memory [0500]: NVIDIA Corporation MCP89 Memory Controller [10de:0d7b] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.2 SMBus [0c05]: NVIDIA Corporation MCP89 SMBus [10de:0d79] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 15
    Region 0: I/O ports at 2000 [size=256]
    Region 4: I/O ports at 2240 [size=64]
    Region 5: I/O ports at 2200 [size=64]
    Capabilities: <access denied>

00:03.3 RAM memory [0500]: NVIDIA Corporation MCP89 Memory Controller [10de:0d69] (rev a1)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.4 Co-processor [0b40]: NVIDIA Corporation MCP89 Co-Processor [10de:0d7a] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 14
    Region 0: Memory at d3400000 (32-bit, non-prefetchable) [size=512K]

00:04.0 USB controller [0c03]: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller [10de:0d9c] (rev a1) (prog-if 10 [OHCI])
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at d348a000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 USB controller [0c03]: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller [10de:0d9d] (rev a2) (prog-if 20 [EHCI])
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at d348b100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:06.0 USB controller [0c03]: NVIDIA Corporation MCP89 OHCI USB 1.1 Controller [10de:0d9c] (rev a1) (prog-if 10 [OHCI])
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at d3489000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:06.1 USB controller [0c03]: NVIDIA Corporation MCP89 EHCI USB 2.0 Controller [10de:0d9d] (rev a2) (prog-if 20 [EHCI])
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin B routed to IRQ 17
    Region 0: Memory at d348b000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:08.0 Audio device [0403]: NVIDIA Corporation MCP89 High Definition Audio [10de:0d94] (rev a2)
    Subsystem: NVIDIA Corporation Device [10de:cb89]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d3480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:0a.0 IDE interface [0101]: NVIDIA Corporation MCP89 SATA Controller [10de:0d85] (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: Apple Inc. Device [106b:cb89]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 2298 [size=8]
    Region 1: I/O ports at 22a4 [size=4]
    Region 2: I/O ports at 2290 [size=8]
    Region 3: I/O ports at 22a0 [size=4]
    Region 4: I/O ports at 2280 [size=16]
    Region 5: Memory at d3484000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ata_generic
    Kernel modules: pata_acpi, ahci

00:0b.0 RAM memory [0500]: NVIDIA Corporation Device [10de:0d75] (rev a1)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 0
    Region 0: Memory at d3488000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

00:0e.0 PCI bridge [0604]: NVIDIA Corporation Device [10de:0d9a] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: d3300000-d33fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:15.0 PCI bridge [0604]: NVIDIA Corporation Device [10de:0d9b] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: d3200000-d32fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 PCI bridge [0604]: NVIDIA Corporation Device [10de:0d9b] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: d3100000-d31fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:17.0 PCI bridge [0604]: NVIDIA Corporation MCP89 PCI Express Bridge [10de:0d76] (rev a1) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: d2000000-d30fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

01:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW643 [TrueFire] PCIe 1394b Controller [11c1:5901] (rev 08) (prog-if 10 [OHCI])
    Subsystem: LSI Corporation FW643 [TrueFire] PCIe 1394b Controller [11c1:5900]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at d3300000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at d3200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: ssb

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 44
    Region 0: Memory at d3100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

04:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:08a0] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Apple Inc. Device [106b:00c2]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 1000 [size=128]
    [virtual] Expansion ROM at d3000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_319, nvidia_304_updates, nvidia_319_updates, nvidia_304, nouveau, nvidiafb
```

---

### Post by varunendra on 2013-09-11
Hi, Welcome to the forums !

First and foremost, please edit your above post to wrap the whole output part within 'Code' tags. It is scaring me in its current form :P
Follow the "Using Code Tags" link in my signature below to see how to use it.

About your card - I believe the driver package bcmwl-kernel-source should have fixed the issue, but seems you have tried quite a few things by now. There may possibly be a conflict situation at the moment, or some other issue. We need to see a detailed report to see the overall status.

Accordingly, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post to download and run the script and post back the report it generates. Thanks.

---

### Post by innocent-devil85 on 2013-09-11
Hopefully I did this one correctly, sorry about my previous post. 

```

*************** info trace ***************

***** uname -a *****

Linux mia-MacBookPro 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel modules: ssb
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3
    Kernel modules: tg3

***** lsusb *****

Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. 

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search hsd1.wa.comcast.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****


****************** done ******************

```

---

### Post by varunendra on 2013-09-11
> **innocent-devil85 said:**
> Hopefully I did this one correctly..
Yes you did, and no problems with the previous one, most newcomers don't know about that. However, you can still edit it to wrap it up. I could request a mod, but thought it'd be a good practice for you. :)

Onto the problem -
I don't want to make a simple thing sound complex, but your system state really seems to have been messed up. I'm wondering how you managed to do that :P -
> **innocent-devil85 said:**
> 
```

***** lspci *****

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel modules: **[COLOR="#FF0000"]ssb[/COLOR]**
....
....
***** lsmod *****
[COLOR="#FF0000"]????[/COLOR]
....
....
***** blacklist *****

[**[COLOR="#FF0000"]/etc/modprobe.d/blacklist-bcm43.conf[/COLOR]**]
blacklist b43
....
....
***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/ssb0:0 (**[COLOR="#FF0000"]b43-pci-bridge[/COLOR]**)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="**[COLOR="#FF0000"]wlan0[/COLOR]**"

```


Some of the highlighted parts above (blacklist part) suggest that you successfully attempted installation of the bcmwl-kernel-source package,
some (udev rules part) suggest probably not, and/or you uninstalled it 'successfully',
yet some ("Kernel module" lspci part) makes no sense at all, but this one may be my lack of experience.

Anyway, let's start with fixing -

Please do -
```
sudo apt-get purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo depmod -a
sudo modprobe -v b43
```

One or more of the above commands will return errors. Post back which one(s), as well as the error messages.

Does the last command make your wifi active? If not, post back the output of -
```
dmesg | grep b43
```

And lastly, do you have a wired connection available on the system? So that we can make things easier.

---

### Post by innocent-devil85 on 2013-09-12
DISCLAIMER: I posted all the code results even if it didn't have any errors

so this is Part 1 
```
mia@mia-MacBookPro:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for mia: 
Sorry, try again.
[sudo] password for mia: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,274 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174030 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic
mia@mia-MacBookPro:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mia@mia-MacBookPro:~$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory
mia@mia-MacBookPro:~$ sudo depmod -a
mia@mia-MacBookPro:~$ sudo modprobe -v b43
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko 
```

Part 2 
```
mia@mia-MacBookPro:~$ dmesg | grep b43
[  285.595938] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[  285.636211] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[  285.892149] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[  286.660049] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
```

wired connection works fine, and when i try to connect to my wireless it just scans the available networks, says it connected but i'm still unable to get on the internet wirelessly. :-k

---

### Post by innocent-devil85 on 2013-09-12
IT WORKS!....IT FINALLY WORKED, thank youuuuuuuuuuu! :guitar:

---

### Post by varunendra on 2013-09-12
> **innocent-devil85 said:**
> IT WORKS!....IT FINALLY WORKED, thank youuuuuuuuuuu! :guitar:

Awesome !

Although I wasn't expecting it to get solved yet, because this card works only 'partially' with the b43 driver that you are using now. 'Partially' probably means that it can't support the card's full capability.

As such, I was expecting to install the sta driver (that you just uninstalled) again, properly this time, and look closely if any errors occur during its installation. We have noticed recently that this default sta driver fails to build on some systems, most probably the very cause of your problems. In that case, there are a few remedies we could try.

However, as long as the current one is working fine, enjoy it. :)

If it suffers any problems again, or doesn't perform satisfactorily, don't hesitate to post back and we can try the other things.

---

### Post by innocent-devil85 on 2013-09-12
i spoke too soon, it reverted back to its prior condition :(. My sound isn't working properly either.

---

### Post by varunendra on 2013-09-12
Well, a total blackout is also something I didn't expect. But let's move onto the obvious step..

While being connected to internet via cable, please do -
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install bcmwl-kernel-source
```

Post if there are any errors reported with the first two commands. Post back the entire output of the third one anyway.

---

### Post by innocent-devil85 on 2013-09-12
```
mia@mia-MacBookPro:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,344 kB of archives.
After this operation, 4,274 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 173965 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-30-generic
Building for architecture x86_64
Building initial module for 3.8.0-30-generic
Error! Bad return status for module build on kernel: 3.8.0-30-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic

```

---

### Post by varunendra on 2013-09-12
> **innocent-devil85 said:**
> ```

Building initial module for 3.8.0-30-generic
**[COLOR="#FF0000"]Error! Bad return status for module build on kernel: 3.8.0-30-generic (x86_64)[/COLOR]**
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
**[COLOR="#FF0000"]FATAL: Module wl not found.[/COLOR]**

```

Exactly what I suspected ^^.

Make sure the essential packages required to build a module are installed on the system. To ensure that, while being connected to internet, please do -
```
sudo apt-get install --reinstall linux-headers-generic build-essential
```

Then try installing the default package again (we're just giving it yet another chance, although it'll most certainly fail again) -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```
Closely observe the outputs and **if the second command returns the same build error as highlighted above**, do the following -

Purge the current (failed) one again -
```
sudo apt-get purge bcmwl-kernel-source
```

Download the newer version (bcmwl-kernel-source_6.30.223.30+bdcom-0ubuntu3_amd64.deb) from [launchpad page]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504").

Double-click it to install. Ubuntu Software Center should open up and install it. After the installation is finished, reboot and check which modules are loaded -
```
lsmod | egrep 'wl|b43'
```
It should only show "wl", not b43.

Does the internet work now? How good?

---

### Post by innocent-devil85 on 2013-09-12
Ok, the internet is working great, it says wl;However, my sound is not working #-o

---

### Post by innocent-devil85 on 2013-09-12
Problem solved, i realized now that this was the wrong category to post that particular problem. Thank you regardless

---

### Post by varunendra on 2013-09-12
> **innocent-devil85 said:**
> Ok, the internet is working great, it says wl;However, my sound is not working #-o

Hope the Internet part stays great this time, so that you can be sure and comfortable enough to mark the topic [SOLVED] again :)

As you already figured out, you should start a new thread in [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334") section of the forums. Read the "[Sound troubleshooting]("http://ubuntuforums.org/showthread.php?t=1885240")" sticky there before posting, maybe you won't need to post then.

Sound issues are mostly beyond my knowledge, so I may not offer any significant help there. But I'm sure there are many who can.

Thanks for the feedback and Good Luck for the sound issue..

**PS:**
Would be great if you can also confirm which one worked - the default one or the one downloaded from launchpad.

---

