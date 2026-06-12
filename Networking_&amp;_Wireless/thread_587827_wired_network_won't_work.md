---
title: "wired network won't work"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Peque on 2007-10-23
Hey forum. 

I have an huge problem. 
Suddenly this morning as I turned on my PC at work - I'm not able to get connection to the wired network (only wireless) 
I have checked that there's connection - using a windows Machine -. gets the dhcp address at once. 

Connection my Gutsy 7.10 shows only wireless network - eventhough there's ligth in the wired cable etc etc etc: 

Ifup eth1 gives me: ifup: interface eth1 already configured

My /etc/network/interfaces: 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp


But the only error I can see is this one in /var/log/message:

Oct 23 08:56:59 pbj-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Oct 23 08:56:59 pbj-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct 23 08:56:59 pbj-linux dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct 23 08:57:28 pbj-linux kernel: [  309.128488] tg3: eth1: Link is up at 1000 Mbps, full duplex.
Oct 23 08:57:28 pbj-linux kernel: [  309.128492] tg3: eth1: Flow control is off for TX and off for RX.
Oct 23 08:57:29 pbj-linux kernel: [  309.237504] ADDRCONF(NETDEV_UP): eth1: link is not ready
                                                                                                    

What can I do to get this to work?? 
I have tried reconfigurating the network, network-manager - so I'm out of ideas

ifconfig: 
```
eth0      Link encap:Ethernet  HWaddr 00:1C:26:41:1B:99
          inet addr:192.168.2.35  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe41:1b99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4254 errors:0 dropped:292 overruns:0 frame:0
          TX packets:2334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1698298 (1.6 MB)  TX bytes:152958690 (145.8 MB)
          Interrupt:10

eth1      Link encap:Ethernet  HWaddr 00:1C:23:8D:21:0B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18

eth1:avah Link encap:Ethernet  HWaddr 00:1C:23:8D:21:0B
          inet addr:169.254.2.197  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:176 (176.0 b)  TX bytes:176 (176.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.84.1  Bcast:192.168.84.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.85.1  Bcast:192.168.85.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```


And lshw -C network
```
 *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:26:41:1b:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic ip=192.168.2.35 latency=0 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 02
       serial: 00:1c:23:8d:21:0b
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=1GB/s

```

