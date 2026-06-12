---
title: "Strange wlan problem asus eee on ubuntu 8.04"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Kossu on 2008-04-06
Hello,

I seem to have a odd problem. I followed this tutorial to change the kernel and install madwifi drivers 
[http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to:_use_custom_Eee_Linux_kernel](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to:_use_custom_Eee_Linux_kernel)

The wlan card appears in the network tab, and it can find my access point and connect to it, iwconfig shows thats its connected to my access point. However my access point doesnt see my asus eee associating with it. and no data is coming thru :S

I suspected it was ipv6 making it not work, however i blacklisted it and its still not working :S

any help is greatly appreciated
-Kossu

ifconfig reports:
ath0      Link encap:Ethernet  HWaddr 00:15:af:75:f5:bb  
          inet addr:10.0.0.114  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe75:f5bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1739 (1.6 KB)  TX bytes:5893 (5.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:94:79:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73000 (71.2 KB)  TX bytes:73000 (71.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-75-F5-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:1
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:42731 (41.7 KB)  TX bytes:13720 (13.3 KB)
          Interrupt:18

and dmesg

[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f780000 (usable)
[    0.000000]  BIOS-e820: 000000001f780000 - 000000001f790000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f790000 - 000000001f7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7d0000 - 000000001f7de000 (reserved)
[    0.000000]  BIOS-e820: 000000001f7e0000 - 000000001f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 128896) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128896
[    0.000000]   HighMem    128896 ->   128896
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128896
[    0.000000] On node 0 totalpages: 128896
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123825 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FBE60 checksum 0
[    0.000000] ACPI: RSDP 000FBE60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F780000, 0034 (r1 A M I  OEMRSDT   1000808 MSFT       97)
[    0.000000] ACPI: FACP 1F780200, 0081 (r1 A M I  OEMFACP   1000808 MSFT       97)
[    0.000000] ACPI: DSDT 1F780400, 5F2B (r1  A0797 A0797000        0 INTL 20051117)
[    0.000000] ACPI: FACS 1F790000, 0040
[    0.000000] ACPI: APIC 1F780390, 0068 (r1 A M I  OEMAPIC   1000808 MSFT       97)
[    0.000000] ACPI: OEMB 1F790040, 0046 (r1 A M I  AMI_OEM   1000808 MSFT       97)
[    0.000000] ACPI: MCFG 1F786330, 003C (r1 A M I  OEMMCFG   1000808 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df600000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127889
[    0.000000] Kernel command line: root=UUID=bc20ce7b-1e15-4c59-b8fd-3f0c07369fb9 ro quiet splash clocksource=hpet
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 630.089 MHz processor.
[   12.152553] Console: colour VGA+ 80x25
[   12.152563] console [tty0] enabled
[   12.152854] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.153343] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.180691] Memory: 500060k/515584k available (1771k kernel code, 14864k reserved, 979k data, 332k init, 0k highmem)
[   12.180712] virtual kernel memory layout:
[   12.180715]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   12.180718]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.180722]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   12.180725]     lowmem  : 0xc0000000 - 0xdf780000   ( 503 MB)
[   12.180728]       .init : 0xc03b5000 - 0xc0408000   ( 332 kB)
[   12.180731]       .data : 0xc02baf48 - 0xc03afd64   ( 979 kB)
[   12.180734]       .text : 0xc0100000 - 0xc02baf48   (1771 kB)
[   12.180746] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.180830] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.260862] Calibrating delay using timer specific routine.. 1261.74 BogoMIPS (lpj=2523497)
[   12.260920] Security Framework initialized
[   12.260931] SELinux:  Disabled at boot.
[   12.260940] Capability LSM initialized
[   12.260976] Mount-cache hash table entries: 512
[   12.261264] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000 00000000
[   12.261295] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.261302] CPU: L2 cache: 512K
[   12.261311] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000 00000000
[   12.261334] Compat vDSO mapped to ffffe000.
[   12.261362] Checking 'hlt' instruction... OK.
[   12.277481] SMP alternatives: switching to UP code
[   12.282365] Freeing SMP alternatives: 11k freed
[   12.282647] Early unpacking initramfs... done
[   13.182326] ACPI: Core revision 20070126
[   13.182517] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.401490] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 08
[   13.401548] Total of 1 processors activated (1261.74 BogoMIPS).
[   13.401723] ENABLING IO-APIC IRQs
[   13.401966] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   13.548870] Brought up 1 CPUs
[   13.548927] CPU0 attaching sched-domain:
[   13.548934]  domain 0: span 01
[   13.548939]   groups: 01
[   13.549368] net_namespace: 64 bytes
[   13.549393] Booting paravirtualized kernel on bare hardware
[   13.550597] Time: 13:24:15  Date: 04/06/08
[   13.550740] NET: Registered protocol family 16
[   13.551279] EISA bus registered
[   13.551317] ACPI: bus type pci registered
[   13.551831] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   13.551837] PCI: Using configuration type 1
[   13.551842] Setting up standard PCI resources
[   13.576343] ACPI: EC: Look up EC in DSDT
[   13.604317] ACPI: Interpreter enabled
[   13.604326] ACPI: (supports S0 S1 S3 S4 S5)
[   13.604370] ACPI: Using IOAPIC for interrupt routing
[   13.621118] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[   13.621126] ACPI: EC: driver started in poll mode
[   13.621671] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.622705] Force enabled HPET at base address 0xfed00000
[   13.622718] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   13.622729] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   13.623691] PCI: Transparent bridge - 0000:00:1e.0
[   13.623785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.624204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   13.624444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   13.624676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   13.635408] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   13.635766] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   13.636115] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   13.636463] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   13.636860] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.637219] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.637569] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   13.637918] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   13.638291] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.638381] pnp: PnP ACPI init
[   13.638405] ACPI: bus type pnp registered
[   13.643644] pnp: PnP ACPI: found 13 devices
[   13.643652] ACPI: ACPI bus type pnp unregistered
[   13.643663] PnPBIOS: Disabled by ACPI PNP
[   13.644238] PCI: Using ACPI for IRQ routing
[   13.644246] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.664842] NET: Registered protocol family 8
[   13.664849] NET: Registered protocol family 20
[   13.665278] hpet clockevent registered
[   13.665289] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.665300] hpet0: 3 64-bit timers, 14318180 Hz
[   13.668758] Time: hpet clocksource has been installed.
[   13.668780] Switched to high resolution mode on CPU 0
[   13.676809] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   13.676836] system 00:08: ioport range 0x380-0x383 has been reserved
[   13.676844] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   13.676852] system 00:08: ioport range 0x800-0x87f has been reserved
[   13.676859] system 00:08: ioport range 0x480-0x4bf has been reserved
[   13.676868] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   13.676876] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   13.676885] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.676901] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   13.676910] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.676925] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[   13.676939] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[   13.676954] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   13.676963] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[   13.676971] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   13.676979] system 00:0c: iomem range 0x100000-0x1f7fffff could not be reserved
[   13.676988] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   13.708196] PCI: Bridge: 0000:00:1c.0
[   13.708202]   IO window: disabled.
[   13.708211]   MEM window: disabled.
[   13.708218]   PREFETCH window: disabled.
[   13.708227] PCI: Bridge: 0000:00:1c.1
[   13.708231]   IO window: disabled.
[   13.708240]   MEM window: fbf00000-fbffffff
[   13.708247]   PREFETCH window: disabled.
[   13.708256] PCI: Bridge: 0000:00:1c.2
[   13.708260]   IO window: disabled.
[   13.708269]   MEM window: f8000000-fbefffff
[   13.708277]   PREFETCH window: f0000000-f6ffffff
[   13.708286] PCI: Bridge: 0000:00:1e.0
[   13.708290]   IO window: disabled.
[   13.708298]   MEM window: disabled.
[   13.708304]   PREFETCH window: disabled.
[   13.708353] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.708367] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.708397] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 17 (level, low) -> IRQ 17
[   13.708409] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.708439] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.708450] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.708468] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.708495] NET: Registered protocol family 2
[   13.744840] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   13.745350] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   13.745619] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   13.745881] TCP: Hash tables configured (established 16384 bind 16384)
[   13.745888] TCP reno registered
[   13.757008] checking if image is initramfs... it is
[   15.523996] Freeing initrd memory: 6762k freed
[   15.525522] audit: initializing netlink socket (disabled)
[   15.525557] audit(1207488257.020:1): initialized
[   15.531016] VFS: Disk quotas dquot_6.5.1
[   15.531214] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.531621] AppArmor: Unable to register AppArmor
[   15.531742] io scheduler noop registered
[   15.531747] io scheduler anticipatory registered
[   15.531753] io scheduler deadline registered
[   15.531788] io scheduler cfq registered (default)
[   15.531829] Boot video device is 0000:00:02.0
[   15.532233] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.532295] assign_interrupt_mode Found MSI capability
[   15.532379] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.532495] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.532662] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.532722] assign_interrupt_mode Found MSI capability
[   15.532773] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.532873] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.533037] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.533097] assign_interrupt_mode Found MSI capability
[   15.533147] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.533241] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.533651] isapnp: Scanning for PnP cards...
[   15.887704] isapnp: No Plug & Play device found
[   15.978969] Real Time Clock Driver v1.12ac
[   15.979215] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.982444] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.982651] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.982912] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.013585] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.013598] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.024454] mice: PS/2 mouse device common for all mice
[   16.024764] EISA: Probing bus 0 at eisa.0
[   16.024817] EISA: Detected 0 cards.
[   16.024825] cpuidle: using governor ladder
[   16.024830] cpuidle: using governor menu
[   16.025045] TCP cubic registered
[   16.025068] NET: Registered protocol family 1
[   16.025135] Using IPI No-Shortcut mode
[   16.025410]   Magic number: 4:190:432
[   16.025992] Freeing unused kernel memory: 332k freed
[   16.060322] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.626410] fuse init (API version 7.9)
[   17.661870] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   17.661887] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.665660] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.671240] ACPI: Thermal Zone [TZ00] (47 C)
[   19.683490] usbcore: registered new interface driver usbfs
[   19.683546] usbcore: registered new interface driver hub
[   19.705736] usbcore: registered new device driver usb
[   19.736382] USB Universal Host Controller Interface driver v3.0
[   19.736520] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   19.736544] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.736554] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.737078] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.737133] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e400
[   19.737467] usb usb1: configuration #1 chosen from 1 choice
[   19.737531] hub 1-0:1.0: USB hub found
[   19.737545] hub 1-0:1.0: 2 ports detected
[   19.840534] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 20
[   19.840559] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.840569] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.840638] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.840683] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000e480
[   19.840975] usb usb2: configuration #1 chosen from 1 choice
[   19.841037] hub 2-0:1.0: USB hub found
[   19.841052] hub 2-0:1.0: 2 ports detected
[   19.944510] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.944536] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.944545] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.944607] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.944653] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   19.944930] usb usb3: configuration #1 chosen from 1 choice
[   19.944992] hub 3-0:1.0: USB hub found
[   19.945005] hub 3-0:1.0: 2 ports detected
[   20.048470] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   20.048499] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   20.048508] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   20.048568] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   20.048615] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
[   20.048905] usb usb4: configuration #1 chosen from 1 choice
[   20.048967] hub 4-0:1.0: USB hub found
[   20.048980] hub 4-0:1.0: 2 ports detected
[   20.080749] SCSI subsystem initialized
[   20.102609] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   20.152565] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   20.152597] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.152607] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.152672] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   20.156612] ehci_hcd 0000:00:1d.7: debug port 1
[   20.156624] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.156642] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf7eb7c00
[   20.208231] libata version 3.00 loaded.
[   20.232242] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.232537] usb usb5: configuration #1 chosen from 1 choice
[   20.232600] hub 5-0:1.0: USB hub found
[   20.232617] hub 5-0:1.0: 8 ports detected
[   20.337000] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 20
[   20.337082] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.337108] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   20.380953] ata_piix 0000:00:1f.2: version 2.12
[   20.380969] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   20.381010] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 20
[   20.381085] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.412199] scsi0 : ata_piix
[   20.428138] scsi1 : ata_piix
[   20.428460] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   20.428469] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   20.628198] usb 1-2: device not accepting address 2, error -71
[   20.756590] ata2.00: ATA-4: SILICONMOTION SM223AC, , max UDMA/66
[   20.756601] ata2.00: 7815024 sectors, multi 0: LBA
[   20.756640] ata2.00: limited to UDMA/33 due to 40-wire cable
[   20.772592] ata2.00: configured for UDMA/33
[   20.772885] scsi 1:0:0:0: Direct-Access     ATA      SILICONMOTION SM n/a  PQ: 0 ANSI: 5
[   21.364079] usb 5-5: new high speed USB device using ehci_hcd and address 3
[   21.497245] usb 5-5: configuration #1 chosen from 1 choice
[   21.692970] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[   21.693003] sd 1:0:0:0: [sda] Write Protect is off
[   21.693011] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.693054] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   21.693183] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors (4001 MB)
[   21.693208] sd 1:0:0:0: [sda] Write Protect is off
[   21.693214] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.693255] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   21.693264]  sda: sda1
[   21.694172] sd 1:0:0:0: [sda] Attached SCSI disk
[   21.710243] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   21.735964] usb 5-8: new high speed USB device using ehci_hcd and address 4
[   21.837510] usb 5-8: configuration #1 chosen from 1 choice
[   21.839513] usbcore: registered new interface driver libusual
[   21.853851] Initializing USB Mass Storage driver...
[   22.066550] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   22.095385] Clocksource tsc unstable (delta = -64506379 ns)
[   22.183830] usb 1-2: configuration #1 chosen from 1 choice
[   22.191913] scsi2 : SCSI emulation for USB Mass Storage devices
[   22.192136] usbcore: registered new interface driver usb-storage
[   22.192146] USB Mass Storage support registered.
[   22.192454] usb-storage: device found at 3
[   22.192460] usb-storage: waiting for device to settle before scanning
[   26.243774] Linux agpgart interface v0.102
[   26.307431] agpgart: Detected an Intel 915GM Chipset.
[   26.307875] agpgart: Detected 7932K stolen memory.
[   26.478348] usb-storage: device scan complete
[   26.479016] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[   26.480887] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   26.481051] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   26.518416] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.606298] agpgart: AGP aperture is 256M @ 0xd0000000
[   26.606362] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.318182] intel_rng: FWH not detected
[   27.874461] input: Power Button (FF) as /devices/virtual/input/input2
[   27.888540] ACPI: Power Button (FF) [PWRF]
[   27.888878] input: Lid Switch as /devices/virtual/input/input3
[   27.898160] ACPI: Lid Switch [LID]
[   27.898382] input: Sleep Button (CM) as /devices/virtual/input/input4
[   27.910034] ACPI: Sleep Button (CM) [SLPB]
[   27.910237] input: Power Button (CM) as /devices/virtual/input/input5
[   27.922024] ACPI: Power Button (CM) [PWRB]
[   28.038102] iTCO_vendor_support: vendor-support=0
[   28.106053] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   28.106358] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   28.106462] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.073486] Attansic(R) L2 Ethernet Network Driver - version 1.0.40.2
[   31.073496] Copyright (c) 2006 Attansic Corporation.
[   31.073691] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   31.073715] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   31.218121] ath_hal: module license 'Proprietary' taints kernel.
[   31.297433] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[   31.673316] wlan: 0.8.4.2 (svn r2756)
[   31.730253] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   31.861304] ath_pci: 0.9.4.5 (svn r2756)
[   31.862250] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   31.862272] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   32.489656] ACPI: AC Adapter [AC0] (on-line)
[   32.622174] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   32.633105] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.437132] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   33.437182] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.465180] ACPI: Battery Slot [BAT0] (battery present)
[   37.163541] usbcore: registered new interface driver hiddev
[   37.178573] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   37.207853] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input8
[   37.217058] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:1d.0-2
[   37.217102] usbcore: registered new interface driver usbhid
[   37.217112] /exports/tmp/linux-2.6.24/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   37.264637] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   37.531367] Linux video capture interface: v2.00
[   37.585015] uvcvideo: Found UVC 1.00 device <unnamed> (eb1a:2761)
[   37.592384] usbcore: registered new interface driver uvcvideo
[   37.592396] USB Video Class driver (v0.1.0)
[   37.772671] ath_pci: switching rfkill capability off
[   37.864782] ath_rate_sample: 1.2 (svn r2756)
[   37.865041] ath_pci: switching per-packet transmit power control off
[   37.865806] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   37.865820] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   37.865845] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   37.865855] wifi0: mac 14.2 phy 7.0 radio 10.2
[   37.865866] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   37.865872] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   37.865878] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   37.865883] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   37.865888] wifi0: Use hw queue 8 for CAB traffic
[   37.865893] wifi0: Use hw queue 9 for beacons
[   37.955197] wifi0: Atheros 5424/2424: mem=0xfbef0000, irq=18
[   41.857465] lp: driver loaded but no devices found
[   43.035939] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.771957] No dock devices found.
[   45.903267] ppdev: user-space parallel port driver
[   47.631934] Bluetooth: Core ver 2.11
[   47.632338] NET: Registered protocol family 31
[   47.632346] Bluetooth: HCI device and connection manager initialized
[   47.632357] Bluetooth: HCI socket layer initialized
[   47.688818] Bluetooth: L2CAP ver 2.9
[   47.688828] Bluetooth: L2CAP socket layer initialized
[   47.780884] Bluetooth: RFCOMM socket layer initialized
[   47.781695] Bluetooth: RFCOMM TTY layer initialized
[   47.781709] Bluetooth: RFCOMM ver 1.8
[   48.182713] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   50.004435] NET: Registered protocol family 17
[   50.987653] [drm] Initialized drm 1.1.0 20060810
[   50.996841] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.997517] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   52.612173] NET: Registered protocol family 10
[   52.613067] lo: Disabled Privacy Extensions
[   58.589670] ath0: no IPv6 routers present
[   58.856831] eth0: no IPv6 routers present
[  128.436592] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  129.121786] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  129.122305] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  132.921636] eth0: no IPv6 routers present
[  149.415337] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  149.927797] ATL2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  149.928318] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  153.879201] eth0: no IPv6 routers present
[  158.003336] ATL2: eth0 NIC Link is Down

---

