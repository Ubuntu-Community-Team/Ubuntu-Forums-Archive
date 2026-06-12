---
title: "wired network  problem in feisty"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by farside bunny on 2007-09-11
Hi every one!!!
just installed feisty and after a long line of troubles i finely got almost everything running except the wired connection ,for some reason its so so slow ,nothing runs except google and gmail! the weird thing is that the wireless connection works fine everything runs smooth but the wired connection just doesn't move!
i tried the blacklist  ipv6  thing i read about somewhere on the forum and it still doesn't help !!
can anyone please help me?!?!

thanks a lot !!!!!

---

### Post by noob12 on 2007-09-11
Posting the output of these commands will let people know what kind of card and driver you are using, and the state of your connection.  Grab the output of these after a boot when you are connected wired.
```

lspci -nn

sudo lshw -C network

sudo ethtool eth0

ifconfig -a

route -n

dmesg

```

---

### Post by farside bunny on 2007-09-15
Hi! thanks for the replay for help !!
here is the output of all of the commands :
```


bunny@bunny-laptop:~$ ispci -nn
bash: ispci: command not found
bunny@bunny-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X1400 [1002:7145]
02:00.0 Ethernet controller [0200]: Agere Systems ET-131x PCI-E Ethernet Controller [11c1:ed00] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
06:00.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
06:00.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
06:00.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
06:00.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
bunny@bunny-laptop:~$
bunny@bunny-laptop:~$ sudo ishw -C network
Password:
sudo: ishw: command not found
bunny@bunny-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: ET-131x PCI-E Ethernet Controller
       vendor: Agere Systems
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:14:7c:85
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=et131x ip=192.168.1.3 latency=0 multicast=yes
       resources: iomemory:d4000000-d41fffff irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:d8100000-d8100fff irq:19
for dmesg:
 (lpj=7315081)
[   11.370001] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.370003] CPU: L2 cache: 2048K
[   11.370006] CPU 1/1 -> Node 0
[   11.370007] CPU: Physical Processor ID: 0
[   11.370009] CPU: Processor Core ID: 1
[   11.370014] CPU1: Thermal monitoring handled by SMI
[   11.370334] Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[   11.373986] CPU 1: Syncing TSC to CPU 0.
[   11.374163] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 902 cycles)
[   11.374181] Brought up 2 CPUs
[   11.374233] time.c: Using 14.318180 MHz WALL HPET GTOD HPET timer.
[   11.374235] time.c : Detected 1828.750 MHz processor.
[   11.518459] migration_cost=24
[   11.518791] Time: 10:14:30  Date: 08/15/107
[   11.518826] NET: Registered protocol family 16
[   11.518906] ACPI: bus type pci registered
[   11.518913] PCI: Using configuration type 1
[   11.523917] ACPI: Interpreter enabled
[   11.523920] ACPI: Using IOAPIC for interrupt routing
[   11.526014] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.526020 ] PCI: Probing PCI hardware (bus 00)
[   11.527603] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   11.527608] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   11.527929] Boot video device is 0000:01: 00.0
[   11.528981] PCI: Transparent bridge - 0000:00:1e.0
[   11.529058] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#06) (try 'pci=assign-busses')
[   11.529060] Please report the result to linux-kernel to fix this permanently
[   11.529139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.532526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   11.533111] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   11.533482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   11.533795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   11.534760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   11.535365] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   11.535640] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   11.535909] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   11.536178] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   11.536449] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   11.536720] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   11.536989] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   11.537257] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   11.544182] ACPI: Power Resource [CTHT] (on)
[   11.544364] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.544377] pnp: PnP ACPI init
[   11.549847] pnp: PnP ACPI: found 13 devices
[   11.549898] PCI: Using ACPI for IRQ routing
[   11.549901 ] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.550074] NET: Registered protocol family 8
[   11.550076] NET: Registered protocol family 20
[   11.550090] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   11.550094] hpet0: 3 64-bit timers, 14318180 Hz
[   11.551109] PCI-GART: No AMD northbridge found.
[   11.551409] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   11.551412] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   11.551722] PCI: Bridge: 0000:00:01.0
[   11.551725]   IO window: 2000-2fff
[   11.551729]   MEM window: d8000000-d80fffff
[   11.551732]   PREFETCH window: c8000000-cfffffff
[   11.551736] PCI: Bridge: 0000:00: 1c.0
[   11.551739]   IO window: 3000-3fff
[   11.551745]   MEM window: d4000000-d5ffffff
[   11.551750]   PREFETCH window: d0000000-d1ffffff
[   11.551755] PCI: Bridge: 0000:00:1c.2
[   11.551758]   IO window: 4000-4fff
[   11.551764]   MEM window: d6000000-d7ffffff
[   11.551769]   PREFETCH window: d2000000-d3ffffff
[   11.551775] PCI: Bridge: 0000:00:1c.3
[   11.551776]   IO window: disabled.
[   11.551782]   MEM window: d8100000-d81fffff
[   11.551786]   PREFETCH window: disabled.
[   11.551799] PCI: Bus 7, cardbus bridge: 0000:06:00.0
[   11.551801]   IO window: 00005000-000050ff
[   11.551805]   IO window: 00005400-000054ff
[   11.551811 ]   PREFETCH window: 50000000-53ffffff
[   11.551816]   MEM window: 54000000-57ffffff
[   11.551821] PCI: Bridge: 0000:00:1e.0
[   11.551824]   IO window: 5000-5fff
[   11.551830]   MEM window: d8200000-d82fffff
[   11.551835]   PREFETCH window: 50000000-53ffffff
[   11.551851] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.551856] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   11.551879] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   11.551884] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   11.551907] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   11.551913] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   11.551935] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   11.551941] PCI: Setting latency timer of device 0000:00: 1c.3 to 64
[   11.551954] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.551971] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   11.552012] NET: Registered protocol family 2
[   11.589677] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   11.589830] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   11.590782] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   11.591675] TCP: Hash tables configured (established 131072 bind 65536)
[   11.591678] TCP reno registered
[   11.605756] checking if image is initramfs... it is
[   12.292938] Freeing initrd memory: 6828k freed
[   12.296834] Simple Boot Flag at 0x38 set to 0x1
[   12.297405] audit: initializing netlink socket (disabled)
[   12.297424] audit(1189851271.524:1): initialized
[   12.297616] VFS: Disk quotas dquot_6.5.1
[   12.297639] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   12.297694] io scheduler noop registered
[   12.297697] io scheduler anticipatory registered
[   12.297699] io scheduler deadline registered
[   12.297712] io scheduler cfq registered (default)
[   12.297998] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   12.298033] assign_interrupt_mode Found MSI capability
[   12.298037] Allocate Port Service[0000:00: 01.0:pcie00]
[   12.298126] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.298182] assign_interrupt_mode Found MSI capability
[   12.298184] Allocate Port Service[0000:00:1c.0:pcie00]
[   12.298222 ] Allocate Port Service[0000:00:1c.0:pcie02]
[   12.298341] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.298397] assign_interrupt_mode Found MSI capability
[   12.298399] Allocate Port Service[0000:00: 1c.2:pcie00]
[   12.298433] Allocate Port Service[0000:00:1c.2:pcie02]
[   12.298555] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   12.298611] assign_interrupt_mode Found MSI capability
[   12.298613 ] Allocate Port Service[0000:00:1c.3:pcie00]
[   12.298650] Allocate Port Service[0000:00:1c.3:pcie02]
[   12.321288] Real Time Clock Driver v1.12ac
[   12.321349] Linux agpgart interface v0.102 (c) Dave Jones
[   12.321352] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.321503] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.322077] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.322280] mice: PS/2 mouse device common for all mice
[   12.322872] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.323018] input: Macintosh mouse button emulation as /class/input/input0
[   12.323057] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.323061] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.323314] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.326203] i8042.c: Detected active multiplexing controller, rev 1.1.
[   12.329029] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.329033] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   12.329035] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   12.329038] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   12.329041] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   12.329219] TCP cubic registered
[   12.329230] NET: Registered protocol family 1
[   12.329353] ACPI: (supports S0 S3 S4 S5)
[   12.329398]   Magic number: 7:372:224
[   12.329428]   hash matches device ttyu8
[   12.329438]   hash matches device ttyrb
[   12.329512] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.329582] Freeing unused kernel memory: 304k freed
[   12.338984] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.488410] Capability LSM initialized
[   13.518013] ACPI: Transitioning device [FAN0] to D3
[   13.518017] ACPI: Transitioning device [FAN0] to D3
[   13.518020] ACPI: Fan [FAN0] (off)
[   13.521177] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[   13.521474 ] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[   13.522796] Monitor-Mwait will be used to enter C-1 state
[   13.522798] Monitor-Mwait will be used to enter C-2 state
[   13.522801] Monitor-Mwait will be used to enter C-3 state
[   13.522806] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   13.522811] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.523341] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   13.523560] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[   13.524898] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   13.524903] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.525997] ACPI: Thermal Zone [TZ0] (64 C)
[   13.527209] ACPI: Thermal Zone [TZ1] (47 C)
[   13.528889] ACPI: Thermal Zone [TZ2] (40 C)
[   13.886037] usbcore: registered new interface driver usbfs
[   13.886060] usbcore: registered new interface driver hub
[   13.886084] usbcore: registered new device driver usb
[   13.899155] USB Universal Host Controller Interface driver v3.0
[   13.899225] ACPI: PCI Interrupt 0000:00: 1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   13.899236] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.899241] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.899360] uhci_hcd 0000:00:1d.0 : new USB bus registered, assigned bus number 1
[   13.899394] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[   13.899511] usb usb1: configuration #1 chosen from 1 choice
[   13.899537] hub 1-0:1.0: USB hub found
[   13.899543] hub 1-0:1.0: 2 ports detected
[   13.924394] SCSI subsystem initialized
[   13.950167] libata version 2.20 loaded.
[   13.968822] ieee1394: Initialized config rom entry `ip1394'
[   13.978410 ] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   13.978423] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   13.978427] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   13.978451 ] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   13.978485] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[   13.978573] usb usb2: configuration #1 chosen from 1 choice
[   13.978599 ] hub 2-0:1.0: USB hub found
[   13.978603] hub 2-0:1.0: 2 ports detected
[   13.983143] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.983154] PCI: Setting latency timer of device 0000:00: 1d.2 to 64
[   13.983158] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.983177] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.983208] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   13.983293] usb usb3: configuration #1 chosen from 1 choice
[   13.983316] hub 3-0:1.0: USB hub found
[   13.983321] hub 3-0:1.0: 2 ports detected
[   13.994463] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 21 (level, low) -> IRQ 21
[   13.994472] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   13.994476] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   13.994496] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   13.994527] uhci_hcd 0000:00:1d.3: irq 21, io base 0x00001860
[   13.994610] usb usb4: configuration #1 chosen from 1 choice
[   13.994631] hub 4-0:1.0: USB hub found
[   13.994637] hub 4-0:1.0: 2 ports detected
[   14.008175] ahci 0000:00:1f.2: version 2.1
[   14.008204] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   14.038260] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   14.046580] usb 3-2: configuration #1 chosen from 1 choice
[   14.072042] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   14.082364] usb 4-1: configuration #1 chosen from 1 choice
[   14.083580 ] usbcore: registered new interface driver hiddev
[   14.099461] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input2
[   14.099481] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.2-2
[   14.099497] usbcore: registered new interface driver usbhid
[   14.099500] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.113211] PCI: Setting latency timer of device 0000:00: 1f.2 to 64
[   14.113220] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[   14.113224] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
[   14.113329] ata1: SATA max UDMA/133 cmd 0xffffc2000003a500 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   14.113392] ata2: SATA max UDMA/133 cmd 0xffffc2000003a580 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   14.113457] ata3: SATA max UDMA/133 cmd 0xffffc2000003a600 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   14.113522] ata4: SATA max UDMA/133 cmd 0xffffc2000003a680 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 19
[   14.113529] scsi0 : ahci
[   14.128255] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   14.128754] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[   14.128759] ata1.00: ATA-7: FUJITSU MHV2100BH, 00000028, max UDMA/100
[   14.128762] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   14.131243] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[   14.131246] ata1.00: configured for UDMA/100
[   14.131270] scsi1 : ahci
[   14.140454] ata2: SATA link down (SStatus 0 SControl 0)
[   14.140464] scsi2 : ahci
[   14.149647] ata3: SATA link down (SStatus 0 SControl 300)
[   14.149657] scsi3 : ahci
[   14.158846] ata4: SATA link down (SStatus 0 SControl 0)
[   14.158934] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2100B 0000 PQ: 0 ANSI: 5
[   14.159693] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   14.159711] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.159714] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.159743] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   14.159776] ehci_hcd 0000:00:1d.7: debug port 1
[   14.159783] PCI: cache line size of 32 is not supported by device 0000:00: 1d.7
[   14.159788] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd8504000
[   14.163674] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.163778] usb usb5: configuration #1 chosen from 1 choice
[   14.163805] hub 5-0:1.0: USB hub found
[   14.163813] hub 5-0:1.0: 8 ports detected
[   14.169702] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[   14.169713] sda: Write Protect is off
[   14.169715] sda: Mode Sense: 00 3a 00 00
[   14.169729] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.169775] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[   14.169784] sda: Write Protect is off
[   14.169786] sda: Mode Sense: 00 3a 00 00
[   14.169799] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.169804]  sda: sda1 sda2 <<6>usb 4-1: USB disconnect, address 2
[   14.266835] ACPI: PCI Interrupt 0000:06:00.1[A] -> GSI 16 (level, low) -> IRQ 16
[   14.271494]  sda5 sda6 > sda3
[   14.292809] sd 0:0:0:0: Attached scsi disk sda
[   14.317085] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d8205000-d82057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   14.317219] ata_piix 0000:00:1f.1: version 2.10ac1
[   14.317240] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   14.317261] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   14.317292] ata5: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000011880 irq 14
[   14.317329] ata6: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000011888 irq 15
[   14.317353] scsi4 : ata_piix
[   14.317778] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.623331] ata5.00: ATAPI, max UDMA/33
[   14.638520] Attempting manual resume
[   14.638523] swsusp: Resume From Partition 8:6
[   14.638525] PM: Checking swsusp image.
[   14.638727] PM: Resume from disk failed.
[   14.663774] kjournald starting.  Commit interval 5 seconds
[   14.663784] EXT3-fs: mounted filesystem with ordered data mode.
[   14.735532] usb 3-2: USB disconnect, address 2
[   14.783640] ata5.00: configured for UDMA/33
[   14.783652] scsi5 : ata_piix
[   14.783723] ata6: port disabled. ignoring.
[   14.787593] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082N HH02 PQ: 0 ANSI: 5
[   14.787642] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   14.974956] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   15.147808] usb 3-2: configuration #1 chosen from 1 choice
[   15.199813 ] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /class/input/input3
[   15.199834] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.2-2
[   15.421013] usb 4-1: new full speed USB device using uhci_hcd and address 3
[   15.587476] usb 4-1: configuration #1 chosen from 1 choice
[   27.739121] agpgart: Detected an Intel 945GM Chipset.
[   27.797653] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.820542] agpgart: AGP aperture is 256M @ 0x0
[   27.820572] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.846752] intel_rng: FWH not detected
[   27.861994] ACPI: PCI Interrupt 0000:06:00.2[A] -> GSI 16 (level, low) -> IRQ 16
[   27.895401] tifm_core: MMC/SD card detected in socket 0:1
[   27.939404] Yenta: CardBus bridge found at 0000:06:00.0 [1854:005f]
[   27.939427] Yenta: Using INTVAL to route CSC interrupts to PCI
[   27.939429] Yenta: Routing CardBus interrupts to PCI
[   27.939435] Yenta TI: socket 0000:06:00.0, mfunc 0x01001002, devctl 0x64
[   28.035137] sdhci: Secure Digital Host Controller Interface driver
[   28.035140] sdhci: Copyright(c) Pierre Ossman
[   28.084512 ] parport: PnPBIOS parport detected.
[   28.084593] parport0: PC-style at 0x378 (0x778), irq 5, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   28.097099] iTCO_vendor_support: vendor-support=0
[   28.108030] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   28.160019] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   28.160026] Uniform CD-ROM driver Revision: 3.20
[   28.160107] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   28.171684] Yenta: ISA IRQ mask 0x0cd8, PCI irq 16
[   28.171687] Socket status: 30000006
[   28.171690] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   28.171696] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   28.171698] pcmcia: parent PCI bridge Memory window: 0xd8200000 - 0xd82fffff
[   28.171701] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   28.179368] sdhci: SDHCI controller found at 0000:06: 00.3 [104c:803c] (rev 0)
[   28.179391] ACPI: PCI Interrupt 0000:06:00.3[A] -> GSI 16 (level, low) -> IRQ 16
[   28.179469] mmc1: SDHCI at 0xd8205800 irq 16 PIO
[   28.296856] et131x: module license 'BSD' taints kernel.
[   28.297577] 10/100/1000 Base-T Ethernet Driver for the ET1310, v1.2.3 01/31/2006 15:40:00 by Agere Systems, http://www.agere.com
[   28.297651] ACPI: PCI Interrupt 0000:02:00.0 [A] -> GSI 16 (level, low) -> IRQ 16
[   28.297664] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   28.310018] ieee80211_crypt: registered algorithm 'NULL'
[   28.311818] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.311822] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.435078] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   28.435082] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   28.435523] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   28.435539] PCI: Setting latency timer of device 0000:05: 00.0 to 64
[   28.439316] ipw3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   28.478323] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x200000
[   28.524745] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   28.529023] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   28.529058] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.668136] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   28.668163] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.801034] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   29.147052] fuse init (API version 7.8)
[   29.164714 ] lp0: using parport0 (interrupt-driven).
[   29.231390] Adding 634528k swap on /dev/disk/by-uuid/f1eabacb-b955-4859-a8ca-ee9cbba66660.  Priority:-1 extents:1 across:634528k
[   29.360611] EXT3 FS on sda3, internal journal
[   29.394530] NET: Registered protocol family 17
[   29.993016] ipw3945: Radio Frequency Kill Switch is On:
[   29.993018] Kill switch must be turned off for wireless networking to work.
[   32.750112] No dock devices found.
[   32.771079] ACPI: Video Device [EGFX] (multi-head: yes  rom: no  post: no)
[   32.842115] ibm_acpi: ec object not found
[   32.867883] input: Power Button (FF) as /class/input/input5
[   32.868035] ACPI: Power Button (FF) [PWRF]
[   32.868280] input: Lid Switch as /class/input/input6
[   32.868300] ACPI: Lid Switch [LID0]
[   32.868331] input: Power Button (CM) as /class/input/input7
[   32.868353] ACPI: Power Button (CM) [PWRB]
[   32.868383] input: Sleep Button (CM) as /class/input/input8
[   32.868398] ACPI: Sleep Button (CM) [SLPB]
[   32.920542] ACPI: AC Adapter [AC] (on-line)
[   32.946706] ACPI: Battery Slot [CMB0] (battery present)
[   32.956883] Using specific hotkey driver
[   32.965879] wmi_add device=ffff81003d000800
[   32.965882] calling WQBA
[   32.965894] wmi_add device=ffff81003d000000
[   32.965895] calling WQBA
[   32.977943 ] pcc_acpi: loading...
[   36.090613] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[   38.327014] ppdev: user-space parallel port driver
[   39.691458] Bluetooth: Core ver 2.11
[   39.691622] NET: Registered protocol family 31
[   39.691624] Bluetooth: HCI device and connection manager initialized
[   39.691646] Bluetooth: HCI socket layer initialized
[   39.725328] Bluetooth: L2CAP ver 2.8
[   39.725351] Bluetooth: L2CAP socket layer initialized
[   39.811226] Bluetooth: RFCOMM socket layer initialized
[   39.811290] Bluetooth: RFCOMM TTY layer initialized
[   39.811311] Bluetooth: RFCOMM ver 1.8
[  175.554475] NTFS driver 2.1.28 [Flags: R/O MODULE].
[  175.554893] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  175.662166] NTFS volume version 3.1.
[  231.149557] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  231.149563] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  231.149584] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  231.313808] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.313818]     Additional sense: Medium not present
[  231.313878] end_request: I/O error, dev sr0, sector 0
[  231.313883] Buffer I/O error on device sr0, logical block 0
[  231.313909] Buffer I/O error on device sr0, logical block 1
[  231.313915] Buffer I/O error on device sr0, logical block 2
[  231.313940] Buffer I/O error on device sr0, logical block 3
[  231.313945] Buffer I/O error on device sr0, logical block 4
[  231.313949] Buffer I/O error on device sr0, logical block 5
[  231.313973] Buffer I/O error on device sr0, logical block 6
[  231.313978] Buffer I/O error on device sr0, logical block 7
[  231.316457] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.316482]     Additional sense: Medium not present
[  231.316490] end_request: I/O error, dev sr0, sector 0
[  231.316513] Buffer I/O error on device sr0, logical block 0
[  231.318922] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.318929]     Additional sense: Medium not present
[  231.318955] end_request: I/O error, dev sr0, sector 4
[  231.318959] Buffer I/O error on device sr0, logical block 1
[  231.321950] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.321974]     Additional sense: Medium not present
[  231.321982] end_request: I/O error, dev sr0, sector 0
[  231.323925] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.323950 ]     Additional sense: Medium not present
[  231.323957] end_request: I/O error, dev sr0, sector 4
[  231.326388] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.326412]     Additional sense: Medium not present
[  231.326420] end_request: I/O error, dev sr0, sector 0
[  231.328321] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.328346]     Additional sense: Medium not present
[  231.328353 ] end_request: I/O error, dev sr0, sector 4
[  231.331065] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.331090]     Additional sense: Medium not present
[  231.331097] end_request: I/O error, dev sr0, sector 0
[  231.333503] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.333533]     Additional sense: Medium not present
[  231.333540] end_request: I/O error, dev sr0, sector 4
[  231.337460 ] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.337485]     Additional sense: Medium not present
[  231.337492] end_request: I/O error, dev sr0, sector 0
[  231.339407] sr 4:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[  231.339431]     Additional sense: Medium not present
[  231.339438] end_request: I/O error, dev sr0, sector 4
[  231.412797] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8b01
[  231.412863] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[  231.412891] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
[  231.412926] et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946

