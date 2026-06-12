---
title: "Toshiba, Atheros, wifi problem"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by STMan on 2006-08-14
Hi
I have problem with Toshiba Satellite A105-a2141, this is my log: 
iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

lspci -v | grep Ethernet
> 
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
0000:0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

sudo lshw -C network
> 
*-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:d0100000-d010ffff irq:233
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0b:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:45:2c:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driververs ion=0.9.27 duplex=full ip=192.168.1.107 link=yes multicast=yes port=MII speed=10 0MB/s
       resources: ioport:a000-a0ff iomemory:d0200000-d02000ff irq:58

uname -r
[quote]
2.6.15-26-386
[/quute]
I have a  linux-restricted-modules-2.6.15-26-386 ver. 2.6.15.11-3

I cant use my wifi card, pls help me 
thanks for any help

---

### Post by STMan on 2006-08-15
plis, help me

---

### Post by STMan on 2006-08-17
I think, that this problem is not hart ;)

---

### Post by tturrisi on 2006-08-17
It appears that the madwifi driver is not loading, post the contents of this file:  /var/log/dmesg

---

### Post by STMan on 2006-08-20
> 
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[17179569.184000]  BIOS-e820: 000000001be80000 - 000000001be93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001be93000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7e30
[17179569.184000] On node 0 totalpages: 114304
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110208 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f7d80
[17179569.184000] ACPI: RSDT (v001 TOSINV   RSDT   0x06040000  LTP 0x00000000) @ 0x1be8d7e5
[17179569.184000] ACPI: FADT (v001 TOSINV Bonefish 0x06040000 ATI  0x000f4240) @ 0x1be92f00
[17179569.184000] ACPI: MADT (v001 TOSINV 	 APIC   0x06040000  LTP 0x00000000) @ 0x1be92f74
[17179569.184000] ACPI: MCFG (v001 TOSINV   MCFG   0x06040000  LTP 0x00000000) @ 0x1be92fc4
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x1be8dd52
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x1be8d81d
[17179569.184000] ACPI: DSDT (v001 TOSINV    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:c4000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1463.377 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.792000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.792000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.804000] Memory: 442668k/457216k available (1976k kernel code, 13904k reserved, 606k data, 288k init, 0k highmem)
[17179572.804000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.884000] Calibrating delay using timer specific routine.. 2932.17 BogoMIPS (lpj=5864350)
[17179572.884000] Security Framework v1.0.0 initialized
[17179572.884000] SELinux:  Disabled at boot.
[17179572.884000] Mount-cache hash table entries: 512
[17179572.884000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179572.884000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179572.884000] monitor/mwait feature present.
[17179572.884000] using mwait in idle threads.
[17179572.884000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.884000] CPU: L2 cache: 1024K
[17179572.884000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 0000c109 00000000 00000000
[17179572.884000] mtrr: v2.0 (20020519)
[17179572.884000] CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[17179572.884000] Enabling fast FPU save and restore... done.
[17179572.884000] Enabling unmasked SIMD FPU exception support... done.
[17179572.884000] Checking 'hlt' instruction... OK.
[17179572.900000] checking if image is initramfs... it is
[17179573.628000] Freeing initrd memory: 6625k freed
[17179573.664000] ACPI: Looking for DSDT ... not found!
[17179574.312000] ENABLING IO-APIC IRQs
[17179574.312000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179574.456000] NET: Registered protocol family 16
[17179574.456000] EISA bus registered
[17179574.456000] ACPI: bus type pci registered
[17179574.464000] PCI: PCI BIOS revision 2.10 entry at 0xfd5c4, last bus=13
[17179574.464000] PCI: Using MMCONFIG
[17179574.464000] ACPI: Subsystem revision 20051216
[17179574.468000] ACPI: Interpreter enabled
[17179574.468000] ACPI: Using IOAPIC for interrupt routing
[17179574.468000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.468000] PCI: Probing PCI hardware (bus 00)
[17179574.500000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179574.500000] Boot video device is 0000:01:05.0
[17179574.500000] PCI: Transparent bridge - 0000:00:14.4
[17179574.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[17179574.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[17179574.504000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[17179574.504000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179574.504000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179574.504000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179574.504000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179574.504000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179574.508000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179574.508000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179574.508000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179574.508000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[17179574.556000] ACPI: Embedded Controller [EC0] (gpe 7) interrupt mode.
[17179574.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179574.556000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179574.556000] ACPI: Power Resource [PFA1] (off)
[17179574.556000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.556000] pnp: PnP ACPI init
[17179574.588000] pnp: PnP ACPI: found 9 devices
[17179574.588000] PnPBIOS: Disabled by ACPI PNP
[17179574.588000] PCI: Using ACPI for IRQ routing
[17179574.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.588000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[17179574.588000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[17179574.588000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[17179574.588000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[17179574.616000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[17179574.616000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[17179574.616000] pnp: 00:07: ioport range 0x400-0x401 has been reserved
[17179574.616000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179574.616000] PCI: Bridge: 0000:00:01.0
[17179574.616000]   IO window: 9000-9fff
[17179574.616000]   MEM window: d0000000-d00fffff
[17179574.616000]   PREFETCH window: d8000000-dfffffff
[17179574.616000] PCI: Bridge: 0000:00:04.0
[17179574.616000]   IO window: disabled.
[17179574.616000]   MEM window: d0100000-d01fffff
[17179574.616000]   PREFETCH window: disabled.
[17179574.616000] PCI: Bridge: 0000:00:06.0
[17179574.616000]   IO window: disabled.
[17179574.616000]   MEM window: disabled.
[17179574.616000]   PREFETCH window: disabled.
[17179574.616000] PCI: Bridge: 0000:00:07.0
[17179574.616000]   IO window: disabled.
[17179574.616000]   MEM window: disabled.
[17179574.616000]   PREFETCH window: disabled.
[17179574.616000] PCI: Bus 12, cardbus bridge: 0000:0b:06.0
[17179574.616000]   IO window: 0000a400-0000a4ff
[17179574.616000]   IO window: 0000a800-0000a8ff
[17179574.616000]   PREFETCH window: 20000000-21ffffff
[17179574.616000]   MEM window: 24000000-25ffffff
[17179574.616000] PCI: Bridge: 0000:00:14.4
[17179574.616000]   IO window: a000-afff
[17179574.616000]   MEM window: d0200000-d02fffff
[17179574.616000]   PREFETCH window: 20000000-21ffffff
[17179574.616000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179574.616000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179574.616000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179574.616000] PCI: Enabling device 0000:0b:06.0 (0000 -> 0003)
[17179574.616000] ACPI: PCI Interrupt 0000:0b:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179574.616000] audit: initializing netlink socket (disabled)
[17179574.616000] audit(1156122696.616:1): initialized
[17179574.616000] VFS: Disk quotas dquot_6.5.1
[17179574.616000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.616000] Initializing Cryptographic API
[17179574.616000] io scheduler noop registered
[17179574.616000] io scheduler anticipatory registered
[17179574.616000] io scheduler deadline registered
[17179574.616000] io scheduler cfq registered
[17179574.616000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179574.616000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
[17179574.616000] assign_interrupt_mode Found MSI capability
[17179574.616000] Allocate Port Service[pcie00]
[17179574.616000] Allocate Port Service[pcie01]
[17179574.616000] Allocate Port Service[pcie03]
[17179574.616000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179574.616000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[17179574.620000] assign_interrupt_mode Found MSI capability
[17179574.620000] Allocate Port Service[pcie00]
[17179574.620000] Allocate Port Service[pcie01]
[17179574.620000] Allocate Port Service[pcie03]
[17179574.620000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179574.620000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[17179574.620000] assign_interrupt_mode Found MSI capability
[17179574.620000] Allocate Port Service[pcie00]
[17179574.620000] Allocate Port Service[pcie01]
[17179574.620000] Allocate Port Service[pcie03]
[17179574.620000] isapnp: Scanning for PnP cards...
[17179574.976000] isapnp: No Plug & Play device found
[17179574.992000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179574.992000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.996000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.996000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.996000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.996000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.996000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.996000] mice: PS/2 mouse device common for all mice
[17179574.996000] EISA: Probing bus 0 at eisa.0
[17179574.996000] Cannot allocate resource for EISA slot 1
[17179574.996000] Cannot allocate resource for EISA slot 8
[17179574.996000] EISA: Detected 0 cards.
[17179574.996000] NET: Registered protocol family 2
[17179575.036000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179575.036000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.036000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.036000] TCP: Hash tables configured (established 16384 bind 16384)
[17179575.036000] TCP reno registered
[17179575.036000] TCP bic registered
[17179575.036000] NET: Registered protocol family 1
[17179575.036000] NET: Registered protocol family 8
[17179575.036000] NET: Registered protocol family 20
[17179575.036000] Using IPI Shortcut mode
[17179575.036000] ACPI wakeup devices: 
[17179575.036000]  LID  PB2  PB3  PB4  PB6  PB7 OHC1 OHC2 EHCI  P2P AUDO MODM AZLA 
[17179575.036000] ACPI: (supports S0 S3 S4 S5)
[17179575.036000] Freeing unused kernel memory: 288k freed
[17179575.036000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.084000] vga16fb: initializing
[17179575.084000] vga16fb: mapped to 0xc00a0000
[17179575.180000] Console: switching to colour frame buffer device 80x25
[17179575.180000] fb0: VGA16 VGA frame buffer device
[17179576.244000] Capability LSM initialized
[17179576.372000] ACPI: Fan [FAN1] (off)
[17179576.376000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.376000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179576.588000] ACPI: Thermal Zone [TZCR] (56 C)
[17179577.040000] SCSI subsystem initialized
[17179577.044000] ACPI: bus type scsi registered
[17179577.044000] libata version 1.20 loaded.
[17179577.044000] sata_sil 0000:00:12.0: version 0.9
[17179577.044000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179577.044000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 225
[17179577.044000] ata1: SATA max UDMA/100 cmd 0xDC874080 ctl 0xDC87408A bmdma 0xDC874000 irq 225
[17179577.044000] ata2: SATA max UDMA/100 cmd 0xDC8740C0 ctl 0xDC8740CA bmdma 0xDC874008 irq 225
[17179577.412000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7f69 84:6063 85:f469 86:3d49 87:6063 88:203f 93:0000
[17179577.412000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179577.412000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdb7eca80
[17179577.460000] ata1: dev 0 configured for UDMA/100
[17179577.460000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdb7eca80
[17179577.508000] scsi0 : sata_sil
[17179577.712000] ata2: no device found (phy stat 00000000)
[17179577.712000] scsi1 : sata_sil
[17179577.712000]   Vendor: ATA       Model: HTS541080G9SA00   Rev: MB4O
[17179577.712000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179577.716000] Driver 'sd' needs updating - please use bus_type methods
[17179577.716000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179577.716000] SCSI device sda: drive cache: write back
[17179577.720000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179577.720000] SCSI device sda: drive cache: write back
[17179577.720000]  sda: sda1 sda2 sda3 sda4
[17179577.760000] sd 0:0:0:0: Attached scsi disk sda
[17179578.124000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179578.124000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 233
[17179578.124000] ATIIXP: chipset revision 128
[17179578.124000] ATIIXP: not 100% native mode: will probe irqs later
[17179578.124000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
[17179578.124000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179578.124000] Probing IDE interface ide0...
[17179578.692000] Probing IDE interface ide1...
[17179579.428000] hdc: DVD/CDRW UJDA770, ATAPI CD/DVD-ROM drive
[17179579.764000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.772000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.772000] Uniform CD-ROM driver Revision: 3.20
[17179579.852000] usbcore: registered new driver usbfs
[17179579.856000] usbcore: registered new driver hub
[17179579.856000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 50
[17179579.856000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.856000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[17179579.856000] ehci_hcd 0000:00:13.2: irq 50, io mem 0xd0506000
[17179579.856000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.856000] hub 1-0:1.0: USB hub found
[17179579.856000] hub 1-0:1.0: 8 ports detected
[17179579.920000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.920000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 50
[17179579.920000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179579.960000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[17179579.960000] ohci_hcd 0000:00:13.0: irq 50, io mem 0xd0504000
[17179579.968000] hub 2-0:1.0: USB hub found
[17179579.968000] hub 2-0:1.0: 4 ports detected
[17179580.072000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 50
[17179580.072000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179580.072000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179580.072000] ohci_hcd 0000:00:13.1: irq 50, io mem 0xd0505000
[17179580.080000] hub 3-0:1.0: USB hub found
[17179580.080000] hub 3-0:1.0: 4 ports detected
[17179580.220000] Probing IDE interface ide0...
[17179580.808000] Attempting manual resume
[17179580.816000] ReiserFS: sda2: found reiserfs format "3.6" with standard journal
[17179581.580000] ReiserFS: sda2: using ordered data mode
[17179581.592000] ReiserFS: sda2: journal params: device sda2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[17179581.592000] ReiserFS: sda2: checking transaction log (sda2)
[17179581.644000] ReiserFS: sda2: Using r5 hash to sort names
[17179590.696000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179592.048000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.084000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.476000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.476000] 8139cp: pci dev 0000:0b:07.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179592.476000] 8139cp: Try the "8139too" driver instead.
[17179592.484000] 8139too Fast Ethernet driver 0.9.27
[17179592.484000] ACPI: PCI Interrupt 0000:0b:07.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179592.488000] eth0: RealTek RTL8139 at 0xdc970000, 00:a0:d1:45:2c:f8, IRQ 58
[17179592.488000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.496000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.728000] input: PC Speaker as /class/input/input1
[17179592.736000] new_ath_hal: module license 'Proprietary' taints kernel.
[17179592.736000] new_ath_hal: 0.9.16.16 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179592.764000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179592.776000] wlan: 0.8.4.2 (svn 2006-07-10)
[17179592.788000] new_ath_rate_sample: 1.2 (svn 2006-07-10)
[17179592.792000] ath_pci: 0.9.4.5 (svn 2006-07-10)
[17179592.792000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 233
[17179592.792000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179592.792000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179592.792000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17179592.796000] ACPI: PCI Interrupt 0000:0b:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179592.796000] Yenta: CardBus bridge found at 0000:0b:06.0 [1179:ff10]
[17179592.796000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179592.796000] Yenta: Routing CardBus interrupts to PCI
[17179592.796000] Yenta TI: socket 0000:0b:06.0, mfunc 0x01111002, devctl 0x44
[17179592.816000] Real Time Clock Driver v1.12
[17179593.028000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179593.028000] Socket status: 30000006
[17179593.028000] Yenta: Raising subordinate bus# of parent bus (#0b) from #0d to #0f
[17179593.028000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179593.028000] cs: IO port probe 0xa000-0xafff: clean.
[17179593.028000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179593.028000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179593.312000] cs: IO port probe 0x100-0x3af: excluding 0x1f0-0x1f7
[17179593.316000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[17179593.316000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.316000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179593.316000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.332000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[17179593.332000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[17179593.368000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179593.404000] ts: Compaq touchscreen protocol output
[17179593.648000] eth0: link down
[17179593.828000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 233
[17179594.532000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179594.688000] NET: Registered protocol family 17
[17179595.160000] lp: driver loaded but no devices found
[17179595.204000] Adding 489972k swap on /dev/sda3.  Priority:-1 extents:1 across:489972k
[17179595.956000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.956000] md: bitmap version 4.39
[17179596.560000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179597.316000] cdrom: open failed.
[17179604.008000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179604.060000] NTFS volume version 3.1.






ty for help man :)

---

### Post by tturrisi on 2006-08-21
[17179592.736000] new_ath_hal: module license 'Proprietary' taints kernel.
[17179592.736000] new_ath_hal: 0.9.16.16 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179592.764000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179592.776000] wlan: 0.8.4.2 (svn 2006-07-10)
[17179592.788000] new_ath_rate_sample: 1.2 (svn 2006-07-10)
[17179592.792000] ath_pci: 0.9.4.5 (svn 2006-07-10)

did you install additioonal drivers?  Something does not look right above, there should not be this:  (one or the other only)
[17179592.764000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179592.776000] wlan: 0.8.4.2 (svn 2006-07-10)

post result of this:  uname -r

---

