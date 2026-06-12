---
title: "wired network connection problem - dchp yes, anything else no"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by kacheng on 2007-12-16
Hi, 
My Ubuntu 7.10 server has been running great until last week. Suddenly I can't connect to anything.

I get an IP address 192.168.1.10.  So the DCHP is working fine.
I get a gateway of 192.168.1.1.

However I can't do anything once I get the IP:

ping hostname works
ping 127.0.0.1 works
ping 192.168.1.10 works 
--
ping 192.168.1.1 doesn't work (gateway)
ping 192.168.1.100 doesn't work (other network computer)
ping [www.google.com](www.google.com) doesn't work
--
ping from another network computer doesn't work
ping from gateway router doesn't work



When I try
/etc/init.d/networking restart
the same still occurs



What does this tell me?
What can I do to troubleshoot further?

---

### Post by f00buntu on 2007-12-16
Hello kacheng,

Please post your dmesg output. In a terminal type:

```
dmesg
```

Any errors?

What type of network card are you using?

---

### Post by kacheng on 2007-12-16
I'm not sure exactly what to look for, but it doesn't seem like there is a problem?

The ethernet port is built-in on the ASUS V8N-CSM motherboard. I think it's NVIDIA chipset.


```
**~$ dmesg | grep eth0**
[   32.546565] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:14.0

**~$ dmesg | grep eth**
[   27.938192] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   32.029432] forcedeth: using HIGHDMA
[   32.546565] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:14.0

**~$ dmesg**
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bfc0000 (usable)
[    0.000000]  BIOS-e820: 000000007bfc0000 - 000000007bfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bfce000 - 000000007bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bff0000 - 000000007c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1087MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 507840) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   507840
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   507840
[    0.000000] On node 0 totalpages: 507840
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2175 pages used for memmap
[    0.000000]   HighMem zone: 276289 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB870 checksum 0
[    0.000000] ACPI: RSDP 000FB870, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7BFC0100, 0044 (r1 A M I  OEMXSDT   4000619 MSFT       97)
[    0.000000] ACPI: FACP 7BFC0290, 00F4 (r3 A M I  OEMFACP   4000619 MSFT       97)
[    0.000000] ACPI: DSDT 7BFC0440, 5683 (r1  A0368 A0368001        1 INTL  2002026)
[    0.000000] ACPI: FACS 7BFCE000, 0040
[    0.000000] ACPI: APIC 7BFC0390, 0070 (r1 A M I  OEMAPIC   4000619 MSFT       97)
[    0.000000] ACPI: MCFG 7BFC0400, 003C (r1 A M I  OEMMCFG   4000619 MSFT       97)
[    0.000000] ACPI: OEMB 7BFCE040, 005B (r1 A M I  AMI_OEM   4000619 MSFT       97)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:7 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7c000000:82c00000)
[    0.000000] Built 1 zonelists.  Total pages: 503873
[    0.000000] Kernel command line: root=UUID=0db753f0-d489-4de6-9fb5-5421132e762c ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.071 MHz processor.
[   24.126775] spurious 8259A interrupt: IRQ7.
[   24.129510] Console: colour VGA+ 80x25
[   24.129809] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   24.130120] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   24.184587] Memory: 2002504k/2031360k available (2015k kernel code, 27648k reserved, 916k data, 364k init, 1113856k highmem)
[   24.184596] virtual kernel memory layout:
[   24.184597]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   24.184598]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.184599]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   24.184600]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   24.184602]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   24.184603]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   24.184604]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   24.184606] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.184638] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.264604] Calibrating delay using timer specific routine.. 4424.08 BogoMIPS (lpj=8848172)
[   24.264626] Security Framework v1.0.0 initialized
[   24.264631] SELinux:  Disabled at boot.
[   24.264641] Mount-cache hash table entries: 512
[   24.264737] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   24.264744] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.264746] CPU: L2 Cache: 1024K (64 bytes/line)
[   24.264748] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   24.264756] Compat vDSO mapped to ffffe000.
[   24.264764] Checking 'hlt' instruction... OK.
[   24.280695] SMP alternatives: switching to UP code
[   24.280843] Freeing SMP alternatives: 11k freed
[   24.281052] Early unpacking initramfs... done
[   24.542945] ACPI: Core revision 20070126
[   24.543001] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.545033] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 01
[   24.545047] Total of 1 processors activated (4424.08 BogoMIPS).
[   24.545342] ENABLING IO-APIC IRQs
[   24.545574] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   24.692361] Brought up 1 CPUs
[   24.692461] Booting paravirtualized kernel on bare hardware
[   24.692510] Time: 16:06:17  Date: 11/16/107
[   24.692525] NET: Registered protocol family 16
[   24.692581] EISA bus registered
[   24.692591] ACPI: bus type pci registered
[   24.693151] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   24.693153] PCI: Using configuration type 1
[   24.693155] Setting up standard PCI resources
[   24.698556] ACPI: EC: Look up EC in DSDT
[   24.702876] ACPI: Interpreter enabled
[   24.702878] ACPI: (supports S0 S1 S3 S4 S5)
[   24.702891] ACPI: Using IOAPIC for interrupt routing
[   24.710779] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.710786] PCI: Probing PCI hardware (bus 00)
[   24.711687] PCI: Transparent bridge - 0000:00:10.0
[   24.711716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.711884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
[   24.711961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
[   24.712038] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[   24.712129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   24.720750] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   24.720923] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *5
[   24.721094] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   24.721270] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *5
[   24.721440] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   24.721611] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   24.721782] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[   24.721952] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   24.722123] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[   24.722294] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[   24.722465] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[   24.722636] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[   24.722806] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   24.722978] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   24.723149] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *5
[   24.723337] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[   24.723508] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[   24.723694] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[   24.723911] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   24.723978] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.723986] pnp: PnP ACPI init
[   24.723990] ACPI: bus type pnp registered
[   24.728410] pnp: PnP ACPI: found 15 devices
[   24.728412] ACPI: ACPI bus type pnp unregistered
[   24.728415] PnPBIOS: Disabled by ACPI PNP
[   24.728443] PCI: Using ACPI for IRQ routing
[   24.728445] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.740512] NET: Registered protocol family 8
[   24.740514] NET: Registered protocol family 20
[   24.740554] pnp: 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   24.740556] pnp: 00:07: iomem range 0xfeb80000-0xfebbffff has been reserved
[   24.740559] pnp: 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[   24.740563] pnp: 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[   24.740566] pnp: 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   24.740570] pnp: 00:0c: ioport range 0x290-0x297 has been reserved
[   24.740574] pnp: 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   24.740578] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   24.740580] pnp: 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[   24.740583] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   24.740585] pnp: 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[   24.744302] Time: tsc clocksource has been installed.
[   24.770757] PCI: Bridge: 0000:00:02.0
[   24.770758]   IO window: disabled.
[   24.770761]   MEM window: disabled.
[   24.770762]   PREFETCH window: disabled.
[   24.770765] PCI: Bridge: 0000:00:03.0
[   24.770766]   IO window: disabled.
[   24.770768]   MEM window: disabled.
[   24.770769]   PREFETCH window: disabled.
[   24.770771] PCI: Bridge: 0000:00:04.0
[   24.770773]   IO window: disabled.
[   24.770774]   MEM window: disabled.
[   24.770776]   PREFETCH window: disabled.
[   24.770779] PCI: Bridge: 0000:00:10.0
[   24.770781]   IO window: c000-cfff
[   24.770784]   MEM window: faa00000-faafffff
[   24.770786]   PREFETCH window: b7f00000-bfefffff
[   24.770795] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.770801] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   24.770806] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.770813] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   24.770823] NET: Registered protocol family 2
[   24.808288] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.808367] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   24.809313] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   24.809630] TCP: Hash tables configured (established 131072 bind 65536)
[   24.809632] TCP reno registered
[   24.820352] checking if image is initramfs... it is
[   25.271962] Switched to high resolution mode on CPU 0
[   25.332555] Freeing initrd memory: 7079k freed
[   25.332820] audit: initializing netlink socket (disabled)
[   25.332829] audit(1197821177.960:1): initialized
[   25.332871] highmem bounce pool size: 64 pages
[   25.334062] VFS: Disk quotas dquot_6.5.1
[   25.334094] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.334152] io scheduler noop registered
[   25.334154] io scheduler anticipatory registered
[   25.334155] io scheduler deadline registered
[   25.334167] io scheduler cfq registered (default)
[   25.334180] Boot video device is 0000:00:05.0
[   25.759590] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.759610] assign_interrupt_mode Found MSI capability
[   25.759612] Allocate Port Service[0000:00:02.0:pcie00]
[   25.759656] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.759674] assign_interrupt_mode Found MSI capability
[   25.759676] Allocate Port Service[0000:00:03.0:pcie00]
[   25.759718] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   25.759737] assign_interrupt_mode Found MSI capability
[   25.759739] Allocate Port Service[0000:00:04.0:pcie00]
[   25.759817] isapnp: Scanning for PnP cards...
[   26.113253] isapnp: No Plug & Play device found
[   26.129217] Real Time Clock Driver v1.12ac
[   26.129281] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.129381] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.129845] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.130290] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.130433] input: Macintosh mouse button emulation as /class/input/input0
[   26.130482] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   26.133567] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.133571] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.133672] mice: PS/2 mouse device common for all mice
[   26.133742] EISA: Probing bus 0 at eisa.0
[   26.133766] EISA: Detected 0 cards.
[   26.133829] TCP cubic registered
[   26.133839] NET: Registered protocol family 1
[   26.133854] Using IPI No-Shortcut mode
[   26.133998]   Magic number: 3:2:136
[   26.134299] Freeing unused kernel memory: 364k freed
[   26.207219] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.311602] AppArmor: AppArmor initialized<5>audit(1197821179.960:2):  type=1505 info="AppArmor initialized" pid=1233
[   27.318263] fuse init (API version 7.8)
[   27.322910] Failure registering capabilities with primary security module.
[   27.338027] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.887881] usbcore: registered new interface driver usbfs
[   27.887901] usbcore: registered new interface driver hub
[   27.887916] usbcore: registered new device driver usb
[   27.888849] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[   27.888859] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 16
[   27.888868] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   27.888871] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   27.888981] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   27.889006] ehci_hcd 0000:00:0b.1: debug port 1
[   27.889010] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   27.889019] ehci_hcd 0000:00:0b.1: irq 16, io mem 0xfebdfc00
[   27.889026] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.889100] usb usb1: configuration #1 chosen from 1 choice
[   27.889121] hub 1-0:1.0: USB hub found
[   27.889127] hub 1-0:1.0: 8 ports detected
[   27.898190] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   27.898194] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   27.909183] SCSI subsystem initialized
[   27.912668] libata version 2.21 loaded.
[   27.938192] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   27.973327] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.017554] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   28.017572] NFORCE-MCP51: chipset revision 161
[   28.017574] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   28.017580] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   28.017588]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   28.017595]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   28.017602] Probing IDE interface ide0...
[   28.052628] Floppy drive(s): fd0 is 1.44M
[   28.111553] FDC 0 is a post-1991 82077
[   28.233597] usb 1-6: new high speed USB device using ehci_hcd and address 2
[   28.305639] hda: ST3250820A, ATA DISK drive
[   28.365869] usb 1-6: configuration #1 chosen from 1 choice
[   28.365982] hub 1-6:1.0: USB hub found
[   28.366066] hub 1-6:1.0: 4 ports detected
[   28.977453] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.978741] Probing IDE interface ide1...
[   29.712546] hdc: PIONEER DVD-RW DVR-105, ATAPI CD/DVD-ROM drive
[   30.495945] hdd: HITACHI CDR-7830, ATAPI CD/DVD-ROM drive
[   30.559126] ide1 at 0x170-0x177,0x376 on irq 15
[   30.586879] sata_nv 0000:00:0e.0: version 3.4
[   30.587165] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[   30.587174] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 17
[   30.587204] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   30.587253] scsi0 : sata_nv
[   30.587400] scsi1 : sata_nv
[   30.587525] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e000 irq 17
[   30.587528] ata2: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001e008 irq 17
[   30.593557] hda: max request size: 512KiB
[   30.623953] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(100)
[   30.648369] hda: cache flushes supported
[   30.648400]  hda: hda1
[   30.680461] hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   30.680467] Uniform CD-ROM driver Revision: 3.20
[   30.707189] hdd: ATAPI 7X CD-ROM drive, 128kB Cache, DMA
[   31.051416] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   31.059652] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/133
[   31.059655] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.067639] ata1.00: configured for UDMA/133
[   31.379153] ata2: SATA link down (SStatus 0 SControl 300)
[   31.389653] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[   31.390171] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
[   31.390180] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 21 (level, low) -> IRQ 18
[   31.390215] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   31.390245] scsi2 : sata_nv
[   31.390358] scsi3 : sata_nv
[   31.390480] ata3: SATA max UDMA/133 cmd 0x0001dc00 ctl 0x0001d882 bmdma 0x0001d400 irq 18
[   31.390484] ata4: SATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d408 irq 18
[   31.698901] ata3: SATA link down (SStatus 0 SControl 300)
[   32.018653] ata4: SATA link down (SStatus 0 SControl 300)
[   32.029416] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   32.029424] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 19
[   32.029428] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   32.029432] forcedeth: using HIGHDMA
[   32.037160] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.037170] sd 0:0:0:0: [sda] Write Protect is off
[   32.037172] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.037183] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.037217] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.037223] sd 0:0:0:0: [sda] Write Protect is off
[   32.037225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.037234] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.037237]  sda: sda1 sda2 < sda5 sda6 sda7 >
[   32.079990] sd 0:0:0:0: [sda] Attached SCSI disk
[   32.083419] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.332483] Attempting manual resume
[   32.332486] swsusp: Resume From Partition 8:5
[   32.332488] PM: Checking swsusp image.
[   32.332638] PM: Resume from disk failed.
[   32.339383] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   32.343134] SGI XFS Quota Management subsystem
[   32.379204] XFS mounting filesystem sda6
[   32.478982] Ending clean XFS mount for filesystem: sda6
[   32.546565] eth0: forcedeth.c: subsystem: 01043:8141 bound to 0000:00:14.0
[   32.546945] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   32.546949] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 16
[   32.546959] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   32.546961] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   32.546983] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   32.546995] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xfebde000
[   32.604256] usb usb2: configuration #1 chosen from 1 choice
[   32.604277] hub 2-0:1.0: USB hub found
[   32.604284] hub 2-0:1.0: 8 ports detected
[   32.706504] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[   32.706512] ACPI: PCI Interrupt 0000:04:05.0[A] -> Link [LNKD] -> GSI 19 (level, low) -> IRQ 20
[   32.759244] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[faaff800-faafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   34.033156] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000067a83e]
[   41.531552] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   41.531575] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   41.772358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.881728] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.986005] Linux agpgart interface v0.102 (c) Dave Jones
[   42.225817] Linux video capture interface: v2.00
[   42.284411] ivtv:  ==================== START INIT IVTV ====================
[   42.284414] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   42.284473] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   42.284787] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   42.284796] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [LNKB] -> GSI 18 (level, low) -> IRQ 21
[   42.524250] parport_pc 00:06: reported by Plug and Play ACPI
[   42.524372] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   42.540336] nvidia: module license 'NVIDIA' taints kernel.
[   42.812795] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 17
[   42.812806] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNEC] -> GSI 17 (level, low) -> IRQ 22
[   42.812813] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   42.864441] input: PC Speaker as /class/input/input2
[   42.995388] logips2pp: Detected unknown logitech mouse model 127
[   43.062800] ivtv0: loaded v4l-cx2341x-enc.fw firmware (4160317728 bytes)
[   43.133323] ivtv0: loaded v4l-cx2341x-dec.fw firmware (4160317736 bytes)
[   43.353860] ivtv0: Encoder revision: 0x02060039
[   43.361870] ivtv0: Decoder revision: 0x02020023
[   43.418593] tveeprom 2-0050: Hauppauge model 48132, rev J323, serial# 7113513
[   43.418596] tveeprom 2-0050: tuner model is Philips FM1236 (idx 23, type 2)
[   43.418599] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   43.418601] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[   43.418603] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   43.418605] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   43.418608] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   43.448730] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   43.482775] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   43.502578] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   43.703826] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   43.726576] msp3400 2-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   43.726579] msp3400 2-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[   43.726670] tuner 2-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   43.996756] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   43.996863] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   43.996983] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   43.997039] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   43.997163] ivtv0: Registered device radio0 for encoder radio
[   43.997183] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   43.997216] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   43.997405] ivtv0: Registered device vbi16 for decoder VOUT
[   43.997432] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   44.077813] ivtv0: loaded v4l-cx2341x-init.mpg firmware (4152500256 bytes)
[   44.301186] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   44.301205] ivtv:  ====================  END INIT IVTV  ====================
[   44.301270] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   44.302366] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   44.302370] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 17
[   44.302385] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   45.773217] lp0: using parport0 (interrupt-driven).
[   45.842925] lirc_dev: IR Remote Control driver registered, at major 61 
[   45.925391] bttv: driver version 0.9.17 loaded
[   45.925395] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   45.999136] cx2388x v4l2 driver version 0.0.6 loaded
[   46.003354] lirc_i2c: chip 0x10020 found @ 0x18 (Hauppauge IR)
[   46.003371] lirc_dev: lirc_register_plugin: sample_rate: 10
[   46.065238] Adding 979924k swap on /dev/sda5.  Priority:-1 extents:1 across:979924k
[   46.837901] kjournald starting.  Commit interval 5 seconds
[   46.843303] EXT3 FS on sda1, internal journal
[   46.843307] EXT3-fs: mounted filesystem with ordered data mode.
[   46.934424] XFS mounting filesystem sda7
[   47.188289] Ending clean XFS mount for filesystem: sda7
[   47.275026] XFS mounting filesystem hda1
[   47.383442] Ending clean XFS mount for filesystem: hda1
[   49.813226] No dock devices found.
[   49.893571] input: Power Button (FF) as /class/input/input4
[   49.897078] ACPI: Power Button (FF) [PWRF]
[   49.930529] input: Power Button (CM) as /class/input/input5
[   49.934008] ACPI: Power Button (CM) [PWRB]
[   50.299728] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (version 2.00.00)
[   50.299759] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   50.299761] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   50.299763] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   50.299765] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   53.734715] ppdev: user-space parallel port driver
[   54.170797] audit(1197821207.034:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5273 profile="/usr/sbin/cupsd"
[   54.410341] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   54.410345] apm: overridden by ACPI.
[   54.745765] Netfilter messages via NETLINK v0.30.
[   54.762837] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   54.823904] ip_tables: (C) 2000-2006 Netfilter Core Team
[   61.180829] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   61.374600] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   61.374865] NFSD: starting 90-second grace period
[   38.128000] Marking TSC unstable due to: cpufreq changes.
[   38.132000] Time: acpi_pm clocksource has been installed.
[   38.484000] Clocksource tsc unstable (delta = -197041913 ns)
[   40.788000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   40.788000] vboxdrv: Successfully done.
[   41.992000] Failure registering capabilities with primary security module.
[   47.220000] NET: Registered protocol family 17
```

---

### Post by f00buntu on 2007-12-17
Did you set up custom iptables rules? 

```
iptables -v --list
```

Does a ping to your router result in an arp cache entry?

```
ping -c2 192.168.1.1
arp -a
```

Sniff traffic to your router with tcpdump or tshark while running a ping:

```
sudo tcpdump -i eth0
```

Any response from your router? Try the same for a dhcp request:

```
sudo dhclient3 eth0
```

---

### Post by kacheng on 2007-12-17
Your suggestion reminded me that I upgraded moblock, which sets iptables rules.

I uninstalled moblock and connectivity is restored!  Thanks.

---

