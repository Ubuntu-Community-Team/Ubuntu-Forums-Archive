---
title: "Newbie with no wired connection"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by crasyone on 2008-09-21
I am new to ubuntu and do not know a lot about linux but i cannot seem to get my wired network connected. I am connected to a router with ip 192.168.1.1 and subnet 255.255.255.0. I had Hardy installed previously with some problems connecting to the network, but i simply resolved them by replacing the wire to the router. I had to reinstall ubuntu 8.04 and now can't get the network connected with any of my previous solutions. I have sifted through the forums but can't figure this out, especially being such an amateur. I am using integrated networking with my ASUS A8N-SLI SE motherboard. Please help me, it is greatly appreciated. I am sure i left out some important information, so please tell me if i can supply any additional information.

---

### Post by blingo on 2008-09-21
For start can you ping your router?

Open a terminal and write:

'ping 192.168.1.1'

do you see "timed out" or number of milliseconds?

---

### Post by crasyone on 2008-09-21
First off, i got an error when pinging my router:
connect: Network is unreachable

Second, the problem is becoming more complex. I reinstalled ubuntu a couple of days ago and when i turned the pc on for the first time one morning...the internet miraculously worked, but the internet was incredibly slow. So I then turned to that problem finding that any people on the forums had this issue as well, but in the process i ended up having to restart and it was back to no internet connection. I clanged back all settings i had changed to fix the slow internet, but no luck. I then turned it off and left it alone, came back after about 2 hours, turn it on and the internet is back to working. I try to download some stuff, freezes, restart, no internet. Now that i think about it, before i had reinstalled ubuntu, the internet hadn't started working until a couple days after the install. This problem is getting more and more irritating by the second...please help.

---

### Post by anubhavrocks on 2008-09-21
Provide outputs of following commands

sudo lshw -C network
dmesg
ifconfig -a
route -n

---

