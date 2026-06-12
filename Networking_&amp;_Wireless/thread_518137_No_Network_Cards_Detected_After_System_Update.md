---
title: "No Network Cards Detected After System Update"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by papyromancer on 2007-08-05
Yesterday I ran system update, and then I rebooted my computer.  Now I can't connect to the internet or any other network.

```
$ sudo ifconfig eth0 up 
``` tells me there is "No such device"

I've included all the diagnostic information that I know how to retrieve.  I don't know how to query apt to find out what updates were performed just before this error occured.

the following is output from 

```
$ ifconfig -a
$ cat /etc/network/interfaces
$ lspci -nn
$ sudo lshw -C network
$ dmesg
```

note that ```
lshw -C network
``` returned nothing

```
$ ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:622950 (608.3 KiB)  TX bytes:622950 (608.3 KiB)


$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82946GZ/PL/GL Memory Controller Hub [8086:2970] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82946GZ/GL Integrated Graphics Controller [8086:2972] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)

$ sudo lshw -C network


$ dmesg

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f6f0000 end: 000000001f7f0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f7f0000 size: 0000000000003000 end: 000000001f7f3000 type: 4
[    0.000000] copy_e820_map() start: 000000001f7f3000 size: 000000000000d000 end: 000000001f800000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7f3000 - 000000001f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f36b0
[    0.000000] Entering add_active_range(0, 0, 129008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   129008
[    0.000000]   HighMem    129008 ->   129008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   129008
[    0.000000] On node 0 totalpages: 129008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x000f7820
[    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f3040
[    0.000000] ACPI: FADT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f30c0
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000020) @ 0x1f7f6d80
[    0.000000] ACPI: MCFG (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f6f40
[    0.000000] ACPI: MADT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f6c80
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20041203) @ 0x1f7f6fc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20041203) @ 0x1f7f7450
[    0.000000] ACPI: DSDT (v001 ACRSYS ACRPRDCT 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:c0800000)
[    0.000000] Detected 3391.736 MHz processor.
[   15.514262] Built 1 zonelists.  Total pages: 128001
[   15.514266] Kernel command line: root=UUID=ef4274a4-84b5-4a84-a4af-f6b1afa73d7b ro quiet splash
[   15.514407] mapped APIC to ffffd000 (fee00000)
[   15.514410] mapped IOAPIC to ffffc000 (fec00000)
[   15.514412] Enabling fast FPU save and restore... done.
[   15.514415] Enabling unmasked SIMD FPU exception support... done.
[   15.514423] Initializing CPU#0
[   15.514483] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   15.515982] Console: colour VGA+ 80x25
[   15.516195] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.516380] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.522875] Memory: 500536k/516032k available (1992k kernel code, 14944k reserved, 900k data, 328k init, 0k highmem)
[   15.522883] virtual kernel memory layout:
[   15.522884]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.522885]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.522886]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   15.522887]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[   15.522888]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   15.522889]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   15.522890]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   15.522893] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.602222] Calibrating delay using timer specific routine.. 6789.03 BogoMIPS (lpj=13578078)
[   15.602260] Security Framework v1.0.0 initialized
[   15.602265] SELinux:  Disabled at boot.
[   15.602280] Mount-cache hash table entries: 512
[   15.602396] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   15.602404] monitor/mwait feature present.
[   15.602406] using mwait in idle threads.
[   15.602411] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.602414] CPU: L2 cache: 2048K
[   15.602416] CPU: Physical Processor ID: 0
[   15.602418] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e59d 00000000 00000001
[   15.602427] Compat vDSO mapped to ffffe000.
[   15.602430] Remapping vsyscall page to ffffe000
[   15.602444] Checking 'hlt' instruction... OK.
[   15.618269] SMP alternatives: switching to UP code
[   15.618549] Early unpacking initramfs... done
[   15.858868] ACPI: Core revision 20060707
[   15.859576] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.866470] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[   15.866490] SMP alternatives: switching to SMP code
[   15.866605] Booting processor 1/1 eip 3000
[   15.877019] Initializing CPU#1
[   15.957143] Calibrating delay using timer specific routine.. 6783.48 BogoMIPS (lpj=13566975)
[   15.957153] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   15.957159] monitor/mwait feature present.
[   15.957165] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.957167] CPU: L2 cache: 2048K
[   15.957170] CPU: Physical Processor ID: 0
[   15.957172] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e59d 00000000 00000001
[   15.957564] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[   15.957602] Total of 2 processors activated (13572.52 BogoMIPS).
[   15.957747] ENABLING IO-APIC IRQs
[   15.957925] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.104704] checking TSC synchronization across 2 CPUs: passed.
[    0.003987] Brought up 2 CPUs
[    0.227648] migration_cost=137
[    0.227909] Booting paravirtualized kernel on bare hardware
[    0.227987] Time: 17:11:07  Date: 07/05/107
[    0.228016] NET: Registered protocol family 16
[    0.228099] EISA bus registered
[    0.228105] ACPI: bus type pci registered
[    0.229335] PCI: PCI BIOS revision 3.00 entry at 0xfa020, last bus=4
[    0.229337] PCI: Using configuration type 1
[    0.229340] Setting up standard PCI resources
[    0.245557] ACPI: Interpreter enabled
[    0.245560] ACPI: Using IOAPIC for interrupt routing
[    0.246172] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.246179] PCI: Probing PCI hardware (bus 00)
[    0.246427] Boot video device is 0000:00:02.0
[    0.246875] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.246880] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.247296] PCI: Transparent bridge - 0000:00:1e.0
[    0.247352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.259476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.259682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.259890] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.260210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.262242] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.262489] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.262733] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.262977] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.263249] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.263496] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.263743] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.263988] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.264299] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.264309] pnp: PnP ACPI init
[    0.265835] pnp: PnP ACPI: found 10 devices
[    0.265840] PnPBIOS: Disabled by ACPI PNP
[    0.265892] PCI: Using ACPI for IRQ routing
[    0.265896] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.285642] NET: Registered protocol family 8
[    0.285645] NET: Registered protocol family 20
[    0.286059] pnp: 00:06: ioport range 0x400-0x4bf could not be reserved
[    0.286368] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.286372] PCI: Bridge: 0000:00:1c.0
[    0.286375]   IO window: b000-bfff
[    0.286380]   MEM window: fde00000-fdefffff
[    0.286384]   PREFETCH window: fdd00000-fddfffff
[    0.286390] PCI: Bridge: 0000:00:1c.1
[    0.286393]   IO window: d000-dfff
[    0.286398]   MEM window: fdc00000-fdcfffff
[    0.286403]   PREFETCH window: fdb00000-fdbfffff
[    0.286408] PCI: Bridge: 0000:00:1c.2
[    0.286412]   IO window: c000-cfff
[    0.286417]   MEM window: fda00000-fdafffff
[    0.286421]   PREFETCH window: fd900000-fd9fffff
[    0.286426] PCI: Bridge: 0000:00:1e.0
[    0.286430]   IO window: e000-efff
[    0.286435]   MEM window: fd700000-fd7fffff
[    0.286439]   PREFETCH window: fd600000-fd6fffff
[    0.286462] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.286469] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.286486] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.286491] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.286508] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.286513] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.286523] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.286549] NET: Registered protocol family 2
[    0.339054] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.339130] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.339196] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.339230] TCP: Hash tables configured (established 16384 bind 8192)
[    0.339233] TCP reno registered
[    0.355085] checking if image is initramfs... it is
[    0.829938] Freeing initrd memory: 6781k freed
[    0.830492] audit: initializing netlink socket (disabled)
[    0.830509] audit(1186333867.508:1): initialized
[    0.830672] VFS: Disk quotas dquot_6.5.1
[    0.830694] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.830743] io scheduler noop registered
[    0.830746] io scheduler anticipatory registered
[    0.830748] io scheduler deadline registered
[    0.830759] io scheduler cfq registered (default)
[    0.830952] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.830993] assign_interrupt_mode Found MSI capability
[    0.830996] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.831030] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.831132] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.831172] assign_interrupt_mode Found MSI capability
[    0.831175] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.831211] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.831307] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.831347] assign_interrupt_mode Found MSI capability
[    0.831349] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.831391] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.831546] isapnp: Scanning for PnP cards...
[    1.182111] isapnp: No Plug & Play device found
[    1.206634] Real Time Clock Driver v1.12ac
[    1.206685] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.207249] mice: PS/2 mouse device common for all mice
[    1.207846] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.207994] input: Macintosh mouse button emulation as /class/input/input0
[    1.208032] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.208036] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.208272] PNP: No PS/2 controller found. Probing ports directly.
[    1.208597] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.208605] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.208710] EISA: Probing bus 0 at eisa.0
[    1.208748] EISA: Detected 0 cards.
[    1.238737] TCP cubic registered
[    1.238746] NET: Registered protocol family 1
[    1.238770] Starting balanced_irq
[    1.238776] Using IPI No-Shortcut mode
[    1.238867] ACPI: (supports S0 S3 S4 S5)
[    1.238913]   Magic number: 3:805:187
[    1.239230] Freeing unused kernel memory: 328k freed
[    1.240224] Time: tsc clocksource has been installed.
[    2.510870] Capability LSM initialized
[    2.539141] ACPI: Fan [FAN] (on)
[    2.542507] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.542553] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.542560] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.543713] ACPI: Thermal Zone [THRM] (63 C)
[    2.543938] ACPI: Thermal Zone [SYST] (55 C)
[    2.944184] usbcore: registered new interface driver usbfs
[    2.944213] usbcore: registered new interface driver hub
[    2.944243] usbcore: registered new device driver usb
[    2.945247] USB Universal Host Controller Interface driver v3.0
[    2.945299] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    2.945313] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    2.945318] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.945430] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.945458] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000fe00
[    2.945575] usb usb1: configuration #1 chosen from 1 choice
[    2.945610] hub 1-0:1.0: USB hub found
[    2.945617] hub 1-0:1.0: 2 ports detected
[    3.047032] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.047047] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.047054] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.047085] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.047118] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000fd00
[    3.047233] usb usb2: configuration #1 chosen from 1 choice
[    3.047269] hub 2-0:1.0: USB hub found
[    3.047277] hub 2-0:1.0: 2 ports detected
[    3.150661] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.150676] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.150681] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.150709] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.150742] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    3.150880] usb usb3: configuration #1 chosen from 1 choice
[    3.150919] hub 3-0:1.0: USB hub found
[    3.150928] hub 3-0:1.0: 2 ports detected
[    3.254345] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.254356] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.254361] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.254389] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.254416] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    3.254541] usb usb4: configuration #1 chosen from 1 choice
[    3.254580] hub 4-0:1.0: USB hub found
[    3.254588] hub 4-0:1.0: 2 ports detected
[    3.286164] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    3.359233] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.359248] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.359253] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.359288] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.359319] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    3.359326] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfdfff000
[    3.363205] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.363294] usb usb5: configuration #1 chosen from 1 choice
[    3.363326] hub 5-0:1.0: USB hub found
[    3.363333] hub 5-0:1.0: 8 ports detected
[    3.365578] SCSI subsystem initialized
[    3.372650] libata version 2.20 loaded.
[    3.468066] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.468073] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.468097] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.468114] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.468167] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fa00 irq 14
[    3.468200] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fa08 irq 15
[    3.468222] scsi0 : ata_piix
[    3.629548] ata1.00: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[    3.629556] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OA70A, max UDMA/133
[    3.629560] ata1.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.637539] ata1.00: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[    3.637545] ata1.00: configured for UDMA/133
[    3.637556] scsi1 : ata_piix
[    3.808669] usb 1-2: device not accepting address 2, error -71
[    3.956642] ata2.01: ATAPI, max UDMA/33
[    4.103840] usb 5-2: new high speed USB device using ehci_hcd and address 2
[    4.120174] ata2.01: configured for UDMA/33
[    4.120286] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    4.122295] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-85JS  F100 PQ: 0 ANSI: 5
[    4.127817] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[    4.127834] sda: Write Protect is off
[    4.127838] sda: Mode Sense: 00 3a 00 00
[    4.127863] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.127932] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[    4.127946] sda: Write Protect is off
[    4.127950] sda: Mode Sense: 00 3a 00 00
[    4.127973] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.127977]  sda: sda1 < sda5 sda6 sda7 >
[    4.160757] sd 0:0:0:0: Attached scsi disk sda
[    4.164616] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.164642] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    4.168139] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    4.168145] Uniform CD-ROM driver Revision: 3.20
[    4.168199] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    4.236171] usb 5-2: configuration #1 chosen from 1 choice
[    4.236393] hub 5-2:1.0: USB hub found
[    4.236441] hub 5-2:1.0: 3 ports detected
[    4.389353] Attempting manual resume
[    4.389357] swsusp: Resume From Partition 8:6
[    4.389358] PM: Checking swsusp image.
[    4.389495] PM: Resume from disk failed.
[    4.415567] kjournald starting.  Commit interval 5 seconds
[    4.415582] EXT3-fs: mounted filesystem with ordered data mode.
[    4.539517] usb 5-2.1: new low speed USB device using ehci_hcd and address 3
[    4.636679] usb 5-2.1: configuration #1 chosen from 1 choice
[    4.835243] usb 5-2.2: new low speed USB device using ehci_hcd and address 4
[    4.931398] usb 5-2.2: configuration #1 chosen from 1 choice
[    5.130834] usb 5-2.3: new full speed USB device using ehci_hcd and address 5
[    5.225873] usb 5-2.3: configuration #1 chosen from 1 choice
[    5.226070] hub 5-2.3:1.0: USB hub found
[    5.226410] hub 5-2.3:1.0: 3 ports detected
[    5.530731] usb 5-2.3.1: new low speed USB device using ehci_hcd and address 6
[    5.635975] usb 5-2.3.1: configuration #1 chosen from 1 choice
[    5.850502] usb 5-2.3.3: new full speed USB device using ehci_hcd and address 7
[    5.949388] usb 5-2.3.3: configuration #1 chosen from 1 choice
[   11.459000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.469055] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.509554] Linux agpgart interface v0.102 (c) Dave Jones
[   11.511449] agpgart: Detected an Intel 946GZ Chipset.
[   11.512086] agpgart: Detected 7676K stolen memory.
[   11.527095] agpgart: AGP aperture is 256M @ 0xd0000000
[   12.023912] input: PC Speaker as /class/input/input1
[   12.150993] iTCO_vendor_support: vendor-support=0
[   12.152567] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   12.153300] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   12.153676] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.169257] intel_rng: FWH not detected
[   12.195277] input: Wacom Graphire4 4x5 as /class/input/input2
[   12.196336] usbcore: registered new interface driver hiddev
[   12.196401] usbcore: registered new interface driver wacom
[   12.196405] drivers/usb/input/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   12.327190] usbcore: registered new interface driver xpad
[   12.327197] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   12.379744] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.379763] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   12.597664] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   17.240032] input: No brand KVM as /class/input/input3
[   17.240103] input: USB HID v1.10 Keyboard [No brand KVM] on usb-0000:00:1d.7-2.1
[   17.244498] input: No brand KVM as /class/input/input4
[   17.244614] input: USB HID v1.10 Mouse [No brand KVM] on usb-0000:00:1d.7-2.1
[   17.345398] input: Primax Electronics Apple Optical USB Mouse as /class/input/input5
[   17.345477] input: USB HID v1.10 Mouse [Primax Electronics Apple Optical USB Mouse] on usb-0000:00:1d.7-2.3.1
[   17.396527] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input6
[   17.396617] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[   17.400700] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input7
[   17.400804] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[   17.400820] usbcore: registered new interface driver usbhid
[   17.400825] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   17.703520] fuse init (API version 7.8)
[   17.737544] lp: driver loaded but no devices found
[   17.761673] Adding 6144820k swap on /dev/disk/by-uuid/f4413df3-22b5-4e35-a9b8-bd08fee08225.  Priority:-1 extents:1 across:6144820k
[   17.857556] EXT3 FS on sda5, internal journal
[   18.029046] kjournald starting.  Commit interval 5 seconds
[   18.029230] EXT3 FS on sda7, internal journal
[   18.029242] EXT3-fs: mounted filesystem with ordered data mode.
[   19.280397] NET: Registered protocol family 17
[   25.276067] Using specific hotkey driver
[   25.360897] ibm_acpi: ec object not found
[   25.386350] input: Power Button (FF) as /class/input/input8
[   25.386382] ACPI: Power Button (FF) [PWRF]
[   25.386431] input: Power Button (CM) as /class/input/input9
[   25.386456] ACPI: Power Button (CM) [PWRB]
[   25.458845] No dock devices found.
[   25.471472] pcc_acpi: loading...
[   30.364405] [drm] Initialized drm 1.1.0 20060810
[   30.367937] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.368031] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   31.435115] ppdev: user-space parallel port driver
[   33.853023] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   33.853028] apm: disabled - APM is not SMP safe.
[   34.417006] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   34.696744] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   34.697036] NFSD: starting 90-second grace period
[   37.507512] NET: Registered protocol family 10
[   37.507669] lo: Disabled Privacy Extensions
[   38.319291] vboxdrv: Trying to deactivate NMI watchdog permanently...
[   38.319298] vboxdrv: Successfully done.
[   39.289931] Bluetooth: Core ver 2.11
[   39.290016] NET: Registered protocol family 31
[   39.290021] Bluetooth: HCI device and connection manager initialized
[   39.290026] Bluetooth: HCI socket layer initialized
[   39.331913] Bluetooth: L2CAP ver 2.8
[   39.331921] Bluetooth: L2CAP socket layer initialized
[   39.466957] Bluetooth: RFCOMM socket layer initialized
[   39.466974] Bluetooth: RFCOMM TTY layer initialized
[   39.466978] Bluetooth: RFCOMM ver 1.8
[  579.055793] usb 5-6: new high speed USB device using ehci_hcd and address 8
[  579.188410] usb 5-6: configuration #1 chosen from 1 choice
[  579.424422] usbcore: registered new interface driver libusual
[  579.742504] Initializing USB Mass Storage driver...
[  579.742640] scsi2 : SCSI emulation for USB Mass Storage devices
[  579.742730] usb-storage: device found at 8
[  579.742735] usbcore: registered new interface driver usb-storage
[  579.742740] usb-storage: waiting for device to settle before scanning
[  579.742749] USB Mass Storage support registered.
[  584.724626] usb-storage: device scan complete
[  584.725886] scsi 2:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.50 PQ: 0 ANSI: 0 CCS
[  584.726480] scsi 2:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.50 PQ: 0 ANSI: 0
[  584.728703] SCSI device sdb: 3932991 512-byte hdwr sectors (2014 MB)
[  584.729326] sdb: Write Protect is off
[  584.729336] sdb: Mode Sense: 45 00 00 08
[  584.729342] sdb: assuming drive cache: write through
[  584.730945] SCSI device sdb: 3932991 512-byte hdwr sectors (2014 MB)
[  584.731567] sdb: Write Protect is off
[  584.731576] sdb: Mode Sense: 45 00 00 08
[  584.731580] sdb: assuming drive cache: write through
[  584.731589]  sdb: sdb1
[  584.732864] sd 2:0:0:0: Attached scsi removable disk sdb
[  584.732950] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  584.739413] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[  584.739489] sr 2:0:0:1: Attached scsi CD-ROM sr1
[  584.739558] sr 2:0:0:1: Attached scsi generic sg3 type 5
[ 1109.638339] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.638355]     Additional sense: Medium not present
[ 1109.638364] end_request: I/O error, dev sr0, sector 0
[ 1109.638376] Buffer I/O error on device sr0, logical block 0
[ 1109.638383] Buffer I/O error on device sr0, logical block 1
[ 1109.638413] Buffer I/O error on device sr0, logical block 2
[ 1109.638418] Buffer I/O error on device sr0, logical block 3
[ 1109.638446] Buffer I/O error on device sr0, logical block 4
[ 1109.638452] Buffer I/O error on device sr0, logical block 5
[ 1109.638479] Buffer I/O error on device sr0, logical block 6
[ 1109.638485] Buffer I/O error on device sr0, logical block 7
[ 1109.640301] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.640309]     Additional sense: Medium not present
[ 1109.640318] end_request: I/O error, dev sr0, sector 0
[ 1109.640325] Buffer I/O error on device sr0, logical block 0
[ 1109.641339] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.641347]     Additional sense: Medium not present
[ 1109.641355] end_request: I/O error, dev sr0, sector 4
[ 1109.641361] Buffer I/O error on device sr0, logical block 1
[ 1109.642634] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.642642]     Additional sense: Medium not present
[ 1109.642651] end_request: I/O error, dev sr0, sector 0
[ 1109.643656] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.643665]     Additional sense: Medium not present
[ 1109.643674] end_request: I/O error, dev sr0, sector 4
[ 1109.644899] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.644906]     Additional sense: Medium not present
[ 1109.644915] end_request: I/O error, dev sr0, sector 0
[ 1109.646179] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.646187]     Additional sense: Medium not present
[ 1109.646197] end_request: I/O error, dev sr0, sector 4
[ 1109.647409] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.647417]     Additional sense: Medium not present
[ 1109.647425] end_request: I/O error, dev sr0, sector 0
[ 1109.648432] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.648439]     Additional sense: Medium not present
[ 1109.648448] end_request: I/O error, dev sr0, sector 4
[ 1109.649675] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.649683]     Additional sense: Medium not present
[ 1109.649692] end_request: I/O error, dev sr0, sector 0
[ 1109.650776] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1109.650784]     Additional sense: Medium not present
[ 1109.650794] end_request: I/O error, dev sr0, sector 4
[ 1185.279898] usb 5-2.2: USB disconnect, address 4
[ 1185.404763] usb 5-2.3: USB disconnect, address 5
[ 1185.404771] usb 5-2.3.1: USB disconnect, address 6
[ 1185.405195] usb 5-2.3.3: USB disconnect, address 7
[ 1218.911556] usb 5-2.2: new low speed USB device using ehci_hcd and address 9
[ 1219.007643] usb 5-2.2: configuration #1 chosen from 1 choice
[ 1219.008049] input: Wacom Graphire4 4x5 as /class/input/input10
[ 1219.206659] usb 5-2.3: new full speed USB device using ehci_hcd and address 10
[ 1219.301602] usb 5-2.3: configuration #1 chosen from 1 choice
[ 1219.301771] hub 5-2.3:1.0: USB hub found
[ 1219.302111] hub 5-2.3:1.0: 3 ports detected
[ 1219.605683] usb 5-2.3.1: new low speed USB device using ehci_hcd and address 11
[ 1219.702894] usb 5-2.3.1: configuration #1 chosen from 1 choice
[ 1219.705440] input: Primax Electronics Apple Optical USB Mouse as /class/input/input11
[ 1219.705652] input: USB HID v1.10 Mouse [Primax Electronics Apple Optical USB Mouse] on usb-0000:00:1d.7-2.3.1
[ 1219.904774] usb 5-2.3.3: new full speed USB device using ehci_hcd and address 12
[ 1220.003332] usb 5-2.3.3: configuration #1 chosen from 1 choice
[ 1220.007138] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input12
[ 1220.007288] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[ 1220.011496] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input13
[ 1220.011628] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[ 1255.604982] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.604993]     Additional sense: Medium not present
[ 1255.605003] end_request: I/O error, dev sr0, sector 0
[ 1255.605007] printk: 8 messages suppressed.
[ 1255.605019] Buffer I/O error on device sr0, logical block 0
[ 1255.605027] Buffer I/O error on device sr0, logical block 1
[ 1255.605056] Buffer I/O error on device sr0, logical block 2
[ 1255.605106] Buffer I/O error on device sr0, logical block 3
[ 1255.605113] Buffer I/O error on device sr0, logical block 4
[ 1255.605119] Buffer I/O error on device sr0, logical block 5
[ 1255.605125] Buffer I/O error on device sr0, logical block 6
[ 1255.605131] Buffer I/O error on device sr0, logical block 7
[ 1255.607133] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.607141]     Additional sense: Medium not present
[ 1255.607150] end_request: I/O error, dev sr0, sector 0
[ 1255.607157] Buffer I/O error on device sr0, logical block 0
[ 1255.608174] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.608182]     Additional sense: Medium not present
[ 1255.608191] end_request: I/O error, dev sr0, sector 4
[ 1255.608198] Buffer I/O error on device sr0, logical block 1
[ 1255.609685] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.609693]     Additional sense: Medium not present
[ 1255.609699] end_request: I/O error, dev sr0, sector 0
[ 1255.610710] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.610718]     Additional sense: Medium not present
[ 1255.610727] end_request: I/O error, dev sr0, sector 4
[ 1255.611978] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.611986]     Additional sense: Medium not present
[ 1255.611995] end_request: I/O error, dev sr0, sector 0
[ 1255.613006] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.613014]     Additional sense: Medium not present
[ 1255.613022] end_request: I/O error, dev sr0, sector 4
[ 1255.614289] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.614298]     Additional sense: Medium not present
[ 1255.614306] end_request: I/O error, dev sr0, sector 0
[ 1255.615325] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.615333]     Additional sense: Medium not present
[ 1255.615376] end_request: I/O error, dev sr0, sector 4
[ 1255.616625] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.616634]     Additional sense: Medium not present
[ 1255.616643] end_request: I/O error, dev sr0, sector 0
[ 1255.617724] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[ 1255.617735]     Additional sense: Medium not present
[ 1255.617741] end_request: I/O error, dev sr0, sector 4

```

