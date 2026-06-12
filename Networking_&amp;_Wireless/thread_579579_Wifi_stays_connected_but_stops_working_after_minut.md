---
title: "Wifi stays connected but stops working after minutes or hours"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by martinquested on 2007-10-18
Hello.  I'm using a Compaq Presario V6030US laptop (AMD Turion64 dualcore, NVIDIA GeForce Go 6150, Broadcom mini wifi card) and having followed a million threads and howtos I still have more or less the same problem:

I can get connected to the wifi router, and get full connectivity and relatively fast speeds, but after a few minutes or hours (it varies) it stops working.  The connection stays up, with good or very good signal strength, but all network operations time out.  It is possible for me to ping the router (192.168.1.250) but the response times are very slow (in the 10s to 1000s of milliseconds) with over 20% dropout rate.  It is not possible for me to access the router's configuration page by pointing a browser to the router's URL.

It is sometimes possible for me to reconnect to the router, sometimes not - dhclient reports DHCPDISCOVER and DHCPREQUEST being issued, but often no DHCPOFFER received, or only after a long delay.  Even if I do get reconnected, often there is still virtually no network access possible.  Rebooting often doesn't seem to fix the problem - it's almost as if the thing were overheating, since sometimes it just "goes right" after being allowed to rest for a while (hours or overnight).

I have made a note of the information often requested in such threads, and will post it in a few minutes, after rebooting into Linux and then back into XP, where the wifi is, of course, problem-free.

Thanks in the meantime for any suggestions or ideas...

Martin

---

### Post by martinquested on 2007-10-18
I should just say that even when I describe it as "not working", tiny amounts of data are getting through.  Short content, low-graphics pages can sometimes eventually be loaded, although it takes several reloads and several time-outs first.  And then, very occasionally, a while later, for no good reason, the connection might revert to being wonderful.  So bizarre.

Anyway, here's the info someone else requested regarding another, similar problem:

> If you are already using Feisty, can you post:

Yes, I am using Feisty (forgot to say in the last post)

> - basic info about your wireless network (WAP vs. WEP vs. no encryption; are you broadcasting your ESSID)?

WPA encryption (TKIP-PSK).  Broadcast SSID.  (Remember, it connects to begin with - mostly.)


- the last dozen or so lines of output from 'dmesg'?

here is the entire dmesg...

