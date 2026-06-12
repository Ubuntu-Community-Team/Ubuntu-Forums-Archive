---
title: "Problem with Wireless"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by Sicc on 2008-08-01
k guys, ive searched through quite alot of threads on here, and forgive me if i missed a solution to my problem, would be gratefull if u would point me to it.

I've just installed Ubuntu - dual boot, and its my first time using linux, but im a fast learner. My problem is that i cant access the internet, Ubuntu reads my wireless adapter fine (Belkin F5D7050), and my adapter can find a list of networks just fine aswell, but when i try connecting to MY network, i got a BTHomeHub btw, it wont connect to it, it connects fine to it on vista and always has, i have no clue to whats causing my problem. Will give any needed info.

any help will be much appreciated. Thanks.

---

### Post by pytheas22 on 2008-08-01
Please post the output of these commands:
```

lshw -C Network
lspci
iwlist scan
```

and tell us the name of your network.

Also, if your network is encrypted, could you disable the security temporarily to see if you're able to connect then, please?

---

### Post by Sicc on 2008-08-01
my network is BT Broadband, my Routers full name is 'BTHomeHub 72C9' , there was a WEP encryption, i disabled it just like u said, it still didnt connect, i used the commands you gave me, this is what i got:

lshw -C Network, i get this:
```

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:78:7b:ea
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

lspci, i get this:

```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)

```

iwlist scan, i get this:

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:68:4B:09:3D
                    ESSID:"BTHomeHub-72C9"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/100  Signal level=-65 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000000bb71d57
          Cell 02 - Address: 00:1B:BF:22:76:0B
                    ESSID:"SKY30218"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/100  Signal level=-75 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000147c0bd6b47
          Cell 03 - Address: 00:18:F6:94:15:95
                    ESSID:"BTHomeHub-F289"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/100  Signal level=-81 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000100eb01f099
          Cell 04 - Address: 00:18:F6:AC:E0:59
                    ESSID:"BTHomeHub-5BF6"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=49/100  Signal level=-62 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000004322fdd7a1d

```

---

### Post by pytheas22 on 2008-08-02
Thanks for the information.

First, you may want to see if using wicd, an alternative connection manager, would make a difference.  You can download the installer from [here]("https://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=voxel&filename=wicd_1.4.2-1-all.deb&32524844").  After it's downloaded, run this command:
```

sudo apt-get remove network-manager
```

Then double-click on the wicd installer to install it.  After that, you can find it in the Applications>Internet menu.  Sometimes wicd does a better job of connecting than Network Manager; it just may solve your problem.

If wicd doesn't help, please post the output of:
```

lsusb
```

Then try to connect a couple of times to your network (with encryption turned off).  Immediately after it has cycled through and failed, run this command:
```

dmesg
```

and please post all of the output here.  It's going to be very long but it's useful.

---

### Post by Sicc on 2008-08-02
Unfortunately, wicd didn't help, the outputs i got from those commands were:

lsusb:

```

Bus 002 Device 006: ID 13fe:1e21 Kingston Technology Company Inc. 
Bus 002 Device 004: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 001 Device 002: ID 06a3:8021 Saitek PLC 
Bus 001 Device 001: ID 0000:0000  

```


dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=C6E8BAE4E8BAD243 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfef0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bfef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfef3000 - 00000000bff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786160) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7410 checksum 0
[    0.000000] ACPI: RSDP 000F7410, 0024 (r2 NEC CI)
[    0.000000] ACPI: XSDT BFEF30C0, 0054 (r1 PacBel PBDTNB00 42302E31 AWRD        0)
[    0.000000] ACPI: FACP BFEF8E40, 00F4 (r3 PacBel PBDTNB00 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT BFEF3240, 5BB5 (r1 PacBel PBDTNB00     1000 MSFT  100000E)
[    0.000000] ACPI: FACS BFEF0000, 0040
[    0.000000] ACPI: SLIC BFEF9040, 0176 (r1 PacBel PBDTNB00 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT BFEF9200, 028A (r1 PacBel PBDTNB00        1  LTP        1)
[    0.000000] ACPI: HPET BFEF9500, 0038 (r1 PacBel PBDTNB00 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG BFEF9580, 003C (r1 PacBel PBDTNB00 42302E31 AWRD        0)
[    0.000000] ACPI: APIC BFEF8F80, 007C (r1 PacBel PBDTNB00 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 2 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bfef0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786160) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bfef0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   786160
[    0.000000] On node 0 totalpages: 786063
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1221 pages reserved
[    0.000000]   DMA zone: 2722 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10692 pages used for memmap
[    0.000000]   DMA32 zone: 771372 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bff00000:30100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 774094
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=C6E8BAE4E8BAD243 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   37.583945] Marking TSC unstable due to TSCs unsynchronized
[   37.583946] time.c: Detected 2612.036 MHz processor.
[   37.585531] Console: colour VGA+ 80x25
[   37.585534] console [tty0] enabled
[   37.585547] Checking aperture...
[   37.585549] CPU 0: aperture @ 304000000 size 32 MB
[   37.585550] Aperture too small (32 MB)
[   37.591347] No AGP bridge found
[   37.625897] Memory: 3087664k/3144640k available (2489k kernel code, 56588k reserved, 1318k data, 320k init)
[   37.625939] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   37.705919] Calibrating delay using timer specific routine.. 5229.03 BogoMIPS (lpj=10458073)
[   37.705950] Security Framework initialized
[   37.705956] SELinux:  Disabled at boot.
[   37.705968] AppArmor: AppArmor initialized
[   37.705971] Failure registering capabilities with primary security module.
[   37.706237] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   37.709537] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   37.711114] Mount-cache hash table entries: 256
[   37.711241] Initializing cgroup subsys ns
[   37.711245] Initializing cgroup subsys cpuacct
[   37.711256] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   37.711258] CPU: L2 Cache: 512K (64 bytes/line)
[   37.711260] CPU 0/0 -> Node 0
[   37.711261] CPU: Physical Processor ID: 0
[   37.711262] CPU: Processor Core ID: 0
[   37.711285] SMP alternatives: switching to UP code
[   37.711846] Early unpacking initramfs... done
[   37.977527] ACPI: Core revision 20070126
[   37.977579] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   38.022102] Using local APIC timer interrupts.
[   38.060386] APIC timer calibration result 12557858
[   38.060388] Detected 12.557 MHz APIC timer.
[   38.060474] SMP alternatives: switching to SMP code
[   38.060924] Booting processor 1/2 APIC 0x1
[   38.071096] Initializing CPU#1
[   38.148480] Calibrating delay using timer specific routine.. 5224.11 BogoMIPS (lpj=10448223)
[   38.148486] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   38.148487] CPU: L2 Cache: 512K (64 bytes/line)
[   38.148489] CPU 1/1 -> Node 0
[   38.148491] CPU: Physical Processor ID: 0
[   38.148491] CPU: Processor Core ID: 1
[   38.148576] AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 01
[   38.148531] Brought up 2 CPUs
[   38.148631] CPU0 attaching sched-domain:
[   38.148633]  domain 0: span 03
[   38.148634]   groups: 01 02
[   38.148636]   domain 1: span 03
[   38.148637]    groups: 03
[   38.148639] CPU1 attaching sched-domain:
[   38.148640]  domain 0: span 03
[   38.148641]   groups: 02 01
[   38.148643]   domain 1: span 03
[   38.148644]    groups: 03
[   38.148850] net_namespace: 120 bytes
[   38.149188] Time:  5:23:01  Date: 08/02/08
[   38.149222] NET: Registered protocol family 16
[   38.149389] ACPI: bus type pci registered
[   38.149450] PCI: Using configuration type 1
[   38.150585] ACPI: EC: Look up EC in DSDT
[   38.155343] ACPI: Interpreter enabled
[   38.155345] ACPI: (supports S0 S3 S4 S5)
[   38.155357] ACPI: Using IOAPIC for interrupt routing
[   38.162537] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.163041] PCI: Transparent bridge - 0000:00:04.0
[   38.163228] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   38.163444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   38.207823] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.207972] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208119] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208266] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208421] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208568] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208714] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.208862] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[   38.209008] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.209155] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.209302] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   38.209450] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 *7 9 10 11 14 15)
[   38.209597] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[   38.209743] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.209891] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   38.210038] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   38.210184] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.210331] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   38.210477] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   38.210659] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   38.210837] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   38.211016] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   38.211191] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   38.211362] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   38.211533] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   38.211703] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   38.211873] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[   38.212044] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0, disabled.
[   38.212215] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   38.212394] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   38.212565] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   38.212734] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   38.212904] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   38.213073] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   38.213243] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   38.213413] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   38.213583] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   38.213753] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   38.213875] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.213898] pnp: PnP ACPI init
[   38.213906] ACPI: bus type pnp registered
[   38.217090] pnpacpi: exceeded the max number of mem resources: 12
[   38.217179] pnp: PnP ACPI: found 10 devices
[   38.217181] ACPI: ACPI bus type pnp unregistered
[   38.217378] PCI: Using ACPI for IRQ routing
[   38.217382] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.228416] NET: Registered protocol family 8
[   38.228418] NET: Registered protocol family 20
[   38.228485] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   38.228488] hpet0: 3 32-bit timers, 25000000 Hz
[   38.229547] AppArmor: AppArmor Filesystem Enabled
[   38.232380] Time: hpet clocksource has been installed.
[   38.232391] Switched to high resolution mode on CPU 0
[   38.232592] Switched to high resolution mode on CPU 1
[   38.240377] system 00:01: ioport range 0x1000-0x107f has been reserved
[   38.240380] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   38.240382] system 00:01: ioport range 0x1400-0x147f has been reserved
[   38.240384] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   38.240386] system 00:01: ioport range 0x1800-0x187f has been reserved
[   38.240389] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   38.240394] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   38.240396] system 00:02: ioport range 0x800-0x87f has been reserved
[   38.240399] system 00:02: ioport range 0x290-0x297 has been reserved
[   38.240407] system 00:08: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   38.240412] system 00:09: iomem range 0xd0000-0xd3fff has been reserved
[   38.240414] system 00:09: iomem range 0xd5800-0xd7fff has been reserved
[   38.240416] system 00:09: iomem range 0xf0000-0xfbfff could not be reserved
[   38.240419] system 00:09: iomem range 0xfc000-0xfffff could not be reserved
[   38.240421] system 00:09: iomem range 0xfefff000-0xfefff0ff has been reserved
[   38.240423] system 00:09: iomem range 0xbfef0000-0xbfefffff could not be reserved
[   38.240426] system 00:09: iomem range 0xffff0000-0xffffffff has been reserved
[   38.240428] system 00:09: iomem range 0x0-0x9ffff could not be reserved
[   38.240430] system 00:09: iomem range 0x100000-0xbfeeffff could not be reserved
[   38.240433] system 00:09: iomem range 0x0-0x0 could not be reserved
[   38.240435] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[   38.240438] system 00:09: iomem range 0xfee00000-0xfeefffff could not be reserved
[   38.240757] PCI: Bridge: 0000:00:04.0
[   38.240759]   IO window: c000-cfff
[   38.240762]   MEM window: fde00000-fdefffff
[   38.240765]   PREFETCH window: fdf00000-fdffffff
[   38.240767] PCI: Bridge: 0000:00:09.0
[   38.240769]   IO window: b000-bfff
[   38.240770]   MEM window: f8000000-fbffffff
[   38.240772]   PREFETCH window: e0000000-efffffff
[   38.240774] PCI: Bridge: 0000:00:0b.0
[   38.240775]   IO window: a000-afff
[   38.240777]   MEM window: fdd00000-fddfffff
[   38.240779]   PREFETCH window: fdc00000-fdcfffff
[   38.240781] PCI: Bridge: 0000:00:0c.0
[   38.240782]   IO window: 9000-9fff
[   38.240784]   MEM window: fdb00000-fdbfffff
[   38.240785]   PREFETCH window: fda00000-fdafffff
[   38.240794] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   38.240803] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   38.240808] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   38.240813] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   38.240822] NET: Registered protocol family 2
[   38.276494] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   38.278095] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   38.284572] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   38.285354] TCP: Hash tables configured (established 524288 bind 65536)
[   38.285357] TCP reno registered
[   38.296491] checking if image is initramfs... it is
[   38.819862] Freeing initrd memory: 8456k freed
[   38.826768] audit: initializing netlink socket (disabled)
[   38.826779] audit(1217654581.212:1): initialized
[   38.828552] VFS: Disk quotas dquot_6.5.1
[   38.828620] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   38.828735] io scheduler noop registered
[   38.828737] io scheduler anticipatory registered
[   38.828738] io scheduler deadline registered
[   38.828823] io scheduler cfq registered (default)
[   38.828851] pci 0000:00:00.0: Enabling HT MSI Mapping
[   38.844744] pci 0000:00:04.0: Enabling HT MSI Mapping
[   38.844762] pci 0000:00:05.0: Enabling HT MSI Mapping
[   38.844785] pci 0000:00:07.0: Enabling HT MSI Mapping
[   38.844797] pci 0000:00:08.0: Enabling HT MSI Mapping
[   38.844809] pci 0000:00:09.0: Enabling HT MSI Mapping
[   38.844821] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   38.844833] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   38.844851] Boot video device is 0000:02:00.0
[   38.844994] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   38.845012] assign_interrupt_mode Found MSI capability
[   38.845028] Allocate Port Service[0000:00:09.0:pcie00]
[   38.845083] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   38.845100] assign_interrupt_mode Found MSI capability
[   38.845112] Allocate Port Service[0000:00:0b.0:pcie00]
[   38.845158] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   38.845175] assign_interrupt_mode Found MSI capability
[   38.845187] Allocate Port Service[0000:00:0c.0:pcie00]
[   38.868624] Real Time Clock Driver v1.12ac
[   38.868823] hpet_resources: 0xfefff000 is busy
[   38.868843] Linux agpgart interface v0.102
[   38.868845] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.869730] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.869785] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   38.869894] PNP: No PS/2 controller found. Probing ports directly.
[   38.903637] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[   38.903640] If AUX port is really absent please use the 'i8042.noaux' option.
[   39.152343] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.164301] mice: PS/2 mouse device common for all mice
[   39.164333] cpuidle: using governor ladder
[   39.164335] cpuidle: using governor menu
[   39.164465] NET: Registered protocol family 1
[   39.164552] registered taskstats version 1
[   39.164658]   Magic number: 4:511:364
[   39.164801] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   39.164803] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   39.164805] EDD information not available.
[   39.164812] Freeing unused kernel memory: 320k freed
[   40.336159] fuse init (API version 7.9)
[   40.346855] ACPI: Fan [FAN] (on)
[   40.352000] ACPI: Thermal Zone [THRM] (40 C)
[   40.501450] usbcore: registered new interface driver usbfs
[   40.501471] usbcore: registered new interface driver hub
[   40.501492] usbcore: registered new device driver usb
[   40.514212] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.514567] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   40.514576] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   40.514757] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.514763] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   40.514983] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   40.515005] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   40.574179] usb usb1: configuration #1 chosen from 1 choice
[   40.574197] hub 1-0:1.0: USB hub found
[   40.574204] hub 1-0:1.0: 8 ports detected
[   40.681252] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   40.681263] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   40.681472] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   40.681478] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   40.681529] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   40.681557] ehci_hcd 0000:00:02.1: debug port 1
[   40.681560] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   40.681571] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[   40.694533] SCSI subsystem initialized
[   40.699499] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.699598] usb usb2: configuration #1 chosen from 1 choice
[   40.699617] hub 2-0:1.0: USB hub found
[   40.699624] hub 2-0:1.0: 8 ports detected
[   40.757722] libata version 3.00 loaded.
[   40.804242] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   40.804578] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   40.804588] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   40.804593] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   41.324375] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:17:31:75:15:db
[   41.324380] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   41.324572] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.324895] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   41.324905] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   41.324917] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   41.324923] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   41.327335] pata_amd 0000:00:06.0: version 0.3.10
[   41.327378] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.329896] scsi0 : pata_amd
[   41.330015] scsi1 : pata_amd
[   41.330508] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   41.330510] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   41.648221] ata1.00: ATAPI: Optiarc DVD RW AD-5170A, 1.52, max UDMA/66
[   41.828703] ata1.00: configured for UDMA/66
[   41.828737] ata2: port disabled. ignoring.
[   41.829692] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.52 PQ: 0 ANSI: 5
[   41.830122] sata_nv 0000:00:08.0: version 3.5
[   41.830136] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   41.830331] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   41.832214] scsi2 : sata_nv
[   41.832342] scsi3 : sata_nv
[   41.832492] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   41.832494] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   41.839893] usb 2-4: new high speed USB device using ehci_hcd and address 4
[   42.144767] usb 2-4: configuration #1 chosen from 1 choice
[   42.308342] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   42.355768] ata3.00: ATA-7: ST3160212AS, 3.AAE, max UDMA/133
[   42.355772] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   42.422389] ata3.00: configured for UDMA/133
[   42.687870] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   42.739766] ata4: SATA link down (SStatus 0 SControl 300)
[   42.750240] scsi 2:0:0:0: Direct-Access     ATA      ST3160212AS      3.AA PQ: 0 ANSI: 5
[   42.758712] Driver 'sr' needs updating - please use bus_type methods
[   42.762572] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   42.762577] Uniform CD-ROM driver Revision: 3.20
[   42.762630] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   42.767142] Driver 'sd' needs updating - please use bus_type methods
[   42.767222] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   42.767231] sd 2:0:0:0: [sda] Write Protect is off
[   42.767233] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.767243] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.767284] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   42.767289] sd 2:0:0:0: [sda] Write Protect is off
[   42.767291] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.767300] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.767303]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   42.767496] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   42.786887]  sda1 sda2
[   42.786961] sd 2:0:0:0: [sda] Attached SCSI disk
[   42.918068] usb 1-1: configuration #1 chosen from 1 choice
[   43.223803] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   43.439032] usb 1-2: configuration #1 chosen from 1 choice
[   43.714477] loop: module loaded
[   43.738399] kjournald starting.  Commit interval 5 seconds
[   43.738503] EXT3-fs: mounted filesystem with ordered data mode.
[   43.744728] usb 1-8: new full speed USB device using ohci_hcd and address 4
[   43.958993] usb 1-8: configuration #1 chosen from 1 choice
[   43.961916] usbcore: registered new interface driver hiddev
[   43.972139] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input1
[   43.980736] input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:02.0-1
[   44.009966] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.1/input/input2
[   44.020727] input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:02.0-1
[   44.027022] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input3
[   44.036703] input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2
[   44.036717] usbcore: registered new interface driver usbhid
[   44.036720] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   49.623550] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   50.027770] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.048081] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   50.048096] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   50.053789] shpchp: Unknown symbol acpi_run_oshp
[   50.053839] shpchp: Unknown symbol pci_hp_change_slot_info
[   50.053895] shpchp: Unknown symbol pci_hp_register
[   50.054041] shpchp: Unknown symbol pci_hp_deregister
[   50.054152] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   50.065919] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.121117] input: Power Button (FF) as /devices/virtual/input/input5
[   50.190812] ACPI: Power Button (FF) [PWRF]
[   50.190865] input: Power Button (CM) as /devices/virtual/input/input6
[   50.238849] ACPI: Power Button (CM) [PWRB]
[   50.855661] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   50.855665] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 23 (level, low) -> IRQ 23
[   50.855817] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   50.893445] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   51.161238] usbcore: registered new interface driver libusual
[   51.180883] Initializing USB Mass Storage driver...
[   51.182558] scsi4 : SCSI emulation for USB Mass Storage devices
[   51.182656] usbcore: registered new interface driver usb-storage
[   51.182661] USB Mass Storage support registered.
[   51.182788] usb-storage: device found at 4
[   51.182790] usb-storage: waiting for device to settle before scanning
[   51.465610] phy0: Selected rate control algorithm 'simple'
[   51.532539] usbcore: registered new interface driver rt2500usb
[   51.547280] usbcore: registered new interface driver rt73usb
[   51.573562] usbcore: registered new interface driver prism54usb
[   52.105098] lp: driver loaded but no devices found
[   52.797477] EXT3 FS on loop0, internal journal
[   56.187869] usb-storage: device scan complete
[   56.194860] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   56.201851] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   56.208850] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   56.215849] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   56.226917] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   56.226953] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   56.237939] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   56.237977] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   56.248928] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   56.248966] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   56.259914] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   56.259952] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   59.359257] Adding 976552k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:976552k
[   59.744593] ip_tables: (C) 2000-2006 Netfilter Core Team
[   60.048832] No dock devices found.
[   60.384003] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
[   60.383971] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x9
[   60.383975] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
[   60.383977] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
[   60.383978] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
[   60.383980] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
[   60.383981] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[   61.126060] ppdev: user-space parallel port driver
[   61.277693] audit(1217651004.300:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5176 profile="/usr/sbin/cupsd" namespace="default"
[   62.082906] eth0: no link during initialization.
[   62.144899] Bluetooth: Core ver 2.11
[   62.145169] NET: Registered protocol family 31
[   62.145171] Bluetooth: HCI device and connection manager initialized
[   62.145175] Bluetooth: HCI socket layer initialized
[   62.164937] Bluetooth: L2CAP ver 2.9
[   62.164941] Bluetooth: L2CAP socket layer initialized
[   62.184100] Bluetooth: RFCOMM socket layer initialized
[   62.184118] Bluetooth: RFCOMM TTY layer initialized
[   62.184120] Bluetooth: RFCOMM ver 1.8
[   62.430695] Clocksource tsc unstable (delta = -152627631 ns)
[   68.358438] NET: Registered protocol family 10
[   68.358622] lo: Disabled Privacy Extensions
[   68.359016] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.359308] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.004775] usb 2-5: new high speed USB device using ehci_hcd and address 6
[   87.060072] usb 2-5: configuration #1 chosen from 1 choice
[   87.060197] scsi5 : SCSI emulation for USB Mass Storage devices
[   87.060294] usb-storage: device found at 6
[   87.060296] usb-storage: waiting for device to settle before scanning
[   88.983065] usb-storage: device scan complete
[   88.994981] scsi 5:0:0:0: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
[   88.995216] scsi 5:0:0:1: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
[   89.241871] sd 5:0:0:0: [sdf] 4096 512-byte hardware sectors (2 MB)
[   89.242110] sd 5:0:0:0: [sdf] Write Protect is off
[   89.242113] sd 5:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   89.242116] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[   89.243361] sd 5:0:0:0: [sdf] 4096 512-byte hardware sectors (2 MB)
[   89.243601] sd 5:0:0:0: [sdf] Write Protect is off
[   89.243604] sd 5:0:0:0: [sdf] Mode Sense: 23 00 00 00
[   89.243606] sd 5:0:0:0: [sdf] Assuming drive cache: write through
[   89.243610]  sdf: sdf1
[   89.259613] sd 5:0:0:0: [sdf] Attached SCSI removable disk
[   89.259647] sd 5:0:0:0: Attached scsi generic sg6 type 0
[   89.261203] sd 5:0:0:1: [sdg] 1953792 512-byte hardware sectors (1000 MB)
[   89.261445] sd 5:0:0:1: [sdg] Write Protect is off
[   89.261449] sd 5:0:0:1: [sdg] Mode Sense: 23 00 00 00
[   89.261451] sd 5:0:0:1: [sdg] Assuming drive cache: write through
[   89.262882] sd 5:0:0:1: [sdg] 1953792 512-byte hardware sectors (1000 MB)
[   89.263122] sd 5:0:0:1: [sdg] Write Protect is off
[   89.263127] sd 5:0:0:1: [sdg] Mode Sense: 23 00 00 00
[   89.263129] sd 5:0:0:1: [sdg] Assuming drive cache: write through
[   89.263133]  sdg: sdg1
[   89.263470] sd 5:0:0:1: [sdg] Attached SCSI removable disk
[   89.263505] sd 5:0:0:1: Attached scsi generic sg7 type 0
[  151.259569] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  167.663402] eth0: no link during initialization.
[  167.666526] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  167.742420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  168.202259] NET: Registered protocol family 17
[  194.321111] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  195.086772] wlan0: Initial auth_alg=0
[  195.086777] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  195.087447] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  195.087451] wlan0: authenticated
[  195.087453] wlan0: associate with AP 00:1d:68:4b:09:3d
[  195.088400] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  195.088404] wlan0: associated
[  195.088406] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  195.088752] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  195.088754] wlan0: failed to set TX queue parameters for queue 2
[  195.088756] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  195.088759] wlan0: failed to set TX queue parameters for queue 3
[  195.088760] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  195.088763] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  195.091581] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  199.131434] wlan0: no IPv6 routers present
[  216.044311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  216.048501] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  216.053307] wlan0: deauthenticate(reason=3)
[  216.315631] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  216.632296] wlan0: Initial auth_alg=0
[  216.632302] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  216.632948] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  216.632951] wlan0: authenticated
[  216.632953] wlan0: associate with AP 00:1d:68:4b:09:3d
[  216.633903] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  216.633906] wlan0: associated
[  216.633909] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  216.634253] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  216.634256] wlan0: failed to set TX queue parameters for queue 2
[  216.634258] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  216.634260] wlan0: failed to set TX queue parameters for queue 3
[  216.634261] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  216.634264] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  216.637042] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  221.179495] wlan0: no IPv6 routers present
[  349.487017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  349.497242] wlan0: deauthenticate(reason=3)
[  349.624296] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  350.318387] wlan0: Initial auth_alg=0
[  350.318391] wlan0: authenticate with AP 00:18:f6:ac:e0:59
[  350.319053] wlan0: RX authentication from 00:18:f6:ac:e0:59 (alg=0 transaction=2 status=0)
[  350.319055] wlan0: authenticated
[  350.319057] wlan0: associate with AP 00:18:f6:ac:e0:59
[  350.319961] wlan0: RX AssocResp from 00:18:f6:ac:e0:59 (capab=0x411 status=0 aid=1)
[  350.319964] wlan0: associated
[  350.319966] wlan0: switched to short barker preamble (BSSID=00:18:f6:ac:e0:59)
[  350.320506] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  350.320508] wlan0: failed to set TX queue parameters for queue 2
[  350.320510] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  350.320512] wlan0: failed to set TX queue parameters for queue 3
[  350.320514] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  350.320516] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  350.323351] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  350.950835] WEP decrypt failed (ICV)
[  350.952312] WEP decrypt failed (ICV)
[  350.953611] WEP decrypt failed (ICV)
[  351.002822] wlan0: deauthenticate(reason=3)
[  352.224054] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  357.961653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  358.677420] wlan0: Initial auth_alg=0
[  358.677425] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  358.678038] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  358.678041] wlan0: authenticated
[  358.678043] wlan0: associate with AP 00:1d:68:4b:09:3d
[  358.679042] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  358.679045] wlan0: associated
[  358.679047] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  358.679390] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  358.679393] wlan0: failed to set TX queue parameters for queue 2
[  358.679395] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  358.679396] wlan0: failed to set TX queue parameters for queue 3
[  358.679399] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  358.679400] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  358.682227] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  362.575063] wlan0: no IPv6 routers present
[  390.419709] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  390.432099] wlan0: deauthenticate(reason=3)
[  390.665229] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  390.982511] wlan0: Initial auth_alg=0
[  390.982516] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  390.983115] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  390.983118] wlan0: authenticated
[  390.983120] wlan0: associate with AP 00:1d:68:4b:09:3d
[  390.984600] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  390.984603] wlan0: associated
[  390.984605] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  390.985094] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  390.985097] wlan0: failed to set TX queue parameters for queue 2
[  390.985099] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  390.985101] wlan0: failed to set TX queue parameters for queue 3
[  390.985103] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  390.985105] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  390.987891] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  391.977361] wlan0: deauthenticate(reason=3)
[  395.743566] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  396.485184] wlan0: Initial auth_alg=0
[  396.485189] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  396.485842] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  396.485844] wlan0: authenticated
[  396.485846] wlan0: associate with AP 00:1d:68:4b:09:3d
[  396.486799] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  396.486801] wlan0: associated
[  396.486804] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  396.487293] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  396.487295] wlan0: failed to set TX queue parameters for queue 2
[  396.487297] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  396.487299] wlan0: failed to set TX queue parameters for queue 3
[  396.487301] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  396.487303] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  396.490203] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  400.429146] wlan0: no IPv6 routers present
[  464.325875] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  464.331107] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  464.335682] wlan0: deauthenticate(reason=3)
[  464.464601] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  464.818386] wlan0: Initial auth_alg=0
[  464.818390] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  464.819008] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  464.819010] wlan0: authenticated
[  464.819012] wlan0: associate with AP 00:1d:68:4b:09:3d
[  464.820013] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  464.820015] wlan0: associated
[  464.820018] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  464.820504] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  464.820507] wlan0: failed to set TX queue parameters for queue 2
[  464.820509] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  464.820511] wlan0: failed to set TX queue parameters for queue 3
[  464.820513] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  464.820515] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  464.823315] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  468.973138] wlan0: no IPv6 routers present
[  523.561235] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  523.564021] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  523.575167] wlan0: deauthenticate(reason=3)
[  523.719040] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  524.327310] wlan0: Initial auth_alg=0
[  524.327316] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  524.327964] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  524.327967] wlan0: authenticated
[  524.327969] wlan0: associate with AP 00:1d:68:4b:09:3d
[  524.328924] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  524.328927] wlan0: associated
[  524.328929] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  524.329560] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  524.329563] wlan0: failed to set TX queue parameters for queue 2
[  524.329565] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  524.329567] wlan0: failed to set TX queue parameters for queue 3
[  524.329569] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  524.329571] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  524.332432] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  528.527991] wlan0: no IPv6 routers present
[  625.758041] gnome-terminal[5972] general protection rip:7f1aeca4df58 rsp:7ffff799bfb0 error:0
[  658.158048] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  658.171010] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  658.171071] wlan0: deauthenticate(reason=3)
[  658.471150] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  658.485591] wlan0: Initial auth_alg=0
[  658.485598] wlan0: authenticate with AP 00:18:f6:ac:e0:59
[  658.487371] wlan0: RX authentication from 00:18:f6:ac:e0:59 (alg=0 transaction=2 status=0)
[  658.487376] wlan0: authenticated
[  658.487378] wlan0: associate with AP 00:18:f6:ac:e0:59
[  658.488490] wlan0: Initial auth_alg=0
[  658.488495] wlan0: authenticate with AP 00:18:f6:ac:e0:59
[  658.489920] wlan0: association frame received from 00:18:f6:ac:e0:59, but not in associate state - ignored
[  658.497421] wlan0: RX authentication from 00:18:f6:ac:e0:59 (alg=0 transaction=2 status=0)
[  658.497427] wlan0: authenticated
[  658.497430] wlan0: associate with AP 00:18:f6:ac:e0:59
[  658.498304] wlan0: authentication frame received from 00:18:f6:ac:e0:59, but not in authenticate state - ignored
[  658.499214] wlan0: authentication frame received from 00:18:f6:ac:e0:59, but not in authenticate state - ignored
[  658.500056] wlan0: authentication frame received from 00:18:f6:ac:e0:59, but not in authenticate state - ignored
[  658.502666] wlan0: RX AssocResp from 00:18:f6:ac:e0:59 (capab=0x411 status=0 aid=1)
[  658.502672] wlan0: associated
[  658.502676] wlan0: switched to short barker preamble (BSSID=00:18:f6:ac:e0:59)
[  658.503566] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  658.503570] wlan0: failed to set TX queue parameters for queue 2
[  658.503572] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  658.503574] wlan0: failed to set TX queue parameters for queue 3
[  658.503575] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  658.503577] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  658.507015] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  664.320193] wlan0: no IPv6 routers present
[  665.886149] wlan0: deauthenticate(reason=3)
[  666.904552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  670.951130] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  671.062646] wlan0: Initial auth_alg=0
[  671.062651] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  671.063290] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  671.063293] wlan0: authenticated
[  671.063294] wlan0: associate with AP 00:1d:68:4b:09:3d
[  671.064306] wlan0: RX AssocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  671.064309] wlan0: associated
[  671.064313] wlan0: switched to short barker preamble (BSSID=00:1d:68:4b:09:3d)
[  671.064743] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  671.064747] wlan0: failed to set TX queue parameters for queue 2
[  671.064749] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  671.064752] wlan0: failed to set TX queue parameters for queue 3
[  671.064754] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  671.064756] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  671.067552] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  671.083925] wlan0: Initial auth_alg=0
[  671.083932] wlan0: authenticate with AP 00:1d:68:4b:09:3d
[  671.087960] wlan0: RX authentication from 00:1d:68:4b:09:3d (alg=0 transaction=2 status=0)
[  671.087964] wlan0: authenticated
[  671.087966] wlan0: associate with AP 00:1d:68:4b:09:3d
[  671.090076] wlan0: authentication frame received from 00:1d:68:4b:09:3d, but not in authenticate state - ignored
[  671.090085] wlan0: authentication frame received from 00:1d:68:4b:09:3d, but not in authenticate state - ignored
[  671.091898] wlan0: authentication frame received from 00:1d:68:4b:09:3d, but not in authenticate state - ignored
[  671.091905] wlan0: RX ReassocResp from 00:1d:68:4b:09:3d (capab=0x411 status=0 aid=1)
[  671.091907] wlan0: associated
[  671.091930] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  671.091932] wlan0: failed to set TX queue parameters for queue 2
[  671.091934] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  671.091935] wlan0: failed to set TX queue parameters for queue 3
[  671.091937] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  671.091939] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  675.967868] wlan0: no IPv6 routers present

