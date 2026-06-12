---
title: "Feisty with Intel PRO wireless used to work..."
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by dubemasterd88 on 2007-09-21
Hey...
I have a very odd problem.  I have been using Feisty on my Dell XPS m1210, with an Intel PRO/Wireless 3945ABG card and it has been working since July.... Just 2 days ago, my wireless was working fine and I was using it.  I shut the computer down, and 6 hours later, Ubuntu does not recognize that I have any wireless card at all.  PLEASE HELP!!! Here is some info you might need to know:

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)




ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:18:8B:CA:0D:A0  
          inet addr:192.168.11.2  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:feca:da0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2087624 (1.9 MiB)  TX bytes:317550 (310.1 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by noob12 on 2007-09-21
Can you post the output of these:
```

uname -a

ifconfig -a

sudo lshw -C network

dmesg

```

---

### Post by dubemasterd88 on 2007-09-21
uname -a:
Linux ruben-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:18:8B:CA:0D:A0  
          inet addr:192.168.11.2  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:feca:da0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2289009 (2.1 MiB)  TX bytes:349656 (341.4 KiB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sudo lshw -C network:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:efdff000-efdfffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:ca:0d:a0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.11.2 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ef9fe000-ef9fffff irq:17


dmesg:
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f593400 end: 000000003f693400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f693400 size: 000000000096cc00 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004007000 end: 00000000f4007000 type: 2
[    0.000000] copy_e820_map() start: 00000000f4008000 size: 0000000000004000 end: 00000000f400c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000080000 end: 00000000feda0000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f693400 (usable)
[    0.000000]  BIOS-e820: 000000003f693400 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259731) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259731
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259731
[    0.000000] On node 0 totalpages: 259731
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30118 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1d0
[    0.000000] ACPI: RSDT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x3f693a0f
[    0.000000] ACPI: FADT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x3f694800
[    0.000000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x3f694f00
[    0.000000] ACPI: MADT (v001 DELL    M07     0x27d70402 ASL  0x00000047) @ 0x3f695000
[    0.000000] ACPI: MCFG (v016 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x3f694fc0
[    0.000000] ACPI: SLIC (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x3f69509c
[    0.000000] ACPI: BOOT (v001 DELL    M07     0x27d70402 ASL  0x00000061) @ 0x3f694bc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x3f693a4f
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Detected 1828.933 MHz processor.
[    5.915138] Built 1 zonelists.  Total pages: 257702
[    5.915142] Kernel command line: root=UUID=473503f2-78a8-4045-8824-9ecfa1fd6b54 ro quiet splash
[    5.915275] mapped APIC to ffffd000 (fee00000)
[    5.915277] mapped IOAPIC to ffffc000 (fec00000)
[    5.915280] Enabling fast FPU save and restore... done.
[    5.915282] Enabling unmasked SIMD FPU exception support... done.
[    5.915289] Initializing CPU#0
[    5.915352] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    5.916841] Console: colour VGA+ 80x25
[    5.917117] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    5.917400] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    5.936574] Memory: 1018732k/1038924k available (1993k kernel code, 19432k reserved, 900k data, 328k init, 121420k highmem)
[    5.936582] virtual kernel memory layout:
[    5.936583]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    5.936584]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    5.936585]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    5.936586]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    5.936587]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    5.936588]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[    5.936589]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[    5.936592] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    5.936732] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    5.936737] hpet0: 3 64-bit timers, 14318180 Hz
[    5.937741] Using HPET for base-timer
[    6.016603] Calibrating delay using timer specific routine.. 3661.52 BogoMIPS (lpj=7323056)
[    6.016638] Security Framework v1.0.0 initialized
[    6.016642] SELinux:  Disabled at boot.
[    6.016654] Mount-cache hash table entries: 512
[    6.016766] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[    6.016773] monitor/mwait feature present.
[    6.016774] using mwait in idle threads.
[    6.016779] CPU: L1 I cache: 32K, L1 D cache: 32K
[    6.016781] CPU: L2 cache: 2048K
[    6.016783] CPU: Physical Processor ID: 0
[    6.016785] CPU: Processor Core ID: 0
[    6.016786] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[    6.016794] Compat vDSO mapped to ffffe000.
[    6.016797] Remapping vsyscall page to ffffe000
[    6.016807] Checking 'hlt' instruction... OK.
[    6.032660] SMP alternatives: switching to UP code
[    6.032960] Early unpacking initramfs... done
[    6.323398] ACPI: Core revision 20060707
[    6.339708] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    6.342163] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 02
[    6.342179] SMP alternatives: switching to SMP code
[    6.342251] Booting processor 1/1 eip 3000
[    8.362993] Initializing CPU#1
[    8.440026] Calibrating delay using timer specific routine.. 3657.61 BogoMIPS (lpj=7315227)
[    8.440033] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[    8.440037] monitor/mwait feature present.
[    8.440040] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.440042] CPU: L2 cache: 2048K
[    8.440044] CPU: Physical Processor ID: 0
[    8.440045] CPU: Processor Core ID: 1
[    8.440046] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[    6.432403] CPU1: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 02
[    6.432423] Total of 2 processors activated (7319.14 BogoMIPS).
[    6.432620] ENABLING IO-APIC IRQs
[    6.432812] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    6.579652] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -1006173 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 1006173 usecs TSC skew, fixed it up.
[    0.003991] Brought up 2 CPUs
[    0.159018] migration_cost=197
[    0.159265] Booting paravirtualized kernel on bare hardware
[    0.159353] Time: 13:04:46  Date: 08/21/107
[    0.159379] NET: Registered protocol family 16
[    0.159455] EISA bus registered
[    0.159459] ACPI: bus type pci registered
[    0.187982] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=14
[    0.187984] PCI: Using configuration type 1
[    0.187986] Setting up standard PCI resources
[    0.214605] ACPI: Interpreter enabled
[    0.214608] ACPI: Using IOAPIC for interrupt routing
[    0.215445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.215453] PCI: Probing PCI hardware (bus 00)
[    0.215635] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.227783] Boot video device is 0000:00:02.0
[    0.228446] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.228450] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.229649] PCI: Transparent bridge - 0000:00:1e.0
[    0.229725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.249830] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.250067] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *4
[    0.250301] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.250537] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.250771] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.251006] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.251246] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.251484] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.252849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.253088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.253308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.253596] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.253999] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.254011] pnp: PnP ACPI init
[    0.284358] pnp: PnP ACPI: found 12 devices
[    0.284361] PnPBIOS: Disabled by ACPI PNP
[    0.284401] PCI: Using ACPI for IRQ routing
[    0.284404] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.335794] NET: Registered protocol family 8
[    0.335796] NET: Registered protocol family 20
[    0.352889] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.352892] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.352895] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.352900] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.352902] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.352905] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.352907] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.352910] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.352912] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.352918] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.352921] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.352923] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.352925] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.352927] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.353202] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.353206] PCI: Bridge: 0000:00:1c.0
[    0.353207]   IO window: disabled.
[    0.353213]   MEM window: disabled.
[    0.353218]   PREFETCH window: disabled.
[    0.353223] PCI: Bridge: 0000:00:1c.1
[    0.353225]   IO window: disabled.
[    0.353231]   MEM window: efd00000-efdfffff
[    0.353235]   PREFETCH window: disabled.
[    0.353241] PCI: Bridge: 0000:00:1c.3
[    0.353244]   IO window: d000-dfff
[    0.353250]   MEM window: efa00000-efcfffff
[    0.353255]   PREFETCH window: e0000000-e01fffff
[    0.353261] PCI: Bridge: 0000:00:1e.0
[    0.353262]   IO window: disabled.
[    0.353268]   MEM window: ef900000-ef9fffff
[    0.353272]   PREFETCH window: disabled.
[    0.353302] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.353309] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.353333] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.353339] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.353362] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[    0.353368] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.353382] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.353407] NET: Registered protocol family 2
[    0.395367] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.395465] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.395919] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.396163] TCP: Hash tables configured (established 131072 bind 65536)
[    0.396166] TCP reno registered
[    0.411412] checking if image is initramfs... it is
[    0.983098] Freeing initrd memory: 6771k freed
[    0.983271] Simple Boot Flag at 0x79 set to 0x1
[    0.983702] audit: initializing netlink socket (disabled)
[    0.983719] audit(1190379886.712:1): initialized
[    0.983813] highmem bounce pool size: 64 pages
[    0.983895] VFS: Disk quotas dquot_6.5.1
[    0.983913] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.983963] io scheduler noop registered
[    0.983965] io scheduler anticipatory registered
[    0.983967] io scheduler deadline registered
[    0.983977] io scheduler cfq registered (default)
[    0.984222] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.984281] assign_interrupt_mode Found MSI capability
[    0.984284] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.984315] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.984439] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.984497] assign_interrupt_mode Found MSI capability
[    0.984499] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.984529] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.984649] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.984708] assign_interrupt_mode Found MSI capability
[    0.984710] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.984738] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.984913] isapnp: Scanning for PnP cards...
[    1.338231] isapnp: No Plug & Play device found
[    1.357338] Real Time Clock Driver v1.12ac
[    1.357394] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.357959] mice: PS/2 mouse device common for all mice
[    1.358453] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.358658] input: Macintosh mouse button emulation as /class/input/input0
[    1.358690] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.358693] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.358932] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.361982] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.361985] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.362191] EISA: Probing bus 0 at eisa.0
[    1.362201] Cannot allocate resource for EISA slot 1
[    1.362231] EISA: Detected 0 cards.
[    1.392348] TCP cubic registered
[    1.392358] NET: Registered protocol family 1
[    1.392379] Starting balanced_irq
[    1.392385] Using IPI No-Shortcut mode
[    1.392449] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.392504] ACPI: (supports S0 S3 S4 S5)
[    1.392550]   Magic number: 7:487:79
[    1.392838] Freeing unused kernel memory: 328k freed
[    1.393659] Time: tsc clocksource has been installed.
[    2.589331] Capability LSM initialized
[    2.622931] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.623093] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.623282] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.623286] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.623692] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.623842] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.624067] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.624072] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.176000] ACPI: Thermal Zone [THM] (31 C)
[    3.180000] Time: hpet clocksource has been installed.
[    3.504000] usbcore: registered new interface driver usbfs
[    3.504000] usbcore: registered new interface driver hub
[    3.504000] usbcore: registered new device driver usb
[    3.504000] USB Universal Host Controller Interface driver v3.0
[    3.504000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    3.504000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.504000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.504000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.504000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bf80
[    3.504000] usb usb1: configuration #1 chosen from 1 choice
[    3.504000] hub 1-0:1.0: USB hub found
[    3.504000] hub 1-0:1.0: 2 ports detected
[    3.540000] SCSI subsystem initialized
[    3.544000] libata version 2.20 loaded.
[    3.584000] ieee1394: Initialized config rom entry `ip1394'
[    3.608000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 20
[    3.608000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.608000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.608000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.608000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000bf60
[    3.608000] usb usb2: configuration #1 chosen from 1 choice
[    3.608000] hub 2-0:1.0: USB hub found
[    3.608000] hub 2-0:1.0: 2 ports detected
[    3.712000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 21
[    3.712000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.712000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.712000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.712000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000bf40
[    3.712000] usb usb3: configuration #1 chosen from 1 choice
[    3.712000] hub 3-0:1.0: USB hub found
[    3.712000] hub 3-0:1.0: 2 ports detected
[    3.816000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 22
[    3.816000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.816000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.816000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.816000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000bf20
[    3.816000] usb usb4: configuration #1 chosen from 1 choice
[    3.816000] hub 4-0:1.0: USB hub found
[    3.816000] hub 4-0:1.0: 2 ports detected
[    3.920000] b44.c:v1.01 (Jun 16, 2006)
[    3.920000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    3.924000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:18:8b:ca:0d:a0
[    3.924000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 18
[    3.984000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.988000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.988000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.988000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[    3.988000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.988000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    3.988000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    3.988000] scsi0 : ata_piix
[    4.152000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.152000] ata1.00: ATA-7: SAMSUNG HM120JI, YF100-15, max UDMA7
[    4.152000] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.160000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    4.160000] ata1.00: configured for UDMA/133
[    4.160000] scsi1 : ata_piix
[    4.480000] ata2.00: ATAPI, max UDMA/33
[    4.644000] ata2.00: configured for UDMA/33
[    4.644000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM120JI  YF10 PQ: 0 ANSI: 5
[    4.644000] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-5540A 102C PQ: 0 ANSI: 5
[    4.644000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.644000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.644000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.644000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.644000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.644000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.644000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80000
[    4.648000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.648000] usb usb5: configuration #1 chosen from 1 choice
[    4.648000] hub 5-0:1.0: USB hub found
[    4.648000] hub 5-0:1.0: 8 ports detected
[    4.760000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.760000] sda: Write Protect is off
[    4.760000] sda: Mode Sense: 00 3a 00 00
[    4.760000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.760000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    4.760000] sda: Write Protect is off
[    4.760000] sda: Mode Sense: 00 3a 00 00
[    4.760000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.760000]  sda:<7>ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00010d9ed61]
[    5.472000]  sda1 sda2 < sda5 >
[    5.504000] sd 0:0:0:0: Attached scsi disk sda
[    5.508000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.508000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.512000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.512000] Uniform CD-ROM driver Revision: 3.20
[    5.512000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.708000] Attempting manual resume
[    5.708000] swsusp: Resume From Partition 8:5
[    5.708000] PM: Checking swsusp image.
[    5.708000] PM: Resume from disk failed.
[    5.760000] kjournald starting.  Commit interval 5 seconds
[    5.760000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.700000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.760000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.880000] iTCO_vendor_support: vendor-support=0
[   17.904000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   17.904000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.904000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.024000] input: PC Speaker as /class/input/input2
[   18.072000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.076000] agpgart: Detected an Intel 945GM Chipset.
[   18.076000] agpgart: Detected 7932K stolen memory.
[   18.092000] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.116000] ieee80211_crypt: registered algorithm 'NULL'
[   18.128000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.128000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.164000] intel_rng: FWH not detected
[   18.308000] NET: Registered protocol family 17
[   18.312000] sdhci: Secure Digital Host Controller Interface driver
[   18.312000] sdhci: Copyright(c) Pierre Ossman
[   18.312000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   18.312000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   18.312000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   18.340000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   18.340000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   18.340000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.340000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   18.340000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   18.568000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04713/0x200000
[   18.608000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   18.636000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   18.636000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.208000] fuse init (API version 7.8)
[   19.332000] lp: driver loaded but no devices found
[   19.388000] Adding 3004112k swap on /dev/disk/by-uuid/d562e92c-b435-4f31-878c-1356bed585c5.  Priority:-1 extents:1 across:3004112k
[   19.544000] EXT3 FS on sda1, internal journal
[   19.932000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   19.932000] b44: eth0: Flow control is off for TX and off for RX.
[   20.228000] ipw3945: Radio Frequency Kill Switch is On:
[   20.228000] Kill switch must be turned off for wireless networking to work.
[   22.368000] NET: Registered protocol family 10
[   22.368000] lo: Disabled Privacy Extensions
[   23.968000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.972000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   23.972000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   23.984000] Using specific hotkey driver
[   24.024000] input: Lid Switch as /class/input/input4
[   24.024000] ACPI: Lid Switch [LID]
[   24.024000] input: Power Button (CM) as /class/input/input5
[   24.024000] ACPI: Power Button (CM) [PBTN]
[   24.024000] input: Sleep Button (CM) as /class/input/input6
[   24.024000] ACPI: Sleep Button (CM) [SBTN]
[   24.100000] ACPI: Battery Slot [BAT0] (battery present)
[   24.124000] ACPI: AC Adapter [AC] (on-line)
[   24.132000] ibm_acpi: ec object not found
[   24.164000] No dock devices found.
[   24.260000] pcc_acpi: loading...
[   29.384000] [drm] Initialized drm 1.1.0 20060810
[   29.384000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.384000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.464000] ppdev: user-space parallel port driver
[   34.472000] apm: BIOS not found.
[   37.280000] Bluetooth: Core ver 2.11
[   37.280000] NET: Registered protocol family 31
[   37.280000] Bluetooth: HCI device and connection manager initialized
[   37.280000] Bluetooth: HCI socket layer initialized
[   37.304000] Bluetooth: L2CAP ver 2.8
[   37.304000] Bluetooth: L2CAP socket layer initialized
[   37.464000] Bluetooth: RFCOMM socket layer initialized
[   37.464000] Bluetooth: RFCOMM TTY layer initialized
[   37.464000] Bluetooth: RFCOMM ver 1.8
[   41.328000] eth0: no IPv6 routers present
[  544.024000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.024000]     Additional sense: Medium not present
[  544.024000] end_request: I/O error, dev sr0, sector 0
[  544.024000] Buffer I/O error on device sr0, logical block 0
[  544.024000] Buffer I/O error on device sr0, logical block 1
[  544.024000] Buffer I/O error on device sr0, logical block 2
[  544.024000] Buffer I/O error on device sr0, logical block 3
[  544.024000] Buffer I/O error on device sr0, logical block 4
[  544.024000] Buffer I/O error on device sr0, logical block 5
[  544.024000] Buffer I/O error on device sr0, logical block 6
[  544.024000] Buffer I/O error on device sr0, logical block 7
[  544.028000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.028000]     Additional sense: Medium not present
[  544.028000] end_request: I/O error, dev sr0, sector 0
[  544.028000] Buffer I/O error on device sr0, logical block 0
[  544.036000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.036000]     Additional sense: Medium not present
[  544.036000] end_request: I/O error, dev sr0, sector 4
[  544.036000] Buffer I/O error on device sr0, logical block 1
[  544.040000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.040000]     Additional sense: Medium not present
[  544.040000] end_request: I/O error, dev sr0, sector 0
[  544.044000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.044000]     Additional sense: Medium not present
[  544.044000] end_request: I/O error, dev sr0, sector 4
[  544.052000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.052000]     Additional sense: Medium not present
[  544.052000] end_request: I/O error, dev sr0, sector 0
[  544.056000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.056000]     Additional sense: Medium not present
[  544.056000] end_request: I/O error, dev sr0, sector 4
[  544.064000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.064000]     Additional sense: Medium not present
[  544.064000] end_request: I/O error, dev sr0, sector 0
[  544.068000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.068000]     Additional sense: Medium not present
[  544.068000] end_request: I/O error, dev sr0, sector 4
[  544.072000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.072000]     Additional sense: Medium not present
[  544.072000] end_request: I/O error, dev sr0, sector 0
[  544.080000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  544.080000]     Additional sense: Medium not present
[  544.080000] end_request: I/O error, dev sr0, sector 4
[  640.424000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.424000]     Additional sense: Medium not present
[  640.424000] end_request: I/O error, dev sr0, sector 0
[  640.424000] printk: 8 messages suppressed.
[  640.424000] Buffer I/O error on device sr0, logical block 0
[  640.424000] Buffer I/O error on device sr0, logical block 1
[  640.424000] Buffer I/O error on device sr0, logical block 2
[  640.424000] Buffer I/O error on device sr0, logical block 3
[  640.424000] Buffer I/O error on device sr0, logical block 4
[  640.424000] Buffer I/O error on device sr0, logical block 5
[  640.424000] Buffer I/O error on device sr0, logical block 6
[  640.424000] Buffer I/O error on device sr0, logical block 7
[  640.428000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.428000]     Additional sense: Medium not present
[  640.428000] end_request: I/O error, dev sr0, sector 0
[  640.428000] Buffer I/O error on device sr0, logical block 0
[  640.432000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.432000]     Additional sense: Medium not present
[  640.432000] end_request: I/O error, dev sr0, sector 4
[  640.432000] Buffer I/O error on device sr0, logical block 1
[  640.440000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.440000]     Additional sense: Medium not present
[  640.440000] end_request: I/O error, dev sr0, sector 0
[  640.444000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.444000]     Additional sense: Medium not present
[  640.444000] end_request: I/O error, dev sr0, sector 4
[  640.452000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.452000]     Additional sense: Medium not present
[  640.452000] end_request: I/O error, dev sr0, sector 0
[  640.456000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.456000]     Additional sense: Medium not present
[  640.456000] end_request: I/O error, dev sr0, sector 4
[  640.464000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.464000]     Additional sense: Medium not present
[  640.464000] end_request: I/O error, dev sr0, sector 0
[  640.468000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.468000]     Additional sense: Medium not present
[  640.468000] end_request: I/O error, dev sr0, sector 4
[  640.476000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.476000]     Additional sense: Medium not present
[  640.476000] end_request: I/O error, dev sr0, sector 0
[  640.480000] sr 1:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  640.480000]     Additional sense: Medium not present
[  640.480000] end_request: I/O error, dev sr0, sector 4

---

### Post by noob12 on 2007-09-21
This is at least part of your problem
```

[ 20.228000] ipw3945: Radio Frequency Kill Switch is On:
[ 20.228000] Kill switch must be turned off for wireless networking to work.

```
There may be more issues, but fix that if you can.

Do you have a slider switch or do you use the FN+F2 keys to enable the wireless?  If you have a slider switch, make sure it is in the ON position.  

Check your BIOS settings for any setting that controls whether wireless is enabled by default at boot.  You still need any hardware switch on.

---

