---
title: "I'm having trouble setting up wireless connection"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by alontkach on 2008-12-07
Hi, I Just recently got the INtrepid Ubuntu.

I am using a laptop at home, and want it to connect wireless to my cable modem on my desktop computer.

IN the terminal, I have entered the following commands:

nm-tool
iwconfig
ping -c 4 google.com
ifconfig
netstat -r
sudo lshw -C network
lsusb
lspci

Here are the results I got:

NetworkManager Tool

State: disconnected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:08:02:69:6F:D5

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ping: unknown host google.com

eth0      Link encap:Ethernet  HWaddr 00:08:02:69:6f:d5  
          inet6 addr: fe80::208:2ff:fe69:6fd5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68465056 (68.4 MB)  TX bytes:1845531 (1.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17856 (17.8 KB)  TX bytes:17856 (17.8 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

 *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:69:6f:d5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:61:8f:b8:1b:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)


OK guys, thanks in advance!

Al

---

### Post by lovelyvik293 on 2008-12-07
Above output shows that the ubuntu doesn't recognized your wifi card.
Please tell about the vendor of the wifi card of your system

---

### Post by jmoorse on 2008-12-07
What is the make and model of your edit: PCI card?  Does entering the command dmesg show any output that would be related to your card?

I would check out ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

A bit tough to work out for first times but should work.

--Jeff Moorse

---

### Post by alontkach on 2008-12-07
> **jmoorse said:**
> What is the make and model of your PCMICA card?  Does entering the command dmesg show any output that would be related to your card?

I would check out ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

A bit tough to work out for first times but should work.

--Jeff Moorse

I don't know the make and model of the PCMICA card, and I don't know how to find out what it is.

Here is the result after entering: "dmesg" into terminal:

[    0.004412] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004417] CPU: L2 cache: 512K
[    0.004421] CPU: Hyper-Threading is disabled
[    0.004444] Checking 'hlt' instruction... OK.
[    0.020718] SMP alternatives: switching to UP code
[    0.031920] Freeing SMP alternatives: 11k freed
[    0.031927] ACPI: Core revision 20080609
[    0.036625] ACPI: Checking initramfs for custom DSDT
[    0.514072] ACPI: setting ELCR to 0200 (from 0c20)
[    0.516126] weird, boot CPU (#0) not listedby the BIOS.
[    0.516132] SMP motherboard not detected.
[    0.516136] Local APIC not detected. Using dummy APIC emulation.
[    0.516140] SMP disabled
[    0.516245] Brought up 1 CPUs
[    0.516251] Total of 1 processors activated (3987.02 BogoMIPS).
[    0.516270] CPU0 attaching sched-domain:
[    0.516276]  domain 0: span 0 level CPU
[    0.516281]   groups: 0
[    0.520153] net_namespace: 840 bytes
[    0.520167] Booting paravirtualized kernel on bare hardware
[    0.520482] Time: 22:10:40  Date: 12/07/08
[    0.520535] NET: Registered protocol family 16
[    0.521117] EISA bus registered
[    0.521151] ACPI: bus type pci registered
[    0.523540] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=3
[    0.523545] PCI: Using configuration type 1 for base access
[    0.526511] ACPI: EC: Look up EC in DSDT
[    0.527154] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.572233] ACPI: Interpreter enabled
[    0.572242] ACPI: (supports S0 S3 S4 S5)
[    0.572266] ACPI: Using PIC for interrupt routing
[    0.592143] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.592149] ACPI: EC: driver started in interrupt mode
[    0.592303] ACPI: PCI Root Bridge [C03C] (0000:00)
[    0.592433] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.592626] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.592637] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.592644] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH4 GPIO
[    0.592677] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.592686] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.592695] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.592704] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.592713] PCI: 0000:00:1f.1 reg 20 io port: [4440, 444f]
[    0.592723] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.592765] PCI: 0000:00:1f.5 reg 10 io port: [4000, 40ff]
[    0.592774] PCI: 0000:00:1f.5 reg 14 io port: [4400, 443f]
[    0.592856] PCI: 0000:01:00.0 reg 10 32bit mmio: [88000000, 8fffffff]
[    0.592864] PCI: 0000:01:00.0 reg 14 io port: [3000, 30ff]
[    0.592872] PCI: 0000:01:00.0 reg 18 32bit mmio: [80380000, 8038ffff]
[    0.592894] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.592915] pci 0000:01:00.0: supports D1
[    0.592917] pci 0000:01:00.0: supports D2
[    0.592959] PCI: bridge 0000:00:01.0 io port: [3000, 3fff]
[    0.592964] PCI: bridge 0000:00:01.0 32bit mmio: [80300000, 803fffff]
[    0.592969] PCI: bridge 0000:00:01.0 32bit mmio pref: [88000000, 900fffff]
[    0.593018] PCI: 0000:02:04.0 reg 10 32bit mmio: [80280000, 802800ff]
[    0.593028] PCI: 0000:02:04.0 reg 14 io port: [2440, 2447]
[    0.593038] PCI: 0000:02:04.0 reg 18 io port: [2000, 20ff]
[    0.593078] pci 0000:02:04.0: supports D2
[    0.593082] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.593088] pci 0000:02:04.0: PME# disabled
[    0.593126] PCI: 0000:02:06.0 reg 10 32bit mmio: [80080000, 80080fff]
[    0.593145] pci 0000:02:06.0: supports D1
[    0.593148] pci 0000:02:06.0: supports D2
[    0.593151] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593158] pci 0000:02:06.0: PME# disabled
[    0.593193] PCI: 0000:02:08.0 reg 10 32bit mmio: [80100000, 80100fff]
[    0.593202] PCI: 0000:02:08.0 reg 14 io port: [2400, 243f]
[    0.593246] pci 0000:02:08.0: supports D1
[    0.593249] pci 0000:02:08.0: supports D2
[    0.593252] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593258] pci 0000:02:08.0: PME# disabled
[    0.593299] PCI: 0000:02:0e.0 reg 10 32bit mmio: [80180000, 80180fff]
[    0.593349] pci 0000:02:0e.0: supports D1
[    0.593352] pci 0000:02:0e.0: supports D2
[    0.593355] pci 0000:02:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593361] pci 0000:02:0e.0: PME# disabled
[    0.593396] PCI: 0000:02:0e.1 reg 10 32bit mmio: [80200000, 80200fff]
[    0.593445] pci 0000:02:0e.1: supports D1
[    0.593449] pci 0000:02:0e.1: supports D2
[    0.593452] pci 0000:02:0e.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593458] pci 0000:02:0e.1: PME# disabled
[    0.593495] PCI: 0000:02:0e.2 reg 10 32bit mmio: [80300000, 803000ff]
[    0.593547] pci 0000:02:0e.2: supports D1
[    0.593550] pci 0000:02:0e.2: supports D2
[    0.593553] pci 0000:02:0e.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.593559] pci 0000:02:0e.2: PME# disabled
[    0.593593] pci 0000:00:1e.0: transparent bridge
[    0.593599] PCI: bridge 0000:00:1e.0 io port: [2000, 2fff]
[    0.593605] PCI: bridge 0000:00:1e.0 32bit mmio: [80000000, 803fffff]
[    0.593642] bus 00 -> node 0
[    0.593655] ACPI: PCI Interrupt Routing Table [\_SB_.C03C._PRT]
[    0.593698] ACPI: PCI Interrupt Routing Table [\_SB_.C03C.C03D._PRT]
[    0.593729] ACPI: PCI Interrupt Routing Table [\_SB_.C03C.C04E._PRT]
[    0.604686] ACPI: PCI Interrupt Link [C0B6] (IRQs 5 10 *11)
[    0.605074] ACPI: PCI Interrupt Link [C0B7] (IRQs *5 10 11)
[    0.605442] ACPI: PCI Interrupt Link [C0B8] (IRQs 5 10 11) *0, disabled.
[    0.605828] ACPI: PCI Interrupt Link [C0B9] (IRQs 5 10 *11)
[    0.606211] ACPI: PCI Interrupt Link [C0BA] (IRQs 5 *10 11)
[    0.606579] ACPI: PCI Interrupt Link [C0BB] (IRQs) *0, disabled.
[    0.606951] ACPI: PCI Interrupt Link [C0BC] (IRQs) *0, disabled.
[    0.607317] ACPI: PCI Interrupt Link [C0BD] (IRQs) *0, disabled.
[    0.607775] ACPI: Power Resource [C141] (off)
[    0.607946] ACPI: Power Resource [C155] (off)
[    0.608139] ACPI: Power Resource [C159] (off)
[    0.608308] ACPI: Power Resource [C15D] (off)
[    0.608388] ACPI: Power Resource [C166] (on)
[    0.608516] ACPI: Power Resource [C0CF] (on)
[    0.608686] ACPI: Power Resource [C1D5] (off)
[    0.608846] ACPI: Power Resource [C1D6] (off)
[    0.609003] ACPI: Power Resource [C1D7] (off)
[    0.609157] ACPI: Power Resource [C1D8] (off)
[    0.609376] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.609447] pnp: PnP ACPI init
[    0.609464] ACPI: bus type pnp registered
[    0.632381] pnp: PnP ACPI: found 14 devices
[    0.632388] ACPI: ACPI bus type pnp unregistered
[    0.632396] PnPBIOS: Disabled by ACPI PNP
[    0.633120] PCI: Using ACPI for IRQ routing
[    0.633135] pci 0000:00:1e.0: BAR 8: can't allocate resource
[    0.633177] pci 0000:02:0e.2: BAR 0: can't allocate resource
[    0.633326] NET: Registered protocol family 8
[    0.633326] NET: Registered protocol family 20
[    0.633326] NetLabel: Initializing
[    0.633326] NetLabel:  domain hash size = 128
[    0.633326] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.633326] NetLabel:  unlabeled traffic allowed by default
[    0.633326] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.633326]    actual entries 65620
[    0.633326] AppArmor: AppArmor Filesystem Enabled
[    0.633326] ACPI: RTC can wake from S4
[    0.633326] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.633326] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.633326] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[    0.633326] system 00:0c: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.633326] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.633326] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[    0.633326] system 00:0d: ioport range 0x1000-0x107f has been reserved
[    0.633326] system 00:0d: ioport range 0x1100-0x113f has been reserved
[    0.633326] system 00:0d: ioport range 0x1200-0x121f has been reserved
[    0.633326] system 00:0d: iomem range 0xffc00000-0xffc003ff has been reserved
[    0.669989] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.669996] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.670003] pci 0000:00:01.0:   MEM window: 0x80300000-0x803fffff
[    0.670008] pci 0000:00:01.0:   PREFETCH window: 0x00000088000000-0x000000900fffff
[    0.670024] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.670028] pci 0000:02:06.0:   IO window: 0x002800-0x0028ff
[    0.670034] pci 0000:02:06.0:   IO window: 0x002c00-0x002cff
[    0.670042] pci 0000:02:06.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.670048] pci 0000:02:06.0:   MEM window: 0x34000000-0x37ffffff
[    0.670054] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.670059] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.670067] pci 0000:00:1e.0:   MEM window: 0x34000000-0x39ffffff
[    0.670074] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
[    0.670101] pci 0000:00:1e.0: setting latency timer to 64
[    0.670728] ACPI: PCI Interrupt Link [C0B9] enabled at IRQ 11
[    0.670733] PCI: setting IRQ 11 as level-triggered
[    0.670740] pci 0000:02:06.0: PCI INT A -> Link[C0B9] -> GSI 11 (level, low) -> IRQ 11
[    0.670749] bus: 00 index 0 io port: [0, ffff]
[    0.670754] bus: 00 index 1 mmio: [0, ffffffff]
[    0.670758] bus: 01 index 0 io port: [3000, 3fff]
[    0.670762] bus: 01 index 1 mmio: [80300000, 803fffff]
[    0.670765] bus: 01 index 2 mmio: [88000000, 900fffff]
[    0.670769] bus: 01 index 3 mmio: [0, 0]
[    0.670772] bus: 02 index 0 io port: [2000, 2fff]
[    0.670776] bus: 02 index 1 mmio: [34000000, 39ffffff]
[    0.670779] bus: 02 index 2 mmio: [30000000, 33ffffff]
[    0.670782] bus: 02 index 3 io port: [0, ffff]
[    0.670786] bus: 02 index 4 mmio: [0, ffffffff]
[    0.670789] bus: 03 index 0 io port: [2800, 28ff]
[    0.670792] bus: 03 index 1 io port: [2c00, 2cff]
[    0.670795] bus: 03 index 2 mmio: [30000000, 33ffffff]
[    0.670798] bus: 03 index 3 mmio: [34000000, 37ffffff]
[    0.670820] NET: Registered protocol family 2
[    0.671095] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.671497] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.671606] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.671710] TCP: Hash tables configured (established 16384 bind 16384)
[    0.671718] TCP reno registered
[    0.671868] NET: Registered protocol family 1
[    0.672099] checking if image is initramfs... it is
[    1.172097] Switched to high resolution mode on CPU 0
[    1.653702] Freeing initrd memory: 8006k freed
[    1.654790] audit: initializing netlink socket (disabled)
[    1.654824] type=2000 audit(1228687840.652:1): initialized
[    1.661512] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.665577] VFS: Disk quotas dquot_6.5.1
[    1.665745] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.665964] msgmni has been set to 1003
[    1.666186] io scheduler noop registered
[    1.666192] io scheduler anticipatory registered
[    1.666198] io scheduler deadline registered
[    1.666226] io scheduler cfq registered (default)
[    1.666267] pci 0000:01:00.0: Boot video device
[    1.666294] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.666931] isapnp: Scanning for PnP cards...
[    2.021048] isapnp: No Plug & Play device found
[    2.102049] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.102230] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.102707] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a NS16550A
[    2.103650] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.107154] brd: module loaded
[    2.107290] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.107529] PNP: PS/2 Controller [PNP0303:C163,PNP0f13:C164] at 0x60,0x64 irq 1,12
[    2.109874] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.111709] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.111720] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.111725] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.111729] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.111733] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.112879] mice: PS/2 mouse device common for all mice
[    2.113185] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    2.113211] rtc0: alarms up to one month, y3k
[    2.113448] EISA: Probing bus 0 at eisa.0
[    2.113461] Cannot allocate resource for EISA slot 1
[    2.113467] Cannot allocate resource for EISA slot 2
[    2.113472] Cannot allocate resource for EISA slot 3
[    2.113477] Cannot allocate resource for EISA slot 4
[    2.113499] EISA: Detected 0 cards.
[    2.113506] cpuidle: using governor ladder
[    2.113512] cpuidle: using governor menu
[    2.114354] TCP cubic registered
[    2.114406] Using IPI No-Shortcut mode
[    2.114874] registered taskstats version 1
[    2.115045]   Magic number: 4:513:198
[    2.115122] tty ttypd: hash matches
[    2.115284] rtc_cmos 00:09: setting system clock to 2008-12-07 22:10:41 UTC (1228687841)
[    2.115290] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.115295] EDD information not available.
[    2.116046] Freeing unused kernel memory: 424k freed
[    2.116125] Write protecting the kernel text: 2576k
[    2.116173] Write protecting the kernel read-only data: 936k
[    2.137651] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.392849] fuse init (API version 7.9)
[    2.558181] ACPI: Transitioning device [C1D9] to D3
[    2.563279] fan PNP0C0B:00: registered as cooling_device0
[    2.563291] ACPI: Fan [C1D9] (off)
[    2.563596] ACPI: Transitioning device [C1DA] to D3
[    2.568657] fan PNP0C0B:01: registered as cooling_device1
[    2.568668] ACPI: Fan [C1DA] (off)
[    2.568966] ACPI: Transitioning device [C1DB] to D3
[    2.574017] fan PNP0C0B:02: registered as cooling_device2
[    2.574028] ACPI: Fan [C1DB] (off)
[    2.574325] ACPI: Transitioning device [C1DC] to D3
[    2.579375] fan PNP0C0B:03: registered as cooling_device3
[    2.579386] ACPI: Fan [C1DC] (off)
[    2.665017] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.670078] processor ACPI0007:00: registered as cooling_device4
[    2.670086] ACPI: Processor [C000] (supports 8 throttling states)
[    2.710726] thermal LNXTHERM:01: registered as thermal_zone0
[    2.722868] ACPI: Thermal Zone [TZ1] (42 C)
[    2.731361] thermal LNXTHERM:02: registered as thermal_zone1
[    2.737666] ACPI: Thermal Zone [TZ2] (35 C)
[    2.744411] thermal LNXTHERM:03: registered as thermal_zone2
[    2.746495] ACPI: Thermal Zone [TZ3] (16 C)
[    4.275941] No dock devices found.
[    4.370849] SCSI subsystem initialized
[    4.393364] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    4.393371] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.393507] e100 0000:02:08.0: power state changed by ACPI to D0
[    4.394115] ACPI: PCI Interrupt Link [C0BA] enabled at IRQ 10
[    4.394120] PCI: setting IRQ 10 as level-triggered
[    4.394126] e100 0000:02:08.0: PCI INT A -> Link[C0BA] -> GSI 10 (level, low) -> IRQ 10
[    4.417753] e100 0000:02:08.0: PME# disabled
[    4.498841] e100: eth0: e100_probe: addr 0x80100000, irq 10, MAC addr 00:08:02:69:6f:d5
[    4.535338] usbcore: registered new interface driver usbfs
[    4.535383] usbcore: registered new interface driver hub
[    4.549263] usbcore: registered new device driver usb
[    4.637851] ehci_hcd 0000:02:0e.2: PCI INT C -> Link[C0BA] -> GSI 10 (level, low) -> IRQ 10
[    4.637873] ehci_hcd 0000:02:0e.2: EHCI Host Controller
[    4.637968] ehci_hcd 0000:02:0e.2: new USB bus registered, assigned bus number 1
[    4.645865] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.649651] libata version 3.00 loaded.
[    4.660134] ehci_hcd 0000:02:0e.2: irq 10, io mem 0x38000000
[    4.672065] ehci_hcd 0000:02:0e.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[    4.672358] usb usb1: configuration #1 chosen from 1 choice
[    4.672408] hub 1-0:1.0: USB hub found
[    4.672425] hub 1-0:1.0: 5 ports detected
[    4.880734] ohci_hcd 0000:02:0e.0: PCI INT A -> Link[C0BA] -> GSI 10 (level, low) -> IRQ 10
[    4.880761] ohci_hcd 0000:02:0e.0: OHCI Host Controller
[    4.880812] ohci_hcd 0000:02:0e.0: new USB bus registered, assigned bus number 2
[    4.880842] ohci_hcd 0000:02:0e.0: irq 10, io mem 0x80180000
[    6.274321] usb usb2: configuration #1 chosen from 1 choice
[    6.274381] hub 2-0:1.0: USB hub found
[    6.274399] hub 2-0:1.0: 3 ports detected
[    6.892577] ohci_hcd 0000:02:0e.1: PCI INT B -> Link[C0BA] -> GSI 10 (level, low) -> IRQ 10
[    6.892603] ohci_hcd 0000:02:0e.1: OHCI Host Controller
[    6.892653] ohci_hcd 0000:02:0e.1: new USB bus registered, assigned bus number 3
[    6.892683] ohci_hcd 0000:02:0e.1: irq 10, io mem 0x80200000
[    7.564097] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    7.783373] usb 2-2: configuration #1 chosen from 1 choice
[    8.111671] usb usb3: configuration #1 chosen from 1 choice
[    8.111726] hub 3-0:1.0: USB hub found
[    8.111743] hub 3-0:1.0: 2 ports detected
[    8.631758] ata_piix 0000:00:1f.1: version 2.12
[    8.631777] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    8.632443] ACPI: PCI Interrupt Link [C0B8] enabled at IRQ 11
[    8.632450] ata_piix 0000:00:1f.1: PCI INT A -> Link[C0B8] -> GSI 11 (level, low) -> IRQ 11
[    8.632525] ata_piix 0000:00:1f.1: setting latency timer to 64
[    8.633806] scsi0 : ata_piix
[    8.634014] scsi1 : ata_piix
[    8.635417] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4440 irq 14
[    8.635422] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4448 irq 15
[    8.796702] ata1.00: ATA-5: IC25N040ATCS04-0, CA4OA71A, max UDMA/100
[    8.796709] ata1.00: 78140160 sectors, multi 16: LBA 
[    8.812634] ata1.00: configured for UDMA/100
[    8.992411] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4240N, 0111, max MWDMA2
[    9.008353] ata2.00: configured for MWDMA2
[    9.008580] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS04-0 CA4O PQ: 0 ANSI: 5
[    9.013041] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4240N 0111 PQ: 0 ANSI: 5
[    9.145245] usbcore: registered new interface driver hiddev
[    9.152572] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-2/2-2:1.0/input/input2
[    9.168369] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:02:0e.0-2
[    9.168412] usbcore: registered new interface driver usbhid
[    9.168419] usbhid: v2.6:USB HID core driver
[    9.209685] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    9.209747] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    9.274153] Driver 'sd' needs updating - please use bus_type methods
[    9.279665] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    9.279703] sd 0:0:0:0: [sda] Write Protect is off
[    9.279708] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.279764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.279904] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    9.279935] sd 0:0:0:0: [sda] Write Protect is off
[    9.279939] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.279993] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.280047]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    9.300715]  sda1 sda2 < sda5 >
[    9.329465] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.358452] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    9.358462] Uniform CD-ROM driver Revision: 3.20
[    9.358640] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    9.421858] Marking TSC unstable due to TSC halts in idle
[    9.706721] PM: Starting manual resume from disk
[    9.706728] PM: Resume from partition 8:5
[    9.706730] PM: Checking hibernation image.
[    9.707035] PM: Resume from disk failed.
[    9.744127] EXT3-fs: INFO: recovery required on readonly filesystem.
[    9.744133] EXT3-fs: write access will be enabled during recovery.
[   14.560356] kjournald starting.  Commit interval 5 seconds
[   14.560390] EXT3-fs: sda1: orphan cleanup on readonly fs
[   14.958748] ext3_orphan_cleanup: deleting unreferenced inode 688181
[   14.965822] ext3_orphan_cleanup: deleting unreferenced inode 1499176
[   14.965838] EXT3-fs: sda1: 2 orphan inodes deleted
[   14.965841] EXT3-fs: recovery complete.
[   14.984424] EXT3-fs: mounted filesystem with ordered data mode.
[   25.384587] udevd version 124 started
[   26.312701] Linux agpgart interface v0.103
[   26.380374] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.443086] intel_rng: FWH not detected
[   26.596678] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   26.612560] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   26.687165] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.902174] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   26.972731] iTCO_vendor_support: vendor-support=0
[   27.028191] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   27.028432] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   27.028697] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.079072] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   27.088105] ACPI: Power Button (FF) [PWRF]
[   27.088521] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   27.104104] ACPI: Power Button (CM) [C17C]
[   27.104377] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   27.120109] ACPI: Sleep Button (CM) [C11F]
[   27.120381] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input7
[   27.120555] ACPI: Lid Switch [C11E]
[   27.143790] ACPI: AC Adapter [C11B] (on-line)
[   27.206328] ACPI: Battery Slot [C11D] (battery present)
[   27.206716] ACPI: Battery Slot [C11C] (battery absent)
[   28.306836] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x336ab1, caps: 0x984793/0x0
[   28.306847] serio: Synaptics pass-through port at isa0060/serio4/input0
[   28.347403] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   30.268503] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:004a]
[   30.268529] Yenta: Enabling burst memory read transactions
[   30.268535] Yenta: Using CSCINT to route CSC interrupts to PCI
[   30.268538] Yenta: Routing CardBus interrupts to PCI
[   30.268546] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[   30.500673] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   30.500679] Socket status: 30000006
[   30.500685] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   30.500696] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   30.500701] cs: IO port probe 0x2000-0x2fff: clean.
[   30.501008] pcmcia: parent PCI bridge Memory window: 0x34000000 - 0x39ffffff
[   30.501012] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   30.518566] irda_init()
[   30.518591] NET: Registered protocol family 23
[   30.755551] parport_pc 00:05: reported by Plug and Play ACPI
[   30.755663] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   30.852652] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3E8 ; irq 3 ; dma 3.
[   30.853090] nsc-ircc, chip->init
[   30.853103] nsc-ircc, Found chip at base=0x02e
[   30.853130] nsc-ircc, driver loaded (Dag Brattli)
[   30.853140] nsc_ircc_open(), can't get iobase of 0x3e8
[   30.853170] nsc-ircc, Found chip at base=0x02e
[   30.853197] nsc-ircc, driver loaded (Dag Brattli)
[   30.853201] nsc_ircc_open(), can't get iobase of 0x3e8
[   30.857274] nsc-ircc 00:04: disabled
[   31.060679] Intel ICH 0000:00:1f.5: power state changed by ACPI to D0
[   31.061257] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 5
[   31.061262] PCI: setting IRQ 5 as level-triggered
[   31.061268] Intel ICH 0000:00:1f.5: PCI INT B -> Link[C0B7] -> GSI 5 (level, low) -> IRQ 5
[   31.061293] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   31.732143] intel8x0_measure_ac97_clock: measured 54306 usecs
[   31.732149] intel8x0: clocking to 48000
[   32.726727] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input9
[   34.890459] cs: IO port probe 0x100-0x3af: clean.
[   34.892520] cs: IO port probe 0x3e0-0x4ff: clean.
[   34.893349] cs: IO port probe 0x820-0x8ff: clean.
[   34.894080] cs: IO port probe 0xc00-0xcf7: clean.
[   34.895066] cs: IO port probe 0xa00-0xaff: clean.
[   35.360641] lp0: using parport0 (interrupt-driven).
[   35.597741] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   36.169121] EXT3 FS on sda1, internal journal
[   37.462359] type=1505 audit(1228687877.282:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3950
[   37.741564] type=1505 audit(1228687877.562:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3955
[   37.742039] type=1505 audit(1228687877.562:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3955
[   37.946642] ip_tables: (C) 2000-2006 Netfilter Core Team
[   38.880963] ACPI: WMI: Mapper loaded
[   40.383798] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   40.486679] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   40.486692] apm: overridden by ACPI.
[   40.665967] ppdev: user-space parallel port driver
[   42.168051] Clocksource tsc unstable (delta = -174362534 ns)
[   43.535084] ttyS2: LSR safety check engaged!
[   43.780527] Bluetooth: Core ver 2.13
[   43.784618] NET: Registered protocol family 31
[   43.784642] Bluetooth: HCI device and connection manager initialized
[   43.784648] Bluetooth: HCI socket layer initialized
[   43.821961] Bluetooth: L2CAP ver 2.11
[   43.821973] Bluetooth: L2CAP socket layer initialized
[   43.878138] Bluetooth: SCO (Voice Link) ver 0.6
[   43.878176] Bluetooth: SCO socket layer initialized
[   43.903181] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   43.903192] Bluetooth: BNEP filters: protocol multicast
[   43.968260] Bridge firewalling registered
[   43.969519] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   43.995169] Bluetooth: RFCOMM socket layer initialized
[   43.996862] Bluetooth: RFCOMM TTY layer initialized
[   43.996873] Bluetooth: RFCOMM ver 1.10
[   47.692269] ACPI: PCI Interrupt Link [C0B6] enabled at IRQ 11
[   47.692303] pci 0000:01:00.0: PCI INT A -> Link[C0B6] -> GSI 11 (level, low) -> IRQ 11
[   48.121805] [drm] Initialized drm 1.1.0 20060810
[   48.153358] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   48.192193] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   48.667147] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   48.667192] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   48.667213] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   48.777275] NET: Registered protocol family 17
[   49.109759] [drm] Setting GART location based on new memory map
[   49.109787] [drm] Loading R100 Microcode
[   49.109852] [drm] writeback test succeeded in 1 usecs
[  155.655317] ttyS2: LSR safety check engaged!
[  155.655362] type=1503 audit(1228687996.468:5): operation="capable" name="sys_admin" pid=5459 profile="/usr/sbin/cupsd"
[  158.176463] ppdev0: registered pardevice
[  158.224358] ppdev0: unregistered pardevice
[  158.576239] ppdev0: registered pardevice
[  158.624134] ppdev0: unregistered pardevice
[  158.649764] ppdev0: registered pardevice
[  158.700608] ppdev0: unregistered pardevice
[  468.165230] NET: Registered protocol family 10
[  468.169730] lo: Disabled Privacy Extensions
[  478.744046] eth0: no IPv6 routers present
[  967.000356] e100: eth0: e100_watchdog: link down

---

