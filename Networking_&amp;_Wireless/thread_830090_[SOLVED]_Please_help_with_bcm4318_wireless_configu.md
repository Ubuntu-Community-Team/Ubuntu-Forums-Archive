---
title: "[SOLVED] Please help with bcm4318 wireless configuration"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by mjitkop on 2008-06-15
Hello, dear community. :)

I have been trying for months to get my wireless connection working. I have read many guides and tried lots of things to get it to work to no avail. :(

I believe I am close to getting it to work but I don't know what to do anymore. I do not feel like reading through pages and pages of documents anymore.

Would anybody be kind enough to help me finish my configuration? I want it to work so badly so that I can definitely make it my primary OS. Right now I have a dual boot with XP and this is how I am able to post this message.

Here are the results of different commands I came across in different guides. Hopefully this will help you understand my current configuration. For your information, I am using WEP with my router and it doesn't matter to me if it works with the legacy driver or ndiswrapper. I just want it to work. ;)

1/ lspci with focus on "network"

```
02:08.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

2/ lshw

```
<prompt>:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: <serial number>
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: <serial number>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
<prompt>:~$ 
```

3/ dmesg

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff6f000 (usable)
[    0.000000]  BIOS-e820: 000000001ff6f000 - 000000001ff71000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff71000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 130927) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130927
[    0.000000]   HighMem    130927 ->   130927
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130927
[    0.000000] On node 0 totalpages: 130927
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125841 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FD540 checksum 0
[    0.000000] ACPI: RSDP 000FD540, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD554, 0034 (r1 DELL    8250           8 ASL        61)
[    0.000000] ACPI: FACP 000FD588, 0074 (r1 DELL    8250           8 ASL        61)
[    0.000000] ACPI: DSDT FFFE3C22, 2274 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FF6F000, 0040
[    0.000000] ACPI: SSDT FFFE5E96, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD5FC, 006C (r1 DELL    8250           8 ASL        61)
[    0.000000] ACPI: BOOT 000FD668, 0028 (r1 DELL    8250           8 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129905
[    0.000000] Kernel command line: root=UUID=4fdb3960-ac7f-4e36-ae66-fdd4e006f1fe ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2651.784 MHz processor.
[   22.091662] Console: colour VGA+ 80x25
[   22.091667] console [tty0] enabled
[   22.091980] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.092260] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.102137] Memory: 506788k/523708k available (2157k kernel code, 16300k reserved, 998k data, 364k init, 0k highmem)
[   22.102145] virtual kernel memory layout:
[   22.102146]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   22.102147]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.102149]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   22.102150]     lowmem  : 0xc0000000 - 0xdff6f000   ( 511 MB)
[   22.102151]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   22.102152]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   22.102153]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   22.102156] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.102191] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.182183] Calibrating delay using timer specific routine.. 5308.32 BogoMIPS (lpj=10616647)
[   22.182207] Security Framework initialized
[   22.182215] SELinux:  Disabled at boot.
[   22.182229] AppArmor: AppArmor initialized
[   22.182233] Failure registering capabilities with primary security module.
[   22.182242] Mount-cache hash table entries: 512
[   22.182375] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   22.182388] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   22.182391] CPU: L2 cache: 512K
[   22.182394] CPU: Hyper-Threading is disabled
[   22.182396] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   22.182407] Compat vDSO mapped to ffffe000.
[   22.182420] Checking 'hlt' instruction... OK.
[   22.198549] SMP alternatives: switching to UP code
[   22.200124] Freeing SMP alternatives: 11k freed
[   22.200255] Early unpacking initramfs... done
[   22.531369] ACPI: Core revision 20070126
[   22.543423] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.567340] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 07
[   22.567381] Total of 1 processors activated (5308.32 BogoMIPS).
[   22.567518] ENABLING IO-APIC IRQs
[   22.567693] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.714047] Brought up 1 CPUs
[   22.714068] CPU0 attaching sched-domain:
[   22.714071]  domain 0: span 01
[   22.714073]   groups: 01
[   22.714258] net_namespace: 64 bytes
[   22.714269] Booting paravirtualized kernel on bare hardware
[   22.714876] Time: 12:58:17  Date: 06/07/08
[   22.714903] NET: Registered protocol family 16
[   22.715135] EISA bus registered
[   22.715161] ACPI: bus type pci registered
[   22.741549] PCI: PCI BIOS revision 2.10 entry at 0xfbe8e, last bus=2
[   22.741552] PCI: Using configuration type 1
[   22.741554] Setting up standard PCI resources
[   22.743267] ACPI: EC: Look up EC in DSDT
[   22.774988] ACPI: Interpreter enabled
[   22.774992] ACPI: (supports S0 S1 S3 S4 S5)
[   22.775010] ACPI: Using IOAPIC for interrupt routing
[   22.806290] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.806500] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   22.806504] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   22.807408] PCI: Transparent bridge - 0000:00:1e.0
[   22.807433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.807766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   22.885758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   22.886090] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   22.886412] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   22.886734] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   22.887052] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.887379] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.887698] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.888021] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   22.888247] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.888283] pnp: PnP ACPI init
[   22.888294] ACPI: bus type pnp registered
[   22.909913] pnp: PnP ACPI: found 11 devices
[   22.909917] ACPI: ACPI bus type pnp unregistered
[   22.909921] PnPBIOS: Disabled by ACPI PNP
[   22.910186] PCI: Using ACPI for IRQ routing
[   22.910190] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.933928] NET: Registered protocol family 8
[   22.933930] NET: Registered protocol family 20
[   22.934006] AppArmor: AppArmor Filesystem Enabled
[   22.937917] Time: tsc clocksource has been installed.
[   22.945958] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   22.945962] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[   22.945965] system 00:00: iomem range 0x1000000-0x1ff6efff could not be reserved
[   22.945968] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   22.945971] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   22.945973] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   22.945976] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
[   22.945979] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[   22.945992] system 00:0a: ioport range 0x800-0x85f has been reserved
[   22.945994] system 00:0a: ioport range 0xc00-0xc7f has been reserved
[   22.945997] system 00:0a: ioport range 0x860-0x8ff could not be reserved
[   22.976458] PCI: Bridge: 0000:00:01.0
[   22.976461]   IO window: disabled.
[   22.976466]   MEM window: fc000000-fdffffff
[   22.976469]   PREFETCH window: f0000000-f7ffffff
[   22.976475] PCI: Bridge: 0000:00:1e.0
[   22.976478]   IO window: e000-efff
[   22.976483]   MEM window: fe100000-fe2fffff
[   22.976487]   PREFETCH window: disabled.
[   22.976503] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.976517] NET: Registered protocol family 2
[   23.013979] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.014221] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.014298] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   23.014374] TCP: Hash tables configured (established 16384 bind 16384)
[   23.014376] TCP reno registered
[   23.026031] checking if image is initramfs... it is
[   23.477726] Switched to high resolution mode on CPU 0
[   23.675021] Freeing initrd memory: 7690k freed
[   23.675186] Simple Boot Flag at 0x7a set to 0x1
[   23.675623] audit: initializing netlink socket (disabled)
[   23.675638] audit(1212843497.468:1): initialized
[   23.677843] VFS: Disk quotas dquot_6.5.1
[   23.677929] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.678085] io scheduler noop registered
[   23.678088] io scheduler anticipatory registered
[   23.678090] io scheduler deadline registered
[   23.678102] io scheduler cfq registered (default)
[   23.678119] Boot video device is 0000:01:00.0
[   23.678191] PCI: Firmware left 0000:02:0c.0 e100 interrupts enabled, disabling
[   23.678500] isapnp: Scanning for PnP cards...
[   24.032458] isapnp: No Plug & Play device found
[   24.064596] Real Time Clock Driver v1.12ac
[   24.064692] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.064812] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.065657] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.066515] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.066589] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   24.066704] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   24.069404] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.069410] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.073576] mice: PS/2 mouse device common for all mice
[   24.073708] EISA: Probing bus 0 at eisa.0
[   24.073744] EISA: Detected 0 cards.
[   24.073747] cpuidle: using governor ladder
[   24.073749] cpuidle: using governor menu
[   24.073845] NET: Registered protocol family 1
[   24.073876] Using IPI No-Shortcut mode
[   24.073907] registered taskstats version 1
[   24.074010]   Magic number: 12:239:986
[   24.074127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   24.074128] EDD information not available.
[   24.074488] Freeing unused kernel memory: 364k freed
[   24.113399] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   25.317336] fuse init (API version 7.9)
[   25.338977] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   25.892663] usbcore: registered new interface driver usbfs
[   25.892690] usbcore: registered new interface driver hub
[   25.907769] usbcore: registered new device driver usb
[   25.920598] USB Universal Host Controller Interface driver v3.0
[   25.920686] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 16
[   25.920701] uhci_hcd 0000:02:01.0: UHCI Host Controller
[   25.921019] uhci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 1
[   25.921049] uhci_hcd 0000:02:01.0: irq 16, io base 0x0000ece0
[   25.921195] usb usb1: configuration #1 chosen from 1 choice
[   25.921222] hub 1-0:1.0: USB hub found
[   25.921228] hub 1-0:1.0: 2 ports detected
[   25.992567] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   25.992572] e100: Copyright(c) 1999-2006 Intel Corporation
[   26.024812] ACPI: PCI Interrupt 0000:02:01.1[b] -> GSI 18 (level, low) -> IRQ 17
[   26.024827] uhci_hcd 0000:02:01.1: UHCI Host Controller
[   26.024852] uhci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 2
[   26.024880] uhci_hcd 0000:02:01.1: irq 17, io base 0x0000ecc0
[   26.025001] usb usb2: configuration #1 chosen from 1 choice
[   26.025030] hub 2-0:1.0: USB hub found
[   26.025037] hub 2-0:1.0: 2 ports detected
[   26.028783] SCSI subsystem initialized
[   26.071062] libata version 3.00 loaded.
[   26.128595] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 17
[   26.128609] uhci_hcd 0000:02:02.0: UHCI Host Controller
[   26.128635] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 3
[   26.128660] uhci_hcd 0000:02:02.0: irq 17, io base 0x0000eca0
[   26.128775] usb usb3: configuration #1 chosen from 1 choice
[   26.128802] hub 3-0:1.0: USB hub found
[   26.128808] hub 3-0:1.0: 2 ports detected
[   26.232535] ACPI: PCI Interrupt 0000:02:02.1[b] -> GSI 17 (level, low) -> IRQ 18
[   26.232549] uhci_hcd 0000:02:02.1: UHCI Host Controller
[   26.232583] uhci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 4
[   26.232610] uhci_hcd 0000:02:02.1: irq 18, io base 0x0000ec80
[   26.232742] usb usb4: configuration #1 chosen from 1 choice
[   26.232771] hub 4-0:1.0: USB hub found
[   26.232778] hub 4-0:1.0: 2 ports detected
[   26.336678] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 16 (level, low) -> IRQ 19
[   26.336695] ehci_hcd 0000:02:01.2: EHCI Host Controller
[   26.336725] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 5
[   26.336770] ehci_hcd 0000:02:01.2: irq 19, io mem 0xfe1ffc00
[   26.348364] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   26.348494] usb usb5: configuration #1 chosen from 1 choice
[   26.348523] hub 5-0:1.0: USB hub found
[   26.348531] hub 5-0:1.0: 4 ports detected
[   26.452452] ACPI: PCI Interrupt 0000:02:02.2[C] -> GSI 19 (level, low) -> IRQ 16
[   26.452470] ehci_hcd 0000:02:02.2: EHCI Host Controller
[   26.452496] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 6
[   26.452538] ehci_hcd 0000:02:02.2: irq 16, io mem 0xfe1ff800
[   26.464506] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   26.464637] usb usb6: configuration #1 chosen from 1 choice
[   26.464665] hub 6-0:1.0: USB hub found
[   26.464672] hub 6-0:1.0: 4 ports detected
[   26.568484] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 18
[   26.628290] ssb: Sonics Silicon Backplane found on PCI device 0000:02:08.0
[   26.628433] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 18 (level, low) -> IRQ 17
[   26.728631] e100: eth0: e100_probe: addr 0xfe1fe000, irq 17, MAC addr <MAC address>
[   26.732622] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   26.737347] ata_piix 0000:00:1f.1: version 2.12
[   26.737414] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   26.738589] scsi0 : ata_piix
[   26.739443] scsi1 : ata_piix
[   26.739493] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   26.739496] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.132512] ata1.00: ATA-6: ST3120023A, 3.33, max UDMA/100
[   27.132517] ata1.00: 234441648 sectors, multi 8: LBA 
[   27.133297] ata1.01: ATA-4: WDC WD205BA, 16.13M16, max UDMA/66
[   27.133300] ata1.01: 40088160 sectors, multi 8: LBA 
[   27.148401] ata1.00: configured for UDMA/100
[   27.164925] ata1.01: configured for UDMA/66
[   27.648067] ata2.00: ATAPI: _NEC DVD+/-RW ND-3530A, 104C, max UDMA/33
[   27.648095] ata2.01: ATAPI: LG CD-RW CED-8083B, 1.08, max MWDMA2
[   27.819925] ata2.00: configured for UDMA/33
[   27.991846] ata2.01: configured for MWDMA2
[   27.991981] scsi 0:0:0:0: Direct-Access     ATA      ST3120023A       3.33 PQ: 0 ANSI: 5
[   27.992418] scsi 0:0:1:0: Direct-Access     ATA      WDC WD205BA      16.1 PQ: 0 ANSI: 5
[   27.993525] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-3530A 104C PQ: 0 ANSI: 5
[   27.994082] scsi 1:0:1:0: CD-ROM            LG       CD-RW CED-8083B  1.08 PQ: 0 ANSI: 5
[   28.004124] Driver 'sd' needs updating - please use bus_type methods
[   28.004218] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   28.004233] sd 0:0:0:0: [sda] Write Protect is off
[   28.004236] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.004259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.004310] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   28.004323] sd 0:0:0:0: [sda] Write Protect is off
[   28.004326] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.004346] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.004350]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.023048]  sda1 sda2
[   28.023139] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.023849] sd 0:0:1:0: [sdb] 40088160 512-byte hardware sectors (20525 MB)
[   28.023864] sd 0:0:1:0: [sdb] Write Protect is off
[   28.023867] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.023890] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.023944] sd 0:0:1:0: [sdb] 40088160 512-byte hardware sectors (20525 MB)
[   28.023957] sd 0:0:1:0: [sdb] Write Protect is off
[   28.023959] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.023981] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.023984]  sdb: sdb1 sdb2 sdb3
[   28.064907] sd 0:0:1:0: [sdb] Attached SCSI disk
[   28.075188] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   28.075213] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   28.075232] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   28.075251] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   28.077625] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   28.077631] Uniform CD-ROM driver Revision: 3.20
[   28.077694] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   28.082036] sr1: scsi3-mmc drive: 24x/32x writer cd/rw xa/form2 cdda tray
[   28.082100] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   28.592433] Attempting manual resume
[   28.592438] swsusp: Resume From Partition 8:19
[   28.592440] PM: Checking swsusp image.
[   28.592653] PM: Resume from disk failed.
[   28.638674] kjournald starting.  Commit interval 5 seconds
[   28.638690] EXT3-fs: mounted filesystem with ordered data mode.
[   37.099105] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.167427] Linux agpgart interface v0.102
[   37.219409] agpgart: Detected an Intel i850 Chipset.
[   37.226158] agpgart: AGP aperture is 128M @ 0xe8000000
[   37.267463] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.316607] iTCO_vendor_support: vendor-support=0
[   37.372037] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   37.372179] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   37.372188] iTCO_wdt: No card detected
[   37.515295] Intel 82802 RNG detected
[   37.683337] input: Power Button (FF) as /devices/virtual/input/input2
[   37.698745] ACPI: Power Button (FF) [PWRF]
[   37.698875] input: Power Button (CM) as /devices/virtual/input/input3
[   37.711151] ACPI: Power Button (CM) [VBTN]
[   39.332729] gameport: EMU10K1 is pci0000:02:09.1/gameport0, io 0xec70, speed 1084kHz
[   39.686647] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   40.137800] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   40.439832] parport_pc 00:09: reported by Plug and Play ACPI
[   40.439884] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   40.549783] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   40.624619] b43-phy0: Broadcom 4318 WLAN found
[   40.692364] phy0: Selected rate control algorithm 'simple'
[   40.802580] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 18 (level, low) -> IRQ 17
[   40.802605] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/emu10k1x.c:949: Model 1003 Rev 00000000 Serial 10031102
[   42.190470] input: b43-phy0 as /devices/virtual/input/input6
[   43.312912] Registered led device: b43-phy0:tx
[   43.312936] Registered led device: b43-phy0:rx
[   43.312958] Registered led device: b43-phy0:radio
[   43.376577] mac80211-phy0: failed to set key (0, ff:ff:ff:ff:ff:ff) to hardware (-22)
[   43.393628] lp0: using parport0 (interrupt-driven).
[   43.444301] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   43.491135] usbcore: registered new interface driver ndiswrapper
[   43.597886] Adding 795208k swap on /dev/sdb3.  Priority:-1 extents:1 across:795208k
[   44.176210] wlan0: Initial auth_alg=0
[   44.176216] wlan0: authenticate with AP 00:16:b6:31:19:8c
[   44.178982] wlan0: RX authentication from 00:16:b6:31:19:8c (alg=0 transaction=2 status=0)
[   44.178986] wlan0: authenticated
[   44.178989] wlan0: associate with AP 00:16:b6:31:19:8c
[   44.181282] wlan0: RX AssocResp from 00:16:b6:31:19:8c (capab=0x411 status=0 aid=2)
[   44.181285] wlan0: associated
[   44.700489] NET: Registered protocol family 17
[   86.905671] NET: Registered protocol family 10
[   86.905991] lo: Disabled Privacy Extensions
[   91.964089] EXT3 FS on sdb1, internal journal
[   92.679609] kjournald starting.  Commit interval 5 seconds
[   92.679815] EXT3 FS on sdb2, internal journal
[   92.679820] EXT3-fs: mounted filesystem with ordered data mode.
[   92.992155] ip_tables: (C) 2000-2006 Netfilter Core Team
[   93.315850] No dock devices found.
[   94.445525] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   94.445531] apm: overridden by ACPI.
[   94.514768] ppdev: user-space parallel port driver
[   94.581767] audit(1212857969.301:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5453 profile="/usr/sbin/cupsd" namespace="default"
[   95.515470] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   95.521801] Bluetooth: Core ver 2.11
[   95.522749] NET: Registered protocol family 31
[   95.522754] Bluetooth: HCI device and connection manager initialized
[   95.522758] Bluetooth: HCI socket layer initialized
[   95.580632] Bluetooth: L2CAP ver 2.9
[   95.580637] Bluetooth: L2CAP socket layer initialized
[   95.658853] Bluetooth: RFCOMM socket layer initialized
[   95.659511] Bluetooth: RFCOMM TTY layer initialized
[   95.659515] Bluetooth: RFCOMM ver 1.8
[   97.139875] wlan0: no IPv6 routers present
[  101.440509] WEP decrypt failed (ICV)
[  101.443664] WEP decrypt failed (ICV)
[  101.447395] WEP decrypt failed (ICV)
[  101.451010] WEP decrypt failed (ICV)
[  101.454277] WEP decrypt failed (ICV)
[  101.457762] WEP decrypt failed (ICV)
[  101.461504] WEP decrypt failed (ICV)
[  101.465645] WEP decrypt failed (ICV)
[  101.469341] WEP decrypt failed (ICV)
[  101.473087] WEP decrypt failed (ICV)
[  222.322016] printk: 1 messages suppressed.
[  222.322023] WEP decrypt failed (ICV)
[  222.325258] WEP decrypt failed (ICV)
[  222.328963] WEP decrypt failed (ICV)
[  222.332641] WEP decrypt failed (ICV)
[  222.335812] WEP decrypt failed (ICV)
[  222.339383] WEP decrypt failed (ICV)
[  222.343098] WEP decrypt failed (ICV)
[  222.346262] WEP decrypt failed (ICV)
[  222.349993] WEP decrypt failed (ICV)
[  222.353677] WEP decrypt failed (ICV)
[  343.305731] printk: 1 messages suppressed.
[  343.305737] WEP decrypt failed (ICV)
[  343.308908] WEP decrypt failed (ICV)
[  343.312578] WEP decrypt failed (ICV)
[  343.316255] WEP decrypt failed (ICV)
[  343.319445] WEP decrypt failed (ICV)
[  343.322906] WEP decrypt failed (ICV)
[  343.326684] WEP decrypt failed (ICV)
[  343.329858] WEP decrypt failed (ICV)
[  343.333570] WEP decrypt failed (ICV)
[  343.337282] WEP decrypt failed (ICV)
[  399.600404] printk: 1 messages suppressed.
[  399.600410] WEP decrypt failed (ICV)
[  464.289896] WEP decrypt failed (ICV)
[  464.293151] WEP decrypt failed (ICV)
[  464.296926] WEP decrypt failed (ICV)
[  464.300525] WEP decrypt failed (ICV)
[  464.303793] WEP decrypt failed (ICV)
[  464.307281] WEP decrypt failed (ICV)
[  464.311982] WEP decrypt failed (ICV)
[  464.315162] WEP decrypt failed (ICV)
[  464.318811] WEP decrypt failed (ICV)
[  464.322580] WEP decrypt failed (ICV)
[  585.272891] printk: 1 messages suppressed.
[  585.272898] WEP decrypt failed (ICV)
[  585.276151] WEP decrypt failed (ICV)
[  585.279810] WEP decrypt failed (ICV)
[  585.283399] WEP decrypt failed (ICV)
[  585.286553] WEP decrypt failed (ICV)
[  585.290140] WEP decrypt failed (ICV)
[  585.294849] WEP decrypt failed (ICV)
[  585.298048] WEP decrypt failed (ICV)
[  585.301733] WEP decrypt failed (ICV)
[  585.305446] WEP decrypt failed (ICV)
[  703.900097] printk: 1 messages suppressed.
[  703.900103] WEP decrypt failed (ICV)
[  706.256765] WEP decrypt failed (ICV)
[  706.260024] WEP decrypt failed (ICV)
[  706.263704] WEP decrypt failed (ICV)
[  706.267345] WEP decrypt failed (ICV)
[  706.270598] WEP decrypt failed (ICV)
[  706.274158] WEP decrypt failed (ICV)
[  706.277875] WEP decrypt failed (ICV)
[  706.281084] WEP decrypt failed (ICV)
[  706.284741] WEP decrypt failed (ICV)
[  739.726049] printk: 2 messages suppressed.
[  739.726057] WEP decrypt failed (ICV)
[  827.137636] WEP decrypt failed (ICV)
[  827.140897] WEP decrypt failed (ICV)
[  827.144548] WEP decrypt failed (ICV)
[  827.148229] WEP decrypt failed (ICV)
[  827.151498] WEP decrypt failed (ICV)
[  827.155056] WEP decrypt failed (ICV)
[  827.158794] WEP decrypt failed (ICV)
[  827.162027] WEP decrypt failed (ICV)
[  827.165775] WEP decrypt failed (ICV)
[  827.169486] WEP decrypt failed (ICV)
[  831.366876] usbcore: deregistering interface driver ndiswrapper
[  948.121104] printk: 1 messages suppressed.
[  948.121110] WEP decrypt failed (ICV)
[  948.124335] WEP decrypt failed (ICV)
[  948.128050] WEP decrypt failed (ICV)
[  948.131736] WEP decrypt failed (ICV)
[  948.134980] WEP decrypt failed (ICV)
[  948.138515] WEP decrypt failed (ICV)
[  948.142347] WEP decrypt failed (ICV)
[  948.145537] WEP decrypt failed (ICV)
[  948.149176] WEP decrypt failed (ICV)
[  948.152934] WEP decrypt failed (ICV)
[ 1054.465496] printk: 1 messages suppressed.
[ 1054.465503] WEP decrypt failed (ICV)
[ 1069.104606] WEP decrypt failed (ICV)
[ 1069.107752] WEP decrypt failed (ICV)
[ 1069.111453] WEP decrypt failed (ICV)
[ 1069.115039] WEP decrypt failed (ICV)
[ 1069.118265] WEP decrypt failed (ICV)
[ 1069.121819] WEP decrypt failed (ICV)
[ 1069.125590] WEP decrypt failed (ICV)
[ 1069.128726] WEP decrypt failed (ICV)
[ 1069.132470] WEP decrypt failed (ICV)
[ 1069.136222] WEP decrypt failed (ICV)
[ 1190.088006] printk: 1 messages suppressed.
[ 1190.088016] WEP decrypt failed (ICV)
[ 1190.091213] WEP decrypt failed (ICV)
[ 1190.094976] WEP decrypt failed (ICV)
[ 1190.098574] WEP decrypt failed (ICV)
[ 1190.101814] WEP decrypt failed (ICV)
[ 1190.105385] WEP decrypt failed (ICV)
[ 1190.110066] WEP decrypt failed (ICV)
[ 1190.113265] WEP decrypt failed (ICV)
[ 1190.116898] WEP decrypt failed (ICV)
[ 1190.120567] WEP decrypt failed (ICV)
[ 1299.197667] printk: 1 messages suppressed.
[ 1299.197674] WEP decrypt failed (ICV)
[ 1311.071611] WEP decrypt failed (ICV)
[ 1311.074853] WEP decrypt failed (ICV)
[ 1311.078604] WEP decrypt failed (ICV)
[ 1311.082263] WEP decrypt failed (ICV)
[ 1311.085518] WEP decrypt failed (ICV)
[ 1311.088979] WEP decrypt failed (ICV)
[ 1311.092757] WEP decrypt failed (ICV)
[ 1311.095974] WEP decrypt failed (ICV)
[ 1311.099695] WEP decrypt failed (ICV)
[ 1311.103462] WEP decrypt failed (ICV)
[ 1331.399510] UDF-fs: No VRS found
[ 1331.434919] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1331.470713] ISO 9660 Extensions: RRIP_1991A
[ 1431.952785] printk: 1 messages suppressed.
[ 1431.952791] WEP decrypt failed (ICV)
[ 1431.959994] WEP decrypt failed (ICV)
[ 1431.963660] WEP decrypt failed (ICV)
[ 1431.966878] WEP decrypt failed (ICV)
[ 1431.970456] WEP decrypt failed (ICV)
[ 1431.974207] WEP decrypt failed (ICV)
[ 1431.977434] WEP decrypt failed (ICV)
[ 1431.981173] WEP decrypt failed (ICV)
[ 1431.984939] WEP decrypt failed (ICV)
[ 1431.988547] WEP decrypt failed (ICV)
[ 1459.793514] WEP decrypt failed (ICV)
[ 1552.937437] WEP decrypt failed (ICV)
[ 1552.940630] WEP decrypt failed (ICV)
[ 1552.944348] WEP decrypt failed (ICV)
[ 1552.947955] WEP decrypt failed (ICV)
[ 1552.951226] WEP decrypt failed (ICV)
[ 1552.954698] WEP decrypt failed (ICV)
[ 1552.958476] WEP decrypt failed (ICV)
[ 1552.965652] WEP decrypt failed (ICV)
[ 1552.969395] WEP decrypt failed (ICV)
[ 1552.972983] WEP decrypt failed (ICV)
[ 1673.919283] WEP decrypt failed (ICV)
[ 1673.922524] WEP decrypt failed (ICV)
[ 1673.926283] WEP decrypt failed (ICV)
[ 1673.929907] WEP decrypt failed (ICV)
[ 1673.933055] WEP decrypt failed (ICV)
[ 1673.937560] WEP decrypt failed (ICV)
[ 1673.941376] WEP decrypt failed (ICV)
[ 1673.944601] WEP decrypt failed (ICV)
[ 1673.948279] WEP decrypt failed (ICV)
[ 1673.952061] WEP decrypt failed (ICV)
[ 1794.902712] printk: 1 messages suppressed.
[ 1794.902718] WEP decrypt failed (ICV)
[ 1794.905893] WEP decrypt failed (ICV)
[ 1794.909549] WEP decrypt failed (ICV)
[ 1794.913180] WEP decrypt failed (ICV)
[ 1794.916428] WEP decrypt failed (ICV)
[ 1794.919896] WEP decrypt failed (ICV)
[ 1794.923693] WEP decrypt failed (ICV)
[ 1794.927122] WEP decrypt failed (ICV)
[ 1794.930828] WEP decrypt failed (ICV)
[ 1794.934556] WEP decrypt failed (ICV)
[ 1915.886134] printk: 1 messages suppressed.
[ 1915.886140] WEP decrypt failed (ICV)
[ 1915.889336] WEP decrypt failed (ICV)
[ 1915.893046] WEP decrypt failed (ICV)
[ 1915.896713] WEP decrypt failed (ICV)
[ 1915.899922] WEP decrypt failed (ICV)
[ 1915.903542] WEP decrypt failed (ICV)
[ 1915.907267] WEP decrypt failed (ICV)
[ 1915.910530] WEP decrypt failed (ICV)
[ 1915.914179] WEP decrypt failed (ICV)
[ 1915.917873] WEP decrypt failed (ICV)
[ 1990.310235] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1990.321981] usbcore: registered new interface driver ndiswrapper
[ 2036.869490] printk: 1 messages suppressed.
[ 2036.869496] WEP decrypt failed (ICV)
[ 2036.872900] WEP decrypt failed (ICV)
[ 2036.876647] WEP decrypt failed (ICV)
[ 2036.880350] WEP decrypt failed (ICV)
[ 2036.883603] WEP decrypt failed (ICV)
[ 2036.887127] WEP decrypt failed (ICV)
[ 2036.890853] WEP decrypt failed (ICV)
[ 2036.894016] WEP decrypt failed (ICV)
[ 2036.897763] WEP decrypt failed (ICV)
[ 2036.901462] WEP decrypt failed (ICV)

```

Please let me know if I need to provide more information.

Thank you very much in advance. :)

