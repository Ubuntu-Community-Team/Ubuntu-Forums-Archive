---
title: "Network needs to be restarted after system reboot to work"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by alecz20 on 2008-11-15
I am running Ubuntustudio, and I have a D-link wireless card "Atheros Communications Inc. AR5212/AR5213"

After I installed it, I configured Network-Manager to connect to the wireless network.

After I reboot the machine, I have no connection, Network manager settings look, good, but no connection.

If I re-enter the network key, the interface is re-configured and the network works.

Alternately, if I execute a gksu /etc/init.d/networking restart the interfaced is re-configured and the network works.

How can I get Ubuntu to use the configuration I give it by default after reboot?

My syslog fragment:
```

Nov 15 17:22:55 vlad-studio kernel: Inspecting /boot/System.map-2.6.24-21-rt
Nov 15 17:22:55 vlad-studio kernel: Loaded 28515 symbols from /boot/System.map-2.6.24-21-rt.
Nov 15 17:22:55 vlad-studio kernel: Symbols match kernel version 2.6.24.
Nov 15 17:22:55 vlad-studio kernel: Loaded 17764 symbols from 75 modules.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Linux version 2.6.24-21-rt (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP PREEMPT RT Wed Oct 22 01:36:03 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098400 (usable)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 0000000000098400 - 00000000000a0000 (reserved)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6e0000 (usable)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 000000007f6e0000 - 000000007f6e3000 (ACPI NVS)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 000000007f6e3000 - 000000007f6f0000 (ACPI data)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 000000007f6f0000 - 000000007f700000 (reserved)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] 1142MB HIGHMEM available.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] 896MB LOWMEM available.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] found SMP MP-table at 000f5f40
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Entering add_active_range(0, 0, 521952) 0 entries of 256 used
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Zone PFN ranges:
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   DMA             0 ->     4096
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   Normal       4096 ->   229376
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   HighMem    229376 ->   521952
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Movable zone start PFN for each node
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]     0:        0 ->   521952
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] On node 0 totalpages: 521952
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   Normal zone: 3080 pages used for memmap
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   Normal zone: 222200 pages, LIFO batch:31
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   HighMem zone: 4000 pages used for memmap
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   HighMem zone: 288576 pages, LIFO batch:31
Nov 15 17:22:55 vlad-studio kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] DMI present.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8310 checksum 0
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: RSDP 000F8310, 0024 (r2 HPQOEM)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: XSDT 7F6E30C0, 0054 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: FACP 7F6E7A80, 00F4 (r3 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: DSDT 7F6E3280, 4798 (r1 HPQOEM SLIC-CPC     1000 MSFT  3000000)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: FACS 7F6E0000, 0040
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: SLIC 7F6E7CC0, 0176 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: HPET 7F6E7E80, 0038 (r1 HPQOEM SLIC-CPC 42302E31 AWRD       98)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: MCFG 7F6E7F00, 003C (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: APIC 7F6E7BC0, 0084 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: SSDT 7F6E8460, 0304 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Processor #0 6:15 APIC version 20
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Processor #1 6:15 APIC version 20
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f700000:70900000)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] swsusp: Registered nosave memory region: 0000000000098000 - 0000000000099000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] swsusp: Registered nosave memory region: 0000000000099000 - 00000000000a0000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514816
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Kernel command line: root=UUID=b39fb4be-6ac9-44c8-bd47-cb9c4d8b478a ro quiet splash
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Initializing CPU#0
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 15 17:22:55 vlad-studio kernel: [    0.000000] Detected 1867.235 MHz processor.
Nov 15 17:22:55 vlad-studio kernel: [   19.435891] Console: colour VGA+ 80x25
Nov 15 17:22:55 vlad-studio kernel: [   19.435895] console [tty0] enabled
Nov 15 17:22:55 vlad-studio kernel: [   19.436093] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   19.436331] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   19.540260] Memory: 2045312k/2087808k available (2225k kernel code, 41168k reserved, 1058k data, 368k init, 1170304k highmem)
Nov 15 17:22:55 vlad-studio kernel: [   19.540268] virtual kernel memory layout:
Nov 15 17:22:55 vlad-studio kernel: [   19.540269]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540270]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540271]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540272]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540273]       .init : 0xc043b000 - 0xc0497000   ( 368 kB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540274]       .data : 0xc032c740 - 0xc0435324   (1058 kB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540275]       .text : 0xc0100000 - 0xc032c740   (2225 kB)
Nov 15 17:22:55 vlad-studio kernel: [   19.540278] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 15 17:22:55 vlad-studio kernel: [   19.540531] hpet clockevent registered
Nov 15 17:22:55 vlad-studio kernel: [   19.600490] Calibrating delay using timer specific routine.. 3736.58 BogoMIPS (lpj=1868292)
Nov 15 17:22:55 vlad-studio kernel: [   19.600533] Security Framework initialized
Nov 15 17:22:55 vlad-studio kernel: [   19.600540] SELinux:  Disabled at boot.
Nov 15 17:22:55 vlad-studio kernel: [   19.600549] AppArmor: AppArmor initialized
Nov 15 17:22:55 vlad-studio kernel: [   19.600553] Failure registering capabilities with primary security module.
Nov 15 17:22:55 vlad-studio kernel: [   19.600568] Mount-cache hash table entries: 512
Nov 15 17:22:55 vlad-studio kernel: [   19.600716] Initializing cgroup subsys ns
Nov 15 17:22:55 vlad-studio kernel: [   19.600721] Initializing cgroup subsys cpuacct
Nov 15 17:22:55 vlad-studio kernel: [   19.600732] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Nov 15 17:22:55 vlad-studio kernel: [   19.600740] monitor/mwait feature present.
Nov 15 17:22:55 vlad-studio kernel: [   19.600741] using mwait in idle threads.
Nov 15 17:22:55 vlad-studio kernel: [   19.600745] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 15 17:22:55 vlad-studio kernel: [   19.600748] CPU: L2 cache: 2048K
Nov 15 17:22:55 vlad-studio kernel: [   19.600750] CPU: Physical Processor ID: 0
Nov 15 17:22:55 vlad-studio kernel: [   19.600751] CPU: Processor Core ID: 0
Nov 15 17:22:55 vlad-studio kernel: [   19.600753] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Nov 15 17:22:55 vlad-studio kernel: [   19.600762] Compat vDSO mapped to ffffe000.
Nov 15 17:22:55 vlad-studio kernel: [   19.600776] Checking 'hlt' instruction... OK.
Nov 15 17:22:55 vlad-studio kernel: [   19.604900] SMP alternatives: switching to UP code
Nov 15 17:22:55 vlad-studio kernel: [   19.606105] Early unpacking initramfs... done
Nov 15 17:22:55 vlad-studio kernel: [   19.917293] ACPI: Core revision 20070126
Nov 15 17:22:55 vlad-studio kernel: [   19.917339] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 15 17:22:55 vlad-studio kernel: [   19.928468] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
Nov 15 17:22:55 vlad-studio kernel: [   19.928486] SMP alternatives: switching to SMP code
Nov 15 17:22:55 vlad-studio kernel: [   19.929044] Booting processor 1/1 eip 3000
Nov 15 17:22:55 vlad-studio kernel: [   19.939271] Initializing CPU#1
Nov 15 17:22:55 vlad-studio kernel: [   19.999181] Calibrating delay using timer specific routine.. 3734.39 BogoMIPS (lpj=1867195)
Nov 15 17:22:55 vlad-studio kernel: [   19.999188] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001 00000000
Nov 15 17:22:55 vlad-studio kernel: [   19.999193] monitor/mwait feature present.
Nov 15 17:22:55 vlad-studio kernel: [   19.999196] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 15 17:22:55 vlad-studio kernel: [   19.999198] CPU: L2 cache: 2048K
Nov 15 17:22:55 vlad-studio kernel: [   19.999199] CPU: Physical Processor ID: 0
Nov 15 17:22:55 vlad-studio kernel: [   19.999201] CPU: Processor Core ID: 1
Nov 15 17:22:55 vlad-studio kernel: [   19.999202] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e3bd 00000000 00000001 00000000
Nov 15 17:22:55 vlad-studio kernel: [   19.999709] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
Nov 15 17:22:55 vlad-studio kernel: [   19.999729] Total of 2 processors activated (7470.97 BogoMIPS).
Nov 15 17:22:55 vlad-studio kernel: [   19.999872] ENABLING IO-APIC IRQs
Nov 15 17:22:55 vlad-studio kernel: [   20.000040] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 15 17:22:55 vlad-studio kernel: [   20.111725] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 15 17:22:55 vlad-studio kernel: [   20.131746] Brought up 2 CPUs
Nov 15 17:22:55 vlad-studio kernel: [   20.131770] CPU0 attaching sched-domain:
Nov 15 17:22:55 vlad-studio kernel: [   20.131772]  domain 0: span 03
Nov 15 17:22:55 vlad-studio kernel: [   20.131774]   groups: 01 02
Nov 15 17:22:55 vlad-studio kernel: [   20.131779] CPU1 attaching sched-domain:
Nov 15 17:22:55 vlad-studio kernel: [   20.131780]  domain 0: span 03
Nov 15 17:22:55 vlad-studio kernel: [   20.131782]   groups: 02 01
Nov 15 17:22:55 vlad-studio kernel: [   20.132011] net_namespace: 76 bytes
Nov 15 17:22:55 vlad-studio kernel: [   20.132019] Booting paravirtualized kernel on bare hardware
Nov 15 17:22:55 vlad-studio kernel: [   20.132456] Time: 17:22:23  Date: 11/15/08
Nov 15 17:22:55 vlad-studio kernel: [   20.132496] NET: Registered protocol family 16
Nov 15 17:22:55 vlad-studio kernel: [   20.132727] EISA bus registered
Nov 15 17:22:55 vlad-studio kernel: [   20.132732] ACPI: bus type pci registered
Nov 15 17:22:55 vlad-studio kernel: [   20.156581] PCI: PCI BIOS revision 3.00 entry at 0xf1ea0, last bus=1
Nov 15 17:22:55 vlad-studio kernel: [   20.156583] PCI: Using configuration type 1
Nov 15 17:22:55 vlad-studio kernel: [   20.156600] Setting up standard PCI resources
Nov 15 17:22:55 vlad-studio kernel: [   20.159589] mtrr: your CPUs had inconsistent fixed MTRR settings
Nov 15 17:22:55 vlad-studio kernel: [   20.159591] mtrr: probably your BIOS does not setup all CPUs.
Nov 15 17:22:55 vlad-studio kernel: [   20.159592] mtrr: corrected configuration.
Nov 15 17:22:55 vlad-studio kernel: [   20.161084] ACPI: EC: Look up EC in DSDT
Nov 15 17:22:55 vlad-studio kernel: [   20.165736] ACPI: Interpreter enabled
Nov 15 17:22:55 vlad-studio kernel: [   20.165742] ACPI: (supports S0 S1 S3 S4 S5)
Nov 15 17:22:55 vlad-studio kernel: [   20.165771] ACPI: Using IOAPIC for interrupt routing
Nov 15 17:22:55 vlad-studio kernel: [   20.170477] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 15 17:22:55 vlad-studio kernel: [   20.171357] PCI: Transparent bridge - 0000:00:1e.0
Nov 15 17:22:55 vlad-studio kernel: [   20.171378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 15 17:22:55 vlad-studio kernel: [   20.171571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Nov 15 17:22:55 vlad-studio kernel: [   20.182528] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.182640] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.182758] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.182868] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.182977] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *7 9 10 11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.183088] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Nov 15 17:22:55 vlad-studio kernel: [   20.183198] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
Nov 15 17:22:55 vlad-studio kernel: [   20.183308] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
Nov 15 17:22:55 vlad-studio kernel: [   20.183461] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 15 17:22:55 vlad-studio kernel: [   20.183496] pnp: PnP ACPI init
Nov 15 17:22:55 vlad-studio kernel: [   20.183504] ACPI: bus type pnp registered
Nov 15 17:22:55 vlad-studio kernel: [   20.185466] pnpacpi: exceeded the max number of mem resources: 12
Nov 15 17:22:55 vlad-studio kernel: [   20.185533] pnp: PnP ACPI: found 13 devices
Nov 15 17:22:55 vlad-studio kernel: [   20.185535] ACPI: ACPI bus type pnp unregistered
Nov 15 17:22:55 vlad-studio kernel: [   20.185539] PnPBIOS: Disabled by ACPI PNP
Nov 15 17:22:55 vlad-studio kernel: [   20.185795] PCI: Using ACPI for IRQ routing
Nov 15 17:22:55 vlad-studio kernel: [   20.185797] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 15 17:22:55 vlad-studio kernel: [   20.204855] NET: Registered protocol family 8
Nov 15 17:22:55 vlad-studio kernel: [   20.204857] NET: Registered protocol family 20
Nov 15 17:22:55 vlad-studio kernel: [   20.204920] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 15 17:22:55 vlad-studio kernel: [   20.204925] hpet0: 3 64-bit timers, 14318180 Hz
Nov 15 17:22:55 vlad-studio kernel: [   20.205987] AppArmor: AppArmor Filesystem Enabled
Nov 15 17:22:55 vlad-studio kernel: [   20.213380] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213387] system 00:01: ioport range 0x800-0x87f has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213390] system 00:01: ioport range 0x294-0x297 has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213393] system 00:01: ioport range 0x880-0x88f has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213405] system 00:09: ioport range 0x400-0x4bf has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213413] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213421] system 00:0c: iomem range 0xd0800-0xd3fff has been reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213424] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213427] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213430] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213433] system 00:0c: iomem range 0xfed00000-0xfed000ff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213437] system 00:0c: iomem range 0x7f6e0000-0x7f6fffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213440] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213443] system 00:0c: iomem range 0x100000-0x7f6dffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213446] system 00:0c: iomem range 0x0-0x0 could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213449] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213453] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.213456] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
Nov 15 17:22:55 vlad-studio kernel: [   20.243917] PCI: Bridge: 0000:00:1e.0
Nov 15 17:22:55 vlad-studio kernel: [   20.243919]   IO window: disabled.
Nov 15 17:22:55 vlad-studio kernel: [   20.243923]   MEM window: fdd00000-fdefffff
Nov 15 17:22:55 vlad-studio kernel: [   20.243927]   PREFETCH window: disabled.
Nov 15 17:22:55 vlad-studio kernel: [   20.243940] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov 15 17:22:55 vlad-studio kernel: [   20.243963] NET: Registered protocol family 2
Nov 15 17:22:55 vlad-studio kernel: [   20.278615] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   20.278847] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   20.279394] TCP bind hash table entries: 65536 (order: 9, 2359296 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   20.280698] TCP: Hash tables configured (established 131072 bind 65536)
Nov 15 17:22:55 vlad-studio kernel: [   20.280703] TCP reno registered
Nov 15 17:22:55 vlad-studio kernel: [   20.292478] checking if image is initramfs... it is
Nov 15 17:22:55 vlad-studio kernel: [   29.885300] Freeing initrd memory: 7380k freed
Nov 15 17:22:55 vlad-studio kernel: [   29.886237] audit: initializing netlink socket (disabled)
Nov 15 17:22:55 vlad-studio kernel: [   29.886254] audit(1226769752.221:1): initialized
Nov 15 17:22:55 vlad-studio kernel: [   29.886318] krcupreemptd setsched 0
Nov 15 17:22:55 vlad-studio kernel: [   29.886322]   prio = 98
Nov 15 17:22:55 vlad-studio kernel: [   29.886479] highmem bounce pool size: 64 pages
Nov 15 17:22:55 vlad-studio kernel: [   29.886556] VFS: Disk quotas dquot_6.5.1
Nov 15 17:22:55 vlad-studio kernel: [   29.886580] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 15 17:22:55 vlad-studio kernel: [   29.886667] io scheduler noop registered
Nov 15 17:22:55 vlad-studio kernel: [   29.886669] io scheduler anticipatory registered
Nov 15 17:22:55 vlad-studio kernel: [   29.886671] io scheduler deadline registered
Nov 15 17:22:55 vlad-studio kernel: [   29.886680] io scheduler cfq registered (default)
Nov 15 17:22:55 vlad-studio kernel: [   29.886692] Boot video device is 0000:00:02.0
Nov 15 17:22:55 vlad-studio kernel: [   29.887058] isapnp: Scanning for PnP cards...
Nov 15 17:22:55 vlad-studio kernel: [   30.243222] isapnp: No Plug & Play device found
Nov 15 17:22:55 vlad-studio kernel: [   30.271083] Real Time Clock Driver v1.12ac
Nov 15 17:22:55 vlad-studio kernel: [   30.271261] hpet_resources: 0xfed00000 is busy
Nov 15 17:22:55 vlad-studio kernel: [   30.271304] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 15 17:22:55 vlad-studio kernel: [   30.272621] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 15 17:22:55 vlad-studio kernel: [   30.272708] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 15 17:22:55 vlad-studio kernel: [   30.272819] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Nov 15 17:22:55 vlad-studio kernel: [   30.275329] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 15 17:22:55 vlad-studio kernel: [   30.275334] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 15 17:22:55 vlad-studio kernel: [   30.283599] mice: PS/2 mouse device common for all mice
Nov 15 17:22:55 vlad-studio kernel: [   30.283747] EISA: Probing bus 0 at eisa.0
Nov 15 17:22:55 vlad-studio kernel: [   30.283778] EISA: Detected 0 cards.
Nov 15 17:22:55 vlad-studio kernel: [   30.283780] cpuidle: using governor ladder
Nov 15 17:22:55 vlad-studio kernel: [   30.283857] NET: Registered protocol family 1
Nov 15 17:22:55 vlad-studio kernel: [   30.283884] Using IPI No-Shortcut mode
Nov 15 17:22:55 vlad-studio kernel: [   30.283914] registered taskstats version 1
Nov 15 17:22:55 vlad-studio kernel: [   30.284013]   Magic number: 0:783:390
Nov 15 17:22:55 vlad-studio kernel: [   30.284095] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 15 17:22:55 vlad-studio kernel: [   30.284097] EDD information not available.
Nov 15 17:22:55 vlad-studio kernel: [   30.284252] Freeing unused kernel memory: 368k freed
Nov 15 17:22:55 vlad-studio kernel: [   30.310407] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 15 17:22:55 vlad-studio kernel: [   31.495602] fuse init (API version 7.9)
Nov 15 17:22:55 vlad-studio kernel: [   31.500883] ACPI: Fan [FAN] (on)
Nov 15 17:22:55 vlad-studio kernel: [   31.506606] ACPI: SSDT 7F6E7F80, 0175 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [   31.506914] ACPI: SSDT 7F6E8390, 00CE (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
Nov 15 17:22:55 vlad-studio kernel: [   31.507065] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 15 17:22:55 vlad-studio kernel: [   31.507077] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 15 17:22:55 vlad-studio kernel: [   31.508524] ACPI: Thermal Zone [THRM] (25 C)
Nov 15 17:22:55 vlad-studio kernel: [   31.647300] usbcore: registered new interface driver usbfs
Nov 15 17:22:55 vlad-studio kernel: [   31.647322] usbcore: registered new interface driver hub
Nov 15 17:22:55 vlad-studio kernel: [   31.647510] usbcore: registered new device driver usb
Nov 15 17:22:55 vlad-studio kernel: [   31.675142] USB Universal Host Controller Interface driver v3.0
Nov 15 17:22:55 vlad-studio kernel: [   31.675202] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 16
Nov 15 17:22:55 vlad-studio kernel: [   31.675213] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov 15 17:22:55 vlad-studio kernel: [   31.675217] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 15 17:22:55 vlad-studio kernel: [   31.675995] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Nov 15 17:22:55 vlad-studio kernel: [   31.676910] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000fe00
Nov 15 17:22:55 vlad-studio kernel: [   31.677048] usb usb1: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   31.677072] hub 1-0:1.0: USB hub found
Nov 15 17:22:55 vlad-studio kernel: [   31.677078] hub 1-0:1.0: 2 ports detected
Nov 15 17:22:55 vlad-studio kernel: [   31.777644] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Nov 15 17:22:55 vlad-studio kernel: [   31.777655] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov 15 17:22:55 vlad-studio kernel: [   31.777659] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 15 17:22:55 vlad-studio kernel: [   31.777682] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Nov 15 17:22:55 vlad-studio kernel: [   31.778307] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000fd00
Nov 15 17:22:55 vlad-studio kernel: [   31.778421] usb usb2: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   31.778445] hub 2-0:1.0: USB hub found
Nov 15 17:22:55 vlad-studio kernel: [   31.778453] hub 2-0:1.0: 2 ports detected
Nov 15 17:22:55 vlad-studio kernel: [   31.878589] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Nov 15 17:22:55 vlad-studio kernel: [   31.878600] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov 15 17:22:55 vlad-studio kernel: [   31.878604] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 15 17:22:55 vlad-studio kernel: [   31.878629] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Nov 15 17:22:55 vlad-studio kernel: [   31.878745] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
Nov 15 17:22:55 vlad-studio kernel: [   31.878865] usb usb3: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   31.878892] hub 3-0:1.0: USB hub found
Nov 15 17:22:55 vlad-studio kernel: [   31.878898] hub 3-0:1.0: 2 ports detected
Nov 15 17:22:55 vlad-studio kernel: [   31.979779] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
Nov 15 17:22:55 vlad-studio kernel: [   31.979790] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov 15 17:22:55 vlad-studio kernel: [   31.979794] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 15 17:22:55 vlad-studio kernel: [   31.979820] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Nov 15 17:22:55 vlad-studio kernel: [   31.980002] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000fb00
Nov 15 17:22:55 vlad-studio kernel: [   31.980120] usb usb4: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   31.980145] hub 4-0:1.0: USB hub found
Nov 15 17:22:55 vlad-studio kernel: [   31.980150] hub 4-0:1.0: 2 ports detected
Nov 15 17:22:55 vlad-studio kernel: [   32.286507] usb 4-1: new full speed USB device using uhci_hcd and address 2
Nov 15 17:22:55 vlad-studio kernel: [   32.313996] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 16
Nov 15 17:22:55 vlad-studio kernel: [   32.314009] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov 15 17:22:55 vlad-studio kernel: [   32.314012] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 15 17:22:55 vlad-studio kernel: [   32.314046] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Nov 15 17:22:55 vlad-studio kernel: [   32.317951] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Nov 15 17:22:55 vlad-studio kernel: [   32.317960] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xfdfff000
Nov 15 17:22:55 vlad-studio kernel: [   32.402439] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 15 17:22:55 vlad-studio kernel: [   32.402568] usb usb5: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   32.402595] hub 5-0:1.0: USB hub found
Nov 15 17:22:55 vlad-studio kernel: [   32.402602] hub 5-0:1.0: 8 ports detected
Nov 15 17:22:55 vlad-studio kernel: [   32.513061] SCSI subsystem initialized
Nov 15 17:22:55 vlad-studio kernel: [   32.804203] usb 4-1: device not accepting address 2, error -71
Nov 15 17:22:55 vlad-studio kernel: [   32.849986] libata version 3.00 loaded.
Nov 15 17:22:55 vlad-studio kernel: [   33.006270] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Nov 15 17:22:55 vlad-studio kernel: [   33.006304] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov 15 17:22:55 vlad-studio kernel: [   33.006314] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Nov 15 17:22:55 vlad-studio kernel: [   33.048100] ahci 0000:00:1f.2: version 3.0
Nov 15 17:22:55 vlad-studio kernel: [   33.048125] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Nov 15 17:22:55 vlad-studio kernel: [   33.061058] usb 5-7: new high speed USB device using ehci_hcd and address 2
Nov 15 17:22:55 vlad-studio kernel: [   33.194610] usb 5-7: configuration #1 chosen from 1 choice
Nov 15 17:22:55 vlad-studio kernel: [   34.048486] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
Nov 15 17:22:55 vlad-studio kernel: [   34.048491] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
Nov 15 17:22:55 vlad-studio kernel: [   34.048495] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Nov 15 17:22:55 vlad-studio kernel: [   34.048774] scsi0 : ahci
Nov 15 17:22:55 vlad-studio kernel: [   34.049322] scsi1 : ahci
Nov 15 17:22:55 vlad-studio kernel: [   34.049405] scsi2 : ahci
Nov 15 17:22:55 vlad-studio kernel: [   34.049472] scsi3 : ahci
Nov 15 17:22:55 vlad-studio kernel: [   34.049563] ata1: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 223
Nov 15 17:22:55 vlad-studio kernel: [   34.049567] ata2: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 223
Nov 15 17:22:55 vlad-studio kernel: [   34.049570] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 223
Nov 15 17:22:55 vlad-studio kernel: [   34.049573] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 223
Nov 15 17:22:55 vlad-studio kernel: [   34.352042] ata1: SATA link down (SStatus 0 SControl 300)
Nov 15 17:22:55 vlad-studio kernel: [   34.364777] usbcore: registered new interface driver libusual
Nov 15 17:22:55 vlad-studio kernel: [   34.370044] Initializing USB Mass Storage driver...
Nov 15 17:22:55 vlad-studio kernel: [   34.370988] scsi4 : SCSI emulation for USB Mass Storage devices
Nov 15 17:22:55 vlad-studio kernel: [   34.371096] usb-storage: device found at 2
Nov 15 17:22:55 vlad-studio kernel: [   34.371098] usb-storage: waiting for device to settle before scanning
Nov 15 17:22:55 vlad-studio kernel: [   34.371105] usbcore: registered new interface driver usb-storage
Nov 15 17:22:55 vlad-studio kernel: [   34.371109] USB Mass Storage support registered.
Nov 15 17:22:55 vlad-studio kernel: [   34.654882] ata2: SATA link down (SStatus 0 SControl 300)
Nov 15 17:22:55 vlad-studio kernel: [   34.957703] ata3: SATA link down (SStatus 0 SControl 300)
Nov 15 17:22:55 vlad-studio kernel: [   35.413678] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 15 17:22:55 vlad-studio kernel: [   35.414414] ata4.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100
Nov 15 17:22:55 vlad-studio kernel: [   35.414417] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 15 17:22:55 vlad-studio kernel: [   35.415334] ata4.00: configured for UDMA/100
Nov 15 17:22:55 vlad-studio kernel: [   35.415496] scsi 3:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5
Nov 15 17:22:55 vlad-studio kernel: [   35.415725] ata_piix 0000:00:1f.1: version 2.12
Nov 15 17:22:55 vlad-studio kernel: [   35.415740] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Nov 15 17:22:55 vlad-studio kernel: [   35.415771] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Nov 15 17:22:55 vlad-studio kernel: [   35.415905] scsi5 : ata_piix
Nov 15 17:22:55 vlad-studio kernel: [   35.416074] scsi6 : ata_piix
Nov 15 17:22:55 vlad-studio kernel: [   35.417069] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
Nov 15 17:22:55 vlad-studio kernel: [   35.417073] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
Nov 15 17:22:55 vlad-studio kernel: [   35.423909] Driver 'sd' needs updating - please use bus_type methods
Nov 15 17:22:55 vlad-studio kernel: [   35.423990] sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Nov 15 17:22:55 vlad-studio kernel: [   35.424003] sd 3:0:0:0: [sda] Write Protect is off
Nov 15 17:22:55 vlad-studio kernel: [   35.424005] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 15 17:22:55 vlad-studio kernel: [   35.424023] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 17:22:55 vlad-studio kernel: [   35.424073] sd 3:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Nov 15 17:22:55 vlad-studio kernel: [   35.424084] sd 3:0:0:0: [sda] Write Protect is off
Nov 15 17:22:55 vlad-studio kernel: [   35.424086] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 15 17:22:55 vlad-studio kernel: [   35.424105] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 15 17:22:55 vlad-studio kernel: [   35.424108]  sda: sda1 sda2 < sda5 sda6 sda7 >
Nov 15 17:22:55 vlad-studio kernel: [   35.479010] sd 3:0:0:0: [sda] Attached SCSI disk
Nov 15 17:22:55 vlad-studio kernel: [   35.484114] sd 3:0:0:0: Attached scsi generic sg0 type 0
Nov 15 17:22:55 vlad-studio kernel: [   35.567435] ata6: port disabled. ignoring.
Nov 15 17:22:55 vlad-studio kernel: [   35.567530] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 20 (level, low) -> IRQ 20
Nov 15 17:22:55 vlad-studio kernel: [   35.623232] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
Nov 15 17:22:55 vlad-studio kernel: [   36.073586] Attempting manual resume
Nov 15 17:22:55 vlad-studio kernel: [   36.073589] swsusp: Resume From Partition 8:7
Nov 15 17:22:55 vlad-studio kernel: [   36.073591] PM: Checking swsusp image.
Nov 15 17:22:55 vlad-studio kernel: [   36.073743] PM: Resume from disk failed.
Nov 15 17:22:55 vlad-studio kernel: [   36.109132] kjournald starting.  Commit interval 5 seconds
Nov 15 17:22:55 vlad-studio kernel: [   36.109143] EXT3-fs: mounted filesystem with ordered data mode.
Nov 15 17:22:55 vlad-studio kernel: [   36.887939] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001029b0e]
Nov 15 17:22:55 vlad-studio kernel: [   39.368547] usb-storage: device scan complete
Nov 15 17:22:55 vlad-studio kernel: [   39.375040] scsi 4:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
Nov 15 17:22:55 vlad-studio kernel: [   39.381532] scsi 4:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
Nov 15 17:22:55 vlad-studio kernel: [   39.388156] scsi 4:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
Nov 15 17:22:55 vlad-studio kernel: [   39.394772] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
Nov 15 17:22:55 vlad-studio kernel: [   39.396177] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Nov 15 17:22:55 vlad-studio kernel: [   39.396216] sd 4:0:0:0: Attached scsi generic sg1 type 0
Nov 15 17:22:55 vlad-studio kernel: [   39.397297] sd 4:0:0:1: [sdc] Attached SCSI removable disk
Nov 15 17:22:55 vlad-studio kernel: [   39.397332] sd 4:0:0:1: Attached scsi generic sg2 type 0
Nov 15 17:22:55 vlad-studio kernel: [   39.398422] sd 4:0:0:2: [sdd] Attached SCSI removable disk
Nov 15 17:22:55 vlad-studio kernel: [   39.398460] sd 4:0:0:2: Attached scsi generic sg3 type 0
Nov 15 17:22:55 vlad-studio kernel: [   39.399545] sd 4:0:0:3: [sde] Attached SCSI removable disk
Nov 15 17:22:55 vlad-studio kernel: [   39.399579] sd 4:0:0:3: Attached scsi generic sg4 type 0
Nov 15 17:22:55 vlad-studio kernel: [   44.408291] Linux agpgart interface v0.102
Nov 15 17:22:55 vlad-studio kernel: [   44.475658] agpgart: Detected an Intel 945G Chipset.
Nov 15 17:22:55 vlad-studio kernel: [   44.476809] agpgart: Detected 7932K stolen memory.
Nov 15 17:22:55 vlad-studio kernel: [   44.494202] agpgart: AGP aperture is 256M @ 0xe0000000
Nov 15 17:22:55 vlad-studio kernel: [   44.760880] input: PC Speaker as /devices/platform/pcspkr/input/input2
Nov 15 17:22:55 vlad-studio kernel: [   45.918879] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
Nov 15 17:22:55 vlad-studio kernel: [   47.073921] input: Power Button (FF) as /devices/virtual/input/input4
Nov 15 17:22:55 vlad-studio kernel: [   47.089626] ACPI: Power Button (FF) [PWRF]
Nov 15 17:22:55 vlad-studio kernel: [   47.089690] input: Power Button (CM) as /devices/virtual/input/input5
Nov 15 17:22:55 vlad-studio kernel: [   47.106591] ACPI: Power Button (CM) [PWRB]
Nov 15 17:22:55 vlad-studio kernel: [   47.259525] ath_hal: module license 'Proprietary' taints kernel.
Nov 15 17:22:55 vlad-studio kernel: [   47.260655] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Nov 15 17:22:55 vlad-studio kernel: [   47.608081] wlan: 0.9.4
Nov 15 17:22:55 vlad-studio kernel: [   47.709511] ath_pci: 0.9.4
Nov 15 17:22:55 vlad-studio kernel: [   47.709563] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov 15 17:22:55 vlad-studio kernel: [   48.797895] ath_rate_sample: 1.2 (0.9.4)
Nov 15 17:22:55 vlad-studio kernel: [   48.802412] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Nov 15 17:22:55 vlad-studio kernel: [   48.802419] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 15 17:22:55 vlad-studio kernel: [   48.802428] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Nov 15 17:22:55 vlad-studio kernel: [   48.802435] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Nov 15 17:22:55 vlad-studio kernel: [   48.802439] wifi0: mac 7.9 phy 4.5 radio 5.6
Nov 15 17:22:55 vlad-studio kernel: [   48.802443] wifi0: Use hw queue 1 for WME_AC_BE traffic
Nov 15 17:22:55 vlad-studio kernel: [   48.802445] wifi0: Use hw queue 0 for WME_AC_BK traffic
Nov 15 17:22:55 vlad-studio kernel: [   48.802447] wifi0: Use hw queue 2 for WME_AC_VI traffic
Nov 15 17:22:55 vlad-studio kernel: [   48.802449] wifi0: Use hw queue 3 for WME_AC_VO traffic
Nov 15 17:22:55 vlad-studio kernel: [   48.802451] wifi0: Use hw queue 8 for CAB traffic
Nov 15 17:22:55 vlad-studio kernel: [   48.802453] wifi0: Use hw queue 9 for beacons
Nov 15 17:22:55 vlad-studio kernel: [   49.178894] wifi0: Atheros 5212: mem=0xfdee0000, irq=19
Nov 15 17:22:55 vlad-studio kernel: [   49.261236] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 21
Nov 15 17:22:55 vlad-studio kernel: [   49.421176] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/echoaudio/echoaudio.c:47: get_firmware(): Firmware not available (-2)
Nov 15 17:22:55 vlad-studio kernel: [   49.421204] ACPI: PCI interrupt for device 0000:01:05.0 disabled
Nov 15 17:22:55 vlad-studio kernel: [   49.421222] Echoaudio Echo3G: probe of 0000:01:05.0 failed with error -2
Nov 15 17:22:55 vlad-studio kernel: [   49.708904] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov 15 17:22:55 vlad-studio kernel: [   49.708923] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Nov 15 17:22:55 vlad-studio kernel: [   49.717939] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
Nov 15 17:22:55 vlad-studio kernel: [   49.989801] loop: module loaded
Nov 15 17:22:55 vlad-studio kernel: [   50.104600] NET: Registered protocol family 17
Nov 15 17:22:55 vlad-studio kernel: [   50.119797] lp: driver loaded but no devices found
Nov 15 17:22:55 vlad-studio kernel: [   50.272556] Adding 963860k swap on /dev/sda7.  Priority:-1 extents:1 across:963860k
Nov 15 17:22:55 vlad-studio kernel: [   50.844056] EXT3 FS on sda6, internal journal
Nov 15 17:22:55 vlad-studio kernel: [   51.934637] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 15 17:22:55 vlad-studio kernel: [   52.307967] No dock devices found.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Successfully dropped root privileges.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: avahi-daemon 0.6.22 starting up.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Successfully called chroot().
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Successfully dropped remaining capabilities.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: No service file found in /etc/avahi/services.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Network interface enumeration completed.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 15 17:22:55 vlad-studio avahi-daemon[4803]: Server startup complete. Host name is vlad-studio.local. Local service cookie is 204731377.
Nov 15 17:22:55 vlad-studio kernel: [   53.289567] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Nov 15 17:22:55 vlad-studio kernel: [   53.289572] apm: disabled - APM is not SMP safe.
Nov 15 17:22:55 vlad-studio kernel: [   53.412390] ppdev: user-space parallel port driver
Nov 15 17:22:55 vlad-studio kernel: [   53.532149] audit(1226787775.710:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4846 profile="/usr/sbin/cupsd" namespace="default"
Nov 15 17:22:56 vlad-studio hcid[5049]: Bluetooth HCI daemon
Nov 15 17:22:56 vlad-studio kernel: [   54.471296] Bluetooth: Core ver 2.11
Nov 15 17:22:56 vlad-studio kernel: [   54.471904] NET: Registered protocol family 31
Nov 15 17:22:56 vlad-studio kernel: [   54.471907] Bluetooth: HCI device and connection manager initialized
Nov 15 17:22:56 vlad-studio kernel: [   54.471912] Bluetooth: HCI socket layer initialized
Nov 15 17:22:56 vlad-studio hcid[5049]: Starting SDP server
Nov 15 17:22:56 vlad-studio kernel: [   54.484575] Bluetooth: L2CAP ver 2.9
Nov 15 17:22:56 vlad-studio kernel: [   54.484581] Bluetooth: L2CAP socket layer initialized
Nov 15 17:22:56 vlad-studio hcid[5049]: Created local server at unix:abstract=/var/run/dbus-StCvmGmQzG,guid=3756f3d73e64220a67a7923c491f4bc0
Nov 15 17:22:56 vlad-studio audio[5067]: Bluetooth Audio daemon
Nov 15 17:22:56 vlad-studio audio[5067]: Unix socket created: 5
Nov 15 17:22:56 vlad-studio audio[5067]: audio.conf: Key file does not have key 'Enable'
Nov 15 17:22:56 vlad-studio audio[5067]: audio.conf: Key file does not have key 'Disable'
Nov 15 17:22:56 vlad-studio input[5068]: Bluetooth Input daemon
Nov 15 17:22:56 vlad-studio input[5068]: Registered input manager path:/org/bluez/input
Nov 15 17:22:56 vlad-studio kernel: [   54.535697] Bluetooth: RFCOMM socket layer initialized
Nov 15 17:22:56 vlad-studio kernel: [   54.535758] Bluetooth: RFCOMM TTY layer initialized
Nov 15 17:22:56 vlad-studio kernel: [   54.535760] Bluetooth: RFCOMM ver 1.8
Nov 15 17:22:56 vlad-studio audio[5067]: add_service_record: got record id 0x10000
Nov 15 17:22:56 vlad-studio audio[5067]: audio.conf: Key file does not have key 'Disable'
Nov 15 17:22:56 vlad-studio audio[5067]: audio.conf: Key file does not have group 'A2DP'
Nov 15 17:22:56 vlad-studio last message repeated 3 times
Nov 15 17:22:56 vlad-studio audio[5067]: SEP 0x806d308 registered: type:0 codec:0 seid:1
Nov 15 17:22:56 vlad-studio audio[5067]: add_service_record: got record id 0x10001
Nov 15 17:22:56 vlad-studio audio[5067]: add_service_record: got record id 0x10002
Nov 15 17:22:56 vlad-studio audio[5067]: add_service_record: got record id 0x10003
Nov 15 17:22:56 vlad-studio audio[5067]: Registered manager path:/org/bluez/audio
Nov 15 17:22:58 vlad-studio gdm[5111]: WARNING: Didn't understand `' (expected true or false) 
Nov 15 17:22:59 vlad-studio dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
Nov 15 17:22:59 vlad-studio anacron[5151]: Anacron 2.3 started on 2008-11-15
Nov 15 17:22:59 vlad-studio anacron[5151]: Normal exit (0 jobs run)
Nov 15 17:22:59 vlad-studio /usr/sbin/cron[5180]: (CRON) INFO (pidfile fd = 3)
Nov 15 17:22:59 vlad-studio /usr/sbin/cron[5181]: (CRON) STARTUP (fork ok)
Nov 15 17:22:59 vlad-studio /usr/sbin/cron[5181]: (CRON) INFO (Running @reboot jobs)
Nov 15 17:22:59 vlad-studio kernel: [   57.207735] [drm] Initialized drm 1.1.0 20060810
Nov 15 17:22:59 vlad-studio kernel: [   57.210122] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
Nov 15 17:22:59 vlad-studio kernel: [   57.210129] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 15 17:22:59 vlad-studio kernel: [   57.210180] [drm] Initialized i915 1.6.0 20060119 on minor 0
Nov 15 17:23:06 vlad-studio kernel: [   64.343091] NET: Registered protocol family 10
Nov 15 17:23:06 vlad-studio kernel: [   64.343383] lo: Disabled Privacy Extensions
Nov 15 17:23:07 vlad-studio avahi-daemon[4803]: Registering new address record for fe80::211:95ff:fefa:d8e2 on ath0.*.
Nov 15 17:23:09 vlad-studio dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
Nov 15 17:23:16 vlad-studio dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
Nov 15 17:23:16 vlad-studio kernel: [   74.503441] ath0: no IPv6 routers present
Nov 15 17:23:25 vlad-studio dhclient: No DHCPOFFERS received.
Nov 15 17:23:25 vlad-studio dhclient: No working leases in persistent database - sleeping.
Nov 15 17:23:25 vlad-studio avahi-autoipd(ath0)[5485]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Nov 15 17:23:25 vlad-studio avahi-autoipd(ath0)[5485]: Successfully called chroot().
Nov 15 17:23:25 vlad-studio avahi-autoipd(ath0)[5485]: Successfully dropped root privileges.
Nov 15 17:23:25 vlad-studio avahi-autoipd(ath0)[5485]: Starting with address 169.254.11.244
Nov 15 17:23:30 vlad-studio avahi-autoipd(ath0)[5485]: Callout BIND, address 169.254.11.244 on interface ath0
Nov 15 17:23:30 vlad-studio avahi-daemon[4803]: Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.11.244.
Nov 15 17:23:30 vlad-studio avahi-daemon[4803]: New relevant interface ath0.IPv4 for mDNS.
Nov 15 17:23:30 vlad-studio avahi-daemon[4803]: Registering new address record for 169.254.11.244 on ath0.IPv4.
Nov 15 17:23:34 vlad-studio avahi-autoipd(ath0)[5485]: Successfully claimed IP address 169.254.11.244

