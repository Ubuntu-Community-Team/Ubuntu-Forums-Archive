---
title: "It's only using one RAM stick"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-04
I've been trying out the Live CD for a few weeks now.  I've been running it all with 1GB RAM, until I bought another 0.5GB last week.  After noticing Ubuntu had become slower than ever, I ran **free** in the terminal and saw that Linux is only recognizing 0.5GB of my total 1.5GB RAM.  Note that WinXP and MemTest86 are recognizing the full 1.5GB.

(1) Why is it being annoying, and (2) how do I fix it?

---

### Post by DigiTan on 2009-03-05
I really need to make these titles more attention-grabbing.

---

### Post by kanikilu on 2009-03-05
What's your current setup? 1x1GB + 1x512MB, 3x512MB, or...?

Have you tested (not just see if they are visible, but actually tested) each stick independently of each other in memtest?

Could it be a bad slot in the motherboard? If you swap the modules around, does it still show the same thing?

---

### Post by cariboo on 2009-03-05
Is  all of your ram detected during POST?

Jim

---

### Post by DigiTan on 2009-03-05
> **cariboo907 said:**
> Is  all of your ram detected during POST?

Jim

That I'm not certain about.  At POST, it stops counting at 256MB.  But Memtest86 and WinXP report it as having 1.5GB, and Ubuntu is the only system having this problem so far.

I upgraded from having 2x512MB to 3x512MB.  The original two sticks were unchanged; and the new one was the same brand, same specs, just a newer model.

---

