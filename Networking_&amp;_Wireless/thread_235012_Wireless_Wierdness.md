---
title: "Wireless Wierdness"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by tdell on 2006-08-12
Curently using Kbuntu Dapper on a AMD64. It says there is no wireless device, however I can connect to my network wirelessly but not to the Internet, internet works fine with the wired connection.

Any Ideas?

Tom

---

### Post by tdell on 2006-08-12
Anyone at all?

---

### Post by Bezmotivnik on 2006-08-13
> **tdell said:**
> Anyone at all?
Is the wireless device active in ubuntu, detecting the access point, but failing to get a network address?

If so, I'm having the identical problem. ](*,)

---

### Post by tdell on 2006-08-13
**BUMP**

Any answers out there?

---

### Post by JDAAINOKI on 2006-08-13
can you post the output of the follwing:

```
lspci
```

```
iwconfig
```

```
ifconfig -a
```

```
dmesg
```

Thanks,
Jay

---

### Post by tdell on 2006-08-14
OK thanks have also include the output of lsusb, since my wireless is connected to the USB port.

Any help would be appreciated. What confuses me is I can access the other computers on the network but it tells me there is no network.

tom@SERVER:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
0000:00:11.0 ISA bridge: VIA Technologies, Inc.: Unknown device 3287
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 70)
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCIE Bridge
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
0000:02:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
0000:02:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port


tom@SERVER:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


tom@SERVER:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D4:CC:97:54
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fecc:9754/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17102796 (16.3 MiB)  TX bytes:3178486 (3.0 MiB)
          Interrupt:225 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:620 (620.0 b)  TX bytes:620 (620.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tom@SERVER:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sda1 ro quiet splash)
