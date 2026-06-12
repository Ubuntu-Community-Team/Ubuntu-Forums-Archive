---
title: "Realtek Ethernet card not connecting."
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by s_spiff on 2008-05-31
I seem to have a very strange problem. This is the situation :
I have two ethernet cards.
1. Nvidia onboard Ethernet card which is connected to a modem provided by my ISP to connect to the NET.
2. A Realtek Ethernet Card which I used to and want to use to connect to my LAN so that I can play CS, connect to the DC++ hubs, so on and so forth.

I have no issues with the Onboard ethernet card. What seems to be giving me trouble is the Realtek card. Earlier ( about 2 months back I never had issues. All I had to do is plug in the card onto the slot in the motherboard, connect the cable, boot up, assign IP add, and voila!) the card used to work fine on linux/XP. 

Right now, the card seems to work fine on Windows XP without issues. I was able to connect to the hub, ping the server, send and recieve messages to my friends on LAN.

On Ubuntu I get "destination host unreachable' when I try to ping my server.

Here are some additional data if anyone can figure it out. Please note, I'm a complete NOOB at this, and the following is what some people on IRC channel asked me to report. 

> 
 ping 172.16.29.29
PING 172.16.29.29 (172.16.29.29) 56(84) bytes of data.
From 172.16.106.233 icmp_seq=1 Destination Host Unreachable
From 172.16.106.233 icmp_seq=2 Destination Host Unreachable
From 172.16.106.233 icmp_seq=3 Destination Host Unreachable
From 172.16.106.233 icmp_seq=5 Destination Host Unreachable
From 172.16.106.233 icmp_seq=6 Destination Host Unreachable
From 172.16.106.233 icmp_seq=7 Destination Host Unreachable
From 172.16.106.233 icmp_seq=8 Destination Host Unreachable
From 172.16.106.233 icmp_seq=9 Destination Host Unreachable
From 172.16.106.233 icmp_seq=10 Destination Host Unreachable
From 172.16.106.233 icmp_seq=11 Destination Host Unreachable
From 172.16.106.233 icmp_seq=12 Destination Host Unreachable
From 172.16.106.233 icmp_seq=13 Destination Host Unreachable

--- 172.16.29.29 ping statistics ---
14 packets transmitted, 0 received, +12 errors, 100% packet loss, time 13032ms
, pipe 3



>  ifconfig output
eth0      Link encap:Ethernet  HWaddr 00:14:85:e5:6a:46  
          inet addr:219.91.240.109  Bcast:219.91.240.127  Mask:255.255.255.224
          inet6 addr: fe80::214:85ff:fee5:6a46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2381580 (2.2 MB)  TX bytes:378641 (369.7 KB)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:c1:26:06:b4:02  
          inet addr:172.16.106.233  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2c1:26ff:fe06:b402/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:231977 (226.5 KB)  TX bytes:4961 (4.8 KB)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96756 (94.4 KB)  TX bytes:96756 (94.4 KB)