```

---

### Post by Sicc on 2008-08-02
so... any ideas?

---

### Post by Sicc on 2008-08-02
i should aloso mention that when trying to connect it sticks on "Obtaining IP address" before failing, sometimes but rarely it manages to 'connect' but it shows my Lan IP asif its only connected to my Lan 'Connected to BTHomeHub-72C9 at 33 (ip: 192.168.1.65)', websites dont load when this happens

---

### Post by Sicc on 2008-08-02
mhmmm.... guess im prolly the only one with this problem since noone seems to be replying...

---

### Post by Sicc on 2008-08-02
bump

---

### Post by pytheas22 on 2008-08-02
> mhmmm.... guess im prolly the only one with this problem since noone seems to be replying...

I'll keep replying till the problem is fixed, but I'm not always at my computer :)

Anyway, with encryption on your router turned off, try running these commands and please post the output:
```

sudo iwconfig wlan0 mode managed channel 7 rate 11M essid "BTHomeHub-72C9"
sudo dhclient wlan0
```

This should connect you (basically this is what goes on in the background using wicd or Network Manager)--do you get an IP address this way at least--in other words, after running these commands, does:
```

ifconfig wlan0
```

mention an IP?  And if so, can you ping your router:
```

ping 192.168.1.1
```

---

### Post by Sicc on 2008-08-02
Thank You for your support, i really appreciate it.

the commands still havent helped yet.


sudo iwconfig wlan0 mode managed channel 7 rate 11M essid "BTHomeHub-72C9"
sudo dhclient wlan0

```

