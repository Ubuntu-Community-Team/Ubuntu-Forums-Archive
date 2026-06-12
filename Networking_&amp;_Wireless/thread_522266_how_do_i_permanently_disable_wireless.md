---
title: "how do i permanently disable wireless?"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by jamesford on 2007-08-10
hmm i need to disable the wireless. ive read some other posts and found out i need to add blacklist modulename to the file blacklist in the /etc/modprobe.d
the problem is i dont know the module name
iwconfig gives me
```
wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

im not sure what wireless card ive got but the motherboard is a M2N32-SLI Deluxe/Wireless
it looks like the wireless card can be removed but due to the way it extends into the i/o shield it s impossible to remove the card without taking the motherboard out of the case, smt i dont want to do. oh and theres no way to disable it in bios either, this was the first thing i tried. but theres no option for it quite simply. i see this is frequently requested over at the asus forums as well

another option is to disable it via the nm-applet, but the setting doesent stick after a reboot. anyway to make it stick?

---

### Post by noob12 on 2007-08-10
Well
```

sudo lshw -C network

```
will generally show you (in the configuration line) the associated driver.

If you just need to turn the radio off, there's often a switch on the laptop.

Also, with some drivers you can control this with **iwconfig** as follows.
```

sudo iwconfig wlan0 txpower off

```

If this works you can put this command in an rc script, and put a manual config line in
/etc/network/interfaces for wlan0 to prevent NetworkManager from
assuming control.

```

iface wlan0 inet manual

```

---

### Post by jamesford on 2007-08-10
hi
this is not a laptop

i get the following outputs:
```
sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:0f:87:f1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```


```
sudo iwconfig wlan0 txpower off
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.

```

what is the module name ? IEEE 802.11g ?

---

### Post by noob12 on 2007-08-10
No.  In some cases it isn't shown; usually it is.

The second result is because your driver doesn't support turning the radio off.

Do ```
lspci -nn
``` so we can identify the device precisely.  Also, looking at the output of ```
dmesg
``` will generally tell you which driver picked up the device.

---

### Post by noob12 on 2007-08-10
Also do 
```

lsusb -v

```
From the mobo description, it looks like it might be an onboard USB device.

---

### Post by jamesford on 2007-08-10
hmm, this is what i found, not really sure waht to look for so pasting it all

```
 lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f4] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:08.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:09.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:09.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:09.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:0a.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:0a.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:0c.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0d.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:10.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:11.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:17.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:08.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
