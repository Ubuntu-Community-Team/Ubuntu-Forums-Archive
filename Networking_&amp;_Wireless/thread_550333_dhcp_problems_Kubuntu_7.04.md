---
title: "dhcp problems Kubuntu 7.04"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Whitewater155 on 2007-09-13
Hey evryone,

I've already read all the posts on dhcp problems, tried many things, and nothing is working. I've also typed in commands and have output ready. Tell me what I need to post.

I'm having this problem with Ubuntu/Kubuntu, Fedora 7, and Suse 10.2. dhcp works fine under Windows XP.

I'm getting the following IP address, but it's not coming from DHCP: 169.254.9.190. I've run ifdown/ifup and /etc/init.d/networking restart.  It's sending the dhcp request but is not receiving a dhcp offer.

Hardware: 
ethernet: Reatek RTL8139/810X onboard an ASUS Goldfish 2 motherboard. (compaq presario sr1350nx) connected with wire to Linksys WRT54G Wireless-G Broadband Router. 

I was running Ubuntu on another pc with a d-link card and it worked perfectly.

output of lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev 10)
02:05.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)


sudo lshw -C network produced and error...missing parameters

output of ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:D8:19:F6:C5  
          inet6 addr: fe80::211:d8ff:fe19:f6c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x8400 

eth0:avah Link encap:Ethernet  HWaddr 00:11:D8:19:F6:C5  
          inet addr:169.254.9.190  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5568 (5.4 KiB)  TX bytes:5568 (5.4 KiB)


output of sudo ethtool eth0

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

