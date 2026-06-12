---
title: "ndiswrapper driver installed - now what? - totally confused"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by ironfistchamp on 2006-10-21
Hey all

I am trying to get wireless internet access on my step mums laptop. It has a broadcom 4318 rev2 built in card. I used ndiswrapper to get drivers installed (as I heard the firmware method didnt work for this version). Thats all fine it says driver present, hardware present. I followed a guide on here for that actual card. Anyway, I scanned for the access point and then setup the card to use my essid and wep key. When I typed 

```

sudo dhclient eth1

```

as instructed I got this output:

```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP 

Listening on LPF/eth1/00:90:4b:e8:0c:b2
Sending on   LPF/eth1/00:90:4b:e8:0c:b2
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

In the network applet manager it will not show the wireless device. In the network settings GUI the device is setup correctly and activated but I still cannot get a connection. Also I cannot set it as my default gateway device.

Modprobe ndiswrapper yields no output. Dmesg gives this:

```

[17179569.184000] Linux version 2.6.15-27-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000 ]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f7d3800 (usable)
[ 17179569.184000]  BIOS-e820: 000000001f7d3800 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0007000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved) 
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved) 
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 503MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 128979
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0 
[17179569.184000]   Normal zone: 124883 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc970 
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d4425
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d4c00
[17179569.184000] ACPI: MADT (v001 DELL    CPi R   0x27d50b15 ASL  0x00000047) @ 0x1f7d5400 
[17179569.184000] ACPI: MCFG (v016 DELL    CPi R   0x27d50b15 ASL  0x00000061) @ 0x1f7d53c0
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030522) @ 0x1f7d4658
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030522) @ 0x1f7d445d 
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000 ] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1]) 
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23[ 17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000 ] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000) 
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1396.801 MHz processor. 
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.060000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.064000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[ 17179572.076000] Memory: 499816k/515916k available (2115k kernel code, 15520k reserved, 595k data, 332k init, 0k highmem)
[17179572.076000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.156000] Calibrating delay using timer specific routine.. 2797.61 BogoMIPS (lpj=5595238)
[17179572.156000] Security Framework v1.0.0 initialized
[17179572.156000] SELinux:  Disabled at boot.
[17179572.156000 ] Mount-cache hash table entries: 512
[17179572.156000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[17179572.156000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000 
[17179572.156000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.156000] CPU: L2 cache: 1024K
[17179572.156000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000000 00000000 00000000
[17179572.156000 ] mtrr: v2.0 (20020519)
[17179572.156000] Enabling fast FPU save and restore... done.
[17179572.156000] Enabling unmasked SIMD FPU exception support... done.
[17179572.156000] Checking 'hlt' instruction... OK.
[17179572.172000] SMP alternatives: switching to UP code
[17179572.172000] checking if image is initramfs... it is
[17179572.880000] Freeing initrd memory: 6818k freed
[17179572.896000] ACPI: Looking for DSDT ... not found! 
[17179572.900000] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179572.900000] Total of 1 processors activated (2797.61 BogoMIPS).
[17179572.900000] ENABLING IO-APIC IRQs
[17179572.900000 ] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.044000] Brought up 1 CPUs
[17179573.044000] NET: Registered protocol family 16
[17179573.044000] EISA bus registered
[17179573.044000] ACPI: bus type pci registered 
[17179573.056000] PCI: PCI BIOS revision 2.10 entry at 0xfba7e, last bus=13
[17179573.056000] PCI: Using MMCONFIG
[17179573.060000] ACPI: Subsystem revision 20051216
[17179573.080000] ACPI: Interpreter enabled 
[17179573.080000] ACPI: Using IOAPIC for interrupt routing
[17179573.080000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.080000] PCI: Probing PCI hardware (bus 00)
[17179573.080000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0 
[17179573.100000] Boot video device is 0000:00:02.0
[17179573.100000] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[17179573.100000] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[17179573.100000 ] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.100000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.100000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.120000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11) 
[17179573.120000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[17179573.124000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179573.124000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[17179573.124000 ] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.124000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.124000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
[17179573.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179573.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179573.124000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT] 
[17179573.124000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.124000] pnp: PnP ACPI init
[17179573.148000] pnp: PnP ACPI: found 10 devices
[17179573.148000] PnPBIOS: Disabled by ACPI PNP
[17179573.148000 ] PCI: Using ACPI for IRQ routing
[17179573.148000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.196000] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[17179573.196000] pnp: 00:01: ioport range 0x1000-0x1005 could not be reserved
[17179573.196000] pnp: 00:01: ioport range 0x1008-0x100f could not be reserved
[17179573.196000] pnp: 00:02: ioport range 0xf400-0xf4fe has been reserved 
[17179573.196000] pnp: 00:02: ioport range 0x1006-0x1007 has been reserved
[17179573.196000] pnp: 00:02: ioport range 0x100a-0x1059 could not be reserved
[17179573.196000] pnp: 00:02: ioport range 0x1060-0x107f has been reserved 
[17179573.196000] pnp: 00:02: ioport range 0x1080-0x10bf has been reserved
[17179573.196000] pnp: 00:02: ioport range 0x10c0-0x10df has been reserved
[17179573.196000] pnp: 00:07: ioport range 0x900-0x90f has been reserved 
[17179573.196000] pnp: 00:07: ioport range 0x910-0x91f has been reserved
[17179573.196000] pnp: 00:07: ioport range 0x920-0x92f has been reserved
[17179573.196000] pnp: 00:07: ioport range 0x930-0x93f has been reserved 
[17179573.196000] pnp: 00:07: ioport range 0x940-0x97f has been reserved
[17179573.196000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.196000] PCI: Bridge: 0000:00:1c.0
[17179573.196000]   IO window: disabled. 
[17179573.196000]   MEM window: disabled.
[17179573.196000]   PREFETCH window: disabled.
[17179573.196000] PCI: Bridge: 0000:00:1c.3
[17179573.196000]   IO window: d000-dfff
[17179573.196000]   MEM window: dfc00000-dfdfffff 
[17179573.196000]   PREFETCH window: d0000000-d01fffff
[17179573.196000] PCI: Bridge: 0000:00:1e.0
[17179573.196000]   IO window: disabled.
[17179573.196000]   MEM window: dfb00000-dfbfffff
[17179573.196000 ]   PREFETCH window: disabled.
[17179573.196000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.196000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.196000 ] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179573.196000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179573.196000] PCI: Setting latency timer of device 0000:00: 1e.0 to 64
[17179573.196000] audit: initializing netlink socket (disabled)
[17179573.196000] audit(1161452683.192:1): initialized
[17179573.196000] VFS: Disk quotas dquot_6.5.1
[17179573.196000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[17179573.196000] Initializing Cryptographic API
[17179573.196000] io scheduler noop registered
[17179573.196000] io scheduler anticipatory registered
[17179573.196000] io scheduler deadline registered
[17179573.196000 ] io scheduler cfq registered
[17179573.200000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.200000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179573.200000 ] assign_interrupt_mode Found MSI capability
[17179573.200000] Allocate Port Service[pcie00]
[17179573.200000] Allocate Port Service[pcie02]
[17179573.200000] Allocate Port Service[pcie03]
[17179573.200000] ACPI: PCI Interrupt 0000:00: 1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179573.200000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179573.200000] assign_interrupt_mode Found MSI capability
[17179573.200000] Allocate Port Service[pcie00] 
[17179573.200000] Allocate Port Service[pcie02]
[17179573.200000] Allocate Port Service[pcie03]
[17179573.200000] isapnp: Scanning for PnP cards...
[17179573.552000] isapnp: No Plug & Play device found
[17179573.572000] Real Time Clock Driver v1.12
[17179573.572000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.572000] i8042.c: Warning: Keylock active.
[17179573.576000] serio: i8042 AUX port at 0x60,0x64 irq 12 
[17179573.576000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.576000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.576000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[17179573.576000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.576000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.576000] mice: PS/2 mouse device common for all mice 
[17179573.576000] EISA: Probing bus 0 at eisa.0
[17179573.576000] Cannot allocate resource for EISA slot 1
[17179573.580000] EISA: Detected 0 cards.
[17179573.580000] NET: Registered protocol family 2
[17179573.584000 ] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.620000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.620000] TCP established hash table entries: 16384 (order: 5, 196608 bytes) 
[17179573.620000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179573.620000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.620000] TCP reno registered
[17179573.620000 ] TCP bic registered
[17179573.620000] NET: Registered protocol family 1
[17179573.620000] NET: Registered protocol family 8
[17179573.620000] NET: Registered protocol family 20
[17179573.620000] Using IPI No-Shortcut mode 
[17179573.620000] ACPI wakeup devices:
[17179573.620000]  LID PBTN PCI0 USB0 USB1 USB2 USB4 USB3 AZAL MODM PCIE RP01 RP02 RP03 RP04 RP05 RP06
[17179573.620000] ACPI: (supports S0 S3 S4 S5)
[17179573.620000] Freeing unused kernel memory: 332k freed 
[17179573.672000] vga16fb: initializing
[17179573.672000] vga16fb: mapped to 0xc00a0000
[17179573.804000] Console: switching to colour frame buffer device 80x25
[17179573.804000] fb0: VGA16 VGA frame buffer device 
[17179574.832000] Capability LSM initialized
[17179574.952000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.952000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.960000] ACPI: Thermal Zone [THM] (51 C) 
[17179575.436000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.436000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 169
[17179575.436000] ICH6: chipset revision 3
[17179575.436000 ] ICH6: not 100% native mode: will probe irqs later
[17179575.440000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:DMA
[17179575.440000] Probing IDE interface ide0...
[17179575.728000] hda: WDC WD600VE-75HDT1, ATA DISK drive 
[17179576.176000] hdb: _NEC DVD+/-RW ND-6650A, ATAPI CD/DVD-ROM drive
[17179576.232000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.512000] hda: max request size: 128KiB
[17179576.520000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100) 
[17179576.520000] hda: cache flushes supported
[17179576.520000]  hda: hda1 hda2 hda3
[17179576.572000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.572000] Uniform CD-ROM driver Revision: 3.20
[17179576.916000] usbcore: registered new driver usbfs
[17179576.916000] usbcore: registered new driver hub
[17179576.920000] USB Universal Host Controller Interface driver v2.3
[17179576.920000] ACPI: PCI Interrupt 0000:00: 1d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179576.920000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.920000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.920000] uhci_hcd 0000:00: 1d.0: new USB bus registered, assigned bus number 1
[17179576.920000] uhci_hcd 0000:00:1d.0: irq 169, io base 0x0000bf80
[17179576.920000] hub 1-0:1.0: USB hub found
[17179576.920000] hub 1-0:1.0: 2 ports detected 
[17179577.024000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 209
[17179577.024000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.024000] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[17179577.024000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.024000] uhci_hcd 0000:00:1d.1: irq 209, io base 0x0000bf60
[17179577.024000] hub 2-0:1.0: USB hub found
[17179577.024000 ] hub 2-0:1.0: 2 ports detected
[17179577.128000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 217
[17179577.128000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.128000 ] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.128000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.128000] uhci_hcd 0000:00:1d.2: irq 217, io base 0x0000bf40
[17179577.128000 ] hub 3-0:1.0: USB hub found
[17179577.128000] hub 3-0:1.0: 2 ports detected
[17179577.232000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179577.232000] PCI: Setting latency timer of device 0000:00: 1d.3 to 64
[17179577.232000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.232000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.232000] uhci_hcd 0000:00:1d.3: irq 177, io base 0x0000bf20 
[17179577.232000] hub 4-0:1.0: USB hub found
[17179577.232000] hub 4-0:1.0: 2 ports detected
[17179577.336000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 169
[17179577.336000] PCI: Setting latency timer of device 0000:00: 1d.7 to 64
[17179577.336000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.336000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.336000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.336000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.336000] ehci_hcd 0000:00:1d.7: irq 169, io mem 0xb0000000
[17179577.340000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.340000] hub 5-0:1.0: USB hub found
[17179577.340000] hub 5-0:1.0: 8 ports detected
[17179577.468000] Probing IDE interface ide1...
[17179578.048000] Attempting manual resume
[17179578.056000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[17179581.584000] ReiserFS: hda1: using ordered data mode
[17179581.608000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30 
[17179581.608000] ReiserFS: hda1: checking transaction log (hda1)
[17179581.640000] ReiserFS: hda1: Using r5 hash to sort names
[17179591.060000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.068000 ] agpgart: Detected an Intel 915GM Chipset.
[17179591.068000] agpgart: Detected 7932K stolen memory.
[17179591.088000] agpgart: AGP aperture is 256M @ 0xc0000000
[17179591.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.092000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.324000] hw_random: RNG not detected
[17179591.352000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169 
[17179591.352000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179591.720000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[17179591.812000] input: SynPS/2 Synaptics TouchPad as /class/input/input1 
[17179591.872000] input: PC Speaker as /class/input/input2
[17179592.228000] ts: Compaq touchscreen protocol output
[17179592.264000] b44.c:v0.97 (Nov 30, 2005)
[17179592.264000] ACPI: PCI Interrupt 0000:02:00.0 [A] -> GSI 18 (level, low) -> IRQ 217
[17179592.272000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:8a:9c:16
[17179592.808000] lp: driver loaded but no devices found
[17179592.856000] Adding 1574360k swap on /dev/hda3.  Priority:-1 extents:1 across:1574360k 
[17179593.904000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.904000] md: bitmap version 4.39
[17179593.920000] NET: Registered protocol family 17
[17179594.420000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179595.068000] cdrom: open failed.
[17179595.588000] kjournald starting.  Commit interval 5 seconds
[17179595.588000] EXT3 FS on hda2, internal journal 
[17179595.588000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.860000] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[17179595.908000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179595.908000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179595.916000] ndiswrapper: using irq 209
[17179597.080000] wlan0: vendor: ''
[17179597.080000 ] wlan0: ndiswrapper ethernet device 00:90:4b:e8:0c:b2 using driver bcmwl5, 14E4:4318.5.conf
[17179597.080000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 17179668.184000] ACPI: AC Adapter [AC] (on-line)
[17179668.240000] pcc_acpi: loading...
[17179668.252000] ACPI: Lid Switch [LID]
[17179668.252000] ACPI: Power Button (CM) [PBTN]
[17179668.252000] ACPI: Sleep Button (CM) [SBTN] 
[17179668.324000] ibm_acpi: ec object not found
[17179668.624000] ACPI: Battery Slot [BAT0] (battery present)
[17179668.652000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179668.652000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)[ 17179674.460000] [drm] Initialized drm 1.0.1 20051102
[17179674.484000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179674.484000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179676.000000] ppdev: user-space parallel port driver
[17179676.340000] apm: BIOS not found.
[17179680.480000] Bluetooth: Core ver 2.8
[17179680.480000] NET: Registered protocol family 31
[17179680.480000] Bluetooth: HCI device and connection manager initialized 
[17179680.480000] Bluetooth: HCI socket layer initialized
[17179680.632000] Bluetooth: L2CAP ver 2.8
[17179680.632000] Bluetooth: L2CAP socket layer initialized
[17179680.636000] Bluetooth: RFCOMM socket layer initialized 
[17179680.636000] Bluetooth: RFCOMM TTY layer initialized
[17179680.636000] Bluetooth: RFCOMM ver 1.7
[17179732.080000] NET: Registered protocol family 10
[17179732.080000] lo: Disabled Privacy Extensions
[17179732.080000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179732.080000] IPv6 over IPv4 tunneling driver
[17179742.700000] eth1: no IPv6 routers present
[17181915.076000] eth1: no IPv6 routers present
[17182502.208000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17182505.204000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17182505.204000] b44: eth0: Flow control is on for TX and on for RX.
[17182505.208000 ] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17182522.808000] eth0: no IPv6 routers present

```


I really don't know what to do now. Hope someone can help.

Ironfistchamp

---

### Post by az on 2006-10-21
Did you blacklist the native linux driver?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

### Post by ironfistchamp on 2006-10-21
Thanks for the reply yes the driver is blacklisted. Modprobe should produce an output shouldnt it?

---

### Post by az on 2006-10-21
> **ironfistchamp said:**
> Thanks for the reply yes the driver is blacklisted. Modprobe should produce an output shouldnt it?

In dmesg, yes, but there are a few lines that I don't understand.


Like: "ndiswrapper: using irq 209"

I don't know if that's right....


From the command line, a successful loading of a module will not return anything.

The device worked before?

---

### Post by ironfistchamp on 2006-10-21
This is a fresh install of Dapper. I have not tried to get a wireless card working in Linux ever. This is a total pain.

---

### Post by pjbgravely on 2006-10-21
Try installing network-manager to configure. Still Wlan should show up in the networking utility. Does the card light up? Your Dmesg output says the card is working and set as wlan0.

Paul

---

### Post by hyrulian_gamer on 2006-10-21
I'm having troubles too, pretty much the same. My wireless light does come on, but it's flashing. So it's not working.. wanna help me too? :P

---

### Post by ironfistchamp on 2006-10-22
PJ the card is built in but the light on the laptop for the card dodes not light up. Most guides say to press the fn key and wireless key but that does nothing at all. In everything but dmesg it shows up as eth1. I have installed network-manager-gnome but I am not sure how to start it.

---

### Post by alek66 on 2006-10-22
hi everyone, I just installed and set the driver for my ubuntu dapper, under amd64.
I tested the modprobe and it works fine. i want to know what to do, so that ndiswrappers, "starts" during boot?
alex

---

### Post by dabear on 2006-10-22
Hi, you would have to do a «sudo ndiswrapper -m», and if using network-manager, you would have to add ndiswrapper to /etc/modules too.

---

### Post by alek66 on 2006-10-22
> **dabear said:**
> Hi, you would have to do a «sudo ndiswrapper -m», and if using network-manager, you would have to add ndiswrapper to /etc/modules too.

I think I am not using network-manger, I used to be a kde user, y recently switched to gnome and ubuntu. So i dont know...
is there a way to confirm this so i can tell give you more information?

---

### Post by pjbgravely on 2006-10-22
> **ironfistchamp said:**
> PJ the card is built in but the light on the laptop for the card dodes not light up. Most guides say to press the fn key and wireless key but that does nothing at all. In everything but dmesg it shows up as eth1. I have installed network-manager-gnome but I am not sure how to start it.
 NetworkManager will show up in you notification area. If it doesn't make sure it is set to start in your startup programs. If it is try in a console.

```

sudo killall NetworkManager
sudo NetworkManager

```

If that doesn't work there maybe a problem with you Gnome configuration. Try creating a new user and see if it shows up in that users login. 

I wouldn't worry about the eth1/wlan0 difference unless it doesn't show up in Networking. To make NetworkManager work you have to disable all devices in Networking first.

Paul

---

