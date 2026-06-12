---
title: "Upgraded to Gutsy, get IP but no internet"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by ManOnOneWheel on 2007-10-21
I've been using the gutsy beta for a few weeks now, and when the final release came out i did a fresh install. Everything has been going well unitl this morning. When I turned on my computer I discovered I could not connect to the internet. 

I tried resetting the connection, unplugging the cable and plugging it back in, and so forth. both the little lights on my ethernet jack are on. I can ping google, but when i try to use a browser i get 'Refused the connection". I can even ping my desktop(broken internet) with my laptop(on seperate wireless network). 

The internet work in windows, so i know the jack is not the problem. I'm frustrated because the internet was working perfect last night before i shut down. I have an IP address as show by ifconfig

```
 eth0      Link encap:Ethernet  HWaddr 00:19:DB:6D:A7:45  
          inet addr:144.118.195.7  Bcast:144.118.207.255  Mask:255.255.240.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:492352 (480.8 KB)  TX bytes:5486 (5.3 KB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:632 (632.0 b)  TX bytes:632 (632.0 b)
 
```

and my dmesg shows this weird loop involving network stuff that i do not understand.

Here is the first 'regular' part

```
 [    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=20848c16-fc38-4ee1-a14b-9ae35f0fe53d ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffde000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffde000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F8480 checksum 0
[    0.000000] ACPI: RSDP 000F8480, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFD0000, 0038 (r1 A M I  OEMRSDT   2000709 MSFT       97)
[    0.000000] ACPI: FACP 7FFD0200, 0084 (r2 A M I  OEMFACP   2000709 MSFT       97)
[    0.000000] ACPI: DSDT 7FFD0450, 4A23 (r1  1ADKV 1ADKV000        0 INTL 20051117)
[    0.000000] ACPI: FACS 7FFDE000, 0040
[    0.000000] ACPI: APIC 7FFD0390, 0080 (r1 A M I  OEMAPIC   2000709 MSFT       97)
[    0.000000] ACPI: MCFG 7FFD0410, 003C (r1 A M I  OEMMCFG   2000709 MSFT       97)
[    0.000000] ACPI: OEMB 7FFDE040, 0061 (r1 A M I  AMI_OEM   2000709 MSFT       97)
[    0.000000] ACPI: HPET 7FFD4E80, 0038 (r1 A M I  OEMHPET0  2000709 MSFT       97)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffd0000
[    0.000000] Entering add_active_range(0, 0, 155) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      155
[    0.000000]     0:      256 ->   524240
[    0.000000] On node 0 totalpages: 524139
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2814 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513033 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515847
[    0.000000] Kernel command line: root=UUID=20848c16-fc38-4ee1-a14b-9ae35f0fe53d ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   26.631076] time.c: Detected 2333.329 MHz processor.
[   26.632276] Console: colour VGA+ 80x25
[   26.632291] Checking aperture...
[   26.632304] Calgary: detecting Calgary via BIOS EBDA area
[   26.632306] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   26.647573] Memory: 2055388k/2096960k available (2274k kernel code, 41168k reserved, 1181k data, 296k init)
[   26.647611] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   26.724039] Calibrating delay using timer specific routine.. 4671.76 BogoMIPS (lpj=9343524)
[   26.724065] Security Framework v1.0.0 initialized
[   26.724071] SELinux:  Disabled at boot.
[   26.724235] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   26.725358] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.726305] Mount-cache hash table entries: 256
[   26.726415] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.726418] CPU: L2 cache: 4096K
[   26.726420] CPU 0/0 -> Node 0
[   26.726421] using mwait in idle threads.
[   26.726423] CPU: Physical Processor ID: 0
[   26.726424] CPU: Processor Core ID: 0
[   26.726429] CPU0: Thermal monitoring enabled (TM1)
[   26.726437] SMP alternatives: switching to UP code
[   26.726711] Early unpacking initramfs... done
[   27.025841] ACPI: Core revision 20070126
[   27.025873] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.068649] Using local APIC timer interrupts.
[   27.111424] result 20833300
[   27.111426] Detected 20.833 MHz APIC timer.
[   27.115308] SMP alternatives: switching to SMP code
[   27.115372] Booting processor 1/2 APIC 0x1
[   27.125872] Initializing CPU#1
[   27.203092] Calibrating delay using timer specific routine.. 4666.81 BogoMIPS (lpj=9333627)
[   27.203097] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.203099] CPU: L2 cache: 4096K
[   27.203100] CPU 1/1 -> Node 0
[   27.203102] CPU: Physical Processor ID: 0
[   27.203103] CPU: Processor Core ID: 1
[   27.203107] CPU1: Thermal monitoring enabled (TM1)
[   27.203502] Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
[   27.203514] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   27.227057] Brought up 2 CPUs
[   27.273629] migration_cost=13
[   27.273757] NET: Registered protocol family 16
[   27.273817] ACPI: bus type pci registered
[   27.273822] PCI: Using configuration type 1
[   27.276220] ACPI: EC: Look up EC in DSDT
[   27.280170] ACPI: Interpreter enabled
[   27.280172] ACPI: (supports S0 S1 S3 S4 S5)
[   27.280187] ACPI: Using IOAPIC for interrupt routing
[   27.287303] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.287307] PCI: Probing PCI hardware (bus 00)
[   27.289240] PCI: Transparent bridge - 0000:00:10.0
[   27.289290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.289481] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   27.289599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   27.289674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[   27.289749] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[   27.299571] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   27.299736] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[   27.299898] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   27.300060] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *5
[   27.300222] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[   27.300384] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   27.300546] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[   27.301098] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   27.301261] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[   27.301422] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[   27.301583] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[   27.301744] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[   27.301933] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[   27.302095] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[   27.302260] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[   27.302425] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[   27.302588] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[   27.302773] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *5
[   27.302986] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   27.303061] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.303069] pnp: PnP ACPI init
[   27.303076] ACPI: bus type pnp registered
[   27.306941] pnp: PnP ACPI: found 15 devices
[   27.306943] ACPI: ACPI bus type pnp unregistered
[   27.306981] PCI: Using ACPI for IRQ routing
[   27.306983] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.307088] NET: Registered protocol family 8
[   27.307090] NET: Registered protocol family 20
[   27.307103] PCI-GART: No AMD northbridge found.
[   27.307111] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   27.307114] hpet0: 3 32-bit timers, 25000000 Hz
[   27.308155] pnp: 00:07: iomem range 0x0-0x0 could not be reserved
[   27.308158] pnp: 00:07: iomem range 0xfee01000-0xfeefffff has been reserved
[   27.308162] pnp: 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   27.308164] pnp: 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.308169] pnp: 00:0c: ioport range 0xa00-0xadf has been reserved
[   27.308171] pnp: 00:0c: ioport range 0xae0-0xaef has been reserved
[   27.308175] pnp: 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   27.308181] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   27.308183] pnp: 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   27.308185] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   27.308187] pnp: 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[   27.308408] PCI: Bridge: 0000:00:03.0
[   27.308410]   IO window: c000-cfff
[   27.308412]   MEM window: fa000000-fe9fffff
[   27.308415]   PREFETCH window: d0000000-dfffffff
[   27.308418] PCI: Bridge: 0000:00:06.0
[   27.308419]   IO window: d000-dfff
[   27.308422]   MEM window: fea00000-feafffff
[   27.308424]   PREFETCH window: disabled.
[   27.308427] PCI: Bridge: 0000:00:07.0
[   27.308428]   IO window: disabled.
[   27.308430]   MEM window: disabled.
[   27.308432]   PREFETCH window: disabled.
[   27.308434] PCI: Bridge: 0000:00:10.0
[   27.308437]   IO window: e000-efff
[   27.308442]   MEM window: feb00000-febfffff
[   27.308445]   PREFETCH window: disabled.
[   27.308457] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   27.308464] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   27.308471] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.308483] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   27.308491] NET: Registered protocol family 2
[   27.310882] Time: tsc clocksource has been installed.
[   27.363117] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   27.363649] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   27.366290] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   27.366709] TCP: Hash tables configured (established 262144 bind 65536)
[   27.366711] TCP reno registered
[   27.379266] checking if image is initramfs... it is
[   27.970905] Freeing initrd memory: 7725k freed
[   27.973807] audit: initializing netlink socket (disabled)
[   27.973821] audit(1192976406.292:1): initialized
[   27.975353] VFS: Disk quotas dquot_6.5.1
[   27.975389] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   27.975453] io scheduler noop registered
[   27.975455] io scheduler anticipatory registered
[   27.975456] io scheduler deadline registered
[   27.975524] io scheduler cfq registered (default)
[   28.012128] Boot video device is 0000:01:00.0
[   28.012236] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   28.012264] assign_interrupt_mode Found MSI capability
[   28.012266] Allocate Port Service[0000:00:03.0:pcie00]
[   28.012327] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   28.012355] assign_interrupt_mode Found MSI capability
[   28.012356] Allocate Port Service[0000:00:06.0:pcie00]
[   28.012411] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   28.012439] assign_interrupt_mode Found MSI capability
[   28.012441] Allocate Port Service[0000:00:07.0:pcie00]
[   28.027269] Real Time Clock Driver v1.12ac
[   28.027400] hpet_resources: 0xfed00000 is busy
[   28.027429] Linux agpgart interface v0.102 (c) Dave Jones
[   28.027431] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.027554] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.027989] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.028493] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.028586] input: Macintosh mouse button emulation as /class/input/input0
[   28.028641] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   28.030806] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.030810] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.030926] mice: PS/2 mouse device common for all mice
[   28.031026] TCP cubic registered
[   28.031075] NET: Registered protocol family 1
[   28.031244] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   28.031250] Freeing unused kernel memory: 296k freed
[   29.158225] AppArmor: AppArmor initialized<5>audit(1192976407.472:2):  type=1505 info="AppArmor initialized" pid=1255
[   29.161788] fuse init (API version 7.8)
[   29.164533] Failure registering capabilities with primary security module.
[   29.187086] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] -  75, should be 7C [20070126]
[   29.187092] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  6A, should be 65 [20070126]
[   29.187096] ACPI: SSDT 7FFD4EC0, 02E3 (r1    AMI   CPU1PM        1 INTL 20051117)
[   29.187268] ACPI: SSDT 7FFD51B0, 02DA (r1    AMI   CPU2PM        1 INTL 20051117)
[   29.187393] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.187400] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.521639] usbcore: registered new interface driver usbfs
[   29.521660] usbcore: registered new interface driver hub
[   29.521684] usbcore: registered new device driver usb
[   29.526573] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.526874] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   29.526880] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 23
[   29.528115] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.528120] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   29.528216] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   29.528233] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf9fff000
[   29.534619] SCSI subsystem initialized
[   29.537753] libata version 2.21 loaded.
[   29.566937] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.566941] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.583897] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   29.587611] usb usb1: configuration #1 chosen from 1 choice
[   29.587725] hub 1-0:1.0: USB hub found
[   29.587733] hub 1-0:1.0: 8 ports detected
[   29.694471] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[   29.694477] ACPI: PCI Interrupt 0000:04:09.0[A] -> Link [LNKD] -> GSI 19 (level, low) -> IRQ 19
[   29.746553] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   29.753195] sata_sil24 0000:02:00.0: version 0.9
[   29.753442] ACPI: PCI Interrupt Link [LNEC] enabled at IRQ 18
[   29.753446] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNEC] -> GSI 18 (level, low) -> IRQ 18
[   29.755192] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   29.756149] scsi0 : sata_sil24
[   29.756184] ata1: SATA max UDMA/100 cmd 0xffffc20000ac4000 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 18
[   30.002911] usb 1-3: new low speed USB device using ohci_hcd and address 2
[   30.067454] ata1: SATA link down (SStatus 0 SControl 300)
[   30.067550] sata_nv 0000:00:0e.0: version 3.4
[   30.067840] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[   30.067844] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 22 (level, low) -> IRQ 22
[   30.068573] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   30.068906] scsi1 : sata_nv
[   30.068947] scsi2 : sata_nv
[   30.069001] ata2: SATA max UDMA/133 cmd 0x000000000001b800 ctl 0x000000000001b482 bmdma 0x000000000001b000 irq 22
[   30.069005] ata3: SATA max UDMA/133 cmd 0x000000000001b400 ctl 0x000000000001b082 bmdma 0x000000000001b008 irq 22
[   30.242116] usb 1-3: configuration #1 chosen from 1 choice
[   30.538490] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.546925] ata2.00: ATA-7: WDC WD2000JS-22NCB1, 10.02E02, max UDMA/133
[   30.546927] ata2.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   30.550588] usb 1-6: new low speed USB device using ohci_hcd and address 3
[   30.555019] ata2.00: configured for UDMA/133
[   30.772067] usb 1-6: configuration #1 chosen from 1 choice
[   30.864552] ata3: SATA link down (SStatus 0 SControl 300)
[   30.875597] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2000JS-22N 10.0 PQ: 0 ANSI: 5
[   30.876095] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 21
[   30.876099] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSA1] -> GSI 21 (level, low) -> IRQ 21
[   30.876826] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   30.876874] scsi3 : sata_nv
[   30.877081] scsi4 : sata_nv
[   30.877243] ata4: SATA max UDMA/133 cmd 0x000000000001ac00 ctl 0x000000000001a882 bmdma 0x000000000001a400 irq 21
[   30.877247] ata5: SATA max UDMA/133 cmd 0x000000000001a800 ctl 0x000000000001a482 bmdma 0x000000000001a408 irq 21
[   31.035749] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0010b9f701224a6a]
[   31.036201] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[000010dc0107a345]
[   31.047026] scsi5 : SBP-2 IEEE-1394
[   31.190893] ata4: SATA link down (SStatus 0 SControl 300)
[   31.512455] ata5: SATA link down (SStatus 0 SControl 300)
[   31.523755] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 20
[   31.523760] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 20 (level, low) -> IRQ 20
[   31.524489] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   31.524494] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   31.524549] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   31.524578] ehci_hcd 0000:00:0b.1: debug port 1
[   31.524583] PCI: cache line size of 32 is not supported by device 0000:00:0b.1
[   31.524593] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xf9ffec00
[   31.524604] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.524638] usb 1-3: USB disconnect, address 2
[   31.524673] usb usb2: configuration #1 chosen from 1 choice
[   31.524694] hub 2-0:1.0: USB hub found
[   31.524699] hub 2-0:1.0: 8 ports detected
[   31.629418] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   31.629439] NFORCE-MCP51: chipset revision 161
[   31.629441] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   31.629446] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   31.629452] NFORCE-MCP51: 0000:00:0d.0 (rev a1) UDMA133 controller
[   31.629460]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:pio, hdb:pio
[   31.629470]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   31.629476] Probing IDE interface ide0...
[   31.653373] usb 1-6: USB disconnect, address 3
[   32.065852] ieee1394: sbp2: Logged into SBP-2 device
[   32.066061] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   32.067292] scsi 5:0:1:0: Direct-Access     Maxtor   OneTouch         0200 PQ: 0 ANSI: 4
[   32.070171] sd 1:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   32.070179] sd 1:0:0:0: [sda] Write Protect is off
[   32.070181] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.070191] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.070226] sd 1:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   32.070232] sd 1:0:0:0: [sda] Write Protect is off
[   32.070234] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.070244] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.070247]  sda: sda1 sda2 sda3 sda4
[   32.087784] sd 1:0:0:0: [sda] Attached SCSI disk
[   32.088496] sd 5:0:1:0: [sdb] 320171008 512-byte hardware sectors (163928 MB)
[   32.088874] sd 5:0:1:0: [sdb] Write Protect is off
[   32.088876] sd 5:0:1:0: [sdb] Mode Sense: 27 00 00 00
[   32.089190] sd 5:0:1:0: [sdb] Cache data unavailable
[   32.089191] sd 5:0:1:0: [sdb] Assuming drive cache: write through
[   32.089855] sd 5:0:1:0: [sdb] 320171008 512-byte hardware sectors (163928 MB)
[   32.090258] sd 5:0:1:0: [sdb] Write Protect is off
[   32.090260] sd 5:0:1:0: [sdb] Mode Sense: 27 00 00 00
[   32.090544] sd 5:0:1:0: [sdb] Cache data unavailable
[   32.090546] sd 5:0:1:0: [sdb] Assuming drive cache: write through
[   32.090548]  sdb: sdb1
[   32.103949] sd 5:0:1:0: [sdb] Attached SCSI disk
[   32.105929] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   32.105943] sd 5:0:1:0: Attached scsi generic sg1 type 0
[   32.200863] Probing IDE interface ide1...
[   32.457905] usb 1-3: new low speed USB device using ohci_hcd and address 4
[   32.697310] usb 1-3: configuration #1 chosen from 1 choice
[   32.937125] hdc: PHILIPS SPD2413P, ATAPI CD/DVD-ROM drive
[   33.005526] usb 1-6: new low speed USB device using ohci_hcd and address 5
[   33.225261] usb 1-6: configuration #1 chosen from 1 choice
[   33.610434] ide1 at 0x170-0x177,0x376 on irq 15
[   33.623367] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[   33.623370] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 23 (level, low) -> IRQ 23
[   33.623376] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   33.623382] forcedeth: using HIGHDMA
[   33.629267] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   33.629274] Uniform CD-ROM driver Revision: 3.20
[   34.145501] eth0: forcedeth.c: subsystem: 01462:7350 bound to 0000:00:14.0
[   34.159778] usbcore: registered new interface driver hiddev
[   34.173318] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input1
[   34.173327] input: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:0b.0-3
[   34.188426] input: Microsoft Comfort Curve Keyboard 2000 as /class/input/input2
[   34.188432] input: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:0b.0-3
[   34.194502] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   34.194517] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
[   34.194525] usbcore: registered new interface driver usbhid
[   34.194528] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.415460] Attempting manual resume
[   34.415462] swsusp: Resume From Partition 8:1
[   34.415463] PM: Checking swsusp image.
[   34.415592] PM: Resume from disk failed.
[   34.441135] kjournald starting.  Commit interval 5 seconds
[   34.441142] EXT3-fs: mounted filesystem with ordered data mode.
[   38.924550] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.940813] Netfilter messages via NETLINK v0.30.
[   38.946006] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   40.418921] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   40.418937] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[   40.474158] input: PC Speaker as /class/input/input4
[   40.534327] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.536214] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.677055] usbcore: registered new interface driver xpad
[   40.677059] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   40.717858] parport_pc 00:06: reported by Plug and Play ACPI
[   40.717922] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   40.744673] nvidia: module license 'NVIDIA' taints kernel.
[   40.997536] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 17
[   40.997542] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNEA] -> GSI 17 (level, low) -> IRQ 17
[   40.997549] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   40.997623] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.19  Wed Sep 12 14:08:38 PDT 2007
[   41.127955] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   41.127958] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 22
[   41.128893] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   41.338607] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   41.738549] lp0: using parport0 (interrupt-driven).
[   41.798894] Adding 4249152k swap on /dev/sda1.  Priority:-1 extents:1 across:4249152k
[   42.219110] EXT3 FS on sda2, internal journal
[   42.694383] kjournald starting.  Commit interval 5 seconds
[   42.694600] EXT3 FS on sda3, internal journal
[   42.694603] EXT3-fs: mounted filesystem with ordered data mode.
[   43.548531] No dock devices found.
[   43.568420] input: Power Button (FF) as /class/input/input5
[   43.568551] ACPI: Power Button (FF) [PWRF]
[   43.569217] input: Power Button (CM) as /class/input/input6
[   43.569344] ACPI: Power Button (CM) [PWRB]
[   44.733928] ppdev: user-space parallel port driver
[   44.846640] audit(1192990824.165:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5315 profile="/usr/sbin/cupsd"
[   49.522522] NET: Registered protocol family 17
  
```