```

At the end you can see that Ubuntu assigns a random IP to the network card.

When I restart the network, I get this in syslog:
```

Nov 15 17:23:43 vlad-studio dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 5518
Nov 15 17:23:43 vlad-studio dhclient: killed old client process, removed PID file
Nov 15 17:23:43 vlad-studio dhclient: Internet Systems Consortium DHCP Client V3.0.6
Nov 15 17:23:43 vlad-studio dhclient: Copyright 2004-2007 Internet Systems Consortium.
Nov 15 17:23:43 vlad-studio dhclient: All rights reserved.
Nov 15 17:23:43 vlad-studio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 15 17:23:43 vlad-studio dhclient: 
Nov 15 17:23:43 vlad-studio dhclient: wifi0: unknown hardware address type 801
Nov 15 17:23:43 vlad-studio dhclient: wifi0: unknown hardware address type 801
Nov 15 17:23:43 vlad-studio dhclient: Listening on LPF/ath0/00:11:95:fa:d8:e2
Nov 15 17:23:43 vlad-studio dhclient: Sending on   LPF/ath0/00:11:95:fa:d8:e2
Nov 15 17:23:43 vlad-studio dhclient: Sending on   Socket/fallback
Nov 15 17:23:43 vlad-studio dhclient: DHCPRELEASE on ath0 to 192.168.0.1 port 67
Nov 15 17:23:43 vlad-studio avahi-autoipd(ath0)[5485]: Got SIGTERM, quitting.
Nov 15 17:23:43 vlad-studio avahi-autoipd(ath0)[5485]: Callout STOP, address 169.254.11.244 on interface ath0
Nov 15 17:23:43 vlad-studio avahi-daemon[4803]: Withdrawing address record for 169.254.11.244 on ath0.
Nov 15 17:23:43 vlad-studio avahi-daemon[4803]: Leaving mDNS multicast group on interface ath0.IPv4 with address 169.254.11.244.
Nov 15 17:23:43 vlad-studio avahi-daemon[4803]: Interface ath0.IPv4 no longer relevant for mDNS.
Nov 15 17:23:43 vlad-studio avahi-autoipd(ath0)[5486]: client: RTNETLINK answers: No such process
Nov 15 17:23:43 vlad-studio avahi-daemon[4803]: Withdrawing address record for fe80::211:95ff:fefa:d8e2 on ath0.
Nov 15 17:23:43 vlad-studio dhclient: There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Nov 15 17:23:43 vlad-studio dhclient: Internet Systems Consortium DHCP Client V3.0.6
Nov 15 17:23:43 vlad-studio dhclient: Copyright 2004-2007 Internet Systems Consortium.
Nov 15 17:23:43 vlad-studio dhclient: All rights reserved.
Nov 15 17:23:43 vlad-studio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov 15 17:23:43 vlad-studio dhclient: 
Nov 15 17:23:43 vlad-studio dhclient: wifi0: unknown hardware address type 801
Nov 15 17:23:44 vlad-studio ntpdate[5547]: can't find host ntp.ubuntu.com 
Nov 15 17:23:44 vlad-studio ntpdate[5547]: no servers can be used, exiting
Nov 15 17:23:44 vlad-studio dhclient: wifi0: unknown hardware address type 801
Nov 15 17:23:44 vlad-studio dhclient: Listening on LPF/ath0/00:11:95:fa:d8:e2
Nov 15 17:23:44 vlad-studio dhclient: Sending on   LPF/ath0/00:11:95:fa:d8:e2
Nov 15 17:23:44 vlad-studio dhclient: Sending on   Socket/fallback
Nov 15 17:23:44 vlad-studio avahi-daemon[4803]: Registering new address record for fe80::211:95ff:fefa:d8e2 on ath0.*.
Nov 15 17:23:47 vlad-studio dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
Nov 15 17:23:53 vlad-studio dhclient: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
Nov 15 17:23:53 vlad-studio dhclient: DHCPOFFER of 192.168.0.102 from 192.168.0.1
Nov 15 17:23:53 vlad-studio dhclient: DHCPREQUEST of 192.168.0.102 on ath0 to 255.255.255.255 port 67
Nov 15 17:23:53 vlad-studio dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Nov 15 17:23:53 vlad-studio avahi-daemon[4803]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.0.102.
Nov 15 17:23:53 vlad-studio avahi-daemon[4803]: New relevant interface ath0.IPv4 for mDNS.
Nov 15 17:23:53 vlad-studio avahi-daemon[4803]: Registering new address record for 192.168.0.102 on ath0.IPv4.
Nov 15 17:23:53 vlad-studio dhclient: bound to 192.168.0.102 -- renewal in 920695814 seconds.
Nov 15 17:23:53 vlad-studio kernel: [  111.596060] ath0: no IPv6 routers present
Nov 15 17:23:54 vlad-studio ntpdate[5682]: step time server 91.189.94.4 offset 0.995020 sec

```


Edit: Seems like avahi-autoipd assigns a useless ip before dhclient
Any idea how to solve this problem?

---