[    0.000000] Linux version 2.6.17.3jm (root@littlepoint) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Sat Jul 8 19:52:38 EDT 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffb0000 - 000000001ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffbe000 - 000000001ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ffe0000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x00000000000fac60
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x09000505 MSFT 0x00000097) @ 0x000000001ffb0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x09000505 MSFT 0x00000097) @ 0x000000001ffb0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000505 MSFT 0x00000097) @ 0x000000001ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x09000505 MSFT 0x00000097) @ 0x000000001ffbe040
[    0.000000] ACPI: DSDT (v001  A0347 A0347001 0x00000001 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000001ffb0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000001ffb0000
[    0.000000] On node 0 totalpages: 127880
[    0.000000]   DMA zone: 2718 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 125162 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ dc000000 size 64 MB
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 2200.102 MHz processor.
[   20.620869] Console: colour VGA+ 80x25
[   20.621449] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.621838] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[   20.630052] Memory: 504208k/523968k available (2205k kernel code, 19372k reserved, 864k data, 192k init)
[   20.689746] Calibrating delay using timer specific routine.. 4401.60 BogoMIPS (lpj=2200804)
[   20.689806] Security Framework v1.0.0 initialized
[   20.689814] SELinux:  Disabled at boot.
[   20.689837] Mount-cache hash table entries: 256
[   20.689987] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.689989] CPU: L2 Cache: 512K (64 bytes/line)
[   20.689992] CPU 0/0(1) -> Node 0 -> Core 0
[   20.702962] Using local APIC timer interrupts.
[   20.748375] result 12500581
[   20.748377] Detected 12.500 MHz APIC timer.
[   20.748731] Brought up 1 CPUs
[   20.748766] testing NMI watchdog ... OK.
[   20.758807] migration_cost=0
[   20.758900] checking if image is initramfs... it is
[   21.217290] Freeing initrd memory: 6415k freed
[   21.217919] NET: Registered protocol family 16
[   21.217953] ACPI: bus type pci registered
[   21.217962] PCI: Using configuration type 1
[   21.218157] ACPI: Subsystem revision 20060127
[   21.222756] ACPI: Interpreter enabled
[   21.222758] ACPI: Using IOAPIC for interrupt routing
[   21.223729] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.223732] PCI: Probing PCI hardware (bus 00)
[   21.226627] Boot video device is 0000:01:00.0
[   21.226930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.242421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   21.246143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   21.246264] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P9._PRT]
[   21.246520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P8._PRT]
[   21.248651] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   21.248864] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   21.249073] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   21.249303] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   21.249508] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.249713] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.249918] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.250145] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   21.250221] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.250232] pnp: PnP ACPI init
[   21.253946] pnp: PnP ACPI: found 15 devices
[   21.254099] SCSI subsystem initialized
[   21.254131] PCI: Using ACPI for IRQ routing
[   21.254134] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.254292] agpgart: Detected AGP bridge 0
[   21.257018] agpgart: AGP aperture is 64M @ 0xdc000000
[   21.257044] PCI-DMA: Disabling IOMMU.
[   21.257673] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   21.257884] PCI: Bridge: 0000:00:01.0
[   21.257888]   IO window: a000-cfff
[   21.257892]   MEM window: ff500000-ff5fffff
[   21.257895]   PREFETCH window: c7f00000-d7efffff
[   21.257900] PCI: Bridge: 0000:02:00.0
[   21.257901]   IO window: disabled.
[   21.257904]   MEM window: disabled.
[   21.257907]   PREFETCH window: disabled.
[   21.257910] PCI: Bridge: 0000:02:00.1
[   21.257912]   IO window: disabled.
[   21.257915]   MEM window: disabled.
[   21.257917]   PREFETCH window: disabled.
[   21.257921] PCI: Bridge: 0000:00:13.0
[   21.257922]   IO window: disabled.
[   21.257925]   MEM window: disabled.
[   21.257928]   PREFETCH window: disabled.
[   21.257943] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   21.257949] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   21.257960] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.257971] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   21.258029] NET: Registered protocol family 2
[   21.266252] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[   21.266370] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[   21.266585] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[   21.266707] TCP: Hash tables configured (established 16384 bind 8192)
[   21.266709] TCP reno registered
[   21.267043] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   21.267440] audit: initializing netlink socket (disabled)
[   21.267454] audit(1155554731.646:1): initialized
[   21.267616] VFS: Disk quotas dquot_6.5.1
[   21.267638] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.267695] Initializing Cryptographic API
[   21.267700] io scheduler noop registered
[   21.267706] io scheduler anticipatory registered (default)
[   21.267716] io scheduler deadline registered
[   21.267732] io scheduler cfq registered
[   21.268371] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   21.268376] pcie_portdrv_probe->Dev[287c:1106] has invalid IRQ. Check vendor BIOS
[   21.268402] assign_interrupt_mode Found MSI capability
[   21.268456] Allocate Port Service[0000:02:00.0:pcie00]
[   21.268496] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   21.268499] pcie_portdrv_probe->Dev[287d:1106] has invalid IRQ. Check vendor BIOS
[   21.268522] assign_interrupt_mode Found MSI capability
[   21.268557] Allocate Port Service[0000:02:00.1:pcie00]
[   21.287500] Real Time Clock Driver v1.12ac
[   21.287539] Linux agpgart interface v0.101 (c) Dave Jones
[   21.287542] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.287661] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.288248] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.288461] isa bounce pool size: 16 pages
[   21.288874] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.289005] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.289008] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.289253] libata version 1.20 loaded.
[   21.289377] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   21.289565] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.289613] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.289694] mice: PS/2 mouse device common for all mice
[   21.289856] TCP bic registered
[   21.289864] NET: Registered protocol family 1
[   21.289871] NET: Registered protocol family 8
[   21.289872] NET: Registered protocol family 20
[   21.289965] ACPI wakeup devices:
[   21.289967] PCI0 PS2K PS2M UAR1 P7P8 USB1 USB2 USB3 USB4 EHCI ILAN SLPB PWRB
[   21.289980] ACPI: (supports S0 S1 S3 S4 S5)
[   21.290247] Freeing unused kernel memory: 192k freed
[   21.341097] input: AT Translated Set 2 keyboard as /class/input/input0
[   21.341142] vga16fb: initializing
[   21.341145] vga16fb: mapped to 0xffff8100000a0000
[   21.341183] fb0: VGA16 VGA frame buffer device
[   22.393882] ACPI: Processor [CPU1] (supports 16 throttling states)
[   22.892987] ahci 0000:00:0f.0: version 1.2
[   22.893009] GSI 16 sharing vector 0xC1 and IRQ 16
[   22.893012] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 193
[   27.200432] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   27.200437] ahci 0000:00:0f.0: flags: 64bit ncq pm led clo pmp pio slum part
[   27.200497] ata1: SATA max UDMA/133 cmd 0xFFFFC20000062D00 ctl 0x0 bmdma 0x0 irq 201
[   27.200523] ata2: SATA max UDMA/133 cmd 0xFFFFC20000062D80 ctl 0x0 bmdma 0x0 irq 201
[   27.200543] ata3: SATA max UDMA/133 cmd 0xFFFFC20000062E00 ctl 0x0 bmdma 0x0 irq 201
[   27.200562] ata4: SATA max UDMA/133 cmd 0xFFFFC20000062E80 ctl 0x0 bmdma 0x0 irq 201
[   27.566076] ata1: SATA link up 1.5 Gbps (SStatus 113)
[   27.566699] ata1: dev 0 cfg 49:2f00 82:346b 83:5b01 84:4003 85:3469 86:1801 87:4003 88:203f
[   27.566702] ata1: dev 0 ATA-6, max UDMA/100, 78125000 sectors: LBA
[   27.567356] ata1: dev 0 configured for UDMA/100
[   27.567358] scsi0 : ahci
[   28.471187] ata2: SATA link down (SStatus 0)
[   28.471190] scsi1 : ahci
[   29.375309] ata3: SATA link down (SStatus 0)
[   29.375311] scsi2 : ahci
[   30.278432] ata4: SATA link down (SStatus 0)
[   30.278434] scsi3 : ahci
[   30.278589]   Vendor: ATA       Model: WDC WD400BD-75JM  Rev: 05.0
[   30.278596]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   30.278765] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[   30.278773] sda: Write Protect is off
[   30.278775] sda: Mode Sense: 00 3a 00 00
[   30.278785] SCSI device sda: drive cache: write back
[   30.278833] SCSI device sda: 78125000 512-byte hdwr sectors (40000 MB)
[   30.278839] sda: Write Protect is off
[   30.278841] sda: Mode Sense: 00 3a 00 00
[   30.278850] SCSI device sda: drive cache: write back
[   30.278853]  sda: sda1 sda2 < sda5 >
[   30.310113] sd 0:0:0:0: Attached scsi disk sda
[   30.569218] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   30.569239] PCI: VIA IRQ fixup for 0000:00:0f.1, from 255 to 0
[   30.569265] VP_IDE: chipset revision 7
[   30.569267] VP_IDE: not 100% native mode: will probe irqs later
[   30.569280] VP_IDE: VIA vt8251 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   30.569287]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   30.569301]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   30.569310] Probing IDE interface ide0...
[   31.087648] Probing IDE interface ide1...
[   31.880962] hdc: _NEC DVD_RW ND-3520AW, ATAPI CD/DVD-ROM drive
[   32.492581] ide1 at 0x170-0x177,0x376 on irq 15
[   32.500297] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   32.500306] Uniform CD-ROM driver Revision: 3.20
[   32.559954] usbcore: registered new driver usbfs
[   32.559980] usbcore: registered new driver hub
[   32.560676] USB Universal Host Controller Interface driver v3.0
[   32.560736] GSI 17 sharing vector 0xD1 and IRQ 17
[   32.560740] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 209
[   32.560744] PCI: VIA IRQ fixup for 0000:00:10.0, from 10 to 1
[   32.560771] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   32.561100] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   32.561129] uhci_hcd 0000:00:10.0: irq 209, io base 0x0000e080
[   32.561234] usb usb1: configuration #1 chosen from 1 choice
[   32.561253] hub 1-0:1.0: USB hub found
[   32.561261] hub 1-0:1.0: 2 ports detected
[   32.662310] GSI 18 sharing vector 0xD9 and IRQ 18
[   32.662315] ACPI: PCI Interrupt 0000:00:10.1[C] -> GSI 22 (level, low) -> IRQ 217
[   32.662320] PCI: VIA IRQ fixup for 0000:00:10.1, from 5 to 9
[   32.662346] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   32.662425] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   32.662452] uhci_hcd 0000:00:10.1: irq 217, io base 0x0000e000
[   32.662594] usb usb2: configuration #1 chosen from 1 choice
[   32.662671] hub 2-0:1.0: USB hub found
[   32.662679] hub 2-0:1.0: 2 ports detected
[   32.764111] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 193
[   32.764115] PCI: VIA IRQ fixup for 0000:00:10.2, from 11 to 1
[   32.764135] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   32.764216] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   32.764237] uhci_hcd 0000:00:10.2: irq 193, io base 0x0000dc00
[   32.764361] usb usb3: configuration #1 chosen from 1 choice
[   32.764437] hub 3-0:1.0: USB hub found
[   32.764443] hub 3-0:1.0: 2 ports detected
[   32.865013] GSI 19 sharing vector 0xE1 and IRQ 19
[   32.865016] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 225
[   32.865020] PCI: VIA IRQ fixup for 0000:00:10.3, from 3 to 1
[   32.865040] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   32.865121] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   32.865141] uhci_hcd 0000:00:10.3: irq 225, io base 0x0000d880
[   32.865271] usb usb4: configuration #1 chosen from 1 choice
[   32.865352] hub 4-0:1.0: USB hub found
[   32.865359] hub 4-0:1.0: 2 ports detected
[   32.867916] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   32.972048] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 22 (level, low) -> IRQ 217
[   32.972214] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   32.972270] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   32.972315] ehci_hcd 0000:00:10.4: debug port 1
[   32.972325] ehci_hcd 0000:00:10.4: irq 217, io mem 0xff6ff800
[   32.972332] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   32.972400] usb usb5: configuration #1 chosen from 1 choice
[   32.972419] hub 5-0:1.0: USB hub found
[   32.972426] hub 5-0:1.0: 8 ports detected
[   33.088625] Probing IDE interface ide0...
[   33.386410] usb 1-1: device not accepting address 2, error -71
[   33.646040] kjournald starting.  Commit interval 5 seconds
[   33.646052] EXT3-fs: mounted filesystem with ordered data mode.
[   34.680163] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   34.840092] usb 1-1: configuration #1 chosen from 1 choice
[   35.063797] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   35.228152] usb 2-2: configuration #1 chosen from 1 choice
[   39.489259] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.673502] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.927691] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.193390] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[   41.193445] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 225
[   41.193543] eth0: VIA Rhine II at 0x1d000, 00:13:d4:cc:97:54, IRQ 225.
[   41.194259] eth0: MII PHY found at address 1, status 0x7869 advertising 01e1 Link 45e1.
[   41.382575] parport: PnPBIOS parport detected.
[   41.382685] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   41.398957] parport0: Printer, Samsung ML-1430
[   41.642660] Floppy drive(s): fd0 is 1.44M
[   41.689802] FDC 0 is a post-1991 82077
[   41.937642] usbcore: registered new driver hiddev
[   41.968452] input: KYE PowerScroll EYE as /class/input/input1
[   41.968501] input: USB HID v1.10 Mouse [KYE PowerScroll EYE] on usb-0000:00:10.0-1
[   41.968516] usbcore: registered new driver usbhid
[   41.968519] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   42.175142] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   42.183078] ts: Compaq touchscreen protocol output
[   42.813650] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 217
[   42.813785] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   43.256885] NET: Registered protocol family 17
[   44.255654] lp0: using parport0 (interrupt-driven).
[   44.602148] Adding 1494004k swap on /dev/sda5.  Priority:-1 extents:1 across:1494004k
[   44.975592] EXT3 FS on sda1, internal journal
[   45.166739] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   45.166743] md: bitmap version 4.39
[   45.538388] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[   46.213508] device-mapper: dm-linear: Device lookup failed
[   46.213514] device-mapper: error adding target to table
[   46.215461] device-mapper: dm-linear: Device lookup failed
[   46.215467] device-mapper: error adding target to table
[   46.217408] device-mapper: dm-linear: Device lookup failed
[   46.217414] device-mapper: error adding target to table
[   46.219365] device-mapper: dm-linear: Device lookup failed
[   46.219371] device-mapper: error adding target to table
[   46.221384] device-mapper: dm-linear: Device lookup failed
[   46.221389] device-mapper: error adding target to table
[   46.223280] device-mapper: dm-linear: Device lookup failed
[   46.223286] device-mapper: error adding target to table
[   46.225189] device-mapper: dm-linear: Device lookup failed
[   46.225195] device-mapper: error adding target to table
[   46.227170] device-mapper: dm-linear: Device lookup failed
[   46.227176] device-mapper: error adding target to table
[   50.802621] NET: Registered protocol family 10
[   50.802718] lo: Disabled Privacy Extensions
[   50.802866] IPv6 over IPv4 tunneling driver
[   53.887756] ACPI: Power Button (FF) [PWRF]
[   53.887784] ACPI: Sleep Button (CM) [SLPB]
[   53.887790] ACPI: Power Button (CM) [PWRB]
[   53.918309] Using specific hotkey driver
[   53.934236] ibm_acpi: ec object not found
[   53.961321] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[   55.482221] ppdev: user-space parallel port driver
[   57.787369] Capability LSM initialized
[   59.046842] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   59.047085] powernow-k8: MP systems not supported by PSB BIOS structure
[   60.835773] eth0: no IPv6 routers present
[   65.661513] [drm] Initialized drm 1.0.1 20051102
[   65.677673] GSI 20 sharing vector 0xE9 and IRQ 20
[   65.677861] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 233
[   65.685054] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[   66.623110] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   66.623235] agpgart: Device is in legacy mode, falling back to 2.x
[   66.623304] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   66.623432] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[   66.910692] [drm] Setting GART location based on new memory map
[   66.910774] [drm] Loading R200 Microcode
[   66.910840] [drm] writeback test succeeded in 1 usecs
[   76.713380] eth0: no IPv6 routers present
[ 2044.626555] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 2044.626574] agpgart: Device is in legacy mode, falling back to 2.x
[ 2044.626580] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[ 2044.626642] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[ 2044.905464] [drm] Setting GART location based on new memory map
[ 2044.905475] [drm] Loading R200 Microcode
[ 2044.905541] [drm] writeback test succeeded in 1 usecs
tom@SERVER:~$                                  