dmesg
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=63e098c9-2811-45d4-b2b8-9b6546b89e80 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7eb6400 (usable)
[    0.000000]  BIOS-e820: 00000000d7eb6400 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884406) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000FBED0 checksum 0
[    0.000000] ACPI: RSDP 000FBED0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT D7EB7E00, 0064 (r1 DELL    M08     27D70417 ASL        61)
[    0.000000] ACPI: FACP D7EB7C9C, 00F4 (r4 DELL    M08     27D70417 ASL        61)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT D7EB8400, 4E6B (r2 INT430 SYSFexxx     1001 INTL 20050624)
[    0.000000] ACPI: FACS D7EC6C00, 0040
[    0.000000] ACPI: HPET D7EB7F00, 0038 (r1 DELL    M08            1 ASL        61)
[    0.000000] ACPI: APIC D7EB8000, 0068 (r1 DELL    M08     27D70417 ASL        47)
[    0.000000] ACPI: ASF! D7EB7C00, 006A (r32 DELL    M08     27D70417 ASL        61)
[    0.000000] ACPI: MCFG D7EB7FC0, 003E (r16 DELL    M08     27D70417 ASL        61)
[    0.000000] ACPI: SLIC D7EB809C, 0176 (r1 DELL    M08     27D70417 ASL        61)
[    0.000000] ACPI: TCPA D7EB8300, 0032 (r1                        0 ASL         0)
[    0.000000] ACPI: SSDT D7EC7000, 0206 (r1 DELL    M08     20000BEE ASL        61)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 884406) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1179648
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   884406
[    0.000000]     0:  1048576 ->  1179648
[    0.000000] On node 0 totalpages: 1015381
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 866030 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000d7eb6000 - 00000000d7eb7000
[    0.000000] swsusp: Registered nosave memory region: 00000000d7eb7000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f8000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f8000000 - 00000000fc000000
[    0.000000] swsusp: Registered nosave memory region: 00000000fc000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee10000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee10000 - 00000000fff00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e2000000 (gap: e0000000:18000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 998128
[    0.000000] Kernel command line: root=UUID=63e098c9-2811-45d4-b2b8-9b6546b89e80 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   11.111025] time.c: Detected 1995.001 MHz processor.
[   11.111760] Console: colour VGA+ 80x25
[   11.111778] Checking aperture...
[   11.111781] CPU 0: aperture @ 8000000 size 32 MB
[   11.111783] Aperture too small (32 MB)
[   11.121313] No AGP bridge found
[   11.121315] Your BIOS doesn't leave a aperture memory hole
[   11.121317] Please enable the IOMMU option in the BIOS setup
[   11.121319] This costs you 64 MB of RAM
[   11.150370] Mapping aperture over 65536 KB of RAM @ 4000000
[   11.185779] Memory: 3919512k/4718592k available (2274k kernel code, 142012k reserved, 1181k data, 296k init)
[   11.185824] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.264818] Calibrating delay using timer specific routine.. 3993.13 BogoMIPS (lpj=7986274)
[   11.264847] Security Framework v1.0.0 initialized
[   11.264853] SELinux:  Disabled at boot.
[   11.265144] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   11.267422] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   11.268536] Mount-cache hash table entries: 256
[   11.268656] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.268659] CPU: L2 Cache: 512K (64 bytes/line)
[   11.268662] CPU 0/0 -> Node 0
[   11.268664] CPU: Physical Processor ID: 0
[   11.268665] CPU: Processor Core ID: 0
[   11.268682] SMP alternatives: switching to UP code
[   11.268916] Early unpacking initramfs... done
[   11.562451] ACPI: Core revision 20070126
[   11.562503] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.609313] Using local APIC timer interrupts.
[   11.659413] result 12468751
[   11.659415] Detected 12.468 MHz APIC timer.
[   11.660663] SMP alternatives: switching to SMP code
[   11.660767] Booting processor 1/2 APIC 0x1
[   11.670449] Initializing CPU#1
[   11.748148] Calibrating delay using timer specific routine.. 3990.09 BogoMIPS (lpj=7980188)
[   11.748154] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.748157] CPU: L2 Cache: 512K (64 bytes/line)
[   11.748159] CPU 1/1 -> Node 0
[   11.748161] CPU: Physical Processor ID: 0
[   11.748163] CPU: Processor Core ID: 1
[   11.748259] AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 01
[   11.752557] Brought up 2 CPUs
[   12.229305] migration_cost=155
[   12.229905] NET: Registered protocol family 16
[   12.229989] ACPI: bus type pci registered
[   12.229999] PCI: Using configuration type 1
[   12.236435] ACPI: EC: Look up EC in DSDT
[   12.272382] ACPI: SSDT D7EC6C80, 0043 (r1  LMPWR  DELLLOM     1001 INTL 20050624)
[   12.272511] ACPI: Interpreter enabled
[   12.272514] ACPI: (supports S0 S3 S4 S5)
[   12.272529] ACPI: Using IOAPIC for interrupt routing
[   12.356402] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.356411] PCI: Probing PCI hardware (bus 00)
[   12.357688] PCI: Transparent bridge - 0000:00:14.4
[   12.357782] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.358018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[   12.358167] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.358269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   12.358372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   12.425538] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *0, disabled.
[   12.425625] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *0, disabled.
[   12.425704] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *0, disabled.
[   12.425782] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[   12.425862] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.425942] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.426023] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.426104] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   12.426205] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.426215] pnp: PnP ACPI init
[   12.426227] ACPI: bus type pnp registered
[   12.511440] pnp: PnP ACPI: found 15 devices
[   12.511443] ACPI: ACPI bus type pnp unregistered
[   12.511502] PCI: Using ACPI for IRQ routing
[   12.511504] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.511519] PCI: Cannot allocate resource region 5 of device 0000:00:12.0
[   12.511743] NET: Registered protocol family 8
[   12.511745] NET: Registered protocol family 20
[   12.511809] PCI-DMA: Disabling AGP.
[   12.512097] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   12.512102] PCI-DMA: using GART IOMMU.
[   12.512110] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   12.512340] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   12.512345] hpet0: 4 32-bit timers, 14318180 Hz
[   12.513463] pnp: 00:05: ioport range 0xc80-0xcaf has been reserved
[   12.513466] pnp: 00:05: ioport range 0xcc0-0xcff could not be reserved
[   12.513478] pnp: 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[   12.513486] pnp: 00:0b: ioport range 0xcb0-0xcbb has been reserved
[   12.513490] pnp: 00:0b: iomem range 0xfed40000-0xfed44fff has been reserved
[   12.513495] pnp: 00:0c: ioport range 0x900-0x97f has been reserved
[   12.513499] pnp: 00:0c: ioport range 0x980-0x9ff has been reserved
[   12.513501] pnp: 00:0c: ioport range 0xa00-0xa7f has been reserved
[   12.513504] pnp: 00:0c: ioport range 0xa80-0xaff has been reserved
[   12.513507] pnp: 00:0c: ioport range 0xcb0-0xcff could not be reserved
[   12.513510] pnp: 00:0c: ioport range 0xd00-0xd7f has been reserved
[   12.513513] pnp: 00:0c: ioport range 0xd80-0xdff has been reserved
[   12.513519] pnp: 00:0d: ioport range 0xf400-0xf4fe has been reserved
[   12.513523] pnp: 00:0d: ioport range 0x1006-0x1007 has been reserved
[   12.513526] pnp: 00:0d: ioport range 0x100a-0x1059 has been reserved
[   12.513528] pnp: 00:0d: ioport range 0x1080-0x10bf has been reserved
[   12.513531] pnp: 00:0d: ioport range 0x10c0-0x10df could not be reserved
[   12.513534] pnp: 00:0d: ioport range 0x1010-0x102f has been reserved
[   12.513538] pnp: 00:0d: ioport range 0x809-0x809 has been reserved
[   12.513544] pnp: 00:0e: iomem range 0x0-0x9efff could not be reserved
[   12.513547] pnp: 00:0e: iomem range 0x9f000-0x9ffff could not be reserved
[   12.513550] pnp: 00:0e: iomem range 0xc0000-0xcffff has been reserved
[   12.513552] pnp: 00:0e: iomem range 0xe0000-0xfffff has been reserved
[   12.513867] PCI: Bridge: 0000:00:01.0
[   12.513869]   IO window: e000-efff
[   12.513872]   MEM window: fe900000-feafffff
[   12.513875]   PREFETCH window: e0000000-efffffff
[   12.513878] PCI: Bridge: 0000:00:05.0
[   12.513879]   IO window: disabled.
[   12.513882]   MEM window: fe800000-fe8fffff
[   12.513884]   PREFETCH window: disabled.
[   12.513887] PCI: Bridge: 0000:00:06.0
[   12.513889]   IO window: disabled.
[   12.513892]   MEM window: fe700000-fe7fffff
[   12.513894]   PREFETCH window: disabled.
[   12.513904] PCI: Bus 4, cardbus bridge: 0000:03:01.0
[   12.513906]   IO window: 00002000-000020ff
[   12.513911]   IO window: 00002400-000024ff
[   12.513916]   PREFETCH window: f0000000-f3ffffff
[   12.513922]   MEM window: 120000000-123ffffff
[   12.513926] PCI: Bridge: 0000:00:14.4
[   12.513929]   IO window: 2000-2fff
[   12.513935]   MEM window: fe600000-fe6fffff
[   12.513939]   PREFETCH window: f0000000-f3ffffff
[   12.513957] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   12.513963] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   12.513983] PCI: Enabling device 0000:03:01.0 (0000 -> 0003)
[   12.513992] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 23 (level, low) -> IRQ 23
[   12.514051] NET: Registered protocol family 2
[   12.515734] Time: hpet clocksource has been installed.
[   12.559806] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.561183] TCP established hash table entries: 524288 (order: 11, 12582912 bytes)
[   12.567652] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   12.568225] TCP: Hash tables configured (established 524288 bind 65536)
[   12.568228] TCP reno registered
[   12.583816] checking if image is initramfs... it is
[   13.168673] Freeing initrd memory: 7203k freed
[   13.173404] audit: initializing netlink socket (disabled)
[   13.173416] audit(1193122351.944:1): initialized
[   13.175575] VFS: Disk quotas dquot_6.5.1
[   13.175638] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.175739] io scheduler noop registered
[   13.175741] io scheduler anticipatory registered
[   13.175743] io scheduler deadline registered
[   13.175843] io scheduler cfq registered (default)
[   13.175855] PCI: MSI quirk detected. MSI deactivated.
[   13.177627] Boot video device is 0000:01:05.0
[   13.177783] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   13.177802] assign_interrupt_mode Found MSI capability
[   13.177806] Allocate Port Service[0000:00:05.0:pcie00]
[   13.177869] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.177887] assign_interrupt_mode Found MSI capability
[   13.177890] Allocate Port Service[0000:00:06.0:pcie00]
[   13.204955] Real Time Clock Driver v1.12ac
[   13.205086] hpet_resources: 0xfed00000 is busy
[   13.205135] Linux agpgart interface v0.102 (c) Dave Jones
[   13.205138] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.205259] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.205953] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.206643] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.206865] input: Macintosh mouse button emulation as /class/input/input0
[   13.206940] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.211163] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.211170] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.211333] mice: PS/2 mouse device common for all mice
[   13.211455] TCP cubic registered
[   13.211513] NET: Registered protocol family 1
[   13.211721] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.211728] Freeing unused kernel memory: 296k freed
[   13.215336] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.393974] AppArmor: AppArmor initialized<5>audit(1193122353.164:2):  type=1505 info="AppArmor initialized" pid=1278
[   14.399349] fuse init (API version 7.8)
[   14.404576] Failure registering capabilities with primary security module.
[   14.446693] ACPI: Processor [CPU0] (supports 8 throttling states)
[   14.447018] ACPI: Processor [CPU1] (supports 8 throttling states)
[   14.451631] ACPI: Thermal Zone [THM] (63 C)
[   14.958958] SCSI subsystem initialized
[   15.008873] libata version 2.21 loaded.
[   15.010349] ahci 0000:00:12.0: version 2.2
[   15.010376] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
[   15.010553] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   15.017514] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.017519] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.029976] usbcore: registered new interface driver usbfs
[   15.030003] usbcore: registered new interface driver hub
[   15.035299] usbcore: registered new device driver usb
[   15.071613] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.014219] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   16.014224] ahci 0000:00:12.0: flags: ncq ilck pm led clo pmp pio slum part
[   16.015040] scsi0 : ahci
[   16.015283] scsi1 : ahci
[   16.015456] scsi2 : ahci
[   16.015627] scsi3 : ahci
[   16.015918] ata1: SATA max UDMA/133 cmd 0xffffc20001438100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   16.015924] ata2: SATA max UDMA/133 cmd 0xffffc20001438180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   16.015929] ata3: SATA max UDMA/133 cmd 0xffffc20001438200 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   16.015934] ata4: SATA max UDMA/133 cmd 0xffffc20001438280 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 22
[   16.501544] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.846502] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL140D, max UDMA/100
[   16.846506] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
[   16.847343] ata1.00: configured for UDMA/100
[   17.161181] ata2: SATA link down (SStatus 0 SControl 300)
[   17.477007] ata3: SATA link down (SStatus 0 SControl 300)
[   17.788837] ata4: SATA link down (SStatus 0 SControl 300)
[   17.789318] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL14 PQ: 0 ANSI: 5
[   17.790457] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[   17.790474] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   17.790486] SB600_PATA: chipset revision 0
[   17.790488] SB600_PATA: not 100% native mode: will probe irqs later
[   17.790496]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[   17.790507] Probing IDE interface ide0...
[   17.805335] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.805346] sd 0:0:0:0: [sda] Write Protect is off
[   17.805348] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.805362] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.805441] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.805448] sd 0:0:0:0: [sda] Write Protect is off
[   17.805450] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.805462] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.805467]  sda: sda1 sda2 sda3
[   17.877826] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.881028] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.090893] Attempting manual resume
[   18.090897] swsusp: Resume From Partition 8:2
[   18.090899] PM: Checking swsusp image.
[   18.091174] PM: Resume from disk failed.
[   18.136900] kjournald starting.  Commit interval 5 seconds
[   18.136912] EXT3-fs: mounted filesystem with ordered data mode.
[   18.553130] hda: Optiarc DVD+/-RW AD-5540A, ATAPI CD/DVD-ROM drive
[   19.249492] hda: selected mode 0x42
[   19.249687] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.250316] ACPI: PCI Interrupt 0000:03:01.4[A] -> GSI 23 (level, low) -> IRQ 23
[   19.301568] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[fe6ff000-fe6ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   19.305034] tg3.c:v3.77 (May 31, 2007)
[   19.305099] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   19.305112] PCI: Setting latency timer of device 0000:09:00.0 to 64
[   19.325626] eth0: Tigon3 [partno(BCM95755m) rev a002 PHY(5755)] (PCI Express) 10/100/1000Base-T Ethernet 00:1c:23:8d:21:0b
[   19.325633] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   19.325636] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   19.325802] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.325969] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   19.326159] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   19.326185] ohci_hcd 0000:00:13.0: irq 16, io mem 0xffb00000
[   19.386774] usb usb1: configuration #1 chosen from 1 choice
[   19.386799] hub 1-0:1.0: USB hub found
[   19.386812] hub 1-0:1.0: 2 ports detected
[   19.492382] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.492554] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   19.492607] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   19.492631] ohci_hcd 0000:00:13.1: irq 17, io mem 0xffb01000
[   19.554912] usb usb2: configuration #1 chosen from 1 choice
[   19.554938] hub 2-0:1.0: USB hub found
[   19.554951] hub 2-0:1.0: 2 ports detected
[   19.656253] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.656442] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   19.656498] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   19.656523] ohci_hcd 0000:00:13.2: irq 18, io mem 0xffb02000
[   19.720248] usb usb3: configuration #1 chosen from 1 choice
[   19.720273] hub 3-0:1.0: USB hub found
[   19.720286] hub 3-0:1.0: 2 ports detected
[   19.826810] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[   19.826982] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   19.827038] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   19.827063] ohci_hcd 0000:00:13.3: irq 17, io mem 0xffb03000
[   19.884158] usb usb4: configuration #1 chosen from 1 choice
[   19.884182] hub 4-0:1.0: USB hub found
[   19.884195] hub 4-0:1.0: 2 ports detected
[   19.988085] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[   19.988264] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   19.988322] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   19.988344] ohci_hcd 0000:00:13.4: irq 18, io mem 0xffb04000
[   20.051357] usb usb5: configuration #1 chosen from 1 choice
[   20.051385] hub 5-0:1.0: USB hub found
[   20.051397] hub 5-0:1.0: 2 ports detected
[   20.152713] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 20 (level, low) -> IRQ 20
[   20.152894] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   20.153040] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   20.153085] ehci_hcd 0000:00:13.5: debug port 1
[   20.153099] ehci_hcd 0000:00:13.5: irq 20, io mem 0xffa80000
[   20.315446] usb 4-2: new full speed USB device using ohci_hcd and address 2
[   20.315467] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.315609] usb usb6: configuration #1 chosen from 1 choice
[   20.315634] hub 6-0:1.0: USB hub found
[   20.315641] hub 6-0:1.0: 10 ports detected
[   20.579939] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc000355c8c70]
[   21.130999] usb 6-9: new high speed USB device using ehci_hcd and address 3
[   21.267364] usb 6-9: configuration #1 chosen from 1 choice
[   21.267418] hub 6-9:1.0: USB hub found
[   21.267519] hub 6-9:1.0: 4 ports detected
[   21.694683] usb 4-2: new full speed USB device using ohci_hcd and address 3
[   21.947653] usb 4-2: configuration #1 chosen from 1 choice
[   22.150518] usb 6-9.2: new high speed USB device using ehci_hcd and address 4
[   22.245802] usb 6-9.2: configuration #1 chosen from 1 choice
[   22.245872] hub 6-9.2:1.0: USB hub found
[   22.245972] hub 6-9.2:1.0: 4 ports detected
[   22.554337] usb 6-9.2.4: new low speed USB device using ehci_hcd and address 5
[   22.658616] usb 6-9.2.4: configuration #1 chosen from 1 choice
[   22.914047] usb 6-9.2.3: new low speed USB device using ehci_hcd and address 6
[   23.011964] usb 6-9.2.3: configuration #1 chosen from 1 choice
[   25.863956] PM: Writing back config space on device 0000:09:00.0 at offset c (was ff690000, writing 0)
[   27.585117] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.592797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.455923] Bluetooth: Core ver 2.11
[   28.455969] NET: Registered protocol family 31
[   28.455971] Bluetooth: HCI device and connection manager initialized
[   28.455974] Bluetooth: HCI socket layer initialized
[   28.479796] NET: Registered protocol family 17
[   28.631014] Bluetooth: HCI USB driver ver 2.9
[   28.635248] usbcore: registered new interface driver hci_usb
[   28.658644] input: PC Speaker as /class/input/input2
[   28.747706] usbcore: registered new interface driver hiddev
[   28.752012] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   28.752073] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.5-9.2.4
[   28.755761] input: Dell Dell USB Keyboard as /class/input/input4
[   28.755805] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:13.5-9.2.3
[   28.755818] usbcore: registered new interface driver usbhid
[   28.755821] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   28.877225] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.991248] input: PS/2 Mouse as /class/input/input5
[   29.010698] input: AlpsPS/2 ALPS GlidePoint as /class/input/input6
[   29.011038] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0206]
[   29.011073] Yenta O2: res at 0x94/0xD4: 00/ea
[   29.011075] Yenta O2: enabling read prefetch/write burst
[   29.017964] parport_pc 00:0a: reported by Plug and Play ACPI
[   29.018230] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   29.128208] ieee80211_crypt: registered algorithm 'NULL'
[   29.130847] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   29.130851] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   29.140194] Yenta: ISA IRQ mask 0x0c38, PCI irq 23
[   29.140201] Socket status: 30000006
[   29.140204] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   29.140211] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   29.140215] pcmcia: parent PCI bridge Memory window: 0xfe600000 - 0xfe6fffff
[   29.140218] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf3ffffff
[   29.168199] bcm43xx driver
[   29.168820] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.168838] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   29.405762] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   29.405806] Uniform CD-ROM driver Revision: 3.20
[   29.495464] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   30.718108] hda_intel: azx_get_response timeout, switching to polling mode...
[   31.721546] hda_intel: azx_get_response timeout, switching to single_cmd mode...
[   31.722188] hda_codec: No auto-config is available, default to model=ref
[   32.679358] loop: module loaded
[   32.698454] lp0: using parport0 (interrupt-driven).
[   32.882445] Adding 3903784k swap on /dev/sda2.  Priority:-1 extents:1 across:3903784k
[   33.310249] EXT3 FS on sda3, internal journal
[   35.087624] ACPI: Battery Slot [BAT0] (battery present)
[   35.087865] ACPI: Battery Slot [BAT1] (battery absent)
[   35.353078] ACPI: ACPI Dock Station Driver
[   35.358140] ACPI: \_SB_.PCI0.IDE1.PRI_.MAST: found ejectable bay
[   35.358146] ACPI: \_SB_.PCI0.IDE1.PRI_.MAST: Adding notify handler
[   35.358223] ACPI: Bay [\_SB_.PCI0.IDE1.PRI_.MAST] Added
[   35.372135] input: Lid Switch as /class/input/input7
[   35.372421] ACPI: Lid Switch [LID]
[   35.379356] input: Power Button (CM) as /class/input/input8
[   35.379624] ACPI: Power Button (CM) [PBTN]
[   35.380660] input: Sleep Button (CM) as /class/input/input9
[   35.380925] ACPI: Sleep Button (CM) [SBTN]
[   35.431851] ACPI: AC Adapter [AC] (on-line)
[   35.461191] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   35.461662] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   35.949363] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (version 2.00.00)
[   35.949203] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[   35.949208] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   35.949211] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   35.949213] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   37.338509] ppdev: user-space parallel port driver
[   37.698741] audit(1193122377.153:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5214 profile="/usr/sbin/cupsd"
[   39.968912] Failure registering capabilities with primary security module.
[   40.208607] Bluetooth: L2CAP ver 2.8
[   40.208612] Bluetooth: L2CAP socket layer initialized
[   40.269632] Bluetooth: RFCOMM socket layer initialized
[   40.269709] Bluetooth: RFCOMM TTY layer initialized
[   40.269723] Bluetooth: RFCOMM ver 1.8
[   43.511089] vmmon: module license 'unspecified' taints kernel.
[   43.515209] /dev/vmmon[5635]: Module vmmon: registered with major=10 minor=165
[   43.515469] /dev/vmmon[5635]: Module vmmon: initialized
[   43.973192] /dev/vmnet: open called by PID 5662 (vmnet-bridge)
[   43.973439] /dev/vmnet: hub 0 does not exist, allocating memory.
[   43.973614] /dev/vmnet: port on hub 0 successfully opened
[   43.973778] bridge-eth0: enabling the bridge
[   43.973923] bridge-eth0: up
[   43.974044] bridge-eth0: already up
[   43.974048] bridge-eth0: attached
[   44.019860] /dev/vmnet: open called by PID 5681 (vmnet-bridge)
[   44.020106] /dev/vmnet: hub 2 does not exist, allocating memory.
[   44.020276] /dev/vmnet: port on hub 2 successfully opened
[   44.020442] bridge-eth1: enabling the bridge
[   44.020583] bridge-eth1: up
[   44.020735] bridge-eth1: already up
[   44.020738] bridge-eth1: attached
[   44.023833] /dev/vmnet: open called by PID 5686 (vmnet-bridge)
[   44.024111] /dev/vmnet: hub 3 does not exist, allocating memory.
[   44.024282] /dev/vmnet: port on hub 3 successfully opened
[   44.024480] bridge-vmnet1: peer interface vmnet1 not found, will wait for it to come up
[   44.024484] bridge-vmnet1: attached
[   44.044485] /dev/vmnet: open called by PID 5672 (vmnet-netifup)
[   44.044748] /dev/vmnet: hub 1 does not exist, allocating memory.
[   44.044922] /dev/vmnet: port on hub 1 successfully opened
[   44.047732] /dev/vmnet: open called by PID 5692 (vmnet-netifup)
[   44.047972] /dev/vmnet: hub 8 does not exist, allocating memory.
[   44.048143] /dev/vmnet: port on hub 8 successfully opened
[   44.062247] bridge-vmnet1: enabling the bridge
[   44.062631] bridge-vmnet1: up
[   44.084424] /dev/vmnet: open called by PID 5696 (vmnet-natd)
[   44.084661] /dev/vmnet: port on hub 8 successfully opened
[   44.250211] [fglrx] Maximum main memory to use for locked dma buffers: 3674 MBytes.
[   44.250491] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   44.277520] ACPI: PCI Interrupt 0000:01:05.0[B] -> GSI 19 (level, low) -> IRQ 19
[   44.804455] /dev/vmnet: open called by PID 5722 (vmnet-dhcpd)
[   44.804549] /dev/vmnet: port on hub 1 successfully opened
[   44.806130] /dev/vmnet: open called by PID 5723 (vmnet-dhcpd)
[   44.806310] /dev/vmnet: port on hub 8 successfully opened
[   47.904890] mtrr: no more MTRRs available
[   47.904993] mtrr: no more MTRRs available
[   47.905078] mtrr: no more MTRRs available
[   74.049731] NET: Registered protocol family 10
[   74.050325] lo: Disabled Privacy Extensions
[   74.050764] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   74.050847] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.821736] ieee80211_crypt: registered algorithm 'WEP'
[   79.419517] SoftMAC: Open Authentication completed with 00:90:4b:a0:18:98
[   79.459200] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   84.432493] vmnet1: no IPv6 routers present
[   84.992179] vmnet8: no IPv6 routers present
[   95.750252] eth0: no IPv6 routers present
[  261.442708] bridge-eth0: disabling the bridge
[  261.460518] bridge-eth0: down
[  262.063800] bridge-eth0: enabling the bridge
[  262.033401] bridge-eth0: up
[  262.033409] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  262.461601] bridge-eth0: disabling the bridge
[  262.488759] bridge-eth0: down
[  272.393562] bridge-eth0: enabling the bridge
[  272.434443] bridge-eth0: up
[  272.434470] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  274.477320] SoftMAC: Open Authentication completed with 00:90:4b:a0:18:98
[  274.491542] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  291.072053] eth0: no IPv6 routers present
[  309.108286] PM: Writing back config space on device 0000:09:00.0 at offset 1 (was 60100106, writing 100106)
[  309.128488] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[  309.128492] tg3: eth1: Flow control is off for TX and off for RX.
[  309.162177] bridge-eth1: disabling the bridge
[  309.177196] bridge-eth1: down
[  309.153412] PM: Writing back config space on device 0000:09:00.0 at offset 1 (was 60100106, writing 100106)
[  309.237489] bridge-eth1: enabling the bridge
[  309.237500] bridge-eth1: up
[  309.237504] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  838.397303] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  838.397321] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  838.397334] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```

Thanks

---

### Post by Blackcomb on 2007-10-23
> Suddenly this morning as I turned on my PC at work
so it worked before, or didn't it?

Have you tried to set a static IP address, netmask and gateway (+ restart network) ?

---

### Post by Peque on 2007-10-23
Yes - I have allso tried to give it a static ip. 

Well started at  - did some work - did some work out of the building - came back - and it wouldn't take the IP when I turned it on again  ???  
I haven't got the whole through the wired. 

And haven't got a clue of what happend. I have rebooted several times at work but no luck. 
Came back home - started the machine and got the wired working at once ?? 

So pretty funny what's gonna happen tomorrow?? 

But thanks
P

---

### Post by BotLobsta on 2007-10-31
I have this same problem on a Dell Latitude D830 with gutsy and a BCM5755M ethernet card.  I started noticing this about a month ago.  What happens is that the wired connection loses its link after a certain amount of time. (I havent figured out exactly how much)  It cannot get a dhcp address or function at all after that time.  If I restart/hibernate, it will be working again. (I have not tried suspending.)

Also, I have tried reloading the module for it (tg3), but that has had no effect.

---

### Post by tengil on 2007-11-08
It seems I have the same problem, more or less. Wireless is ok. Wired gets ip from dhcp at work but not at home. Other PCs at home (including feisty) are ok.

Did you resolve this problem?

---

### Post by BotLobsta on 2007-11-08
No.  I filed a bug report on it (#159808) but there has been no response on it.  I dont have another network to try it on so I cant try that.  I find it surprising that no one else has mentioned noticing this because I know there are a lot more users with the same kind of laptop that I have due to bugs with other hardware.  That makes me wonder if its an Ubuntu bug or a network bug.

---

### Post by tengil on 2007-11-08
Well, I just fixed my problem. Just had to restart my cable modem. The dhcp server was actually not sending ip to the new laptop.

Hope you work it out.

---

