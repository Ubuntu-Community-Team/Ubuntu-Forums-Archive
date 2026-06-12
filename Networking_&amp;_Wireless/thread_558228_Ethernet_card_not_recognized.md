---
title: "Ethernet card not recognized"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by jakartographer on 2007-09-23
When I try to access anything online (or my router's internal pages), I get a notice saying that the host is unknown.  When I looked for an ethernet connection, I saw nothing, although my motherboard has an integrated port (It's an EliteGroup board, so that might be the problem :) ).  Any pointers?

---

### Post by noob12 on 2007-09-24
You'd have to post more information about your machine and the current situation.  

Posting the output from these would help.  You can use a USB jump drive or a shared partition to get output off to post.

```

lspci -nn

sudo lshw -C network

ifconfig -a

```

---

### Post by jakartographer on 2007-09-24
The output came as follows (not verbatim):

```

lspci -nn
00:00.0 0500: 10de:03ea (rev a1)
00:01.0 0601: 10de:03e0 (rev a2)
00:01.1 0c05: 10de:03eb (rev a2)
00:01.2 0500: 10de:03f5 (rev a2)
00:02.0 0c03: 10de:03f1 (rev a2)
00:02.1 0c03: 10de:03f2 (rev a2)
00:04.0 0604: 10de:03f3 (rev a1)
00:05.0 0403: 10de:03f0 (rev a2)
00:06.0 0101: 10de:03ec (rev a2)
00:07.0 0680: 10de:03ef (rev a2)
00:08.0 0101: 10de:03f6 (rev a2)
00:09.0 0604: 10de:03e8 (rev a2)
00:0b.0 0604: 10de:03e9 (rev a2)
00:0c.0 0604: 10de:03e9 (rev a2)
00:0d.0 0300: 10de:03d1 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103

ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3856 (3.7 KiB)  TX bytes:3856 (3.7 KiB)


```

The lshw -C network command did something weird.  Konsole started flashing strings of three letters at the cursor, but they disappeared instantaneously before the next trio showed up, and the command ultimately had no output.

I'll check some other terminal emulator and get back to you on that.

---

### Post by noob12 on 2007-09-24
This is it: **10de:03ef**

This device id corresponds to an nvidia MCP61 Ethernet and it is supported and should be claimed by the **forcedeth** driver that is in Ubuntu 7.04 (based on looking at my own 2.6.20-16-generic)

The driver hasn't successfully claimed the device. There may be clues in the **dmesg** output.

What Ubuntu release and edition are you running?   And what kernel (what does **uname -a** say).

---