And here is the weird network stuff that goes on forever

```
 [  146.444728] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=62.65.215.198 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=116 ID=21193 PROTO=UDP SPT=32800 DPT=49156 LEN=111 
[  287.330751] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=218.111.180.49 DST=144.118.195.7 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=12944 PROTO=UDP SPT=23950 DPT=49156 LEN=70 
[  333.051380] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.103 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=7485 DF PROTO=TCP SPT=45549 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  336.041998] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.103 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=7486 DF PROTO=TCP SPT=45549 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  336.042280] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.99 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=38363 DF PROTO=TCP SPT=60355 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  339.036127] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.99 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=38364 DF PROTO=TCP SPT=60355 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  339.036415] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=33044 DF PROTO=TCP SPT=58078 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  339.510517] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=206.253.159.115 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x20 TTL=116 ID=7226 PROTO=UDP SPT=50715 DPT=49156 LEN=111 
[  342.030257] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.104 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=33045 DF PROTO=TCP SPT=58078 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  342.030528] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.147 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=32349 DF PROTO=TCP SPT=48753 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  345.024384] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=64.233.161.147 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=32350 DF PROTO=TCP SPT=48753 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  360.880586] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=209.44.123.21 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=16880 DF PROTO=TCP SPT=50685 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  363.875013] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=209.44.123.21 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=16881 DF PROTO=TCP SPT=50685 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  365.077514] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=193.239.179.89 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=116 ID=16169 PROTO=UDP SPT=60906 DPT=49156 LEN=111 
[  365.709836] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=80.190.233.5 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=42289 DF PROTO=TCP SPT=50152 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  368.703630] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=80.190.233.5 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=42290 DF PROTO=TCP SPT=50152 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  370.754703] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=144.118.31.81 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=37423 DF PROTO=TCP SPT=42919 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
[  373.748251] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=144.118.31.81 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=37424 DF PROTO=TCP SPT=42919 DPT=443 WINDOW=5840 RES=0x00 SYN URGP=0 
[  375.304823] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=69.63.176.16 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=33002 DF PROTO=TCP SPT=55428 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  378.298649] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=69.63.176.16 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=33003 DF PROTO=TCP SPT=55428 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  380.248607] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=66.165.70.6 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=43246 DF PROTO=TCP SPT=42175 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  383.243832] Outbound IN= OUT=eth0 SRC=144.118.195.7 DST=66.165.70.6 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=43247 DF PROTO=TCP SPT=42175 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
[  448.112838] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=80.196.119.66 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=110 ID=39778 PROTO=UDP SPT=11024 DPT=49156 LEN=111 
[  464.471589] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=68.45.94.28 DST=144.118.195.7 LEN=119 TOS=0x00 PREC=0x20 TTL=109 ID=26453 PROTO=UDP SPT=6881 DPT=49156 LEN=99 
[  490.413964] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=190.21.101.230 DST=144.118.195.7 LEN=90 TOS=0x00 PREC=0x00 TTL=46 ID=3547 PROTO=UDP SPT=3 DPT=49156 LEN=70 
[  500.606644] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=60.234.251.14 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=113 ID=487 PROTO=UDP SPT=61295 DPT=49156 LEN=111 
[  546.150185] usb 2-7: USB disconnect, address 4
[  548.415709] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=68.55.201.49 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x20 TTL=109 ID=59675 PROTO=UDP SPT=16144 DPT=49156 LEN=111 
[  755.355438] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=62.51.60.65 DST=144.118.195.7 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1223 DF PROTO=TCP SPT=19714 DPT=49156 WINDOW=65535 RES=0x00 SYN URGP=0 
[  758.279343] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=62.51.60.65 DST=144.118.195.7 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=1545 DF PROTO=TCP SPT=19714 DPT=49156 WINDOW=65535 RES=0x00 SYN URGP=0 
[  764.358569] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=62.51.60.65 DST=144.118.195.7 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=2208 DF PROTO=TCP SPT=19714 DPT=49156 WINDOW=65535 RES=0x00 SYN URGP=0 
[  827.182703] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=87.242.28.240 DST=144.118.195.7 LEN=134 TOS=0x00 PREC=0x00 TTL=111 ID=1307 PROTO=UDP SPT=48388 DPT=49156 LEN=114 
[  830.184490] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=124.109.66.24 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=109 ID=31515 PROTO=UDP SPT=24063 DPT=49156 LEN=111 
[  839.495893] Inbound IN=eth0 OUT= MAC=00:19:db:6d:a7:45:00:18:73:0d:30:00:08:00 SRC=213.142.128.62 DST=144.118.195.7 LEN=131 TOS=0x00 PREC=0x00 TTL=114 ID=41629 PROTO=UDP SPT=51184 DPT=49156 LEN=111  
```