```


[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Sep 23 19:50:39 UTC 2007 (Ubuntu 2.6.20-16.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d2000 size: 000000000002e000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003de00000 end: 000000003df00000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003df00000 size: 0000000000017000 end: 000000003df17000 type: 3
[    0.000000] copy_e820_map() start: 000000003df17000 size: 0000000000069000 end: 000000003df80000 type: 4
[    0.000000] copy_e820_map() start: 000000003df80000 size: 0000000002080000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003df00000 (usable)
[    0.000000]  BIOS-e820: 000000003df00000 - 000000003df17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003df17000 - 000000003df80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003df80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 95MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f89d0
[    0.000000] Entering add_active_range(0, 0, 253696) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   253696
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   253696
[    0.000000] On node 0 totalpages: 253696
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 190 pages used for memmap
[    0.000000]   HighMem zone: 24130 pages, LIFO batch:3
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x000f89a0
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x3df0fbe7
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x3df16d52
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x3df16dc6
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x3df16f48
[    0.000000] ACPI: MADT (v001 HP     	 APIC   0x06040000  LTP 0x00000000) @ 0x3df16f84
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3df16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   Product ID: C51-MCP51    APIC at: 0xFEE00000
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1607.387 MHz processor.
[   16.439278] Built 1 zonelists.  Total pages: 251714
[   16.439282] Kernel command line: root=UUID=64450cb3-928f-4b64-8f04-dbc3dfc14932 ro quiet splash noapic nolapic noioapic
[   16.439452] mapped APIC to ffffd000 (fee00000)
[   16.439455] mapped IOAPIC to ffffc000 (fec00000)
[   16.439458] Enabling fast FPU save and restore... done.
[   16.439461] Enabling unmasked SIMD FPU exception support... done.
[   16.439469] Initializing CPU#0
[   16.439532] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.443232] Console: colour VGA+ 80x25
[   16.443586] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.444215] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.465084] Memory: 994924k/1014784k available (1993k kernel code, 19212k reserved, 900k data, 328k init, 97280k highmem)
[   16.465095] virtual kernel memory layout:
[   16.465097]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.465098]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.465100]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.465101]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.465103]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   16.465104]       .data : 0xc02f2429 - 0xc03d36d4   ( 900 kB)
[   16.465106]       .text : 0xc0100000 - 0xc02f2429   (1993 kB)
[   16.465109] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.543532] Calibrating delay using timer specific routine.. 3217.77 BogoMIPS (lpj=6435544)
[   16.543575] Security Framework v1.0.0 initialized
[   16.543581] SELinux:  Disabled at boot.
[   16.543598] Mount-cache hash table entries: 512
[   16.543729] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   16.543738] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.543741] CPU: L2 Cache: 256K (64 bytes/line)
[   16.543745] CPU 0(2) -> Core 0
[   16.543747] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   16.543758] Compat vDSO mapped to ffffe000.
[   16.543762] Remapping vsyscall page to ffffe000
[   16.543772] Checking 'hlt' instruction... OK.
[   16.559662] SMP alternatives: switching to UP code
[   16.560021] Early unpacking initramfs... done
[   16.904373] ACPI: Core revision 20060707
[   16.907274] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.909507] ACPI: setting ELCR to 0200 (from 0ca0)
[   16.913383] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[   16.913403] SMP alternatives: switching to SMP code
[   16.913480] Booting processor 1/1 eip 3000
[   16.923795] Initializing CPU#1
[   17.003633] Calibrating delay using timer specific routine.. 3214.87 BogoMIPS (lpj=6429757)
[   17.003640] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[   17.003648] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.003650] CPU: L2 Cache: 256K (64 bytes/line)
[   17.003653] CPU 1(2) -> Core 1
[   17.003655] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[   17.003666] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[   17.003683] Total of 2 processors activated (6432.65 BogoMIPS).
[   17.111499] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -70 usecs TSC skew, fixed it up.
[    0.000004] CPU#1 had 70 usecs TSC skew, fixed it up.
[    0.003996] Brought up 2 CPUs
[    0.004004] spurious 8259A interrupt: IRQ7.
[    0.040837] migration_cost=157
[    0.041103] Booting paravirtualized kernel on bare hardware
[    0.041197] Time: 16:55:43  Date: 09/18/107
[    0.041228] NET: Registered protocol family 16
[    0.041309] EISA bus registered
[    0.041313] ACPI: bus type pci registered
[    0.056819] PCI: BIOS BUG #81[49435000] found
[    0.056864] PCI: Using configuration type 1
[    0.056866] Setting up standard PCI resources
[    0.062397] ACPI: Interpreter enabled
[    0.062401] ACPI: Using PIC for interrupt routing
[    0.063347] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.063352] PCI: Probing PCI hardware (bus 00)
[    0.063533] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.063882] Boot video device is 0000:00:05.0
[    0.064866] PCI: Transparent bridge - 0000:00:10.0
[    0.064897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.100616] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.101912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.102093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.102452] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.102771] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.103087] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.103403] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.103718] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.104053] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.104372] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 *10 11 14 15)
[    0.104689] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.105005] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.105323] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 *11 14 15)
[    0.105637] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[    0.105958] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[    0.106274] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.106591] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.106907] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.107226] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.107544] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.107873] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[    0.108206] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.108340] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.108356] pnp: PnP ACPI init
[    0.110899] pnp: PnP ACPI: found 11 devices
[    0.110903] PnPBIOS: Disabled by ACPI PNP
[    0.110959] PCI: Using ACPI for IRQ routing
[    0.110962] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.111061] NET: Registered protocol family 8
[    0.111064] NET: Registered protocol family 20
[    0.111614] pnp: 00:03: ioport range 0x1000-0x107f could not be reserved
[    0.111617] pnp: 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.111620] pnp: 00:03: ioport range 0x1400-0x147f has been reserved
[    0.111624] pnp: 00:03: ioport range 0x1480-0x14ff could not be reserved
[    0.111627] pnp: 00:03: ioport range 0x1800-0x187f has been reserved
[    0.111630] pnp: 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.111633] pnp: 00:03: ioport range 0x2000-0x203f has been reserved
[    0.111963] PCI: Bridge: 0000:00:02.0
[    0.111981]   IO window: 4000-4fff
[    0.111985]   MEM window: b3000000-b31fffff
[    0.111995]   PREFETCH window: d0000000-d01fffff
[    0.111998] PCI: Bridge: 0000:00:03.0
[    0.112000]   IO window: disabled.
[    0.112003]   MEM window: b3200000-b33fffff
[    0.112006]   PREFETCH window: disabled.
[    0.112009] PCI: Bridge: 0000:00:10.0
[    0.112011]   IO window: disabled.
[    0.112014]   MEM window: b3400000-b34fffff
[    0.112017]   PREFETCH window: disabled.
[    0.112030] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.112038] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.112047] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    0.112080] NET: Registered protocol family 2
[    0.164045] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.164194] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.165080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.165497] TCP: Hash tables configured (established 131072 bind 65536)
[    0.165501] TCP reno registered
[    0.184119] checking if image is initramfs... it is
[    0.866400] Freeing initrd memory: 6747k freed
[    0.866530] Simple Boot Flag at 0x36 set to 0x1
[    1.436000] audit: initializing netlink socket (disabled)
[    1.436000] audit(1192726543.620:1): initialized
[    1.436000] highmem bounce pool size: 64 pages
[    1.436000] VFS: Disk quotas dquot_6.5.1
[    1.436000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.436000] io scheduler noop registered
[    1.436000] io scheduler anticipatory registered
[    1.436000] io scheduler deadline registered
[    1.436000] io scheduler cfq registered (default)
[    1.452000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.452000] assign_interrupt_mode Found MSI capability
[    1.452000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.452000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    1.452000] assign_interrupt_mode Found MSI capability
[    1.452000] Allocate Port Service[0000:00:03.0:pcie00]
[    1.452000] isapnp: Scanning for PnP cards...
[    1.804000] isapnp: No Plug & Play device found
[    1.828000] Real Time Clock Driver v1.12ac
[    1.828000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.828000] mice: PS/2 mouse device common for all mice
[    1.828000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.828000] input: Macintosh mouse button emulation as /class/input/input0
[    1.828000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.828000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.828000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.848000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.848000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.848000] EISA: Probing bus 0 at eisa.0
[    1.848000] Cannot allocate resource for EISA slot 1
[    1.848000] Cannot allocate resource for EISA slot 2
[    1.848000] Cannot allocate resource for EISA slot 3
[    1.848000] Cannot allocate resource for EISA slot 4
[    1.848000] EISA: Detected 0 cards.
[    1.876000] TCP cubic registered
[    1.876000] NET: Registered protocol family 1
[    1.876000] Starting balanced_irq
[    1.876000] Using IPI No-Shortcut mode
[    1.876000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.876000] ACPI: (supports S0 S3 S4 S5)
[    1.876000]   Magic number: 11:963:944
[    1.876000]   hash matches device ptyyf
[    1.876000]   hash matches device tty1
[    1.876000] Freeing unused kernel memory: 328k freed
[    1.880000] Time: acpi_pm clocksource has been installed.
[    3.148000] Capability LSM initialized
[    3.200000] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.200000] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    3.200000] ACPI: Thermal Zone [THRM] (56 C)
[    3.780000] usbcore: registered new interface driver usbfs
[    3.780000] usbcore: registered new interface driver hub
[    3.780000] usbcore: registered new device driver usb
[    3.784000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.784000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[    3.784000] PCI: setting IRQ 11 as level-triggered
[    3.784000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[    3.784000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    3.784000] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    3.784000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    3.784000] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[    3.816000] ieee1394: Initialized config rom entry `ip1394'
[    3.852000] usb usb1: configuration #1 chosen from 1 choice
[    3.852000] hub 1-0:1.0: USB hub found
[    3.852000] hub 1-0:1.0: 8 ports detected
[    3.872000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[    3.956000] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[    3.956000] NFORCE-MCP51: chipset revision 241
[    3.956000] NFORCE-MCP51: not 100% native mode: will probe irqs later
[    3.956000] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[    3.956000] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[    3.956000]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[    3.956000] Probing IDE interface ide0...
[    4.260000] usb 1-6: new full speed USB device using ohci_hcd and address 2
[    4.476000] usb 1-6: configuration #1 chosen from 1 choice
[    4.476000] hub 1-6:1.0: USB hub found
[    4.480000] hub 1-6:1.0: 4 ports detected
[    4.700000] hda: HL-DT-ST DVDRAM GSA-4084N, ATAPI CD/DVD-ROM drive
[    4.820000] usb 1-6.2: new low speed USB device using ohci_hcd and address 3
[    4.940000] usb 1-6.2: configuration #0 chosen from 1 choice
[    4.940000] usb 1-6.2: config 0 descriptor??
[    4.956000] usbcore: registered new interface driver hiddev
[    4.960000] input: ???????? as /class/input/input2
[    4.960000] input: USB HID v1.10 Mouse [????????] on usb-0000:00:0b.0-6.2
[    4.960000] usbcore: registered new interface driver usbhid
[    4.960000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.036000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.040000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[    5.040000] PCI: setting IRQ 7 as level-triggered
[    5.040000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[    5.040000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[    5.040000] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    5.040000] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    5.040000] ehci_hcd 0000:00:0b.1: debug port 1
[    5.040000] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[    5.040000] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[    5.040000] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.040000] usb 1-6: USB disconnect, address 2
[    5.040000] usb 1-6.2: USB disconnect, address 3
[    5.040000] usb usb2: configuration #1 chosen from 1 choice
[    5.040000] hub 2-0:1.0: USB hub found
[    5.040000] hub 2-0:1.0: 8 ports detected
[    5.148000] SCSI subsystem initialized
[    5.148000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[    5.148000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[    5.148000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[    5.148000] forcedeth: using HIGHDMA
[    5.152000] libata version 2.20 loaded.
[    5.668000] usb 1-6: new full speed USB device using ohci_hcd and address 4
[    5.668000] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[    5.668000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    5.668000] PCI: setting IRQ 10 as level-triggered
[    5.668000] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[    5.716000] sata_nv 0000:00:0e.0: version 3.3
[    5.716000] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[    5.716000] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[    5.716000] PCI: setting IRQ 5 as level-triggered
[    5.716000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[    5.716000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    5.720000] ata1: SATA max UDMA/133 cmd 0x000130b0 ctl 0x000130a6 bmdma 0x00013090 irq 5
[    5.720000] ata2: SATA max UDMA/133 cmd 0x000130a8 ctl 0x000130a2 bmdma 0x00013098 irq 5
[    5.720000] scsi0 : sata_nv
[    5.720000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[b3400000-b34007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.864000] usb 1-6: configuration #1 chosen from 1 choice
[    5.864000] hub 1-6:1.0: USB hub found
[    5.868000] hub 1-6:1.0: 4 ports detected
[    6.196000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.204000] ata1.00: ATA-7: FUJITSU MHV2080BH PL, 892C, max UDMA/100
[    6.204000] ata1.00: 156301488 sectors, multi 16: LBA48 
[    6.204000] usb 1-6.2: new low speed USB device using ohci_hcd and address 5
[    6.216000] ata1.00: configured for UDMA/100
[    6.216000] scsi1 : sata_nv
[    6.324000] usb 1-6.2: configuration #0 chosen from 1 choice
[    6.324000] usb 1-6.2: config 0 descriptor??
[    6.332000] input: ???????? as /class/input/input3
[    6.332000] input: USB HID v1.10 Mouse [????????] on usb-0000:00:0b.0-6.2
[    6.528000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.536000] ATA: abnormal status 0x7F on port 0x000130af
[    6.536000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080B 892C PQ: 0 ANSI: 5
[    6.548000] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[    6.548000] Uniform CD-ROM driver Revision: 3.20
[    6.548000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.548000] sda: Write Protect is off
[    6.548000] sda: Mode Sense: 00 3a 00 00
[    6.548000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.548000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.548000] sda: Write Protect is off
[    6.548000] sda: Mode Sense: 00 3a 00 00
[    6.548000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.548000]  sda: sda1 sda2 sda3 sda4
[    6.656000] sd 0:0:0:0: Attached scsi disk sda
[    6.660000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.004000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc000aeb2a700]
[    7.020000] Attempting manual resume
[    7.020000] swsusp: Resume From Partition 8:2
[    7.020000] PM: Checking swsusp image.
[    7.020000] PM: Resume from disk failed.
[    7.048000] kjournald starting.  Commit interval 5 seconds
[    7.048000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.208000] eth0: no link during initialization.
[   22.488000] NET: Registered protocol family 17
[   22.636000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   22.636000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   22.736000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.740000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.036000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.096000] input: PC Speaker as /class/input/input4
[   23.128000] nvidia: module license 'NVIDIA' taints kernel.
[   23.380000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 10
[   23.380000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 10 (level, low) -> IRQ 10
[   23.380000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   23.380000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
[   23.488000] sdhci: Secure Digital Host Controller Interface driver
[   23.488000] sdhci: Copyright(c) Pierre Ossman
[   23.488000] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   23.488000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[   23.488000] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[   23.488000] mmc0: SDHCI at 0xb3400800 irq 10 DMA
[   23.628000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   23.692000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   23.848000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 9
[   23.848000] PCI: setting IRQ 9 as level-triggered
[   23.848000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 9 (level, low) -> IRQ 9
[   23.848000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   24.316000] lp: driver loaded but no devices found
[   24.428000] fuse init (API version 7.8)
[   24.464000] USB Universal Host Controller Interface driver v3.0
[   24.540000] Adding 1052248k swap on /dev/disk/by-uuid/dfc07643-b785-4f3f-864e-1c3783f771f9.  Priority:-1 extents:1 across:1052248k
[   24.692000] EXT3 FS on sda3, internal journal
[   33.060000] ndiswrapper version 1.48 loaded (smp=yes, preempt=no)
[   33.208000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   33.208000] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 11
[   33.208000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[   33.208000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.212000] ndiswrapper: using IRQ 11
[   33.548000] wlan0: ethernet device 00:14:a5:b8:73:98 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[   33.548000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   33.548000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   33.552000] usbcore: registered new interface driver ndiswrapper
[   35.552000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.196000] Netfilter messages via NETLINK v0.30.
[   36.216000] nf_conntrack version 0.5.0 (7928 buckets, 63424 max)
[   40.960000] ACPI: AC Adapter [ACAD] (on-line)
[   40.996000] ACPI: Battery Slot [BAT0] (battery absent)
[   41.016000] input: Power Button (FF) as /class/input/input6
[   41.016000] ACPI: Power Button (FF) [PWRF]
[   41.016000] input: Power Button (CM) as /class/input/input7
[   41.016000] ACPI: Power Button (CM) [PWRB]
[   41.016000] input: Sleep Button (CM) as /class/input/input8
[   41.016000] ACPI: Sleep Button (CM) [SLPB]
[   41.016000] input: Lid Switch as /class/input/input9
[   41.016000] ACPI: Lid Switch [LID]
[   41.116000] Using specific hotkey driver
[   41.256000] No dock devices found.
[   41.296000] ibm_acpi: ec object not found
[   41.956000] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   41.956000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   42.044000] pcc_acpi: loading...
[   42.052000] wmi_add device=df890400
[   42.052000] calling WQBA
[   45.120000] ppdev: user-space parallel port driver
[   51.096000] hub 2-0:1.0: resuming
[   51.096000] hub 2-0:1.0: PM: resume from 2, parent usb2 still 2
[   51.096000] hub 2-0:1.0: resuming
[  126.828000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=286 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=266 
[  126.864000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=151 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=131 
[  127.084000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=286 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=266 
[  127.340000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=286 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=266 
[  127.540000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=268 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=248 
[  128.040000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=151 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=131 
[  130.204000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=256 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=236 
[  130.884000] IN-world:IN=eth0 OUT= MAC= SRC=169.254.6.132 DST=224.0.0.251 LEN=268 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=248 
[  137.524000] PASS-unknown:IN=eth1 OUT=eth0 SRC=192.168.1.250 DST=192.168.1.51 LEN=576 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
[  140.924000] PASS-unknown:IN=eth1 OUT=eth0 SRC=192.168.1.250 DST=192.168.1.51 LEN=576 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
[  140.944000] PASS-unknown:IN=eth1 OUT=eth0 SRC=192.168.1.250 DST=192.168.1.51 LEN=576 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
[  142.008000] PASS-unknown:IN=eth1 OUT=eth0 SRC=192.168.1.250 DST=192.168.1.51 LEN=576 TOS=0x00 PREC=0x00 TTL=63 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
[  142.304000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=285 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=265 
[  142.356000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=151 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=131 
[  142.552000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=285 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=265 
[  142.808000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=285 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=265 
[  143.008000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=267 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=247 
[  143.564000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=256 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=236 
[  145.480000] IN-world:IN=eth1 OUT= MAC=00:14:a5:b8:73:98:00:11:f5:1d:14:b4:08:00 SRC=192.168.1.250 DST=192.168.1.51 LEN=576 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
[  145.776000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=256 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=236 
[  146.424000] IN-world:IN=eth1 OUT= MAC= SRC=192.168.1.51 DST=224.0.0.251 LEN=267 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=247 


```




> - what is your wireless card (e.g. Intel ipw3945abg)?

Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)



> - the output from 'iwconfig'?

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"UpperTaylorRd"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:11:F5:1D:14:B5
          Bit Rate=48 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Hope that helps.  Please somebody help me!

Martin

---

