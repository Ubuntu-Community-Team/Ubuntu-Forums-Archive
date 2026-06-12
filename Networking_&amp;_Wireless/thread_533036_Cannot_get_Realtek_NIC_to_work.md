---
title: "Cannot get Realtek NIC to work"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by jhr76 on 2007-08-23
Hi. I am new to the forums and extremely new to Linux. I have recently installed Ubuntu 7.04 Feisty Fawn 64 bits version and I cannot get my network to work. I have an Asus P5LD2 Se motherboard that has a built in Realtek 8168/8111B NIC (that works perfectly in Windows). I have dsl (2,5 megs) with a static Ip configuration for my Zyxel 650R-31 modem/router. Ubuntu appears to recognize the NIC, but the 100 Mbits LAN led will not light up. I do show an eth0 device, but if I run sudo mii-tool it says no link. I have downloaded and compiled the driver from the Realtek website (the one that came included in the motherboard´s Cd appears to be corrupt since the traball will not unpack). I followed the instructions to the letter and nothing. I have searched thru many forums and tried a number of different commands other than the ones specified in the driver´s readme but it still would not work. After having suppossedly installed the driver following the instructions on the readme file and running the command to check if the process was there (lsmod something, I do not recall, I am at work now), it was but it would still not work. Then the next day I booted into Linux accidentally (I wanted Windows but I forgot to change it and by default the system booted into linux) and lo and behold the 100 Mbits LAN led was on. I run pppoeconf and I was able to connect and browse properly. I run some updates for the system, it prompted me to restart, so I did. The kernel had updated so I chose the new one (it was 2.6.20-15-generic and it changed to 15 again since I have since formatted and reinstalled). I still had a network connection so I installed Automatix to be able to install the Nvidia drivers (I was having issues with that too, it said I was missing some libc header files) and also a few other utilities and the like (such as ndiswrapper). It all installed properly and prompted me to restart so I did, but when I booted back up I had no network again. I kept messing with it, re compiling the driver and such and still nothing, so I tried ndiwrapper to try and use the Windows drivers, and after that the 10 Mbits lit up but I still had no connection. Since I couldn´t find a way to remove the network information to start fresh and try the drivers again (but keep all the other updates) I formatted and reinstalled and recompiled the drivers, did everything the same, but it will not work anymore. I have tried everything and I am at my wits end. I will now include the output of several diganostics commands I run while I was online (so the card was working at the time), because even though I saved the output of those same commands to a text file and into a floppy when the NIC did not work, the file was blank when I opened it in Windows.
javier@JHR:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02) 
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) 
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01) 
01:00.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007] 
01:01.0 Modem [0703]: Smart Link Ltd. Unknown device [2003:8800] (rev 02) 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01) 
04:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0295] (rev a1) 

javier@JHR:~$ lshw -C network 
WARNING: you should run this program as super-user. 
*-network 
description: Ethernet interface 
product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@02:00.0 
logical name: eth0 
version: 01 
serial: 00:18:f3:65:44:fa 
width: 64 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 multicast=yes 
resources: ioport:c800-c8ff iomemory:dceff000-dcefffff irq:19 

javier@JHR:~$ ifconfig -a 
eth0 Link encap:Ethernet HWaddr 00:18:F3:65:44:FA 
inet6 addr: fe80::218:f3ff:fe65:44fa/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:66970 errors:0 dropped:0 overruns:0 frame:0 
TX packets:45055 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:99536782 (94.9 MiB) TX bytes:3782521 (3.6 MiB) 
Interrupt:19 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:54 errors:0 dropped:0 overruns:0 frame:0 
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:3996 (3.9 KiB) TX bytes:3996 (3.9 KiB) 

ppp0 Link encap:Point-to-Point Protocol 
inet addr:201.252.85.164 P-t-P:200.3.60.2 Mask:255.255.255.255 
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1 
RX packets:66907 errors:0 dropped:0 overruns:0 frame:0 
TX packets:44933 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:3 
RX bytes:98060090 (93.5 MiB) TX bytes:2779835 (2.6 MiB) 

javier@JHR:~$ netstat -rn 
Kernel IP routing table 
Destination Gateway Genmask Flags MSS Window irtt Iface 
200.3.60.2 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0 
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0 