I'm pretty desperte to get my internet working again if any one can point me in the right direction

---

### Post by ManOnOneWheel on 2007-10-21
please? i cant find anything else like this.

---

### Post by Dafydd on 2007-10-24
it's frustrating, but i am in the same position. i get an ip number, but cannot connect on my home network (with wep for the wireless or with the wired connect - d-link router).

strangely, it seems to work at work and on another unprotected wireless network.

daf

---

### Post by teslaw on 2007-10-28
Try to disable IPv6 networking - if it's an option for You -  it helped me connect my old PC to the network (newer PC and laptop don't seem to care about it being enabled).

---

### Post by the_nz_monkey on 2007-10-29
Hi guys, similar issue here, too:

Gutsy desktop with wired network sharing worked with Feisty/XP notebook, but fresh installing notebook to Gutsy left me able to access desktop IP and dig web addresses, but not connect using any update (apt-get or synaptic), or firefox.

And in the process of following other posts - disabling ipv6 (or fiddling with the DNS on the desktop to see if that was giving me issues), I've hosed the whole lot :( 

Well, not true, I have desktop internet, but I think that my masquerade might have taken a beating.

But, hey, I've only been going in circles for a few hours so far ](*,)

I'm going to sleep on it, and see what else I can throw at the notebook tomorrow..