---

### Post by rlzyoner on 2008-06-15
IF not already done, download ndiswrapper and from a terminal, run the command

ndiswrapper -i /mount/sda1/drivers/network/RFXXX/bcmwl5.inf

Where after the -i is the path to the BCM drivers on your windows partition.

The run,
ndiswrapper -m  (to load the driver)

Now in the file /etc/modules, enter "ndiswrapper" - without quotes and reboot.

Enable your wireless adaptor and hopefully you wil be good to go.

---

### Post by prshah on 2008-06-15
> **mjitkop said:**
> 
I believe I am close to getting it to work but I don't know what to do anymore. I do not feel like reading through pages and pages of documents anymore.



Why not try my (solved) step-by-step thread _(with expected outputs)_ ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260))? It has output examples so that you can follow along. If you run into any trouble, post back here with the step you are stuck at and error messages/output.

---

### Post by mjitkop on 2008-06-15
> **rlzyoner said:**
> IF not already done, download ndiswrapper and from a terminal, run the command

ndiswrapper -i /mount/sda1/drivers/network/RFXXX/bcmwl5.inf

Where after the -i is the path to the BCM drivers on your windows partition.

The run,
ndiswrapper -m  (to load the driver)

Now in the file /etc/modules, enter "ndiswrapper" - without quotes and reboot.