---

### Post by chadrlz on 2007-08-05
Something extremely similar happend to me just the other day. I have to think that this must be it. I also ran an update and now I am also without a connection. I checked the router which says its connected. I also checked for the tell tale green light on the NIC which was lit. My other boxes still work however I am now hesitant to run an update. I didnt make a new post because I didnt want to distract from this one. If there is a way undo whatever was in the update lets hear it.

---

### Post by papyromancer on 2007-08-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93906](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93906) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				maybe it relates to this bug???

---

### Post by noob12 on 2007-08-05
Does everything come back if you boot 2.6.20-15 (which you probably still have on your machine)?

---

### Post by papyromancer on 2007-08-05
I made grub go back to 20-15, and the network still doesn't show up...

Is there a modprobe command that would give me information about where the problem might lie?

How do I query apt or dpkg to find out the upgrade history?

I'd rather revert packages one by one than set up the whole system again.

```
$ ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)


$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82946GZ/PL/GL Memory Controller Hub [8086:2970] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82946GZ/GL Integrated Graphics Controller [8086:2972] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)

$ sudo lshw -C network


$ dmesg

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f6f0000 end: 000000001f7f0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f7f0000 size: 0000000000003000 end: 000000001f7f3000 type: 4
[    0.000000] copy_e820_map() start: 000000001f7f3000 size: 000000000000d000 end: 000000001f800000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7f3000 - 000000001f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f36b0
[    0.000000] Entering add_active_range(0, 0, 129008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   129008
[    0.000000]   HighMem    129008 ->   129008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   129008
[    0.000000] On node 0 totalpages: 129008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123937 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 ACRSYS                                ) @ 0x000f7820
[    0.000000] ACPI: RSDT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f3040
[    0.000000] ACPI: FADT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f30c0
[    0.000000] ACPI: SLIC (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000020) @ 0x1f7f6d80
[    0.000000] ACPI: MCFG (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f6f40
[    0.000000] ACPI: MADT (v001 ACRSYS ACRPRDCT 0x42302e31 AWRD 0x00000000) @ 0x1f7f6c80
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20041203) @ 0x1f7f6fc0
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20041203) @ 0x1f7f7450
[    0.000000] ACPI: DSDT (v001 ACRSYS ACRPRDCT 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:6 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:c0800000)
[    0.000000] Detected 3391.817 MHz processor.
[   17.559866] Built 1 zonelists.  Total pages: 128001
[   17.559869] Kernel command line: root=UUID=ef4274a4-84b5-4a84-a4af-f6b1afa73d7b ro quiet splash
[   17.560005] mapped APIC to ffffd000 (fee00000)
[   17.560008] mapped IOAPIC to ffffc000 (fec00000)
[   17.560010] Enabling fast FPU save and restore... done.
[   17.560013] Enabling unmasked SIMD FPU exception support... done.
[   17.560021] Initializing CPU#0
[   17.560083] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   17.561572] Console: colour VGA+ 80x25
[   17.561786] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.561970] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.568549] Memory: 500288k/516032k available (1992k kernel code, 15160k reserved, 893k data, 328k init, 0k highmem)
[   17.568559] virtual kernel memory layout:
[   17.568560]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.568561]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.568562]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   17.568562]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[   17.568563]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.568564]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.568565]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.568568] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.647823] Calibrating delay using timer specific routine.. 6789.02 BogoMIPS (lpj=13578054)
[   17.647860] Security Framework v1.0.0 initialized
[   17.647864] SELinux:  Disabled at boot.
[   17.647879] Mount-cache hash table entries: 512
[   17.647997] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   17.648005] monitor/mwait feature present.
[   17.648006] using mwait in idle threads.
[   17.648013] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   17.648015] CPU: L2 cache: 2048K
[   17.648017] CPU: Physical Processor ID: 0
[   17.648019] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e59d 00000000 00000001
[   17.648028] Compat vDSO mapped to ffffe000.
[   17.648031] Remapping vsyscall page to ffffe000
[   17.648045] Checking 'hlt' instruction... OK.
[   17.663873] SMP alternatives: switching to UP code
[   17.664162] Early unpacking initramfs... done
[   17.912013] ACPI: Core revision 20060707
[   17.912736] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.919533] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[   17.919553] SMP alternatives: switching to SMP code
[   17.919672] Booting processor 1/1 eip 3000
[   17.930081] Initializing CPU#1
[   18.010719] Calibrating delay using timer specific routine.. 6783.50 BogoMIPS (lpj=13567011)
[   18.010728] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e59d 00000000 00000001
[   18.010735] monitor/mwait feature present.
[   18.010741] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.010743] CPU: L2 cache: 2048K
[   18.010746] CPU: Physical Processor ID: 0
[   18.010748] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003180 0000e59d 00000000 00000001
[   18.011163] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 05
[   18.011201] Total of 2 processors activated (13572.53 BogoMIPS).
[   18.011347] ENABLING IO-APIC IRQs
[   18.011525] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.158277] checking TSC synchronization across 2 CPUs: passed.
[    0.003988] Brought up 2 CPUs
[    0.229135] migration_cost=111
[    0.229408] Booting paravirtualized kernel on bare hardware
[    0.229481] Time:  3:27:31  Date: 07/06/107
[    0.229509] NET: Registered protocol family 16
[    0.229595] EISA bus registered
[    0.229601] ACPI: bus type pci registered
[    0.230830] PCI: PCI BIOS revision 3.00 entry at 0xfa020, last bus=4
[    0.230832] PCI: Using configuration type 1
[    0.230833] Setting up standard PCI resources
[    0.247001] ACPI: Interpreter enabled
[    0.247004] ACPI: Using IOAPIC for interrupt routing
[    0.247618] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.247624] PCI: Probing PCI hardware (bus 00)
[    0.247874] Boot video device is 0000:00:02.0
[    0.248321] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.248325] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.248734] PCI: Transparent bridge - 0000:00:1e.0
[    0.248790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.260931] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.261137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.261342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.261663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.263694] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.263944] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.264186] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.264434] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.264676] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.264920] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.265168] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.265413] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.265729] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.265739] pnp: PnP ACPI init
[    0.267297] pnp: PnP ACPI: found 10 devices
[    0.267302] PnPBIOS: Disabled by ACPI PNP
[    0.267348] PCI: Using ACPI for IRQ routing
[    0.267351] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.287219] NET: Registered protocol family 8
[    0.287221] NET: Registered protocol family 20
[    0.287587] pnp: 00:06: ioport range 0x400-0x4bf could not be reserved
[    0.287899] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.287903] PCI: Bridge: 0000:00:1c.0
[    0.287906]   IO window: b000-bfff
[    0.287911]   MEM window: fde00000-fdefffff
[    0.287915]   PREFETCH window: fdd00000-fddfffff
[    0.287919] PCI: Bridge: 0000:00:1c.1
[    0.287922]   IO window: d000-dfff
[    0.287927]   MEM window: fdc00000-fdcfffff
[    0.287931]   PREFETCH window: fdb00000-fdbfffff
[    0.287935] PCI: Bridge: 0000:00:1c.2
[    0.287938]   IO window: c000-cfff
[    0.287943]   MEM window: fda00000-fdafffff
[    0.287946]   PREFETCH window: fd900000-fd9fffff
[    0.287951] PCI: Bridge: 0000:00:1e.0
[    0.287953]   IO window: e000-efff
[    0.287958]   MEM window: fd700000-fd7fffff
[    0.287962]   PREFETCH window: fd600000-fd6fffff
[    0.287984] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.287990] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.288008] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    0.288013] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.288030] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.288035] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.288045] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.288071] NET: Registered protocol family 2
[    0.331058] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.331144] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.331211] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.331245] TCP: Hash tables configured (established 16384 bind 8192)
[    0.331248] TCP reno registered
[    0.347097] checking if image is initramfs... it is
[    0.837205] Freeing initrd memory: 7007k freed
[    0.837788] audit: initializing netlink socket (disabled)
[    0.837806] audit(1186370851.516:1): initialized
[    0.837975] VFS: Disk quotas dquot_6.5.1
[    0.837995] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.838041] io scheduler noop registered
[    0.838044] io scheduler anticipatory registered
[    0.838046] io scheduler deadline registered
[    0.838058] io scheduler cfq registered (default)
[    0.838249] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.838291] assign_interrupt_mode Found MSI capability
[    0.838293] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.838328] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.838427] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.838468] assign_interrupt_mode Found MSI capability
[    0.838470] Allocate Port Service[0000:00:1c.1:pcie00]
[    0.838508] Allocate Port Service[0000:00:1c.1:pcie02]
[    0.838607] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.838647] assign_interrupt_mode Found MSI capability
[    0.838649] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.838682] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.838842] isapnp: Scanning for PnP cards...
[    1.189451] isapnp: No Plug & Play device found
[    1.214142] Real Time Clock Driver v1.12ac
[    1.214199] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.214769] mice: PS/2 mouse device common for all mice
[    1.215386] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.215533] input: Macintosh mouse button emulation as /class/input/input0
[    1.215572] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.215576] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.215819] PNP: No PS/2 controller found. Probing ports directly.
[    1.216031] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.216037] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.216143] EISA: Probing bus 0 at eisa.0
[    1.216173] EISA: Detected 0 cards.
[    1.246241] TCP cubic registered
[    1.246250] NET: Registered protocol family 1
[    1.246271] Starting balanced_irq
[    1.246278] Using IPI No-Shortcut mode
[    1.246350] ACPI: (supports S0 S3 S4 S5)
[    1.246394]   Magic number: 3:702:461
[    1.246697] Freeing unused kernel memory: 328k freed
[    1.248205] Time: tsc clocksource has been installed.
[    2.520624] Capability LSM initialized
[    2.549025] ACPI: Fan [FAN] (on)
[    2.552425] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.552469] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.552476] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.553640] ACPI: Thermal Zone [THRM] (60 C)
[    2.553865] ACPI: Thermal Zone [SYST] (54 C)
[    2.964040] usbcore: registered new interface driver usbfs
[    2.964068] usbcore: registered new interface driver hub
[    2.964099] usbcore: registered new device driver usb
[    2.965176] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    2.965190] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.965195] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.965306] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.965336] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    2.965347] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfdfff000
[    2.969223] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.969324] usb usb1: configuration #1 chosen from 1 choice
[    2.969356] hub 1-0:1.0: USB hub found
[    2.969364] hub 1-0:1.0: 8 ports detected
[    3.045929] USB Universal Host Controller Interface driver v3.0
[    3.089001] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.089016] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.089021] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.089060] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.089090] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000fe00
[    3.089201] usb usb2: configuration #1 chosen from 1 choice
[    3.089232] hub 2-0:1.0: USB hub found
[    3.089239] hub 2-0:1.0: 2 ports detected
[    3.090870] SCSI subsystem initialized
[    3.097464] libata version 2.20 loaded.
[    3.194363] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.194377] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.194383] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.194414] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.194448] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000fd00
[    3.194575] usb usb3: configuration #1 chosen from 1 choice
[    3.194612] hub 3-0:1.0: USB hub found
[    3.194620] hub 3-0:1.0: 2 ports detected
[    3.302036] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.302048] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.302053] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.302080] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.302110] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    3.302232] usb usb4: configuration #1 chosen from 1 choice
[    3.302268] hub 4-0:1.0: USB hub found
[    3.302277] hub 4-0:1.0: 2 ports detected
[    3.321886] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.409736] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    3.409747] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.409752] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.409780] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.409808] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    3.409938] usb usb5: configuration #1 chosen from 1 choice
[    3.409974] hub 5-0:1.0: USB hub found
[    3.409982] hub 5-0:1.0: 2 ports detected
[    3.469932] usb 1-2: configuration #1 chosen from 1 choice
[    3.470001] hub 1-2:1.0: USB hub found
[    3.470098] hub 1-2:1.0: 3 ports detected
[    3.516767] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.516776] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.516815] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.516841] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.516904] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fa00 irq 14
[    3.516938] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fa08 irq 15
[    3.516966] scsi0 : ata_piix
[    3.677264] ata1.00: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[    3.677274] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OA70A, max UDMA/133
[    3.677278] ata1.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.685253] ata1.00: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[    3.685260] ata1.00: configured for UDMA/133
[    3.685272] scsi1 : ata_piix
[    3.900285] usb 1-2.1: new low speed USB device using ehci_hcd and address 3
[    3.997450] usb 1-2.1: configuration #1 chosen from 1 choice
[    4.004341] ata2.01: ATAPI, max UDMA/33
[    4.167860] ata2.01: configured for UDMA/33
[    4.167981] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    4.169996] scsi 1:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-85JS  F100 PQ: 0 ANSI: 5
[    4.180014] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[    4.180101] sda: Write Protect is off
[    4.180105] sda: Mode Sense: 00 3a 00 00
[    4.180129] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.180203] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[    4.180221] sda: Write Protect is off
[    4.180225] sda: Mode Sense: 00 3a 00 00
[    4.180255] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.180260]  sda: sda1 < sda5<6>usb 1-2.2: new low speed USB device using ehci_hcd and address 4
[    4.200271]  sda6 sda7 >
[    4.212629] sd 0:0:0:0: Attached scsi disk sda
[    4.216553] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.216580] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    4.222011] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    4.222018] Uniform CD-ROM driver Revision: 3.20
[    4.222078] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    4.291815] usb 1-2.2: configuration #1 chosen from 1 choice
[    4.361103] Attempting manual resume
[    4.361107] swsusp: Resume From Partition 8:6
[    4.361108] PM: Checking swsusp image.
[    4.361240] PM: Resume from disk failed.
[    4.392688] kjournald starting.  Commit interval 5 seconds
[    4.392699] EXT3-fs: mounted filesystem with ordered data mode.
[    4.491358] usb 1-2.3: new full speed USB device using ehci_hcd and address 5
[    4.586399] usb 1-2.3: configuration #1 chosen from 1 choice
[    4.586588] hub 1-2.3:1.0: USB hub found
[    4.587053] hub 1-2.3:1.0: 3 ports detected
[    4.891126] usb 1-2.3.1: new low speed USB device using ehci_hcd and address 6
[    4.988054] usb 1-2.3.1: configuration #1 chosen from 1 choice
[    5.190585] usb 1-2.3.3: new full speed USB device using ehci_hcd and address 7
[    5.289365] usb 1-2.3.3: configuration #1 chosen from 1 choice
[    5.290167] usbcore: registered new interface driver hiddev
[    5.292770] input: No brand KVM as /class/input/input1
[    5.292798] input: USB HID v1.10 Keyboard [No brand KVM] on usb-0000:00:1d.7-2.1
[    5.300492] input: No brand KVM as /class/input/input2
[    5.300541] input: USB HID v1.10 Mouse [No brand KVM] on usb-0000:00:1d.7-2.1
[    5.302562] input: Primax Electronics Apple Optical USB Mouse as /class/input/input3
[    5.302582] input: USB HID v1.10 Mouse [Primax Electronics Apple Optical USB Mouse] on usb-0000:00:1d.7-2.3.1
[    5.305595] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input4
[    5.305635] input: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[    5.309515] input: Mitsumi Electric Apple Extended USB Keyboard as /class/input/input5
[    5.309569] input: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:1d.7-2.3.3
[    5.309579] usbcore: registered new interface driver usbhid
[    5.309582] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   11.505030] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.516097] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.527139] Linux agpgart interface v0.102 (c) Dave Jones
[   11.529044] agpgart: Detected an Intel 946GZ Chipset.
[   11.529668] agpgart: Unknown page table size, assuming 512KB
[   11.529674] agpgart: Detected 7676K stolen memory.
[   11.544536] agpgart: AGP aperture is 256M @ 0xd0000000
[   11.559601] iTCO_vendor_support: vendor-support=0
[   11.560743] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   11.560849] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[   11.560920] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.568617] intel_rng: FWH not detected
[   11.871451] input: PC Speaker as /class/input/input6
[   12.011082] input: Wacom Graphire4 4x5 as /class/input/input7
[   12.012214] usbcore: registered new interface driver wacom
[   12.012225] drivers/usb/input/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver
[   12.014732] usbcore: registered new interface driver xpad
[   12.014737] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   12.190318] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   12.190340] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   12.397277] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.623164] fuse init (API version 7.8)
[   12.666144] lp: driver loaded but no devices found
[   12.696488] Adding 6144820k swap on /dev/disk/by-uuid/f4413df3-22b5-4e35-a9b8-bd08fee08225.  Priority:-1 extents:1 across:6144820k
[   12.810823] EXT3 FS on sda5, internal journal
[   13.026197] kjournald starting.  Commit interval 5 seconds
[   13.026385] EXT3 FS on sda7, internal journal
[   13.026392] EXT3-fs: mounted filesystem with ordered data mode.
[   14.339316] NET: Registered protocol family 17
[   20.407638] Using specific hotkey driver
[   20.492281] ibm_acpi: ec object not found
[   20.530305] input: Power Button (FF) as /class/input/input8
[   20.530338] ACPI: Power Button (FF) [PWRF]
[   20.530390] input: Power Button (CM) as /class/input/input9
[   20.530415] ACPI: Power Button (CM) [PWRB]
[   20.611925] No dock devices found.
[   20.624511] pcc_acpi: loading...
[   25.521075] [drm] Initialized drm 1.1.0 20060810
[   25.523873] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.523954] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.591369] ppdev: user-space parallel port driver
[   28.825504] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   28.825510] apm: disabled - APM is not SMP safe.
[   29.561860] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   29.716753] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   29.717026] NFSD: starting 90-second grace period
[   32.558007] NET: Registered protocol family 10
[   32.558169] lo: Disabled Privacy Extensions
[   34.175241] Bluetooth: Core ver 2.11
[   34.175361] NET: Registered protocol family 31
[   34.175365] Bluetooth: HCI device and connection manager initialized
[   34.175371] Bluetooth: HCI socket layer initialized
[   34.210660] Bluetooth: L2CAP ver 2.8
[   34.210669] Bluetooth: L2CAP socket layer initialized
[   34.330368] Bluetooth: RFCOMM socket layer initialized
[   34.330388] Bluetooth: RFCOMM TTY layer initialized
[   34.330393] Bluetooth: RFCOMM ver 1.8
[  100.253237] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.253248]     Additional sense: Medium not present
[  100.253258] end_request: I/O error, dev sr0, sector 0
[  100.253263] Buffer I/O error on device sr0, logical block 0
[  100.253299] Buffer I/O error on device sr0, logical block 1
[  100.253307] Buffer I/O error on device sr0, logical block 2
[  100.253312] Buffer I/O error on device sr0, logical block 3
[  100.253318] Buffer I/O error on device sr0, logical block 4
[  100.253324] Buffer I/O error on device sr0, logical block 5
[  100.253330] Buffer I/O error on device sr0, logical block 6
[  100.253336] Buffer I/O error on device sr0, logical block 7
[  100.255260] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.255304]     Additional sense: Medium not present
[  100.255310] end_request: I/O error, dev sr0, sector 0
[  100.255315] Buffer I/O error on device sr0, logical block 0
[  100.256313] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.256321]     Additional sense: Medium not present
[  100.256329] end_request: I/O error, dev sr0, sector 4
[  100.256336] Buffer I/O error on device sr0, logical block 1
[  100.257771] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.257779]     Additional sense: Medium not present
[  100.257788] end_request: I/O error, dev sr0, sector 0
[  100.258809] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.258817]     Additional sense: Medium not present
[  100.258825] end_request: I/O error, dev sr0, sector 4
[  100.260094] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.260102]     Additional sense: Medium not present
[  100.260110] end_request: I/O error, dev sr0, sector 0
[  100.261130] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.261138]     Additional sense: Medium not present
[  100.261181] end_request: I/O error, dev sr0, sector 4
[  100.262207] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.262216]     Additional sense: Medium not present
[  100.262225] end_request: I/O error, dev sr0, sector 0
[  100.263246] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.263255]     Additional sense: Medium not present
[  100.263265] end_request: I/O error, dev sr0, sector 4
[  100.264302] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.264314]     Additional sense: Medium not present
[  100.264320] end_request: I/O error, dev sr0, sector 0
[  100.265333] sr 1:0:1:0: Device not ready: <6>: Current: sense key: Not Ready
[  100.265342]     Additional sense: Medium not present
[  100.265351] end_request: I/O error, dev sr0, sector 4

```