---

### Post by SupSoc on 2007-10-29
Hi guys,

I encounter the same or at least a very similar problem. I've been using feisty for a couple of months and everything was working fine, until I upgraded to gutsy. After reboot, no more internet-connection. I get an IP-adress and everything seems OK to me (subnet-mask, DNS-server,..). I even can logon to my DSL modem/router and check or tweek my router and internet settings, and I can ping to sites. But still no internet connection when using firefox, thunderbird, update-manager, ...
I really can't figger this one out.

---

### Post by Cochise on 2007-10-29
i had the same probelm, for some reason when i did a fresh install and all the updates availible it fixed it. i also installed the new ati driver at the same time, unrelated but worth mentioning since it was the same time it started working

---

### Post by SupSoc on 2007-10-29
Well, I tried disabling ipv6 just now, and guess what?? My connection is working!!! 

For disabling ipv6:

 gksudo gedit /etc/modprobe.d/aliases  (in gnome, for kde this will be slightly different)

and change the line that says:

 alias net -pf -10 ipv6

to:

 alias net -pf -10 off

save and reboot

---

### Post by wolfsta on 2007-10-29
Hi Guys

I had the same problem.. And i still cant explain it but it turned out to be something to do with the dns on my router (think its screwed)

I skipped the routers dns 192.168.0.1 or whatever yours is and pointed gutsy straight at my isp's dns servers.  And it fixed everything.  Dunno if some sort of change in gutsy looking at the routers dns is possible or not but it fixed it.