bunny@bunny-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

btw is there any chance you can explain a bit on each command and what it did ? since i am really really  new to this thing 
again thanks for the help !

---

### Post by farside bunny on 2007-09-16
bump !
can any one please help me?!

---

### Post by farside bunny on 2007-10-16
bump any one?!

---

### Post by Faelblood on 2007-10-17
I have the exact same problem. I'm on my mac laptop with the exact same wire right now and it works just fine, but when I plug into my desktop SHAZAM, only google and gmail work.

---

### Post by gareth279 on 2007-10-19
I have the same problem... see thread  [http://ubuntuforums.org/showthread.php?p=3571627](http://ubuntuforums.org/showthread.php?p=3571627) 

Hopefully someone has an suggested fix?

---

### Post by farside bunny on 2007-11-01
bump!!
anyone please i really need help here :confused::confused::confused:

---

### Post by Fire_Chief on 2007-11-01
Hi Farside Bunny, 

Welcome to Ubuntu! Hopefully we can get you straightened out with this issue...

I noticed in your dmesg output these errors```
t131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8b01
et131x.ko:WARNING:et131x_ioctl Unhandled IOCTL Code: 0x8946
```
This may give a hint at part of the problem (this file is related to your network card driver).

The errors are also asked about at this thread [http://ubuntuforums.org/showthread.php?t=580822]("http://ubuntuforums.org/showthread.php?t=580822")

While there is a sourceforge project working on this driver, the latest release is the same version as what you have installed. :( 

Do you have a 2nd PC on your LAN to test connectivity and speed with? If so, how well do file transfers behave between the two systems? What happens if you use strictly IPs to connect instead of NetBIOS or DNS names? What is in your resolv.conf file? ( sudo gedit /etc/resolv.conf )

---

### Post by froy02 on 2007-11-02
Can you just the results of:

sudo ethtool eth0

---

