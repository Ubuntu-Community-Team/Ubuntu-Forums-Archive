---
title: "need help - NIC does not light up"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by drewy on 2007-08-13
hey all,

im new to ubuntu, i have a problem with my network card (onboard realtek 10/100 on asus board A8V-MX-UAYKZ). The problem is the green light on the NIC never comes on, however on my router it says that it is connected, and also the network will all of a sudden start working and the orange light flashes but then after a random period of time it stops. can someone please help me?

---

### Post by noob12 on 2007-08-14
Please post the full output of these.
```

lspci -nn

lshw -C network

dmesg

```

---

### Post by drewy on 2007-08-16
sorry it took so long to reply ive been without net,  here is the output from those commands, also the net is working all the time now, but the green light still doesn't come on:

lspci -nn:
00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:0204]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:1204]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:2204]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:3204]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:4204]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8M800 Host Bridge [1106:7204]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller [1106:3349]
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 90)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8251 PCI to ISA Bridge [1106:3287]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 70)
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
00:13.0 PCI bridge [0604]: VIA Technologies, Inc. VT8251 Host Bridge [1106:287b]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
02:00.0 PCI bridge [0604]: VIA Technologies, Inc. VT8251 PCIE Root Port [1106:287c]
02:00.1 PCI bridge [0604]: VIA Technologies, Inc. VT8251 PCIE Root Port [1106:287d]

lshw -C network:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:15:f2:30:5d:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.0.25 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:d000-d0ff iomemory:ff6ff400-ff6ff4ff irq:19