here's the big one
output of dmesg

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f6c0000 end: 000000001f7c0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f7c0000 size: 000000000000e000 end: 000000001f7ce000 type: 3
[    0.000000] copy_e820_map() start: 000000001f7ce000 size: 0000000000022000 end: 000000001f7f0000 type: 4
[    0.000000] copy_e820_map() start: 000000001f7f0000 size: 0000000000010000 end: 000000001f800000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7c0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7c0000 - 000000001f7ce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f7ce000 - 000000001f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 128960) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128960
[    0.000000]   HighMem    128960 ->   128960
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128960
[    0.000000] On node 0 totalpages: 128960
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 975 pages used for memmap
[    0.000000]   Normal zone: 123889 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fb560
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000506 MSFT 0x00000097) @ 0x1f7c0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x09000506 MSFT 0x00000097) @ 0x1f7c0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000506 MSFT 0x00000097) @ 0x1f7c0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x09000506 MSFT 0x00000097) @ 0x1f7ce040
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x09000506 MSFT 0x00000097) @ 0x1f7c4bd0
[    0.000000] ACPI: DSDT (v001  A0005 A0005095 0x00000095 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:e0380000)
[    0.000000] Detected 3065.747 MHz processor.
[   54.244763] Built 1 zonelists.  Total pages: 127953
[   54.244767] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[   54.244954] mapped APIC to ffffd000 (fee00000)
[   54.244957] mapped IOAPIC to ffffc000 (fec00000)
[   54.244959] Enabling fast FPU save and restore... done.
[   54.244962] Enabling unmasked SIMD FPU exception support... done.
[   54.244973] Initializing CPU#0
[   54.245036] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   54.247125] Console: colour VGA+ 80x25
[   54.247316] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   54.247504] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   54.255015] Memory: 500160k/515840k available (1992k kernel code, 15096k reserved, 893k data, 328k init, 0k highmem)
[   54.255025] virtual kernel memory layout:
[   54.255026]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   54.255028]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   54.255029]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   54.255030]     lowmem  : 0xc0000000 - 0xdf7c0000   ( 503 MB)
[   54.255031]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   54.255032]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   54.255033]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   54.255036] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   54.333038] Calibrating delay using timer specific routine.. 6136.93 BogoMIPS (lpj=12273871)
[   54.333078] Security Framework v1.0.0 initialized
[   54.333083] SELinux:  Disabled at boot.
[   54.333098] Mount-cache hash table entries: 512
[   54.333227] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000451d 00000000 00000000
[   54.333236] monitor/mwait feature present.
[   54.333238] using mwait in idle threads.
[   54.333245] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   54.333248] CPU: L2 cache: 1024K
[   54.333251] CPU: Hyper-Threading is disabled
[   54.333253] CPU: After all inits, caps: bfebfbff 00100000 00000000 00003180 0000451d 00000000 00000000
[   54.333262] Compat vDSO mapped to ffffe000.
[   54.333265] Remapping vsyscall page to ffffe000
[   54.333280] Checking 'hlt' instruction... OK.
[   54.349122] SMP alternatives: switching to UP code
[   54.349272] Freeing SMP alternatives: 11k freed
[   54.349456] Early unpacking initramfs... done
[   54.622835] ACPI: Core revision 20060707
[   54.622995] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   54.636575] CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 01
[   54.636616] Total of 1 processors activated (6136.93 BogoMIPS).
[   54.636767] ENABLING IO-APIC IRQs
[   54.636948] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   54.781055] Brought up 1 CPUs
[   54.781291] Booting paravirtualized kernel on bare hardware
[   54.781359] Time: 17:48:07  Date: 08/13/107
[   54.781385] NET: Registered protocol family 16
[   54.781469] EISA bus registered
[   54.781474] ACPI: bus type pci registered
[   54.781740] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   54.781743] PCI: Using configuration type 1
[   54.781744] Setting up standard PCI resources
[   54.794856] ACPI: Interpreter enabled
[   54.794859] ACPI: Using IOAPIC for interrupt routing
[   54.795941] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   54.795949] PCI: Probing PCI hardware (bus 00)
[   54.796265] Boot video device is 0000:00:02.0
[   54.796706] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   54.796710] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   54.797282] PCI: Transparent bridge - 0000:00:1e.0
[   54.797321] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   54.799853] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   54.806074] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   54.806343] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   54.806606] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   54.806871] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   54.807134] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[   54.807398] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   54.807660] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   54.807930] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   54.808075] Linux Plug and Play Support v0.97 (c) Adam Belay
[   54.808085] pnp: PnP ACPI init
[   54.812386] pnp: PnP ACPI: found 17 devices
[   54.812391] PnPBIOS: Disabled by ACPI PNP
[   54.812438] PCI: Using ACPI for IRQ routing
[   54.812441] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   54.825091] NET: Registered protocol family 8
[   54.825093] NET: Registered protocol family 20
[   54.826079] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[   54.826383] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   54.826388] PCI: Bridge: 0000:00:1c.0
[   54.826391]   IO window: c000-cfff
[   54.826396]   MEM window: disabled.
[   54.826400]   PREFETCH window: disabled.
[   54.826405] PCI: Bridge: 0000:00:1e.0
[   54.826408]   IO window: d000-efff
[   54.826413]   MEM window: cff00000-cfffffff
[   54.826417]   PREFETCH window: disabled.
[   54.826445] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.826452] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   54.826464] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   54.826489] NET: Registered protocol family 2
[   54.865083] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   54.865155] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   54.865231] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   54.865264] TCP: Hash tables configured (established 16384 bind 8192)
[   54.865267] TCP reno registered
[   54.877136] checking if image is initramfs... it is
[   55.409089] Freeing initrd memory: 6965k freed
[   55.409546] audit: initializing netlink socket (disabled)
[   55.409559] audit(1189705687.240:1): initialized
[   55.409672] VFS: Disk quotas dquot_6.5.1
[   55.409691] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   55.409734] io scheduler noop registered
[   55.409737] io scheduler anticipatory registered
[   55.409739] io scheduler deadline registered
[   55.409748] io scheduler cfq registered (default)
[   55.409961] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   55.410006] assign_interrupt_mode Found MSI capability
[   55.410011] Allocate Port Service[0000:00:1c.0:pcie00]
[   55.410046] Allocate Port Service[0000:00:1c.0:pcie02]
[   55.410209] isapnp: Scanning for PnP cards...
[   55.762157] isapnp: No Plug & Play device found
[   55.786326] Real Time Clock Driver v1.12ac
[   55.786379] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   55.787024] mice: PS/2 mouse device common for all mice
[   55.787577] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   55.787804] input: Macintosh mouse button emulation as /class/input/input0
[   55.787838] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   55.787842] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   55.788041] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   55.790964] serio: i8042 KBD port at 0x60,0x64 irq 1
[   55.790970] serio: i8042 AUX port at 0x60,0x64 irq 12
[   55.791111] EISA: Probing bus 0 at eisa.0
[   55.791140] Cannot allocate resource for EISA slot 8
[   55.791142] EISA: Detected 0 cards.
[   55.821221] TCP cubic registered
[   55.821230] NET: Registered protocol family 1
[   55.821251] Using IPI No-Shortcut mode
[   55.821311] ACPI: (supports S0 S1 S3 S4 S5)
[   55.821355]   Magic number: 7:585:845
[   55.821464]   hash matches device ptyre
[   55.821690] Freeing unused kernel memory: 328k freed
[   55.824958] Time: tsc clocksource has been installed.
[   55.838969] input: AT Translated Set 2 keyboard as /class/input/input1
[   57.023386] Capability LSM initialized
[   57.058096] ACPI: Processor [CPU1] (supports 8 throttling states)
[   57.058106] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   57.437892] usbcore: registered new interface driver usbfs
[   57.437914] usbcore: registered new interface driver hub
[   57.437935] usbcore: registered new device driver usb
[   57.438750] USB Universal Host Controller Interface driver v3.0
[   57.438795] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   57.438805] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   57.438809] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   57.438944] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   57.438972] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000a400
[   57.439069] usb usb1: configuration #1 chosen from 1 choice
[   57.439097] hub 1-0:1.0: USB hub found
[   57.439104] hub 1-0:1.0: 2 ports detected
[   57.507927] ieee1394: Initialized config rom entry `ip1394'
[   57.517359] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   57.541124] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   57.541136] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   57.541140] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   57.541163] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   57.541192] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000a800
[   57.541283] usb usb2: configuration #1 chosen from 1 choice
[   57.541312] hub 2-0:1.0: USB hub found
[   57.541319] hub 2-0:1.0: 2 ports detected
[   57.645876] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   57.645888] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   57.645892] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   57.645917] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   57.645946] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000b000
[   57.646035] usb usb3: configuration #1 chosen from 1 choice
[   57.646064] hub 3-0:1.0: USB hub found
[   57.646070] hub 3-0:1.0: 2 ports detected
[   57.749078] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   57.749091] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   57.749095] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   57.749120] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   57.749150] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b400
[   57.749243] usb usb4: configuration #1 chosen from 1 choice
[   57.749269] hub 4-0:1.0: USB hub found
[   57.749275] hub 4-0:1.0: 2 ports detected
[   57.780971] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   57.853835] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[   57.853852] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   57.853856] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   57.853887] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   57.853920] ehci_hcd 0000:00:1d.7: debug port 1
[   57.853926] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   57.853933] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xcfe37c00
[   57.857821] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   57.857896] usb usb5: configuration #1 chosen from 1 choice
[   57.857922] hub 5-0:1.0: USB hub found
[   57.857929] hub 5-0:1.0: 8 ports detected
[   57.967679] SCSI subsystem initialized
[   57.973069] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 20 (level, low) -> IRQ 20
[   58.026636] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[cffff800-cfffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   58.032639] libata version 2.20 loaded.
[   58.033912] 8139cp 0000:02:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   58.033915] 8139cp 0000:02:02.0: Try the "8139too" driver instead.
[   58.038782] 8139too Fast Ethernet driver 0.9.28
[   58.038831] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 21 (level, low) -> IRQ 21
[   58.039190] eth0: RealTek RTL8139 at 0xe0048400, 00:11:d8:19:f6:c5, IRQ 21
[   58.039193] eth0:  Identified 8139 chip type 'RTL-8101'
[   58.040912] ata_piix 0000:00:1f.1: version 2.10ac1
[   58.040926] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   58.040943] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   58.041678] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   58.041709] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   58.041728] scsi0 : ata_piix
[   58.312955] usb 1-1: device not accepting address 2, error -71
[   58.526154] ata1.00: ATAPI, max UDMA/33
[   58.526157] ata1.01: ATAPI, max UDMA/33
[   58.689390] ata1.00: configured for UDMA/33
[   58.853196] ata1.01: configured for UDMA/33
[   58.853208] scsi1 : ata_piix
[   59.019101] ATA: abnormal status 0x7F on port 0x00010177
[   59.023935] scsi 0:0:0:0: CD-ROM            HP       DVD Writer 640b  E223 PQ: 0 ANSI: 5
[   59.024599] scsi 0:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B402 PQ: 0 ANSI: 5
[   59.025953] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   59.025979] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[   59.025995] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   59.026030] ata3: SATA max UDMA/133 cmd 0x0001a000 ctl 0x00019802 bmdma 0x00018800 irq 18
[   59.026055] ata4: SATA max UDMA/133 cmd 0x00019400 ctl 0x00019002 bmdma 0x00018808 irq 18
[   59.026064] scsi2 : ata_piix
[   59.124943] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   59.190367] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   59.190371] ata3.00: ATA-6: WDC WD2000JD-22HBB0, 08.02D08, max UDMA/133
[   59.190374] ata3.00: 390721968 sectors, multi 16: LBA48 
[   59.198356] ata3.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   59.198359] ata3.00: configured for UDMA/133
[   59.198368] scsi3 : ata_piix
[   59.257388] usb 5-1: configuration #1 chosen from 1 choice
[   59.257477] hub 5-1:1.0: USB hub found
[   59.257573] hub 5-1:1.0: 7 ports detected
[   59.305072] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000bed378]
[   59.363081] ATA: abnormal status 0x7F on port 0x00019407
[   59.363972] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JD-22H 08.0 PQ: 0 ANSI: 5
[   59.385752] sr0: scsi3-mmc drive: 24x/40x writer cd/rw xa/form2 cdda tray
[   59.385757] Uniform CD-ROM driver Revision: 3.20
[   59.385890] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   59.390242] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   59.390358] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   59.394450] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   59.394548] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   59.394649] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   59.404905] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   59.405826] sda: Write Protect is off
[   59.405829] sda: Mode Sense: 00 3a 00 00
[   59.405855] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.405907] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   59.405918] sda: Write Protect is off
[   59.405920] sda: Mode Sense: 00 3a 00 00
[   59.405936] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.405939]  sda: sda1 sda2
[   59.422891] sd 2:0:0:0: Attached scsi disk sda
[   59.604940] usb 5-2: new high speed USB device using ehci_hcd and address 3
[   59.756227] usb 5-2: configuration #1 chosen from 1 choice
[   60.521638] ISO 9660 Extensions: Microsoft Joliet Level 3
[   60.544917] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   60.547886] ISO 9660 Extensions: RRIP_1991A
[   60.562664] Registering unionfs 20060916-2203
[   60.562668] unionfs: debugging is not enabled
[   60.575612] loop: loaded (max 8 devices)
[   60.610614] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher
[   60.722946] usb 2-1: configuration #1 chosen from 1 choice
[   60.964916] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   61.153908] usb 2-2: configuration #1 chosen from 1 choice
[   61.396897] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   61.573049] usb 4-1: configuration #1 chosen from 1 choice
[   61.576094] usbcore: registered new interface driver hiddev
[   61.624844] input: HID 3353:3713 as /class/input/input2
[   61.624878] input: USB HID v1.10 Keyboard [HID 3353:3713] on usb-0000:00:1d.1-1
[   61.664805] input: HID 3353:3713 as /class/input/input3
[   61.664814] input: USB HID v1.10 Device [HID 3353:3713] on usb-0000:00:1d.1-1
[   61.664831] usbcore: registered new interface driver usbhid
[   61.664835] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   61.665796] usbcore: registered new interface driver libusual
[   61.669209] Initializing USB Mass Storage driver...
[   61.669275] scsi4 : SCSI emulation for USB Mass Storage devices
[   61.669321] usb-storage: device found at 2
[   61.669323] usb-storage: waiting for device to settle before scanning
[   61.669330] usbcore: registered new interface driver usb-storage
[   61.669333] USB Mass Storage support registered.
[   66.670429] usb-storage: device scan complete
[   66.673417] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   66.676414] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   66.679413] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   66.682411] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   66.727463] sd 4:0:0:0: Attached scsi removable disk sdb
[   66.727512] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   66.772455] sd 4:0:0:1: Attached scsi removable disk sdc
[   66.772506] sd 4:0:0:1: Attached scsi generic sg4 type 0
[   66.816890] sd 4:0:0:2: Attached scsi removable disk sdd
[   66.816941] sd 4:0:0:2: Attached scsi generic sg5 type 0
[   66.860450] sd 4:0:0:3: Attached scsi removable disk sde
[   66.860498] sd 4:0:0:3: Attached scsi generic sg6 type 0
[  101.443592] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  102.683669] Linux agpgart interface v0.102 (c) Dave Jones
[  102.931956] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  102.944718] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  102.974742] agpgart: Detected an Intel 915G Chipset.
[  102.974958] agpgart: Detected 7932K stolen memory.
[  102.992049] agpgart: AGP aperture is 256M @ 0xd0000000
[  103.013492] iTCO_vendor_support: vendor-support=0
[  103.014499] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  103.014591] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[  103.014637] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  103.248669] intel_rng: FWH not detected
[  103.724881] usbcore: registered new interface driver xpad
[  103.724887] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[  103.807507] Linux video capture interface: v2.00
[  104.168345] NET: Registered protocol family 17
[  104.345076] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7504
[  104.345088] usbcore: registered new interface driver usblp
[  104.345093] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  104.489193] input: PC Speaker as /class/input/input4
[  104.577662] parport: PnPBIOS parport detected.
[  104.577719] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  104.631789] saa7130/34: v4l2 driver version 0.2.14 loaded
[  104.631854] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[  104.631863] saa7133[0]: found at 0000:02:04.0, rev: 16, irq: 16, latency: 64, mmio: 0xcfffe800
[  104.631870] saa7133[0]: subsystem: 1043:4843, board: ASUS TV-FM 7133 [card=25,autodetected]
[  104.631878] saa7133[0]: board init: gpio is 0
[  104.799955] saa7133[0]: i2c eeprom 00: 43 10 43 48 ff ff ff ff ff ff ff ff ff ff ff ff
[  104.799966] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.799975] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.799983] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.799991] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.799999] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.800007] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.800016] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  104.888703] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[  104.892042] tuner 0-0043: chip found @ 0x86 (saa7133[0])
[  104.892072] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[  104.908063] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  104.908070] tuner 0-0060: chip found @ 0xc0 (saa7133[0])
[  104.908122] tuner 0-0060: type set to 39 (LG NTSC (newer TAPC series))
[  104.908125] tuner 0-0060: type set to 39 (LG NTSC (newer TAPC series))
[  104.938127] saa7133[0]: registered device video0 [v4l2]
[  104.938163] saa7133[0]: registered device vbi0
[  104.938196] saa7133[0]: registered device radio0
[  104.938769] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[  104.938790] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  104.950988] saa7134 ALSA driver for DMA sound loaded
[  104.951016] saa7133[0]/alsa: saa7133[0] at 0xcfffe800 irq 16 registered as card -2
[  105.530011] fuse init (API version 7.8)
[  112.551034] input: Power Button (FF) as /class/input/input6
[  112.554938] ACPI: Power Button (FF) [PWRF]
[  112.587649] input: Power Button (CM) as /class/input/input7
[  112.591590] ACPI: Power Button (CM) [PWRB]
[  112.626046] No dock devices found.
[  112.644776] Using specific hotkey driver
[  112.694573] ibm_acpi: ec object not found
[  112.827369] pcc_acpi: loading...
[  119.572268] lp0: using parport0 (interrupt-driven).
[  119.612017] ppdev: user-space parallel port driver
[  123.068414] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  123.068421] apm: overridden by ACPI.
[  124.441861] Bluetooth: Core ver 2.11
[  124.441922] NET: Registered protocol family 31
[  124.441924] Bluetooth: HCI device and connection manager initialized
[  124.441927] Bluetooth: HCI socket layer initialized
[  124.645729] Bluetooth: L2CAP ver 2.8
[  124.645733] Bluetooth: L2CAP socket layer initialized
[  124.816184] Bluetooth: RFCOMM socket layer initialized
[  124.816197] Bluetooth: RFCOMM TTY layer initialized
[  124.816199] Bluetooth: RFCOMM ver 1.8
[  126.011023] [drm] Initialized drm 1.1.0 20060810
[  126.026772] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  126.029329] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  137.459399] NETDEV WATCHDOG: eth0: transmit timed out
[  140.459347] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  140.459353] eth0: Tx queue start entry 4  dirty entry 0.
[  140.459356] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  140.459360] eth0:  Tx descriptor 1 is 00082156.
[  140.459363] eth0:  Tx descriptor 2 is 00082156.
[  140.459365] eth0:  Tx descriptor 3 is 00082156.
[  140.459378] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  148.791033] NET: Registered protocol family 10
[  148.791127] lo: Disabled Privacy Extensions
[  152.459102] NETDEV WATCHDOG: eth0: transmit timed out
[  155.459053] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  155.459058] eth0: Tx queue start entry 4  dirty entry 0.
[  155.459062] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  155.459065] eth0:  Tx descriptor 1 is 0008203c.
[  155.459068] eth0:  Tx descriptor 2 is 0008203c.
[  155.459071] eth0:  Tx descriptor 3 is 00082156.
[  155.459084] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  159.690962] eth0: no IPv6 routers present
[  167.458807] NETDEV WATCHDOG: eth0: transmit timed out
[  170.458767] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  170.458772] eth0: Tx queue start entry 4  dirty entry 0.
[  170.458776] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  170.458779] eth0:  Tx descriptor 1 is 0008203c.
[  170.458782] eth0:  Tx descriptor 2 is 0008203c.
[  170.458785] eth0:  Tx descriptor 3 is 00082118.
[  170.458797] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  182.454513] NETDEV WATCHDOG: eth0: transmit timed out
[  185.454462] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  185.454467] eth0: Tx queue start entry 4  dirty entry 0.
[  185.454471] eth0:  Tx descriptor 0 is 0008209b. (queue head)
[  185.454474] eth0:  Tx descriptor 1 is 00082118.
[  185.454477] eth0:  Tx descriptor 2 is 00082118.
[  185.454480] eth0:  Tx descriptor 3 is 00082106.
[  185.454493] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  191.362344] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  191.505569] usb 4-2: not running at top speed; connect to a high speed hub
[  191.533667] usb 4-2: configuration #1 chosen from 1 choice
[  191.536678] scsi5 : SCSI emulation for USB Mass Storage devices
[  191.536836] usb-storage: device found at 3
[  191.536839] usb-storage: waiting for device to settle before scanning
[  196.536042] usb-storage: device scan complete
[  196.539042] scsi 5:0:0:0: Direct-Access     MicroAdv QuickiDrive256M  2.00 PQ: 0 ANSI: 2
[  197.470217] NETDEV WATCHDOG: eth0: transmit timed out
[  197.636903] ready
[  197.639897] SCSI device sdf: 512000 512-byte hdwr sectors (262 MB)
[  197.642895] sdf: Write Protect is off
[  197.642898] sdf: Mode Sense: 03 00 00 00
[  197.642900] sdf: assuming drive cache: write through
[  197.654897] SCSI device sdf: 512000 512-byte hdwr sectors (262 MB)
[  197.657893] sdf: Write Protect is off
[  197.657897] sdf: Mode Sense: 03 00 00 00
[  197.657898] sdf: assuming drive cache: write through
[  197.657901]  sdf: sdf1
[  197.663966] sd 5:0:0:0: Attached scsi removable disk sdf
[  197.664016] sd 5:0:0:0: Attached scsi generic sg7 type 0
[  200.470168] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  200.470173] eth0: Tx queue start entry 4  dirty entry 0.
[  200.470177] eth0:  Tx descriptor 0 is 0008209b. (queue head)
[  200.470180] eth0:  Tx descriptor 1 is 0008203c.
[  200.470183] eth0:  Tx descriptor 2 is 00082106.
[  200.470186] eth0:  Tx descriptor 3 is 000820fa.
[  200.470199] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  212.469924] NETDEV WATCHDOG: eth0: transmit timed out
[  215.469872] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  215.469878] eth0: Tx queue start entry 4  dirty entry 0.
[  215.469881] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  215.469885] eth0:  Tx descriptor 1 is 00082106.
[  215.469887] eth0:  Tx descriptor 2 is 0008205a.
[  215.469890] eth0:  Tx descriptor 3 is 0008204e.
[  215.469903] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  227.469630] NETDEV WATCHDOG: eth0: transmit timed out
[  230.469585] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  230.469590] eth0: Tx queue start entry 4  dirty entry 0.
[  230.469594] eth0:  Tx descriptor 0 is 00082046. (queue head)
[  230.469597] eth0:  Tx descriptor 1 is 0008205a.
[  230.469600] eth0:  Tx descriptor 2 is 000820c0.
[  230.469603] eth0:  Tx descriptor 3 is 00082069.
[  230.469616] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  242.469333] NETDEV WATCHDOG: eth0: transmit timed out
[  245.469282] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  245.469287] eth0: Tx queue start entry 4  dirty entry 0.
[  245.469291] eth0:  Tx descriptor 0 is 000820c0. (queue head)
[  245.469294] eth0:  Tx descriptor 1 is 000820c0.
[  245.469296] eth0:  Tx descriptor 2 is 00082069.
[  245.469299] eth0:  Tx descriptor 3 is 000820b4.
[  245.469312] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  257.469038] NETDEV WATCHDOG: eth0: transmit timed out
[  260.468987] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  260.468992] eth0: Tx queue start entry 4  dirty entry 0.
[  260.468996] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  260.468999] eth0:  Tx descriptor 1 is 000820b4.
[  260.469002] eth0:  Tx descriptor 2 is 00082046.
[  260.469005] eth0:  Tx descriptor 3 is 000820b4.
[  260.469018] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  294.174168] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.174175]     Additional sense: Medium not present
[  294.174181] end_request: I/O error, dev sr0, sector 0
[  294.174184] Buffer I/O error on device sr0, logical block 0
[  294.174189] Buffer I/O error on device sr0, logical block 1
[  294.174192] Buffer I/O error on device sr0, logical block 2
[  294.174195] Buffer I/O error on device sr0, logical block 3
[  294.174197] Buffer I/O error on device sr0, logical block 4
[  294.174200] Buffer I/O error on device sr0, logical block 5
[  294.174203] Buffer I/O error on device sr0, logical block 6
[  294.174205] Buffer I/O error on device sr0, logical block 7
[  294.175314] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.175319]     Additional sense: Medium not present
[  294.175323] end_request: I/O error, dev sr0, sector 0
[  294.175325] Buffer I/O error on device sr0, logical block 0
[  294.176290] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.176294]     Additional sense: Medium not present
[  294.176299] end_request: I/O error, dev sr0, sector 4
[  294.176301] Buffer I/O error on device sr0, logical block 1
[  294.177423] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.177427]     Additional sense: Medium not present
[  294.177432] end_request: I/O error, dev sr0, sector 0
[  294.178364] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.178368]     Additional sense: Medium not present
[  294.178372] end_request: I/O error, dev sr0, sector 4
[  294.179484] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.179488]     Additional sense: Medium not present
[  294.179492] end_request: I/O error, dev sr0, sector 0
[  294.180428] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.180432]     Additional sense: Medium not present
[  294.180436] end_request: I/O error, dev sr0, sector 4
[  294.181576] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.181580]     Additional sense: Medium not present
[  294.181584] end_request: I/O error, dev sr0, sector 0
[  294.182523] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.182527]     Additional sense: Medium not present
[  294.182531] end_request: I/O error, dev sr0, sector 4
[  294.183607] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.183612]     Additional sense: Medium not present
[  294.183616] end_request: I/O error, dev sr0, sector 0
[  294.184547] sr 0:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  294.184551]     Additional sense: Medium not present
[  294.184555] end_request: I/O error, dev sr0, sector 4

output of sudo mii-tool -v

eth0: link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   software reset, autonegotiation enabled
  basic status: link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

output of cat /etc/network/interfaces

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


messages from dhcp when bringing eth0 up

Sep 13 17:56:27 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 13 17:56:27 ubuntu dhclient: 
Sep 13 17:56:27 ubuntu dhclient: Listening on LPF/eth0/00:11:d8:19:f6:c5
Sep 13 17:56:27 ubuntu dhclient: Sending on   LPF/eth0/00:11:d8:19:f6:c5
Sep 13 17:56:27 ubuntu dhclient: Sending on   Socket/fallback
Sep 13 17:56:33 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Sep 13 17:56:33 ubuntu dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 13 17:56:33 ubuntu dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 13 17:56:33 ubuntu dhclient: All rights reserved.
Sep 13 17:56:33 ubuntu dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Sep 13 17:56:33 ubuntu dhclient: 
Sep 13 17:56:34 ubuntu dhclient: Listening on LPF/eth0/00:11:d8:19:f6:c5
Sep 13 17:56:34 ubuntu dhclient: Sending on   LPF/eth0/00:11:d8:19:f6:c5
Sep 13 17:56:34 ubuntu dhclient: Sending on   Socket/fallback
Sep 13 17:56:35 ubuntu dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 13 17:56:37 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Sep 13 17:56:39 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 13 17:56:41 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Sep 13 17:56:46 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Sep 13 17:56:52 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Sep 13 17:56:58 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Sep 13 17:57:02 ubuntu dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep 13 17:57:08 ubuntu dhclient: No DHCPOFFERS received.
Sep 13 17:57:08 ubuntu dhclient: No working leases in persistent database - sleeping.
Sep 13 17:57:10 ubuntu dhclient: No DHCPOFFERS received.

I've run linux on this computer before with no problems. When I ran it before, it was with a different ISP and a wireless router/dsl modem. I can't use the old wireless modem with my current provider.

Let me know if there's any more commands to run and any suggestion/solutions you may have. I will greatly appreciate your responses.

Thanks
Whitewater

---

### Post by Whitewater155 on 2007-09-14
OK.. now I feel totally stupid. Fixed the problem. 

I shut down the computer, removed the power cable from the wall, waited a minute or so, turned the pc on, and now I'm getting the dhcp answer from the router.

what's wierd is that dhcp was working on windows xp with no problem before I unplugged the power from the wall.

Whitewater

---