javier@JHR:~$ dmesg 
[ 0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic) 
[ 0.000000] Command line: root=UUID=7de7d198-2012-4b0c-9ed7-91c8d8e99bfc ro quiet splash 
[ 0.000000] BIOS-provided physical RAM map: 
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
[ 0.000000] BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved) 
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable) 
[ 0.000000] BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data) 
[ 0.000000] BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS) 
[ 0.000000] BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved) 
[ 0.000000] BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved) 
[ 0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used 
[ 0.000000] Entering add_active_range(0, 256, 524192) 1 entries of 3200 used 
[ 0.000000] end_pfn_map = 1048576 
[ 0.000000] DMI 2.4 present. 
[ 0.000000] ACPI: RSDP (v002 ACPIAM ) @ 0x00000000000fad20 
[ 0.000000] ACPI: XSDT (v001 A M I OEMXSDT 0x11000620 MSFT 0x00000097) @ 0x000000007ffa0100 
[ 0.000000] ACPI: FADT (v003 A M I OEMFACP 0x11000620 MSFT 0x00000097) @ 0x000000007ffa0290 
[ 0.000000] ACPI: MADT (v001 A M I OEMAPIC 0x11000620 MSFT 0x00000097) @ 0x000000007ffa0390 
[ 0.000000] ACPI: OEMB (v001 A M I AMI_OEM 0x11000620 MSFT 0x00000097) @ 0x000000007ffae040 
[ 0.000000] ACPI: HPET (v001 A M I OEMHPET 0x11000620 MSFT 0x00000097) @ 0x000000007ffa8940 
[ 0.000000] ACPI: MCFG (v001 A M I OEMMCFG 0x11000620 MSFT 0x00000097) @ 0x000000007ffa8980 
[ 0.000000] ACPI: DSDT (v001 A0402 A0402000 0x00000000 INTL 0x02002026) @ 0x0000000000000000 
[ 0.000000] No NUMA configuration found 
[ 0.000000] Faking a node at 0000000000000000-000000007ffa0000 
[ 0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used 
[ 0.000000] Entering add_active_range(0, 256, 524192) 1 entries of 3200 used 
[ 0.000000] Bootmem setup node 0 0000000000000000-000000007ffa0000 
[ 0.000000] Zone PFN ranges: 
[ 0.000000] DMA 0 -> 4096 
[ 0.000000] DMA32 4096 -> 1048576 
[ 0.000000] Normal 1048576 -> 1048576 
[ 0.000000] early_node_map[2] active PFN ranges 
[ 0.000000] 0: 0 -> 159 
[ 0.000000] 0: 256 -> 524192 
[ 0.000000] On node 0 totalpages: 524095 
[ 0.000000] DMA zone: 56 pages used for memmap 
[ 0.000000] DMA zone: 1086 pages reserved 
[ 0.000000] DMA zone: 2857 pages, LIFO batch:0 
[ 0.000000] DMA32 zone: 7110 pages used for memmap 
[ 0.000000] DMA32 zone: 512986 pages, LIFO batch:31 
[ 0.000000] Normal zone: 0 pages used for memmap 
[ 0.000000] ACPI: PM-Timer IO Port: 0x808 
[ 0.000000] ACPI: Local APIC address 0xfee00000 
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[ 0.000000] Processor #0 (Bootup-CPU) 
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled) 
[ 0.000000] Processor #1 
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled) 
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled) 
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[ 0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[ 0.000000] ACPI: IRQ0 used by override. 
[ 0.000000] ACPI: IRQ2 used by override. 
[ 0.000000] ACPI: IRQ9 used by override. 
[ 0.000000] Setting APIC routing to physical flat 
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
[ 0.000000] Using ACPI (MADT) for SMP configuration information 
[ 0.000000] Nosave address range: 000000000009f000 - 00000000000a0000 
[ 0.000000] Nosave address range: 00000000000a0000 - 00000000000e4000 
[ 0.000000] Nosave address range: 00000000000e4000 - 0000000000100000 
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb80000) 
[ 0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs 
[ 0.000000] PERCPU: Allocating 34048 bytes of per cpu data 
[ 0.000000] Built 1 zonelists. Total pages: 515843 
[ 0.000000] Kernel command line: root=UUID=7de7d198-2012-4b0c-9ed7-91c8d8e99bfc ro quiet splash 
[ 0.000000] Initializing CPU#0 
[ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
[ 24.304183] Console: colour VGA+ 80x25 
[ 24.305351] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[ 24.306381] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[ 24.306523] Checking aperture... 
[ 24.306533] Calgary: detecting Calgary via BIOS EBDA area 
[ 24.306535] Calgary: Unable to locate Rio Grande table in EBDA - bailing! 
[ 24.328009] Memory: 2052736k/2096768k available (2217k kernel code, 43644k reserved, 1162k data, 304k init) 
[ 24.404402] Calibrating delay using timer specific routine.. 4277.76 BogoMIPS (lpj=8555537) 
[ 24.404450] Security Framework v1.0.0 initialized 
[ 24.404456] SELinux: Disabled at boot. 
[ 24.404478] Mount-cache hash table entries: 256 
[ 24.404620] CPU: L1 I cache: 32K, L1 D cache: 32K 
[ 24.404622] CPU: L2 cache: 2048K 
[ 24.404624] CPU 0/0 -> Node 0 
[ 24.404626] using mwait in idle threads. 
[ 24.404628] CPU: Physical Processor ID: 0 
[ 24.404629] CPU: Processor Core ID: 0 
[ 24.404636] CPU0: Thermal monitoring enabled (TM2) 
[ 24.404646] SMP alternatives: switching to UP code 
[ 24.404878] Early unpacking initramfs... done 
[ 24.719769] ACPI: Core revision 20060707 
[ 24.720031] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
[ 24.764115] Using local APIC timer interrupts. 
[ 24.810897] result 16695225 
[ 24.810898] Detected 16.695 MHz APIC timer. 
[ 24.812382] SMP alternatives: switching to SMP code 
[ 24.812447] Booting processor 1/2 APIC 0x1 
[ 24.822858] Initializing CPU#1 
[ 24.900214] Calibrating delay using timer specific routine.. 4274.06 BogoMIPS (lpj=8548123) 
[ 24.900220] CPU: L1 I cache: 32K, L1 D cache: 32K 
[ 24.900222] CPU: L2 cache: 2048K 
[ 24.900224] CPU 1/1 -> Node 0 
[ 24.900226] CPU: Physical Processor ID: 0 
[ 24.900227] CPU: Processor Core ID: 1 
[ 24.900232] CPU1: Thermal monitoring enabled (TM2) 
[ 24.900502] Intel(R) Core(TM)2 CPU 6400 @ 2.13GHz stepping 06 
[ 24.904228] Brought up 2 CPUs 
[ 24.904267] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer. 
[ 24.904269] time.c: Detected 2136.990 MHz processor. 
[ 24.945797] migration_cost=36 
[ 24.946070] Time: 18:37:52 Date: 07/15/107 
[ 24.946099] NET: Registered protocol family 16 
[ 24.946164] ACPI: bus type pci registered 
[ 24.946170] PCI: Using configuration type 1 
[ 24.955246] ACPI: Interpreter enabled 
[ 24.955248] ACPI: Using IOAPIC for interrupt routing 
[ 24.956212] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[ 24.956217] PCI: Probing PCI hardware (bus 00) 
[ 24.956751] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO 
[ 24.956755] PCI quirk: region 0480-04bf claimed by ICH6 GPIO 
[ 24.956943] Boot video device is 0000:04:00.0 
[ 24.957321] PCI: Transparent bridge - 0000:00:1e.0 
[ 24.957369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[ 24.959516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT] 
[ 24.959787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT] 
[ 24.960088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT] 
[ 24.960734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT] 
[ 24.967349] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[ 24.967577] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[ 24.967804] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15) 
[ 24.968030] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[ 24.968278] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15) 
[ 24.968503] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[ 24.968728] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[ 24.968957] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15) 
[ 24.969048] Linux Plug and Play Support v0.97 (c) Adam Belay 
[ 24.969056] pnp: PnP ACPI init 
[ 24.974239] pnp: PnP ACPI: found 18 devices 
[ 24.974287] PCI: Using ACPI for IRQ routing 
[ 24.974289] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report 
[ 24.974363] NET: Registered protocol family 8 
[ 24.974364] NET: Registered protocol family 20 
[ 24.974374] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[ 24.974377] hpet0: 3 64-bit timers, 14318180 Hz 
[ 24.975388] PCI-GART: No AMD northbridge found. 
[ 24.976035] pnp: 00:08: ioport range 0x290-0x297 has been reserved 
[ 24.976335] PCI: Bridge: 0000:00:01.0 
[ 24.976337] IO window: e000-efff 
[ 24.976340] MEM window: dcf00000-deffffff 
[ 24.976343] PREFETCH window: e0000000-efffffff 
[ 24.976345] PCI: Bridge: 0000:00:1c.0 
[ 24.976348] IO window: d000-dfff 
[ 24.976351] MEM window: disabled. 
[ 24.976354] PREFETCH window: disabled. 
[ 24.976358] PCI: Bridge: 0000:00:1c.3 
[ 24.976360] IO window: c000-cfff 
[ 24.976364] MEM window: dce00000-dcefffff 
[ 24.976367] PREFETCH window: disabled. 
[ 24.976371] PCI: Bridge: 0000:00:1e.0 
[ 24.976373] IO window: b000-bfff 
[ 24.976377] MEM window: disabled. 
[ 24.976380] PREFETCH window: df000000-dfffffff 
[ 24.976392] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 24.976396] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[ 24.976410] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16 
[ 24.976414] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[ 24.976428] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19 
[ 24.976432] PCI: Setting latency timer of device 0000:00:1c.3 to 64 
[ 24.976440] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[ 24.976471] NET: Registered protocol family 2 
[ 25.024476] IP route cache hash table entries: 65536 (order: 7, 524288 bytes) 
[ 25.024658] TCP established hash table entries: 262144 (order: 10, 4194304 bytes) 
[ 25.026991] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[ 25.027708] TCP: Hash tables configured (established 262144 bind 65536) 
[ 25.027710] TCP reno registered 
[ 25.040685] checking if image is initramfs... it is 
[ 25.657885] Freeing initrd memory: 7305k freed 
[ 25.661332] audit: initializing netlink socket (disabled) 
[ 25.661350] audit(1187203072.320:1): initialized 
[ 25.661510] VFS: Disk quotas dquot_6.5.1 
[ 25.661528] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[ 25.661577] io scheduler noop registered 
[ 25.661579] io scheduler anticipatory registered 
[ 25.661581] io scheduler deadline registered 
[ 25.661592] io scheduler cfq registered (default) 
[ 25.661807] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[ 25.661834] assign_interrupt_mode Found MSI capability 
[ 25.661837] Allocate Port Service[0000:00:01.0:pcie00] 
[ 25.661905] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[ 25.661938] assign_interrupt_mode Found MSI capability 
[ 25.661940] Allocate Port Service[0000:00:1c.0:pcie00] 
[ 25.661970] Allocate Port Service[0000:00:1c.0:pcie02] 
[ 25.662048] PCI: Setting latency timer of device 0000:00:1c.3 to 64 
[ 25.662080] assign_interrupt_mode Found MSI capability 
[ 25.662082] Allocate Port Service[0000:00:1c.3:pcie00] 
[ 25.680226] Real Time Clock Driver v1.12ac 
[ 25.680411] hpet_resources: 0xfed00000 is busy 
[ 25.680431] Linux agpgart interface v0.102 (c) Dave Jones 
[ 25.680434] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[ 25.680902] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 25.681439] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 25.681546] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 21 (level, low) -> IRQ 21 
[ 25.681553] ACPI: PCI interrupt for device 0000:01:01.0 disabled 
[ 25.681607] mice: PS/2 mouse device common for all mice 
[ 25.682071] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[ 25.682196] input: Macintosh mouse button emulation as /class/input/input0 
[ 25.682225] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[ 25.682228] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[ 25.682395] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12 
[ 25.682397] PNP: PS/2 controller doesn't have KBD irq; using default 1 
[ 25.685081] serio: i8042 KBD port at 0x60,0x64 irq 1 
[ 25.685084] serio: i8042 AUX port at 0x60,0x64 irq 12 
[ 25.685161] TCP cubic registered 
[ 25.685169] NET: Registered protocol family 1 
[ 25.685255] ACPI: (supports S0 S1 S3 S4 S5) 
[ 25.685294] Magic number: 3:629:645 
[ 25.685333] hash matches device ptyda 
[ 25.685384] drivers/rtc/hctosys.c: unable to open rtc device (rtc0) 
[ 25.685442] Freeing unused kernel memory: 304k freed 
[ 26.821782] Capability LSM initialized 
[ 26.848979] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ AMI] OemTableId [ CPU1PM] [20060707] 
[ 26.849267] ACPI: Processor [CPU1] (supports 8 throttling states) 
[ 26.849432] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ AMI] OemTableId [ CPU2PM] [20060707] 
[ 26.849702] ACPI: Processor [CPU2] (supports 8 throttling states) 
[ 26.849708] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
[ 26.849713] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707] 
[ 27.153563] usbcore: registered new interface driver usbfs 
[ 27.153592] usbcore: registered new interface driver hub 
[ 27.184799] SCSI subsystem initialized 
[ 27.188433] libata version 2.20 loaded. 
[ 27.189447] ata_piix 0000:00:1f.1: version 2.10ac1 
[ 27.189464] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22 
[ 27.189480] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[ 27.189518] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14 
[ 27.189563] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15 
[ 27.189578] scsi0 : ata_piix 
[ 27.189723] usbcore: registered new device driver usb 
[ 27.198711] USB Universal Host Controller Interface driver v3.0 
[ 27.213676] Floppy drive(s): fd0 is 1.44M 
[ 27.232245] FDC 0 is a post-1991 82077 
[ 27.511296] ata1.00: ATAPI, max UDMA/66 
[ 27.676197] ata1.00: configured for UDMA/66 
[ 27.676207] scsi1 : ata_piix 
[ 27.844195] ATA: abnormal status 0x7F on port 0x0000000000010177 
[ 27.850549] scsi 0:0:0:0: CD-ROM PIONEER DVD-RW DVR-111D 1.23 PQ: 0 ANSI: 5 
[ 27.851796] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ] 
[ 27.851818] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 23 (level, low) -> IRQ 23 
[ 27.851832] PCI: Setting latency timer of device 0000:00:1f.2 to 64 
[ 27.851856] ata3: SATA max UDMA/133 cmd 0x000000000001a800 ctl 0x000000000001a402 bmdma 0x0000000000019400 irq 23 
[ 27.851875] ata4: SATA max UDMA/133 cmd 0x000000000001a000 ctl 0x0000000000019802 bmdma 0x0000000000019408 irq 23 
[ 27.851886] scsi2 : ata_piix 
[ 28.019211] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168 
[ 28.019216] ata3.00: ATA-7: Hitachi HDT725025VLA380, V5DOA52A, max UDMA/133 
[ 28.019219] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[ 28.031287] ata3.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168 
[ 28.031291] ata3.00: configured for UDMA/133 
[ 28.031296] scsi3 : ata_piix 
[ 28.198556] ATA: abnormal status 0x7F on port 0x000000000001a007 
[ 28.198616] scsi 2:0:0:0: Direct-Access ATA Hitachi HDT72502 V5DO PQ: 0 ANSI: 5 
[ 28.199808] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20 
[ 28.199816] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[ 28.199819] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[ 28.200031] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[ 28.200055] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008000 
[ 28.200855] usb usb1: configuration #1 chosen from 1 choice 
[ 28.200983] hub 1-0:1.0: USB hub found 
[ 28.200988] hub 1-0:1.0: 2 ports detected 
[ 28.304962] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17 
[ 28.304973] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[ 28.304977] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[ 28.305000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[ 28.305026] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00008400 
[ 28.305117] usb usb2: configuration #1 chosen from 1 choice 
[ 28.305138] hub 2-0:1.0: USB hub found 
[ 28.305142] hub 2-0:1.0: 2 ports detected 
[ 28.409933] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18 
[ 28.409943] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[ 28.409946] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[ 28.409968] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[ 28.409992] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008800 
[ 28.410079] usb usb3: configuration #1 chosen from 1 choice 
[ 28.410111] hub 3-0:1.0: USB hub found 
[ 28.410115] hub 3-0:1.0: 2 ports detected 
[ 28.514700] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19 
[ 28.514710] PCI: Setting latency timer of device 0000:00:1d.3 to 64 
[ 28.514713] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[ 28.514733] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[ 28.514757] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009000 
[ 28.514842] usb usb4: configuration #1 chosen from 1 choice 
[ 28.514876] hub 4-0:1.0: USB hub found 
[ 28.514883] hub 4-0:1.0: 2 ports detected 
[ 28.546770] usb 1-2: new low speed USB device using uhci_hcd and address 2 
[ 28.619317] r8169 Gigabit Ethernet driver 2.2LK loaded 
[ 28.619340] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19 
[ 28.619369] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[ 28.619554] eth0: RTL8168b/8111b at 0xffffc2000000e000, 00:18:f3:65:44:fa, IRQ 19 
[ 28.626520] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20 
[ 28.626534] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[ 28.626537] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[ 28.626569] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[ 28.626598] ehci_hcd 0000:00:1d.7: debug port 1 
[ 28.626603] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[ 28.626609] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdcdffc00 
[ 28.630494] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[ 28.630589] usb usb5: configuration #1 chosen from 1 choice 
[ 28.630613] hub 5-0:1.0: USB hub found 
[ 28.630620] hub 5-0:1.0: 8 ports detected 
[ 28.769716] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray 
[ 28.769721] Uniform CD-ROM driver Revision: 3.20 
[ 28.769900] sr 0:0:0:0: Attached scsi CD-ROM sr0 
[ 28.770142] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB) 
[ 28.770151] sda: Write Protect is off 
[ 28.770153] sda: Mode Sense: 00 3a 00 00 
[ 28.770164] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 28.770196] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB) 
[ 28.770203] sda: Write Protect is off 
[ 28.770205] sda: Mode Sense: 00 3a 00 00 
[ 28.770216] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 28.770220] sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5 
[ 28.772476] sd 2:0:0:0: Attached scsi generic sg1 type 0 
[ 28.789257] sda1 sda2 < sda5 sda6 > 
[ 28.805166] sd 2:0:0:0: Attached scsi disk sda 
[ 29.035371] Attempting manual resume 
[ 29.035374] swsusp: Resume From Partition 8:5 
[ 29.035376] PM: Checking swsusp image. 
[ 29.035526] PM: Resume from disk failed. 
[ 29.056790] kjournald starting. Commit interval 5 seconds 
[ 29.056802] EXT3-fs: mounted filesystem with ordered data mode. 
[ 29.079071] usb 1-2: device not accepting address 2, error -71 
[ 29.563901] usb 1-2: new low speed USB device using uhci_hcd and address 4 
[ 29.727594] usb 1-2: configuration #1 chosen from 1 choice 
[ 36.919703] r8169: eth0: link up 
[ 36.919711] r8169: eth0: link up 
[ 37.699537] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[ 37.701585] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[ 37.730351] iTCO_vendor_support: vendor-support=0 
[ 37.747396] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006) 
[ 37.813006] agpgart: Detected an Intel 945G Chipset. 
[ 37.839575] agpgart: AGP aperture is 256M @ 0x0 
[ 37.955141] usbcore: registered new interface driver hiddev 
[ 38.019335] parport: PnPBIOS parport detected. 
[ 38.019443] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA] 
[ 38.067634] input: HID 0566:3004 as /class/input/input1 
[ 38.067772] input: USB HID v1.10 Keyboard [HID 0566:3004] on usb-0000:00:1d.0-2 
[ 38.111181] input: HID 0566:3004 as /class/input/input2 
[ 38.111474] input,hiddev96: USB HID v1.10 Device [HID 0566:3004] on usb-0000:00:1d.0-2 
[ 38.111487] usbcore: registered new interface driver usbhid 
[ 38.111489] drivers/usb/input/hid-core.c: v2.6:USB HID core driver 
[ 38.148322] NET: Registered protocol family 17 
[ 38.174007] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17 
[ 38.174024] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102 
[ 38.197414] usbcore: registered new interface driver xpad 
[ 38.197418] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6 
[ 38.364834] input: ImPS/2 Generic Wheel Mouse as /class/input/input3 
[ 38.368216] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860) 
[ 38.368260] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[ 38.372846] input: PC Speaker as /class/input/input4 
[ 38.389825] intel_rng: FWH not detected 
[ 38.502777] fuse init (API version 7. 
[ 38.512403] lp0: using parport0 (interrupt-driven). 
[ 38.547017] Adding 995988k swap on /dev/disk/by-uuid/5ee42704-b7b2-4fff-87c4-14bb6c51bf9f. Priority:-1 extents:1 across:995988k 
[ 38.650273] EXT3 FS on sda6, internal journal 
[ 38.811791] NTFS driver 2.1.28 [Flags: R/O MODULE]. 
[ 38.848684] NTFS volume version 3.1. 
[ 45.114661] input: Power Button (FF) as /class/input/input5 
[ 45.114682] ACPI: Power Button (FF) [PWRF] 
[ 45.114736] input: Power Button (CM) as /class/input/input6 
[ 45.114749] ACPI: Power Button (CM) [PWRB] 
[ 45.144026] No dock devices found. 
[ 45.224482] Using specific hotkey driver 
[ 45.268117] ibm_acpi: ec object not found 
[ 45.324728] pcc_acpi: loading... 
[ 50.233457] ppdev: user-space parallel port driver 
[ 50.879125] Bluetooth: Core ver 2.11 
[ 50.879487] NET: Registered protocol family 31 
[ 50.879490] Bluetooth: HCI device and connection manager initialized 
[ 50.879493] Bluetooth: HCI socket layer initialized 
[ 50.910943] Bluetooth: L2CAP ver 2.8 
[ 50.910947] Bluetooth: L2CAP socket layer initialized 
[ 51.019049] Bluetooth: RFCOMM socket layer initialized 
[ 51.019064] Bluetooth: RFCOMM TTY layer initialized 
[ 51.019066] Bluetooth: RFCOMM ver 1.8 
[ 79.194104] NET: Registered protocol family 10 
[ 79.194200] lo: Disabled Privacy Extensions 
[ 89.580925] eth0: no IPv6 routers present 
[ 190.912004] r8169: eth0: link up 
[ 201.721522] eth0: no IPv6 routers present 
[ 205.084915] r8169: eth0: link up 
[ 215.168317] eth0: no IPv6 routers present 
[ 351.796954] PPP generic driver version 2.4.2 
[ 351.800470] NET: Registered protocol family 24 
[ 642.184715] ip_tables: (C) 2000-2006 Netfilter Core Team 
[ 2163.871087] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.871094] Additional sense: Medium not present 
[ 2163.871101] end_request: I/O error, dev sr0, sector 0 
[ 2163.871105] Buffer I/O error on device sr0, logical block 0 
[ 2163.871110] Buffer I/O error on device sr0, logical block 1 
[ 2163.871114] Buffer I/O error on device sr0, logical block 2 
[ 2163.871118] Buffer I/O error on device sr0, logical block 3 
[ 2163.871122] Buffer I/O error on device sr0, logical block 4 
[ 2163.871125] Buffer I/O error on device sr0, logical block 5 
[ 2163.871129] Buffer I/O error on device sr0, logical block 6 
[ 2163.871133] Buffer I/O error on device sr0, logical block 7 
[ 2163.877060] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.877064] Additional sense: Medium not present 
[ 2163.877071] end_request: I/O error, dev sr0, sector 0 
[ 2163.877073] Buffer I/O error on device sr0, logical block 0 
[ 2163.877987] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.877991] Additional sense: Medium not present 
[ 2163.877995] end_request: I/O error, dev sr0, sector 4 
[ 2163.877998] Buffer I/O error on device sr0, logical block 1 
[ 2163.883039] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.883043] Additional sense: Medium not present 
[ 2163.883050] end_request: I/O error, dev sr0, sector 0 
[ 2163.883956] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.883960] Additional sense: Medium not present 
[ 2163.883965] end_request: I/O error, dev sr0, sector 4 
[ 2163.889023] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.889029] Additional sense: Medium not present 
[ 2163.889035] end_request: I/O error, dev sr0, sector 0 
[ 2163.889997] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.890002] Additional sense: Medium not present 
[ 2163.890008] end_request: I/O error, dev sr0, sector 4 
[ 2163.894997] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.895002] Additional sense: Medium not present 
[ 2163.895008] end_request: I/O error, dev sr0, sector 0 
[ 2163.895916] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.895920] Additional sense: Medium not present 
[ 2163.895926] end_request: I/O error, dev sr0, sector 4 
[ 2163.900975] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.900979] Additional sense: Medium not present 
[ 2163.900984] end_request: I/O error, dev sr0, sector 0 
[ 2163.901891] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready 
[ 2163.901895] Additional sense: Medium not present 
[ 2163.901900] end_request: I/O error, dev sr0, sector 4 
javier@JHR:~$
Any help would be greatly appreciated. Thanks in advance
                       Javier

