---
title: "[SOLVED] no wireless after upgrading to hardy on aspire 5630"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by vitalik1982 on 2008-08-04
wireless worked fine on gusty and after upgrading to hurdy it just disappeared.

iwlist
```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Failed to read scan data : Resource temporarily unavailable

```

iwconfig
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw
```
sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:5c:c0:af
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:52:38:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=132.72.151.75 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

```

please HELP, anyone !!

---

### Post by pytheas22 on 2008-08-04
Please do a fresh reboot of your system.  When it's done loading, open a terminal and type:
```

dmesg
```

and please post the output here (it's going to be long but please post it all).

Also, does this by any chance make a difference:
```

sudo rmmod iwl3945
sudo modprobe iwl3945
iwlist scan
```

---

### Post by vitalik1982 on 2008-08-05
it was one of the first things i tried:
```
vitalyb@vitalyb-laptop:~$ sudo rmmod iwl3945
vitalyb@vitalyb-laptop:~$ sudo modprobe iwl3945
vitalyb@vitalyb-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Failed to read scan data : Resource temporarily unavailable


```

dmesg as you asked
```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
[    0.000000]  BIOS-e820: 000000003f680000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6520
[    0.000000] Entering add_active_range(0, 0, 259712) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259712
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259712
[    0.000000] On node 0 totalpages: 259712
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30099 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F64F0 checksum 0
[    0.000000] ACPI: RSDP 000F64F0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 3F686052, 0048 (r1 PTLTD  Capell00  6040000  LTP        0)
[    0.000000] ACPI: FACP 3F68CE20, 0074 (r1 Acer   Grape     6040000 LOHR       5A)
[    0.000000] ACPI: DSDT 3F68708A, 5D96 (r1 Acer   CALISTGA  6040000 INTL 20050228)
[    0.000000] ACPI: FACS 3F68DFC0, 0040
[    0.000000] ACPI: APIC 3F68CE94, 0068 (r1 Acer   Grape     6040000 LOHR       5A)
[    0.000000] ACPI: HPET 3F68CEFC, 0038 (r1 Acer   Grape     6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 3F68CF34, 003C (r1 Acer   Grape     6040000 LOHR       5A)
[    0.000000] ACPI: APIC 3F68CF70, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3F68CFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 3F686626, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3F686580, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3F68609A, 04E6 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
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
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257683
[    0.000000] Kernel command line: root=UUID=3c7ee219-159e-48c0-92b5-3a41bcf4b38e ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1662.560 MHz processor.
[   11.729512] Console: colour VGA+ 80x25
[   11.729517] console [tty0] enabled
[   11.729835] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.730259] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.765964] Memory: 1017700k/1038848k available (2177k kernel code, 20424k reserved, 1006k data, 368k init, 121344k highmem)
[   11.765976] virtual kernel memory layout:
[   11.765978]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   11.765980]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.765981]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.765983]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.765985]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   11.765987]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   11.765988]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   11.765993] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.766037] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.766189] hpet clockevent registered
[   11.846076] Calibrating delay using timer specific routine.. 3329.73 BogoMIPS (lpj=6659463)
[   11.846104] Security Framework initialized
[   11.846110] SELinux:  Disabled at boot.
[   11.846126] AppArmor: AppArmor initialized
[   11.846132] Failure registering capabilities with primary security module.
[   11.846145] Mount-cache hash table entries: 512
[   11.846305] Initializing cgroup subsys ns
[   11.846311] Initializing cgroup subsys cpuacct
[   11.846326] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   11.846338] monitor/mwait feature present.
[   11.846340] using mwait in idle threads.
[   11.846346] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.846350] CPU: L2 cache: 2048K
[   11.846353] CPU: Physical Processor ID: 0
[   11.846356] CPU: Processor Core ID: 0
[   11.846359] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   11.846372] Compat vDSO mapped to ffffe000.
[   11.846391] Checking 'hlt' instruction... OK.
[   11.862677] SMP alternatives: switching to UP code
[   11.865339] Early unpacking initramfs... done
[   12.434822] ACPI: Core revision 20070126
[   12.434891] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.460242] CPU0: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   12.460266] SMP alternatives: switching to SMP code
[   12.461433] Booting processor 1/1 eip 3000
[   12.471805] Initializing CPU#1
[   12.548988] Calibrating delay using timer specific routine.. 3325.09 BogoMIPS (lpj=6650182)
[   12.548999] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   12.549007] monitor/mwait feature present.
[   12.549012] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.549015] CPU: L2 cache: 2048K
[   12.549018] CPU: Physical Processor ID: 0
[   12.549021] CPU: Processor Core ID: 1
[   12.549023] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   12.549846] CPU1: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   12.549879] Total of 2 processors activated (6654.82 BogoMIPS).
[   12.550089] ENABLING IO-APIC IRQs
[   12.550299] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.696925] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   12.716921] Brought up 2 CPUs
[   12.716955] CPU0 attaching sched-domain:
[   12.716959]  domain 0: span 03
[   12.716962]   groups: 01 02
[   12.716967] CPU1 attaching sched-domain:
[   12.716969]  domain 0: span 03
[   12.716972]   groups: 02 01
[   12.717348] net_namespace: 64 bytes
[   12.717363] Booting paravirtualized kernel on bare hardware
[   12.718109] Time: 12:06:44  Date: 08/05/08
[   12.718152] NET: Registered protocol family 16
[   12.718489] EISA bus registered
[   12.718496] ACPI: bus type pci registered
[   12.718762] PCI: PCI BIOS revision 2.10 entry at 0xfd673, last bus=7
[   12.718766] PCI: Using configuration type 1
[   12.718793] Setting up standard PCI resources
[   12.722722] ACPI: EC: Look up EC in DSDT
[   12.726802] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   12.726806] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   12.727634] ACPI: Interpreter enabled
[   12.727639] ACPI: (supports S0 S3 S4 S5)
[   12.727662] ACPI: Using IOAPIC for interrupt routing
[   12.733421] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   12.774839] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   12.774843] ACPI: EC: driver started in interrupt mode
[   12.774917] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.776065] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   12.776072] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   12.777743] PCI: Transparent bridge - 0000:00:1e.0
[   12.777882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.778371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   12.778583] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   12.778792] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   12.779000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   12.779228] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   12.784165] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 5 *6 10 12 14 15)
[   12.784336] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 5 6 *11 12 14 15)
[   12.784502] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 5 6 10 12 14 15) *11
[   12.784673] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 5 6 11 12 14 15) *10
[   12.784839] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 5 6 10 12 14 15) *0, disabled.
[   12.785004] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 5 6 11 12 14 15) *10
[   12.785168] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 5 6 *10 12 14 15)
[   12.785336] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *5 6 11 12 14 15)
[   12.785586] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.785641] pnp: PnP ACPI init
[   12.785654] ACPI: bus type pnp registered
[   12.809961] pnp: PnP ACPI: found 10 devices
[   12.809965] ACPI: ACPI bus type pnp unregistered
[   12.809970] PnPBIOS: Disabled by ACPI PNP
[   12.810361] PCI: Using ACPI for IRQ routing
[   12.810366] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.810371] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   12.810375] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   12.872679] NET: Registered protocol family 8
[   12.872683] NET: Registered protocol family 20
[   12.872740] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   12.872748] hpet0: 3 64-bit timers, 14318180 Hz
[   12.873800] AppArmor: AppArmor Filesystem Enabled
[   12.876491] Time: tsc clocksource has been installed.
[   12.876509] Switched to high resolution mode on CPU 0
[   12.876669] Switched to high resolution mode on CPU 1
[   12.889480] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   12.889485] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   12.889490] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   12.889495] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   12.889500] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   12.889505] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   12.889518] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   12.889529] system 00:06: ioport range 0x800-0x80f has been reserved
[   12.889534] system 00:06: ioport range 0x1000-0x107f has been reserved
[   12.889538] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   12.889542] system 00:06: ioport range 0x1640-0x164f has been reserved
[   12.889547] system 00:06: ioport range 0xfe00-0xfefe has been reserved
[   12.889551] system 00:06: ioport range 0xff2c-0xff2f has been reserved
[   12.920276] PCI: Bridge: 0000:00:1c.0
[   12.920279]   IO window: disabled.
[   12.920286]   MEM window: disabled.
[   12.920292]   PREFETCH window: disabled.
[   12.920300] PCI: Bridge: 0000:00:1c.1
[   12.920302]   IO window: disabled.
[   12.920310]   MEM window: disabled.
[   12.920315]   PREFETCH window: disabled.
[   12.920323] PCI: Bridge: 0000:00:1c.2
[   12.920325]   IO window: disabled.
[   12.920333]   MEM window: disabled.
[   12.920338]   PREFETCH window: disabled.
[   12.920346] PCI: Bridge: 0000:00:1c.3
[   12.920348]   IO window: disabled.
[   12.920356]   MEM window: d0100000-d01fffff
[   12.920362]   PREFETCH window: disabled.
[   12.920382] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   12.920385]   IO window: 00001400-000014ff
[   12.920392]   IO window: 00001c00-00001cff
[   12.920399]   PREFETCH window: 50000000-53ffffff
[   12.920406]   MEM window: 54000000-57ffffff
[   12.920413] PCI: Bridge: 0000:00:1e.0
[   12.920415]   IO window: disabled.
[   12.920423]   MEM window: d0000000-d00fffff
[   12.920429]   PREFETCH window: disabled.
[   12.920470] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   12.920482] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.920515] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   12.920524] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.920556] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   12.920564] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.920596] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   12.920605] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   12.920620] PCI: Enabling device 0000:00:1e.0 (0004 -> 0006)
[   12.920629] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.920650] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 17
[   12.920671] NET: Registered protocol family 2
[   12.957404] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.957747] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.958442] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.958768] TCP: Hash tables configured (established 131072 bind 65536)
[   12.958772] TCP reno registered
[   12.969500] checking if image is initramfs... it is
[   14.091744] Freeing initrd memory: 7317k freed
[   14.091968] Simple Boot Flag at 0x36 set to 0x1
[   14.093059] audit: initializing netlink socket (disabled)
[   14.093077] audit(1217938005.188:1): initialized
[   14.093367] highmem bounce pool size: 64 pages
[   14.096858] VFS: Disk quotas dquot_6.5.1
[   14.096983] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   14.097197] io scheduler noop registered
[   14.097201] io scheduler anticipatory registered
[   14.097204] io scheduler deadline registered
[   14.097222] io scheduler cfq registered (default)
[   14.097237] Boot video device is 0000:00:02.0
[   14.097530] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.097607] assign_interrupt_mode Found MSI capability
[   14.097673] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.097734] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.097879] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.097955] assign_interrupt_mode Found MSI capability
[   14.098015] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.098072] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.098219] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.098295] assign_interrupt_mode Found MSI capability
[   14.098355] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.098415] Allocate Port Service[0000:00:1c.2:pcie02]
[   14.098563] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.098646] assign_interrupt_mode Found MSI capability
[   14.098706] Allocate Port Service[0000:00:1c.3:pcie00]
[   14.098769] Allocate Port Service[0000:00:1c.3:pcie02]
[   14.099202] isapnp: Scanning for PnP cards...
[   14.453377] isapnp: No Plug & Play device found
[   14.497804] Real Time Clock Driver v1.12ac
[   14.498160] hpet_resources: 0xfed00000 is busy
[   14.498201] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.500216] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.500327] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.500497] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[   14.500909] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.500996] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.501004] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.501008] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.501012] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.501016] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.518286] mice: PS/2 mouse device common for all mice
[   14.518480] EISA: Probing bus 0 at eisa.0
[   14.518489] Cannot allocate resource for EISA slot 1
[   14.518528] EISA: Detected 0 cards.
[   14.518532] cpuidle: using governor ladder
[   14.518535] cpuidle: using governor menu
[   14.518657] NET: Registered protocol family 1
[   14.518699] Using IPI No-Shortcut mode
[   14.518741] registered taskstats version 1
[   14.518909]   Magic number: 4:722:126
[   14.519005]   hash matches device device:01
[   14.519011] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.519014] EDD information not available.
[   14.519248] Freeing unused kernel memory: 368k freed
[   14.520971] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.884274] fuse init (API version 7.9)
[   15.924034] ACPI: SSDT 3F686DCC, 01F6 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   15.924412] ACPI: SSDT 3F686885, 04C2 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   15.927164] Monitor-Mwait will be used to enter C-1 state
[   15.927169] Monitor-Mwait will be used to enter C-2 state
[   15.927172] Monitor-Mwait will be used to enter C-3 state
[   15.927384] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.927393] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.927787] ACPI: SSDT 3F686FC2, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050228)
[   15.928141] ACPI: SSDT 3F686D47, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[   15.929438] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   15.929448] ACPI: Processor [CPU1] (supports 8 throttling states)
[   15.933070] ACPI: Thermal Zone [TZ00] (51 C)
[   15.935008] ACPI: Thermal Zone [TZ01] (51 C)
[   16.586830] usbcore: registered new interface driver usbfs
[   16.586870] usbcore: registered new interface driver hub
[   16.608919] usbcore: registered new device driver usb
[   16.633176] SCSI subsystem initialized
[   16.650674] USB Universal Host Controller Interface driver v3.0
[   16.650750] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   16.650765] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.650771] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.651071] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   16.651110] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[   16.651317] usb usb1: configuration #1 chosen from 1 choice
[   16.651358] hub 1-0:1.0: USB hub found
[   16.651366] hub 1-0:1.0: 2 ports detected
[   16.679935] libata version 3.00 loaded.
[   16.754608] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   16.754625] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.754632] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.754676] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   16.754715] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[   16.754897] usb usb2: configuration #1 chosen from 1 choice
[   16.754936] hub 2-0:1.0: USB hub found
[   16.754944] hub 2-0:1.0: 2 ports detected
[   16.858492] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.858510] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.858516] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.858554] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   16.858594] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   16.858786] usb usb3: configuration #1 chosen from 1 choice
[   16.858826] hub 3-0:1.0: USB hub found
[   16.858834] hub 3-0:1.0: 2 ports detected
[   16.962282] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   16.962298] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   16.962305] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   16.962345] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   16.962383] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   16.962562] usb usb4: configuration #1 chosen from 1 choice
[   16.962602] hub 4-0:1.0: USB hub found
[   16.962610] hub 4-0:1.0: 2 ports detected
[   17.066311] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   17.066331] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.066336] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.066375] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   17.070305] ehci_hcd 0000:00:1d.7: debug port 1
[   17.070314] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.070323] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0544000
[   17.098961] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   17.109932] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.110116] usb usb5: configuration #1 chosen from 1 choice
[   17.110158] hub 5-0:1.0: USB hub found
[   17.110167] hub 5-0:1.0: 8 ports detected
[   17.215091] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   17.215140] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   17.215161] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   17.224046] ata_piix 0000:00:1f.1: version 2.12
[   17.224066] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   17.224109] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   17.226402] scsi0 : ata_piix
[   17.226556] scsi1 : ata_piix
[   17.227472] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   17.227477] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   17.454406] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   17.555123] ata1.00: ATA-6: ST9120822A, 3.ALC, max UDMA/100
[   17.555129] ata1.00: 234441648 sectors, multi 16: LBA48
[   17.555174] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33
[   17.571736] ata1.00: configured for UDMA/100
[   17.626348] usb 5-4: configuration #1 chosen from 1 choice
[   17.741431] ata1.01: configured for UDMA/33
[   17.741534] ata2: port disabled. ignoring.
[   17.741809] scsi 0:0:0:0: Direct-Access     ATA      ST9120822A       3.AL PQ: 0 ANSI: 5
[   17.745486] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  PP02 PQ: 0 ANSI: 5
[   17.745868] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 21 (level, low) -> IRQ 21
[   17.745889] PCI: Setting latency timer of device 0000:06:01.0 to 64
[   17.756429] Driver 'sd' needs updating - please use bus_type methods
[   17.756545] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.756566] sd 0:0:0:0: [sda] Write Protect is off
[   17.756570] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.756598] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.756671] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.756689] sd 0:0:0:0: [sda] Write Protect is off
[   17.756693] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.756720] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.756725]  sda:<6>ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   17.762445] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   17.762456] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   17.762549] Driver 'sr' needs updating - please use bus_type methods
[   17.801959] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[   17.802002] b44.c:v2.0
[   17.820843]  sda1 sda2 <<6>eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d4:52:38:cb
[   17.841435]  sda5 sda6 >
[   17.850698] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.857414] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.857446] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   17.869589] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   17.869596] Uniform CD-ROM driver Revision: 3.20
[   17.869676] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   18.312679] Attempting manual resume
[   18.312684] swsusp: Resume From Partition 8:5
[   18.312687] PM: Checking swsusp image.
[   18.312924] PM: Resume from disk failed.
[   18.335887] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.335893] EXT3-fs: write access will be enabled during recovery.
[   18.395964] Clocksource tsc unstable (delta = -414193671 ns)
[   18.404168] Time: hpet clocksource has been installed.
[   20.824056] kjournald starting.  Commit interval 5 seconds
[   20.824100] EXT3-fs: recovery complete.
[   20.824550] EXT3-fs: mounted filesystem with ordered data mode.
[   33.108264] Linux agpgart interface v0.102
[   33.415697] intel_rng: FWH not detected
[   33.447680] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.511631] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.559084] ACPI: WMI-Acer: Mapper loaded
[   33.623490] agpgart: Detected an Intel 945GM Chipset.
[   33.625179] agpgart: Detected 7932K stolen memory.
[   33.642725] agpgart: AGP aperture is 256M @ 0xc0000000
[   33.711431] input: Power Button (FF) as /devices/virtual/input/input2
[   33.746181] ACPI: Power Button (FF) [PWRF]
[   33.746280] input: Lid Switch as /devices/virtual/input/input3
[   33.762238] ACPI: Lid Switch [LID]
[   33.762333] input: Sleep Button (CM) as /devices/virtual/input/input4
[   33.810075] ACPI: Sleep Button (CM) [SLPB]
[   33.810170] input: Power Button (CM) as /devices/virtual/input/input5
[   33.857992] ACPI: Power Button (CM) [PWRB]
[   33.878413] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   33.878423] acer_acpi: Detected Acer WMID interface
[   33.882810] acer_acpi: Setting keyboard quirk to enable multimedia keys
[   33.882948] Registered led device: acer_acpi:mail
[   34.007002] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   34.126630] Yenta: CardBus bridge found at 0000:06:04.0 [1025:0090]
[   34.126661] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.126665] Yenta: Routing CardBus interrupts to PCI
[   34.126673] Yenta TI: socket 0000:06:04.0, mfunc 0x90501212, devctl 0x44
[   34.302365] iTCO_vendor_support: vendor-support=0
[   34.359092] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   34.359099] Socket status: 30000006
[   34.359103] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   34.359111] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd00fffff
[   34.585490] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7
[   34.617803] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.618122] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   34.669708] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   34.673971] ACPI: AC Adapter [ACAD] (on-line)
[   34.693681] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.753639] sdhci: Secure Digital Host Controller Interface driver
[   34.753644] sdhci: Copyright(c) Pierre Ossman
[   34.753704] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   34.753729] PCI: Enabling device 0000:06:04.2 (0000 -> 0002)
[   34.753739] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 16
[   34.753830] mmc0: SDHCI at 0xd0003400 irq 16 PIO
[   34.753845] sdhci: SDHCI controller found at 0000:06:04.4 [1524:0551] (rev 1)
[   34.753867] PCI: Enabling device 0000:06:04.4 (0000 -> 0002)
[   34.753874] ACPI: PCI Interrupt 0000:06:04.4[B] -> GSI 17 (level, low) -> IRQ 16
[   34.753927] mmc1: SDHCI at 0xd0003100 irq 16 PIO
[   34.958343] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   34.987830] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   35.042381] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   35.042436] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   35.179996] ACPI: Battery Slot [BAT1] (battery present)
[   35.568295] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   35.568302] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.568436] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   35.568455] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   35.568484] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   35.715943] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   35.875295] Linux video capture interface: v2.00
[   36.014208] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321)
[   36.021139] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[   36.162122] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   36.162164] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   36.243589] usbcore: registered new interface driver gspca
[   36.243597] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   37.287789] udev: renamed network interface wlan0 to eth1
[   37.504232] cs: IO port probe 0x100-0x3af: clean.
[   37.506362] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   37.507249] cs: IO port probe 0x820-0x8ff: clean.
[   37.507980] cs: IO port probe 0xc00-0xcf7: clean.
[   37.508965] cs: IO port probe 0xa00-0xaff: clean.
[   37.774240] lp: driver loaded but no devices found
[   37.960984] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   38.807048] EXT3 FS on sda6, internal journal
[  131.595664] ip_tables: (C) 2000-2006 Netfilter Core Team
[  132.864394] NET: Registered protocol family 10
[  132.864794] lo: Disabled Privacy Extensions
[  133.075428] No dock devices found.
[  134.917097] ppdev: user-space parallel port driver
[  135.215652] audit(1217927328.023:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6945 profile="/usr/sbin/cupsd" namespace="default"
[  135.287975] apm: BIOS not found.
[  139.245122] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  139.338968] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  139.339116] PM: Writing back config space on device 0000:05:00.0 at offset 1 (was 100102, writing 100106)
[  139.426349] Bluetooth: Core ver 2.11
[  139.426738] NET: Registered protocol family 31
[  139.426743] Bluetooth: HCI device and connection manager initialized
[  139.426749] Bluetooth: HCI socket layer initialized
[  139.556472] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[  139.559928] Bluetooth: L2CAP ver 2.9
[  139.559934] Bluetooth: L2CAP socket layer initialized
[  139.560432] Registered led device: iwl-phy0:RX
[  139.560468] Registered led device: iwl-phy0:TX
[  139.569837] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  139.815039] Bluetooth: RFCOMM socket layer initialized
[  139.815056] Bluetooth: RFCOMM TTY layer initialized
[  139.815059] Bluetooth: RFCOMM ver 1.8
[  140.709718] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  140.709799] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4414 ser 0x0000004B
[  141.703340] iwl3945: Can't stop Rx DMA.
[  141.862335] Registered led device: iwl-phy0:RX
[  141.862373] Registered led device: iwl-phy0:TX
[  142.731927] b44: eth0: Link is up at 100 Mbps, full duplex.
[  142.731934] b44: eth0: Flow control is off for TX and off for RX.
[  142.735470] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  143.375020] [drm] Initialized drm 1.1.0 20060810
[  143.379639] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  143.379654] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  143.379754] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  144.464774] NET: Registered protocol family 17
[  170.047837] CPU0 attaching NULL sched-domain.
[  170.047843] CPU1 attaching NULL sched-domain.
[  170.075708] CPU0 attaching sched-domain:
[  170.075714]  domain 0: span 03
[  170.075716]   groups: 01 02
[  170.075719] CPU1 attaching sched-domain:
[  170.075721]  domain 0: span 03
[  170.075723]   groups: 02 01

```

---

### Post by pytheas22 on 2008-08-05
Thanks for the information.  Your problem looks related to [this]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.24/+bug/226134"), [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/185470") and [this]("http://ubuntuforums.org/showthread.php?t=820297").