### Post by jakartographer on 2007-09-26
dmesg
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003bee0000 (usable)
[17179569.184000]  BIOS-e820: 000000003bee0000 - 000000003bee3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003bee3000 - 000000003bef0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003bef0000 - 000000003bf00000 (reserved)
[17179569.184000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[17179569.184000] 62MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f3a00
[17179569.184000] On node 0 totalpages: 245472
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 16096 pages, LIFO batch:3
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f7a10
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee3040
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee30c0
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x3bee9600
[17179569.184000] ACPI: _HPT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000098) @ 0x3bee98c0
[17179569.184000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee9940
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3bee9540
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:11 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:11 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 0 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2311.043 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.580000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.580000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.596000] Memory: 963496k/981888k available (1910k kernel code, 17812k reserved, 1070k data, 308k init, 64384k highmem)
[17179569.596000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.676000] Calibrating delay using timer specific routine.. 4628.48 BogoMIPS (lpj=9256965)
[17179569.676000] Security Framework v1.0.0 initialized
[17179569.676000] SELinux:  Disabled at boot.
[17179569.676000] Mount-cache hash table entries: 512
[17179569.676000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179569.676000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179569.676000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.676000] CPU: L2 Cache: 512K (64 bytes/line)
[17179569.676000] CPU 0(2) -> Core 0
[17179569.676000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[17179569.676000] Checking 'hlt' instruction... OK.
[17179569.692000] SMP alternatives: switching to UP code
[17179569.692000] checking if image is initramfs... it is
[17179570.088000] Freeing initrd memory: 5523k freed
[17179570.088000] ACPI: Core revision 20060707
[17179570.092000] ACPI: Looking for DSDT ... not found!
[17179570.092000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 01
[17179570.092000] SMP alternatives: switching to SMP code
[17179570.092000] Booting processor 1/1 eip 3000
[17179570.104000] Initializing CPU#1
[17179570.184000] Calibrating delay using timer specific routine.. 4621.67 BogoMIPS (lpj=9243340)
[17179570.184000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179570.184000] CPU: After vendor identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[17179570.184000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.184000] CPU: L2 Cache: 512K (64 bytes/line)
[17179570.184000] CPU 1(2) -> Core 1
[17179570.184000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[17179570.184000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 01
[17179570.184000] Total of 2 processors activated (9250.15 BogoMIPS).
[17179570.184000] ENABLING IO-APIC IRQs
[17179570.184000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.332000] checking TSC synchronization across 2 CPUs:
[17179570.336000] Brought up 2 CPUs
[17179570.400000] migration_cost=0
[17179570.400000] NET: Registered protocol family 16
[17179570.400000] EISA bus registered
[17179570.400000] ACPI: bus type pci registered
[17179570.400000] PCI: Using MMCONFIG
[17179570.400000] PCI: No mmconfig possible on 0:18
[17179570.400000] Setting up standard PCI resources
[17179570.412000] ACPI: Interpreter enabled
[17179570.412000] ACPI: Using IOAPIC for interrupt routing
[17179570.412000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.412000] PCI: Probing PCI hardware (bus 00)
[17179570.416000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:06.0
[17179570.416000] Boot video device is 0000:00:0d.0
[17179570.416000] PCI: Transparent bridge - 0000:00:04.0
[17179570.416000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.484000] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.484000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 *10 11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.488000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[17179570.488000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[17179570.492000] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[17179570.492000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[17179570.496000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.500000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.500000] pnp: PnP ACPI init
[17179570.504000] pnp: PnP ACPI: found 13 devices
[17179570.504000] PnPBIOS: Disabled by ACPI PNP
[17179570.504000] PCI: Using ACPI for IRQ routing
[17179570.504000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.504000] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[17179570.504000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[17179570.504000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[17179570.504000] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[17179570.504000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[17179570.504000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[17179570.504000] PCI: Bridge: 0000:00:04.0
[17179570.504000]   IO window: c000-cfff
[17179570.504000]   MEM window: fdf00000-fdffffff
[17179570.504000]   PREFETCH window: fd800000-fd8fffff
[17179570.504000] PCI: Bridge: 0000:00:09.0
[17179570.504000]   IO window: b000-bfff
[17179570.504000]   MEM window: fde00000-fdefffff
[17179570.504000]   PREFETCH window: fdd00000-fddfffff
[17179570.504000] PCI: Bridge: 0000:00:0b.0
[17179570.504000]   IO window: a000-afff
[17179570.504000]   MEM window: fdc00000-fdcfffff
[17179570.504000]   PREFETCH window: fdb00000-fdbfffff
[17179570.504000] PCI: Bridge: 0000:00:0c.0
[17179570.504000]   IO window: 9000-9fff
[17179570.504000]   MEM window: fda00000-fdafffff
[17179570.504000]   PREFETCH window: fd900000-fd9fffff
[17179570.504000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179570.504000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179570.504000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179570.504000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179570.504000] NET: Registered protocol family 2
[17179570.552000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.552000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179570.552000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179570.552000] TCP: Hash tables configured (established 131072 bind 65536)
[17179570.552000] TCP reno registered
[17179570.552000] audit: initializing netlink socket (disabled)
[17179570.552000] audit(1190825187.552:1): initialized
[17179570.552000] highmem bounce pool size: 64 pages
[17179570.552000] VFS: Disk quotas dquot_6.5.1
[17179570.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.552000] Initializing Cryptographic API
[17179570.552000] io scheduler noop registered
[17179570.552000] io scheduler anticipatory registered
[17179570.552000] io scheduler deadline registered
[17179570.552000] io scheduler cfq registered (default)
[17179570.552000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179570.552000] pcie_portdrv_probe->Dev[03e8:10de] has invalid IRQ. Check vendor BIOS
[17179570.552000] assign_interrupt_mode Found MSI capability
[17179570.552000] Allocate Port Service[0000:00:09.0:pcie00]
[17179570.552000] Allocate Port Service[0000:00:09.0:pcie03]
[17179570.552000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179570.552000] pcie_portdrv_probe->Dev[03e9:10de] has invalid IRQ. Check vendor BIOS
[17179570.552000] assign_interrupt_mode Found MSI capability
[17179570.552000] Allocate Port Service[0000:00:0b.0:pcie00]
[17179570.552000] Allocate Port Service[0000:00:0b.0:pcie03]
[17179570.552000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179570.552000] pcie_portdrv_probe->Dev[03e9:10de] has invalid IRQ. Check vendor BIOS
[17179570.552000] assign_interrupt_mode Found MSI capability
[17179570.552000] Allocate Port Service[0000:00:0c.0:pcie00]
[17179570.552000] Allocate Port Service[0000:00:0c.0:pcie03]
[17179570.552000] isapnp: Scanning for PnP cards...
[17179570.904000] isapnp: No Plug & Play device found
[17179570.924000] Real Time Clock Driver v1.12ac
[17179570.924000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.924000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.924000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.924000] mice: PS/2 mouse device common for all mice
[17179570.924000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.924000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.924000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.924000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179570.924000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.464000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.468000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.468000] EISA: Probing bus 0 at eisa.0
[17179571.468000] Cannot allocate resource for EISA slot 1
[17179571.468000] EISA: Detected 0 cards.
[17179571.468000] TCP bic registered
[17179571.468000] NET: Registered protocol family 1
[17179571.468000] NET: Registered protocol family 8
[17179571.468000] NET: Registered protocol family 20
[17179571.468000] Starting balanced_irq
[17179571.468000] Using IPI No-Shortcut mode
[17179571.468000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.468000] Freeing unused kernel memory: 308k freed
[17179571.508000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.552000] Capability LSM initialized
[17179572.576000] ACPI: Fan [FAN] (on)
[17179572.580000] ACPI: Thermal Zone [THRM] (40 C)
[17179572.904000] SCSI subsystem initialized
[17179572.904000] libata version 1.20 loaded.
[17179572.904000] sata_nv 0000:00:08.0: version 0.8
[17179572.904000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179572.904000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 209
[17179572.904000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179572.904000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xD800 irq 209
[17179572.904000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xD808 irq 209
[17179573.108000] ata1: SATA link down (SStatus 0)
[17179573.108000] scsi0 : sata_nv
[17179573.312000] ata2: SATA link down (SStatus 0)
[17179573.312000] scsi1 : sata_nv
[17179573.388000] Probing IDE interface ide0...
[17179573.400000] usbcore: registered new driver usbfs
[17179573.400000] usbcore: registered new driver hub
[17179573.400000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179573.404000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179573.404000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 217
[17179573.404000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179573.404000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179573.404000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179573.424000] ohci_hcd 0000:00:02.0: irq 217, io mem 0xfe02f000
[17179573.484000] usb usb1: configuration #1 chosen from 1 choice
[17179573.484000] hub 1-0:1.0: USB hub found
[17179573.484000] hub 1-0:1.0: 8 ports detected
[17179573.592000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[17179573.592000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 21 (level, low) -> IRQ 225
[17179573.592000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179573.592000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179573.592000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179573.592000] ehci_hcd 0000:00:02.1: debug port 1
[17179573.592000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[17179573.592000] ehci_hcd 0000:00:02.1: irq 225, io mem 0xfe02e000
[17179573.592000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179573.592000] usb usb2: configuration #1 chosen from 1 choice
[17179573.592000] hub 2-0:1.0: USB hub found
[17179573.592000] hub 2-0:1.0: 8 ports detected
[17179573.828000] hda: ST340810A, ATA DISK drive
[17179573.932000] ohci_hcd 0000:00:02.0: wakeup
[17179574.108000] hdb: Conner Peripherals 420MB - CFS420A, ATA DISK drive
[17179574.168000] Probing IDE interface ide1...
[17179574.316000] usb 1-3: new low speed USB device using ohci_hcd and address 2
[17179574.540000] usb 1-3: configuration #1 chosen from 1 choice
[17179574.548000] usbcore: registered new driver hiddev
[17179574.556000] input: Logitech USB Trackball as /class/input/input1
[17179574.556000] input: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:02.0-3
[17179574.556000] usbcore: registered new driver usbhid
[17179574.556000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179574.732000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.740000] hda: max request size: 128KiB
[17179574.740000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63
[17179574.740000] hda: cache flushes not supported
[17179574.740000]  hda: hda1 hda2 hda3 hda4
[17179574.784000] hdb: max request size: 128KiB
[17179574.784000] hdb: 832608 sectors (426 MB) w/64KiB Cache, CHS=826/16/63
[17179574.784000] hdb: cache flushes not supported
[17179574.784000]  hdb: hdb1
[17179575.936000] Attempting manual resume
[17179575.980000] kjournald starting.  Commit interval 5 seconds
[17179575.980000] EXT3-fs: mounted filesystem with ordered data mode.
[17179594.324000] Floppy drive(s): fd0 is 1.44M
[17179594.364000] FDC 0 is a post-1991 82077
[17179594.428000] input: PC Speaker as /class/input/input2
[17179594.860000] parport: PnPBIOS parport detected.
[17179594.860000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179595.408000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.420000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.488000] Linux agpgart interface v0.101 (c) Dave Jones
[17179595.684000] ts: Compaq touchscreen protocol output
[17179595.840000] lp0: using parport0 (interrupt-driven).
[17179595.864000] Adding 612352k swap on /dev/disk/by-uuid/a1e47adc-ead8-4226-955b-4a1395ad9eb9.  Priority:-1 extents:1 across:612352k
[17179596.288000] EXT3 FS on hda3, internal journal
[17179599.080000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179599.164000] NTFS volume version 3.1.
[17179599.312000] NTFS volume version 3.1.
[17179600.632000] NET: Registered protocol family 17
[17179605.784000] ACPI: Power Button (FF) [PWRF]
[17179605.784000] ACPI: Power Button (CM) [PWRB]
[17179605.904000] ibm_acpi: ec object not found
[17179605.936000] pcc_acpi: loading...
[17179606.256000] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179606.256000] powernow-k8:    0 : fid 0xf (2300 MHz), vid 0x9 (1325 mV)
[17179606.256000] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xa (1300 mV)
[17179606.256000] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xc (1250 mV)
[17179606.256000] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xe (1200 mV)
[17179606.256000] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12 (1100 mV)
[17179606.256000] cpu_init done, current fid 0xf, vid 0x9
[17179609.180000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179609.180000] apm: disabled - APM is not SMP safe.
[17179616.340000] Bluetooth: Core ver 2.8
[17179616.340000] NET: Registered protocol family 31
[17179616.340000] Bluetooth: HCI device and connection manager initialized
[17179616.340000] Bluetooth: HCI socket layer initialized
[17179616.520000] Bluetooth: L2CAP ver 2.8
[17179616.520000] Bluetooth: L2CAP socket layer initialized
[17179616.644000] Bluetooth: RFCOMM socket layer initialized
[17179616.644000] Bluetooth: RFCOMM TTY layer initialized
[17179616.644000] Bluetooth: RFCOMM ver 1.7
```

uname -a
```
Linux akka-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
```

Also, just for future reference, what exactly is dmesg?

---

### Post by noob12 on 2007-09-26
OK.  Support for that card was added to the **forcedeth** driver sometime after kernel version 2.6.17-10-generic that you have from Edgy.  It is supported by the version of that driver in Feisty's current kernel 2.6.20-16-generic (and should be in Gutsy as well).

If this is a new installation, you might want to consider using Feisty, which should support it out-of-box.  That would probably be your easiest path.

Alternatively you can probably download the source of version 0.60 or later of the forcedeth driver and build it yourself, but I won't be the best guide there since I haven't built that particular driver.
As far as I can tell, the latest version is 0.62 in driver package 1.23 available here: [http://www.nvidia.com/object/linux_nforce_archive.html](http://www.nvidia.com/object/linux_nforce_archive.html)

ADDED:
dmesg (see **man dmesg**) prints out kernel log messages from your boot.

---

### Post by jakartographer on 2007-09-26
Since I haven't had any Internet access, my box isn't at all cluttered, so I wouldn't have many problems making the switch.  Is there some way I could save my settings (especially visual themes) for export to Feisty?  I probably should migrate, anyway, and I've been thinking about it for some time.

---

### Post by rustybronco on 2007-09-26
is ethernet enabled or disabled in the bios?

---

### Post by jakartographer on 2007-10-09
It looks enabled, but it's hard to tell.  My BIOS doesn't give me a well-labeled "ethernet port" entry, but I've pretty much decided to update to Feisty or Gutsy, anyway.  Question:  If I backup my user directory and empty its contents into my new user directory after the update, will my settings survive the change of venue?  A friend recommended this, but I want to be sure that it'll work.

---