---

### Post by livestockPimp on 2007-08-24
was the eth0 showing before you compiled the drivers? ubuntu's hotplug can pickup the wrong drivers, I would run "lsmod" and ensure that there are no other network drivers, I would even rmmod the ones you compiled, once you have no network drivers and eth0 is not there then modprobe in the correct drivers.

if you are getting the wrong drivers automatically been loaded then you can blacklist them in the /etc/modules.blacklist

---

### Post by jhr76 on 2007-08-24
Hi. Eth0 was always showing, even before I first tried to compile the driver, but when I tried to configure it it would give me an error, something to the effect that the device did not exist or something of the sort, I really don´t recall. The only other network driver was the loopback, but I also remember another one showing on some of my many Ubuntu reinstallations, it sad eth0:avah (or something like that), but I do not believe it shows this time (I´d need to check when I get home).
If I run rmmod to remove all the network drivers (BTW, is that all I have to type or do I need to specify eth0 or something?). Also, about the modprobe command, do I have to recompile the drivers again first and then run it, and if so, with what options or syntax? Thanks again in advance for your reply.
BTW, here are the instructions in the driver´s readme file (I tried them all):
<Quick install with proper kernel settings>

Unpack the tarball :
tar vzxf r1000_vX.YZ.tgz

Change to the directory:
cd r1000_vX.YZ