>  dmesg output
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-17-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 13:57:17 UTC 2008 (Ubuntu 2.6.24-17.31-generic)
[    0.000000] Command line: root=UUID=775a4bc2-f38a-49a2-a07d-57fb2692e31e ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bff0000 (usable)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff3000 - 000000003c000000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245744) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6BC0 checksum 0
[    0.000000] ACPI: RSDP 000F6BC0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 3BFF3000, 0030 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: FACP 3BFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: DSDT 3BFF30C0, 4D2C (r1 GBT    AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 3BFF0000, 0040
[    0.000000] ACPI: MCFG 3BFF7E80, 003C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] ACPI: APIC 3BFF7E00, 0072 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003bff0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 245744) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bff0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   245744
[    0.000000] On node 0 totalpages: 245647
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1219 pages reserved
[    0.000000]   DMA zone: 2724 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3303 pages used for memmap
[    0.000000]   DMA32 zone: 238345 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 241069
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=775a4bc2-f38a-49a2-a07d-57fb2692e31e ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   19.992774] time.c: Detected 2210.055 MHz processor.
[   19.995748] Console: colour VGA+ 80x25
[   19.995751] console [tty0] enabled
[   19.995766] Checking aperture...
[   19.995769] CPU 0: aperture @ 2048000000 size 32 MB
[   19.995770] Aperture too small (32 MB)
[   20.002623] No AGP bridge found
[   20.014568] Memory: 956608k/982976k available (2488k kernel code, 25980k reserved, 1319k data, 320k init)
[   20.014609] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.090692] Calibrating delay using timer specific routine.. 4424.05 BogoMIPS (lpj=8848103)
[   20.090730] Security Framework initialized
[   20.090739] SELinux:  Disabled at boot.
[   20.090754] AppArmor: AppArmor initialized
[   20.090758] Failure registering capabilities with primary security module.
[   20.090848] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.091786] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   20.092236] Mount-cache hash table entries: 256
[   20.092398] Initializing cgroup subsys ns
[   20.092402] Initializing cgroup subsys cpuacct
[   20.092415] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.092416] CPU: L2 Cache: 512K (64 bytes/line)
[   20.092419] CPU 0/0 -> Node 0
[   20.092444] SMP alternatives: switching to UP code
[   20.093051] Early unpacking initramfs... done
[   20.374691] ACPI: Core revision 20070126
[   20.374746] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.418809] Using local APIC timer interrupts.
[   20.464027] APIC timer calibration result 12557130
[   20.464029] Detected 12.557 MHz APIC timer.
[   20.464091] Brought up 1 CPUs
[   20.464182] CPU0 attaching sched-domain:
[   20.464185]  domain 0: span 01
[   20.464186]   groups: 01
[   20.464338] net_namespace: 120 bytes
[   20.464701] Time: 20:28:59  Date: 05/31/08
[   20.464733] NET: Registered protocol family 16
[   20.464892] ACPI: bus type pci registered
[   20.464954] PCI: Using configuration type 1
[   20.466022] ACPI: EC: Look up EC in DSDT
[   20.471833] ACPI: Interpreter enabled
[   20.471835] ACPI: (supports S0 S1 S4 S5)
[   20.471846] ACPI: Using IOAPIC for interrupt routing
[   20.480623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.481471] PCI: Transparent bridge - 0000:00:10.0
[   20.481485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.481757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   20.561728] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   20.561895] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.562062] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   20.562226] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.562392] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.562557] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.562723] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[   20.562888] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.563056] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   20.563221] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.563388] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[   20.563554] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.563721] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[   20.563886] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.564058] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.564229] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   20.564396] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   20.564570] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.564736] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   20.564908] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   20.565113] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   20.565306] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   20.565499] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   20.565692] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   20.565884] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   20.566079] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   20.566275] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[   20.566467] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   20.566659] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   20.566851] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   20.567044] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   20.567236] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   20.567429] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   20.567621] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   20.567813] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   20.568009] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   20.568201] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   20.568393] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   20.568586] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   20.568779] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   20.568971] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   20.569085] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.569108] pnp: PnP ACPI init
[   20.569115] ACPI: bus type pnp registered
[   20.573724] pnp: PnP ACPI: found 13 devices
[   20.573726] ACPI: ACPI bus type pnp unregistered
[   20.573922] PCI: Using ACPI for IRQ routing
[   20.573927] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.583989] NET: Registered protocol family 8
[   20.583991] NET: Registered protocol family 20
[   20.584102] AppArmor: AppArmor Filesystem Enabled
[   20.587955] Time: tsc clocksource has been installed.
[   20.595976] system 00:01: ioport range 0x1000-0x107f has been reserved
[   20.595980] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   20.595983] system 00:01: ioport range 0x1400-0x147f has been reserved
[   20.595986] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   20.595988] system 00:01: ioport range 0x1800-0x187f has been reserved
[   20.595991] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   20.595993] system 00:01: ioport range 0x2000-0x207f has been reserved
[   20.595996] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   20.596000] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   20.596003] system 00:01: iomem range 0x3c000000-0x3fffffff could not be reserved
[   20.596006] system 00:01: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   20.596011] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   20.596013] system 00:02: ioport range 0x290-0x29f has been reserved
[   20.596021] system 00:0c: iomem range 0xd1800-0xd3fff has been reserved
[   20.596024] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   20.596027] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   20.596030] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   20.596032] system 00:0c: iomem range 0x3bff0000-0x3bffffff could not be reserved
[   20.596035] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[   20.596038] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   20.596041] system 00:0c: iomem range 0x100000-0x3bfeffff could not be reserved
[   20.596043] system 00:0c: iomem range 0x3c000000-0x3fffffff could not be reserved
[   20.596046] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   20.596049] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.596375] PCI: Bridge: 0000:00:10.0
[   20.596377]   IO window: a000-afff
[   20.596381]   MEM window: f5000000-f50fffff
[   20.596383]   PREFETCH window: disabled.
[   20.596394] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   20.596427] NET: Registered protocol family 2
[   20.632013] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   20.632462] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   20.634321] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   20.635229] TCP: Hash tables configured (established 131072 bind 65536)
[   20.635232] TCP reno registered
[   20.644080] checking if image is initramfs... it is
[   21.099590] Switched to high resolution mode on CPU 0
[   21.184459] Freeing initrd memory: 7487k freed
[   21.191774] audit: initializing netlink socket (disabled)
[   21.191787] audit(1212265740.168:1): initialized
[   21.193464] VFS: Disk quotas dquot_6.5.1
[   21.193527] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.193653] io scheduler noop registered
[   21.193655] io scheduler anticipatory registered
[   21.193657] io scheduler deadline registered
[   21.193743] io scheduler cfq registered (default)
[   21.193758] Boot video device is 0000:00:05.0
[   21.217475] Real Time Clock Driver v1.12ac
[   21.217570] Linux agpgart interface v0.102
[   21.217572] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.217699] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.218190] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.218800] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.218858] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.218934] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.221530] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.221534] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.227589] mice: PS/2 mouse device common for all mice
[   21.227620] cpuidle: using governor ladder
[   21.227622] cpuidle: using governor menu
[   21.227769] NET: Registered protocol family 1
[   21.227862] registered taskstats version 1
[   21.227997]   Magic number: 8:372:499
[   21.228127] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.228130] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.228132] EDD information not available.
[   21.228140] Freeing unused kernel memory: 320k freed
[   21.263444] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.400738] fuse init (API version 7.9)
[   22.419542] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.194577] usbcore: registered new interface driver usbfs
[   23.194598] usbcore: registered new interface driver hub
[   23.205972] usbcore: registered new device driver usb
[   23.214139] SCSI subsystem initialized
[   23.249939] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.250342] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   23.250350] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   23.250452] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.250459] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   23.250711] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   23.250733] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xf5108000
[   23.273889] libata version 3.00 loaded.
[   23.288207] 8139too Fast Ethernet driver 0.9.28
[   23.307976] usb usb1: configuration #1 chosen from 1 choice
[   23.307999] hub 1-0:1.0: USB hub found
[   23.308008] hub 1-0:1.0: 8 ports detected
[   23.410242] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   23.410252] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   23.410372] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   23.410378] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   23.410435] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   23.410468] ehci_hcd 0000:00:0b.1: debug port 1
[   23.410471] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   23.410483] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xf5104000
[   23.413396] Floppy drive(s): fd0 is 1.44M
[   23.421780] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.421894] usb usb2: configuration #1 chosen from 1 choice
[   23.421915] hub 2-0:1.0: USB hub found
[   23.421921] hub 2-0:1.0: 8 ports detected
[   23.433675] FDC 0 is a post-1991 82077
[   23.526339] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   23.526349] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   23.526928] eth0: RealTek RTL8139 at 0xa000, 00:c1:26:06:b4:02, IRQ 16
[   23.526930] eth0:  Identified 8139 chip type 'RTL-8139C'
[   23.528681] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   23.529035] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   23.529043] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   23.529048] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   23.530791] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   24.049965] forcedeth 0000:00:14.0: ifname eth1, PHY OUI 0x3f1 @ 7, addr 00:14:85:e5:6a:46
[   24.049971] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   24.050682] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   24.050691] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   24.103837] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[f5001000-f50017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.112223] pata_amd 0000:00:0d.0: version 0.3.10
[   24.112286] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.113909] scsi0 : pata_amd
[   24.114319] scsi1 : pata_amd
[   24.115034] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   24.115036] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   24.293325] ata1.00: HPA unlocked: 234490943 -> 234493056, native 234493056
[   24.293332] ata1.00: ATA-7: SAMSUNG SP1203N, TL100-24, max UDMA/100
[   24.293334] ata1.00: 234493056 sectors, multi 16: LBA48 
[   24.301317] ata1.01: HPA unlocked: 156365903 -> 156368016, native 156368016
[   24.301320] ata1.01: ATA-7: SAMSUNG SP0802N, TK100-31, max UDMA/100
[   24.301322] ata1.01: 156368016 sectors, multi 16: LBA48 
[   24.309346] ata1.00: configured for UDMA/100
[   24.317355] ata1.01: configured for UDMA/100
[   24.800944] ata2.00: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
[   24.800961] ata2.01: ATAPI: SONY    DVD RW DRU-810A, 1.0a, max UDMA/33
[   24.972749] ata2.00: configured for UDMA/33
[   25.144863] ata2.01: configured for UDMA/33
[   25.144983] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1203N  TL10 PQ: 0 ANSI: 5
[   25.145365] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
[   25.146383] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX230ED  4YS1 PQ: 0 ANSI: 5
[   25.148948] scsi 1:0:1:0: CD-ROM            SONY     DVD RW DRU-810A  1.0a PQ: 0 ANSI: 5
[   25.150597] sata_nv 0000:00:0e.0: version 3.5
[   25.150956] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   25.150965] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   25.151097] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.152707] scsi2 : sata_nv
[   25.153021] scsi3 : sata_nv
[   25.153194] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   25.153197] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   25.380289] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000148500e50fc7]
[   25.464133] ata3: SATA link down (SStatus 0 SControl 300)
[   25.783881] ata4: SATA link down (SStatus 0 SControl 300)
[   25.794794] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   25.794798] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   25.794980] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   25.796378] scsi4 : sata_nv
[   25.796668] scsi5 : sata_nv
[   25.796836] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[   25.796839] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[   26.107629] ata5: SATA link down (SStatus 0 SControl 300)
[   26.427387] ata6: SATA link down (SStatus 0 SControl 300)
[   26.447608] Driver 'sd' needs updating - please use bus_type methods
[   26.447699] sd 0:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   26.447710] sd 0:0:0:0: [sda] Write Protect is off
[   26.447712] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.447725] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.447764] sd 0:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   26.447771] sd 0:0:0:0: [sda] Write Protect is off
[   26.447773] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.447784] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.447788]  sda: sda1 sda2 sda3 sda4
[   26.451767] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.451839] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   26.451850] sd 0:0:1:0: [sdb] Write Protect is off
[   26.451852] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.451865] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.451899] sd 0:0:1:0: [sdb] 156368016 512-byte hardware sectors (80060 MB)
[   26.451907] sd 0:0:1:0: [sdb] Write Protect is off
[   26.451909] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.451920] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.451924]  sdb:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.467032]  sdb1 sdb2 < sdb5 >
[   26.492938] sd 0:0:1:0: [sdb] Attached SCSI disk
[   26.500650] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.500669] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.500684] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   26.500698] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   26.503794] sr0: scsi3-mmc drive: 98x/52x writer cd/rw xa/form2 cdda tray
[   26.503801] Uniform CD-ROM driver Revision: 3.20
[   26.503851] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.516293] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   26.516350] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   27.121144] Attempting manual resume
[   27.121148] swsusp: Resume From Partition 8:21
[   27.121150] PM: Checking swsusp image.
[   27.132845] PM: Resume from disk failed.
[   27.174500] kjournald starting.  Commit interval 5 seconds
[   27.174516] EXT3-fs: mounted filesystem with ordered data mode.
[   37.079549] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.398326] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   37.398343] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   37.646880] nvidia: module license 'NVIDIA' taints kernel.
[   38.192552] input: Power Button (FF) as /devices/virtual/input/input3
[   38.214827] ACPI: Power Button (FF) [PWRF]
[   38.214908] input: Power Button (CM) as /devices/virtual/input/input4
[   38.228165] ACPI: Power Button (CM) [PWRB]
[   38.288970] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   38.300832] parport_pc 00:09: reported by Plug and Play ACPI
[   38.300893] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.393679] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   39.393684] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   39.393773] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   39.950192] udev: renamed network interface eth0 to eth1
[   39.968702] udev: renamed network interface eth1_rename to eth0
[   40.010166] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   40.010172] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[   40.010178] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   40.017752] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   40.739496] NET: Registered protocol family 10
[   40.739688] lo: Disabled Privacy Extensions
[   42.596977] lp0: using parport0 (interrupt-driven).
[   42.701122] Adding 2819368k swap on /dev/sdb5.  Priority:-1 extents:1 across:2819368k
[   43.364114] EXT3 FS on sdb1, internal journal
[   44.993869] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.407278] No dock devices found.
[   45.660451] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   45.660485] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   45.660487] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   46.629826] ppdev: user-space parallel port driver
[   46.763596] audit(1212290966.037:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5229 profile="/usr/sbin/cupsd" namespace="default"
[   47.011323] Marking TSC unstable due to cpufreq changes
[   47.018255] Time: acpi_pm clocksource has been installed.
[   47.271239] Clocksource tsc unstable (delta = -272742415 ns)
[   48.126569] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   48.184363] Bluetooth: Core ver 2.11
[   48.184796] NET: Registered protocol family 31
[   48.184799] Bluetooth: HCI device and connection manager initialized
[   48.184802] Bluetooth: HCI socket layer initialized
[   48.225085] Bluetooth: L2CAP ver 2.9
[   48.225091] Bluetooth: L2CAP socket layer initialized
[   48.252215] Bluetooth: RFCOMM socket layer initialized
[   48.252406] Bluetooth: RFCOMM TTY layer initialized
[   48.252409] Bluetooth: RFCOMM ver 1.8
[   49.060791] eth0: no IPv6 routers present
[   52.767130] eth1: no IPv6 routers present


