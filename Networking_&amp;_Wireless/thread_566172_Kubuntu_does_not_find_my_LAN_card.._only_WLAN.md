---
title: "Kubuntu does not find my LAN card.. only WLAN"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by fahim on 2007-10-03
Hello,

I have a laptop with wifi and lan. I am wondering why kubuntu does find my wifi card, but does not fine my lan card. There is even no device for the lan. Does anybody know this problem?

One time I could see my lan card in the knetworkmanager. but really only once!

Thank you very much

---

### Post by dresnu on 2007-10-03
Don't know what might be, but just an advice. Try this [http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/") instead of knetworkmanager.
I had many problems with knm, wicd is five steps above it, muuch better!

---

### Post by fahim on 2007-10-03
Do you think in depens on knetworkmanager? Because the system can not find the ethernet device... Do you know if there is a vpn support for wicid (with an addon perhaps?!)

---

### Post by dresnu on 2007-10-03
> **fahim said:**
> Do you know if there is a vpn support for wicid

Hmmm, from what I know not yet.

If you go to Kmenu>System Settings>Network Settings can you see your wired ethernet adapter? And is it enabled?

---

### Post by fahim on 2007-10-03
Yes my wired ethernet (eth0) is listet, activated and works great all the time. Only my lan ethernet adapter ist not listed. Thats really serious ?!

---

### Post by dresnu on 2007-10-03
Uhm, wait. What do you mean by lan? Do you mean that your wired adapter (eth0) is seen and working but you get no connection when connecting a cable to it?
Is it a router you are trying to connect to?

---

### Post by fahim on 2007-10-03
No. my wireless card is eth0 an works great with knetworkmanager. Only my wired card will not be found in kubuntu... thats why I am wondering?! I can't find any device of the wired card...

---

### Post by noob12 on 2007-10-03
Can you please post the output of these commands?

Thanks

```

lspci -nn

sudo lshw -C network

cat /etc/iftab

dmesg

```

---

### Post by fahim on 2007-10-03
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b4)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 09)
15:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 18)

```

```

 *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: iomemory:ee000000-ee01ffff ioport:2000-201f irq:20
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:de:ba:4c:1f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:edf00000-edf00fff irq:21

```

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:18:de:ba:4c:1f arp 1

```