If you are running the target kernel, then you should be
able to do :

make clean modules (as root or with sudo)
make install
depmod -a

<Force Link Status>

1. Force the link status when insert the driver.
If the user is in the path ~/r1000, the link status can be forced to one of the 5 modes as following command.

#insmod ./src/r1000.ko speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION

,where
SPEED_MODE = 1000 for 1000Mbps
= 100 for 100Mbps
= 10 for 10Mbps
DUPLEX_MODE = 0 for half-duplex
= 1 for full-duplex
NWAY_OPTION = 0 for auto-negotiation off
= 1 for auto-negotiation on
For example:
#insmod ./src/r1000.ko speed=100 duplex=0 autoneg=0
will force PHY to operate in 100Mpbs Half-duplex.

2. Force the link status by using ethtool.
a. Insert the driver first.
b. Make sure that ethtool exists in /sbin.
c. Force the link status as the following command.

#ethtool -s eth? speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION

,where
SPEED_MODE = 1000 for 1000Mbps
= 100 for 100Mbps
= 10 for 10Mbps
DUPLEX_MODE = half for half-duplex
= full for full-duplex
NWAY_OPTION = off for auto-negotiation off
= on for auto-negotiation on

<Advanced feature>

- Supports Jumbo Frame
- Hardware Tx/Rx flow control

