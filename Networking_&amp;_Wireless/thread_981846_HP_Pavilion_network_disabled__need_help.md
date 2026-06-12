---
title: "HP Pavilion network disabled // need help"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Janjaya on 2008-11-14
My PC is a HP Pavilion dv6000 series (I had Windows XP on it before). I have tried a few guides, but none of them have worked. I haven't managed to get Ubuntu to detect my network card. I think that's the problem. And I have Ubuntu version 8.10. Got aditional questions? Just ask me.
Thanks to anyone who tries to slove my problem.

Type: Network adapter
Data Link Protocol: Ethernet / Fast Ethernet / IEEE 802.11b / IEEE 802.11a / IEEE 802.11g
Wireless Protocol: 802.11a/b/g
Wireless LAN Supported: Yes



[http://alatest.no/produktdetaljer/baerbare-datamaskiner/hp-pavilion-dv6000-series-laptop-computer/pd3-34068572,30/?p=277881](http://alatest.no/produktdetaljer/baerbare-datamaskiner/hp-pavilion-dv6000-series-laptop-computer/pd3-34068572,30/?p=277881) (it's a norwegian link, but the computer details is in english)



[COLOR="Red"]"lshw -C network"

[SIZE="1"]WARNING: you should run this program as super-user.
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: f6:6e:c5:17:c6:6b
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 fireware= N/A multicast=yes[/SIZE][/COLOR]

---

### Post by Iowan on 2008-11-14
[Here]("http://excid3.betaserver.org/2008/09/29/installing-ubuntu-hardy-heron-on-hp-and-compaq-laptops/#content") is a How-To on setting up Hardy on your computer.  I'll see if I can find more pertinent info on the network in particular. [This one]("http://ubuntuforums.org/showthread.php?t=831525") mentions Nvidia/broadcom and NDISWRAPPER.

---

### Post by Janjaya on 2008-11-15
it is working fine until the last part with the code "sudo ifconfig wlan0 up". I have installed the b43-fwcutter + firmware. My source guide: [http://ubuntuforums.org/showthread.php?t=779754]("http://ubuntuforums.org/showthread.php?t=779754")


It only say:
```
~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

Anyone have an idea of why I get this error message?

---

### Post by walkerk on 2008-11-15
> **Janjaya said:**
> it is working fine until the last part with the code "sudo ifconfig wlan0 up". I have installed the b43-fwcutter + firmware. My source guide: [http://ubuntuforums.org/showthread.php?t=779754]("http://ubuntuforums.org/showthread.php?t=779754")


It only say:
```
~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

Anyone have an idea of why I get this error message?

b43-fwcutter has since been replaced by b43. Please provide the following from the terminal:
```
sudo lshw -C network
```
```
lspci
```

With the above I can point you in the right direction.

---

### Post by Janjaya on 2008-11-15
~$ sudo lshw -C network 
```
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:de:24:0c:36:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

~$ lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

It is nothing wrong with my wired connection btw:P

---

### Post by walkerk on 2008-11-15
Ok... so I don't even see a mention of your wlan ethernet controller. I have a very similar laptop and my last line of [lspci] is as follows:
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Two things to check.

1. Is WLAN enabled in your BIOS?
2. Do you have a wireless switch on your computer? If yes, toggle it. For whatever reason with mine on = off, and off = on.

Let me know.

---

### Post by Janjaya on 2008-11-15
*1. Is WLAN enabled in your BIOS?*
I restarted my computer, and went into BIOS. I could not see any WLAN enabled/disabled (maybe I did it wrong). I think that's my problem. That my WLAN isn't enabled.


*2. Do you have a wireless switch on your computer? If yes, toggle it. For whatever reason with mine on = off, and off = on.*
Yes I have. I have toggle it on and off, but no change.

---

### Post by walkerk on 2008-11-15
Did a quick search online for your laptop and the results look dark. Not sure if you are have the same problems or not but I would take a look [here]("http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1226744282209+28353475&threadId=1107945").

---

### Post by Janjaya on 2008-11-15
Damn, maybe I have to switch back to Windows XP again:(

---

### Post by walkerk on 2008-11-15
> **Janjaya said:**
> Damn, maybe I have to switch back to Windows XP again:(

If it worked fine with XP it should work with Ubuntu. Those people were having problems getting it to work w/ Windows. Did you look in the BIOS? Toggle the Wifi switch?

edit: I see you already answered me. I'm going to reboot my computer and look in the BIOS.

edit2: Rebooted but I didn't see a WLAN option in the BIOS :/

---

### Post by walkerk on 2008-11-15
Please post the results of

```
dmesg
```

---

### Post by Janjaya on 2008-11-15
Here you go, hope you find something out, because I'm out of ideas.


```
~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=a19a30fc-c120-4f1c-9201-7e7ed5809ef9 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff15000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff15000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x3ff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 003fe00000 page 2M
[    0.000000]  003fe00000 - 003ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 3ff00000 @ 8000-b000
[    0.000000] last_map_addr: 3ff00000 end: 3ff00000
[    0.000000] RAMDISK: 377b2000 - 37fefb4a
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F88F0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3FF0BD23, 003C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 3FF14D10, 0074 (r1 HP     MCP51M    6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 3FF0BD5F, 8FB1 (r1 HP       MCP51M  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FF15FC0, 0040
[    0.000000] ACPI: SSDT 3FF14D84, 0182 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG 3FF14F06, 003C (r1 HP       MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET 3FF14F42, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC 3FF14F7A, 005E (r1 HP     	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 3FF14FD8, 0028 (r1     HP $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [0000000000009000 -  0000000000010fdf] pages 8
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b2000 - 0037fefb4a]          RAMDISK ==> [00377b2000 - 0037fefb4a]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 0000009000]          PGTABLE ==> [0000008000 - 0000009000]
[    0.000000] found SMP MP-table at [ffff8800000f8920] 000f8920
[    0.000000]  [ffffe20000000000-ffffe20000ffffff] PMD -> [ffff880001200000-ffff8800021fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003ff00
[    0.000000] On node 0 totalpages: 261789
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 253764 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 255873
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=a19a30fc-c120-4f1c-9201-7e7ed5809ef9 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1607.285 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ d334000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1015176k/1047552k available (3112k kernel code, 31980k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3214.57 BogoMIPS (lpj=6429140)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] tseg: 003ff80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080609
[    0.006185] ACPI: Checking initramfs for custom DSDT
[    0.448692] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.488448] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.488454] Using local APIC timer interrupts.
[    0.492032] APIC timer calibration result 12556931
[    0.492035] Detected 12.556 MHz APIC timer.
[    0.492233] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3214.64 BogoMIPS (lpj=6429281)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.580212] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.580229] Brought up 2 CPUs
[    0.580232] Total of 2 processors activated (6429.21 BogoMIPS).
[    0.580353] CPU0 attaching sched-domain:
[    0.580357]  domain 0: span 0-1 level CPU
[    0.580360]   groups: 0 1
[    0.580365]   domain 1: span 0-1 level NODE
[    0.580368]    groups: 0-1
[    0.580374] CPU1 attaching sched-domain:
[    0.580376]  domain 0: span 0-1 level CPU
[    0.580379]   groups: 1 0
[    0.580383]   domain 1: span 0-1 level NODE
[    0.580385]    groups: 0-1
[    0.580496] Switch to broadcast mode on CPU0
[    0.580496] net_namespace: 1552 bytes
[    0.580496] Booting paravirtualized kernel on bare hardware
[    0.580496] Time: 19:18:33  Date: 11/15/08
[    0.580496] NET: Registered protocol family 16
[    0.580496] node 0 link 0: io port [1000, fffff]
[    0.580496] TOM: 0000000040000000 aka 1024M
[    0.580496] node 0 link 0: mmio [e0000000, efffffff]
[    0.580496] node 0 link 0: mmio [a0000, bffff]
[    0.580496] node 0 link 0: mmio [40000000, fe0bffff]
[    0.580496] bus: [00,ff] on node 0 link 0
[    0.580496] bus: 00 index 0 io port: [0, ffff]
[    0.580496] bus: 00 index 1 mmio: [40000000, fcffffffff]
[    0.580496] bus: 00 index 2 mmio: [a0000, bffff]
[    0.580496] ACPI: bus type pci registered
[    0.580496] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.580496] PCI: MCFG area at e0000000 reserved in E820
[    0.580509] PCI: Using MMCONFIG at e0000000 - e06fffff
[    0.580511] PCI: Using configuration type 1 for base access
[    0.584165] ACPI: EC: Look up EC in DSDT
[    0.588190] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.588702] ACPI: Interpreter enabled
[    0.588705] ACPI: (supports S0 S3 S4 S5)
[    0.588723] ACPI: Using IOAPIC for interrupt routing
[    0.588820] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.612239] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.612239] ACPI: EC: driver started in interrupt mode
[    0.612239] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.612269] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612273] pci 0000:00:02.0: PME# disabled
[    0.612300] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612303] pci 0000:00:03.0: PME# disabled
[    0.612329] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612333] pci 0000:00:04.0: PME# disabled
[    0.612486] PCI: 0000:00:0a.0 reg 10 io port: [1d00, 1d7f]
[    0.612548] PCI: 0000:00:0a.1 reg 20 io port: [3040, 307f]
[    0.612554] PCI: 0000:00:0a.1 reg 24 io port: [3000, 303f]
[    0.612574] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.612580] pci 0000:00:0a.1: PME# disabled
[    0.612608] PCI: 0000:00:0a.3 reg 10 32bit mmio: [c0040000, c007ffff]
[    0.612700] PCI: 0000:00:0b.0 reg 10 32bit mmio: [c0004000, c0004fff]
[    0.612733] pci 0000:00:0b.0: supports D1
[    0.612735] pci 0000:00:0b.0: supports D2
[    0.612737] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612742] pci 0000:00:0b.0: PME# disabled
[    0.612768] PCI: 0000:00:0b.1 reg 10 32bit mmio: [c0005000, c00050ff]
[    0.612800] pci 0000:00:0b.1: supports D1
[    0.612802] pci 0000:00:0b.1: supports D2
[    0.612804] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612808] pci 0000:00:0b.1: PME# disabled
[    0.612843] PCI: 0000:00:0d.0 reg 20 io port: [3080, 308f]
[    0.612884] PCI: 0000:00:0e.0 reg 10 io port: [30c0, 30c7]
[    0.612889] PCI: 0000:00:0e.0 reg 14 io port: [30b4, 30b7]
[    0.612894] PCI: 0000:00:0e.0 reg 18 io port: [30b8, 30bf]
[    0.612899] PCI: 0000:00:0e.0 reg 1c io port: [30b0, 30b3]
[    0.612905] PCI: 0000:00:0e.0 reg 20 io port: [3090, 309f]
[    0.612910] PCI: 0000:00:0e.0 reg 24 32bit mmio: [c0006000, c0006fff]
[    0.612988] PCI: 0000:00:10.1 reg 10 32bit mmio: [c0000000, c0003fff]
[    0.613019] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.613023] pci 0000:00:10.1: PME# disabled
[    0.613051] PCI: 0000:00:14.0 reg 10 32bit mmio: [c0008000, c0008fff]
[    0.613056] PCI: 0000:00:14.0 reg 14 io port: [30e0, 30e7]
[    0.613079] pci 0000:00:14.0: supports D1
[    0.613081] pci 0000:00:14.0: supports D2
[    0.613083] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613087] pci 0000:00:14.0: PME# disabled
[    0.613176] PCI: bridge 0000:00:02.0 io port: [4000, 4fff]
[    0.613176] PCI: bridge 0000:00:02.0 32bit mmio: [c2000000, c3ffffff]
[    0.613176] PCI: bridge 0000:00:02.0 64bit mmio pref: [c8200000, c83fffff]
[    0.613176] PCI: bridge 0000:00:03.0 io port: [5000, 5fff]
[    0.613176] PCI: bridge 0000:00:03.0 32bit mmio: [c4000000, c5ffffff]
[    0.613176] PCI: bridge 0000:00:03.0 64bit mmio pref: [c8400000, c85fffff]
[    0.613176] PCI: 0000:05:00.0 reg 10 32bit mmio: [c7000000, c7ffffff]
[    0.613176] PCI: 0000:05:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.613176] PCI: 0000:05:00.0 reg 1c 64bit mmio: [c6000000, c6ffffff]
[    0.613176] PCI: 0000:05:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.613176] PCI: bridge 0000:00:04.0 32bit mmio: [c6000000, c7ffffff]
[    0.613176] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, dfffffff]
[    0.613176] PCI: 0000:07:05.0 reg 10 32bit mmio: [c8000000, c80007ff]
[    0.613176] pci 0000:07:05.0: supports D1
[    0.613176] pci 0000:07:05.0: supports D2
[    0.613176] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613176] pci 0000:07:05.0: PME# disabled
[    0.613176] PCI: 0000:07:05.1 reg 10 32bit mmio: [c8000800, c80008ff]
[    0.613176] pci 0000:07:05.1: supports D1
[    0.613176] pci 0000:07:05.1: supports D2
[    0.613176] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613176] pci 0000:07:05.1: PME# disabled
[    0.613176] PCI: 0000:07:05.2 reg 10 32bit mmio: [c8000c00, c8000cff]
[    0.613176] pci 0000:07:05.2: supports D1
[    0.613176] pci 0000:07:05.2: supports D2
[    0.613176] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613176] pci 0000:07:05.2: PME# disabled
[    0.613176] PCI: 0000:07:05.3 reg 10 32bit mmio: [c8001000, c80010ff]
[    0.613176] pci 0000:07:05.3: supports D1
[    0.613176] pci 0000:07:05.3: supports D2
[    0.613176] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613176] pci 0000:07:05.3: PME# disabled
[    0.613176] PCI: 0000:07:05.4 reg 10 32bit mmio: [c8001400, c80014ff]
[    0.613176] pci 0000:07:05.4: supports D1
[    0.613176] pci 0000:07:05.4: supports D2
[    0.613176] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613176] pci 0000:07:05.4: PME# disabled
[    0.613176] pci 0000:00:10.0: transparent bridge
[    0.613176] PCI: bridge 0000:00:10.0 32bit mmio: [c8000000, c80fffff]
[    0.613176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.613176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.613176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.613176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.613176] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.668378] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.668709] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.669033] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.669355] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.669677] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[    0.669998] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.670320] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.670641] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.670964] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.671009] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.671009] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.671009] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.671009] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.671009] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.671009] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.671009] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.671009] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.671030] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.671360] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.672127] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.672127] pnp: PnP ACPI init
[    0.672127] ACPI: bus type pnp registered
[    0.677414] pnp: PnP ACPI: found 13 devices
[    0.677414] ACPI: ACPI bus type pnp unregistered
[    0.680070] PCI: Using ACPI for IRQ routing
[    0.696044] NET: Registered protocol family 8
[    0.696046] NET: Registered protocol family 20
[    0.700042] NetLabel: Initializing
[    0.700042] NetLabel:  domain hash size = 128
[    0.700042] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.700062] NetLabel:  unlabeled traffic allowed by default
[    0.700170] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.700175] hpet0: 3 32-bit timers, 25000000 Hz
[    0.702861] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.702863]    actual entries 65586
[    0.703009] AppArmor: AppArmor Filesystem Enabled
[    0.703044] ACPI: RTC can wake from S4
[    0.704057] Switched to high resolution mode on CPU 0
[    0.704069] Switched to high resolution mode on CPU 1
[    0.709068] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.709076] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.709080] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.709084] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.709087] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.709095] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.709104] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.709108] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.709111] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.709114] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.709118] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.709121] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.709124] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.709132] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.709136] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.709139] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.714649] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.714653] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.714658] pci 0000:00:02.0:   MEM window: 0xc2000000-0xc3ffffff
[    0.714662] pci 0000:00:02.0:   PREFETCH window: 0x000000c8200000-0x000000c83fffff
[    0.714667] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.714670] pci 0000:00:03.0:   IO window: 0x5000-0x5fff
[    0.714673] pci 0000:00:03.0:   MEM window: 0xc4000000-0xc5ffffff
[    0.714677] pci 0000:00:03.0:   PREFETCH window: 0x000000c8400000-0x000000c85fffff
[    0.714684] pci 0000:05:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.714688] pci 0000:00:04.0: PCI bridge, secondary bus 0000:05
[    0.714690] pci 0000:00:04.0:   IO window: disabled
[    0.714694] pci 0000:00:04.0:   MEM window: 0xc6000000-0xc7ffffff
[    0.714697] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.714702] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.714705] pci 0000:00:10.0:   IO window: disabled
[    0.714709] pci 0000:00:10.0:   MEM window: 0xc8000000-0xc80fffff
[    0.714713] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.714725] pci 0000:00:02.0: setting latency timer to 64
[    0.714731] pci 0000:00:03.0: setting latency timer to 64
[    0.714736] pci 0000:00:04.0: setting latency timer to 64
[    0.714742] pci 0000:00:10.0: setting latency timer to 64
[    0.714746] bus: 00 index 0 io port: [0, ffff]
[    0.714748] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.714751] bus: 01 index 0 io port: [4000, 4fff]
[    0.714754] bus: 01 index 1 mmio: [c2000000, c3ffffff]
[    0.714756] bus: 01 index 2 mmio: [c8200000, c83fffff]
[    0.714759] bus: 01 index 3 mmio: [0, 0]
[    0.714761] bus: 03 index 0 io port: [5000, 5fff]
[    0.714764] bus: 03 index 1 mmio: [c4000000, c5ffffff]
[    0.714767] bus: 03 index 2 mmio: [c8400000, c85fffff]
[    0.714769] bus: 03 index 3 mmio: [0, 0]
[    0.714771] bus: 05 index 0 mmio: [0, 0]
[    0.714774] bus: 05 index 1 mmio: [c6000000, c7ffffff]
[    0.714776] bus: 05 index 2 mmio: [d0000000, dfffffff]
[    0.714779] bus: 05 index 3 mmio: [0, 0]
[    0.714781] bus: 07 index 0 mmio: [0, 0]
[    0.714783] bus: 07 index 1 mmio: [c8000000, c80fffff]
[    0.714786] bus: 07 index 2 mmio: [0, 0]
[    0.714788] bus: 07 index 3 io port: [0, ffff]
[    0.714791] bus: 07 index 4 mmio: [0, ffffffffffffffff]
[    0.714809] NET: Registered protocol family 2
[    0.753148] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.753798] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.755322] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.756018] TCP: Hash tables configured (established 131072 bind 65536)
[    0.756022] TCP reno registered
[    0.765140] NET: Registered protocol family 1
[    0.765292] checking if image is initramfs... it is
[    1.801490] Freeing initrd memory: 8438k freed
[    1.807311] Simple Boot Flag at 0x36 set to 0x1
[    1.808978] audit: initializing netlink socket (disabled)
[    1.808993] type=2000 audit(1226776713.808:1): initialized
[    1.816280] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.820098] VFS: Disk quotas dquot_6.5.1
[    1.820228] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.820366] msgmni has been set to 1999
[    1.820539] io scheduler noop registered
[    1.820541] io scheduler anticipatory registered
[    1.820543] io scheduler deadline registered
[    1.820724] io scheduler cfq registered (default)
[    1.820740] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.820785] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.820796] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.820808] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.820833] pci 0000:00:09.0: Enabling HT MSI Mapping
[    2.024096] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    2.024108] pci 0000:00:10.0: Enabling HT MSI Mapping
[    2.024122] pci 0000:00:10.1: Enabling HT MSI Mapping
[    2.024148] pci 0000:05:00.0: Boot video device
[    2.024341] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.024367] pcieport-driver 0000:00:02.0: found MSI capability
[    2.024395] pci_express 0000:00:02.0:pcie00: allocate port service
[    2.024476] pci_express 0000:00:02.0:pcie03: allocate port service
[    2.024588] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    2.024613] pcieport-driver 0000:00:03.0: found MSI capability
[    2.024632] pci_express 0000:00:03.0:pcie00: allocate port service
[    2.024706] pci_express 0000:00:03.0:pcie03: allocate port service
[    2.024814] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    2.024838] pcieport-driver 0000:00:04.0: found MSI capability
[    2.024857] pci_express 0000:00:04.0:pcie00: allocate port service
[    2.024940] pci_express 0000:00:04.0:pcie03: allocate port service
[    2.086128] hpet_resources: 0xfed00000 is busy
[    2.086254] Linux agpgart interface v0.103
[    2.086260] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.089865] brd: module loaded

