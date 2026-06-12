---
title: "Toshiba A105 randomly drops wireless and USB mouse; here's a debug log"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by diablo75 on 2010-09-30
I've been messing around with someone elses laptop who switched to Ubuntu a few months ago.  They love it, except for these little glitches and considering that it's a Toshiba... well, doesn't exactly surprise me.

Anyway, while I was there, we got the wireless adapter working with no problem.  And it continued to work for about the next half hour.  But then it suddenly dropped it's connection, said it was disconnected, and I couldn't get it to reconnect without restarting the system.

They also have a wireless USB mouse that seems to do the same thing:  Works for a bit, then unexpectedly quits.  Removing the dongle from the USB port and plugging it back in does nothing; a restart is require to fix it.

I don't have a debug related to the mouse failing but I THINK I might have something about the wireless adapter failing and if my brains serve me correctly, I remember Toshiba and ACPI always being a problem.  Anyway, I noticed the "ACPI" part of the below and thought it's probably related.  This is all apparently what happened in a matter of a couple of seconds:

```
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] MTRR default type: uncachable
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] MTRR fixed ranges enabled:
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   00000-9FFFF write-back
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   A0000-BFFFF uncachable
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   C0000-CFFFF write-protect
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   D0000-DFFFF uncachable
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   E0000-FFFFF write-protect
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] MTRR variable ranges enabled:
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   0 base 000000000 mask FF0000000 write-back
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   1 base 010000000 mask FF8000000 write-back
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   2 base 018000000 mask FFC000000 write-back
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   3 base 01BF00000 mask FFFF00000 uncachable
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   4 disabled
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   5 disabled
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   6 disabled
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   7 disabled
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]  0000400000 - 001bc00000 page 2M
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]  001bc00000 - 001bea0000 page 4k
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] kernel direct mapping tables up to 1bea0000 @ 10000-15000
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] On node 0 totalpages: 114223
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c1001200
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   Normal zone: 862 pages used for memmap
Sep 30 20:47:38 owner-laptop kernel: [    0.000000]   Normal zone: 109378 pages, LIFO batch:31
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep 30 20:47:38 owner-laptop kernel: [    0.000000] nr_irqs_gsi: 24
Sep 30 20:47:38 owner-laptop kernel: [    0.048339]   alloc irq_desc for 21 on node 0
Sep 30 20:47:38 owner-laptop kernel: [    0.048342]   alloc kstat_irqs on node 0
Sep 30 20:47:38 owner-laptop kernel: [    0.092001] CPU0 attaching NULL sched-domain.
Sep 30 20:47:38 owner-laptop kernel: [    0.092001] ACPI: EC: Look up EC in DSDT
Sep 30 20:47:38 owner-laptop kernel: [    0.153020] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
Sep 30 20:47:38 owner-laptop kernel: [    0.153031] pci 0000:00:12.0: reg 14 io port: [0x8430-0x8433]
Sep 30 20:47:38 owner-laptop kernel: [    0.153042] pci 0000:00:12.0: reg 18 io port: [0x8420-0x8427]
Sep 30 20:47:38 owner-laptop kernel: [    0.153053] pci 0000:00:12.0: reg 1c io port: [0x8410-0x8413]
Sep 30 20:47:38 owner-laptop kernel: [    0.153064] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
Sep 30 20:47:38 owner-laptop kernel: [    0.153075] pci 0000:00:12.0: reg 24 32bit mmio: [0xd0004000-0xd00041ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153087] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153129] pci 0000:00:12.0: supports D1 D2
Sep 30 20:47:38 owner-laptop kernel: [    0.153191] pci 0000:00:13.0: reg 10 32bit mmio: [0xd0005000-0xd0005fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153325] pci 0000:00:13.1: reg 10 32bit mmio: [0xd0006000-0xd0006fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153472] pci 0000:00:13.2: reg 10 32bit mmio: [0xd0007000-0xd0007fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153560] pci 0000:00:13.2: supports D1 D2
Sep 30 20:47:38 owner-laptop kernel: [    0.153622] pci 0000:00:14.0: reg 10 io port: [0x8450-0x845f]
Sep 30 20:47:38 owner-laptop kernel: [    0.153634] pci 0000:00:14.0: reg 14 32bit mmio: [0xd0004400-0xd00047ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.153739] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
Sep 30 20:47:38 owner-laptop kernel: [    0.153750] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
Sep 30 20:47:38 owner-laptop kernel: [    0.153761] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
Sep 30 20:47:38 owner-laptop kernel: [    0.153772] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
Sep 30 20:47:38 owner-laptop kernel: [    0.153783] pci 0000:00:14.1: reg 20 io port: [0x8460-0x846f]
Sep 30 20:47:38 owner-laptop kernel: [    0.153908] pci 0000:00:14.2: reg 10 64bit mmio: [0xd0000000-0xd0003fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154213] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd8000000-0xdfffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154219] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154226] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154243] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154261] pci 0000:01:05.0: supports D1 D2
Sep 30 20:47:38 owner-laptop kernel: [    0.154293] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154298] pci 0000:00:01.0: bridge 32bit mmio: [0xd0100000-0xd01fffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154303] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154380] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0200000-0xd020ffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154546] pci 0000:02:06.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154584] pci 0000:02:06.0: supports D1 D2
Sep 30 20:47:38 owner-laptop kernel: [    0.154663] pci 0000:02:07.0: reg 10 io port: [0xa000-0xa0ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154675] pci 0000:02:07.0: reg 14 32bit mmio: [0xd0211000-0xd02110ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154760] pci 0000:02:07.0: supports D1 D2
Sep 30 20:47:38 owner-laptop kernel: [    0.154852] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154859] pci 0000:00:14.4: bridge 32bit mmio: [0xd0200000-0xd02fffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.154909] pci_bus 0000:00: on NUMA node 0
Sep 30 20:47:38 owner-laptop kernel: [    0.154914] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Sep 30 20:47:38 owner-laptop kernel: [    0.155118] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Sep 30 20:47:38 owner-laptop kernel: [    0.155271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Sep 30 20:47:38 owner-laptop kernel: [    0.158643] libata version 3.00 loaded.
Sep 30 20:47:38 owner-laptop kernel: [    0.209935]   alloc irq_desc for 23 on node -1
Sep 30 20:47:38 owner-laptop kernel: [    0.209938]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [    0.209955] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209959] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209962] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209966] pci_bus 0000:01: resource 1 mem: [0xd0100000-0xd01fffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209969] pci_bus 0000:01: resource 2 pref mem [0xd8000000-0xdfffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209972] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209976] pci_bus 0000:02: resource 1 mem: [0xd0200000-0xd02fffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209979] pci_bus 0000:02: resource 2 pref mem [0x1c000000-0x1fffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209982] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209985] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209989] pci_bus 0000:03: resource 0 io:  [0xa400-0xa4ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209992] pci_bus 0000:03: resource 1 io:  [0xa800-0xa8ff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209995] pci_bus 0000:03: resource 2 pref mem [0x1c000000-0x1fffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.209999] pci_bus 0000:03: resource 3 mem: [0x24000000-0x27ffffff]
Sep 30 20:47:38 owner-laptop kernel: [    0.884904] pci 0000:01:05.0: Boot video device
Sep 30 20:47:38 owner-laptop kernel: [    1.169755]   alloc irq_desc for 22 on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.169758]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.169868]   alloc irq_desc for 16 on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.169871]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.169901] pata_acpi 0000:00:14.1: setting latency timer to 64
Sep 30 20:47:38 owner-laptop kernel: [    1.170539]   alloc irq_desc for 19 on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.170542]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [    1.351596] PM: Resume from disk failed.
Sep 30 20:47:38 owner-laptop kernel: [    1.939220] sata_sil 0000:00:12.0: version 2.4
Sep 30 20:47:38 owner-laptop kernel: [    2.293315] sr 1:0:0:0: Attached scsi CD-ROM sr0
Sep 30 20:47:38 owner-laptop kernel: [    2.294191] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 30 20:47:38 owner-laptop kernel: [    2.625925]   alloc irq_desc for 20 on node -1
Sep 30 20:47:38 owner-laptop kernel: [    2.625928]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [   20.369179]   alloc irq_desc for 17 on node -1
Sep 30 20:47:38 owner-laptop kernel: [   20.369182]   alloc kstat_irqs on node -1
Sep 30 20:47:38 owner-laptop kernel: [   20.759058] vga16fb: initializing
Sep 30 20:47:38 owner-laptop kernel: [   21.419801] ath: EEPROM regdomain: 0x64
Sep 30 20:47:38 owner-laptop kernel: [   21.419805] ath: EEPROM indicates we should expect a direct regpair map
Sep 30 20:47:38 owner-laptop kernel: [   21.419811] ath: Country alpha2 being used: 00
Sep 30 20:47:38 owner-laptop kernel: [   21.419814] ath: Regpair used: 0x64
Sep 30 20:47:38 owner-laptop kernel: [   21.434612] phy0: Selected rate control algorithm 'minstrel'
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Sucessfully called chroot.
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Sucessfully dropped privileges.
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Sucessfully limited resources.
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Running.
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Watchdog thread running.
Sep 30 20:47:40 owner-laptop rtkit-daemon[1092]: Canary thread running.
Sep 30 20:47:41 owner-laptop rtkit-daemon[1092]: Supervising 1 threads of 1 processes of 1 users.
Sep 30 20:47:41 owner-laptop rtkit-daemon[1092]: Supervising 2 threads of 1 processes of 1 users.
Sep 30 20:47:41 owner-laptop rtkit-daemon[1092]: Supervising 3 threads of 1 processes of 1 users.
Sep 30 20:47:41 owner-laptop rtkit-daemon[1092]: Supervising 4 threads of 2 processes of 1 users.
Sep 30 20:47:47 owner-laptop kernel: [   30.292149] wlan0: direct probe to AP 68:7f:74:25:31:11 (try 1)
Sep 30 20:47:47 owner-laptop kernel: [   30.292189] wlan0: deauthenticating from 68:7f:74:25:31:11 by local choice (reason=3)
Sep 30 20:47:47 owner-laptop kernel: [   30.292253] wlan0: direct probe to AP 68:7f:74:25:31:11 (try 1)
Sep 30 20:47:47 owner-laptop kernel: [   30.296358] wlan0: direct probe responded
Sep 30 20:47:47 owner-laptop kernel: [   30.296366] wlan0: authenticate with AP 68:7f:74:25:31:11 (try 1)
Sep 30 20:47:47 owner-laptop kernel: [   30.302801] wlan0: authenticated
Sep 30 20:47:47 owner-laptop kernel: [   30.302833] wlan0: associate with AP 68:7f:74:25:31:11 (try 1)
Sep 30 20:47:47 owner-laptop kernel: [   30.305232] wlan0: RX AssocResp from 68:7f:74:25:31:11 (capab=0x411 status=0 aid=1)
Sep 30 20:47:47 owner-laptop kernel: [   30.305238] wlan0: associated
Sep 30 20:47:57 owner-laptop kernel: [   40.520044] wlan0: no IPv6 routers present
```

Beyond that point was a system restart.

Anything above look "interesting"?  I'd really like to get the hardware on this thing running stable.

---