Enable your wireless adaptor and hopefully you wil be good to go.

Thanks for these suggestions, rlzyoner. I had already done all this and I still don't see any wireless networks in my neighborhood (including mine).

Now what do you mean by "Enable your wireless adaptor" exactly? I think it is already enabled but if it isn't, what do I click on or type in a terminal?

---

### Post by mjitkop on 2008-06-15
> **prshah said:**
> Why not try my (solved) step-by-step thread _(with expected outputs)_ ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260))? It has output examples so that you can follow along. If you run into any trouble, post back here with the step you are stuck at and error messages/output.

I looked at your thread, prshah, and *iwconfig* gives me this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"<my router's ESSID>"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address>   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-56 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I checked my router's configuration and the frequency of 2.432 GHz is correct. I noticed that the bit rate reported above is only 11 Mb/s instead of 54 but I'll be very happy if it works with only 11!

Then in step 11 I get this:

```
<prompt>:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/<my NIC's MAC address>
Sending on   LPF/wlan0/<my NIC's MAC address>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
[COLOR=Red]No DHCPOFFERS received.[/COLOR]
No working leases in persistent database - sleeping.
```

So for some reason my router did not assign an IP address to my NIC.

Any suggestions? :-k

---

### Post by prshah on 2008-06-15
> **mjitkop said:**
> 
```


wlan0     IEEE 802.11g  ESSID:"<my router's ESSID>"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC address>   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=55/100  Signal level=-56 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

 I noticed that the bit rate reported above is only 11 Mb/s instead of 54 but I'll be very happy if it works with only 11!

```
<prompt>:~$ sudo dhclient wlan0
[COLOR=Red]No DHCPOFFERS received.[/COLOR]
No working leases in persistent database - sleeping.
```




54Mbps works only for unsecured connections. For WEP secured connections, the speed drops.

btw, where/how did you enter your WEP password? 

Your router is not handing out DHCP addresses. My first suggestion would be to find out why and fix _that_. Shouldn't take more than a few minutes. 

Second suggestion: If you want to set up the IP manually, we can easily do that as well.

---

### Post by mjitkop on 2008-06-16
> **prshah said:**
> 54Mbps works only for unsecured connections. For WEP secured connections, the speed drops.

btw, where/how did you enter your WEP password? 

Your router is not handing out DHCP addresses. My first suggestion would be to find out why and fix _that_. Shouldn't take more than a few minutes. 

Second suggestion: If you want to set up the IP manually, we can easily do that as well.

I don't remember where I entered my password but I didn't do it yesterday. Even if I do not enter my password, shouldn't I be able to see a list of available wireless connections around me? That's the way it is in Windows. 

I use the same PC with Windows XP and I have no problem getting an IP from my router. I checked MAC filtering and my NIC's MAC is allowed (it wouldn't work with XP anyway if it was not in the allowed list). 

All the PCs, laptops and the Wii in my house add up to 8 devices connected to my router and they all work well but not this one. DHCP works fine and if I switch to static IPs, I think the Wii will not connect anymore because I think it only works with DHCP. My Hardy Heron must be able to use DHCP.

Another thing is that the network icon in the upper right corner of the screen shows that it is in manual mode when I move the mouse on it. I don't know how to go back to automatic.

Thank you for your help.

At this point, is there any more data I can provide to help debug this connection issue?

---

### Post by Ayuthia on 2008-06-16
I am not for sure which driver you have been using since your post has shown both.  Can you try the following:
```
sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe b43
sudo ifconfing wlan0 up
sudo iwconfig wlan0 <my router's ESSID>
sudo dhclient wlan0
```

If you want to try the ndiswrapper route:
```