tom@SERVER:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 124a:4017 AirVast PC-Chips 802.11b Adapter
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0458:001a KYE Systems Corp. (Mouse Systems) Genius WebScroll+
Bus 001 Device 001: ID 0000:0000

---

### Post by garrye on 2006-08-14
Hmmm nothing matching the search string "net" in dmesg.
Usb adapter that is compliant with 802.11b (NOT g NOT b/g BUT b only?)
You might want to try another.  I'm running wireless on Broadcom 4318 silicon in a laptop and wish I could have solved my woes so easily.
What drivers are you using?  Ndiswrapper?  I don't see an entry in dmesg for ndiswrapper.

---

### Post by bensexson on 2006-08-14
It looks like you will need to use ndiswrapper.  Look here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by tdell on 2006-08-15
I will give that a try but I don;t think it will help I can access my network now even though it says there isn't one. The only problem is accessing the Internet with wireless.


tom

---

### Post by JDAAINOKI on 2006-08-15
Is your DNS info correct? Try giving a ping to google using their IP address 64.233.187.99 and see if you can get a return.
```
ping 64.233.187.99 -c 3
``` 

Good Luck
Jay

---

### Post by Garfield360 on 2006-08-15
Im having the same problem, i can connect to the router but not the internet, it is connected to the router as i get a reply when i ping the IP address:confused:

