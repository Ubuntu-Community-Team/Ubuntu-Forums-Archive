---
title: "network card not detected"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by romihim on 2007-09-29
the subject says it all. 
so i m posting the result of some commands which i typed
:-

himanshu@himanshu-desktop:~/Desktop/sc$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
01:01.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)



himanshu@himanshu-desktop:~/Desktop/sc$ sudo modprobe 8139cp
himanshu@himanshu-desktop:~/Desktop/sc$ sudo modprobe 8139too
himanshu@himanshu-desktop:~/Desktop/sc$ lsmod | grep 8139
8139cp                 25088  0 
8139too                27648  0 
mii                     6528  2 8139cp,8139too



himanshu@himanshu-desktop:~/Desktop/sc$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


dmesg | grep 8139
[   22.781392] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 1456.962342] 8139too Fast Ethernet driver 0.9.28
[ 2079.753379] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)


himanshu@himanshu-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=40 mingnt=20
       resources: iomemory:ed010000-ed0100ff ioport:c000-c0ff irq:11


himanshu@himanshu-desktop:~$ dmesg | grep irqpoll
<no msg>

---

### Post by romihim on 2007-09-29
i m dual booting ubuntu with xp. in july i had ubuntu with internet working with the same card(that time the card worked out of box for me ),then i had to format my hard disk due to some reasons ....but wen i reinstalled feisty again ,it is not detecting my network card .

plz help

---

### Post by SeanTater on 2007-09-29
I believe it would be most helpful if you gave us the chipset or other information about your wireless card. There are numerous tutorials, as long as you know which card you have.

---

### Post by noob12 on 2007-09-29
The UNCLAIMED indicates the driver didn't successfully claim the device at all.  The dmesg snippets are not really enough to see what is going on.  If you can get the full **dmesg** output from there it might be possible to see more.

Typically this is due to a PCI routing issue.  Before you re-installed were you booting with some additional boot flags?  If so, do you remember what you had used before?  Can you try booting with the option **pci=noacpi** ?  (Let me know if you need instructions for that.)


[NOTE: If you get the driver to claim the device and still have problems, make sure you also know about these other issues, which you are likely to run into: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448).  This is not your current issue. ]

---

### Post by romihim on 2007-09-29
previously i just didnot do any thing .....................
except plugging in the card .
today when i was researching  for the prob , somewhere it was asked to add irqpoll to boot parameters ,so now having irqpoll added .

---