---

### Post by livestockPimp on 2007-08-24
you should not need to compile the drivers, but i would rmmod all the drivers related to the "eth0" you currently have present.
and yes, if you have lets say "orinoco" listed when you lsmod and you want to remove it then all you type is "rmmod orinoco". once all the drivers are removed then ensure your eth0 has disappeared by "ifconfig -a |less" and try modprobing in your new drivers. This _should_ be all you need to do.

---

### Post by jhr76 on 2007-08-25
Hi livestockPimp. Your suggestion worked...!!! :) :) :)
I run lsmod and 2 network drivers were showing, r8168 (which I had compiled) and r8169
I run rmmod for both of them and the I run modprobe r8168 and the 100 Mbit led lit up. I run pppoeconf and was able to connect. I am in fact online via Ubuntu right now and running updates on the system. Once they complete I will need to restart and then I´ll know whether the changes stuck or not, or if that other r8169 driver loads automatically again, in which case I will try to black list it as you said...
IF I still have a connection after the udates I will try to install the Nvidia drivers and then Beryl :)
Thanks for all your help...!!! I will post again to let you know whether this was a permanent fix or not

---

### Post by jhr76 on 2007-08-27
Hi. The solution appears to be permanent. I have restarted several times and it still works. The transfer rates during the updates sucked, but that´s another story...
I also managed to install the nvidia drivers, Swiftfox and its plugins and Beryl, though it has some graphical glitches, but that´s a minor inconvenience. Once again, thank you for all your help... :)

---

### Post by zmigliozzi on 2007-08-27
> The Realtek Windows driver disables the NIC at Windows shutdown time. The current linux r8169 driver does not know how to turn on the NIC from this disabled state, therefor the device will not respond, even if the driver loads and reports that the device is up.


Try this hopefully this saves you the time of recompiling/installing drivers
[http://en.opensuse.org/SDB:Realtek_8169_driver_problem](http://en.opensuse.org/SDB:Realtek_8169_driver_problem)

---