---

### Post by JDAAINOKI on 2006-08-15
Garfield,
can you ping any outside ip?  Don't try google.com or anything, but try and ping their actual ip.  Check your /etc/resolv.conf file and make sure it lists your router as the nameserver. Try to manualy configure your card if that doesn't work. Add your information in place of IPs and interfaces below.

```
ifconfig ra0 up
ifconfig ra0 192.168.0.101
route add default gw 192.168.0.101
nano /etc/resolv.conf ---make sure your nameserver is set to your router IP
dhclient ra0 ----just to make sure
```

Good Luck
Jay

---

### Post by tdell on 2006-08-18
> **bensexson said:**
> It looks like you will need to use ndiswrapper.  Look here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Well still no go, but since I can access the network it says does not exist i will just use it as is, just need to connect to the router with a wire for Internet.

---

### Post by tdell on 2006-08-21
OK. I have found ut my wireless card IS supported. I downloaded linux-wlan-ng-0.2.3 ran it and followed the setup instructions. I then have a wireless connection, however I lose it on a re-boot and have to go through the configuration process again to get a wireless connect????

Any ideas how how to get it to start on booting?

---

### Post by tdell on 2006-08-27
OK I have given uo I have gone back to SUSE, it has a problem or two, but at least it automatically configured my wireless and printer  with no problems.

---