### Post by crasyone on 2008-09-21
```
matt@Bernardo:~$ sudo lshw -C network
PCI (sysfs)

dmesg got cut off, so it started here:
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 000000000009d000
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515782
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=ff531110-55f4-4b55-85d1-e397115b79a5 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   19.223716] Marking TSC unstable due to TSCs unsynchronized
[   19.223718] time.c: Detected 2613.384 MHz processor.
[   19.224815] Console: colour VGA+ 80x25
[   19.224818] console [tty0] enabled
[   19.224833] Checking aperture...
[   19.224835] CPU 0: aperture @ dcfc000000 size 32 MB
[   19.224836] Aperture too small (32 MB)
[   19.229591] No AGP bridge found
[   19.259521] Memory: 2054716k/2097088k available (2489k kernel code, 41972k reserved, 1318k data, 320k init)
[   19.259572] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   19.337469] Calibrating delay using timer specific routine.. 5229.98 BogoMIPS (lpj=10459977)
[   19.337512] Security Framework initialized
[   19.337520] SELinux:  Disabled at boot.
[   19.337537] AppArmor: AppArmor initialized
[   19.337541] Failure registering capabilities with primary security module.
[   19.337678] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   19.340030] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.341181] Mount-cache hash table entries: 256
[   19.341354] Initializing cgroup subsys ns
[   19.341358] Initializing cgroup subsys cpuacct
[   19.341373] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.341374] CPU: L2 Cache: 1024K (64 bytes/line)
[   19.341376] CPU 0/0 -> Node 0
[   19.341378] CPU: Physical Processor ID: 0
[   19.341379] CPU: Processor Core ID: 0
[   19.341403] SMP alternatives: switching to UP code
[   19.342042] Early unpacking initramfs... done
[   19.601050] ACPI: Core revision 20070126
[   19.601110] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.645305] Using local APIC timer interrupts.
[   19.683492] APIC timer calibration result 12564335
[   19.683494] Detected 12.564 MHz APIC timer.
[   19.683603] SMP alternatives: switching to SMP code
[   19.684112] Booting processor 1/2 APIC 0x1
[   19.694423] Initializing CPU#1
[   19.771567] Calibrating delay using timer specific routine.. 5226.80 BogoMIPS (lpj=10453607)
[   19.771573] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   19.771575] CPU: L2 Cache: 1024K (64 bytes/line)
[   19.771577] CPU 1/1 -> Node 0
[   19.771578] CPU: Physical Processor ID: 0
[   19.771579] CPU: Processor Core ID: 1
[   19.771684] AMD Athlon(tm) 64 FX-60 Dual Core Processor  stepping 02
[   19.771510] Brought up 2 CPUs
[   19.771585] CPU0 attaching sched-domain:
[   19.771587]  domain 0: span 03
[   19.771588]   groups: 01 02
[   19.771590]   domain 1: span 03
[   19.771591]    groups: 03
[   19.771593] CPU1 attaching sched-domain:
[   19.771594]  domain 0: span 03
[   19.771595]   groups: 02 01
[   19.771596]   domain 1: span 03
[   19.771597]    groups: 03
[   19.771787] net_namespace: 120 bytes
[   19.772112] Time: 18:32:54  Date: 09/21/08
[   19.772143] NET: Registered protocol family 16
[   19.772302] ACPI: bus type pci registered
[   19.772360] PCI: Using configuration type 1
[   19.773497] ACPI: EC: Look up EC in DSDT
[   19.779497] ACPI: Interpreter enabled
[   19.779500] ACPI: (supports S0 S1 S3 S4 S5)
[   19.779511] ACPI: Using IOAPIC for interrupt routing
[   19.787058] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.787487] PCI: Transparent bridge - 0000:00:09.0
[   19.787739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.788021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   19.841576] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   19.841714] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.841851] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.841989] ACPI: PCI Interrupt Link [LNK4] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   19.842126] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.842263] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.842399] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.842537] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.842675] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.842812] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.842949] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.843087] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.843229] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.843376] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.843523] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   19.843667] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.843822] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   19.843968] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   19.844114] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   19.844261] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   19.844359] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   19.844509] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   19.844659] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   19.844809] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   19.844959] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   19.845109] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   19.845260] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   19.845410] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   19.845561] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   19.845719] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   19.845876] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   19.846034] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   19.846133] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.846155] pnp: PnP ACPI init
[   19.846161] ACPI: bus type pnp registered
[   19.850501] pnpacpi: exceeded the max number of mem resources: 12
[   19.850549] pnp: PnP ACPI: found 16 devices
[   19.850551] ACPI: ACPI bus type pnp unregistered
[   19.850732] PCI: Using ACPI for IRQ routing
[   19.850735] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.859167] NET: Registered protocol family 8
[   19.859168] NET: Registered protocol family 20
[   19.859266] AppArmor: AppArmor Filesystem Enabled
[   19.871135] system 00:01: ioport range 0x4000-0x407f has been reserved
[   19.871138] system 00:01: ioport range 0x4080-0x40ff has been reserved
[   19.871140] system 00:01: ioport range 0x4400-0x447f has been reserved
[   19.871142] system 00:01: ioport range 0x4480-0x44ff has been reserved
[   19.871144] system 00:01: ioport range 0x4800-0x487f has been reserved
[   19.871147] system 00:01: ioport range 0x4880-0x48ff has been reserved
[   19.871149] system 00:01: iomem range 0x0-0x0 could not be reserved
[   19.871153] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   19.871156] system 00:02: ioport range 0x800-0x87f has been reserved
[   19.871158] system 00:02: ioport range 0x290-0x297 has been reserved
[   19.871165] system 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
[   19.871169] system 00:0f: iomem range 0xdac00-0xdbfff has been reserved
[   19.871172] system 00:0f: iomem range 0xf0000-0xf7fff could not be reserved
[   19.871174] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   19.871176] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   19.871179] system 00:0f: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   19.871181] system 00:0f: iomem range 0xffff0000-0xffffffff has been reserved
[   19.871184] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   19.871186] system 00:0f: iomem range 0x100000-0x7ffeffff could not be reserved
[   19.871188] system 00:0f: iomem range 0xfec00000-0xfec00fff has been reserved
[   19.871191] system 00:0f: iomem range 0xfee00000-0xfeefffff could not be reserved
[   19.871193] system 00:0f: iomem range 0xfefff000-0xfeffffff has been reserved
[   19.871195] system 00:0f: iomem range 0xfff80000-0xfff80fff has been reserved
[   19.871478] PCI: Bridge: 0000:00:09.0
[   19.871480]   IO window: disabled.
[   19.871482]   MEM window: disabled.
[   19.871484]   PREFETCH window: disabled.
[   19.871486] PCI: Bridge: 0000:00:0b.0
[   19.871487]   IO window: disabled.
[   19.871488]   MEM window: disabled.
[   19.871490]   PREFETCH window: disabled.
[   19.871492] PCI: Bridge: 0000:00:0c.0
[   19.871493]   IO window: disabled.
[   19.871494]   MEM window: disabled.
[   19.871496]   PREFETCH window: disabled.
[   19.871498] PCI: Bridge: 0000:00:0d.0
[   19.871499]   IO window: a000-afff
[   19.871501]   MEM window: d0000000-d1ffffff
[   19.871503]   PREFETCH window: c0000000-cfffffff
[   19.871505] PCI: Bridge: 0000:00:0e.0
[   19.871506]   IO window: disabled.
[   19.871508]   MEM window: disabled.
[   19.871509]   PREFETCH window: disabled.
[   19.871515] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   19.871522] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.871526] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.871531] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   19.871536] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   19.871576] NET: Registered protocol family 2
[   19.875103] Time: acpi_pm clocksource has been installed.
[   19.875117] Switched to high resolution mode on CPU 0
[   19.875492] Switched to high resolution mode on CPU 1
[   19.907103] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   19.907934] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   19.912556] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.913674] TCP: Hash tables configured (established 262144 bind 65536)
[   19.913677] TCP reno registered
[   19.923145] checking if image is initramfs... it is
[   20.427310] Freeing initrd memory: 8216k freed
[   20.437226] audit: initializing netlink socket (disabled)
[   20.437243] audit(1222021974.188:1): initialized
[   20.439157] VFS: Disk quotas dquot_6.5.1
[   20.439218] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   20.439317] io scheduler noop registered
[   20.439319] io scheduler anticipatory registered
[   20.439320] io scheduler deadline registered
[   20.439411] io scheduler cfq registered (default)
[   20.439424] pci 0000:00:00.0: Enabling HT MSI Mapping
[   20.455673] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   20.455683] PCI: Found enabled HT MSI Mapping on 0000:00:0b.0
[   20.455690] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   20.455695] PCI: Found enabled HT MSI Mapping on 0000:00:0c.0
[   20.455701] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   20.455706] PCI: Found enabled HT MSI Mapping on 0000:00:0d.0
[   20.455713] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   20.455717] PCI: Found enabled HT MSI Mapping on 0000:00:0e.0
[   20.455723] Boot video device is 0000:02:00.0
[   20.455921] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   20.455937] assign_interrupt_mode Found MSI capability
[   20.455953] Allocate Port Service[0000:00:0b.0:pcie00]
[   20.456012] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   20.456026] assign_interrupt_mode Found MSI capability
[   20.456036] Allocate Port Service[0000:00:0c.0:pcie00]
[   20.456083] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   20.456097] assign_interrupt_mode Found MSI capability
[   20.456107] Allocate Port Service[0000:00:0d.0:pcie00]
[   20.456158] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   20.456171] assign_interrupt_mode Found MSI capability
[   20.456181] Allocate Port Service[0000:00:0e.0:pcie00]
[   20.479658] Real Time Clock Driver v1.12ac
[   20.479767] Linux agpgart interface v0.102
[   20.479770] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.479885] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.480335] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.481034] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.481095] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.481177] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.484155] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.484161] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.499056] mice: PS/2 mouse device common for all mice
[   20.499093] cpuidle: using governor ladder
[   20.499095] cpuidle: using governor menu
[   20.499244] NET: Registered protocol family 1
[   20.499341] registered taskstats version 1
[   20.499467]   Magic number: 8:982:544
[   20.499549] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   20.499551] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.499553] EDD information not available.
[   20.499568] Freeing unused kernel memory: 320k freed
[   20.537721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.651956] fuse init (API version 7.9)
[   21.662263] ACPI: Fan [FAN] (on)
[   21.667467] ACPI: Thermal Zone [THRM] (40 C)
[   21.984248] usbcore: registered new interface driver usbfs
[   21.984275] usbcore: registered new interface driver hub
[   21.984346] usbcore: registered new device driver usb
[   21.985545] SCSI subsystem initialized
[   21.985949] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   21.985958] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   21.986474] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   21.986483] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   21.986799] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   21.986828] ehci_hcd 0000:00:02.1: debug port 1
[   21.986831] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   21.986840] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfeb00000
[   21.987704] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.992373] libata version 3.00 loaded.
[   21.998503] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.998627] usb usb1: configuration #1 chosen from 1 choice
[   21.998647] hub 1-0:1.0: USB hub found
[   21.998654] hub 1-0:1.0: 10 ports detected
[   22.071445] Floppy drive(s): fd0 is 1.44M
[   22.090384] FDC 0 is a post-1991 82077
[   22.102803] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   22.102814] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   22.103387] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.103394] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   22.103453] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   22.103474] ohci_hcd 0000:00:02.0: irq 22, io mem 0xd2004000
[   22.160254] usb usb2: configuration #1 chosen from 1 choice
[   22.160278] hub 2-0:1.0: USB hub found
[   22.160286] hub 2-0:1.0: 10 ports detected
[   22.262138] sata_nv 0000:00:07.0: version 3.5
[   22.262502] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[   22.262511] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 21 (level, low) -> IRQ 21
[   22.262515] sata_nv 0000:00:07.0: Using ADMA mode
[   22.263302] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   22.263881] scsi0 : sata_nv
[   22.263931] scsi1 : sata_nv
[   22.264090] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 21
[   22.264092] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 21
[   22.573246] ata1: SATA link down (SStatus 0 SControl 300)
[   22.645197] usb 2-5: new full speed USB device using ohci_hcd and address 2
[   22.865997] usb 2-5: configuration #1 chosen from 1 choice
[   22.876986] usbcore: registered new interface driver libusual
[   22.881950] Initializing USB Mass Storage driver...
[   22.885048] scsi2 : SCSI emulation for USB Mass Storage devices
[   22.884861] usb-storage: device found at 2
[   22.884863] usb-storage: waiting for device to settle before scanning
[   22.885119] usbcore: registered new interface driver usb-storage
[   22.885122] USB Mass Storage support registered.
[   22.888557] ata2: SATA link down (SStatus 0 SControl 300)
[   22.888936] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[   22.888944] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 20 (level, low) -> IRQ 20
[   22.888949] sata_nv 0000:00:08.0: Using ADMA mode
[   22.889565] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   22.889706] scsi3 : sata_nv
[   22.889780] scsi4 : sata_nv
[   22.889945] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 20
[   22.889947] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 20
[   23.359531] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.364878] ata3.00: ATA-7: Maxtor 6L300S0, BACE1G20, max UDMA/133
[   23.364882] ata3.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   23.380730] ata3.00: configured for UDMA/133
[   23.690814] ata4: SATA link down (SStatus 0 SControl 300)
[   23.690910] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6L300S0   BACE PQ: 0 ANSI: 5
[   23.690916] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   23.691097] pata_amd 0000:00:06.0: version 0.3.10
[   23.691151] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   23.691781] scsi5 : pata_amd
[   23.691828] scsi6 : pata_amd
[   23.692260] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   23.692262] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   23.695938] Driver 'sd' needs updating - please use bus_type methods
[   23.696025] sd 3:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   23.696034] sd 3:0:0:0: [sda] Write Protect is off
[   23.696036] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.696048] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.696090] sd 3:0:0:0: [sda] 586114704 512-byte hardware sectors (300091 MB)
[   23.696095] sd 3:0:0:0: [sda] Write Protect is off
[   23.696097] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.696106] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.696109]  sda: sda1 sda2 < sda5 >
[   23.739430] sd 3:0:0:0: [sda] Attached SCSI disk
[   23.742400] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   23.868776] Attempting manual resume
[   23.868780] swsusp: Resume From Partition 8:5
[   23.868781] PM: Checking swsusp image.
[   23.868877] PM: Resume from disk failed.
[   23.877660] EXT3-fs: INFO: recovery required on readonly filesystem.
[   23.877664] EXT3-fs: write access will be enabled during recovery.
[   23.939392] kjournald starting.  Commit interval 5 seconds
[   23.939659] EXT3-fs: sda1: orphan cleanup on readonly fs
[   23.939668] ext3_orphan_cleanup: deleting unreferenced inode 11100172
[   23.939695] EXT3-fs: sda1: 1 orphan inode deleted
[   23.939696] EXT3-fs: recovery complete.
[   23.940561] EXT3-fs: mounted filesystem with ordered data mode.
[   24.193950] ata6.00: ATAPI: DVDRW DRW-6S160H, CSG6, max UDMA/66
[   24.193961] ata6.00: limited to UDMA/33 due to 40-wire cable
[   24.381474] ata6.00: configured for UDMA/33
[   24.382563] scsi 6:0:0:0: CD-ROM            DVDRW    DRW-6S160H       CSG6 PQ: 0 ANSI: 5
[   24.382640] scsi 6:0:0:0: Attached scsi generic sg1 type 5
[   27.871359] usb-storage: device scan complete
[   27.878083] scsi 2:0:0:0: Direct-Access     IC       USB Storage-CFC  301b PQ: 0 ANSI: 0 CCS
[   27.885047] scsi 2:0:0:1: Direct-Access     IC       USB Storage-SMC  301b PQ: 0 ANSI: 0 CCS
[   27.892040] scsi 2:0:0:2: Direct-Access     IC       USB Storage-MMC  301b PQ: 0 ANSI: 0 CCS
[   27.899026] scsi 2:0:0:3: Direct-Access     IC       USB Storage-MSC  301b PQ: 0 ANSI: 0 CCS
[   27.910018] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   27.910046] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   27.920992] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   27.921010] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   27.931967] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   27.931984] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   27.942946] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   27.942965] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   31.368896] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   31.423932] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.455596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.519378] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   31.519393] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   31.602393] parport_pc 00:09: reported by Plug and Play ACPI
[   31.602445] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   31.625770] input: Power Button (FF) as /devices/virtual/input/input3
[   31.645532] ACPI: Power Button (FF) [PWRF]
[   31.645622] input: Power Button (CM) as /devices/virtual/input/input4
[   31.677465] ACPI: Power Button (CM) [PWRB]
[   31.836958] logips2pp: Detected unknown logitech mouse model 101
[   32.319519] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   32.328000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   32.328005] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 23 (level, low) -> IRQ 23
[   32.328374] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   32.441204] Driver 'sr' needs updating - please use bus_type methods
[   32.444197] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   32.444200] Uniform CD-ROM driver Revision: 3.20
[   32.444237] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   32.648578] intel8x0_measure_ac97_clock: measured 54623 usecs
[   32.648582] intel8x0: clocking to 46960
[   32.649352] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   32.649362] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   32.649909] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   34.747491] lp0: using parport0 (interrupt-driven).
[   34.805690] Adding 6040400k swap on /dev/sda5.  Priority:-1 extents:1 across:6040400k
[   35.340091] EXT3 FS on sda1, internal journal
[   36.285852] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.608776] No dock devices found.
[   36.848300] powernow-k8: Found 1 AMD Athlon(tm) 64 FX-60 Dual Core Processor  processors (2 cpu cores) (version 2.20.00)
[   36.848095] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x8
[   36.848099] powernow-k8:    1 : fid 0x4 (1200 MHz), vid 0x12
[   37.526704] ppdev: user-space parallel port driver
[   37.734445] audit(1222021992.091:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5094 profile="/usr/sbin/cupsd" namespace="default"
[   37.777575] NET: Registered protocol family 10
[   37.777818] lo: Disabled Privacy Extensions
[   39.060162] Clocksource tsc unstable (delta = -269231208 ns)
[   41.428063] Bluetooth: Core ver 2.11
[   41.428127] NET: Registered protocol family 31
[   41.428128] Bluetooth: HCI device and connection manager initialized
[   41.428131] Bluetooth: HCI socket layer initialized
[   41.436767] Bluetooth: L2CAP ver 2.9
[   41.436772] Bluetooth: L2CAP socket layer initialized
[   41.443722] Bluetooth: RFCOMM socket layer initialized
[   41.443873] Bluetooth: RFCOMM TTY layer initialized
[   41.443875] Bluetooth: RFCOMM ver 1.8
[   52.862383] UDF-fs: No VRS found
[   52.939296] ISO 9660 Extensions: Microsoft Joliet Level 3
[   52.940228] ISOFS: changing to secondary root
[ 1755.699904] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 1755.761529] usb 1-6: configuration #1 chosen from 1 choice
[ 1755.764376] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1755.764594] usb-storage: device found at 3
[ 1755.764596] usb-storage: waiting for device to settle before scanning
[ 1758.067200] usb-storage: device scan complete
[ 1758.067721] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[ 1758.068572] scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2
[ 1758.076402] sd 7:0:0:0: [sdf] 3999373 512-byte hardware sectors (2048 MB)
[ 1758.077721] sd 7:0:0:0: [sdf] Write Protect is off
[ 1758.077724] sd 7:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 1758.077726] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 1758.082388] sd 7:0:0:0: [sdf] 3999373 512-byte hardware sectors (2048 MB)
[ 1758.083711] sd 7:0:0:0: [sdf] Write Protect is off
[ 1758.083714] sd 7:0:0:0: [sdf] Mode Sense: 03 00 00 00
[ 1758.083716] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 1758.083719]  sdf: sdf1
[ 1758.084747] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[ 1758.084777] sd 7:0:0:0: Attached scsi generic sg6 type 0
[ 1758.092468] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 1758.092516] sr 7:0:0:1: Attached scsi CD-ROM sr1
[ 1758.092544] sr 7:0:0:1: Attached scsi generic sg7 type 5

matt@Bernardo:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

On the rare occoasions that the connection  was working, ifconfig -a would output a eth0 connection with 192.168.1.1 and subnet 255.255.255.0

---

### Post by anubhavrocks on 2008-09-22
Somehow your network adapter is not being detected.Can you please provide the output of
```
 lspci -vvv
```

Also are you sure that the Hardware is okay.Normally network adapters have LEDs,that LED should be active.Also check that you have enabled the internal network adapter in the BIOS.

---

### Post by Iowan on 2008-09-22
These lines look interesting:```
[   19.850732] PCI: Using ACPI for IRQ routing
[   19.850735] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[ 
```

---

