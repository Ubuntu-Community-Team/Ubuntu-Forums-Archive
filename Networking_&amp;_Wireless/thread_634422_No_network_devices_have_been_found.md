---
title: "No network devices have been found"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by rshields on 2007-12-07
Hi, I upgraded from Feisty to Gutsy and the upgrade completed successfully, but I have no network interfaces. Network Manager says "No network devices have been found" and ifconfig just shows lo and irda0. I have to boot an old kernel (2.6.20-15-generic) but even then Network Manager doesn't work, I have to use the "manual configuration" to get my wireless working. I can't find anything in syslog. I have no idea what's going on, where should I be looking for clues? Thanks.

---

### Post by rshields on 2007-12-07
OK, the wired interface (eth1) seems to be working. There's no wireless interface showing up. It's an ipw8945 chipset.

My ifconfig
```

eth1      Link encap:Ethernet  HWaddr 00:16:D3:30:24:5A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 Memory:ee000000-ee020000 

eth1:avah Link encap:Ethernet  HWaddr 00:16:D3:30:24:5A  
          inet addr:169.254.4.159  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1848 (1.8 KB)  TX bytes:1848 (1.8 KB)

```

My dmesg:
```

[    0.000000] Linux version 2.6.22-14-386 (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Sun Oct 14 22:36:54 GMT 2007 (Ubuntu 2.6.22-14.46-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6df000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6df000 - 000000007f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6800
[    0.000000] Entering add_active_range(0, 0, 521936) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521936
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521936
[    0.000000] On node 0 totalpages: 521936
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2285 pages used for memmap
[    0.000000]   HighMem zone: 290275 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F67C0 checksum 0
[    0.000000] ACPI: RSDP 000F67C0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 7F6D19D9, 0084 (r1 LENOVO TP-7B        2030  LTP        0)
[    0.000000] ACPI: FACP 7F6D1B00, 00F4 (r3 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT 7F6D1F32, CE5A (r1 LENOVO TP-7B        2030 MSFT  100000E)
[    0.000000] ACPI: FACS 7F6F4000, 0040
[    0.000000] ACPI: SSDT 7F6D1CB4, 027E (r1 LENOVO TP-7B        2030 MSFT  100000E)
[    0.000000] ACPI: ECDT 7F6DED8C, 0052 (r1 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI: TCPA 7F6DEDDE, 0032 (r2 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI: APIC 7F6DEE10, 0068 (r1 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI: MCFG 7F6DEE78, 003C (r1 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI: HPET 7F6DEEB4, 0038 (r1 LENOVO TP-7B        2030 LNVO        1)
[    0.000000] ACPI: BOOT 7F6DEFD8, 0028 (r1 LENOVO TP-7B        2030  LTP        1)
[    0.000000] ACPI: SSDT 7F6F2645, 025F (r1 LENOVO TP-7B        2030 INTL 20050513)
[    0.000000] ACPI: SSDT 7F6F28A4, 00A6 (r1 LENOVO TP-7B        2030 INTL 20050513)
[    0.000000] ACPI: SSDT 7F6F294A, 04F7 (r1 LENOVO TP-7B        2030 INTL 20050513)
[    0.000000] ACPI: SSDT 7F6F2E41, 01D8 (r1 LENOVO TP-7B        2030 INTL 20050513)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] Built 1 zonelists.  Total pages: 517859
[    0.000000] Kernel command line: root=UUID=8e80daa6-e21d-4b36-bea7-cc81d718edf4 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.665 MHz processor.
[   16.685565] Console: colour VGA+ 80x25
[   16.685813] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.686170] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.763449] Memory: 2058804k/2087744k available (1929k kernel code, 27764k reserved, 877k data, 348k init, 1170240k highmem)
[   16.763458] virtual kernel memory layout:
[   16.763460]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   16.763461]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.763462]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.763464]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.763465]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   16.763466]       .data : 0xc02e25d5 - 0xc03bda04   ( 877 kB)
[   16.763468]       .text : 0xc0100000 - 0xc02e25d5   (1929 kB)
[   16.763471] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.763516] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.763665] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.763669] hpet0: 3 64-bit timers, 14318180 Hz
[   16.844565] Calibrating delay using timer specific routine.. 3328.59 BogoMIPS (lpj=6657196)
[   16.844586] Security Framework v1.0.0 initialized
[   16.844593] SELinux:  Disabled at boot.
[   16.844599] Mount-cache hash table entries: 512
[   16.844696] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   16.844703] monitor/mwait feature present.
[   16.844705] using mwait in idle threads.
[   16.844709] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.844712] CPU: L2 cache: 2048K
[   16.844714] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   16.844722] Compat vDSO mapped to ffffe000.
[   16.844733] CPU: Intel(R) Core(TM) Duo CPU      L2400  @ 1.66GHz stepping 0c
[   16.844738] Checking 'hlt' instruction... OK.
[   16.861041] Early unpacking initramfs... done
[   17.206653] ACPI: Core revision 20070126
[   17.206754] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.234322] ENABLING IO-APIC IRQs
[   17.234520] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.379806] Booting paravirtualized kernel on bare hardware
[   17.379887] Time: 22:09:48  Date: 11/07/107
[   17.379905] NET: Registered protocol family 16
[   17.379968] EISA bus registered
[   17.379972] ACPI: bus type pci registered
[   17.380098] PCI: PCI BIOS revision 2.10 entry at 0xfd82b, last bus=24
[   17.380100] PCI: Using configuration type 1
[   17.380102] Setting up standard PCI resources
[   17.383657] ACPI: EC: Found ECDT
[   17.394167] ACPI: Interpreter enabled
[   17.394170] ACPI: (supports S0 S3 S4 S5)
[   17.394186] ACPI: Using IOAPIC for interrupt routing
[   17.403560] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   17.403606] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.403614] PCI: Probing PCI hardware (bus 00)
[   17.404340] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   17.404345] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   17.405607] PCI: Transparent bridge - 0000:00:1e.0
[   17.405746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.405939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   17.406079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   17.406219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   17.406361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   17.406502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   17.409521] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[   17.409754] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   17.409991] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   17.410220] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   17.410450] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   17.410679] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   17.410909] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   17.411138] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   17.411434] ACPI: Power Resource [PUBS] (on)
[   17.411449] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.411457] pnp: PnP ACPI init
[   17.411462] ACPI: bus type pnp registered
[   17.415700] pnp: PnP ACPI: found 14 devices
[   17.415703] ACPI: ACPI bus type pnp unregistered
[   17.415706] PnPBIOS: Disabled by ACPI PNP
[   17.415741] PCI: Using ACPI for IRQ routing
[   17.415743] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.479176] NET: Registered protocol family 8
[   17.479178] NET: Registered protocol family 20
[   17.479222] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   17.479226] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   17.479229] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   17.479232] pnp: 00:00: iomem range 0xc8000-0xcbfff has been reserved
[   17.479237] pnp: 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   17.479241] pnp: 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   17.479244] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   17.479247] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   17.479593] Time: tsc clocksource has been installed.
[   17.479606] Switched to high resolution mode on CPU 0
[   17.509455] PCI: Bridge: 0000:00:1c.0
[   17.509458]   IO window: 2000-2fff
[   17.509464]   MEM window: ee000000-ee0fffff
[   17.509469]   PREFETCH window: disabled.
[   17.509474] PCI: Bridge: 0000:00:1c.1
[   17.509477]   IO window: 3000-4fff
[   17.509483]   MEM window: ec000000-edffffff
[   17.509487]   PREFETCH window: e4000000-e40fffff
[   17.509493] PCI: Bridge: 0000:00:1c.2
[   17.509496]   IO window: 5000-6fff
[   17.509502]   MEM window: e8000000-e9ffffff
[   17.509507]   PREFETCH window: e4100000-e41fffff
[   17.509512] PCI: Bridge: 0000:00:1c.3
[   17.509515]   IO window: 7000-8fff
[   17.509521]   MEM window: ea000000-ebffffff
[   17.509526]   PREFETCH window: e4200000-e42fffff
[   17.509535] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   17.509537]   IO window: 00009000-000090ff
[   17.509542]   IO window: 00009400-000094ff
[   17.509548]   PREFETCH window: e0000000-e3ffffff
[   17.509553]   MEM window: 88000000-8bffffff
[   17.509558] PCI: Bridge: 0000:00:1e.0
[   17.509561]   IO window: 9000-cfff
[   17.509567]   MEM window: e4300000-e7ffffff
[   17.509572]   PREFETCH window: e0000000-e3ffffff
[   17.509600] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[   17.509607] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.509629] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[   17.509635] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.509657] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[   17.509663] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.509685] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[   17.509691] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.509701] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   17.509707] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.509725] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   17.509732] PCI: Setting latency timer of device 0000:15:00.0 to 64
[   17.509742] NET: Registered protocol family 2
[   17.547482] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.547534] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.548273] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   17.548481] TCP: Hash tables configured (established 131072 bind 65536)
[   17.548484] TCP reno registered
[   17.559564] checking if image is initramfs... it is
[   18.240937] Freeing initrd memory: 7065k freed
[   18.241036] Simple Boot Flag at 0x35 set to 0x1
[   18.241321] audit: initializing netlink socket (disabled)
[   18.241333] audit(1197065389.348:1): initialized
[   18.241388] highmem bounce pool size: 64 pages
[   18.243012] VFS: Disk quotas dquot_6.5.1
[   18.243022] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.243100] io scheduler noop registered
[   18.243102] io scheduler anticipatory registered
[   18.243104] io scheduler deadline registered
[   18.243118] io scheduler cfq registered (default)
[   18.243129] Boot video device is 0000:00:02.0
[   18.243286] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.243340] assign_interrupt_mode Found MSI capability
[   18.243343] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.243372] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.243461] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.243514] assign_interrupt_mode Found MSI capability
[   18.243517] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.243542] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.243630] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   18.243683] assign_interrupt_mode Found MSI capability
[   18.243685] Allocate Port Service[0000:00:1c.2:pcie00]
[   18.243711] Allocate Port Service[0000:00:1c.2:pcie02]
[   18.243798] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.243851] assign_interrupt_mode Found MSI capability
[   18.243853] Allocate Port Service[0000:00:1c.3:pcie00]
[   18.243883] Allocate Port Service[0000:00:1c.3:pcie02]
[   18.244016] isapnp: Scanning for PnP cards...
[   18.598150] isapnp: No Plug & Play device found
[   18.617447] hpet_resources: 0xfed00000 is busy
[   18.617484] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.618514] pnp: Device 00:0a activated.
[   18.618717] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.619297] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.619453] input: Macintosh mouse button emulation as /class/input/input0
[   18.619522] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   18.630723] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.630728] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.630855] mice: PS/2 mouse device common for all mice
[   18.630939] EISA: Probing bus 0 at eisa.0
[   18.630947] Cannot allocate resource for EISA slot 1
[   18.630950] Cannot allocate resource for EISA slot 2
[   18.630952] Cannot allocate resource for EISA slot 3
[   18.630954] Cannot allocate resource for EISA slot 4
[   18.630957] Cannot allocate resource for EISA slot 5
[   18.630959] Cannot allocate resource for EISA slot 6
[   18.630961] Cannot allocate resource for EISA slot 7
[   18.630963] Cannot allocate resource for EISA slot 8
[   18.630965] EISA: Detected 0 cards.
[   18.631049] TCP cubic registered
[   18.631060] NET: Registered protocol family 1
[   18.631080] Using IPI Shortcut mode
[   18.631229]   Magic number: 3:513:198
[   18.631269]   hash matches device ttypd
[   18.631497] Freeing unused kernel memory: 348k freed
[   18.697523] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.813205] AppArmor: AppArmor initialized<5>audit(1197065390.924:2):  type=1505 info="AppArmor initialized" pid=1169
[   19.820821] fuse init (API version 7.8)
[   19.825832] Failure registering capabilities with primary security module.
[   19.844703] ACPI: SSDT 7F6F1D26, 0240 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   19.844966] ACPI: SSDT 7F6F1FEB, 065A (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   19.845891] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.845895] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.960000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.960000] ACPI: Thermal Zone [THM0] (46 C)
[    2.964000] Time: hpet clocksource has been installed.
[    2.964000] ACPI: Thermal Zone [THM1] (47 C)
[    3.392000] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[    3.392000] Copyright (c) 1999-2006 Intel Corporation.
[    3.392000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.392000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.428000] usbcore: registered new interface driver usbfs
[    3.428000] usbcore: registered new interface driver hub
[    3.428000] usbcore: registered new device driver usb
[    3.428000] USB Universal Host Controller Interface driver v3.0
[    3.484000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:16:d3:30:24:5a
[    3.512000] SCSI subsystem initialized
[    3.516000] libata version 2.21 loaded.
[    3.656000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.656000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.656000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.656000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.656000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.656000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[    3.656000] usb usb1: configuration #1 chosen from 1 choice
[    3.656000] hub 1-0:1.0: USB hub found
[    3.656000] hub 1-0:1.0: 2 ports detected
[    3.760000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.760000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.760000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.760000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.760000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[    3.760000] usb usb2: configuration #1 chosen from 1 choice
[    3.760000] hub 2-0:1.0: USB hub found
[    3.760000] hub 2-0:1.0: 2 ports detected
[    3.864000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.864000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.864000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.864000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.864000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001860
[    3.864000] usb usb3: configuration #1 chosen from 1 choice
[    3.864000] hub 3-0:1.0: USB hub found
[    3.864000] hub 3-0:1.0: 2 ports detected
[    3.968000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 23
[    3.968000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.968000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.968000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.968000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001880
[    3.968000] usb usb4: configuration #1 chosen from 1 choice
[    3.968000] hub 4-0:1.0: USB hub found
[    3.968000] hub 4-0:1.0: 2 ports detected
[    4.072000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    4.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.072000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.072000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.072000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.072000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.072000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee444000
[    4.076000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.076000] usb usb5: configuration #1 chosen from 1 choice
[    4.076000] hub 5-0:1.0: USB hub found
[    4.076000] hub 5-0:1.0: 8 ports detected
[    4.180000] ahci 0000:00:1f.2: version 2.2
[    4.180000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[    4.904000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[    5.036000] usb 5-6: configuration #1 chosen from 1 choice
[    5.036000] hub 5-6:1.0: USB hub found
[    5.036000] hub 5-6:1.0: 4 ports detected
[    5.184000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[    5.184000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.184000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.184000] scsi0 : ahci
[    5.184000] scsi1 : ahci
[    5.184000] scsi2 : ahci
[    5.184000] scsi3 : ahci
[    5.184000] ata1: SATA max UDMA/133 cmd 0xf88be500 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.184000] ata2: SATA max UDMA/133 cmd 0xf88be580 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.184000] ata3: SATA max UDMA/133 cmd 0xf88be600 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.184000] ata4: SATA max UDMA/133 cmd 0xf88be680 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.620000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    5.668000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.668000] ata1.00: ATA-7: HTS541080G9SA00, MB4IC60R, max UDMA/100
[    5.668000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.668000] ata1.00: configured for UDMA/100
[    5.792000] usb 3-1: configuration #1 chosen from 1 choice
[    5.980000] ata2: SATA link down (SStatus 0 SControl 0)
[    6.036000] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    6.212000] usb 4-2: configuration #1 chosen from 1 choice
[    6.224000] usbcore: registered new interface driver hiddev
[    6.236000] input: Logitech Optical USB Mouse as /class/input/input2
[    6.236000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.2-1
[    6.236000] usbcore: registered new interface driver usbhid
[    6.236000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.292000] ata3: SATA link down (SStatus 0 SControl 0)
[    6.604000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.604000] scsi 0:0:0:0: Direct-Access     ATA      HTS541080G9SA00  MB4I PQ: 0 ANSI: 5
[    6.608000] ata_piix 0000:00:1f.1: version 2.11
[    6.608000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 20
[    6.608000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.608000] scsi4 : ata_piix
[    6.608000] scsi5 : ata_piix
[    6.608000] ata5: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    6.608000] ata6: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    6.616000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.616000] sd 0:0:0:0: [sda] Write Protect is off
[    6.616000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.616000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.616000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    6.616000] sd 0:0:0:0: [sda] Write Protect is off
[    6.616000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.616000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.616000]  sda:<6>ata5.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4247N, 1.01, max UDMA/33
[    6.976000]  sda1 sda2 sda3
[    6.992000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.996000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.100000] ata5.00: configured for UDMA/33
[    7.100000] ata6: port disabled. ignoring.
[    7.104000] scsi 4:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4247N 1.01 PQ: 0 ANSI: 5
[    7.104000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    7.104000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[    7.104000] PCI: Setting latency timer of device 0000:15:00.1 to 64
[    7.156000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e4301000-e43017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    7.188000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    7.188000] Uniform CD-ROM driver Revision: 3.20
[    7.188000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.284000] Attempting manual resume
[    7.284000] swsusp: Resume From Partition 8:3
[    7.284000] PM: Checking swsusp image.
[    7.284000] PM: Resume from disk failed.
[    8.436000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4060045205a]
[   15.880000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.924000] agpgart: Detected an Intel 945GM Chipset.
[   15.924000] agpgart: Detected 7932K stolen memory.
[   15.936000] agpgart: AGP aperture is 256M @ 0xd0000000
[   15.984000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.024000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.588000] NET: Registered protocol family 17
[   16.640000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:201c]
[   16.768000] Yenta: ISA IRQ mask 0x04b8, PCI irq 20
[   16.768000] Socket status: 30000006
[   16.768000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
[   16.768000] cs: IO port probe 0x9000-0xcfff: clean.
[   16.768000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   16.768000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   16.828000] ieee80211_crypt: registered algorithm 'NULL'
[   16.828000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.828000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.872000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   16.872000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.872000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   16.872000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.872000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   17.256000] sdhci: Secure Digital Host Controller Interface driver
[   17.256000] sdhci: Copyright(c) Pierre Ossman
[   17.304000] iTCO_vendor_support: vendor-support=0
[   17.312000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   17.312000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.312000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.548000] input: PC Speaker as /class/input/input3
[   17.684000] Real Time Clock Driver v1.12ac
[   17.700000] intel_rng: FWH not detected
[   17.800000] irda_init()
[   17.800000] NET: Registered protocol family 23
[   17.860000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.880000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   17.884000] parport_pc 00:0b: reported by Plug and Play ACPI
[   17.884000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   17.984000] pnp: Device 00:0c activated.
[   17.984000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   17.984000] nsc-ircc, chip->init
[   17.984000] nsc-ircc, Found chip at base=0x164e
[   17.984000] nsc-ircc, driver loaded (Dag Brattli)
[   17.984000] IrDA: Registered device irda0
[   17.984000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   17.984000] nsc-ircc, chip->init
[   17.984000] nsc-ircc, Found chip at base=0x02e
[   17.984000] nsc-ircc, driver loaded (Dag Brattli)
[   17.984000] nsc_ircc_open(), can't get iobase of 0x2f8
[   18.568000] cs: IO port probe 0x100-0x3af: clean.
[   18.568000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.568000] cs: IO port probe 0x820-0x8ff: clean.
[   18.568000] cs: IO port probe 0xc00-0xcf7: clean.
[   18.692000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 18)
[   18.692000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   18.692000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   18.692000] mmc0: SDHCI at 0xe4301800 irq 22 DMA
[   18.708000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   18.708000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   18.708000] cs: IO port probe 0xa00-0xaff: clean.
[   28.008000] lp0: using parport0 (interrupt-driven).
[   28.072000] Adding 3903784k swap on /dev/sda3.  Priority:-1 extents:1 across:3903784k
[   34.528000] ACPI: AC Adapter [AC] (on-line)
[   34.580000] ACPI: Battery Slot [BAT0] (battery present)
[   34.612000] ACPI: ACPI Dock Station Driver 
[   34.612000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   34.616000] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   34.616000] ACPI: Error installing bay notify handler
[   34.616000] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   34.676000] input: Power Button (FF) as /class/input/input5
[   34.680000] ACPI: Power Button (FF) [PWRF]
[   34.720000] input: Lid Switch as /class/input/input6
[   34.724000] ACPI: Lid Switch [LID]
[   34.768000] input: Sleep Button (CM) as /class/input/input7
[   34.772000] ACPI: Sleep Button (CM) [SLPB]
[   37.808000] [drm] Initialized drm 1.1.0 20060810
[   37.812000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   37.812000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.624000] NET: Registered protocol family 10
[   38.624000] lo: Disabled Privacy Extensions
[   38.624000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.036000] ppdev: user-space parallel port driver
[   39.344000] audit(1197065427.695:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4951 profile="/usr/sbin/cupsd"
[   39.448000] apm: BIOS not found.
[   39.604000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   39.604000] thinkpad_acpi: http://ibm-acpi.sf.net/
[   39.604000] thinkpad_acpi: ThinkPad EC firmware 7BHT36WW-1.09
[   41.320000] Failure registering capabilities with primary security module.

```

---

### Post by rshields on 2007-12-07
Everything works fine if I boot the 2.6.22-14-generic kernel.

---

### Post by FoxOne on 2007-12-07
is this a pci device?

---

### Post by rshields on 2007-12-08
It's an on board wireless controller in my laptop (Thinkpad X60s). The controller is an ipw3945.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
**03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)

```

The driver is loaded properly into the 2.6.22-14 kernel, but there's no eth0 (wireless) interface.

```

$ lsmod | grep ipw
ipw3945               119840  1 
ieee80211              35656  1 ipw3945

```

---

### Post by rshields on 2007-12-08
OK, I've fixed the problem. I needed to install linux-restricted-modules-386 to get /sbin/ipw3945d-2.6.22-14-386 installed.

---