[    2.089971] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.090157] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.107156] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.107166] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.125273] mice: PS/2 mouse device common for all mice
[    2.125495] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    2.125534] rtc0: alarms up to one year, y3k, hpet irqs
[    2.125602] cpuidle: using governor ladder
[    2.125604] cpuidle: using governor menu
[    2.126083] TCP cubic registered
[    2.126458] registered taskstats version 1
[    2.126650]   Magic number: 0:445:344
[    2.126734] tty tty61: hash matches
[    2.126810] rtc_cmos 00:09: setting system clock to 2008-11-15 19:18:35 UTC (1226776715)
[    2.126814] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.126816] EDD information not available.
[    2.126879] Freeing unused kernel memory: 536k freed
[    2.127188] Write protecting the kernel read-only data: 4348k
[    2.138146] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.316137] fuse init (API version 7.9)
[    2.380184] ACPI: processor limited to max C-state 1
[    2.380382] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.380459] processor ACPI0007:00: registered as cooling_device0
[    2.380659] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.380733] processor ACPI0007:01: registered as cooling_device1
[    2.384323] thermal LNXTHERM:01: registered as thermal_zone0
[    2.385691] ACPI: Thermal Zone [THRM] (48 C)
[    3.042654] usbcore: registered new interface driver usbfs
[    3.042696] usbcore: registered new interface driver hub
[    3.042765] usbcore: registered new device driver usb
[    3.043045] No dock devices found.
[    3.085127] SCSI subsystem initialized
[    3.122757] libata version 3.00 loaded.
[    3.125178] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.125884] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    3.125899] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    3.125906] forcedeth 0000:00:14.0: setting latency timer to 64
[    3.125942] nv_probe: set workaround bit for reversed mac addr
[    3.159423] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.645070] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:78:2b:5e
[    3.645076] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    3.646864] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    3.646879] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    3.646895] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    3.646899] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.646987] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.647024] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    3.703346] usb usb1: configuration #1 chosen from 1 choice
[    3.703384] hub 1-0:1.0: USB hub found
[    3.703399] hub 1-0:1.0: 8 ports detected
[    4.017709] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.017717] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    4.017733] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    4.017737] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    4.017794] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    4.017836] ehci_hcd 0000:00:0b.1: debug port 1
[    4.017842] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    4.017852] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    4.400278] usb 1-4: new full speed USB device using ohci_hcd and address 2
[    4.528301] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.528498] usb usb2: configuration #1 chosen from 1 choice
[    4.528536] hub 2-0:1.0: USB hub found
[    4.528549] hub 2-0:1.0: 8 ports detected
[    4.656360] hub 1-0:1.0: unable to enumerate USB device on port 4
[    4.784744] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    4.785945] sata_nv 0000:00:0e.0: version 3.5
[    4.785955] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    4.786521] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    4.786536] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    4.786540] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    4.786597] sata_nv 0000:00:0e.0: setting latency timer to 64
[    4.786811] scsi0 : sata_nv
[    4.788342] scsi1 : sata_nv
[    4.788606] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    4.788611] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    5.552673] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.681005] ata1.00: ATA-7: ST98823AS, 7.24, max UDMA/100
[    5.681010] ata1.00: 156301488 sectors, multi 16: LBA48 
[    5.936774] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    5.937144] ata1.00: configured for UDMA/100
[    6.331889] ata2: SATA link down (SStatus 0 SControl 300)
[    6.331973] isa bounce pool size: 16 pages
[    6.332081] scsi 0:0:0:0: Direct-Access     ATA      ST98823AS        7.24 PQ: 0 ANSI: 5
[    6.338727] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    6.338744] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    6.338924] pata_amd 0000:00:0d.0: version 0.3.10
[    6.338985] pata_amd 0000:00:0d.0: setting latency timer to 64
[    6.390893] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[c8000000-c80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.394928] scsi2 : pata_amd
[    6.398342] scsi3 : pata_amd
[    6.399476] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    6.399480] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    6.399687] usb 2-4: configuration #1 chosen from 1 choice
[    6.705555] ata3.00: ATAPI: HL-DT-ST DVDRAM GMA-4082N, HQ04, max MWDMA2
[    6.705571] ata3: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    6.961645] ata3.00: configured for MWDMA2
[    6.962042] ata4: port disabled. ignoring.
[    6.965895] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4082N HQ04 PQ: 0 ANSI: 5
[    6.979111] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.979163] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[    7.006053] Driver 'sd' needs updating - please use bus_type methods
[    7.006192] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.006221] sd 0:0:0:0: [sda] Write Protect is off
[    7.006224] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.006272] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.006363] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.006388] sd 0:0:0:0: [sda] Write Protect is off
[    7.006391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.006435] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.006441]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.018248]  sda1 sda2 < sda5 >
[    7.044712] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.065471] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.065479] Uniform CD-ROM driver Revision: 3.20
[    7.065625] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    7.163428] usb 1-6: new low speed USB device using ohci_hcd and address 3
[    7.401987] PM: Starting manual resume from disk
[    7.401992] PM: Resume from partition 8:5
[    7.401994] PM: Checking hibernation image.
[    7.402244] PM: Resume from disk failed.
[    7.406674] usb 1-6: configuration #1 chosen from 1 choice
[    7.441085] usbcore: registered new interface driver hiddev
[    7.447808] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
[    7.487151] kjournald starting.  Commit interval 5 seconds
[    7.487174] EXT3-fs: mounted filesystem with ordered data mode.
[    7.493763] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-6
[    7.493813] usbcore: registered new interface driver usbhid
[    7.495877] usbhid: v2.6:USB HID core driver
[    7.696369] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc00099e2ad00]
[   13.954110] udevd version 124 started
[   14.358745] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   14.377048] ACPI: Power Button (FF) [PWRF]
[   14.377220] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   14.409072] ACPI: Power Button (CM) [PWRB]
[   14.409227] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   14.441045] ACPI: Sleep Button (CM) [SLPB]
[   14.441298] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   14.441761] ACPI: Lid Switch [LID]
[   14.442949] ACPI: AC Adapter [ACAD] (on-line)
[   14.536228] ACPI: WMI: Mapper loaded
[   14.905553] ACPI: Battery Slot [BAT0] (battery present)
[   15.389027] acpi device:24: registered as cooling_device2
[   15.389375] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input7
[   15.420060] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   15.424801] acpi device:2a: registered as cooling_device3
[   15.425179] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/device:28/input/input8
[   15.445032] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.487446] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.540454] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.639741] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   15.639766] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   15.796961] ricoh-mmc: Ricoh MMC Controller disabling driver
[   15.796965] ricoh-mmc: Copyright(c) Philip Langdale
[   15.797016] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   15.797034] ricoh-mmc: Controller is now disabled.
[   15.924445] sdhci: Secure Digital Host Controller Interface driver
[   15.924449] sdhci: Copyright(c) Pierre Ossman
[   16.059030] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   16.059604] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   16.059618] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   16.062703] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   16.138575] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   16.273694] Linux video capture interface: v2.00
[   16.446059] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   16.447953] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb2/2-4/2-4:1.0/input/input10
[   16.652284] usbcore: registered new interface driver uvcvideo
[   16.652290] USB Video Class driver (v0.1.0)
[   16.826575] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   16.826591] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   16.826631] HDA Intel 0000:00:10.1: setting latency timer to 64
[   17.112080] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   17.174364] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   19.038968] lp: driver loaded but no devices found
[   19.336124] Adding 2996080k swap on /dev/sda5.  Priority:-1 extents:1 across:2996080k
[   19.905265] EXT3 FS on sda1, internal journal
[   20.983441] type=1505 audit(1226776734.207:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4401
[   21.190322] type=1505 audit(1226776734.415:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4406
[   21.190575] type=1505 audit(1226776734.415:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4406
[   21.361262] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.409864] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (2 cpu cores) (version 2.20.00)
[   22.409934] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[   22.409938] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   23.265436] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   23.469371] ppdev: user-space parallel port driver
[   26.004024] Clocksource tsc unstable (delta = -132908439 ns)
[   26.072033] Bluetooth: Core ver 2.13
[   26.076662] NET: Registered protocol family 31
[   26.076675] Bluetooth: HCI device and connection manager initialized
[   26.076684] Bluetooth: HCI socket layer initialized
[   26.103971] Bluetooth: L2CAP ver 2.11
[   26.103979] Bluetooth: L2CAP socket layer initialized
[   26.130219] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.130236] Bluetooth: BNEP filters: protocol multicast
[   26.147325] Bluetooth: RFCOMM socket layer initialized
[   26.147364] Bluetooth: RFCOMM TTY layer initialized
[   26.147370] Bluetooth: RFCOMM ver 1.10
[   26.175625] Bridge firewalling registered
[   26.183686] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   26.212358] Bluetooth: SCO (Voice Link) ver 0.6
[   26.212382] Bluetooth: SCO socket layer initialized
[   30.390590] eth0: no link during initialization.
[   52.431993] canberra-gtk-pl[5724]: segfault at 101098d78 ip 00007f75d7940988 sp 00007fffe4b190a0 error 4 in libc-2.8.90.so[7f75d78c5000+169000]
[   58.995624] CPU0 attaching NULL sched-domain.
[   58.995666] CPU1 attaching NULL sched-domain.
[   59.015466] CPU0 attaching sched-domain:
[   59.015490]  domain 0: span 0-1 level CPU
[   59.015497]   groups: 0 1
[   59.015508]   domain 1: span 0-1 level NODE
[   59.015514]    groups: 0-1
[   59.015527] CPU1 attaching sched-domain:
[   59.015532]  domain 0: span 0-1 level CPU
[   59.015537]   groups: 1 0
[   59.015546]   domain 1: span 0-1 level NODE
[   59.015551]    groups: 0-1
[   70.365274] eth0: link up.
[   70.547989] NET: Registered protocol family 17
[   80.905569] NET: Registered protocol family 10
[   80.908721] lo: Disabled Privacy Extensions
[   91.209039] eth0: no IPv6 routers present
[  125.806678] type=1503 audit(1226773247.100:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6030/net/" pid=6030 profile="/usr/sbin/cupsd"
[  126.855993] type=1503 audit(1226773248.148:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6034/net/" pid=6034 profile="/usr/sbin/cupsd"
[  126.856136] type=1503 audit(1226773248.152:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856152] type=1503 audit(1226773248.152:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856167] type=1503 audit(1226773248.152:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856184] type=1503 audit(1226773248.152:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856199] type=1503 audit(1226773248.152:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856215] type=1503 audit(1226773248.152:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  126.856230] type=1503 audit(1226773248.152:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
```

---

### Post by walkerk on 2008-11-16
Unfortunately I do not see your wlan NIC w/ errors in dmesg. I believe you are using Ubuntu 64bit? If so, give [[COLOR="DarkOrange"]this tutorial[/COLOR]]("http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html") a try. It seems to have worked for others... assuming you have an Atheros chip (most likely)

If you are having problems w/ the tutorial let me know. Hope this helps.

---

### Post by Janjaya on 2008-11-16
The install went very well. Had no trouble with that. But at the end, when I plugged the wired Internet connection out and restarted my computer. Until I tried to locate the Internet connection micro-icon and set it to wireless. I was unable to do that. Yes I use the 64bit version of Ubuntu, should I use the 32bit version?

I have nothing important on this laptop atm. So I can switch to 32bit if needed.

---