### Post by romihim on 2007-09-29
himanshu@himanshu-desktop:~/Desktop/sc$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001f6f0000 end: 000000001f7f0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001f7f0000 size: 0000000000003000 end: 000000001f7f3000 type: 4
[    0.000000] copy_e820_map() start: 000000001f7f3000 size: 000000000000d000 end: 000000001f800000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000001f7f0000 - 000000001f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f7f3000 - 000000001f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 503MB LOWMEM available.
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
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f7290
[    0.000000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1f7f3000
[    0.000000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1f7f3040
[    0.000000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:df400000)
[    0.000000] Detected 1717.104 MHz processor.
[   17.550863] Built 1 zonelists.  Total pages: 128001
[   17.550870] Kernel command line: root=UUID=3231b27c-4b05-4cfb-9d05-dd21221643aa ro quiet splash
[   17.551118] Found and enabled local APIC!
[   17.551123] mapped APIC to ffffd000 (fee00000)
[   17.551128] Enabling fast FPU save and restore... done.
[   17.551133] Enabling unmasked SIMD FPU exception support... done.
[   17.551149] Initializing CPU#0
[   17.551255] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   17.552996] Console: colour VGA+ 80x25
[   17.553378] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.553809] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.572025] Memory: 500416k/516032k available (1992k kernel code, 15132k reserved, 893k data, 328k init, 0k highmem)
[   17.572040] virtual kernel memory layout:
[   17.572041]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.572043]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.572045]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   17.572046]     lowmem  : 0xc0000000 - 0xdf7f0000   ( 503 MB)
[   17.572048]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   17.572050]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   17.572052]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   17.572057] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.651199] Calibrating delay using timer specific routine.. 3437.50 BogoMIPS (lpj=6875015)
[   17.651267] Security Framework v1.0.0 initialized
[   17.651277] SELinux:  Disabled at boot.
[   17.651308] Mount-cache hash table entries: 512
[   17.651539] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   17.651558] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   17.651562] CPU: L2 cache: 256K
[   17.651566] CPU: Hyper-Threading is disabled
[   17.651569] CPU: After all inits, caps: 3febfbff 00000000 00000000 00003080 00000000 00000000 00000000
[   17.651587] Compat vDSO mapped to ffffe000.
[   17.651593] Remapping vsyscall page to ffffe000
[   17.651613] Checking 'hlt' instruction... OK.
[   17.667384] SMP alternatives: switching to UP code
[   17.667726] Freeing SMP alternatives: 11k freed
[   17.668088] Early unpacking initramfs... done
[   18.156173] ACPI: Core revision 20060707
[   18.161837] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.164413] ACPI: setting ELCR to 0200 (from 0e20)
[   18.175223] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   18.175233] SMP motherboard not detected.
[   18.282871] Brought up 1 CPUs
[   18.283296] Booting paravirtualized kernel on bare hardware
[   18.283422] Time: 13:02:02  Date: 08/29/107
[   18.283473] NET: Registered protocol family 16
[   18.283657] EISA bus registered
[   18.283667] ACPI: bus type pci registered
[   18.308920] PCI: PCI BIOS revision 2.10 entry at 0xfaea0, last bus=1
[   18.308925] PCI: Using configuration type 1
[   18.308928] Setting up standard PCI resources
[   18.321300] ACPI: Interpreter enabled
[   18.321308] ACPI: Using PIC for interrupt routing
[   18.322298] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.322306] PCI: Probing PCI hardware (bus 00)
[   18.322842] Boot video device is 0000:00:02.0
[   18.323187] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   18.323189] * this clock source is slow. If you are sure your timer does not have
[   18.323191] * this bug, please use "acpi_pm_good" to disable the workaround
[   18.323249] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   18.323254] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   18.323711] PCI: Transparent bridge - 0000:00:1e.0
[   18.323748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.357244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.359234] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   18.359685] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   18.360128] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   18.360565] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   18.360997] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   18.361434] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   18.361865] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   18.362299] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   18.367161] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.367190] pnp: PnP ACPI init
[   18.374360] pnp: PnP ACPI: found 16 devices
[   18.374370] PnPBIOS: Disabled by ACPI PNP
[   18.374477] PCI: Using ACPI for IRQ routing
[   18.374483] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.386935] NET: Registered protocol family 8
[   18.386939] NET: Registered protocol family 20
[   18.387640] pnp: 00:03: ioport range 0x400-0x4bf could not be reserved
[   18.388175] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   18.388195] PCI: Bridge: 0000:00:1e.0
[   18.388199]   IO window: c000-cfff
[   18.388207]   MEM window: ec000000-edffffff
[   18.388213]   PREFETCH window: 20000000-200fffff
[   18.388232] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.388280] NET: Registered protocol family 2
[   18.426837] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.426984] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.427109] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   18.427178] TCP: Hash tables configured (established 16384 bind 8192)
[   18.427182] TCP reno registered
[   18.438945] checking if image is initramfs... it is
[   19.395181] Freeing initrd memory: 7011k freed
[   19.395863] audit: initializing netlink socket (disabled)
[   19.395884] audit(1191070922.916:1): initialized
[   19.396116] VFS: Disk quotas dquot_6.5.1
[   19.396147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.396227] io scheduler noop registered
[   19.396233] io scheduler anticipatory registered
[   19.396236] io scheduler deadline registered
[   19.396250] io scheduler cfq registered (default)
[   19.396704] isapnp: Scanning for PnP cards...
[   19.750925] isapnp: No Plug & Play device found
[   19.831672] Real Time Clock Driver v1.12ac
[   19.831756] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.831919] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.832326] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.833775] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.834446] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   19.835049] mice: PS/2 mouse device common for all mice
[   19.836002] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.836431] input: Macintosh mouse button emulation as /class/input/input0
[   19.836499] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.836506] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.836851] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.839814] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.839826] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.840118] EISA: Probing bus 0 at eisa.0
[   19.840162] EISA: Detected 0 cards.
[   19.870305] TCP cubic registered
[   19.870319] NET: Registered protocol family 1
[   19.870446] Testing NMI watchdog ... OK.
[   19.910157] Using IPI No-Shortcut mode
[   19.910256] ACPI: (supports S0 S1 S4 S5)
[   19.910332]   Magic number: 7:537:29
[   19.910348]   hash matches device ttydc
[   19.911011] Freeing unused kernel memory: 328k freed
[   19.913781] Time: tsc clocksource has been installed.
[   19.923492] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.410113] Capability LSM initialized
[   21.478313] ACPI: Fan [FAN] (on)
[   21.484576] ACPI: Processor [CPU0] (supports 2 throttling states)
[   21.487233] ACPI: Thermal Zone [THRM] (41 C)
[   22.449831] usbcore: registered new interface driver usbfs
[   22.449880] usbcore: registered new interface driver hub
[   22.449921] usbcore: registered new device driver usb
[   22.451574] USB Universal Host Controller Interface driver v3.0
[   22.451974] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   22.451980] PCI: setting IRQ 10 as level-triggered
[   22.451985] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   22.452002] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.452008] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.452238] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.452274] uhci_hcd 0000:00:1d.0: irq 10, io base 0x0000d800
[   22.452469] usb usb1: configuration #1 chosen from 1 choice
[   22.452512] hub 1-0:1.0: USB hub found
[   22.452527] hub 1-0:1.0: 2 ports detected
[   22.529714] SCSI subsystem initialized
[   22.539305] libata version 2.20 loaded.
[   22.560572] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   22.560580] PCI: setting IRQ 9 as level-triggered
[   22.560584] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   22.560602] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.560608] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.560664] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.560695] uhci_hcd 0000:00:1d.1: irq 9, io base 0x0000d000
[   22.560860] usb usb2: configuration #1 chosen from 1 choice
[   22.560903] hub 2-0:1.0: USB hub found
[   22.560918] hub 2-0:1.0: 2 ports detected
[   22.668560] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   22.668567] PCI: setting IRQ 11 as level-triggered
[   22.668572] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   22.668590] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.668596] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.668652] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.668685] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000d400
[   22.668837] usb usb3: configuration #1 chosen from 1 choice
[   22.668885] hub 3-0:1.0: USB hub found
[   22.668897] hub 3-0:1.0: 2 ports detected
[   22.748924] Floppy drive(s): fd0 is 1.44M
[   22.777322] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   22.777331] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   22.777352] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.777358] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.777440] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.777492] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.777503] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xee080000
[   22.781392] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.781539] usb usb4: configuration #1 chosen from 1 choice
[   22.781585] hub 4-0:1.0: USB hub found
[   22.781600] hub 4-0:1.0: 6 ports detected
[   22.834287] FDC 0 is a post-1991 82077
[   22.888517] ata_piix 0000:00:1f.1: version 2.10ac1
[   22.888549] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   22.888579] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.888694] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   22.888742] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   22.888780] scsi0 : ata_piix
[   23.060134] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.060141] ata1.00: ATA-6: ST340810A, 3.99, max UDMA/100
[   23.060145] ata1.00: 78165360 sectors, multi 16: LBA 
[   23.072112] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
[   23.072117] ata1.00: configured for UDMA/100
[   23.072133] scsi1 : ata_piix
[   23.591589] ata2.00: ATAPI, max UDMA/66
[   23.591595] ata2.01: ATAPI, max UDMA/33
[   23.591603] ata2.00: limited to UDMA/33 due to 40-wire cable
[   23.783468] ata2.00: configured for UDMA/33
[   23.955351] ata2.01: configured for UDMA/33
[   23.955564] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        3.99 PQ: 0 ANSI: 5
[   23.957270] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DW-G120A  MYR5 PQ: 0 ANSI: 5
[   23.958736] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R952 PQ: 0 ANSI: 5
[   24.006156] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[   24.007620] sda: Write Protect is off
[   24.007626] sda: Mode Sense: 00 3a 00 00
[   24.009432] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.009542] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
[   24.009560] sda: Write Protect is off
[   24.009564] sda: Mode Sense: 00 3a 00 00
[   24.009592] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.009597]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[   24.087630] sd 0:0:0:0: Attached scsi disk sda
[   24.094394] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.094426] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   24.094454] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   24.131288] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.131297] Uniform CD-ROM driver Revision: 3.20
[   24.131694] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.137424] sr1: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   24.137755] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   24.642029] Attempting manual resume
[   24.642035] swsusp: Resume From Partition 8:6
[   24.642038] PM: Checking swsusp image.
[   24.642360] PM: Resume from disk failed.
[   24.685638] kjournald starting.  Commit interval 5 seconds
[   24.685662] EXT3-fs: mounted filesystem with ordered data mode.
[   40.459622] iTCO_vendor_support: vendor-support=0
[   40.466112] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   40.466263] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   40.466272] iTCO_wdt: No card detected
[   40.486102] intel_rng: FWH not detected
[   40.992455] Linux agpgart interface v0.102 (c) Dave Jones
[   41.003131] agpgart: Detected an Intel 845G Chipset.
[   41.003255] agpgart: Detected 8060K stolen memory.
[   41.021626] agpgart: AGP aperture is 128M @ 0xe0000000
[   41.035703] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.065715] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.329847] parport: PnPBIOS parport detected.
[   41.329903] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.342698] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   41.356021] input: PC Speaker as /class/input/input2
[   41.676682] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   41.948368] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   41.948375] PCI: setting IRQ 5 as level-triggered
[   41.948381] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   41.948426] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   42.271155] intel8x0_measure_ac97_clock: measured 58861 usecs
[   42.271161] intel8x0: clocking to 48000
[   42.525987] fuse init (API version 7.8)
[   42.550722] lp0: using parport0 (interrupt-driven).
[   42.605359] Adding 385520k swap on /dev/disk/by-uuid/9bc5bc7b-c729-4b32-a401-36e2a73545c5.  Priority:-1 extents:1 across:385520k
[   42.946421] EXT3 FS on sda5, internal journal
[   88.475918] NET: Registered protocol family 17
[   94.255127] input: Power Button (FF) as /class/input/input4
[   94.262308] ACPI: Power Button (FF) [PWRF]
[   94.313706] input: Power Button (CM) as /class/input/input5
[   94.320834] ACPI: Power Button (CM) [PWRB]
[   94.345355] Using specific hotkey driver
[   94.385944] No dock devices found.
[   94.466621] ibm_acpi: ec object not found
[   94.689292] pcc_acpi: loading...
[  100.773286] ppdev: user-space parallel port driver
[  102.056693] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  102.056701] apm: overridden by ACPI.
[  102.355810] Bluetooth: Core ver 2.11
[  102.355905] NET: Registered protocol family 31
[  102.355909] Bluetooth: HCI device and connection manager initialized
[  102.355915] Bluetooth: HCI socket layer initialized
[  102.417687] Bluetooth: L2CAP ver 2.8
[  102.417694] Bluetooth: L2CAP socket layer initialized
[  102.544850] Bluetooth: RFCOMM socket layer initialized
[  102.544877] Bluetooth: RFCOMM TTY layer initialized
[  102.544880] Bluetooth: RFCOMM ver 1.8
[  115.254239] NET: Registered protocol family 10
[  115.254389] lo: Disabled Privacy Extensions
[ 1456.962342] 8139too Fast Ethernet driver 0.9.28
[ 1708.863528] drivers/usb/net/rtl8150.c: rtl8150 based usb-ethernet driver v0.6.2 (2004/08/27)
[ 1708.864430] usbcore: registered new interface driver rtl8150
[ 1715.171933] usbcore: registered new interface driver rtl8187
[ 2079.753379] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

---

### Post by noob12 on 2007-09-30
After you boot you can look in your dmesg for a line like this.  It will tell you what flags were on the command line.  
```
[ 17.550870] Kernel command line: root=UUID=3231b27c-4b05-4cfb-9d05-dd21221643aa ro quiet splash
```

In this case, it reveals you hadn't sucessfully added the **irqpoll** flag.

Here are instructions for how to set boot flags for a one-time boot.  I would try each of these (independently) to see if they help:  **irqpoll** , **pci=noacpi**

**Instructions for one-time boot flag entry**

When booting you'll normally see  a boot selection menu flash up for a little while.  While this menu is up with the default boot selection highlighted, press **e**.  This will take you to a screen that shows the boot commands for that selection.  Use the arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  This will put you into an editing mode for that line with the cursor at the end of the line.   Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.

---