First of all, does the wireless work again if you run these commands:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

If that doesn't work, it may help to enable the Hardy-backports repository by going to System>Administration>Software Sources, clicking on the Updates tab and checking the box for "Unsupported Updates."  Then reload the package manager and apply all Ubuntu system updates.  There may be a fix if you download the updates in that repository.

If neither of the above helps, you will probably have to compile the latest wifi drivers from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download).

Please let me know if either of the first two fixes works.

---

### Post by vitalik1982 on 2008-08-05
the second option didn't help, i tried it while i was searching for a solution but disabling the hw scan helped, thanks!!!!

---

### Post by pytheas22 on 2008-08-05
Alright, I'm glad the hw_scan stuff helped.

You should probably disable the Hardy Backports repository now, since you don't need it.

Also, you will have to type that command each time you reboot your computer to get the wireless to work.  If you want to fix it so that the commands will be entered automatically every time, let me know.

---

### Post by vitalik1982 on 2008-08-05
> **pytheas22 said:**
> 
Also, you will have to type that command each time you reboot your computer to get the wireless to work.  If you want to fix it so that the commands will be entered automatically every time, let me know.

how do i do that?

---

### Post by pytheas22 on 2008-08-06
Write a startup script.  Follow these directions:

1. type:
```

sudo gedit /etc/init.d/wireless-fix.sh
```

A file will open.  Add to it these lines:
```

#!/bin/bash
#this script fixes a bug with the iwl3945 wireless driver; see http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5531540 for details

rmmod -f iwl3945
modprobe iwl3945 disable_hw_scan=1
```

Then save and close the file.

2. now we have to make the script executable and tell the system to run it at boot:
```

sudo -s
cd /etc/init.d
chmod +x wireless-fix.sh
update-rc.d wireless-fix.sh defaults
```

Now the fix should be applied automatically each time the system boots.  Let me know if you run into any trouble.

---