The following is dmesg:
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007f5d0000 end: 000000007f6d0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007f6d0000 size: 000000000000f000 end: 000000007f6df000 type: 3
[    0.000000] copy_e820_map() start: 000000007f6df000 size: 0000000000021000 end: 000000007f700000 type: 4
[    0.000000] copy_e820_map() start: 000000007f700000 size: 0000000000900000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000800000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
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
[    0.000000] found SMP MP-table at 000f67f0
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
[    0.000000] ACPI: RSDP (v002 LENOVO                                ) @ 0x000f67c0
[    0.000000] ACPI: XSDT (v001 LENOVO TP-7J    0x00001100  LTP 0x00000000) @ 0x7f6d1259
[    0.000000] ACPI: FADT (v003 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6d1300
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7J    0x00001100 MSFT 0x0100000e) @ 0x7f6d14b4
[    0.000000] ACPI: ECDT (v001 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6deb8e
[    0.000000] ACPI: TCPA (v002 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6debe0
[    0.000000] ACPI: MADT (v001 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6dec12
[    0.000000] ACPI: MCFG (v001 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6dec7a
[    0.000000] ACPI: HPET (v001 LENOVO TP-7J    0x00001100 LNVO 0x00000001) @ 0x7f6decb6
[    0.000000] ACPI: SLIC (v001 LENOVO TP-7J    0x00001100  LTP 0x00000000) @ 0x7f6dee62
[    0.000000] ACPI: BOOT (v001 LENOVO TP-7J    0x00001100  LTP 0x00000001) @ 0x7f6defd8
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7J    0x00001100 INTL 0x20050513) @ 0x7f6f2645
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7J    0x00001100 INTL 0x20050513) @ 0x7f6f28a4
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7J    0x00001100 INTL 0x20050513) @ 0x7f6f294a
[    0.000000] ACPI: SSDT (v001 LENOVO TP-7J    0x00001100 INTL 0x20050513) @ 0x7f6f2e41
[    0.000000] ACPI: DSDT (v001 LENOVO TP-7J    0x00001100 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
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
[    0.000000] Detected 1828.884 MHz processor.
[   14.204599] Built 1 zonelists.  Total pages: 517859
[   14.204602] Kernel command line: root=UUID=aef4c3b4-7f25-4d40-87d3-df47ed7be7ee ro quiet splash locale=de_DE
[   14.204757] mapped APIC to ffffd000 (fee00000)
[   14.204760] mapped IOAPIC to ffffc000 (fec00000)
[   14.204763] Enabling fast FPU save and restore... done.
[   14.204765] Enabling unmasked SIMD FPU exception support... done.
[   14.204771] Initializing CPU#0
[   14.204842] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.206416] Console: colour VGA+ 80x25
[   14.206666] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.207005] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.301941] Memory: 2058840k/2087744k available (1993k kernel code, 27652k reserved, 900k data, 328k init, 1170240k highmem)
[   14.301951] virtual kernel memory layout:
[   14.301952]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.301953]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.301954]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.301956]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.301957]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   14.301958]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   14.301959]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   14.301963] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.302127] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.302133] hpet0: 3 64-bit timers, 14318180 Hz
[   14.303390] Using HPET for base-timer
[   14.381995] Calibrating delay using timer specific routine.. 3661.50 BogoMIPS (lpj=7323014)
[   14.382038] Security Framework v1.0.0 initialized
[   14.382045] SELinux:  Disabled at boot.
[   14.382060] Mount-cache hash table entries: 512
[   14.382190] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   14.382198] monitor/mwait feature present.
[   14.382200] using mwait in idle threads.
[   14.382204] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.382206] CPU: L2 cache: 2048K
[   14.382208] CPU: Physical Processor ID: 0
[   14.382210] CPU: Processor Core ID: 0
[   14.382212] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.382221] Compat vDSO mapped to ffffe000.
[   14.382225] Remapping vsyscall page to ffffe000
[   14.382236] Checking 'hlt' instruction... OK.
[   14.398076] SMP alternatives: switching to UP code
[   14.398430] Early unpacking initramfs... done
[   14.701742] ACPI: Core revision 20060707
[   14.701958] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.825758] CPU0: Intel(R) Core(TM) Duo CPU      L2500  @ 1.83GHz stepping 0c
[   14.825778] SMP alternatives: switching to SMP code
[   14.825887] Booting processor 1/1 eip 3000
[   14.836574] Initializing CPU#1
[   14.913383] Calibrating delay using timer specific routine.. 3657.61 BogoMIPS (lpj=7315231)
[   14.913389] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000
[   14.913394] monitor/mwait feature present.
[   14.913398] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.913399] CPU: L2 cache: 2048K
[   14.913402] CPU: Physical Processor ID: 0
[   14.913403] CPU: Processor Core ID: 1
[   14.913405] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000
[   14.913551] CPU1: Intel(R) Core(TM) Duo CPU      L2500  @ 1.83GHz stepping 0c
[   14.913575] Total of 2 processors activated (7319.12 BogoMIPS).
[   14.913771] ENABLING IO-APIC IRQs
[   14.913975] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.060847] checking TSC synchronization across 2 CPUs:
[    0.000001] CPU#0 had -142 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 142 usecs TSC skew, fixed it up.
[    0.003997] Brought up 2 CPUs
[    0.152288] migration_cost=74
[    0.152551] Booting paravirtualized kernel on bare hardware
[    0.152651] Time: 23:43:17  Date: 09/02/107
[    0.152679] NET: Registered protocol family 16
[    0.152762] EISA bus registered
[    0.152769] ACPI: bus type pci registered
[    0.152892] PCI: PCI BIOS revision 2.10 entry at 0xfd82b, last bus=24
[    0.152894] PCI: Using configuration type 1
[    0.152895] Setting up standard PCI resources
[    0.164388] ACPI: Interpreter enabled
[    0.164391] ACPI: Using IOAPIC for interrupt routing
[    0.165210] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.165799] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.166386] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.166973] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.167561] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.168171] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.168757] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.169341] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.169721] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.169726] PCI: Probing PCI hardware (bus 00)
[    0.170991] Boot video device is 0000:00:02.0
[    0.171633] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.171637] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.172892] PCI: Transparent bridge - 0000:00:1e.0
[    0.173030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.177880] ACPI: Power Resource [PUBS] (on)
[    0.179572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.179765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.179942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.180158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.180367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.181945] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.181953] pnp: PnP ACPI init
[    0.186452] pnp: PnP ACPI: found 13 devices
[    0.186456] PnPBIOS: Disabled by ACPI PNP
[    0.186497] PCI: Using ACPI for IRQ routing
[    0.186500] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.248998] NET: Registered protocol family 8
[    0.249000] NET: Registered protocol family 20
[    0.249997] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.250001] PCI: Bridge: 0000:00:1c.0
[    0.250004]   IO window: 2000-2fff
[    0.250010]   MEM window: ee000000-ee0fffff
[    0.250014]   PREFETCH window: disabled.
[    0.250020] PCI: Bridge: 0000:00:1c.1
[    0.250023]   IO window: 3000-4fff
[    0.250029]   MEM window: ec000000-edffffff
[    0.250034]   PREFETCH window: e4000000-e40fffff
[    0.250039] PCI: Bridge: 0000:00:1c.2
[    0.250042]   IO window: 5000-6fff
[    0.250048]   MEM window: e8000000-e9ffffff
[    0.250053]   PREFETCH window: e4100000-e41fffff
[    0.250058] PCI: Bridge: 0000:00:1c.3
[    0.250061]   IO window: 7000-8fff
[    0.250067]   MEM window: ea000000-ebffffff
[    0.250072]   PREFETCH window: e4200000-e42fffff
[    0.250081] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[    0.250083]   IO window: 00009000-000090ff
[    0.250088]   IO window: 00009400-000094ff
[    0.250092]   PREFETCH window: e0000000-e3ffffff
[    0.250097]   MEM window: 88000000-8bffffff
[    0.250101] PCI: Bridge: 0000:00:1e.0
[    0.250104]   IO window: 9000-cfff
[    0.250110]   MEM window: e4300000-e7ffffff
[    0.250115]   PREFETCH window: e0000000-e3ffffff
[    0.250143] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 16
[    0.250149] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.250172] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 17
[    0.250178] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.250201] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 18
[    0.250207] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.250229] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 19
[    0.250235] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.250246] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[    0.250252] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.250268] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    0.250274] PCI: Setting latency timer of device 0000:15:00.0 to 64
[    0.250301] NET: Registered protocol family 2
[    0.303527] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.303629] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.304312] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.304661] TCP: Hash tables configured (established 131072 bind 65536)
[    0.304664] TCP reno registered
[    0.319577] checking if image is initramfs... it is
[    0.919307] Freeing initrd memory: 6779k freed
[    0.919474] Simple Boot Flag at 0x35 set to 0x1
[    0.919911] audit: initializing netlink socket (disabled)
[    0.919928] audit(1191368597.644:1): initialized
[    0.920020] highmem bounce pool size: 64 pages
[    0.920104] VFS: Disk quotas dquot_6.5.1
[    0.920123] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.920171] io scheduler noop registered
[    0.920173] io scheduler anticipatory registered
[    0.920176] io scheduler deadline registered
[    0.920187] io scheduler cfq registered (default)
[    0.920436] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.920492] assign_interrupt_mode Found MSI capability
[    0.920495] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.920526] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.920644] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.920701] assign_interrupt_mode Found MSI capability
[    0.920704] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.920732] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.920846] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.920900] assign_interrupt_mode Found MSI capability
[    0.920903] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.920932] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.921048] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.921103] assign_interrupt_mode Found MSI capability
[    0.921105] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.921136] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.921311] isapnp: Scanning for PnP cards...
[    1.274719] isapnp: No Plug & Play device found
[    1.296716] Real Time Clock Driver v1.12ac
[    1.296770] hpet_resources: 0xfed00000 is busy
[    1.296796] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.297009] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[    1.297624] 00:0b: ttyS0 at I/O 0x200 (irq = 5) is a NS16550A
[    1.297837] mice: PS/2 mouse device common for all mice
[    1.298328] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.298539] input: Macintosh mouse button emulation as /class/input/input0
[    1.298571] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.298574] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.298856] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.310921] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.310925] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.311035] EISA: Probing bus 0 at eisa.0
[    1.311042] Cannot allocate resource for EISA slot 1
[    1.311046] Cannot allocate resource for EISA slot 2
[    1.311048] Cannot allocate resource for EISA slot 3
[    1.311050] Cannot allocate resource for EISA slot 4
[    1.311053] Cannot allocate resource for EISA slot 5
[    1.311055] Cannot allocate resource for EISA slot 6
[    1.311057] Cannot allocate resource for EISA slot 7
[    1.311059] Cannot allocate resource for EISA slot 8
[    1.311061] EISA: Detected 0 cards.
[    1.341107] TCP cubic registered
[    1.341116] NET: Registered protocol family 1
[    1.341136] Starting balanced_irq
[    1.341142] Using IPI No-Shortcut mode
[    1.341247] ACPI: (supports S0 S3 S4 S5)
[    1.341294]   Magic number: 11:299:756
[    1.341541] Freeing unused kernel memory: 328k freed
[    1.341737] Time: tsc clocksource has been installed.
[    1.344686] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.541293] Capability LSM initialized
[    2.573062] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.573432] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.574323] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.574328] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.574879] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.575147] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.576073] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.576079] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.120000] ACPI: Thermal Zone [THM0] (52 C)
[    3.120000] ACPI: Thermal Zone [THM1] (51 C)
[    3.128000] Time: hpet clocksource has been installed.
[    3.464000] usbcore: registered new interface driver usbfs
[    3.464000] usbcore: registered new interface driver hub
[    3.464000] usbcore: registered new device driver usb
[    3.464000] USB Universal Host Controller Interface driver v3.0
[    3.464000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.464000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.464000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.464000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.464000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001820
[    3.464000] usb usb1: configuration #1 chosen from 1 choice
[    3.464000] hub 1-0:1.0: USB hub found
[    3.464000] hub 1-0:1.0: 2 ports detected
[    3.464000] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[    3.464000] Copyright (c) 1999-2006 Intel Corporation.
[    3.480000] SCSI subsystem initialized
[    3.492000] libata version 2.20 loaded.
[    3.528000] ieee1394: Initialized config rom entry `ip1394'
[    3.568000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[    3.568000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.568000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.568000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.568000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001840
[    3.568000] usb usb2: configuration #1 chosen from 1 choice
[    3.568000] hub 2-0:1.0: USB hub found
[    3.568000] hub 2-0:1.0: 2 ports detected
[    3.672000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[    3.672000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.672000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.672000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.672000] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001860
[    3.672000] usb usb3: configuration #1 chosen from 1 choice
[    3.672000] hub 3-0:1.0: USB hub found
[    3.672000] hub 3-0:1.0: 2 ports detected
[    3.776000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 23
[    3.776000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.776000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.776000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.776000] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001880
[    3.776000] usb usb4: configuration #1 chosen from 1 choice
[    3.776000] hub 4-0:1.0: USB hub found
[    3.776000] hub 4-0:1.0: 2 ports detected
[    3.880000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[    3.880000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.940000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    3.960000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[    3.960000] e1000: probe of 0000:02:00.0 failed with error -5
[    3.960000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[    3.960000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.960000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.960000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.960000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.960000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.960000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xee444000
[    3.964000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.964000] usb usb5: configuration #1 chosen from 1 choice
[    3.964000] hub 5-0:1.0: USB hub found
[    3.964000] hub 5-0:1.0: 8 ports detected
[    4.016000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.068000] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.068000] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 20
[    4.068000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.068000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.068000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.068000] scsi0 : ata_piix
[    4.232000] ATA: abnormal status 0x7F on port 0x000101f7
[    4.232000] scsi1 : ata_piix
[    4.236000] ata2: port disabled. ignoring.
[    4.236000] ahci 0000:00:1f.2: version 2.1
[    4.236000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 20
[    4.320000] usb 5-5: new high speed USB device using ehci_hcd and address 2
[    4.452000] usb 5-5: configuration #1 chosen from 1 choice
[    4.452000] hub 5-5:1.0: USB hub found
[    4.452000] hub 5-5:1.0: 7 ports detected
[    4.756000] usb 5-5.2: new high speed USB device using ehci_hcd and address 3
[    4.848000] usb 5-5.2: configuration #1 chosen from 1 choice
[    5.048000] usb 5-5.3: new low speed USB device using ehci_hcd and address 4
[    5.144000] usb 5-5.3: configuration #1 chosen from 1 choice
[    5.240000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.240000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x1 impl SATA mode
[    5.240000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[    5.240000] ata3: SATA max UDMA/133 cmd 0xf8908500 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.240000] ata4: SATA max UDMA/133 cmd 0xf8908580 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.240000] ata5: SATA max UDMA/133 cmd 0xf8908600 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.240000] ata6: SATA max UDMA/133 cmd 0xf8908680 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.240000] scsi2 : ahci
[    5.344000] usb 5-5.7: new low speed USB device using ehci_hcd and address 5
[    5.440000] usb 5-5.7: configuration #1 chosen from 1 choice
[    5.440000] usbcore: registered new interface driver libusual
[    5.444000] Initializing USB Mass Storage driver...
[    5.444000] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.444000] usb-storage: device found at 3
[    5.444000] usb-storage: waiting for device to settle before scanning
[    5.444000] usbcore: registered new interface driver usb-storage
[    5.444000] USB Mass Storage support registered.
[    5.444000] usbcore: registered new interface driver hiddev
[    5.448000] input: NOVATEK USB Keyboard as /class/input/input2
[    5.448000] input: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.7-5.3
[    5.452000] input: NOVATEK USB Keyboard as /class/input/input3
[    5.452000] input,hiddev96: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.7-5.3
[    5.452000] input: PS/2+USB Mouse as /class/input/input4
[    5.452000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.7-5.7
[    5.452000] usbcore: registered new interface driver usbhid
[    5.452000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.724000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.732000] ata3.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    5.732000] ata3.00: ATA-7: SAMSUNG HM120JI, YF100-19, max UDMA7
[    5.732000] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.740000] ata3.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[    5.740000] ata3.00: configured for UDMA/133
[    5.740000] scsi3 : ahci
[    6.052000] ata4: SATA link down (SStatus 0 SControl 0)
[    6.052000] scsi4 : ahci
[    6.364000] ata5: SATA link down (SStatus 0 SControl 0)
[    6.364000] scsi5 : ahci
[    6.676000] ata6: SATA link down (SStatus 0 SControl 0)
[    6.676000] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HM120JI  YF10 PQ: 0 ANSI: 5
[    6.676000] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[    6.676000] PCI: Setting latency timer of device 0000:15:00.1 to 64
[    6.728000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    6.728000] sda: Write Protect is off
[    6.728000] sda: Mode Sense: 00 3a 00 00
[    6.728000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.728000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    6.728000] sda: Write Protect is off
[    6.728000] sda: Mode Sense: 00 3a 00 00
[    6.728000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.728000]  sda:<6>ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[e4301000-e43017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.744000]  sda1 sda2 sda3
[    6.772000] sd 2:0:0:0: Attached scsi disk sda
[    6.776000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    6.960000] Attempting manual resume
[    6.960000] swsusp: Resume From Partition 8:2
[    6.960000] PM: Checking swsusp image.
[    6.960000] PM: Resume from disk failed.
[    7.004000] kjournald starting.  Commit interval 5 seconds
[    7.004000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.008000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae40600512068]
[   10.444000] usb-storage: device scan complete
[   10.444000] scsi 6:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB04 PQ: 0 ANSI: 0
[   10.444000] scsi 6:0:0:0: Attached scsi generic sg1 type 5
[   18.644000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.660000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.752000] Linux agpgart interface v0.102 (c) Dave Jones
[   18.852000] agpgart: Detected an Intel 945GM Chipset.
[   18.852000] agpgart: Detected 7932K stolen memory.
[   18.868000] intel_rng: FWH not detected
[   18.868000] agpgart: AGP aperture is 256M @ 0xd0000000
[   18.868000] input: PC Speaker as /class/input/input5
[   19.260000] iTCO_vendor_support: vendor-support=0
[   19.260000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   19.260000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   19.260000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.308000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:201c]
[   19.352000] ieee80211_crypt: registered algorithm 'NULL'
[   19.380000] sdhci: Secure Digital Host Controller Interface driver
[   19.380000] sdhci: Copyright(c) Pierre Ossman
[   19.384000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.384000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.404000] usbcore: registered new interface driver xpad
[   19.404000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   19.436000] Yenta: ISA IRQ mask 0x04b8, PCI irq 20
[   19.436000] Socket status: 30000006
[   19.436000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
[   19.436000] cs: IO port probe 0x9000-0xcfff: clean.
[   19.436000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[   19.436000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[   19.436000] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 18)
[   19.436000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   19.436000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   19.436000] mmc0: SDHCI at 0xe4301800 irq 22 DMA
[   19.448000] irda_init()
[   19.448000] NET: Registered protocol family 23
[   19.496000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   19.496000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   19.500000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   19.500000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   19.500000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.580000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.580000] Uniform CD-ROM driver Revision: 3.20
[   19.580000] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   19.744000] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   19.744000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   19.824000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.844000] input: TPPS/2 IBM TrackPoint as /class/input/input6
[   19.848000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   19.848000] nsc-ircc, chip->init
[   19.848000] nsc-ircc, Found chip at base=0x164e
[   19.848000] nsc-ircc, driver loaded (Dag Brattli)
[   19.848000] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.848000] nsc-ircc, Found chip at base=0x164e
[   19.848000] nsc-ircc, driver loaded (Dag Brattli)
[   19.848000] nsc_ircc_open(), can't get iobase of 0x2f8
[   19.848000] pnp: Device 00:0a disabled.
[   19.856000] cs: IO port probe 0x100-0x3af: clean.
[   19.856000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.856000] cs: IO port probe 0x820-0x8ff: clean.
[   19.856000] cs: IO port probe 0xc00-0xcf7: clean.
[   19.860000] cs: IO port probe 0xa00-0xaff: clean.
[   20.244000] fuse init (API version 7.8)
[   20.332000] lp: driver loaded but no devices found
[   20.388000] Adding 2008116k swap on /dev/disk/by-uuid/2fbef525-8ae3-46f3-a980-9abd39575343.  Priority:-1 extents:1 across:2008116k
[   20.568000] EXT3 FS on sda3, internal journal
[   20.776000] kjournald starting.  Commit interval 5 seconds
[   20.776000] EXT3 FS on sda1, internal journal
[   20.776000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.392000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   22.160000] NET: Registered protocol family 17
[   86.280000] NET: Registered protocol family 10
[   86.280000] lo: Disabled Privacy Extensions
[   86.280000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   91.412000] Using specific hotkey driver
[   91.472000] ibm_acpi: ThinkPad EC firmware 7JHT13WW-1.04
[   91.472000] ibm_acpi: IBM ThinkPad ACPI Extras v0.13
[   91.472000] ibm_acpi: http://ibm-acpi.sf.net/
[   91.496000] ACPI: ACPI Dock Station Driver
[   91.532000] ACPI: Battery Slot [BAT0] (battery present)
[   91.676000] input: Power Button (FF) as /class/input/input7
[   91.676000] ACPI: Power Button (FF) [PWRF]
[   91.688000] input: Lid Switch as /class/input/input8
[   91.688000] ACPI: Lid Switch [LID]
[   91.688000] input: Sleep Button (CM) as /class/input/input9
[   91.688000] ACPI: Sleep Button (CM) [SLPB]
[   91.732000] ACPI: AC Adapter [AC] (on-line)
[   91.784000] pcc_acpi: loading...
[   94.904000] ttyS1: LSR safety check engaged!
[   95.788000] ppdev: user-space parallel port driver
[   96.436000] apm: BIOS not found.
[   96.564000] Non-volatile memory driver v1.2
[   96.584000] input: /usr/sbin/thinkpad-keys as /class/input/input10
[   97.096000] Bluetooth: Core ver 2.11
[   97.096000] NET: Registered protocol family 31
[   97.096000] Bluetooth: HCI device and connection manager initialized
[   97.096000] Bluetooth: HCI socket layer initialized
[   97.128000] Bluetooth: L2CAP ver 2.8
[   97.128000] Bluetooth: L2CAP socket layer initialized
[   97.240000] Bluetooth: RFCOMM socket layer initialized
[   97.240000] Bluetooth: RFCOMM TTY layer initialized
[   97.240000] Bluetooth: RFCOMM ver 1.8
[  100.164000] [drm] Initialized drm 1.1.0 20060810
[  100.168000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[  100.168000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  306.216000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  306.248000] ieee80211_crypt: registered algorithm 'TKIP'
[  325.048000] eth0: no IPv6 routers present
[25700.004000] usb 5-5: USB disconnect, address 2
[25700.004000] usb 5-5.2: USB disconnect, address 3
[25700.004000] usb 5-5.3: USB disconnect, address 4
[25700.004000] usb 5-5.7: USB disconnect, address 5
[30060.376000] thinkpad_ec: thinkpad_ec 0.32 loaded.
[30060.380000] tp_smapi: Unknown parameter `hdaps'
[30106.296000] thinkpad_ec: unloaded.
[30115.820000] thinkpad_ec: thinkpad_ec 0.32 loaded.
[30115.820000] tp_smapi: Unknown parameter `hdaps'
[33028.008000] vmmon: module license 'unspecified' taints kernel.
[33028.012000] /dev/vmmon[13524]: Module vmmon: registered with major=10 minor=165
[33028.012000] /dev/vmmon[13524]: Module vmmon: initialized
[33028.016000] /dev/vmmon[13531]: Module vmmon: unloaded
[33286.968000] /dev/vmmon[14471]: Module vmmon: registered with major=10 minor=165
[33286.968000] /dev/vmmon[14471]: Module vmmon: initialized
[33286.968000] /dev/vmmon[14478]: Module vmmon: unloaded
[33482.572000] /dev/vmmon[14852]: Module vmmon: registered with major=10 minor=165
[33482.572000] /dev/vmmon[14852]: Module vmmon: initialized
[33482.924000] /dev/vmnet: open called by PID 14886 (vmnet-bridge)
[33482.924000] /dev/vmnet: hub 0 does not exist, allocating memory.
[33482.924000] /dev/vmnet: port on hub 0 successfully opened
[33482.924000] bridge-eth0: enabling the bridge
[33482.924000] bridge-eth0: is a Wireless Adapter
[33482.924000] bridge-eth0: up
[33482.924000] bridge-eth0: already up
[33482.924000] bridge-eth0: attached
[33509.028000] ttyS1: LSR safety check engaged!
[33513.772000] ttyS1: LSR safety check engaged!
[33547.908000] /dev/vmnet: open called by PID 14936 (vmware-vmx)
[33547.908000] /dev/vmnet: port on hub 0 successfully opened
[33548.184000] /dev/vmmon[14946]: host clock rate change request 0 -> 19
[33553.200000] /dev/vmmon[14946]: host clock rate change request 19 -> 83
[33696.512000] /dev/vmnet: open called by PID 14946 (vmware-vmx)
[33696.512000] /dev/vmnet: port on hub 0 successfully opened
[33719.272000] /dev/vmnet: open called by PID 14948 (vmware-vmx)
[33719.272000] /dev/vmnet: port on hub 0 successfully opened
[33719.360000] /dev/vmmon[14948]: host clock rate change request 83 -> 19
[33719.380000] /dev/vmmon[14946]: host clock rate change request 19 -> 1
[33719.380000] /dev/vmmon[14946]: host clock rate change request 1 -> 19
[33725.356000] /dev/vmmon[14946]: host clock rate change request 19 -> 83
[33742.104000] /dev/vmnet: open called by PID 14948 (vmware-vmx)
[33742.104000] /dev/vmnet: port on hub 0 successfully opened
[34627.576000] /dev/vmmon[14936]: host clock rate change request 83 -> 0
[34627.608000] vmmon: Had to deallocate locked 224566 pages from vm driver f6687000
[34627.620000] vmmon: Had to deallocate AWE 9000 pages from vm driver f6687000
[34897.068000] usb 5-5: new high speed USB device using ehci_hcd and address 6
[34897.200000] usb 5-5: configuration #1 chosen from 1 choice
[34897.200000] hub 5-5:1.0: USB hub found
[34897.200000] hub 5-5:1.0: 7 ports detected
[34897.504000] usb 5-5.2: new high speed USB device using ehci_hcd and address 7
[34897.596000] usb 5-5.2: configuration #1 chosen from 1 choice
[34897.596000] scsi7 : SCSI emulation for USB Mass Storage devices
[34897.596000] usb-storage: device found at 7
[34897.596000] usb-storage: waiting for device to settle before scanning
[34897.796000] usb 5-5.3: new low speed USB device using ehci_hcd and address 8
[34897.892000] usb 5-5.3: configuration #1 chosen from 1 choice
[34897.896000] input: NOVATEK USB Keyboard as /class/input/input11
[34897.896000] input: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.7-5.3
[34897.900000] input: NOVATEK USB Keyboard as /class/input/input12
[34897.900000] input,hiddev96: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.7-5.3
[34898.100000] usb 5-5.7: new low speed USB device using ehci_hcd and address 9
[34898.196000] usb 5-5.7: configuration #1 chosen from 1 choice
[34898.200000] input: PS/2+USB Mouse as /class/input/input13
[34898.200000] input: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.7-5.7
[34902.596000] usb-storage: device scan complete
[34902.596000] scsi 7:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB04 PQ: 0 ANSI: 0
[34902.608000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[34902.608000] sr 7:0:0:0: Attached scsi CD-ROM sr0
[34902.608000] sr 7:0:0:0: Attached scsi generic sg1 type 5
[38434.976000] usbcore: registered new interface driver hsfusbcd2
[39101.292000] ttyS1: LSR safety check engaged!
[39119.352000] /dev/vmnet: open called by PID 18017 (vmware-vmx)
[39119.352000] /dev/vmnet: port on hub 0 successfully opened
[39119.556000] /dev/vmmon[18030]: host clock rate change request 0 -> 19
[39119.556000] /dev/vmmon[18030]: host clock rate change request 19 -> 83
[40309.468000] /dev/vmmon[18017]: host clock rate change request 83 -> 0
[40309.500000] vmmon: Had to deallocate locked 177262 pages from vm driver de90f000
[40309.508000] vmmon: Had to deallocate AWE 9148 pages from vm driver de90f000
[43041.392000] usb 5-5.3: USB disconnect, address 8
[43064.176000] usb 5-5.7: USB disconnect, address 9
[43561.584000] usb 5-1: new high speed USB device using ehci_hcd and address 10
[43561.720000] usb 5-1: configuration #1 chosen from 1 choice
[43561.720000] scsi8 : SCSI emulation for USB Mass Storage devices
[43561.720000] usb-storage: device found at 10
[43561.720000] usb-storage: waiting for device to settle before scanning
[43566.720000] usb-storage: device scan complete
[43566.720000] scsi 8:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[43566.920000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[43566.920000] sdb: Write Protect is off
[43566.920000] sdb: Mode Sense: 23 00 00 00
[43566.920000] sdb: assuming drive cache: write through
[43566.924000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[43566.924000] sdb: Write Protect is off
[43566.924000] sdb: Mode Sense: 23 00 00 00
[43566.924000] sdb: assuming drive cache: write through
[43566.924000]  sdb: sdb1
[43566.924000] sd 8:0:0:0: Attached scsi removable disk sdb
[43566.924000] sd 8:0:0:0: Attached scsi generic sg2 type 0
[43611.240000] usb 5-1: USB disconnect, address 10
[46002.456000] usb 5-2: new high speed USB device using ehci_hcd and address 11
[46002.592000] usb 5-2: configuration #1 chosen from 1 choice
[46002.592000] scsi9 : SCSI emulation for USB Mass Storage devices
[46002.592000] usb-storage: device found at 11
[46002.592000] usb-storage: waiting for device to settle before scanning
[46007.592000] usb-storage: device scan complete
[46007.592000] scsi 9:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[46007.796000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[46007.796000] sdb: Write Protect is off
[46007.796000] sdb: Mode Sense: 23 00 00 00
[46007.796000] sdb: assuming drive cache: write through
[46007.800000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[46007.800000] sdb: Write Protect is off
[46007.800000] sdb: Mode Sense: 23 00 00 00
[46007.800000] sdb: assuming drive cache: write through
[46007.800000]  sdb: sdb1
[46007.800000] sd 9:0:0:0: Attached scsi removable disk sdb
[46007.800000] sd 9:0:0:0: Attached scsi generic sg2 type 0
[46037.244000] usb 5-2: USB disconnect, address 11
[47100.924000] usb 5-1: new high speed USB device using ehci_hcd and address 12
[47101.060000] usb 5-1: configuration #1 chosen from 1 choice
[47101.060000] scsi10 : SCSI emulation for USB Mass Storage devices
[47101.060000] usb-storage: device found at 12
[47101.060000] usb-storage: waiting for device to settle before scanning
[47106.060000] usb-storage: device scan complete
[47106.060000] scsi 10:0:0:0: Direct-Access     PNY      USB 2.0 FD       PMAP PQ: 0 ANSI: 0 CCS
[47106.260000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[47106.260000] sdb: Write Protect is off
[47106.260000] sdb: Mode Sense: 23 00 00 00
[47106.260000] sdb: assuming drive cache: write through
[47106.264000] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[47106.264000] sdb: Write Protect is off
[47106.264000] sdb: Mode Sense: 23 00 00 00
[47106.264000] sdb: assuming drive cache: write through
[47106.264000]  sdb: sdb1
[47106.264000] sd 10:0:0:0: Attached scsi removable disk sdb
[47106.264000] sd 10:0:0:0: Attached scsi generic sg2 type 0
[47196.696000] usb 5-1: USB disconnect, address 12
[58600.160000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074511578:2074516359. Repaired.
[58601.320000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074511578:2074516359. Repaired.
[58610.564000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074544974:2074549755. Repaired.
[58611.444000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074544974:2074549755. Repaired.
[58613.204000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074544974:2074549755. Repaired.
[58616.724000] TCP: Treason uncloaked! Peer 80.142.184.62:61185/52906 shrinks window 2074544974:2074549755. Repaired.
[69148.520000] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[69148.520000] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[69148.520000] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[69148.720000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.720000]     Additional sense: Medium not present - tray closed
[69148.720000] end_request: I/O error, dev sr0, sector 0
[69148.720000] Buffer I/O error on device sr0, logical block 0
[69148.720000] Buffer I/O error on device sr0, logical block 1
[69148.720000] Buffer I/O error on device sr0, logical block 2
[69148.720000] Buffer I/O error on device sr0, logical block 3
[69148.720000] Buffer I/O error on device sr0, logical block 4
[69148.720000] Buffer I/O error on device sr0, logical block 5
[69148.720000] Buffer I/O error on device sr0, logical block 6
[69148.720000] Buffer I/O error on device sr0, logical block 7
[69148.720000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.720000]     Additional sense: Medium not present - tray closed
[69148.720000] end_request: I/O error, dev sr0, sector 0
[69148.720000] Buffer I/O error on device sr0, logical block 0
[69148.720000] Buffer I/O error on device sr0, logical block 1
[69148.724000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.724000]     Additional sense: Medium not present - tray closed
[69148.724000] end_request: I/O error, dev sr0, sector 0
[69148.724000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.724000]     Additional sense: Medium not present - tray closed
[69148.724000] end_request: I/O error, dev sr0, sector 4
[69148.728000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.728000]     Additional sense: Medium not present - tray closed
[69148.728000] end_request: I/O error, dev sr0, sector 0
[69148.728000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.728000]     Additional sense: Medium not present - tray closed
[69148.728000] end_request: I/O error, dev sr0, sector 0
[69148.732000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.732000]     Additional sense: Medium not present - tray closed
[69148.732000] end_request: I/O error, dev sr0, sector 4
[69148.732000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.732000]     Additional sense: Medium not present - tray closed
[69148.732000] end_request: I/O error, dev sr0, sector 0
[69148.736000] sr 7:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[69148.736000]     Additional sense: Medium not present - tray closed
[69148.736000] end_request: I/O error, dev sr0, sector 4

```

---

### Post by noob12 on 2007-10-03
OK.  Your chipset is covered by the existing e1000 driver but it is encountering this problem
```

[    3.940000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    3.960000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[    3.960000] e1000: probe of 0000:02:00.0 failed with error -5

```

In order to workaround that you can do the following.  This adds a line to /etc/modprobe.d/options
that tells the system to add an option to ignore the checksum when loading e1000.
```

echo "options e1000 eeprom_bad_csum_allow=1" | sudo tee -a /etc/modprobe.d/options

```

Reboot.  You should see e1000 load properly and your wired interface should appear (use **ifconfig -a**)

Now as a result of eth0 already being mapped to your wireless interface it will probably come up as eth1.  It is more conventional that eth0 be the first wired interface.  If you want to switch these, you can edit /etc/iftab and use the mac addresses shown by **ifconfig -a** to swap the names.  Let's first get it to show up and then let me know if you need specific instructions for swapping the names.

---

### Post by fahim on 2007-10-04
Thank you very much. I tried that out but do get the same error:

```
[    4.176000] e1000: 0000:02:00.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    4.196000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[    4.196000] e1000: probe of 0000:02:00.0 failed with error -5

```

The Allowed Checksum Error has been written in /etc/modprobe.d/options but seems not to be working?!

---

### Post by noob12 on 2007-10-04
Sorry.  Those instructions would have applied to Feisty.  What release are you running?

Can you post the output of **uname -r** and **modinfo e1000**

---

### Post by noob12 on 2007-10-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/60388](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/60388) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Added relevant bug ref.

---

### Post by fahim on 2007-10-05
That did not work too. Sometimes my wired ethernet will be recognized, somtimes not. I did now install kubuntu 7.10 and everything works great. Thanks

---

### Post by noob12 on 2007-10-05
OK.  Glad to hear.

---