dmesg:
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003feb0000 end: 000000003ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffb0000 size: 000000000000e000 end: 000000003ffbe000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffbe000 size: 0000000000022000 end: 000000003ffe0000 type: 4
[    0.000000] copy_e820_map() start: 000000003ffe0000 size: 0000000000020000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffbe000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fac60
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000505 MSFT 0x00000097) @ 0x3ffb0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x10000505 MSFT 0x00000097) @ 0x3ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000505 MSFT 0x00000097) @ 0x3ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x10000505 MSFT 0x00000097) @ 0x3ffbe040
[    0.000000] ACPI: DSDT (v001  A0347 A0347001 0x00000001 INTL 0x02002026) @ 0x00000000
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 2000.122 MHz processor.
[   36.045351] Built 1 zonelists.  Total pages: 260017
[   36.045355] Kernel command line: root=UUID=42fa0e69-e004-4cf4-8f9e-7ca64b061183 ro quiet splash
[   36.045480] mapped APIC to ffffd000 (fee00000)
[   36.045483] mapped IOAPIC to ffffc000 (fec00000)
[   36.045485] Enabling fast FPU save and restore... done.
[   36.045488] Enabling unmasked SIMD FPU exception support... done.
[   36.045495] Initializing CPU#0
[   36.045552] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   36.046824] Console: colour VGA+ 80x25
[   36.047245] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.047678] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.066110] Memory: 1028056k/1048256k available (1992k kernel code, 19484k reserved, 900k data, 328k init, 130752k highmem)
[   36.066119] virtual kernel memory layout:
[   36.066120]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   36.066122]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.066123]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.066124]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.066125]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   36.066126]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   36.066127]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   36.066130] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.145372] Calibrating delay using timer specific routine.. 4002.64 BogoMIPS (lpj=8005292)
[   36.145410] Security Framework v1.0.0 initialized
[   36.145417] SELinux:  Disabled at boot.
[   36.145431] Mount-cache hash table entries: 512
[   36.145557] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   36.145565] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.145568] CPU: L2 Cache: 512K (64 bytes/line)
[   36.145570] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   36.145581] Compat vDSO mapped to ffffe000.
[   36.145585] Remapping vsyscall page to ffffe000
[   36.145594] Checking 'hlt' instruction... OK.
[   36.161471] SMP alternatives: switching to UP code
[   36.161690] Freeing SMP alternatives: 11k freed
[   36.161873] Early unpacking initramfs... done
[   36.440687] ACPI: Core revision 20060707
[   36.441123] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   36.443048] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[   36.443067] Total of 1 processors activated (4002.64 BogoMIPS).
[   36.443171] ENABLING IO-APIC IRQs
[   36.443340] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   36.588581] Brought up 1 CPUs
[   36.588766] Booting paravirtualized kernel on bare hardware
[   36.588858] Time: 23:37:32  Date: 07/16/107
[   36.588881] NET: Registered protocol family 16
[   36.588947] EISA bus registered
[   36.588950] ACPI: bus type pci registered
[   36.589652] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   36.589654] PCI: Using configuration type 1
[   36.589656] Setting up standard PCI resources
[   36.598374] ACPI: Interpreter enabled
[   36.598376] ACPI: Using IOAPIC for interrupt routing
[   36.599400] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.599404] PCI: Probing PCI hardware (bus 00)
[   36.600462] Boot video device is 0000:01:00.0
[   36.600747] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.619892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   36.623701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   36.623810] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P9._PRT]
[   36.624047] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P8._PRT]
[   36.626151] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   36.626354] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   36.626556] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   36.626759] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   36.627014] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.627218] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.627423] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.627628] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.627700] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.627709] pnp: PnP ACPI init
[   36.631588] pnp: PnP ACPI: found 14 devices
[   36.631592] PnPBIOS: Disabled by ACPI PNP
[   36.631637] PCI: Using ACPI for IRQ routing
[   36.631640] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.644593] NET: Registered protocol family 8
[   36.644595] NET: Registered protocol family 20
[   36.645269] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[   36.645464] PCI: Bridge: 0000:00:01.0
[   36.645466]   IO window: a000-cfff
[   36.645471]   MEM window: ff500000-ff5fffff
[   36.645474]   PREFETCH window: 7ff00000-bfefffff
[   36.645478] PCI: Bridge: 0000:02:00.0
[   36.645479]   IO window: disabled.
[   36.645482]   MEM window: disabled.
[   36.645485]   PREFETCH window: disabled.
[   36.645488] PCI: Bridge: 0000:02:00.1
[   36.645490]   IO window: disabled.
[   36.645493]   MEM window: disabled.
[   36.645495]   PREFETCH window: disabled.
[   36.645499] PCI: Bridge: 0000:00:13.0
[   36.645500]   IO window: disabled.
[   36.645503]   MEM window: disabled.
[   36.645505]   PREFETCH window: disabled.
[   36.645522] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   36.645528] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   36.645540] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   36.645551] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   36.645574] NET: Registered protocol family 2
[   36.676455] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.676614] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   36.677538] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   36.678025] TCP: Hash tables configured (established 131072 bind 65536)
[   36.678027] TCP reno registered
[   36.688481] checking if image is initramfs... it is
[   37.238258] Freeing initrd memory: 6788k freed
[   37.238615] audit: initializing netlink socket (disabled)
[   37.238627] audit(1187307452.272:1): initialized
[   37.238678] highmem bounce pool size: 64 pages
[   37.238728] VFS: Disk quotas dquot_6.5.1
[   37.238743] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.238787] io scheduler noop registered
[   37.238789] io scheduler anticipatory registered
[   37.238791] io scheduler deadline registered
[   37.238799] io scheduler cfq registered (default)
[   37.239034] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   37.239062] assign_interrupt_mode Found MSI capability
[   37.239064] Allocate Port Service[0000:02:00.0:pcie00]
[   37.239138] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   37.239166] assign_interrupt_mode Found MSI capability
[   37.239168] Allocate Port Service[0000:02:00.1:pcie00]
[   37.239279] isapnp: Scanning for PnP cards...
[   37.592546] isapnp: No Plug & Play device found
[   37.615720] Real Time Clock Driver v1.12ac
[   37.615758] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.615860] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.616462] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.616628] mice: PS/2 mouse device common for all mice
[   37.617014] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.617185] input: Macintosh mouse button emulation as /class/input/input0
[   37.617208] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   37.617211] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   37.617446] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   37.617449] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   37.617784] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.617788] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.617866] EISA: Probing bus 0 at eisa.0
[   37.617905] EISA: Detected 0 cards.
[   37.648004] TCP cubic registered
[   37.648014] NET: Registered protocol family 1
[   37.648030] Using IPI No-Shortcut mode
[   37.648095] ACPI: (supports S0 S1 S3 S4 S5)
[   37.648132]   Magic number: 3:237:656
[   37.648492] Freeing unused kernel memory: 328k freed
[   37.650568] Time: tsc clocksource has been installed.
[   37.660922] input: AT Translated Set 2 keyboard as /class/input/input1
[   38.866286] Capability LSM initialized
[   39.190128] ACPI: Processor [CPU1] (supports 16 throttling states)
[   39.190136] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   39.852846] SCSI subsystem initialized
[   39.856745] libata version 2.20 loaded.
[   39.859445] ahci 0000:00:0f.0: version 2.1
[   39.859467] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 16
[   39.876958] usbcore: registered new interface driver usbfs
[   39.876979] usbcore: registered new interface driver hub
[   39.876996] usbcore: registered new device driver usb
[   39.877675] USB Universal Host Controller Interface driver v3.0
[   40.022295] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   40.055273] Floppy drive(s): fd0 is 1.44M
[   40.110389] FDC 0 is a post-1991 82077
[   40.860656] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   40.860661] ahci 0000:00:0f.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   40.860776] ata1: SATA max UDMA/133 cmd 0xf884ad00 ctl 0x00000000 bmdma 0x00000000 irq 16
[   40.860872] ata2: SATA max UDMA/133 cmd 0xf884ad80 ctl 0x00000000 bmdma 0x00000000 irq 16
[   40.860967] ata3: SATA max UDMA/133 cmd 0xf884ae00 ctl 0x00000000 bmdma 0x00000000 irq 16
[   40.861061] ata4: SATA max UDMA/133 cmd 0xf884ae80 ctl 0x00000000 bmdma 0x00000000 irq 16
[   40.861071] scsi0 : ahci
[   41.343747] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   41.388177] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   41.388182] ata1.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[   41.388184] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   41.446367] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   41.446371] ata1.00: configured for UDMA/133
[   41.446378] scsi1 : ahci
[   41.754970] ata2: SATA link down (SStatus 0 SControl 300)
[   41.754979] scsi2 : ahci
[   42.066392] ata3: SATA link down (SStatus 0 SControl 300)
[   42.066401] scsi3 : ahci
[   42.377815] ata4: SATA link down (SStatus 0 SControl 300)
[   42.377899] scsi 0:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[   42.379278] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   42.379299] VP_IDE: chipset revision 7
[   42.379301] VP_IDE: not 100% native mode: will probe irqs later
[   42.379311] VP_IDE: VIA vt8251 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   42.379318]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   42.379329]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   42.379335] Probing IDE interface ide0...
[   42.395795] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   42.395805] sda: Write Protect is off
[   42.395808] sda: Mode Sense: 00 3a 00 00
[   42.395818] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.395858] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   42.395864] sda: Write Protect is off
[   42.395866] sda: Mode Sense: 00 3a 00 00
[   42.395875] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.395877]  sda: sda1 sda2 sda3
[   42.433238] sd 0:0:0:0: Attached scsi disk sda
[   42.436999] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   42.656881] Attempting manual resume
[   42.656885] swsusp: Resume From Partition 8:2
[   42.656886] PM: Checking swsusp image.
[   42.673975] PM: Resume from disk failed.
[   42.702250] kjournald starting.  Commit interval 5 seconds
[   42.702259] EXT3-fs: mounted filesystem with ordered data mode.
[   42.944765] Probing IDE interface ide1...
[   43.807254] hdc: ASUS DRW-1608P3S, ATAPI CD/DVD-ROM drive
[   44.589797] hdd: AOPEN CD-RW CRW4850 1.02 20021009, ATAPI CD/DVD-ROM drive
[   44.646697] ide1 at 0x170-0x177,0x376 on irq 15
[   44.649727] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 17
[   44.649738] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   44.649931] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   44.649955] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000e080
[   44.650052] usb usb1: configuration #1 chosen from 1 choice
[   44.650074] hub 1-0:1.0: USB hub found
[   44.650081] hub 1-0:1.0: 2 ports detected
[   44.753477] ACPI: PCI Interrupt 0000:00:10.1[C] -> GSI 22 (level, low) -> IRQ 18
[   44.753484] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   44.753498] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   44.753518] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000e000
[   44.753578] usb usb2: configuration #1 chosen from 1 choice
[   44.753596] hub 2-0:1.0: USB hub found
[   44.753601] hub 2-0:1.0: 2 ports detected
[   44.857255] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 16
[   44.857261] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   44.857274] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   44.857291] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000dc00
[   44.857356] usb usb3: configuration #1 chosen from 1 choice
[   44.857371] hub 3-0:1.0: USB hub found
[   44.857376] hub 3-0:1.0: 2 ports detected
[   44.961066] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 19
[   44.961072] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   44.961086] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   44.961106] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000d880
[   44.961170] usb usb4: configuration #1 chosen from 1 choice
[   44.961186] hub 4-0:1.0: USB hub found
[   44.961191] hub 4-0:1.0: 2 ports detected
[   45.065077] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 22 (level, low) -> IRQ 18
[   45.065089] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   45.065112] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   45.065145] ehci_hcd 0000:00:10.4: debug port 1
[   45.065153] ehci_hcd 0000:00:10.4: irq 18, io mem 0xff6ff800
[   45.065160] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   45.065219] usb usb5: configuration #1 chosen from 1 choice
[   45.065238] hub 5-0:1.0: USB hub found
[   45.065245] hub 5-0:1.0: 8 ports detected
[   45.168844] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 19
[   45.168915] eth0: VIA Rhine II at 0x1d000, 00:15:f2:30:5d:03, IRQ 19.
[   45.169627] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link cde1.
[   46.354428] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   46.539179] usb 2-2: configuration #1 chosen from 1 choice
[   50.381776] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   50.556963] NET: Registered protocol family 10
[   50.557047] lo: Disabled Privacy Extensions
[   52.077952] Linux agpgart interface v0.102 (c) Dave Jones
[   52.200568] agpgart: Detected AGP bridge 0
[   52.208258] agpgart: AGP aperture is 256M @ 0xd0000000
[   52.216935] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.218289] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.622892] usbcore: registered new interface driver hiddev
[   52.717729] input: Razer Razer Copperhead Laser Mouse as /class/input/input2
[   52.717794] input: USB HID v1.00 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.1-2
[   52.720704] input: Razer Razer Copperhead Laser Mouse as /class/input/input3
[   52.720735] input: USB HID v0.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.1-2
[   52.720745] usbcore: registered new interface driver usbhid
[   52.720748] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   52.771516] input: PC Speaker as /class/input/input4
[   53.019994] parport: PnPBIOS parport detected.
[   53.020103] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   53.035239] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(33)
[   53.035247] Uniform CD-ROM driver Revision: 3.20
[   53.053390] hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   53.406098] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   53.406227] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   54.093805] fuse init (API version 7.8)
[   54.117027] lp0: using parport0 (interrupt-driven).
[   54.146809] Adding 2048276k swap on /dev/disk/by-uuid/b907c779-1322-48c4-aac5-5792a15493c1.  Priority:-1 extents:1 across:2048276k
[   54.260918] EXT3 FS on sda3, internal journal
[   54.489152] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   54.575130] NTFS volume version 3.1.
[   55.878758] NET: Registered protocol family 17
[   59.958218] ibm_acpi: ec object not found
[   60.077623] No dock devices found.
[   60.124490] input: Power Button (FF) as /class/input/input5
[   60.128381] ACPI: Power Button (FF) [PWRF]
[   60.156402] input: Sleep Button (CM) as /class/input/input6
[   60.160327] ACPI: Sleep Button (CM) [SLPB]
[   60.187212] input: Power Button (CM) as /class/input/input7
[   60.191080] ACPI: Power Button (CM) [PWRB]
[   60.203614] Using specific hotkey driver
[   60.278290] pcc_acpi: loading...
[   60.520309] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
[   60.524640] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   60.759673] eth0: no IPv6 routers present
[   65.976332] [drm] Initialized drm 1.1.0 20060810
[   65.982736] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   65.985277] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   66.919065] ppdev: user-space parallel port driver
[   67.632291] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   67.632461] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   67.632523] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[   67.959287] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   67.959292] apm: overridden by ACPI.
[   68.097274] Bluetooth: Core ver 2.11
[   68.097325] NET: Registered protocol family 31
[   68.097327] Bluetooth: HCI device and connection manager initialized
[   68.097331] Bluetooth: HCI socket layer initialized
[   68.125866] Bluetooth: L2CAP ver 2.8
[   68.125870] Bluetooth: L2CAP socket layer initialized
[   68.246536] Bluetooth: RFCOMM socket layer initialized
[   68.246548] Bluetooth: RFCOMM TTY layer initialized
[   68.246550] Bluetooth: RFCOMM ver 1.8
[   75.957146] [drm] Setting GART location based on new memory map
[   75.957156] [drm] Loading R300 Microcode
[   75.957222] [drm] writeback test succeeded in 1 usecs
[ 1163.218497] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount shoW-blocked-tasks

---

### Post by noob12 on 2007-08-16
OK.  You seem to be fine.  If the network is all working now but the LED on the card just isn't coming on, I'm not sure what's causing that.  Could just be a faulty LED or maybe the driver (via-rhine) doesn't do what it needs to for the LED to function.

If **sudo ethtool eth0** says its negotiated the expected rates and the link is detected, I'd leave it at that.  I have no suggestions.

Post if you need help.

---