There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:78:7b:ea
Sending on   LPF/wlan0/00:11:50:78:7b:ea
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
Trying recorded lease 192.168.1.65
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.

--- 192.168.1.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.


```


ifconfig wlan0

```

wlan0     Link encap:Ethernet  HWaddr 00:11:50:78:7b:ea  
          inet6 addr: fe80::211:50ff:fe78:7bea/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3025 (2.9 KB)  TX bytes:14372 (14.0 KB)


```


ping 192.168.1.1

```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 169.254.8.152 icmp_seq=1 Destination Host Unreachable
From 169.254.8.152 icmp_seq=2 Destination Host Unreachable
From 169.254.8.152 icmp_seq=3 Destination Host Unreachable
From 169.254.8.152 icmp_seq=4 Destination Host Unreachable
From 169.254.8.152 icmp_seq=5 Destination Host Unreachable
From 169.254.8.152 icmp_seq=6 Destination Host Unreachable
From 169.254.8.152 icmp_seq=7 Destination Host Unreachable
From 169.254.8.152 icmp_seq=8 Destination Host Unreachable
From 169.254.8.152 icmp_seq=9 Destination Host Unreachable
From 169.254.8.152 icmp_seq=10 Destination Host Unreachable
From 169.254.8.152 icmp_seq=11 Destination Host Unreachable
From 169.254.8.152 icmp_seq=12 Destination Host Unreachable
From 169.254.8.152 icmp_seq=13 Destination Host Unreachable
From 169.254.8.152 icmp_seq=14 Destination Host Unreachable
From 169.254.8.152 icmp_seq=15 Destination Host Unreachable
From 169.254.8.152 icmp_seq=16 Destination Host Unreachable
From 169.254.8.152 icmp_seq=17 Destination Host Unreachable
From 169.254.8.152 icmp_seq=18 Destination Host Unreachable
From 169.254.8.152 icmp_seq=19 Destination Host Unreachable
From 169.254.8.152 icmp_seq=20 Destination Host Unreachable
From 169.254.8.152 icmp_seq=21 Destination Host Unreachable
From 169.254.8.152 icmp_seq=22 Destination Host Unreachable
From 169.254.8.152 icmp_seq=23 Destination Host Unreachable
From 169.254.8.152 icmp_seq=24 Destination Host Unreachable
From 169.254.8.152 icmp_seq=25 Destination Host Unreachable
From 169.254.8.152 icmp_seq=26 Destination Host Unreachable
From 169.254.8.152 icmp_seq=27 Destination Host Unreachable
From 169.254.8.152 icmp_seq=28 Destination Host Unreachable
From 169.254.8.152 icmp_seq=29 Destination Host Unreachable
From 169.254.8.152 icmp_seq=30 Destination Host Unreachable
From 169.254.8.152 icmp_seq=31 Destination Host Unreachable
From 169.254.8.152 icmp_seq=32 Destination Host Unreachable
From 169.254.8.152 icmp_seq=33 Destination Host Unreachable
From 169.254.8.152 icmp_seq=34 Destination Host Unreachable
From 169.254.8.152 icmp_seq=35 Destination Host Unreachable
From 169.254.8.152 icmp_seq=36 Destination Host Unreachable
From 169.254.8.152 icmp_seq=37 Destination Host Unreachable
From 169.254.8.152 icmp_seq=38 Destination Host Unreachable
From 169.254.8.152 icmp_seq=39 Destination Host Unreachable
From 169.254.8.152 icmp_seq=40 Destination Host Unreachable
From 169.254.8.152 icmp_seq=41 Destination Host Unreachable
From 169.254.8.152 icmp_seq=42 Destination Host Unreachable
From 169.254.8.152 icmp_seq=43 Destination Host Unreachable
From 169.254.8.152 icmp_seq=44 Destination Host Unreachable
From 169.254.8.152 icmp_seq=45 Destination Host Unreachable
From 169.254.8.152 icmp_seq=46 Destination Host Unreachable
From 169.254.8.152 icmp_seq=47 Destination Host Unreachable
From 169.254.8.152 icmp_seq=48 Destination Host Unreachable
From 169.254.8.152 icmp_seq=49 Destination Host Unreachable
From 169.254.8.152 icmp_seq=50 Destination Host Unreachable
From 169.254.8.152 icmp_seq=51 Destination Host Unreachable
From 169.254.8.152 icmp_seq=52 Destination Host Unreachable
From 169.254.8.152 icmp_seq=53 Destination Host Unreachable
From 169.254.8.152 icmp_seq=54 Destination Host Unreachable
From 169.254.8.152 icmp_seq=55 Destination Host Unreachable
From 169.254.8.152 icmp_seq=56 Destination Host Unreachable
From 169.254.8.152 icmp_seq=57 Destination Host Unreachable
From 169.254.8.152 icmp_seq=58 Destination Host Unreachable
From 169.254.8.152 icmp_seq=59 Destination Host Unreachable
From 169.254.8.152 icmp_seq=60 Destination Host Unreachable
From 169.254.8.152 icmp_seq=61 Destination Host Unreachable
From 169.254.8.152 icmp_seq=62 Destination Host Unreachable
From 169.254.8.152 icmp_seq=63 Destination Host Unreachable
From 169.254.8.152 icmp_seq=64 Destination Host Unreachable
From 169.254.8.152 icmp_seq=65 Destination Host Unreachable
From 169.254.8.152 icmp_seq=66 Destination Host Unreachable
From 169.254.8.152 icmp_seq=67 Destination Host Unreachable
From 169.254.8.152 icmp_seq=68 Destination Host Unreachable
From 169.254.8.152 icmp_seq=69 Destination Host Unreachable
From 169.254.8.152 icmp_seq=70 Destination Host Unreachable
From 169.254.8.152 icmp_seq=71 Destination Host Unreachable
From 169.254.8.152 icmp_seq=72 Destination Host Unreachable
From 169.254.8.152 icmp_seq=73 Destination Host Unreachable
From 169.254.8.152 icmp_seq=74 Destination Host Unreachable
From 169.254.8.152 icmp_seq=75 Destination Host Unreachable
From 169.254.8.152 icmp_seq=76 Destination Host Unreachable
From 169.254.8.152 icmp_seq=77 Destination Host Unreachable
From 169.254.8.152 icmp_seq=78 Destination Host Unreachable
From 169.254.8.152 icmp_seq=79 Destination Host Unreachable
From 169.254.8.152 icmp_seq=80 Destination Host Unreachable
From 169.254.8.152 icmp_seq=81 Destination Host Unreachable
From 169.254.8.152 icmp_seq=82 Destination Host Unreachable
From 169.254.8.152 icmp_seq=83 Destination Host Unreachable
From 169.254.8.152 icmp_seq=84 Destination Host Unreachable
From 169.254.8.152 icmp_seq=85 Destination Host Unreachable
From 169.254.8.152 icmp_seq=86 Destination Host Unreachable
From 169.254.8.152 icmp_seq=87 Destination Host Unreachable
From 169.254.8.152 icmp_seq=88 Destination Host Unreachable
From 169.254.8.152 icmp_seq=89 Destination Host Unreachable
From 169.254.8.152 icmp_seq=90 Destination Host Unreachable
From 169.254.8.152 icmp_seq=91 Destination Host Unreachable
From 169.254.8.152 icmp_seq=92 Destination Host Unreachable
From 169.254.8.152 icmp_seq=93 Destination Host Unreachable
From 169.254.8.152 icmp_seq=94 Destination Host Unreachable
From 169.254.8.152 icmp_seq=95 Destination Host Unreachable
From 169.254.8.152 icmp_seq=96 Destination Host Unreachable
From 169.254.8.152 icmp_seq=97 Destination Host Unreachable
From 169.254.8.152 icmp_seq=98 Destination Host Unreachable
From 169.254.8.152 icmp_seq=99 Destination Host Unreachable
From 169.254.8.152 icmp_seq=100 Destination Host Unreachable
From 169.254.8.152 icmp_seq=101 Destination Host Unreachable
From 169.254.8.152 icmp_seq=102 Destination Host Unreachable
From 169.254.8.152 icmp_seq=103 Destination Host Unreachable
From 169.254.8.152 icmp_seq=104 Destination Host Unreachable
From 169.254.8.152 icmp_seq=105 Destination Host Unreachable
From 169.254.8.152 icmp_seq=106 Destination Host Unreachable
From 169.254.8.152 icmp_seq=107 Destination Host Unreachable
From 169.254.8.152 icmp_seq=108 Destination Host Unreachable
From 169.254.8.152 icmp_seq=110 Destination Host Unreachable
From 169.254.8.152 icmp_seq=111 Destination Host Unreachable
From 169.254.8.152 icmp_seq=112 Destination Host Unreachable
From 169.254.8.152 icmp_seq=114 Destination Host Unreachable
From 169.254.8.152 icmp_seq=115 Destination Host Unreachable
From 169.254.8.152 icmp_seq=116 Destination Host Unreachable
From 169.254.8.152 icmp_seq=118 Destination Host Unreachable
From 169.254.8.152 icmp_seq=119 Destination Host Unreachable
From 169.254.8.152 icmp_seq=120 Destination Host Unreachable
From 169.254.8.152 icmp_seq=121 Destination Host Unreachable
From 169.254.8.152 icmp_seq=122 Destination Host Unreachable
From 169.254.8.152 icmp_seq=123 Destination Host Unreachable
From 169.254.8.152 icmp_seq=124 Destination Host Unreachable
From 169.254.8.152 icmp_seq=125 Destination Host Unreachable
From 169.254.8.152 icmp_seq=126 Destination Host Unreachable
From 169.254.8.152 icmp_seq=128 Destination Host Unreachable
From 169.254.8.152 icmp_seq=129 Destination Host Unreachable
From 169.254.8.152 icmp_seq=130 Destination Host Unreachable
From 169.254.8.152 icmp_seq=132 Destination Host Unreachable
From 169.254.8.152 icmp_seq=133 Destination Host Unreachable
From 169.254.8.152 icmp_seq=134 Destination Host Unreachable
From 169.254.8.152 icmp_seq=136 Destination Host Unreachable
From 169.254.8.152 icmp_seq=137 Destination Host Unreachable
From 169.254.8.152 icmp_seq=138 Destination Host Unreachable
From 169.254.8.152 icmp_seq=139 Destination Host Unreachable
From 169.254.8.152 icmp_seq=140 Destination Host Unreachable
From 169.254.8.152 icmp_seq=141 Destination Host Unreachable
From 169.254.8.152 icmp_seq=142 Destination Host Unreachable
From 169.254.8.152 icmp_seq=143 Destination Host Unreachable
From 169.254.8.152 icmp_seq=144 Destination Host Unreachable
From 169.254.8.152 icmp_seq=145 Destination Host Unreachable
From 169.254.8.152 icmp_seq=146 Destination Host Unreachable
From 169.254.8.152 icmp_seq=147 Destination Host Unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
From 169.254.8.152 icmp_seq=161 Destination Host Unreachable
From 169.254.8.152 icmp_seq=162 Destination Host Unreachable
From 169.254.8.152 icmp_seq=163 Destination Host Unreachable
From 169.254.8.152 icmp_seq=165 Destination Host Unreachable
From 169.254.8.152 icmp_seq=166 Destination Host Unreachable
From 169.254.8.152 icmp_seq=167 Destination Host Unreachable
From 169.254.8.152 icmp_seq=169 Destination Host Unreachable
From 169.254.8.152 icmp_seq=170 Destination Host Unreachable
From 169.254.8.152 icmp_seq=171 Destination Host Unreachable
From 169.254.8.152 icmp_seq=172 Destination Host Unreachable
From 169.254.8.152 icmp_seq=173 Destination Host Unreachable
From 169.254.8.152 icmp_seq=174 Destination Host Unreachable
From 169.254.8.152 icmp_seq=175 Destination Host Unreachable
From 169.254.8.152 icmp_seq=176 Destination Host Unreachable
From 169.254.8.152 icmp_seq=177 Destination Host Unreachable
From 169.254.8.152 icmp_seq=178 Destination Host Unreachable
From 169.254.8.152 icmp_seq=179 Destination Host Unreachable
From 169.254.8.152 icmp_seq=180 Destination Host Unreachable
From 169.254.8.152 icmp_seq=181 Destination Host Unreachable
From 169.254.8.152 icmp_seq=182 Destination Host Unreachable
From 169.254.8.152 icmp_seq=183 Destination Host Unreachable
From 169.254.8.152 icmp_seq=184 Destination Host Unreachable
From 169.254.8.152 icmp_seq=185 Destination Host Unreachable
From 169.254.8.152 icmp_seq=186 Destination Host Unreachable
From 169.254.8.152 icmp_seq=187 Destination Host Unreachable
From 169.254.8.152 icmp_seq=188 Destination Host Unreachable
From 169.254.8.152 icmp_seq=189 Destination Host Unreachable
From 169.254.8.152 icmp_seq=190 Destination Host Unreachable
From 169.254.8.152 icmp_seq=191 Destination Host Unreachable
From 169.254.8.152 icmp_seq=192 Destination Host Unreachable
From 169.254.8.152 icmp_seq=193 Destination Host Unreachable
From 169.254.8.152 icmp_seq=194 Destination Host Unreachable
From 169.254.8.152 icmp_seq=195 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
197 packets transmitted, 0 received, +174 errors, 100% packet loss, time 196471ms
, pipe 3