01:08.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
01:08.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04)
01:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:00.0 Mass storage controller [0180]: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller [1095:3132] (rev 01)
03:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0295] (rev a1)
```


```
dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=fc5a8728-910c-44a6-831e-3d56645ad7fa ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000dfee0000 - 00000000dfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfee3000 - 00000000dfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 Nvidia                                ) @ 0x00000000000f7bc0
[    0.000000] ACPI: XSDT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x00000000dfee3100
[    0.000000] ACPI: FADT (v003 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x00000000dfeec880
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x00000000dfeeca80
[    0.000000] ACPI: HPET (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000098) @ 0x00000000dfeece00
[    0.000000] ACPI: MCFG (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x00000000dfeece80
[    0.000000] ACPI: MADT (v001 Nvidia ASUSACPI 0x42302e31 AWRD 0x00000000) @ 0x00000000dfeec9c0
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 0000000120000000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917216) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1179648
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   917216
[    0.000000]     0:  1048576 ->  1179648
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1089 pages reserved
[    0.000000]   DMA zone: 2854 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898840 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
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
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000f0000
[    0.000000] Nosave address range: 00000000000f0000 - 0000000000100000
[    0.000000] Nosave address range: 00000000dfee0000 - 00000000dfee3000
[    0.000000] Nosave address range: 00000000dfee3000 - 00000000dfef0000
[    0.000000] Nosave address range: 00000000dfef0000 - 00000000dff00000
[    0.000000] Nosave address range: 00000000dff00000 - 00000000f0000000
[    0.000000] Nosave address range: 00000000f0000000 - 00000000f4000000
[    0.000000] Nosave address range: 00000000f4000000 - 00000000fec00000
[    0.000000] Nosave address range: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1030974
[    0.000000] Kernel command line: root=UUID=fc5a8728-910c-44a6-831e-3d56645ad7fa ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   23.371654] Console: colour VGA+ 80x25
[   23.372743] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   23.374583] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   23.375223] Checking aperture...
[   23.375226] CPU 0: aperture @ 4000000 size 32 MB
[   23.375228] Aperture too small (32 MB)
[   23.380566] No AGP bridge found
[   23.380567] Your BIOS doesn't leave a aperture memory hole
[   23.380568] Please enable the IOMMU option in the BIOS setup
[   23.380569] This costs you 64 MB of RAM
[   23.397631] Mapping aperture over 65536 KB of RAM @ 4000000
[   23.420717] Memory: 4045140k/4718592k available (2217k kernel code, 147624k reserved, 1162k data, 304k init)
[   23.496963] Calibrating delay using timer specific routine.. 6034.16 BogoMIPS (lpj=12068338)
[   23.497000] Security Framework v1.0.0 initialized
[   23.497003] SELinux:  Disabled at boot.
[   23.497018] Mount-cache hash table entries: 256
[   23.497104] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.497106] CPU: L2 Cache: 1024K (64 bytes/line)
[   23.497108] CPU 0/0 -> Node 0
[   23.497109] CPU: Physical Processor ID: 0
[   23.497110] CPU: Processor Core ID: 0
[   23.497124] SMP alternatives: switching to UP code
[   23.497280] Early unpacking initramfs... done
[   23.689652] ACPI: Core revision 20060707
[   23.696655] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.742250] Using local APIC timer interrupts.
[   23.775359] result 12557165
[   23.775360] Detected 12.557 MHz APIC timer.
[   23.776454] SMP alternatives: switching to SMP code
[   23.776502] Booting processor 1/2 APIC 0x1
[   23.787025] Initializing CPU#1
[   23.864383] Calibrating delay using timer specific routine.. 6027.49 BogoMIPS (lpj=12054985)
[   23.864387] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.864389] CPU: L2 Cache: 1024K (64 bytes/line)
[   23.864391] CPU 1/1 -> Node 0
[   23.864392] CPU: Physical Processor ID: 0
[   23.864393] CPU: Processor Core ID: 1
[   23.864470] AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[   23.868372] CPU 1: Syncing TSC to CPU 0.
[   23.868174] CPU 1: synchronized TSC with CPU 0 (last diff 2 cycles, maxerr 601 cycles)
[   23.868181] Brought up 2 CPUs
[   23.868255] time.c: Using 25.000000 MHz WALL HPET GTOD HPET timer.
[   23.868256] time.c: Detected 3013.718 MHz processor.
[   24.363884] migration_cost=222
[   24.364110] Time: 16:26:00  Date: 07/10/107
[   24.364135] NET: Registered protocol family 16
[   24.364186] ACPI: bus type pci registered
[   24.364190] PCI: Using configuration type 1
[   24.376667] ACPI: Interpreter enabled
[   24.376670] ACPI: Using IOAPIC for interrupt routing
[   24.377189] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   24.377192] PCI: Probing PCI hardware (bus 00)
[   24.379310] PCI: Transparent bridge - 0000:00:0e.0
[   24.379466] Boot video device is 0000:03:00.0
[   24.379517] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   24.443769] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   24.448054] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.448333] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.448611] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   24.448889] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.449167] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.449447] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
[   24.449725] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 *11 14 15)
[   24.450001] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.450279] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.450556] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.450840] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   24.451124] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 *11 14 15)
[   24.451407] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.451685] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.451963] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.452239] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.452520] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   24.452798] ACPI: PCI Interrupt Link [LSID] (IRQs *5 7 9 10 11 14 15)
[   24.453076] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[   24.453356] ACPI: PCI Interrupt Link [LSA2] (IRQs *5 7 9 10 11 14 15)
[   24.453698] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   24.454032] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.454365] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   24.454698] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.455036] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   24.455367] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   24.455701] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   24.456032] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   24.456367] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[   24.456698] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[   24.457031] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[   24.457363] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   24.457696] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[   24.458031] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[   24.458364] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[   24.458696] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   24.459037] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   24.459369] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[   24.459702] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[   24.460034] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[   24.460222] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.460229] pnp: PnP ACPI init
[   24.466347] pnp: PnP ACPI: found 15 devices
[   24.466384] PCI: Using ACPI for IRQ routing
[   24.466387] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   24.466452] NET: Registered protocol family 8
[   24.466453] NET: Registered protocol family 20
[   24.466464] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   24.466467] hpet0: 3 32-bit timers, 25000000 Hz
[   24.467513] PCI-DMA: Disabling AGP.
[   24.467535] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   24.467536] PCI-DMA: using GART IOMMU.
[   24.467538] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[   24.467888] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[   24.467890] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   24.467893] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   24.467895] pnp: 00:01: ioport range 0x1480-0x14ff could not be reserved
[   24.467897] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   24.467899] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   24.468087] PCI: Bridge: 0000:00:0e.0
[   24.468089]   IO window: a000-afff
[   24.468092]   MEM window: fdf00000-fdffffff
[   24.468093]   PREFETCH window: disabled.
[   24.468095] PCI: Bridge: 0000:00:16.0
[   24.468097]   IO window: 9000-9fff
[   24.468099]   MEM window: fde00000-fdefffff
[   24.468101]   PREFETCH window: disabled.
[   24.468103] PCI: Bridge: 0000:00:17.0
[   24.468104]   IO window: 8000-8fff
[   24.468107]   MEM window: fa000000-fcffffff
[   24.468109]   PREFETCH window: e0000000-efffffff
[   24.468116] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.468122] PCI: Setting latency timer of device 0000:00:16.0 to 64
[   24.468127] PCI: Setting latency timer of device 0000:00:17.0 to 64
[   24.468156] NET: Registered protocol family 2
[   24.510663] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   24.511020] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   24.512261] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   24.512570] TCP: Hash tables configured (established 262144 bind 65536)
[   24.512572] TCP reno registered
[   24.526667] checking if image is initramfs... it is
[   24.921975] Freeing initrd memory: 6833k freed
[   24.924947] audit: initializing netlink socket (disabled)
[   24.924957] audit(1186763160.532:1): initialized
[   24.925090] VFS: Disk quotas dquot_6.5.1
[   24.925103] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.925134] io scheduler noop registered
[   24.925136] io scheduler anticipatory registered
[   24.925137] io scheduler deadline registered
[   24.925146] io scheduler cfq registered (default)
[   24.941787] PCI: Setting latency timer of device 0000:00:16.0 to 64
[   24.941809] assign_interrupt_mode Found MSI capability
[   24.941811] Allocate Port Service[0000:00:16.0:pcie00]
[   24.941864] PCI: Setting latency timer of device 0000:00:17.0 to 64
[   24.941885] assign_interrupt_mode Found MSI capability
[   24.941886] Allocate Port Service[0000:00:17.0:pcie00]
[   24.956523] Real Time Clock Driver v1.12ac
[   24.956652] hpet_resources: 0xfefff000 is busy
[   24.956661] Linux agpgart interface v0.102 (c) Dave Jones
[   24.956663] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.956767] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.957132] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.957261] mice: PS/2 mouse device common for all mice
[   24.957614] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.957753] input: Macintosh mouse button emulation as /class/input/input0
[   24.957773] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.957776] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.957907] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.958285] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.958289] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.958344] TCP cubic registered
[   24.958350] NET: Registered protocol family 1
[   24.958407] ACPI: (supports S0 S1 S3 S4 S5)
[   24.958444]   Magic number: 3:833:438
[   24.958522] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.958567] Freeing unused kernel memory: 304k freed
[   24.987815] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.071305] Capability LSM initialized
[   26.116384] ACPI: Fan [FAN] (on)
[   26.120160] ACPI: Thermal Zone [THRM] (40 C)
[   26.386578] SCSI subsystem initialized
[   26.407546] libata version 2.20 loaded.
[   26.408737] sata_nv 0000:00:0d.0: version 3.3
[   26.409125] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   26.409133] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 23
[   26.409150] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   26.409188] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001e000 irq 23
[   26.436583] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001e008 irq 23
[   26.436597] scsi0 : sata_nv
[   26.436661] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   26.436705] usbcore: registered new interface driver usbfs
[   26.436719] usbcore: registered new interface driver hub
[   26.436737] usbcore: registered new device driver usb
[   26.438761] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.441828] ieee1394: Initialized config rom entry `ip1394'
[   26.457618] Floppy drive(s): fd0 is 1.44M
[   26.479507] FDC 0 is a post-1991 82077
[   26.909112] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   26.921262] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   26.921266] ata1.00: ATA-8: SAMSUNG HD321KJ, CP100-10, max UDMA7
[   26.921268] ata1.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   26.933225] ata1.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   26.933227] ata1.00: configured for UDMA/133
[   26.933249] scsi1 : sata_nv
[   27.407958] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   27.434070] ata2.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   27.434074] ata2.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[   27.434076] ata2.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/1)
[   27.444106] ata2.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   27.444108] ata2.00: configured for UDMA/133
[   27.444184] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[   27.444540] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[   27.445190] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   27.445198] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 22
[   27.445214] PCI: Setting latency timer of device 0000:00:0d.1 to 64
[   27.445239] ata3: SATA max UDMA/133 cmd 0x00000000000109e0 ctl 0x0000000000010be2 bmdma 0x000000000001cc00 irq 22
[   27.445257] ata4: SATA max UDMA/133 cmd 0x0000000000010960 ctl 0x0000000000010b62 bmdma 0x000000000001cc08 irq 22
[   27.445266] scsi2 : sata_nv
[   27.918778] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   27.930853] ata3.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/100
[   27.930855] ata3.00: 586072368 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   27.942810] ata3.00: configured for UDMA/100
[   27.942831] scsi3 : sata_nv
[   28.417625] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.460933] ata4.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   28.460936] ata4.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[   28.460938] ata4.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[   28.527414] ata4.00: ata_hpa_resize 1: sectors = 625142448, hpa_sectors = 625142448
[   28.527417] ata4.00: configured for UDMA/133
[   28.527476] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[   28.527810] scsi 3:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[   28.528457] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[   28.528463] ACPI: PCI Interrupt 0000:00:0d.2[C] -> Link [ASA2] -> GSI 21 (level, low) -> IRQ 21
[   28.528476] PCI: Setting latency timer of device 0000:00:0d.2 to 64
[   28.528497] ata5: SATA max UDMA/133 cmd 0x000000000001c800 ctl 0x000000000001c402 bmdma 0x000000000001b800 irq 21
[   28.528515] ata6: SATA max UDMA/133 cmd 0x000000000001c000 ctl 0x000000000001bc02 bmdma 0x000000000001b808 irq 21
[   28.528523] scsi4 : sata_nv
[   29.000278] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.167993] ata5.00: ATAPI, max UDMA/66
[   29.339582] ata5.00: configured for UDMA/66
[   29.339604] scsi5 : sata_nv
[   29.810406] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.978119] ata6.00: ATAPI, max UDMA/33
[   29.978121] ata6.00: applying bridge limits
[   30.149707] ata6.00: configured for UDMA/33
[   30.150169] scsi 4:0:0:0: CD-ROM            ASUS     DRW-1814BLT      1.04 PQ: 0 ANSI: 5
[   30.151585] scsi 5:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S183A SB01 PQ: 0 ANSI: 5
[   30.152457] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   30.152463] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 20
[   30.152471] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[   30.152473] ehci_hcd 0000:00:0a.1: EHCI Host Controller
[   30.152561] ehci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 1
[   30.152581] ehci_hcd 0000:00:0a.1: debug port 1
[   30.152583] PCI: cache line size of 64 is not supported by device 0000:00:0a.1
[   30.152591] ehci_hcd 0000:00:0a.1: irq 20, io mem 0xfe02e000
[   30.152596] ehci_hcd 0000:00:0a.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.152659] usb usb1: configuration #1 chosen from 1 choice
[   30.152676] hub 1-0:1.0: USB hub found
[   30.152681] hub 1-0:1.0: 10 ports detected
[   30.257832] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   30.257834] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   30.257838] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   30.257844] forcedeth: using HIGHDMA
[   30.684372] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   30.780403] eth0: forcedeth.c: subsystem: 01043:cb84 bound to 0000:00:10.0
[   30.780777] ACPI: PCI Interrupt Link [AMC1] enabled at IRQ 22
[   30.780779] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [AMC1] -> GSI 22 (level, low) -> IRQ 22
[   30.780783] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   30.780789] forcedeth: using HIGHDMA
[   31.219116] usb 1-4: device not accepting address 3, error -71
[   31.303179] eth1: forcedeth.c: subsystem: 01043:cb84 bound to 0000:00:11.0
[   31.303546] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   31.303548] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 21
[   31.303555] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.303558] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[   31.303579] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 2
[   31.303588] ohci_hcd 0000:00:0a.0: irq 21, io mem 0xfe02f000
[   31.334854] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   31.364860] usb usb2: configuration #1 chosen from 1 choice
[   31.364877] hub 2-0:1.0: USB hub found
[   31.364884] hub 2-0:1.0: 10 ports detected
[   31.471032] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   31.471040] ACPI: PCI Interrupt 0000:01:08.2[B] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   31.475602] usb 1-4: configuration #1 chosen from 1 choice
[   31.521040] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.521427] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   31.521432] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   31.571427] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdffe000-fdffe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.571454] sata_sil24 0000:02:00.0: version 0.8
[   31.571839] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   31.571841] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 16
[   31.571878] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   31.572126] ata7: SATA max UDMA/100 cmd 0xffffc20000068000 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   31.572252] ata8: SATA max UDMA/100 cmd 0xffffc2000006a000 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 16
[   31.572259] scsi6 : sata_sil24
[   31.721957] usb 1-5: new high speed USB device using ehci_hcd and address 5
[   31.870191] usb 1-5: configuration #1 chosen from 1 choice
[   31.885603] ata7: SATA link down (SStatus 0 SControl 300)
[   31.885601] scsi7 : sata_sil24
[   32.117043] usb 1-9: new high speed USB device using ehci_hcd and address 6
[   32.196882] ata8: SATA link down (SStatus 0 SControl 300)
[   32.199201] NFORCE-MCP55: IDE controller at PCI slot 0000:00:0c.0
[   32.199214] NFORCE-MCP55: chipset revision 161
[   32.199216] NFORCE-MCP55: not 100% native mode: will probe irqs later
[   32.199220] NFORCE-MCP55: 0000:00:0c.0 (rev a1) UDMA133 controller
[   32.199224] NFORCE-MCP55: neither IDE port enabled (BIOS)
[   32.209753] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   32.209763] sda: Write Protect is off
[   32.209764] sda: Mode Sense: 00 3a 00 00
[   32.209773] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.209808] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[   32.209813] sda: Write Protect is off
[   32.209814] sda: Mode Sense: 00 3a 00 00
[   32.209823] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.209825]  sda: sda1 sda2
[   32.260270] sd 0:0:0:0: Attached scsi disk sda
[   32.260405] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   32.260412] sdb: Write Protect is off
[   32.260413] sdb: Mode Sense: 00 3a 00 00
[   32.260422] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.260448] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[   32.260453] sdb: Write Protect is off
[   32.260454] sdb: Mode Sense: 00 3a 00 00
[   32.260463] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.260465]  sdb: sdb1
[   32.262168] sd 1:0:0:0: Attached scsi disk sdb
[   32.262271] SCSI device sdc: 586072368 512-byte hdwr sectors (300069 MB)
[   32.262277] sdc: Write Protect is off
[   32.262278] sdc: Mode Sense: 00 3a 00 00
[   32.262287] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.262306] SCSI device sdc: 586072368 512-byte hdwr sectors (300069 MB)
[   32.262311] sdc: Write Protect is off
[   32.262312] sdc: Mode Sense: 00 3a 00 00
[   32.262320] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.262322]  sdc:<6>usb 1-9: configuration #1 chosen from 1 choice
[   32.297170]  sdc1
[   32.297374] sd 2:0:0:0: Attached scsi disk sdc
[   32.297497] SCSI device sdd: 625142448 512-byte hdwr sectors (320073 MB)
[   32.297504] sdd: Write Protect is off
[   32.297505] sdd: Mode Sense: 00 3a 00 00
[   32.297514] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.297544] SCSI device sdd: 625142448 512-byte hdwr sectors (320073 MB)
[   32.297549] sdd: Write Protect is off
[   32.297550] sdd: Mode Sense: 00 3a 00 00
[   32.297558] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.297560]  sdd: sdd1
[   32.315229] sd 3:0:0:0: Attached scsi disk sdd
[   32.318727] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.318742] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   32.318754] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   32.318767] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   32.318780] sr 4:0:0:0: Attached scsi generic sg4 type 5
[   32.318792] scsi 5:0:0:0: Attached scsi generic sg5 type 5
[   32.322288] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   32.322291] Uniform CD-ROM driver Revision: 3.20
[   32.323030] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   32.334988] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   32.335027] sr 5:0:0:0: Attached scsi CD-ROM sr1
[   32.472107] Attempting manual resume
[   32.472109] swsusp: Resume From Partition 8:2
[   32.472111] PM: Checking swsusp image.
[   32.472241] PM: Resume from disk failed.
[   32.508812] kjournald starting.  Commit interval 5 seconds
[   32.508802] EXT3-fs: mounted filesystem with ordered data mode.
[   32.571995] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   32.772615] usb 2-3: configuration #1 chosen from 1 choice
[   32.775684] usbcore: registered new interface driver libusual
[   32.791571] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01510d8205]
[   33.033240] Initializing USB Mass Storage driver...
[   33.033295] scsi8 : SCSI emulation for USB Mass Storage devices
[   33.033348] usb-storage: device found at 5
[   33.033350] usb-storage: waiting for device to settle before scanning
[   33.033338] usbcore: registered new interface driver usb-storage
[   33.033340] USB Mass Storage support registered.
[   33.066980] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0011d8000156b4d1]
[   38.023893] usb-storage: device scan complete
[   38.025772] scsi 8:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   38.027763] scsi 8:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   38.029758] scsi 8:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   38.031753] scsi 8:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9144 PQ: 0 ANSI: 0
[   38.034145] sd 8:0:0:0: Attached scsi removable disk sde
[   38.034172] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   38.036131] sd 8:0:0:1: Attached scsi removable disk sdf
[   38.036149] sd 8:0:0:1: Attached scsi generic sg7 type 0
[   38.038128] sd 8:0:0:2: Attached scsi removable disk sdg
[   38.038147] sd 8:0:0:2: Attached scsi generic sg8 type 0
[   38.040122] sd 8:0:0:3: Attached scsi removable disk sdh
[   38.040141] sd 8:0:0:3: Attached scsi generic sg9 type 0
[   40.368059] NET: Registered protocol family 10
[   40.368123] lo: Disabled Privacy Extensions
[   40.992458] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.994233] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.083473] input: PC Speaker as /class/input/input2
[   41.186283] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   41.186297] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   41.215631] Linux video capture interface: v2.00
[   41.236509] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x4117
[   41.236520] usbcore: registered new interface driver usblp
[   41.236523] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   41.267895] gameport: EMU10K1 is pci0000:01:08.1/gameport0, io 0xa800, speed 1200kHz
[   41.420573] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   41.420577] quickcam: Kernel:2.6.20-16-generic bus:2 class:FF subclass:FF vendor:046D product:0870
[   41.444516] quickcam: Sensor HDCS-1020 detected
[   41.450528] quickcam: Registered device: /dev/video0
[   41.450541] usbcore: registered new interface driver quickcam
[   41.483848] input: PS2++ Logitech MX Mouse as /class/input/input3
[   41.557386] parport: PnPBIOS parport detected.
[   41.557412] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   41.676378] nvidia: module license 'NVIDIA' taints kernel.
[   41.929562] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   41.929565] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC6] -> GSI 16 (level, low) -> IRQ 16
[   41.929571] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   41.929675] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007
[   42.049446] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   42.049455] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   42.052125] Installing spdif_bug patch: Audigy 2 ZS [SB0350]
[   42.153533] wmaster0: Selected rate control algorithm 'simple'
[   42.198242] wiphy0: hwaddr 00:15:af:0f:87:f1, rtl8187 V1 + rtl8225z2
[   42.198252] usbcore: registered new interface driver rtl8187
[   42.266836] lp0: using parport0 (interrupt-driven).
[   42.579572] it87: Found IT8716F chip at 0x290, revision 1
[   42.579581] it87: in3 is VCC (+5V)
[   42.579583] it87: in7 is VCCH (+5V Stand-By)
[   42.602419] Adding 7783484k swap on /dev/disk/by-uuid/ca29603a-cea3-4f62-90a3-0924dce7ea1c.  Priority:-1 extents:1 across:7783484k
[   42.764892] EXT3 FS on sda1, internal journal
[   43.059154] kjournald starting.  Commit interval 5 seconds
[   43.059391] EXT3 FS on sdb1, internal journal
[   43.059394] EXT3-fs: mounted filesystem with ordered data mode.
[   43.077526] kjournald starting.  Commit interval 5 seconds
[   43.077804] EXT3 FS on sdd1, internal journal
[   43.077807] EXT3-fs: mounted filesystem with ordered data mode.
[   43.091548] kjournald starting.  Commit interval 5 seconds
[   43.091717] EXT3 FS on sdc1, internal journal
[   43.091720] EXT3-fs: mounted filesystem with ordered data mode.
[   45.405743] input: Power Button (FF) as /class/input/input4
[   45.405762] ACPI: Power Button (FF) [PWRF]
[   45.405782] input: Power Button (CM) as /class/input/input5
[   45.405793] ACPI: Power Button (CM) [PWRB]
[   45.438753] No dock devices found.
[   45.518466] ibm_acpi: ec object not found
[   45.566466] Using specific hotkey driver
[   45.610192] pcc_acpi: loading...
[   45.789577] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ processors (version 2.00.00)
[   45.789595] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x8
[   45.789598] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xa
[   45.789600] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xc
[   45.789601] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xe
[   45.789603] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10
[   45.789604] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[   45.789606] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[   45.789607] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   48.943184] ppdev: user-space parallel port driver
[   50.431235] wmaster0: Does not support passive scan, disabled
[   50.454774] wlan0: starting scan
[   50.503293] eth1: no link during initialization.
[   50.503536] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   50.953550] eth0: no IPv6 routers present
[   51.775661] wlan0: scan completed
[   52.521974] Netfilter messages via NETLINK v0.30.
[   52.525703] nf_conntrack version 0.5.0 (8192 buckets, 65536 max)
[   52.838520] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.384916] /dev/vmmon[6142]: Module vmmon: registered with major=10 minor=165
[   54.384931] /dev/vmmon[6142]: Module vmmon: initialized
[   54.644180] /dev/vmnet: open called by PID 6170 (vmnet-bridge)
[   54.644323] /dev/vmnet: hub 0 does not exist, allocating memory.
[   54.644421] /dev/vmnet: port on hub 0 successfully opened
[   54.644520] bridge-eth0: enabling the bridge
[   54.644601] bridge-eth0: up
[   54.644673] bridge-eth0: already up
[   54.644751] bridge-eth0: attached
[   54.852323] /dev/vmnet: open called by PID 6184 (vmnet-natd)
[   54.852331] /dev/vmnet: hub 8 does not exist, allocating memory.
[   54.852340] /dev/vmnet: port on hub 8 successfully opened
[   57.876755] /dev/vmnet: open called by PID 6396 (vmnet-netifup)
[   57.876910] /dev/vmnet: hub 1 does not exist, allocating memory.
[   57.877013] /dev/vmnet: port on hub 1 successfully opened
[   57.877655] /dev/vmnet: open called by PID 6395 (vmnet-netifup)
[   57.877763] /dev/vmnet: port on hub 8 successfully opened
[   58.163103] /dev/vmnet: open called by PID 6418 (vmnet-dhcpd)
[   58.163225] /dev/vmnet: port on hub 8 successfully opened
[   58.163915] /dev/vmnet: open called by PID 6417 (vmnet-dhcpd)
[   58.164018] /dev/vmnet: port on hub 1 successfully opened
[   62.051035] vmnet8: no IPv6 routers present
[   62.092387] vmnet1: no IPv6 routers present
[   64.392584] wlan0: starting scan
[   65.709483] wlan0: scan completed
[   82.286535] wlan0: starting scan
[   82.725465] wlan0: scan completed
[   96.250532] wlan0: starting scan
[   96.732127] wlan0: scan completed
[  105.352855] wlan0: starting scan
[  105.793118] wlan0: scan completed
[  114.289005] wlan0: starting scan
[  114.727925] wlan0: scan completed
[  121.411203] wlan0: starting scan
[  121.850138] wlan0: scan completed
```
```


lsusb -v

Bus 002 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x0870 QuickCam Express
  bcdDevice            1.00
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           55
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               90mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              16
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 005: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05e3 Genesys Logic, Inc.
  idProduct          0x0710 USB 2.0 33-in-1 Card Reader
  bcdDevice           91.44
  iManufacturer           0 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8187 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 004: ID 03f0:4117 Hewlett-Packard 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03f0 Hewlett-Packard
  idProduct          0x4117 
  bcdDevice            1.00
  iManufacturer           1 Hewlett-Packard
  iProduct                2 HP LaserJet 1018
  iSerial                 3 KP22M2K
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 001 Device 001: ID 0000:0000  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x0000 
  idProduct          0x0000 
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

---

### Post by noob12 on 2007-08-10
This is the guy;  I should have told you to use **sudo** with the lsusb.  But we got enough info.

> 
Bus 001 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x8187 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


and here's your driver name **rtl8187**

> 
[   42.153533] wmaster0: Selected rate control algorithm 'simple'
[   42.198242] wiphy0: hwaddr 00:15:af:0f:87:f1, rtl8187 V1 + rtl8225z2
[   42.198252] usbcore: registered new interface driver rtl8187


Hope that helps.

---

### Post by jamesford on 2007-08-10
hooray that worked :D
thank you so much for your help and patience :)

---