---

### Post by noob12 on 2007-08-06
Is this a desktop or laptop?  Is it a wired card or wireless?  Can you check BIOS settings to make sure the devices are enabled.  If it is the wireless can you make sure the switch is on?

If it isn't one of those things, can you try booting with either **acpi=off** or **pci=routeirq** set in your boot flags?

---

### Post by papyromancer on 2007-08-06
I foung the dpkg log :)

Here's everything from Aug 4th

```
2007-08-04 14:04:37 upgrade tzdata 2007e-0ubuntu0.7.04 2007f-0ubuntu0.7.4
2007-08-04 14:04:37 status half-configured tzdata 2007e-0ubuntu0.7.04
2007-08-04 14:04:37 status unpacked tzdata 2007e-0ubuntu0.7.04
2007-08-04 14:04:37 status half-installed tzdata 2007e-0ubuntu0.7.04
2007-08-04 14:04:39 status half-installed tzdata 2007e-0ubuntu0.7.04
2007-08-04 14:04:39 status unpacked tzdata 2007f-0ubuntu0.7.4
2007-08-04 14:04:39 status unpacked tzdata 2007f-0ubuntu0.7.4
2007-08-04 14:04:40 status unpacked tzdata 2007f-0ubuntu0.7.4
2007-08-04 14:04:40 status half-configured tzdata 2007f-0ubuntu0.7.4
2007-08-04 14:04:40 status installed tzdata 2007f-0ubuntu0.7.4
2007-08-04 14:04:48 upgrade libdbus-1-3 1.0.2-1ubuntu3 1.0.2-1ubuntu4
2007-08-04 14:04:48 status half-configured libdbus-1-3 1.0.2-1ubuntu3
2007-08-04 14:04:48 status unpacked libdbus-1-3 1.0.2-1ubuntu3
2007-08-04 14:04:48 status half-installed libdbus-1-3 1.0.2-1ubuntu3
2007-08-04 14:04:48 status half-installed libdbus-1-3 1.0.2-1ubuntu3
2007-08-04 14:04:48 status unpacked libdbus-1-3 1.0.2-1ubuntu4
2007-08-04 14:04:48 status unpacked libdbus-1-3 1.0.2-1ubuntu4
2007-08-04 14:04:48 upgrade dbus 1.0.2-1ubuntu3 1.0.2-1ubuntu4
2007-08-04 14:04:48 status half-configured dbus 1.0.2-1ubuntu3
2007-08-04 14:04:49 status unpacked dbus 1.0.2-1ubuntu3
2007-08-04 14:04:49 status half-installed dbus 1.0.2-1ubuntu3
2007-08-04 14:04:49 status half-installed dbus 1.0.2-1ubuntu3
2007-08-04 14:04:49 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:04:49 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:04:49 upgrade dbus-1-utils 1.0.2-1ubuntu3 1.0.2-1ubuntu4
2007-08-04 14:04:49 status half-configured dbus-1-utils 1.0.2-1ubuntu3
2007-08-04 14:04:49 status unpacked dbus-1-utils 1.0.2-1ubuntu3
2007-08-04 14:04:49 status half-installed dbus-1-utils 1.0.2-1ubuntu3
2007-08-04 14:04:49 status half-installed dbus-1-utils 1.0.2-1ubuntu3
2007-08-04 14:04:49 status unpacked dbus-1-utils 1.0.2-1ubuntu4
2007-08-04 14:04:49 status unpacked dbus-1-utils 1.0.2-1ubuntu4
2007-08-04 14:04:49 upgrade python-launchpad-bugs 0.1.13 0.1.13.2
2007-08-04 14:04:49 status half-configured python-launchpad-bugs 0.1.13
2007-08-04 14:04:50 status unpacked python-launchpad-bugs 0.1.13
2007-08-04 14:04:50 status half-installed python-launchpad-bugs 0.1.13
2007-08-04 14:04:50 status half-installed python-launchpad-bugs 0.1.13
2007-08-04 14:04:50 status unpacked python-launchpad-bugs 0.1.13.2
2007-08-04 14:04:50 status unpacked python-launchpad-bugs 0.1.13.2
2007-08-04 14:04:50 status unpacked libdbus-1-3 1.0.2-1ubuntu4
2007-08-04 14:04:50 status half-configured libdbus-1-3 1.0.2-1ubuntu4
2007-08-04 14:05:01 status installed libdbus-1-3 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status half-configured dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status installed dbus 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked dbus-1-utils 1.0.2-1ubuntu4
2007-08-04 14:05:01 status half-configured dbus-1-utils 1.0.2-1ubuntu4
2007-08-04 14:05:01 status installed dbus-1-utils 1.0.2-1ubuntu4
2007-08-04 14:05:01 status unpacked python-launchpad-bugs 0.1.13.2
2007-08-04 14:05:01 status half-configured python-launchpad-bugs 0.1.13.2
2007-08-04 14:05:02 status installed python-launchpad-bugs 0.1.13.2

```

