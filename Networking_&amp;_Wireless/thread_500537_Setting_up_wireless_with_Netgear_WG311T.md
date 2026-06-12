---
title: "Setting up wireless with Netgear WG311T"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by spazsui on 2007-07-14
Ok folks, just to clarify I am a beginner but have learned alot since Breezy.  I've been looking through the forums and surfing the internet looking for an answer on setting up this wireless card on my desktop.  Apparently alot of people have problems with this card even though hardware support says it works out of the box.  From everything I read I'm just going to have to post some info and start from scratch.  Hopefully I won't forget anything but here it goes:  Computer is the Biostar 210v which had a working internet connection when wired.  Card is the Netgear WG311T using the Atheros chipset AR5212  802.11abg NIC revision 1.  Running Feisty with the 2.6.20-16-generic kernal.  The card is detected by the system but I don't get an ath0 showing up in the network configuration setup.   After the card was installed Ubuntu told me that it had loaded the restricted driver and enabled it.   I have added the information on my system but if I have forgot anything let me know and I will post that on the reply.  Thanks for any help you can give me.  Below is the info I get when running -n result, ifconfig, and iwconfig:

lspci -n result

00:00.0 0600: 1106:3205 
00:01.0 0604: 1106:b198 
00:08.0 0200: 168c:0013 (rev 01) 
00:09.0 0c00: 1106:3044 (rev 80) 
00:0f.0 0104: 1106:3149 (rev 80) 
00:0f.1 0101: 1106:0571 (rev 06) 
00:10.0 0c03: 1106:3038 (rev 81) 
00:10.1 0c03: 1106:3038 (rev 81) 
00:10.2 0c03: 1106:3038 (rev 81) 
00:10.3 0c03: 1106:3038 (rev 81) 
00:10.4 0c03: 1106:3104 (rev 86) 
00:11.0 0601: 1106:3227 
00:11.5 0401: 1106:3059 (rev 60) 
00:12.0 0200: 1106:3065 (rev 78) 
01:00.0 0300: 1106:7205 (rev 01)

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:D7:C6:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:19 Base address:0xc400 

eth0:avah Link encap:Ethernet  HWaddr 00:E0:4C:D7:C6:30  
          inet addr:169.254.8.6  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:19 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:608 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:56595 (55.2 KiB)  TX bytes:56595 (55.2 KiB) 

john@john-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

Next is my dmesg which is pretty long:

