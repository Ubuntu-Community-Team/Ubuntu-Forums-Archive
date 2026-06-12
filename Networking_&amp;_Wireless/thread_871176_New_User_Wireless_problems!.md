---
title: "New User Wireless problems!"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by james1306 on 2008-07-26
Hey guys,

Firstly, sorry if this has already been posted a thousand times!

I'm having massive problems connecting to the wireless network. Im using a broadcom 4318 adapter, and ubuntu on an Acer 4404 Tavelmate laptop. I've tried tonnes of things that have been posted on the web, and still can't seem to connect!

If anyone has any ideas, would be much appreciated!

---

### Post by steveneddy on 2008-07-26
I went to the search feature on these forums, simply typed in

[B]broadcom 4318
[/B]
and came up with this thread.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

The search function is at the top of all forum pages, on the uppermost gray bar, fourth selection from the left.

Hope that helps.

---

### Post by james1306 on 2008-07-26
Hey,

Cheers for the reply, but I'ver already tried that. I'm running the Hardy version and that box is ticked with a green tick. Just doesn't make any difference.

Could it be router issues? I've turned off wireless security for the momemnt and added an access list to it. That used to work when my laptop used to have windows fine. 

I'm using Linux due to my HDD corrupting, and decided on started afresh, rather than Windows constantly pissing me off; if that's much help?

---

### Post by superprash2003 on 2008-07-26
in your terminal type lshw -C network and post output here

---

### Post by james1306 on 2008-07-27
```
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 02
       serial: 00:16:ce:0c:77:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,02/11/2005, 3.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:f0:18:1c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

```
Cheers

---

### Post by Bison Ravi on 2008-07-27
I would also like to see the output of

ifconfig

iwconfig

dmesg

lspci

iwlist wlan0 scanning

---