---

### Post by noob12 on 2007-08-06
I don't see anything there that would cause us to stop seeing the device even show up in lspci.  This is all user-space stuff.  This seems to be some issue during PCI setup.  

I'll reiterate my previous suggestions.

---

### Post by papyromancer on 2007-08-06
You fixed it :)

setting "acpi=off" in grub worked...

Why ? ;)

Thanks for your help :)

---

### Post by noob12 on 2007-08-06
OK, you've established that acpi=off works.  

Before you settle for that, I would see if partial disablng works for you.  I think the
right order to try these is:  pci=routeirq  first, then pci=noacpi and if they still don't work go to acpi=off, but this loses all ACPI functionality.

Once you have settled on the right setting edit your /boot/grub/menu.lst and set the option for normal boots.

I think you can go back to 2.6.20-16 now too.

---

### Post by noob12 on 2007-08-06
The real mystery to me is why things were working and suddenly stopped working with acpi enabled.  I'm assuming you did not do anything like flash the BIOS, or boot another OS in between?

Once you're working comfortably with the boot flag settings, you might consider filing a bug on launchpad or directly with the ACPI folks, but you'll need to be prepared to supply all the details. If you do this, first search to see if one is already filed for your type of computer if it is an off-the-shelf or motherboard if you built your own.  The ACPI bug system is at [http://bugzilla.kernel.org](http://bugzilla.kernel.org), under the ACPI product.  Your bug would probably be in category Config - Interrupts or Config - Other under that.  Recognize that Ubuntu Feisty is based on 2.6.20, but the 2.6.22.1 is the latest stable release.

---

### Post by chadrlz on 2007-08-06
I am a total noob to linux. I have only been using it a little while. A lot of what was said is above my head. Like boot flags? Or acpi=disabled. How do I do these things. Step by step would be good. Im lost but hopefully someone will help me out. 

Cuda

---

### Post by noob12 on 2007-08-06
Cuda, unless you know you have the exact same issue, you should probably start a new thread.  We'll help diagnose your issue.  Your issue (and its solution) may not be the same.  Lacking any diagnosis, I would suggest that you do not just go disable acpi.  If it comes to that I or others can give you step by step instructions.

---

### Post by chadrlz on 2007-08-06
I don't know what else it could be. Like I said everything worked fine before the update and after the only thing that didnt work was the NIC. I was able to go online with a live cd. If there is information that you need to have tell me how to get it from using Live CD and I will get it out to you. Like I said I am a noob so. I am a techie but its like starting all over with training wheels. I wish I had studied linux since I was 12 instead of winblows. I have 4 other comps that are waiting on updates and they have been put on hold in light of this new problem. I appreciate all the advice I am getting.

Cuda

---

### Post by noob12 on 2007-08-06
It can be about a jillion other things.

Here is how to set boot flags.

Boot from the hard drive rather than your LiveCd.  You'll see a message like 'Grub loading', hit ESC to get the boot menu.  The top line is generally your default boot setup and will be selected.  

Hit the **e** key to edit commands.  A list of the commands is shown.

Use the down arrow key to go down to the line that starts with **kernel**.  Hit **e** again.  This puts you in a mode where you are editing this line.  Your cursor will be typically be after the word splash.  Enter a space and **acpi=off** and Enter.  This puts you back in the menu.  Then press **b** to boot.

After you boot you can use the command **dmesg | grep 'Kernel command'** to check whether you added the flag properly or not.  If you did, it will be shown there.

This will only last for that one boot.  If it works I can give you step by step instructions on how to make it permanent.  If it doesn't work, please start a new thread to diagnose your problem.

---

### Post by chadrlz on 2007-08-06
Hey Noob first off your the man. Second off you were right. And third off if I was the noob you are (noob12 lol) I wouldnt be asking how to make this permanent. Alright dude just wanted to say thanks again for all the advice so far as it has helped a lot. 


Cuda

---

### Post by noob12 on 2007-08-06
Being the noob that I am, I'm not sure I understood that.  Did it work for you?  Do you need instructions for setting it up permanently or will you be starting a new thread?  (I checked just now and didn't see one from you).