```

---

### Post by pytheas22 on 2008-08-02
Alright, give this a shot:
```

sudo dhclient -r wlan0
sudo iwconfig wlan0 mode managed channel 7 rate 11M essid "BTHomeHub-72C9"
sudo dhclient wlan0
ifconfig wlan0
```

Please post all output.

---

### Post by Sicc on 2008-08-02
Still dosent connect


sudo dhclient -r wlan0

```
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:78:7b:ea
Sending on   LPF/wlan0/00:11:50:78:7b:ea
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```


sudo iwconfig wlan0 mode managed channel 7 rate 11M essid "BTHomeHub-72C9"
sudo dhclient wlan0

```
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:78:7b:ea
Sending on   LPF/wlan0/00:11:50:78:7b:ea
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


ifconfig wlan0

```
wlan0     Link encap:Ethernet  HWaddr 00:11:50:78:7b:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3025 (2.9 KB)  TX bytes:14372 (14.0 KB)
```

---

### Post by pytheas22 on 2008-08-02
Alright, since it doesn't seem to be connecting at all, I'm thinking that this is a driver issue.  Try running these commands to install a different version of the driver (I'm assuming you have an ethernet connection enabled while you run these commands; if it's impossible to get a wired connection let me know):
```

sudo -s
apt-get install build-essential rutilt
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*/Module
make
make install
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

Then reboot.  After the reboot, see if you can connect in wicd.

If it still doesn't work, please post:
```

cat /etc/modprobe.d/blacklist
iwlist scan
lshw -C Network
```

---

### Post by Sicc on 2008-08-03
i managed to connect through wired, but have decided to just forget about linux for now, seems abit too much for me. i'l just stick to windows for now, thanks for your help :)

---

### Post by pytheas22 on 2008-08-03
> i managed to connect through wired, but have decided to just forget about linux for now, seems abit too much for me. i'l just stick to windows for now, thanks for your help

That's alright if it's what you want to do...but I wanted to point out that I really think the instructions in my previous post would solve the problem--I have a wireless card with the same chipset as yours and ran into a similar issue once, and that solved it.  So if you can find a little more patience for Linux, you may want to give it one last shot.  Otherwise, I hope you'll try it again before too long; it gets easier and easier every day.

---