If anything else is needed, I shall gladly provide. 

Thanks for the help.

---

### Post by s_spiff on 2008-06-01
*bump*
Anyone???

---

### Post by pdwerryhouse on 2008-06-01
Does ethtool show the link as being up?

For example, here's the output from mine:

```
# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```

Sometimes speed/duplex autonegotiation can cause problems with cheap switches/hubs. Might be worth trying something like:

ethtool -s eth1 autoneg off speed 100 duplex full

(assuming that ethtool works with your card; it doesn't always).

---

### Post by s_spiff on 2008-06-01
looks like it doesn't. Here's what I got when I i/p ethtool eth1 :
> 
Settings for eth1:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
    Current message level: 0x00000007 (7)
Cannot get link status: Operation not permitted



now what??

---

### Post by s_spiff on 2008-06-01
ok..it needed a sudo.

here's the output :

> 
alok@spiffed:~$ sudo ethtool eth1
[sudo] password for alok: 
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: mb
    Current message level: 0x00000007 (7)
    Link detected: yes
alok@spiffed:~$ sudo ethtool -s eth1 autoneg off speed 100 duplex full
alok@spiffed:~$ 



---

### Post by pdwerryhouse on 2008-06-04
Right, that all seems ok then, your network card definitely has a link.

I notice that you're using a subnet mask of 255.255.0.0 on that interface. Is your server using that subnet mask also?

---

