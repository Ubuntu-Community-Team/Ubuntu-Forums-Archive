---
title: "Belkin 54G PCMCIA Wifi Adapter"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by TrueJk7 on 2006-10-21
History:
Allright I've checked though the forums and all posts related to this thing. It's about my fourth day and I've now got a decent Idea on how Linux does networking. If anyone would be able to help out with this thing please leave a post!

OS:
Draper Drake

installed: 
ndiswrapper 1.8 
aircrack
wifiradar

Driver:
(Straight from CD) bcmwl5.inf

Card: 
Belkin 54g FC7010

So I've had the driver installed and ndiswrapper said "driver present, hardware present" Then I plug the card in. The power lights up and the network led is off. I go to the network-admin and it's not listed there. So     I really don't know what all to do. The card seems to be alive, but network-admin, ifconfig, iwconfig, iwlist, ifup, all dont list or find the device I am working with.

I've tried 
1. reinstalling the driver
2. removeing all wifi applications
3. editing the bootmisc.sh to uninstall and reinstall through ndiswrapper at start up
4. editing the network interfaces
5. editing /etc/modules
6. removeing /etc/ndiswrapper
7. reinstalling ndiswrapper

So I'm at the point that I've searched all though ubuntu forums for belkin and wifi, read all the docs I can but no dice.

Listing of current state
(all wifi apps are gone besides ndiswrapper)

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0


```

/etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

## Linux Printer - disabling because I am going to try the SNES device later - Have to add the joy-stick alias for that
# lp
psmouse

ndiswrapper


```

/etc/modprobe.d/ndiswrapper
```
alias wlan0 ndiswrapper

```

/etc/ndiswrapper/bcmwl5$ ls
```
 14E4:4320:1799:7010.5.conf  14E4:4320.5.conf  bcmwl5.inf  bcmwl5.sys

```

```
jake@leftarm:/etc/ndiswrapper/bcmwl5$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

```

```
jake@leftarm:/etc/ndiswrapper/bcmwl5$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:95:EC:F4
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe95:ecf4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:788037 (769.5 KiB)  TX bytes:137198 (133.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

```