sudo modprobe -r b43 ssb ndiswrapper bcm43xx
sudo depmod -ae
sudo modprobe ndiswrapper
sudo iwconfig wlan0 <my router's ESSID>
sudo dhclient wlan0
```

EDIT:
Please replace <my router's ESSID> with the real name.

---

### Post by prshah on 2008-06-16
> **mjitkop said:**
> I don't remember where I entered my password but I didn't do it yesterday.


Give the following commands```

sudo iwconfig wlan0 essid YOURID key YOURPASSWORD
sudo dhclient wlan0

```

Replace YOURID with your router's SSID and YOURPASSWORD with the WEP key (hex only)

As a matter of interest, what does ```

sudo iwlist wlan0 scan
```
show?

---

### Post by mjitkop on 2008-06-16
Thank you so much everybody! I am posting this message from my Hardy Heron account! :guitar:
I got it to work by following the instructions from Ayuthia and prshah:

```
gildas@GILDAS-UBUNTU:~$ sudo modprobe -r b43 ssb ndiswrapper bcm43xx
[sudo] password for gildas: 
gildas@GILDAS-UBUNTU:~$ sudo depmod -ae
gildas@GILDAS-UBUNTU:~$ sudo modprobe b43
gildas@GILDAS-UBUNTU:~$ sudo ifconfing wlan0 up
sudo: ifconfing: command not found
gildas@GILDAS-UBUNTU:~$ sudo ifconfig wlan0 up
gildas@GILDAS-UBUNTU:~$ sudo iwconfig wlan0 <my ESSID>
iwconfig: unknown command "<my ESSID>"
gildas@GILDAS-UBUNTU:~$ sudo iwconfig wlan0 essid <my ESSID> key <my key>
gildas@GILDAS-UBUNTU:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/<MAC address>
Sending on   LPF/wlan0/<MAC address>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPOFFER of 192.168.2.100 from 192.168.2.1
DHCPREQUEST of 192.168.2.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.100 from 192.168.2.1
egrep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.2.100 -- renewal in 41367 seconds.
gildas@GILDAS-UBUNTU:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: <a neighbor's MAC>
                    ESSID:"<a neighbor's ESSID>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: <a neighbor's MAC>
                    ESSID:"<a neighbor's ESSID>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <my MAC>
                    ESSID:"<my ESSID>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