This may not fix yours i dont know but the only reason why i suggested it is because it only affected my linux machines (which are both gutsy) my windows machines had no dns issues at all.

Cheers

Wolfsta

---

### Post by ross350 on 2007-10-29
same thing here on a dell 1501
and can someone come on here with something noob friendly 
is gutsy not ready for the 1501?
why up grade ?
starting to think why go back?
if i didnt have 2 computers how would i get help 
reinstall feisty and then go back and forth between versions 
this is silly !!!!
someone help!!!!

---

### Post by the_nz_monkey on 2007-10-29
And a brain wave here, too

Plugged the gutsy notebook straight into my router, updated everything possible.

Rebooted, switched back all network cables to my normal arrangement.  Gutsy notebook *still* not able to connect.

Thought I'd see what would happen if I changed the Gateway address on the notebook to the Desktop machines internal IP, and...

It's all working again(!!)
It seems like the notebook wasn't able to attach to the network I'd provided, because the DHCP lookup was pointing at a really weird address (I checked, it was looking at 255.255.255.255)

Now, lets have a look at those 8.42 ATi drivers...

---

### Post by ~cyrus~ on 2007-10-29
If you are connecting with an ADSL router, see if [this post]("http://ubuntuforums.org/showpost.php?p=3654324&postcount=109") helps.

