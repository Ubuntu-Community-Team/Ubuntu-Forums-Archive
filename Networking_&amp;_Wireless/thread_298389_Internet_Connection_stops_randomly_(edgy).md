---
title: "Internet Connection stops randomly (edgy)"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by not_cool on 2006-11-12
I can get out to the internet using my wirless connection, but after a while of browsing the web (or using wine with programs that need the internet, or anything else, it doesn't matter), my connection drops. I can't get back out to the web (the gnome panel system monitor shows no network use). Every time I have to reboot (I'm sure there is an easier way but I just came over from a short period at gentoo and am not used to some of the ubuntu commands such as start/stop wlan0/eth0).
My current connection is wlan0, but it doesn't matter if I use eth0 either. My wireless card is WPC54G v2, which Ubuntu configured during installation. 

ifconfig output
```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:10:90:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:10:98:A5:D0  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:10ff:fe98:a5d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1880 errors:7 dropped:0 overruns:0 frame:0
          TX packets:1711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1493994 (1.4 MiB)  TX bytes:266303 (260.0 KiB)
          Interrupt:11 

```

dmesg output
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000002eff0000 (usable)
[17179569.184000]  BIOS-e820: 000000002eff0000 - 000000002effffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000002effffc0 - 000000002f000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 751MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 192496
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 188400 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e4010
[17179569.184000] ACPI: RSDT (v001 OID_00 RSDT_000 0x30303030 &#65533;& 0x00010007) @ 0x2efffbc0
[17179569.184000] ACPI: FADT (v002 INSYDE FACP_000 0x00000100 &#65533;& 0x00010007) @ 0x2efffac0
[17179569.184000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 &#65533;& 0x00010007) @ 0x2efffb50
[17179569.184000] ACPI: DBGP (v001 INSYDE SYS_DBGP 0x00000100 &#65533;& 0x00010007) @ 0x2efffb80
[17179569.184000] ACPI: DSDT (v001 INSYDE   VT8362 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 2f000000:d0f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (015ec000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1200.283 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.468000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.472000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.516000] Memory: 753256k/769984k available (1910k kernel code, 16160k reserved, 1070k data, 308k init, 0k highmem)
[17179572.516000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.596000] Calibrating delay using timer specific routine.. 2402.59 BogoMIPS (lpj=4805198)
[17179572.596000] Security Framework v1.0.0 initialized
[17179572.596000] SELinux:  Disabled at boot.
[17179572.596000] Mount-cache hash table entries: 512
[17179572.596000] CPU: After generic identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.596000] CPU: After vendor identify, caps: 0183f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.596000] Enabling disabled K7/SSE Support.
[17179572.596000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.596000] CPU: L2 Cache: 64K (64 bytes/line)
[17179572.596000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.596000] Checking 'hlt' instruction... OK.
[17179572.612000] SMP alternatives: switching to UP code
[17179572.612000] Freeing SMP alternatives: 16k freed
[17179572.612000] checking if image is initramfs... it is
[17179573.448000] Freeing initrd memory: 5563k freed
[17179573.448000] ACPI: Core revision 20060707
[17179573.448000] ACPI: Looking for DSDT ... not found!
[17179573.448000] ACPI: setting ELCR to 0200 (from 0c00)
[17179573.460000] CPU0: AMD mobile AMD  Duron(tm) stepping 02
[17179573.460000] SMP motherboard not detected.
[17179573.460000] Local APIC not detected. Using dummy APIC emulation.
[17179573.460000] Brought up 1 CPUs
[17179573.460000] migration_cost=0
[17179573.460000] NET: Registered protocol family 16
[17179573.460000] EISA bus registered
[17179573.460000] ACPI: bus type pci registered
[17179573.460000] PCI: PCI BIOS revision 2.10 entry at 0xe8a44, last bus=1
[17179573.460000] PCI: Using configuration type 1
[17179573.460000] Setting up standard PCI resources
[17179573.532000] ACPI: Interpreter enabled
[17179573.532000] ACPI: Using PIC for interrupt routing
[17179573.532000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.532000] PCI: Probing PCI hardware (bus 00)
[17179573.532000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.536000] Disabling VIA memory write queue (PCI ID 0305, rev 80): [55] 3c & 1f -> 1c
[17179573.536000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.536000] Boot video device is 0000:01:00.0
[17179573.536000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.548000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179573.548000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[17179573.552000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.552000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[17179573.552000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
[17179573.552000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.552000] pnp: PnP ACPI init
[17179573.556000] PCI: setting IRQ 13 as level-triggered
[17179573.556000] pnp: PnP ACPI: found 11 devices
[17179573.556000] PnPBIOS: Disabled by ACPI PNP
[17179573.556000] PCI: Using ACPI for IRQ routing
[17179573.556000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.556000] PCI: Cannot allocate resource region 0 of device 0000:00:0a.0
[17179573.556000] pnp: 00:07: ioport range 0x1600-0x167f has been reserved
[17179573.556000] pnp: 00:07: ioport range 0x2c8-0x2cf has been reserved
[17179573.556000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179573.556000] pnp: 00:07: ioport range 0x1000-0x105f could not be reserved
[17179573.560000] PCI: Bridge: 0000:00:01.0
[17179573.560000]   IO window: c000-dfff
[17179573.560000]   MEM window: e0000000-efffffff
[17179573.560000]   PREFETCH window: 90000000-9fffffff
[17179573.560000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179573.560000]   IO window: 00001400-000014ff
[17179573.560000]   IO window: 00001800-000018ff
[17179573.560000]   PREFETCH window: 30000000-31ffffff
[17179573.560000]   MEM window: 32000000-33ffffff
[17179573.560000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.560000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179573.560000] PCI: setting IRQ 11 as level-triggered
[17179573.560000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179573.560000] NET: Registered protocol family 2
[17179573.600000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.600000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179573.604000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.604000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.604000] TCP reno registered
[17179573.604000] Simple Boot Flag at 0x37 set to 0x1
[17179573.608000] audit: initializing netlink socket (disabled)
[17179573.608000] audit(1163367592.608:1): initialized
[17179573.608000] VFS: Disk quotas dquot_6.5.1
[17179573.608000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.608000] Initializing Cryptographic API
[17179573.608000] io scheduler noop registered
[17179573.608000] io scheduler anticipatory registered
[17179573.608000] io scheduler deadline registered
[17179573.608000] io scheduler cfq registered (default)
[17179573.608000] Applying VIA southbridge workaround.
[17179573.608000] isapnp: Scanning for PnP cards...
[17179573.960000] isapnp: No Plug & Play device found
[17179574.060000] Real Time Clock Driver v1.12ac
[17179574.060000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.060000] mice: PS/2 mouse device common for all mice
[17179574.064000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.064000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.064000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.064000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179574.076000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.088000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.088000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.088000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.092000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.092000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.092000] EISA: Probing bus 0 at eisa.0
[17179574.092000] Cannot allocate resource for EISA slot 1
[17179574.096000] EISA: Detected 0 cards.
[17179574.096000] TCP bic registered
[17179574.096000] NET: Registered protocol family 1
[17179574.096000] NET: Registered protocol family 8
[17179574.096000] NET: Registered protocol family 20
[17179574.096000] Using IPI No-Shortcut mode
[17179574.096000] ACPI: (supports S0 S3 S4 S5)
[17179574.096000] Freeing unused kernel memory: 308k freed
[17179574.392000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.420000] Capability LSM initialized
[17179575.516000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.516000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.520000] ACPI: Thermal Zone [THRM] (68 C)
[17179576.812000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.812000] VP_IDE: chipset revision 6
[17179576.812000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.812000] VP_IDE: VIA vt8231 (rev 10) IDE UDMA100 controller on pci0000:00:11.1
[17179576.812000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179576.812000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179576.812000] Probing IDE interface ide0...
[17179577.228000] hda: IC25N020ATCS04-0, ATA DISK drive
[17179577.900000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.924000] Probing IDE interface ide1...
[17179578.788000] hdc: QSI CD-RW/DVD-ROM SBW-081, ATAPI CD/DVD-ROM drive
[17179579.124000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.140000] hda: max request size: 128KiB
[17179579.160000] hda: 39070080 sectors (20003 MB) w/1768KiB Cache, CHS=38760/16/63, UDMA(100)
[17179579.160000] hda: cache flushes not supported
[17179579.160000]  hda: hda1 hda2 < hda5 >
[17179579.268000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.268000] Uniform CD-ROM driver Revision: 3.20
[17179579.572000] usbcore: registered new driver usbfs
[17179579.576000] usbcore: registered new driver hub
[17179579.576000] USB Universal Host Controller Interface driver v3.0
[17179579.576000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179579.576000] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179579.576000] uhci_hcd 0000:00:11.2: UHCI Host Controller
[17179579.576000] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[17179579.576000] uhci_hcd 0000:00:11.2: irq 11, io base 0x00001200
[17179579.576000] usb usb1: configuration #1 chosen from 1 choice
[17179579.576000] hub 1-0:1.0: USB hub found
[17179579.576000] hub 1-0:1.0: 2 ports detected
[17179579.744000] Attempting manual resume
[17179579.788000] kjournald starting.  Commit interval 5 seconds
[17179579.788000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.048000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[17179580.228000] usb 1-2: configuration #1 chosen from 1 choice
[17179598.296000] parport_pc: VIA 686A/8231 detected
[17179598.296000] parport_pc: probing current configuration
[17179598.296000] parport_pc: Current parallel port base: 0x378
[17179598.296000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[17179598.404000] parport_pc: VIA parallel port: io=0x378, irq=7
[17179598.604000] irda_init()
[17179598.604000] NET: Registered protocol family 23
[17179598.652000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.752000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[17179598.760000] agpgart: AGP aperture is 64M @ 0xa0000000
[17179599.048000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179599.048000] PCI: Enabling device 0000:00:12.0 (0001 -> 0003)
[17179599.048000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.052000] eth0: VIA Rhine II at 0x1e800, 00:c0:9f:10:90:bb, IRQ 11.
[17179599.056000] eth0: MII PHY found at address 1, status 0x7809 advertising 01e1 Link 0000.
[17179599.184000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179599.276000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.416000] Floppy drive(s): fd0 is 1.44M
[17179599.856000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179599.856000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0022]
[17179599.856000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179599.856000] Yenta O2: enabling read prefetch/write burst
[17179599.984000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[17179599.984000] Socket status: 30000821
[17179600.152000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179600.152000] PCI: setting IRQ 10 as level-triggered
[17179600.152000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179600.392000] input: PC Speaker as /class/input/input1
[17179600.632000] pccard: CardBus card inserted into slot 0
[17179600.820000] eth0: link down
[17179600.832000] usbcore: registered new driver hiddev
[17179600.860000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[17179600.860000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:11.2-2
[17179600.860000] usbcore: registered new driver usbhid
[17179600.860000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179600.880000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[17179600.904000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179600.956000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179601.044000] ts: Compaq touchscreen protocol output
[17179601.104000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[17179601.104000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179601.200000] cs: IO port probe 0x100-0x3af: clean.
[17179601.200000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179601.204000] cs: IO port probe 0x820-0x8ff: clean.
[17179601.204000] cs: IO port probe 0xc00-0xcf7: clean.
[17179601.204000] cs: IO port probe 0xa00-0xaff: clean.
[17179601.512000] MC'97 0 converters and GPIO not ready (0x1)
[17179601.512000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179601.512000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179601.900000] NET: Registered protocol family 17
[17179602.036000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179602.036000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179602.036000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179602.036000] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x32020000, phymem2:0x32000000, mem1:0xefa3c000, mem1_size:8192, mem2:0xefb40000, mem2_size:131072
[17179602.432000] floppy0: no floppy controllers found
[17179603.160000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[17179603.160000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[17179603.160000] usbcore: registered new driver acx_usb
[17179603.268000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179603.472000] lp0: using parport0 (interrupt-driven).
[17179603.556000] Adding 827308k swap on /dev/disk/by-uuid/34cf094e-13b7-4a83-9c63-f7e26ab2173c.  Priority:-1 extents:1 across:827308k
[17179603.676000] EXT3 FS on hda1, internal journal
[17179610.344000] ACPI: AC Adapter [ADP0] (on-line)
[17179610.416000] ACPI: Battery Slot [BAT0] (battery present)
[17179610.452000] ACPI: Power Button (FF) [PWRF]
[17179610.452000] ACPI: Lid Switch [LID]
[17179610.452000] ACPI: Power Button (CM) [PBTN]
[17179610.704000] ibm_acpi: ec object not found
[17179610.756000] pcc_acpi: loading...
[17179610.968000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179611.452000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17179611.456000] powernow: SGTC: 10000
[17179611.456000] powernow: Minimum speed 500 MHz. Maximum speed 1200 MHz.
[17179614.516000] NET: Registered protocol family 10
[17179614.516000] lo: Disabled Privacy Extensions
[17179614.516000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179614.516000] IPv6 over IPv4 tunneling driver
[17179615.704000] mtrr: no more MTRRs available
[17179615.708000] mtrr: no more MTRRs available
[17179616.468000] [drm] Initialized drm 1.0.1 20051102
[17179616.612000] ICMPv6 NA: someone advertises our address on wlan0!
[17179616.624000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179616.628000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[17179616.628000] mtrr: 0x90000000,0x8000000 overlaps existing 0x90000000,0x1000000
[17179616.628000] mtrr: 0x90000000,0x2000000 overlaps existing 0x90000000,0x1000000
[17179616.632000] mtrr: base(0x92000000) is not aligned on a size(0x5000000) boundary
[17179616.632000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179616.632000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179616.632000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179617.880000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179617.880000] apm: overridden by ACPI.
[17179624.772000] wlan0: no IPv6 routers present
[17179627.028000] Bluetooth: Core ver 2.8
[17179627.028000] NET: Registered protocol family 31
[17179627.028000] Bluetooth: HCI device and connection manager initialized
[17179627.028000] Bluetooth: HCI socket layer initialized
[17179627.116000] Bluetooth: L2CAP ver 2.8
[17179627.116000] Bluetooth: L2CAP socket layer initialized
[17179627.212000] Bluetooth: RFCOMM socket layer initialized
[17179627.212000] Bluetooth: RFCOMM TTY layer initialized
[17179627.212000] Bluetooth: RFCOMM ver 1.7

```

lspci output
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

If there is anything else I am missing, please ask me and I'll get it.

---

### Post by deepwave on 2006-11-12
Possibly a routing or name resolution problem.

Try route when the connection is up.  And when the connection drops, try running it again.  See if it take a longer time for route to run.  If yes, the computer is having problems finding its default gateway.  If it can't find the default gateway quickly, then URLs can not be resolved fast enough.  The network then drops connections quickly.

You can edit /etc/hosts to deal with this.

---

### Post by not_cool on 2006-11-13
Here is route when I have the connection:

```
markus@markus-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

Seeing as the connection hasn't dropped yet, I haven't been able to run route a second time. When it drops, I'll get that info. How would I edit /etc/hosts? What would I put in it? This  is my current hosts file:

```
127.0.0.1	localhost
127.0.1.1	markus-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Would I add this on the first line?

```
192.168.1.1 gateway #(Or nameserver, not sure)
```

EDIT: BTW, your explanation makes perfect sense because the connection always fails when I am trying to connect to many sites at once or am going back or forward pages quickly and repeatedly.

---

### Post by not_cool on 2006-11-13
And here is my route output when the connection drops:

```
markus@markus-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0

```

---

### Post by deepwave on 2006-11-13
Yup definitely a default gateway problem.

Try adding this line to /etc/resolv.conf
nameserver 192.168.1.1

---

### Post by not_cool on 2006-11-13
Thanks, working good so far, I'll update if the problem reappears. Sorry to ask another question in this thread, but now, when I was fooling around with the connection, seeing if I could fix it myself, I seem to have made it not run on startup. :( Now each time my computer turns on I have to run "sudo ifup wlan0." I did mess around a little with hosts, but its all back to normal. Any more help is greatly appreciated! :D

---

### Post by deepwave on 2006-11-15
To get wlan0 to run automatically at start up, make sure you have these lines in /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp

The first line means you want it to startup automatically.  The second line means you want wlan0 to use dhcp and IP4 (standard version of the Internet Protocol if I remember correctly.)

---

### Post by not_cool on 2006-11-15
Thanks, I didn't have auto wlan0 in there.

---