gildas@GILDAS-UBUNTU:~$ 
```

Thank you both! :popcorn:
Thank you also to rlzyoner who was the first person to come to my rescue! \\:D/

---

### Post by mjitkop on 2008-06-17
I spoke too soon. Yes it does work but every time I restart the PC I have to type:

sudo iwconfig wlan0 essid <my ESSID> key <my key>
sudo dhclient wlan0

How do I make it automatic? 

The network icon in the upper right corner shows that I'm in a manual network configuration. It does not show my signal strength with vertical bars.

Once this works automatically my problem will be solved 100%. :)

---

### Post by prshah on 2008-06-17
> **mjitkop said:**
> Yes it does work but every time I restart the PC I have to type:

sudo iwconfig wlan0 essid <my ESSID> key <my key>
sudo dhclient wlan0

How do I make it automatic? 


You can add those two lines (but _without_ sudo) to the "/etc/rc.local" file. This is a quick-and-dirty method. Remember _NOT_ to disturb the _last_ line of rc.local ("exit 0").

Network Manager will show you to be in a "Manual Configuration" when you use these commands, and yes, it will not show signal strengths.

But this is not an ideal solution. Ideally, once the ndiswrapper module is loaded and wlan0 seen with iwconfig, you should be able to click on network manager and see your wireless networks. If they don't show up, wait a while (2~3 mins) and try again. If it still doesn't show up, click on network mananger, then choose the "Connect to other Wireless network" option. Give your wireless details. If it connects successfully, subsequently it will remember the connection and connect automatically.

My advice would be that you hold off on adding the lines to rc.local for now. Try for another 30 mins or so to get network manager working properly, as outlined above. One additional tip: Click network manager, choose "Manual Configuration" and ensure that "Roaming mode enabled" is showing for your "wireless connection"

If nothing else works, you can use the "rc.local" method.

---

### Post by mjitkop on 2008-06-18
> **prshah said:**
> You can add those two lines (but _without_ sudo) to the "/etc/rc.local" file. This is a quick-and-dirty method. Remember _NOT_ to disturb the _last_ line of rc.local ("exit 0").

Network Manager will show you to be in a "Manual Configuration" when you use these commands, and yes, it will not show signal strengths.

But this is not an ideal solution. Ideally, once the ndiswrapper module is loaded and wlan0 seen with iwconfig, you should be able to click on network manager and see your wireless networks. If they don't show up, wait a while (2~3 mins) and try again. If it still doesn't show up, click on network mananger, then choose the "Connect to other Wireless network" option. Give your wireless details. If it connects successfully, subsequently it will remember the connection and connect automatically.

My advice would be that you hold off on adding the lines to rc.local for now. Try for another 30 mins or so to get network manager working properly, as outlined above. One additional tip: Click network manager, choose "Manual Configuration" and ensure that "Roaming mode enabled" is showing for your "wireless connection"

If nothing else works, you can use the "rc.local" method.

Thank you for your suggestions. It seems to be working now. I have restarted several times since my last message and I seem to be connected instantly. I entered my information in the Network Manager but did not enable roaming because every time I did, my information was lost. It's been working in manual mode and that's fine with me.

I consider my problem 100% solved thanks to your help.

Thank you again, everybody!  This community :guitar:! :lolflag:

---