```
jake@leftarm:/etc/ndiswrapper/bcmwl5$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

dmesg
```
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000000ffd0000 - 000000000fff0c00 (reserved)
[17179569.184000]  BIOS-e820: 000000000fff0c00 - 000000000fffc000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000fffc000 - 0000000010000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65488
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61392 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f69f0
[17179569.184000] ACPI: RSDT (v001 COMPAQ CPQ00B7  0x18040320 CPQ  0x00000001) @ 0x0fff0c84
[17179569.184000] ACPI: FADT (v002 COMPAQ CPQ00B7  0x00000002 CPQ  0x00000001) @ 0x0fff0c00
[17179569.184000] ACPI: SSDT (v001 COMPAQ  CPQGysr 0x00001001 MSFT 0x0100000e) @ 0x0fff6c59
[17179569.184000] ACPI: DSDT (v001 COMPAQ EVON610C 0x00010000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:f0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] PM-Timer running at invalid rate: 118% of normal - aborting.
[    0.000000] Detected 2390.064 MHz processor.
[   20.773512] Using tsc for high-res timesource
[   20.774692] Console: colour VGA+ 80x25
[   20.775138] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.775532] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.788405] Memory: 249012k/261952k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[   20.788410] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.853726] Calibrating delay using timer specific routine.. 3992.79 BogoMIPS (lpj=7985580)
[   20.853758] Security Framework v1.0.0 initialized
[   20.853765] SELinux:  Disabled at boot.
[   20.853777] Mount-cache hash table entries: 512
[   20.853864] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.853872] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.853882] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   20.853884] CPU: L2 cache: 512K
[   20.853886] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[   20.853899] mtrr: v2.0 (20020519)
[   20.853904] CPU: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz stepping 07
[   20.853909] Enabling fast FPU save and restore... done.
[   20.853912] Enabling unmasked SIMD FPU exception support... done.
[   20.853917] Checking 'hlt' instruction... OK.
[   20.873691] checking if image is initramfs... it is
[   21.747086] Freeing initrd memory: 6616k freed
[   21.762139] ACPI: Looking for DSDT ... not found!
[   21.765063] ACPI: setting ELCR to 0200 (from 0c00)
[   21.793544] NET: Registered protocol family 16
[   21.793572] EISA bus registered
[   21.793575] ACPI: bus type pci registered
[   21.794346] PCI: PCI BIOS revision 2.10 entry at 0xf03a2, last bus=4
[   21.794354] PCI: Using configuration type 1
[   21.794760] ACPI: Subsystem revision 20051216
[   21.806341] ACPI: Interpreter enabled
[   21.806345] ACPI: Using PIC for interrupt routing
[   21.806606] ACPI: PCI Root Bridge [C045] (0000:00)
[   21.806612] PCI: Probing PCI hardware (bus 00)
[   21.806644] ACPI: Assume root bridge [\_SB_.C045] bus is 0
[   21.814473] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   21.814478] PCI quirk: region 1100-113f claimed by ICH4 GPIO
[   21.814530] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   21.814663] Boot video device is 0000:01:00.0
[   21.815144] PCI: Transparent bridge - 0000:00:1e.0
[   21.815254] ACPI: PCI Interrupt Routing Table [\_SB_.C045._PRT]
[   21.821317] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C046._PRT]
[   21.821558] ACPI: PCI Interrupt Routing Table [\_SB_.C045.C058._PRT]
[   21.824013] ACPI: Power Resource [C15D] (on)
[   21.825891] ACPI: Power Resource [C171] (on)
[   21.827426] ACPI: Power Resource [C175] (on)
[   21.828944] ACPI: Power Resource [C178] (on)
[   21.829280] ACPI: Power Resource [C181] (on)
[   21.830598] ACPI: PCI Interrupt Link [C0C0] (IRQs 5 10 *11)
[   21.831079] ACPI: PCI Interrupt Link [C0C1] (IRQs 5 10 *11)
[   21.831541] ACPI: PCI Interrupt Link [C0C2] (IRQs 5 10 11) *0, disabled.
[   21.832014] ACPI: PCI Interrupt Link [C0C3] (IRQs 5 10 *11)
[   21.832483] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[   21.832945] ACPI: PCI Interrupt Link [C0C5] (IRQs) *0, disabled.
[   21.833403] ACPI: PCI Interrupt Link [C0C6] (IRQs) *0, disabled.
[   21.833892] ACPI: PCI Interrupt Link [C0C7] (IRQs) *0, disabled.
[   21.835059] ACPI: Power Resource [C1EB] (off)
[   21.835195] ACPI: Power Resource [C1EC] (off)
[   21.835328] ACPI: Power Resource [C1ED] (off)
[   21.835527] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.835542] pnp: PnP ACPI init
[   21.847912] pnp: PnP ACPI: found 14 devices
[   21.847918] PnPBIOS: Disabled by ACPI PNP
[   21.847937] PCI: Using ACPI for IRQ routing
[   21.847940] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.887921] pnp: 00:0c: ioport range 0x140-0x14f has been reserved
[   21.887926] pnp: 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   21.887929] pnp: 00:0d: ioport range 0x1000-0x107f could not be reserved
[   21.887933] pnp: 00:0d: ioport range 0x1100-0x113f has been reserved
[   21.887936] pnp: 00:0d: ioport range 0x1200-0x121f has been reserved
[   21.888134] PCI: Bridge: 0000:00:01.0
[   21.888137]   IO window: 3000-3fff
[   21.888142]   MEM window: 40400000-404fffff
[   21.888146]   PREFETCH window: 48000000-4fffffff
[   21.888156] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   21.888159]   IO window: 00002800-000028ff
[   21.888163]   IO window: 00002c00-00002cff
[   21.888168]   PREFETCH window: 20000000-21ffffff
[   21.888172]   MEM window: 26000000-27ffffff
[   21.888177] PCI: Bus 7, cardbus bridge: 0000:02:06.1
[   21.888179]   IO window: 00001400-000014ff
[   21.888183]   IO window: 00001800-000018ff
[   21.888188]   PREFETCH window: 22000000-23ffffff
[   21.888192]   MEM window: 28000000-29ffffff
[   21.888196] PCI: Bridge: 0000:00:1e.0
[   21.888199]   IO window: 2000-2fff
[   21.888205]   MEM window: 40000000-403fffff
[   21.888209]   PREFETCH window: 20000000-23ffffff
[   21.888228] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   21.888248] **** SET: Misaligned resource pointer: cfe015c2 Type 07 Len 0
[   21.888605] ACPI: PCI Interrupt Link [C0C3] enabled at IRQ 11
[   21.888608] PCI: setting IRQ 11 as level-triggered
[   21.888612] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   21.888630] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   21.889070] audit: initializing netlink socket (disabled)
[   21.889080] audit(1161451468.544:1): initialized
[   21.889177] VFS: Disk quotas dquot_6.5.1
[   21.889201] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.889249] Initializing Cryptographic API
[   21.889254] io scheduler noop registered
[   21.889259] io scheduler anticipatory registered
[   21.889264] io scheduler deadline registered
[   21.889274] io scheduler cfq registered
[   21.889466] isapnp: Scanning for PnP cards...
[   22.184131] isapnp: No Plug & Play device found
[   22.198687] PNP: PS/2 Controller [PNP0303:C17E,PNP0f13:C17F] at 0x60,0x64 irq 1,12
[   22.199811] i8042.c: Detected active multiplexing controller, rev 1.1.
[   22.200568] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   22.200667] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   22.200750] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   22.200834] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   22.200915] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.200956] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   22.201057] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.201230] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   22.202984] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.203584] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.203651] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.203655] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.203814] mice: PS/2 mouse device common for all mice
[   22.204103] EISA: Probing bus 0 at eisa.0
[   22.204109] Cannot allocate resource for EISA slot 1
[   22.204112] Cannot allocate resource for EISA slot 2
[   22.204114] Cannot allocate resource for EISA slot 3
[   22.204117] Cannot allocate resource for EISA slot 4
[   22.204129] EISA: Detected 0 cards.
[   22.204177] NET: Registered protocol family 2
[   22.233236] input: AT Translated Set 2 keyboard as /class/input/input0
[   22.233697] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   22.233825] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   22.233876] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   22.233924] TCP: Hash tables configured (established 16384 bind 16384)
[   22.233927] TCP reno registered
[   22.234010] TCP bic registered
[   22.234017] NET: Registered protocol family 1
[   22.234023] NET: Registered protocol family 8
[   22.234025] NET: Registered protocol family 20
[   22.234046] Using IPI Shortcut mode
[   22.234113] ACPI wakeup devices:
[   22.234116] C058 C0AA C0B0 C0B3 C198 C199 C19B C19C
[   22.234131] ACPI: (supports S0 S3 S4 S5)
[   22.234188] Freeing unused kernel memory: 288k freed
[   22.284088] vga16fb: initializing
[   22.284094] vga16fb: mapped to 0xc00a0000
[   22.397047] Console: switching to colour frame buffer device 80x25
[   22.397052] fb0: VGA16 VGA frame buffer device
[   23.291009] Capability LSM initialized
[   23.408239] ACPI: Fan [C1EE] (off)
[   23.408343] ACPI: Fan [C1EF] (off)
[   23.408447] ACPI: Fan [C1F0] (off)
[   23.412551] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   23.412558] ACPI: Processor [C000] (supports 8 throttling states)
[   23.423211] ACPI: Thermal Zone [TZ1] (53 C)
[   23.424126] ACPI: Thermal Zone [C1EA] (45 C)
[   23.961032] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[   23.961043] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   23.961060] **** SET: Misaligned resource pointer: cfc481c2 Type 07 Len 0
[   23.961479] ACPI: PCI Interrupt Link [C0C2] enabled at IRQ 10
[   23.961482] PCI: setting IRQ 10 as level-triggered
[   23.961486] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
[   23.961499] ICH3M: chipset revision 2
[   23.961501] ICH3M: not 100% native mode: will probe irqs later
[   23.961513]     ide0: BM-DMA at 0x4440-0x4447, BIOS settings: hda:DMA, hdb:pio
[   23.961530]     ide1: BM-DMA at 0x4448-0x444f, BIOS settings: hdc:DMA, hdd:pio
[   23.961542] Probing IDE interface ide0...
[   24.017292] hda: WDC WD800VE-22KWT0, ATA DISK drive
[   24.028259] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.029521] Probing IDE interface ide1...
[   24.076426] hdc: DW-224E, ATAPI CD/DVD-ROM drive
[   24.087473] ide1 at 0x170-0x177,0x376 on irq 15
[   24.094532] hda: max request size: 1024KiB
[   24.133211] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   24.133328] hda: cache flushes supported
[   24.133490]  hda: hda1 hda2 < hda5 >
[   24.165105] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1658kB Cache, DMA
[   24.165114] Uniform CD-ROM driver Revision: 3.20
[   24.466359] usbcore: registered new driver usbfs
[   24.466383] usbcore: registered new driver hub
[   24.467197] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   24.467268] **** SET: Misaligned resource pointer: cfc8a502 Type 07 Len 0
[   24.467696] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[   24.467700] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[   24.467715] ohci_hcd 0000:02:0e.0: OHCI Host Controller
[   24.468038] ohci_hcd 0000:02:0e.0: new USB bus registered, assigned bus number 1
[   24.468048] ohci_hcd 0000:02:0e.0: irq 10, io mem 0x40180000
[   24.936376] hub 1-0:1.0: USB hub found
[   24.936389] hub 1-0:1.0: 3 ports detected
[   25.363991] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[   25.364011] ohci_hcd 0000:02:0e.1: OHCI Host Controller
[   25.364106] ohci_hcd 0000:02:0e.1: new USB bus registered, assigned bus number 2
[   25.364115] ohci_hcd 0000:02:0e.1: irq 10, io mem 0x40200000
[   25.617162] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   25.833093] hub 2-0:1.0: USB hub found
[   25.833105] hub 2-0:1.0: 2 ports detected
[   26.261664] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[   26.261685] ehci_hcd 0000:02:0e.2: EHCI Host Controller
[   26.280514] ehci_hcd 0000:02:0e.2: new USB bus registered, assigned bus number 3
[   26.280525] ehci_hcd 0000:02:0e.2: irq 10, io mem 0x40300000
[   26.280536] ehci_hcd 0000:02:0e.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   26.280621] hub 3-0:1.0: USB hub found
[   26.280631] hub 3-0:1.0: 5 ports detected
[   26.368014] usbcore: registered new driver hiddev
[   26.544389] usb 1-2: USB disconnect, address 2
[   26.544396] usbcore: registered new driver usbhid
[   26.544400] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   26.599900] Attempting manual resume
[   26.642336] EXT3-fs: mounted filesystem with ordered data mode.
[   26.642526] kjournald starting.  Commit interval 5 seconds
[   26.800431] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   27.001827] input: FRONT ELECTRONIC CO.,LTD. FRONT USB & PS2 Dual KeyBoard as /class/input/input1
[   27.001840] input: USB HID v1.00 Keyboard [FRONT ELECTRONIC CO.,LTD. FRONT USB & PS2 Dual KeyBoard] on usb-0000:02:0e.0-2
[   35.844527] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.848160] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.885312] hw_random: RNG not detected
[   35.984865] ltmodem: module license 'Proprietary' taints kernel.
[   35.985580] Loading Lucent Modem Controller driver version 8.26-alk-8
[   35.986441] **** SET: Misaligned resource pointer: cd4b0902 Type 07 Len 0
[   35.986892] ACPI: PCI Interrupt Link [C0C1] enabled at IRQ 11
[   35.986896] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [C0C1] -> GSI 11 (level, low) -> IRQ 11
[   35.986908] Detected Parameters Irq=11 BaseAddress=0x2000 ComAddress=0x2440
[   35.986921] ttyLTM0 at I/O 0x2000 (irq = 11) is a Lucent/Agere Modem
[   36.215161] Linux agpgart interface v0.101 (c) Dave Jones
[   36.245087] agpgart: Detected an Intel i845 Chipset.
[   36.266136] agpgart: AGP aperture is 256M @ 0x60000000
[   36.408316] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x884793/0x0
[   36.408323] serio: Synaptics pass-through port at isa0060/serio4/input0
[   36.451365] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   36.591091] parport: PnPBIOS parport detected.
[   36.591121] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   36.624946] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   36.624960] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:00b7]
[   36.624974] Yenta: Enabling burst memory read transactions
[   36.624979] Yenta: Using CSCINT to route CSC interrupts to PCI
[   36.624981] Yenta: Routing CardBus interrupts to PCI
[   36.624986] Yenta TI: socket 0000:02:06.0, mfunc 0x01001002, devctl 0x64
[   36.711280] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0C1] -> GSI 11 (level, low) -> IRQ 11
[   36.711303] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   36.719778] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[   36.719782] e100: Copyright(c) 1999-2005 Intel Corporation
[   36.731007] ts: Compaq touchscreen protocol output
[   36.792344] Floppy drive(s): fd0 is 1.44M
[   36.806169] FDC 0 is a post-1991 82077
[   36.816826] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   36.816831] Socket status: 30000020
[   36.816834] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #06
[   36.816841] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   36.816845] cs: IO port probe 0x2000-0x2fff: clean.
[   36.817067] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[   36.817071] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   36.818156] Real Time Clock Driver v1.12
[   36.818770] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   36.818785] Yenta: CardBus bridge found at 0000:02:06.1 [0e11:00b7]
[   36.818801] Yenta: Using CSCINT to route CSC interrupts to PCI
[   36.818803] Yenta: Routing CardBus interrupts to PCI
[   36.818808] Yenta TI: socket 0000:02:06.1, mfunc 0x01001002, devctl 0x64
[   36.906846] input: PC Speaker as /class/input/input3
[   36.973128] intel8x0_measure_ac97_clock: measured 54817 usecs
[   36.973134] intel8x0: clocking to 48000
[   37.013532] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   37.013538] Socket status: 30000006
[   37.013541] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   37.013549] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   37.013552] cs: IO port probe 0x2000-0x2fff: clean.
[   37.013768] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x403fffff
[   37.013771] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   37.029365] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0C4] -> GSI 10 (level, low) -> IRQ 10
[   37.110520] e100: eth0: e100_probe: addr 0x40100000, irq 10, MAC addr 00:08:02:95:EC:F4
[   37.349777] pccard: CardBus card inserted into slot 0
[   37.892458] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   37.893458] cs: IO port probe 0x3e0-0x4ff: clean.
[   37.893865] cs: IO port probe 0x820-0x8ff: clean.
[   37.894222] cs: IO port probe 0xc00-0xcf7: clean.
[   37.894689] cs: IO port probe 0xa00-0xaff: clean.
[   37.895945] cs: IO port probe 0x100-0x3af: excluding 0x100-0x107
[   37.896934] cs: IO port probe 0x3e0-0x4ff: clean.
[   37.897341] cs: IO port probe 0x820-0x8ff: clean.
[   37.897700] cs: IO port probe 0xc00-0xcf7: clean.
[   37.898190] cs: IO port probe 0xa00-0xaff: clean.
[   38.086486] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   38.989880] NET: Registered protocol family 17
[   40.162167] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[   40.225260] ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
[   40.225493] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   40.225507] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[   40.225545] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   40.230800] ndiswrapper: using irq 11
[   40.363508] Unable to handle kernel NULL pointer dereference at virtual address 00000001
[   40.363514]  printing eip:
[   40.363516] d0ba4f58
[   40.363517] *pde = 00000000
[   40.363520] Oops: 0000 [#1]
[   40.363522] PREEMPT
[   40.363524] Modules linked in: ndiswrapper af_packet pcmcia pcspkr rtc floppy joydev tsdev e100 snd_intel8x0 snd_ac97_codec snd_ac97_bus mii snd_pcm_oss snd_mixer_oss yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport snd_pcm snd_timer intel_agp agpgart ltserial ltmodem shpchp pci_hotplug snd soundcore snd_page_alloc psmouse serio_raw evdev ext3 jbd ide_generic usbhid ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[   40.363556] CPU:    0
[   40.363557] EIP:    0060:[<d0ba4f58>]    Tainted: P      VLI
[   40.363559] EFLAGS: 00010202   (2.6.15-27-386)
[   40.363564] EIP is at 0xd0ba4f58
[   40.363567] eax: ca96e560   ebx: caf69c08   ecx: 00000002   edx: 00000000
[   40.363571] esi: cfddb000   edi: cfddb72c   ebp: caf69c10   esp: caf69b94
[   40.363573] ds: 007b   es: 007b   ss: 0068
[   40.363576] Process loadndisdriver (pid: 3244, threadinfo=caf68000 task=caf5e550)
[   40.363579] Stack: cf3d1668 cfddb000 00000001 00000000 caf68000 caf68000 000236b9 65d9a016
[   40.363586]        00000009 caf5e67c caf5e030 65d9a24a 00000009 caf68000 65d9a0bd 00000009
[   40.363593]        082f719a 00000000 000a0008 d0ba4c70 00120010 d0ba4c7c 00180016 d0ba4c58
[   40.363600] Call Trace:
[   40.363639]  [<d0b8c92e>] miniport_init+0x6e/0xf0 [ndiswrapper]
[   40.363685]  [<d0b8e317>] ndis_start_device+0x17/0x4c0 [ndiswrapper]
[   40.363709]  [<c01dd2b6>] vsnprintf+0x356/0x590
[   40.363723]  [<c011c5e0>] call_console_drivers+0x150/0x170
[   40.363745]  [<c011c8d3>] vprintk+0x1d3/0x340
[   40.363756]  [<c02740ca>] pci_read+0x2a/0x30
[   40.363772]  [<d0b86b05>] IofCompleteRequest+0xd5/0x1c0 [ndiswrapper]
[   40.363797]  [<d0b8b554>] pdoDispatchPnp+0x34/0x170 [ndiswrapper]
[   40.363821]  [<d0b8e260>] NdisDispatchPnp+0xb0/0x150 [ndiswrapper]
[   40.363844]  [<d0b86a14>] IofCallDriver+0x54/0x70 [ndiswrapper]
[   40.363865]  [<d0b8bc30>] pnp_start_device+0x60/0xf0 [ndiswrapper]
[   40.363886]  [<d0b8bfee>] wrap_pnp_start_device+0xfe/0x150 [ndiswrapper]
[   40.363907]  [<c01e6ffc>] __pci_device_probe+0x3c/0x60
[   40.363916]  [<c01e703f>] pci_device_probe+0x1f/0x40
[   40.363924]  [<c024457b>] driver_probe_device+0x3b/0xc0
[   40.363933]  [<c0244670>] __driver_attach+0x0/0x40
[   40.363938]  [<c02446ab>] __driver_attach+0x3b/0x40
[   40.363945]  [<c0243c58>] bus_for_each_dev+0x48/0x80
[   40.363957]  [<c02446c5>] driver_attach+0x15/0x20
[   40.363964]  [<c0244670>] __driver_attach+0x0/0x40
[   40.363969]  [<c02440f9>] bus_add_driver+0x69/0xc0
[   40.363977]  [<c01e728a>] __pci_register_driver+0x6a/0xa0
[   40.363983]  [<d0b7aff2>] register_devices+0x392/0x620 [ndiswrapper]
[   40.364009]  [<d0b7b360>] wrapper_ioctl+0xe0/0x100 [ndiswrapper]
[   40.364033]  [<c01736d0>] filldir64+0x0/0xe0
[   40.364039]  [<c0173847>] sys_getdents64+0x97/0xd6
[   40.364044]  [<c017807d>] dput+0x10d/0x2c0
[   40.364052]  [<c017807d>] dput+0x10d/0x2c0
[   40.364059]  [<c0172fa7>] do_ioctl+0x67/0x80
[   40.364069]  [<c0173141>] vfs_ioctl+0x51/0x1f0
[   40.364074]  [<c015f34b>] filp_close+0x3b/0x80
[   40.364083]  [<c017333d>] sys_ioctl+0x5d/0x90
[   40.364094]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[   40.364112] Code: 1c 07 00 00 00 80 be f7 06 00 00 00 74 60 6a 02 8d 45 cc 50 ff 75 fc 8b c6 8d 5d f8 e8 e6 ed ff ff 84 c0 74 42 8b 45 f8 8b 50 08 <80> 7a 01 00 8d be fc 06 00 00 8b cf 75 0e 0f b7 40 04 6a 20 50
[   40.364142]  <3>ndiswrapper (wrapper_init:173): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
[   40.364716] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[   40.364721]  printing eip:
[   40.364723] c02ec7e7
[   40.364725] *pde = 00000000
[   40.364727] Oops: 0002 [#2]
[   40.364729] PREEMPT
[   40.364731] Modules linked in: ndiswrapper af_packet pcmcia pcspkr rtc floppy joydev tsdev e100 snd_intel8x0 snd_ac97_codec snd_ac97_bus mii snd_pcm_oss snd_mixer_oss yenta_socket rsrc_nonstatic pcmcia_core parport_pc parport snd_pcm snd_timer intel_agp agpgart ltserial ltmodem shpchp pci_hotplug snd soundcore snd_page_alloc psmouse serio_raw evdev ext3 jbd ide_generic usbhid ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[   40.364761] CPU:    0
[   40.364762] EIP:    0060:[<c02ec7e7>]    Tainted: P      VLI
[   40.364763] EFLAGS: 00010046   (2.6.15-27-386)
[   40.364771] EIP is at wait_for_completion+0x67/0xe0
[   40.364774] eax: d0ba10f4   ebx: cfbb0000   ecx: 00000000   edx: cfbb1f1c
[   40.364778] esi: d0ba10f0   edi: cfbb1f98   ebp: cfbb1f2c   esp: cfbb1f10
[   40.364780] ds: 007b   es: 007b   ss: 0068
[   40.364783] Process modprobe (pid: 3239, threadinfo=cfbb0000 task=cea3e030)
[   40.364785] Stack: 00000001 cea3e030 c0118940 d0ba10f4 00000000 d0ba1088 d0b901c0 cfbb0000
[   40.364793]        c0244185 d0ba10e0 c033f3e0 d0ba1088 d0ba109c c03486f4 d0ba109c c0348708
[   40.364800]        d0ba1088 c0244b3b d0ba1088 d0ba1060 c01e72ce d0ba1088 cbf7cd40 d0b7b43c
[   40.364807] Call Trace:
[   40.364811]  [<c0118940>] default_wake_function+0x0/0x20
[   40.364821]  [<c0244185>] bus_remove_driver+0x35/0x70
[   40.364834]  [<c0244b3b>] driver_unregister+0xb/0x20
[   40.364841]  [<c01e72ce>] pci_unregister_driver+0xe/0x20
[   40.364847]  [<d0b7b43c>] loader_exit+0x4c/0x110 [ndiswrapper]
[   40.364867]  [<d0b8b396>] module_cleanup+0x6/0xa0 [ndiswrapper]
[   40.364886]  [<d09be057>] wrapper_init+0x57/0x181 [ndiswrapper]
[   40.364917]  [<c013820f>] sys_init_module+0x9f/0x1d0
[   40.364925]  [<c0102feb>] sysenter_past_esp+0x54/0x79
[   40.364942] Code: 45 f4 00 00 00 00 8b 03 89 45 e8 c7 45 ec 40 89 11 c0 c7 45 e4 01 00 00 00 8d 46 04 8b 48 04 8d 55 f0 89 50 04 89 45 f0 89 4d f4 <89> 11 8d b4 26 00 00 00 00 8b 03 c7 00 02 00 00 00 fb ff 4b 14
[   40.364970]  <6>note: modprobe[3239] exited with preempt_count 1
[   40.411613] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[   40.566568] EXT3 FS on hda1, internal journal
[   40.742696] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   40.742702] md: bitmap version 4.39
[   41.207102] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   42.208126] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[   42.494555] input: TPPS/2 IBM TrackPoint as /class/input/input4
[   43.590298] ACPI: AC Adapter [C19A] (on-line)
[   43.683376] ACPI: Battery Slot [C198] (battery present)
[   43.683509] ACPI: Battery Slot [C199] (battery absent)
[   43.765049] ACPI: Power Button (FF) [PWRF]
[   43.765103] ACPI: Sleep Button (CM) [C19B]
[   43.765111] ACPI: Lid Switch [C19C]
[   43.868540] ibm_acpi: ec object not found
[   43.896750] pcc_acpi: loading...
[   43.995900] ACPI: Video Device [C0CE] (multi-head: yes  rom: no  post: no)
[   48.179783] [drm] Initialized drm 1.0.1 20051102
[   48.218669] **** SET: Misaligned resource pointer: ca0f0dc2 Type 07 Len 0
[   48.220206] ACPI: PCI Interrupt Link [C0C0] enabled at IRQ 11
[   48.220293] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C0] -> GSI 11 (level, low) -> IRQ 11
[   48.220935] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[   49.199929] lp0: using parport0 (interrupt-driven).
[   49.203701] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   49.203721] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   49.203733] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   49.223164] ppdev: user-space parallel port driver
[   49.512186] [drm] Setting GART location based on new memory map
[   49.512375] [drm] writeback test succeeded in 2 usecs
[   49.803491] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   49.803726] apm: overridden by ACPI.
[   51.535252] NET: Registered protocol family 10
[   51.535395] lo: Disabled Privacy Extensions
[   51.535564] IPv6 over IPv4 tunneling driver
[   55.978194] Bluetooth: Core ver 2.8
[   55.978202] NET: Registered protocol family 31
[   55.978204] Bluetooth: HCI device and connection manager initialized
[   55.978216] Bluetooth: HCI socket layer initialized
[   55.990808] Bluetooth: L2CAP ver 2.8
[   55.990815] Bluetooth: L2CAP socket layer initialized
[   56.003829] Bluetooth: RFCOMM socket layer initialized
[   56.003848] Bluetooth: RFCOMM TTY layer initialized
[   56.003850] Bluetooth: RFCOMM ver 1.7
[   98.337613] eth0: no IPv6 routers present
[  107.712287] ISO 9660 Extensions: Microsoft Joliet Level 3
[  107.932662] ISO 9660 Extensions: RRIP_1991A