---

### Post by Dr. Dom on 2007-11-07
Hey guys I had the same problem when I first started out.
I could ping other computers on my LAN as well as direct URLs such as QGL.org through firefox.
But the problem with connecting is that IPv6 is enabled by default in gutsy.

Try this it worked for me: 
In Firefox type in the address bar about:config
In the filters bar type IPv6
Then double click on the only listing there and enable value to true.

Hope this helps.

---

### Post by kotak07 on 2007-11-07
hey guys ive been looking for someone to help me with this same problem but im guessing people are reluctant to. i Disabled ipv6 but still no luck. it says its connected but i can't get on the internet. I can sometimes get on Pidgin AIM but that disconnects most of the time after a while. I need help..thanks.

---

### Post by corn13read on 2007-11-08
I have seen the ipv6 issue this is easily solved by finding out your isp's dns servers and entering them into your dns setting by giong into the network config under the dns tab just enter them in and hit enter no need to restart networking. 

Now that should solve half of the issues...

For the other part I ran into an issue lately with a client that we were able to get an ip and dns and couldn't even ping an outside ip address so that eliminates dns issue. We are working on the kinks with that but it is confirmed that on different hardware router she connects fine. We did everything including "disable" ipv6 in both ubuntu and in firefox to no avail. We were able to ping the router that bridges wireless internet from the wan router but not the wan router's wan ip or any other ip address which i took to be an issue with the hardware wan router. There are mac osx and windows clients connected without issue. 

If anyone has any input please feel free to point us in the right direction. We are currently looking into a firmware update.

---