dmesg 
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic) 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000] sanitize start 
[    0.000000] sanitize end 
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2 
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003def0000 end: 000000003dff0000 type: 1 
[    0.000000] copy_e820_map() type is E820_RAM 
[    0.000000] copy_e820_map() start: 000000003dff0000 size: 0000000000003000 end: 000000003dff3000 type: 4 
[    0.000000] copy_e820_map() start: 000000003dff3000 size: 000000000000d000 end: 000000003e000000 type: 3 
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2 
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2 
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2 
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable) 
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dff0000 (usable) 
[    0.000000]  BIOS-e820: 000000003dff0000 - 000000003dff3000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 000000003dff3000 - 000000003e000000 (ACPI data) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
[    0.000000] 95MB HIGHMEM available. 
[    0.000000] 896MB LOWMEM available. 
[    0.000000] found SMP MP-table at 000f56e0 
[    0.000000] Entering add_active_range(0, 0, 253936) 0 entries of 256 used 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA             0 ->     4096 
[    0.000000]   Normal       4096 ->   229376 
[    0.000000]   HighMem    229376 ->   253936 
[    0.000000] early_node_map[1] active PFN ranges 
[    0.000000]     0:        0 ->   253936 
[    0.000000] On node 0 totalpages: 253936 
[    0.000000]   DMA zone: 32 pages used for memmap 
[    0.000000]   DMA zone: 0 pages reserved 
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
[    0.000000]   Normal zone: 1760 pages used for memmap 
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31 
[    0.000000]   HighMem zone: 191 pages used for memmap 
[    0.000000]   HighMem zone: 24369 pages, LIFO batch:3 
[    0.000000] DMI 2.2 present. 
[    0.000000] ACPI: RSDP (v000 VKT400                                ) @ 0x000f71e0 
[    0.000000] ACPI: RSDT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dff3000 
[    0.000000] ACPI: FADT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dff3040 
[    0.000000] ACPI: MADT (v001 VKT400 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dff7e00 
[    0.000000] ACPI: DSDT (v001 VKT400 AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000 
[    0.000000] ACPI: PM-Timer IO Port: 0x4008 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled) 
[    0.000000] Processor #0 6:8 APIC version 16 
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3e000000:c0c00000) 
[    0.000000] Detected 1795.603 MHz processor. 
[   20.036235] Built 1 zonelists.  Total pages: 251953 
[   20.036240] Kernel command line: root=UUID=f68aca12-f0e3-4dbd-8a43-e0ba32c270fa ro quiet splash 
[   20.036432] mapped APIC to ffffd000 (fee00000) 
[   20.036435] mapped IOAPIC to ffffc000 (fec00000) 
[   20.036439] Enabling fast FPU save and restore... done. 
[   20.036442] Enabling unmasked SIMD FPU exception support... done. 
[   20.036456] Initializing CPU#0 
[   20.036544] PID hash table entries: 4096 (order: 12, 16384 bytes) 
[   20.037797] Console: colour VGA+ 80x25 
[   20.038878] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[   20.040735] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes) 
[   20.080517] Memory: 995892k/1015744k available (1992k kernel code, 19208k reserved, 900k data, 328k init, 98240k highmem) 
[   20.080545] virtual kernel memory layout: 
[   20.080546]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB) 
[   20.080547]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
[   20.080549]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB) 
[   20.080550]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB) 
[   20.080551]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB) 
[   20.080553]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB) 
[   20.080554]       .text : 0xc0100000 - 0xc02f2374   (1992 kB) 
[   20.080558] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
[   20.160489] Calibrating delay using timer specific routine.. 3594.52 BogoMIPS (lpj=7189056) 
[   20.160552] Security Framework v1.0.0 initialized 
[   20.160566] SELinux:  Disabled at boot. 
[   20.160589] Mount-cache hash table entries: 512 
[   20.160820] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 
[   20.160833] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   20.160836] CPU: L2 Cache: 256K (64 bytes/line) 
[   20.160840] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 
[   20.160856] Compat vDSO mapped to ffffe000. 
[   20.160864] Remapping vsyscall page to ffffe000 
[   20.160880] Checking 'hlt' instruction... OK. 
[   20.176699] SMP alternatives: switching to UP code 
[   20.177110] Freeing SMP alternatives: 11k freed 
[   20.177455] Early unpacking initramfs... done 
[   20.524234] ACPI: Core revision 20060707 
[   20.528105] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT. 
[   20.531722] CPU0: AMD Athlon(tm) XP 2200+ stepping 00 
[   20.531754] Total of 1 processors activated (3594.52 BogoMIPS). 
[   20.532533] ENABLING IO-APIC IRQs 
[   20.532843] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1 
[   20.680300] Brought up 1 CPUs 
[   20.680642] Booting paravirtualized kernel on bare hardware 
[   20.680759] Time:  4:30:36  Date: 06/14/107 
[   20.680804] NET: Registered protocol family 16 
[   20.680946] EISA bus registered 
[   20.680952] ACPI: bus type pci registered 
[   20.688791] PCI: PCI BIOS revision 2.10 entry at 0xfb680, last bus=1 
[   20.688794] PCI: Using configuration type 1 
[   20.688796] Setting up standard PCI resources 
[   20.696967] ACPI: Interpreter enabled 
[   20.696974] ACPI: Using IOAPIC for interrupt routing 
[   20.697723] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   20.697730] PCI: Probing PCI hardware (bus 00) 
[   20.697841] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0 
[   20.698688] Boot video device is 0000:01:00.0 
[   20.698733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   20.742519] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15) 
[   20.742885] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15) 
[   20.743262] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15) 
[   20.743610] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   20.743938] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   20.744269] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   20.744590] ACPI: PCI Interrupt Link [LNK0] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   20.744909] ACPI: PCI Interrupt Link [LNK1] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled. 
[   20.745322] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled. 
[   20.745724] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled. 
[   20.746147] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled. 
[   20.746551] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled. 
[   20.750277] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   20.750295] pnp: PnP ACPI init 
[   20.755644] pnp: PnP ACPI: found 14 devices 
[   20.755651] PnPBIOS: Disabled by ACPI PNP 
[   20.755732] PCI: Using ACPI for IRQ routing 
[   20.755738] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   20.783498] NET: Registered protocol family 8 
[   20.783501] NET: Registered protocol family 20 
[   20.783955] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved 
[   20.783959] pnp: 00:02: ioport range 0x5000-0x500f has been reserved 
[   20.784327] PCI: Bridge: 0000:00:01.0 
[   20.784329]   IO window: disabled. 
[   20.784335]   MEM window: dc000000-ddffffff 
[   20.784339]   PREFETCH window: d8000000-dbffffff 
[   20.784359] PCI: Setting latency timer of device 0000:00:01.0 to 64 
[   20.784396] NET: Registered protocol family 2 
[   20.816293] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[   20.816597] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[   20.819136] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[   20.820462] TCP: Hash tables configured (established 131072 bind 65536) 
[   20.820468] TCP reno registered 
[   20.832363] checking if image is initramfs... it is 
[   21.481468] Freeing initrd memory: 6769k freed 
[   21.482093] audit: initializing netlink socket (disabled) 
[   21.482113] audit(1184387436.524:1): initialized 
[   21.482200] highmem bounce pool size: 64 pages 
[   21.482281] VFS: Disk quotas dquot_6.5.1 
[   21.482314] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[   21.482399] io scheduler noop registered 
[   21.482402] io scheduler anticipatory registered 
[   21.482405] io scheduler deadline registered 
[   21.482414] io scheduler cfq registered (default) 
[   21.482492] PCI: Bypassing VIA 8237 APIC De-Assert Message 
[   21.482773] isapnp: Scanning for PnP cards... 
[   21.836518] isapnp: No Plug & Play device found 
[   21.871939] Real Time Clock Driver v1.12ac 
[   21.872017] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   21.872149] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   21.872479] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   21.873387] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[   21.873860] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[   21.874262] mice: PS/2 mouse device common for all mice 
[   21.874962] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   21.875308] input: Macintosh mouse button emulation as /class/input/input0 
[   21.875349] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   21.875355] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   21.875707] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1 
[   21.875711] PNP: PS/2 controller doesn't have AUX irq; using default 12 
[   22.131584] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   22.131830] EISA: Probing bus 0 at eisa.0 
[   22.131854] Cannot allocate resource for EISA slot 4 
[   22.131857] Cannot allocate resource for EISA slot 5 
[   22.131870] EISA: Detected 0 cards. 
[   22.161977] TCP cubic registered 
[   22.161985] NET: Registered protocol family 1 
[   22.162018] Using IPI No-Shortcut mode 
[   22.162102] ACPI: (supports S0 S1 S4 S5) 
[   22.162163]   Magic number: 15:954:514 
[   22.162947] Freeing unused kernel memory: 328k freed 
[   22.163504] Time: tsc clocksource has been installed. 
[   22.176399] input: AT Translated Set 2 keyboard as /class/input/input1 
[   23.439912] Capability LSM initialized 
[   23.484763] ACPI: Fan [FAN] (on) 
[   23.491233] ACPI: Thermal Zone [THRM] (40 C) 
[   24.151840] usbcore: registered new interface driver usbfs 
[   24.151877] usbcore: registered new interface driver hub 
[   24.151908] usbcore: registered new device driver usb 
[   24.153057] USB Universal Host Controller Interface driver v3.0 
[   24.153604] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21 
[   24.153608] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21 
[   24.153622] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16 
[   24.153638] uhci_hcd 0000:00:10.0: UHCI Host Controller 
[   24.153843] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1 
[   24.153882] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000b000 
[   24.154076] usb usb1: configuration #1 chosen from 1 choice 
[   24.154110] hub 1-0:1.0: USB hub found 
[   24.154124] hub 1-0:1.0: 2 ports detected 
[   24.193432] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker 
[   24.213815] ieee1394: Initialized config rom entry `ip1394' 
[   24.229692] SCSI subsystem initialized 
[   24.235889] libata version 2.20 loaded. 
[   24.258622] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16 
[   24.258643] uhci_hcd 0000:00:10.1: UHCI Host Controller 
[   24.258675] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2 
[   24.258705] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000b400 
[   24.258842] usb usb2: configuration #1 chosen from 1 choice 
[   24.258884] hub 2-0:1.0: USB hub found 
[   24.258896] hub 2-0:1.0: 2 ports detected 
[   24.366557] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16 
[   24.366576] uhci_hcd 0000:00:10.2: UHCI Host Controller 
[   24.366607] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3 
[   24.366637] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000b800 
[   24.366775] usb usb3: configuration #1 chosen from 1 choice 
[   24.366807] hub 3-0:1.0: USB hub found 
[   24.366820] hub 3-0:1.0: 2 ports detected 
[   24.394837] Floppy drive(s): fd0 is 1.44M 
[   24.450046] FDC 0 is a post-1991 82077 
[   24.474504] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16 
[   24.474525] uhci_hcd 0000:00:10.3: UHCI Host Controller 
[   24.474571] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4 
[   24.474601] uhci_hcd 0000:00:10.3: irq 16, io base 0x0000bc00 
[   24.474740] usb usb4: configuration #1 chosen from 1 choice 
[   24.474772] hub 4-0:1.0: USB hub found 
[   24.474786] hub 4-0:1.0: 2 ports detected 
[   24.582554] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16 
[   24.582575] ehci_hcd 0000:00:10.4: EHCI Host Controller 
[   24.582619] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5 
[   24.582680] ehci_hcd 0000:00:10.4: irq 16, io mem 0xde011000 
[   24.582687] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   24.582794] usb usb5: configuration #1 chosen from 1 choice 
[   24.582828] hub 5-0:1.0: USB hub found 
[   24.582842] hub 5-0:1.0: 8 ports detected 
[   24.634216] usb 1-2: new low speed USB device using uhci_hcd and address 2 
[   24.690683] sata_via 0000:00:0f.0: version 2.1 
[   24.691181] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20 
[   24.691185] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20 
[   24.691197] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17 
[   24.691222] sata_via 0000:00:0f.0: routed to hard irq line 10 
[   24.691340] ata1: SATA max UDMA/133 cmd 0x00019400 ctl 0x00019802 bmdma 0x0001a400 irq 17 
[   24.708279] ata2: SATA max UDMA/133 cmd 0x00019c00 ctl 0x0001a002 bmdma 0x0001a408 irq 17 
[   24.708314] scsi0 : sata_via 
[   24.914044] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300) 
[   24.924488] ATA: abnormal status 0x7F on port 0x00019407 
[   24.924514] scsi1 : sata_via 
[   25.129935] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300) 
[   25.140379] ATA: abnormal status 0x7F on port 0x00019c07 
[   25.140842] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 18 
[   25.193882] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[de010000-de0107ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[   25.200352] VP_IDE: IDE controller at PCI slot 0000:00:0f.1 
[   25.200385] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17 
[   25.200402] VP_IDE: chipset revision 6 
[   25.200404] VP_IDE: not 100% native mode: will probe irqs later 
[   25.200416] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1 
[   25.200426]     ide0: BM-DMA at 0xac00-0xac07, BIOS settings: hda:DMA, hdb:pio 
[   25.200443]     ide1: BM-DMA at 0xac08-0xac0f, BIOS settings: hdc:DMA, hdd:pio 
[   25.200454] Probing IDE interface ide0... 
[   25.625756] hda: ST3120026A, ATA DISK drive 
[   26.029469] usb 1-2: new low speed USB device using uhci_hcd and address 3 
[   26.207600] usb 1-2: configuration #1 chosen from 1 choice 
[   26.225920] usbcore: registered new interface driver hiddev 
[   26.244911] input: Logitech USB RECEIVER as /class/input/input2 
[   26.245044] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.0-2 
[   26.245068] usbcore: registered new interface driver usbhid 
[   26.245073] drivers/usb/input/hid-core.c: v2.6:USB HID core driver 
[   26.301968] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[   26.305801] Probing IDE interface ide1... 
[   26.477501] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0030670000056905] 
[   27.176948] hdc: TSSTcorpCD/DVDW SH-S182D, ATAPI CD/DVD-ROM drive 
[   27.849330] ide1 at 0x170-0x177,0x376 on irq 15 
[   27.857091] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23 
[   27.857098] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23 
[   27.857111] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19 
[   27.862440] eth0: VIA Rhine II at 0x1c400, 00:e0:4c:d7:c6:30, IRQ 19. 
[   27.863161] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000. 
[   27.872465] hda: max request size: 512KiB 
[   27.887530] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100) 
[   27.887842] hda: cache flushes supported 
[   27.887913]  hda: hda1 hda2 < hda5 > 
[   27.946942] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33) 
[   27.946955] Uniform CD-ROM driver Revision: 3.20 
[   28.161068] Attempting manual resume 
[   28.161073] swsusp: Resume From Partition 3:5 
[   28.161075] PM: Checking swsusp image. 
[   28.161570] PM: Resume from disk failed. 
[   28.214567] kjournald starting.  Commit interval 5 seconds 
[   28.214587] EXT3-fs: mounted filesystem with ordered data mode. 
[   36.707589] eth0: link down 
[   38.250952] NET: Registered protocol family 17 
[   38.726931] ath_hal: module license 'Proprietary' taints kernel. 
[   38.727945] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[   39.716986] wlan: 0.8.4.2 (0.9.3) 
[   39.737825] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   39.740962] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   39.756096] Linux agpgart interface v0.102 (c) Dave Jones 
[   39.759566] agpgart: Detected VIA KM400/KM400A chipset 
[   39.769438] agpgart: AGP aperture is 128M @ 0xd0000000 
[   39.831575] input: PC Speaker as /class/input/input3 
[   39.902127] ath_pci: 0.9.4.5 (0.9.3) 
[   39.912504] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   39.913393] wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14) 
[   39.913413] ACPI: PCI interrupt for device 0000:00:08.0 disabled 
[   40.198028] parport: PnPBIOS parport detected. 
[   40.198092] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE] 
[   40.455651] usbcore: registered new interface driver lmpcm_usb 
[   40.455659] ubuntu/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver 
[   40.711159] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22 
[   40.711166] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22 
[   40.711178] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21 
[   40.711328] PCI: Setting latency timer of device 0000:00:11.5 to 64 
[   41.437914] fuse init (API version 7.8) 
[   41.478505] lp0: using parport0 (interrupt-driven). 
[   41.548559] Adding 2939852k swap on /dev/disk/by-uuid/05cc1dd1-7ac9-4e64-b0b5-2a41454822a2.  Priority:-1 extents:1 across:2939852k 
[   41.707161] EXT3 FS on hda1, internal journal 
[   47.539607] input: Power Button (FF) as /class/input/input4 
[   47.545696] ACPI: Power Button (FF) [PWRF] 
[   47.588316] input: Power Button (CM) as /class/input/input5 
[   47.594329] ACPI: Power Button (CM) [PWRB] 
[   47.637445] input: Sleep Button (CM) as /class/input/input6 
[   47.643546] ACPI: Sleep Button (CM) [SLPB] 
[   47.665245] Using specific hotkey driver 
[   47.908565] No dock devices found. 
[   47.952279] ibm_acpi: ec object not found 
[   48.027140] pcc_acpi: loading... 
[   51.847711] [drm] Initialized drm 1.1.0 20060810 
[   51.864199] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   51.868233] [drm] Initialized via 2.11.0 20061227 on minor 0 
[   51.905443] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0. 
[   51.905827] agpgart: Device is in legacy mode, falling back to 2.x 
[   51.906039] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode 
[   51.906305] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode 
[   51.912166] [drm:via_mem_alloc] *ERROR* Attempt to allocate from uninitialized memory manager. 
[   52.354830] ppdev: user-space parallel port driver 
[   53.437282] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac) 
[   53.437291] apm: overridden by ACPI. 
[   53.787815] Bluetooth: Core ver 2.11 
[   53.787937] NET: Registered protocol family 31 
[   53.787940] Bluetooth: HCI device and connection manager initialized 
[   53.787947] Bluetooth: HCI socket layer initialized 
[   53.890076] Bluetooth: L2CAP ver 2.8 
[   53.890084] Bluetooth: L2CAP socket layer initialized 
[   53.968907] Bluetooth: RFCOMM socket layer initialized 
[   53.968936] Bluetooth: RFCOMM TTY layer initialized 
[   53.968939] Bluetooth: RFCOMM ver 1.8 
[   79.094010] NET: Registered protocol family 10 
[   79.094164] lo: Disabled Privacy Extensions 
[   79.094255] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[  255.078125] usb 3-2: new full speed USB device using uhci_hcd and address 2 
[  258.172039] usb 3-2: configuration #1 chosen from 1 choice 
[  258.285485] usbcore: registered new interface driver libusual 
[  258.301418] Initializing USB Mass Storage driver... 
[  258.301547] scsi2 : SCSI emulation for USB Mass Storage devices 
[  258.301630] usbcore: registered new interface driver usb-storage 
[  258.301634] USB Mass Storage support registered. 
[  258.301842] usb-storage: device found at 2 
[  258.301845] usb-storage: waiting for device to settle before scanning 
[  263.315222] usb-storage: device scan complete 
[  263.318221] scsi 2:0:0:0: Direct-Access     CREATIVE MuVo V100        1023 PQ: 0 ANSI: 4 
[  263.359137] SCSI device sda: 1011520 2048-byte hdwr sectors (2072 MB) 
[  263.362129] sda: Write Protect is off 
[  263.362132] sda: Mode Sense: 38 00 00 00 
[  263.362135] sda: assuming drive cache: write through 
[  263.371123] SCSI device sda: 1011520 2048-byte hdwr sectors (2072 MB) 
[  263.374119] sda: Write Protect is off 
[  263.374122] sda: Mode Sense: 38 00 00 00 
[  263.374124] sda: assuming drive cache: write through 
[  263.374643]  sda: sda1 
[  263.382544] sd 2:0:0:0: Attached scsi removable disk sda 
[  263.399525] sd 2:0:0:0: Attached scsi generic sg0 type 0

---

### Post by spazsui on 2007-07-15
Hmmm, nobody has a clue?  Hopefully someone out there knows how to fix it.   Thanks!

---