### Post by james1306 on 2008-07-27
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:f0:18:1c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fef0:181c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506973 (1.4 MB)  TX bytes:190409 (185.9 KB)
          Interrupt:23 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76700 (74.9 KB)  TX bytes:76700 (74.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:0c:77:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:c0204000-c0206000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:ce:0c:77:7e  
          inet addr:169.254.6.41  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:c0204000-c0206000 

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

dmesg:
```
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 000000000009c000
[    0.000000] swsusp: Registered nosave memory region: 000000000009c000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 256893
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=aeecfb37-2dcb-4128-bd89-cb71a065f34f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   12.963025] time.c: Detected 1799.987 MHz processor.
[   12.964308] Console: colour VGA+ 80x25
[   12.964311] console [tty0] enabled
[   12.964330] Checking aperture...
[   12.964333] CPU 0: aperture @ 464000000 size 32 MB
[   12.964335] Aperture too small (32 MB)
[   12.976183] No AGP bridge found
[   12.991838] Memory: 1019876k/1047168k available (2489k kernel code, 26888k reserved, 1318k data, 320k init)
[   12.991890] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   13.068851] Calibrating delay using timer specific routine.. 3603.83 BogoMIPS (lpj=7207663)
[   13.068898] Security Framework initialized
[   13.068907] SELinux:  Disabled at boot.
[   13.068925] AppArmor: AppArmor initialized
[   13.068929] Failure registering capabilities with primary security module.
[   13.069037] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.070223] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   13.070802] Mount-cache hash table entries: 256
[   13.070983] Initializing cgroup subsys ns
[   13.070988] Initializing cgroup subsys cpuacct
[   13.071002] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   13.071004] CPU: L2 Cache: 1024K (64 bytes/line)
[   13.071007] CPU 0/0 -> Node 0
[   13.071034] SMP alternatives: switching to UP code
[   13.071651] Freeing SMP alternatives: 24k freed
[   13.072564] Early unpacking initramfs... done
[   13.415926] ACPI: Core revision 20070126
[   13.415996] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   13.461351] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   13.501387] Using local APIC timer interrupts.
[   13.556860] APIC timer calibration result 12499899
[   13.556862] Detected 12.499 MHz APIC timer.
[   13.556919] Brought up 1 CPUs
[   13.556986] CPU0 attaching sched-domain:
[   13.556989]  domain 0: span 01
[   13.556991]   groups: 01
[   13.557147] net_namespace: 120 bytes
[   13.557565] Time: 13:27:36  Date: 07/27/08
[   13.557594] NET: Registered protocol family 16
[   13.557762] ACPI: bus type pci registered
[   13.557831] PCI: Using configuration type 1
[   13.558686] ACPI: EC: Look up EC in DSDT
[   13.561534] ACPI: Interpreter enabled
[   13.561537] ACPI: (supports S0 S3 S4 S5)
[   13.561549] ACPI: Using IOAPIC for interrupt routing
[   13.564546] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.601407] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[   13.601410] ACPI: EC: driver started in interrupt mode
[   13.601445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   13.603120] PCI: Transparent bridge - 0000:00:14.4
[   13.603197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   13.603338] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   13.603451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   13.603564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   13.603678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.606763] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   13.606870] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   13.606975] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   13.607080] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   13.607185] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   13.607289] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   13.607394] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   13.607499] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   13.607609] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.607639] pnp: PnP ACPI init
[   13.607646] ACPI: bus type pnp registered
[   13.615457] pnp: PnP ACPI: found 11 devices
[   13.615459] ACPI: ACPI bus type pnp unregistered
[   13.615686] PCI: Using ACPI for IRQ routing
[   13.615689] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.615695] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   13.615697] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   13.615700] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[   13.615702] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[   13.616853] NET: Registered protocol family 8
[   13.616855] NET: Registered protocol family 20
[   13.616962] AppArmor: AppArmor Filesystem Enabled
[   13.620778] Time: tsc clocksource has been installed.
[   13.628797] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   13.628801] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   13.628805] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.628812] system 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.628815] system 00:08: ioport range 0x1200-0x120f has been reserved
[   13.628818] system 00:08: ioport range 0x500-0x51f has been reserved
[   13.628821] system 00:08: ioport range 0x40b-0x40b has been reserved
[   13.628824] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   13.628827] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   13.628830] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   13.628833] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   13.628836] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   13.628839] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   13.628842] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   13.628845] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   13.628848] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   13.628851] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   13.628854] system 00:08: ioport range 0x8000-0x805f has been reserved
[   13.628857] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   13.628860] system 00:08: ioport range 0x87f-0x87f has been reserved
[   13.628870] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   13.628873] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   13.628877] system 00:09: iomem range 0x0-0xfff could not be reserved
[   13.629227] PCI: Bridge: 0000:00:02.0
[   13.629230]   IO window: 9000-9fff
[   13.629233]   MEM window: c0100000-c01fffff
[   13.629235]   PREFETCH window: c8000000-cfffffff
[   13.629237] PCI: Bridge: 0000:00:06.0
[   13.629238]   IO window: disabled.
[   13.629241]   MEM window: disabled.
[   13.629243]   PREFETCH window: disabled.
[   13.629245] PCI: Bridge: 0000:00:07.0
[   13.629246]   IO window: disabled.
[   13.629248]   MEM window: disabled.
[   13.629250]   PREFETCH window: disabled.
[   13.629261] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   13.629263]   IO window: 0000a400-0000a4ff
[   13.629268]   IO window: 0000a800-0000a8ff
[   13.629274]   PREFETCH window: 50000000-53ffffff
[   13.629279]   MEM window: 54000000-57ffffff
[   13.629284] PCI: Bridge: 0000:00:14.4
[   13.629287]   IO window: a000-afff
[   13.629293]   MEM window: c0200000-c02fffff
[   13.629297]   PREFETCH window: disabled.
[   13.629313] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   13.629320] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   13.629327] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.629354] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 20
[   13.629410] NET: Registered protocol family 2
[   13.664807] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.665364] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.667658] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.668822] TCP: Hash tables configured (established 131072 bind 65536)
[   13.668826] TCP reno registered
[   13.680861] checking if image is initramfs... it is
[   14.131985] Switched to high resolution mode on CPU 0
[   14.344293] Freeing initrd memory: 7551k freed
[   14.352944] audit: initializing netlink socket (disabled)
[   14.352959] audit(1217165256.308:1): initialized
[   14.354880] VFS: Disk quotas dquot_6.5.1
[   14.354950] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.355083] io scheduler noop registered
[   14.355086] io scheduler anticipatory registered
[   14.355088] io scheduler deadline registered
[   14.355186] io scheduler cfq registered (default)
[   14.355192] PCI: MSI quirk detected. MSI deactivated.
[   14.787217] Boot video device is 0000:01:00.0
[   14.787396] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.787417] assign_interrupt_mode Found MSI capability
[   14.787421] Allocate Port Service[0000:00:02.0:pcie00]
[   14.787484] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   14.787503] assign_interrupt_mode Found MSI capability
[   14.787506] Allocate Port Service[0000:00:06.0:pcie00]
[   14.787559] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   14.787579] assign_interrupt_mode Found MSI capability
[   14.787582] Allocate Port Service[0000:00:07.0:pcie00]
[   14.813904] Real Time Clock Driver v1.12ac
[   14.813997] Linux agpgart interface v0.102
[   14.814000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.814225] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   14.814572] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   14.814582] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   14.815173] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.815239] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.815321] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.815658] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.815733] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.815738] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.815746] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.815748] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.815751] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.822974] mice: PS/2 mouse device common for all mice
[   14.823008] cpuidle: using governor ladder
[   14.823010] cpuidle: using governor menu
[   14.823156] NET: Registered protocol family 1
[   14.823257] registered taskstats version 1
[   14.823402]   Magic number: 0:340:484
[   14.823552] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   14.823556] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.823558] EDD information not available.
[   14.823567] Freeing unused kernel memory: 320k freed
[   14.826849] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.018828] fuse init (API version 7.9)
[   16.036952] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.040839] Marking TSC unstable due to TSC halts in idle
[   16.040851] Time: acpi_pm clocksource has been installed.
[   16.087529] ACPI: Thermal Zone [TZS0] (61 C)
[   16.136459] ACPI: Thermal Zone [TZS1] (44 C)
[   16.185195] ACPI: Thermal Zone [TZSV] (53 C)
[   16.759450] usbcore: registered new interface driver usbfs
[   16.759475] usbcore: registered new interface driver hub
[   16.763766] usbcore: registered new device driver usb
[   16.777880] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.777938] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
[   16.778249] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   16.778527] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   16.778551] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[   16.818060] SCSI subsystem initialized
[   16.835749] usb usb1: configuration #1 chosen from 1 choice
[   16.835774] hub 1-0:1.0: USB hub found
[   16.835788] hub 1-0:1.0: 4 ports detected
[   16.879315] libata version 3.00 loaded.
[   16.939529] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
[   16.939855] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   16.939920] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   16.939944] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[   16.999476] usb usb2: configuration #1 chosen from 1 choice
[   16.999502] hub 2-0:1.0: USB hub found
[   16.999513] hub 2-0:1.0: 4 ports detected
[   17.103444] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[   17.103759] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   17.103840] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   17.103899] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[   17.115137] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.115258] usb usb3: configuration #1 chosen from 1 choice
[   17.115280] hub 3-0:1.0: USB hub found
[   17.115287] hub 3-0:1.0: 8 ports detected
[   17.219281] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[   17.239366] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   17.239383] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   17.239392] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   17.239401] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   17.278967] ssb: Sonics Silicon Backplane found on PCI device 0000:06:05.0
[   17.281080] r8169 Gigabit Ethernet driver 2.2LK loaded
[   17.281118] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 23
[   17.281368] eth0: RTL8169sb/8110sb at 0xffffc200004f2400, 00:0a:e4:f0:18:1c, XID 10000000 IRQ 23
[   17.281941] ACPI: PCI Interrupt 0000:06:06.2[C] -> GSI 22 (level, low) -> IRQ 22
[   17.332071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208000-c02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   17.335220] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   17.335271] PCI: Setting latency timer of device 0000:00:14.1 to 64
[   17.335285] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[   17.342235] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[   17.343343] scsi0 : pata_atiixp
[   17.343930] scsi1 : pata_atiixp
[   17.344956] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[   17.344959] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[   17.507207] ata1.00: ATA-7: FUJITSU MHV2120AH, 000000A0, max UDMA/100
[   17.507213] ata1.00: 234441648 sectors, multi 16: LBA 
[   17.523155] ata1.00: configured for UDMA/100
[   17.842590] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L632B, TI30, max UDMA/33
[   17.842604] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   18.014276] ata2.00: configured for PIO4
[   18.014387] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120A 0000 PQ: 0 ANSI: 5
[   18.018977] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632B TI30 PQ: 0 ANSI: 5
[   18.025224] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.025230] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.035143] Driver 'sd' needs updating - please use bus_type methods
[   18.035234] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   18.035245] sd 0:0:0:0: [sda] Write Protect is off
[   18.035248] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.035261] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.035304] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   18.035312] sd 0:0:0:0: [sda] Write Protect is off
[   18.035314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.035325] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.035329]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   18.115957]  sda1 sda2 < sda5 >
[   18.144501] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.150713] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.150733] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   18.176743] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.176749] Uniform CD-ROM driver Revision: 3.20
[   18.176805] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   18.387701] Attempting manual resume
[   18.387705] swsusp: Resume From Partition 8:5
[   18.387707] PM: Checking swsusp image.
[   18.387935] PM: Resume from disk failed.
[   18.431247] kjournald starting.  Commit interval 5 seconds
[   18.431263] EXT3-fs: mounted filesystem with ordered data mode.
[   27.918633] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   28.221205] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.257171] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.528762] ACPI: WMI-Acer: Mapper loaded
[   28.652532] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   28.776268] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.852266] irda_init()
[   28.852287] NET: Registered protocol family 23
[   28.950963] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   28.950972] acer_acpi: Detected Acer AMW0 version 2 interface
[   28.952067] Registered led device: acer_acpi:mail
[   29.011776] input: Power Button (FF) as /devices/virtual/input/input3
[   29.035876] ACPI: Power Button (FF) [PWRF]
[   29.035936] input: Lid Switch as /devices/virtual/input/input4
[   29.057418] ACPI: Lid Switch [LID0]
[   29.057499] input: Sleep Button (CM) as /devices/virtual/input/input5
[   29.087814] ACPI: Sleep Button (CM) [SLPB]
[   29.173028] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   29.173067] nsc-ircc, chip->init
[   29.173082] nsc-ircc, Found chip at base=0x02e
[   29.173124] nsc-ircc, driver loaded (Dag Brattli)
[   29.173130] nsc_ircc_open(), can't get iobase of 0x2f8
[   29.173178] nsc-ircc, Found chip at base=0x02e
[   29.173220] nsc-ircc, driver loaded (Dag Brattli)
[   29.173222] nsc_ircc_open(), can't get iobase of 0x2f8
[   29.173461] nsc-ircc 00:0a: disabled
[   29.436683] usbcore: registered new interface driver ndiswrapper
[   29.743549] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[   29.743578] Yenta: Using CSCINT to route CSC interrupts to PCI
[   29.743580] Yenta: Routing CardBus interrupts to PCI
[   29.743587] Yenta TI: socket 0000:06:06.0, mfunc 0x010a1b22, devctl 0x64
[   29.976473] sdhci: Secure Digital Host Controller Interface driver
[   29.976478] sdhci: Copyright(c) Pierre Ossman
[   29.979885] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20
[   29.979890] Socket status: 30000006
[   29.979892] Yenta: Raising subordinate bus# of parent bus (#06) from #06 to #08
[   29.979898] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   29.979901] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   30.052850] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   30.059634] ACPI: PCI Interrupt 0000:06:06.3[A] -> GSI 20 (level, low) -> IRQ 20
[   30.059706] sdhci: SDHCI controller found at 0000:06:06.4 [104c:8034] (rev 0)
[   30.059725] ACPI: PCI Interrupt 0000:06:06.4[A] -> GSI 20 (level, low) -> IRQ 20
[   30.059999] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   30.060096] mmc0: SDHCI at 0xc0209000 irq 20 DMA
[   30.060224] sdhci:slot1: Will use DMA mode even though HW doesn't fully claim to support it.
[   30.060304] mmc1: SDHCI at 0xc0208c00 irq 20 DMA
[   30.060427] sdhci:slot2: Will use DMA mode even though HW doesn't fully claim to support it.
[   30.060507] mmc2: SDHCI at 0xc0208800 irq 20 DMA
[   30.088374] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   30.170074] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   30.289828] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00)
[   30.462501] r8169: eth0: link up
[   30.556324] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:10/LNXVIDEO:00/input/input7
[   30.581390] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.581882] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:19/LNXVIDEO:01/input/input8
[   30.601339] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.825857] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   31.012850] [fglrx] Maximum main memory to use for locked dma buffers: 921 MBytes.
[   31.012884] [fglrx] ASYNCIO init succeed!
[   31.013198] [fglrx] PAT is enabled successfully!
[   31.027179] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   31.051427] ACPI: AC Adapter [ADP1] (on-line)
[   31.269785] b43-phy0: Broadcom 4318 WLAN found
[   31.308020] ACPI: Battery Slot [BAT0] (battery present)
[   31.312152] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   31.312165] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   31.338592] phy0: Selected rate control algorithm 'simple'
[   32.000662] NET: Registered protocol family 17
[   32.885520] input: b43-phy0 as /devices/virtual/input/input9
[   33.136256] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   33.892337] lp: driver loaded but no devices found
[   34.341162] b43-phy0 debug: Chip initialized
[   34.341479] b43-phy0 debug: 32-bit DMA initialized
[   34.359581] Registered led device: b43-phy0:tx
[   34.359599] Registered led device: b43-phy0:rx
[   34.359616] Registered led device: b43-phy0:radio
[   34.359658] b43-phy0 debug: Wireless interface started
[   34.359662] b43-phy0 debug: Adding Interface type 2
[   34.381919] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   34.407163] b43-phy0: Radio hardware status changed to DISABLED
[   34.471046] b43-phy0: Radio turned on by software
[   34.471051] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   34.951541] EXT3 FS on sda1, internal journal
[   35.324115] NET: Registered protocol family 10
[   35.324346] lo: Disabled Privacy Extensions
[   35.325121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.263069] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.745138] ACPI: ACPI Dock Station Driver 
[   37.187159] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-34 processors (1 cpu cores) (version 2.20.00)
[   37.187202] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4
[   37.187205] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   37.187207] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16
[   38.323519] ppdev: user-space parallel port driver
[   38.435160] audit(1217165281.088:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5141 profile="/usr/sbin/cupsd" namespace="default"
[   38.871162] Clocksource tsc unstable (delta = -215681389 ns)
[   38.927945] b43-phy0 debug: Removing Interface type 2
[   38.949317] b43-phy0 debug: Wireless interface stopped
[   38.949546] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[   38.949703] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[   38.952766] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[   38.956374] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[   38.959879] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[   38.963428] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[   38.966972] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[   38.997056] ACPI: PCI interrupt for device 0000:06:05.0 disabled
[   39.055304] usbcore: deregistering interface driver ndiswrapper
[   39.072580] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.118637] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   39.119853] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   39.120321] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 21
[   39.124191] ndiswrapper: using IRQ 21
[   39.226484] wlan0: ethernet device 00:16:ce:0c:77:7e using NDIS driver: bcmwl5, version: 0x364400a, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   39.226764] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   39.226985] usbcore: registered new interface driver ndiswrapper
[   39.281851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.793703] ttyS1: LSR safety check engaged!
[   40.023799] Bluetooth: Core ver 2.11
[   40.024237] NET: Registered protocol family 31
[   40.024240] Bluetooth: HCI device and connection manager initialized
[   40.024243] Bluetooth: HCI socket layer initialized
[   40.042898] Bluetooth: L2CAP ver 2.9
[   40.042901] Bluetooth: L2CAP socket layer initialized
[   40.095335] Bluetooth: RFCOMM socket layer initialized
[   40.095348] Bluetooth: RFCOMM TTY layer initialized
[   40.095350] Bluetooth: RFCOMM ver 1.8
[   41.091360] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.670548] eth0: no IPv6 routers present
[   42.004818] [fglrx] Reserve Block - 0 offset =  0X3ffb000 length = 0X5000
[   42.004825] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X40000
[   42.004828] [fglrx] Reserve Block - 2 offset =  0X3fbb000 length = 0X40000
[   42.137234] [fglrx] interrupt source 20008000 successfully enabled
[   42.137241] [fglrx] enable ID = 0x00000004
[   42.137594] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   42.137805] [fglrx] interrupt source 10000000 successfully enabled
[   42.137809] [fglrx] enable ID = 0x00000005
[   42.138024] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000

```

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

scaning:
```
wlan0     No scan results

```

EDIT:

I've also heard of a program called acer_acpi which is aparently needed to turn on the wireless card, although I have no idea how to install it.. is that any help?

---

### Post by Bison Ravi on 2008-07-27
I have no idea about acer_acpi, I never heard of it before. It is obsolete from what found on google.

huh...

It looks like the hardware is detected and installed properly.

I have a doubt about a line in the dmesg output (cf "wlan0 link is not ready"). I will try to figure out why it never becomes ready. Okay, I checked, I think there is no problem there.

Just go further and do the things below:

iwlist wlan0 scanning should list the existing networks around but you get nothing.

Are you far from the router ? Get next to it to have a strong signal.

You will loose the wired connection with the following.Read the end for how to get it back.

begin with turning off the network manager:
sudo /etc/dbus-1/event.d/25NetworkManager stop

disable the wired connection:
sudo ifconfig eth0 down

try "iwlist wlan0 scanning"

I hope that you can see your network now. try it a couple of times if nothing appear. Try what follows even if the scanning does not show any result, who knows.

type in (I assume the WEP encryption is off, you can deal with that later):

sudo iwconfig wlan0 essid yournetwork

It should associate the wireless card to yournetwork

To check, type in:

iwconfig

ESSID should now be "yournetwork" instead of "off/any"

type in 

sudo dhclient wlan0

It should give you an ip address.

To get the wired connection back, either you reboot the machine or type in:

sudo /etc/dbus-1/event.d/25NetworkManager start
sudo ifconfig eth0 up
sudo dhclient eth0

---

### Post by rtrdom on 2008-07-27
Try looking at a post by Kevdog with title How to Troubleshoot Your Wireless
Connection - Connecting at the command line.  Helped me a lot.
See sticky at top of forums for:[http://ubuntuforums.org/showthread.php?t=571188&highlight=Troubleshoot+Wireless](http://ubuntuforums.org/showthread.php?t=571188&highlight=Troubleshoot+Wireless)

---

### Post by james1306 on 2008-07-27
Tried all of that - and it still doesn't seem to work. I'm right next to my router too since I'm wired to it at the moment.

Whenever I load up the network manager it doesn;t scan for networks either, is that due to the lack of compatibility from my wireless card? 

Really hope this gets sorted as I'll have to move back to Windows otherwise :(

---

### Post by chocbar31 on 2008-07-27
Try turning off the ACL, I have not had good luck with a Linksys router running the ACL list in my experience. Also,in the past I had better luck starting-out with no security and then re-applying security one part at-a-time until issues occurred. 

WPA seems to have been OK for me but not for you it seems.

May I suggest trying this link to see if you have different results?:
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by james1306 on 2008-07-27
Just tried that link, worked completely and had no issues - just still can't get wireless.

**** it - dual boot time.

---

### Post by Ayuthia on 2008-07-27
> **james1306 said:**
> Just tried that link, worked completely and had no issues - just still can't get wireless.

**** it - dual boot time.

Can you post the results of:
```
lsmod|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
```
Your dmesg looks like there might be two drivers loaded that might be conflicting.

---

### Post by InTheShires on 2008-08-01
I'm no expert, but have finally got my Broadcom 4318 wireless setup properly, and am using it now! 

In the end, all I did was download the firmware for the card from [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) (In .deb format to make installation easy!) The version I used on my Acer 3050 was "b43-firmware_1.0-0cafuego0_all.deb"

Once that was installed, I just set up my network settings. (I enabled "Roaming", and then chose "Connect to other wireless network", and entered my details. (SSID/Pass etc)

However, it still wouldn't connect, even though the wifi light was on. So, I held the wifi switch on for a few seconds. (On mine, you slide it to the right) That then bought the little Blue network bars up showing that the wifi was connected. 

I've tried this twice now, on a vanilla install of Hardy 8.4.1 and it's worked both times. I've not had to fiddle with anything else, other than install the file I mentioned above.

Hope others get as lucky as I seem to have!

---