---

### Post by chadrlz on 2007-08-07
I need to know how to make this permanent so that all will be well.

---

### Post by noob12 on 2007-08-07
OK.  To make this permanent do the following
```

xhost +
sudo gedit /boot/grub/menu.lst

```

This will open up an editor on the file /boot/grub/menu.lst

Now find the **first** line that begins with **kernel** (and does not have a # sign in front of it); it should look something like this, but
your version may be different and the UUID will definitely be different in yours.  [B][COLOR="Red"]Don't try to
copy this one, just edit yours.[/COLOR][/B]
```

kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6124792a-a0a0-435a-b68a-28f70317c22e ro quiet splash

```

You'll recognize this as the same line you edited while booting.  Indeed this is the source of that.
Navigate to the end of that line.  Add a space and the **acpi=off** option.  Save the file, and exit the editor.

That will apply to subsequent boots for the default option.

---

### Post by chadrlz on 2007-08-07
Hey dude. My code looks like this.

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 "The code that was here has been removed only for this post, the actual code hasnt been modified yet."/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro <--------------------------------- THIS IS THE FIRST LINE OF CODE THAT STARTS WITH KERNEL.


There is another one that begins after "END OF DEFAULT OPTIONS"
I am wondering if this one is the one I am supposed to edit. As you mentioned it does have a UUID and it is different than yours.


Thanks again
Cuda

---

### Post by harrychitt on 2007-08-07
I'm having the same problem. How do I reset the boot flags?
Thanks,
Harry

---

### Post by harrychitt on 2007-08-07
Sorry about the last question. I did not see the second page of postings where the instructions where located.

---

### Post by papyromancer on 2007-08-10
> **noob12 said:**
> OK, you've established that acpi=off works.  

Before you settle for that, I would see if partial disablng works for you.  I think the
right order to try these is:  pci=routeirq  first, then pci=noacpi and if they still don't work go to acpi=off, but this loses all ACPI functionality.

Once you have settled on the right setting edit your /boot/grub/menu.lst and set the option for normal boots.

I think you can go back to 2.6.20-16 now too.

Neither of those worked, and I'm completely baffled about why this became a problem.  

> The real mystery to me is why things were working and suddenly stopped working with acpi enabled. I'm assuming you did not do anything like flash the BIOS, or boot another OS in between?

Once you're working comfortably with the boot flag settings, you might consider filing a bug on launchpad or directly with the ACPI folks, but you'll need to be prepared to supply all the details. If you do this, first search to see if one is already filed for your type of computer if it is an off-the-shelf or motherboard if you built your own. The ACPI bug system is at [http://bugzilla.kernel.org](http://bugzilla.kernel.org), under the ACPI product. Your bug would probably be in category Config - Interrupts or Config - Other under that. Recognize that Ubuntu Feisty is based on 2.6.20, but the 2.6.22.1 is the latest stable release.

I'll probably just wait till aroud for the update to trickle down if other people are having a similar problem, although I haven't been able to find this bug anywhere in launchpad...maybe I should write out a bug report...  Should I include all the diagnostic information the Kernel Team asks for both a bootup without working networking and a bootup with "acpi=off' boot flags?

--papy

---