```


bootmisc.sh is back to normal 



if anyone can help, please let me know! 

Peace,
Jake

---

### Post by TrueJk7 on 2006-10-22
OK. So I took out all my modifications (except for the black listing and the /etc/modules modifcation.) (completely) Removed all WIFI apps, and reinstalled ONLY Ndiswrapper 1.8-0ubuntu. Then I installed another dirver I found for it from belkin's website.

Identical issue ([http://www.experts-exchange.com/Networking/Linux_Networking/Q_22007109.html](http://www.experts-exchange.com/Networking/Linux_Networking/Q_22007109.html))

Now The thing is. It can find a wireless signal, configure it all. but no connection will stay, not even for a second. When all I used was network-admin to manage the connections. In the top pannel of gnome it showed my network connection and signal strength, all though nothing would resolve.

Then I tried installing wifi-radar. Now the utility in the gnome pannel says no wireless connecitons available. The network-admin shows the wifi networks in range. But still I can not connect. wifi-radar says "got IP address" but still no hostnames or IPs will resolve through firefox or terminal. 

So I am a little confused here. Anyone have an Idea whats going on. 

The power led on the card will not say lit either. It will stay lit when scanning and kwazi-say-lit every 5-7 seconds when I am just sitting there.

So I dont know. More fights with drivers? or do I have a fail somewhere else? any clue???


Edit: --- >
Drivers used
bcmwl5
bcmwl5a

If you go to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B) you can find the exact device/driver I am using. The B's restart numbering half way though so if you look for the second #4, that would be it. I tried downloading that file and running the unzipping tool in wine and that's where I got the "bcmwl5a" INF file along with it's SYS and CAT files. I guess the only other change I can do is put the SYS and CAT files in the /etc/ndiswrapper/bcmwl5a/ directory. :-? Hopefully that works but that's about it for right now. I'll try it when I get home.

Any other suggestions??? :-k

---

### Post by TrueJk7 on 2006-10-23
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Ok! I got mine working! Check out the help Doc on the Wiki. I didnt know the wiki was that detailed! 

All I did after following the directions was go to /etc/init.d/bootmisc.sh and add the line "modprobe bcm43xx" WOO HOO! tmarios did some major help and dgrafix had a good suggestion of a card that is recognized automatically. NetGear WG511T ([http://ubuntuforums.org/showthread.php?t=187004&page=4](http://ubuntuforums.org/showthread.php?t=187004&page=4)) awesomeness. I am done! Now to go help everyone else I read. lol

---