### Post by kanikilu on 2009-03-05
That nForce board in your sig (assumed this is the one you're talking about) supports dual channel memory which have to be installed in sets of 2, so your 3 DIMM setup won't work. I think you can disable that in some BIOS's, but not sure about yours. Check through your BIOS settings.

[http://forums.nvidia.com/lofiversion/index.php?t17062.html](http://forums.nvidia.com/lofiversion/index.php?t17062.html)

[http://www.hardwaresecrets.com/article/133](http://www.hardwaresecrets.com/article/133)

---

### Post by blackened on 2009-03-05
> **kanikilu said:**
> That nForce board in your sig (assumed this is the one you're talking about) supports dual channel memory which have to be installed in sets of 2, so your 3 DIMM setup won't work. I think you can disable that in some BIOS's, but not sure about yours. Check through your BIOS settings.

[http://forums.nvidia.com/lofiversion/index.php?t17062.html](http://forums.nvidia.com/lofiversion/index.php?t17062.html)

[http://www.hardwaresecrets.com/article/133](http://www.hardwaresecrets.com/article/133)

I might be inclined to agree with you if he hadn't already said that memtest and Windows both recognize the full 1.5Gb. The dual-channel issue you linked to is the exception to the rule. Most boards default back to single channel mode if you install non-paired modules.

Are you sure you're reading the output of the free command correctly?

Try this: go to System->Administration->System Monitor, look at the "System" tab. How much memory is being reported there?

---

### Post by DigiTan on 2009-03-05
That's what I was afraid of.  I remember the manual required filling them in a specific order, but not the pairing part.  The new problem is my 4th RAM slot doesn't seem to be working at all and I'm suspecting there's a bent pin.



In other news, anyone want some RAM cheap?

---

### Post by blackened on 2009-03-05
> **DigiTan said:**
> That's what I was afraid of.  I remember the manual required filling them in a specific order, but not the pairing part.  The new problem is my 4th RAM slot doesn't seem to be working at all and I'm suspecting there's a bent pin.



In other news, anyone want some RAM cheap?

What you're saying makes absolutely no sense. If Windows and Memtest are seeing the full 1.5Gb, then it is *_NOT_* a hardware problem.

---

### Post by anubhavrocks on 2009-03-05
Can you post the output of ```

dmesg
```

---

### Post by DigiTan on 2009-03-05
I tried installing the 4th RAM stick one last time.  This time, I didn't use the locking clamps and the system will now boot with the full set of 4.  But it's still seeing only 512MB.  WinXP and MemTest86+ also say 512MB now, which makes me suspect something was reconfigured since the time they said 1.5GB.

In my previous RAM attempt, I **did** once witness a menu indicate a hardware problem and options for (1) Safe mode, (2) Last known good configuration, and one other option.  Usually, these are WinXP options, but I could have sworn this appeared before the HDD booted.  Maybe the BIOS reverted to some safe mode that only uses one RAM channel?

Output of dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-generic (buildd@crested) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:13:46 UTC 2008 (Ubuntu 2.6.24-23.46-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz acpi=off irqpoll file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 131056) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.2 present.
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000001fff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 131056) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000001fff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   131056
[    0.000000] On node 0 totalpages: 130959
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1234 pages reserved
[    0.000000]   DMA zone: 2709 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1735 pages used for memmap
[    0.000000]   DMA32 zone: 125225 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #2 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 127934
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz acpi=off irqpoll file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Misrouted IRQ fixup and polling support enabled
[    0.000000] This may significantly impact system performance
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 16384 bytes)
[    0.000000] TSC calibrated against PIT
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.000000] time.c: Detected 2211.338 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 6398000000 size 32 MB
[    0.000000] Aperture too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] Memory: 503476k/524224k available (2491k kernel code, 20360k reserved, 1317k data, 320k init)
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] Calibrating delay using timer specific routine.. 4436.71 BogoMIPS (lpj=8873431)
[    0.000000] Security Framework initialized
[    0.000000] SELinux:  Disabled at boot.
[    0.000000] AppArmor: AppArmor initialized
[    0.000000] Failure registering capabilities with primary security module.
[    0.000000] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.000000] Mount-cache hash table entries: 256
[    0.000000] Initializing cgroup subsys ns
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.000000] CPU 0/0 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 0
[    0.000000] SMP alternatives: switching to UP code
[    0.000000] Early unpacking initramfs... done
[    0.000000] ExtINT not setup in hardware but reported by MP table
[    0.000000] Using local APIC timer interrupts.
[    0.000000] APIC timer calibration result 12564421
[    0.000000] Detected 12.564 MHz APIC timer.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 1/2 APIC 0x1
[    0.000000] Initializing CPU#1
[    0.000000] Calibrating delay using timer specific routine.. 4422.68 BogoMIPS (lpj=8845379)
[    0.000000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.000000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.000000] CPU 1/1 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 1
[    0.000000] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[    0.000000] Brought up 2 CPUs
[    0.000000] CPU0 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 01 02
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] CPU1 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 02 01
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] net_namespace: 120 bytes
[    0.000000] Time: 19:24:17  Date: 03/05/09
[    0.000000] NET: Registered protocol family 16
[    0.000000] PCI: Using configuration type 1
[    0.000000] ACPI: Interpreter disabled.
[    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.000000] pnp: PnP ACPI: disabled
[    0.000000] PCI: Probing PCI hardware
[    0.000000] PCI: Probing PCI hardware (bus 00)
[    0.000000] PCI: Transparent bridge - 0000:00:09.0
[    0.000000] PCI->APIC IRQ transform: 0000:00:01.1[A] -> IRQ 3
[    0.000000] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 5
[    0.000000] PCI->APIC IRQ transform: 0000:00:02.1[B] -> IRQ 10
[    0.000000] PCI->APIC IRQ transform: 0000:00:04.0[A] -> IRQ 3
[    0.000000] PCI->APIC IRQ transform: 0000:00:07.0[A] -> IRQ 11
[    0.000000] PCI->APIC IRQ transform: 0000:00:08.0[A] -> IRQ 10
[    0.000000] PCI->APIC IRQ transform: 0000:00:0a.0[A] -> IRQ 11
[    0.000000] PCI->APIC IRQ transform: 0000:05:00.0[A] -> IRQ 5
[    0.000000] NET: Registered protocol family 8
[    0.000000] NET: Registered protocol family 20
[    0.000000] AppArmor: AppArmor Filesystem Enabled
[    0.000000] PCI: Bridge: 0000:00:09.0
[    0.000000]   IO window: a000-afff
[    0.000000]   MEM window: fde00000-fdefffff
[    0.000000]   PREFETCH window: fdf00000-fdffffff
[    0.000000] PCI: Bridge: 0000:00:0b.0
[    0.000000]   IO window: 9000-9fff
[    0.000000]   MEM window: fdd00000-fddfffff
[    0.000000]   PREFETCH window: fdc00000-fdcfffff
[    0.000000] PCI: Bridge: 0000:00:0c.0
[    0.000000]   IO window: 8000-8fff
[    0.000000]   MEM window: fdb00000-fdbfffff
[    0.000000]   PREFETCH window: fda00000-fdafffff
[    0.000000] PCI: Bridge: 0000:00:0d.0
[    0.000000]   IO window: 7000-7fff
[    0.000000]   MEM window: fd900000-fd9fffff
[    0.000000]   PREFETCH window: fd800000-fd8fffff
[    0.000000] PCI: Bridge: 0000:00:0e.0
[    0.000000]   IO window: 6000-6fff
[    0.000000]   MEM window: fa000000-fcffffff
[    0.000000]   PREFETCH window: d0000000-dfffffff
[    0.000000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] NET: Registered protocol family 2
[    0.000000] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.000000] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.000000] TCP: Hash tables configured (established 16384 bind 16384)
[    0.000000] TCP reno registered
[    0.000000] checking if image is initramfs... it is
[    0.000000] Freeing initrd memory: 8169k freed
[    0.000000] audit: initializing netlink socket (disabled)
[    0.000000] audit(1236281057.184:1): initialized
[    0.000000] VFS: Disk quotas dquot_6.5.1
[    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.000000] io scheduler noop registered
[    0.000000] io scheduler anticipatory registered
[    0.000000] io scheduler deadline registered
[    0.000000] io scheduler cfq registered (default)
[    0.000000] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.000000] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:0b.0
[    0.000000] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:0c.0
[    0.000000] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:0d.0
[    0.000000] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.000000] PCI: Found enabled HT MSI Mapping on 0000:00:0e.0
[    0.000000] Boot video device is 0000:05:00.0
[    0.000000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0b.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0c.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0d.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:0e.0:pcie00]
[    0.000000] Real Time Clock Driver v1.12ac
[    0.000000] Linux agpgart interface v0.102
[    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.000000] PNP: No PS/2 controller found. Probing ports directly.
[    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.000000] mice: PS/2 mouse device common for all mice
[    0.000000] cpuidle: using governor ladder
[    0.000000] cpuidle: using governor menu
[    0.000000] NET: Registered protocol family 1
[    0.000000] registered taskstats version 1
[    0.000000]   Magic number: 1:745:444
[    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.000000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.000000] EDD information not available.
[    0.000000] Freeing unused kernel memory: 320k freed
[    0.000000] Write protecting the kernel read-only data: 1036k
[    0.000000] fuse init (API version 7.9)
[    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.000000] usbcore: registered new interface driver usbfs
[    0.000000] usbcore: registered new interface driver hub
[    0.000000] SCSI subsystem initialized
[    0.000000] usbcore: registered new device driver usb
[    0.000000] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    0.000000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    0.000000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.000000] libata version 3.00 loaded.
[    0.000000] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:19:21:21:05:a5
[    0.000000] forcedeth 0000:00:0a.0: highdma csum timirq lnktim desc-v3
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.000000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    0.000000] ohci_hcd 0000:00:02.0: irq 5, io mem 0xfe02f000
[    0.000000] usb usb1: configuration #1 chosen from 1 choice
[    0.000000] hub 1-0:1.0: USB hub found
[    0.000000] hub 1-0:1.0: 10 ports detected
[    0.000000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    0.000000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.000000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    0.000000] ehci_hcd 0000:00:02.1: debug port 1
[    0.000000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    0.000000] ehci_hcd 0000:00:02.1: irq 10, io mem 0xfe02e000
[    0.000000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    0.000000] usb usb2: configuration #1 chosen from 1 choice
[    0.000000] hub 2-0:1.0: USB hub found
[    0.000000] hub 2-0:1.0: 10 ports detected
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.000000] sata_nv 0000:00:07.0: version 3.5
[    0.000000] sata_nv 0000:00:07.0: Using ADMA mode
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] scsi0 : sata_nv
[    0.000000] scsi1 : sata_nv
[    0.000000] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 11
[    0.000000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 11
[    0.000000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.000000] ata1.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
[    0.000000] ata1.00: 145226112 sectors, multi 16: LBA48 
[    0.000000] ata1.00: configured for UDMA/133
[    0.000000] ata2: SATA link down (SStatus 0 SControl 300)
[    0.000000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
[    0.000000] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[    0.000000] sata_nv 0000:00:08.0: Using ADMA mode
[    0.000000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    0.000000] scsi2 : sata_nv
[    0.000000] scsi3 : sata_nv
[    0.000000] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 10
[    0.000000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 10
[    0.000000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    0.000000] usb 1-1: configuration #1 chosen from 1 choice
[    0.000000] ata3: SATA link down (SStatus 0 SControl 300)
[    0.000000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    0.000000] ata4: SATA link down (SStatus 0 SControl 300)
[    0.000000] pata_amd 0000:00:06.0: version 0.3.10
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] scsi4 : pata_amd
[    0.000000] scsi5 : pata_amd
[    0.000000] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe800 irq 14
[    0.000000] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe808 irq 15
[    0.000000] Driver 'sd' needs updating - please use bus_type methods
[    0.000000] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors (74356 MB)
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sda: sda1
[    0.000000] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.000000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.000000] usb 1-2: configuration #1 chosen from 1 choice
[    0.000000] usbcore: registered new interface driver hiddev
[    0.000000] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input1
[    0.000000] input,hidraw0: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:02.0-1
[    0.000000] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input2
[    0.000000] input,hidraw1: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:02.0-2
[    0.000000] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input3
[    0.000000] input,hidraw2: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:02.0-2
[    0.000000] usbcore: registered new interface driver usbhid
[    0.000000] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    0.000000] ata6.00: ATAPI: ATAPI   iHAP422   8, VL13, max UDMA/66
[    0.000000] ata6.00: configured for UDMA/66
[    0.000000] scsi 5:0:0:0: CD-ROM            ATAPI    iHAP422   8      VL13 PQ: 0 ANSI: 5
[    0.000000] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[    0.000000] Driver 'sr' needs updating - please use bus_type methods
[    0.000000] sr0: scsi3-mmc drive: 16x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.000000] Uniform CD-ROM driver Revision: 3.20
[    0.000000] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    0.000000] ISO 9660 Extensions: Microsoft Joliet Level 3
[    0.000000] ISO 9660 Extensions: RRIP_1991A
[    0.000000] Registering unionfs 1.4
[    0.000000] unionfs: debugging is not enabled
[    0.000000] loop: module loaded
[    0.000000] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.000000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    0.000000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.000000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.000000] intel8x0_measure_ac97_clock: measured 56004 usecs
[    0.000000] intel8x0: clocking to 48000
[    0.000000] ip_tables: (C) 2000-2006 Netfilter Core Team
[    0.000000] powernow_k8: Unknown symbol acpi_processor_notify_smm
[    0.000000] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[    0.000000] powernow_k8: Unknown symbol acpi_processor_register_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[    0.000000] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[    0.000000] parport0: irq 7 detected
[    0.000000] lp0: using parport0 (polling).
[    0.000000] ppdev: user-space parallel port driver
[    0.000000] Bluetooth: Core ver 2.11
[    0.000000] NET: Registered protocol family 31
[    0.000000] Bluetooth: HCI device and connection manager initialized
[    0.000000] Bluetooth: HCI socket layer initialized
[    0.000000] Bluetooth: L2CAP ver 2.9
[    0.000000] Bluetooth: L2CAP socket layer initialized
[    0.000000] Bluetooth: RFCOMM socket layer initialized
[    0.000000] Bluetooth: RFCOMM TTY layer initialized
[    0.000000] Bluetooth: RFCOMM ver 1.8
[    0.000000] NET: Registered protocol family 17
[    0.000000] NET: Registered protocol family 10
[    0.000000] lo: Disabled Privacy Extensions
[    0.000000] eth0: no IPv6 routers present
```

---

### Post by DigiTan on 2009-03-05
It's looking like the whole board is ******.  Only 1 RAM socket is working--any time I try any other I get that God-damn long beep code and no indication of the actual problem.  I've tried dozens of mount combinations, compressed air, vacuum, and solvent.  Now I'm stuck with half the RAM I started out with.  960 memory pins to diagnose and all the only tool they give you is a stupid beep.

---

### Post by anubhavrocks on 2009-03-06
I dont see any thing wrong with the OS here.The BIOS reports that you have 512MiB of RAM.
When you have a 64bit box why don't you use the 64bit edition of ubuntu?You can obtain the latest 64 bit edition of ubuntu from 
> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by DigiTan on 2009-03-06
Yeah, I already burned one.  But with only half a Gig, the Live distros lock up from downloading a single mp3 plugin.  Which is a shame, but I thought it was running quite fast for optical media.

Since this seems to be attributable to foolish bios engineering and not Ubuntu, I'm laying this topic to rest.

---

