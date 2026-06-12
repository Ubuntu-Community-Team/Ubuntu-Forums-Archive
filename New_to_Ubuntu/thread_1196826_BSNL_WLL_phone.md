---
title: "BSNL WLL phone"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by ttsdinesh on 2009-06-25
I am using BSNL WLL phone. On the phone cover the company name is printed as HTC Clarity-IIA. But i installed VIA CBP USB driver. When i installed OpenSolaris,it detected my modem as CDS4. I am using USB to USB cable to connect phone and PC.I cant configure this modem in Ubuntu. please help me with step by step process of configuring.I am new to ubuntu. So please help me. "If possible" mail the steps to [EMAIL="ttsdinesh@gmail.com"]ttsdinesh@gmail.com[/EMAIL].

-->I tried the following steps:
```
**lsusb**
```
the output is:
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

-->Again when i pluged-in my modem, i got:

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 15eb:0001 ** 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```
**dmesg |grep usb**
```
the output is:
[    2.815386] usbcore: registered new interface driver usbfs
[    2.815427] usbcore: registered new interface driver hub
[    2.815502] usbcore: registered new device driver usb
[    2.861066] usb usb1: configuration #1 chosen from 1 choice
[    3.069279] usb usb2: configuration #1 chosen from 1 choice
[    3.180648] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.277349] usb usb3: configuration #1 chosen from 1 choice
[    3.356053] usb 1-1: configuration #1 chosen from 1 choice
[    3.468031] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.484631] usb usb4: configuration #1 chosen from 1 choice
[    3.625368] usb 2-2: configuration #1 chosen from 1 choice
[    3.704373] usb usb5: configuration #1 chosen from 1 choice
[    3.758141] usbcore: registered new interface driver hiddev
[    3.777791] usbcore: registered new interface driver usbhid
[    3.777796] usbhid: v2.6:USB HID core driver
[    3.872080] usb 2-2: USB disconnect, address 2
[    4.000066] usb 1-1: USB disconnect, address 2
[    4.608036] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    4.755442]  sdb:<6>usb 2-2: configuration #1 chosen from 1 choice
[    5.016031] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    5.192047] usb 1-1: configuration #1 chosen from 1 choice
[    5.208349] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input2
[    5.236460] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.0-1
[   18.008088] usb 2-2: USB disconnect, address 3
[  186.692027] usb 2-2: new full speed USB device using uhci_hcd and address 4
[  186.854331] usb 2-2: configuration #1 chosen from 1 choice

```
**sudo gedit /etc/udev/rules.d/026_ti_usb_3410.rules**
```

-->I typed the following codes in a text file

#TI USB **15eb**
SUBSYSTEM==?usb_device? ACTION==?add? \
SYSFS{idVendor}==?**0001**?,SYSFS{idProduct}==?**15eb**? \
SYSFS{bNumConfigurations}==?5? \
SYSFS{bConfigurationValue}==?1? \
RUN+=?/bin/sh -c ?echo 2 > /sys%p/device/bConfigurationValue??

-->When i saved & closed the text file,following error appears in terminal:

[B]I/O error : No such file or directory
I/O error : No such file or directory

** (gedit:5743): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.80IDWU': No such file or directory
[/B]
I ignored the error and continued.

```
**sudo gedit /etc/wvdial.conf**
```
-->I typed the following codes in a text file

[Dialer bsnl]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = username
Password = password
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap
nobsdcomp nodeflate

-->When i saved & closed the text file,following error appears in terminal:

[B]** (gedit:5759): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.K7RIWU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
[/B]
-->Again ignored the error and continued.

```
**sudo wvdial bsnl**
```
the output is:

--> Ignoring malformed input line: "nobsdcomp nodeflate"
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

Please help me..

---

### Post by rraj.be on 2009-06-25
Dinesh, Please post some useful information like outputs of 

> lsusb

dmesg

wvdial

ls /dev | grep tty

wvdialconf

so that we can help you by knowing whats the exact problem with your device.

---

### Post by balachandarlinks on 2009-06-25
try this and alter it for your need.

         [http://infoqueue.wordpress.com/tag/bsnl-data-card/](http://infoqueue.wordpress.com/tag/bsnl-data-card/)
         
                    cheers....

---

### Post by rraj.be on 2009-06-26
Fine dinesh.

First remove your usb cable.

type

```
sudo dmesg -c
```

now plug in the USB cable and post the output of 

```
dmesg
```

Further, post your reply VIA Reply and dont edit the same post again and again.

---

### Post by t0p on 2009-06-26
Some more advice for you!  I saw you edit /etc/wvdial.conf and tried to run wvdial, but I didn't see that you first ran **wvdialconf**.  This command will detect any modems connected to your machine.  So try it - the program will detect the modem (if it can) and write necessary config info to /etc/wvdial.conf.  It must be run as root, ie

```
sudo wvdialconf
```

---

### Post by ttsdinesh on 2009-06-26
ok let me try it and will tell you the status

---

### Post by ttsdinesh on 2009-06-26
Raj, i gave following command ```
 **sudo dmesg -c**
```
 I got following output:
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0004dfc0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004dfc0
[    0.000000] On node 0 totalpages: 319327
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 89256 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 4e000000:b0c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 316519
[    0.000000] Kernel command line: root=UUID=0b36088e-bb97-4a47-8337-56a9aac159f4 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2661.462 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1251728k/1277696k available (2572k kernel code, 25084k reserved, 1160k data, 424k init, 360192k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038329a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038329a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004023] Calibrating delay loop (skipped), value calculated using timer frequency.. 5322.92 BogoMIPS (lpj=10645848)
[    0.004053] Security Framework initialized
[    0.004068] SELinux:  Disabled at boot.
[    0.004105] AppArmor: AppArmor initialized
[    0.004123] Mount-cache hash table entries: 512
[    0.004424] Initializing cgroup subsys ns
[    0.004432] Initializing cgroup subsys cpuacct
[    0.004436] Initializing cgroup subsys memory
[    0.004467] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004471] CPU: L2 cache: 1024K
[    0.004475] CPU: Physical Processor ID: 0
[    0.004478] CPU: Processor Core ID: 0
[    0.004483] using mwait in idle threads.
[    0.004503] Checking 'hlt' instruction... OK.
[    0.023254] ACPI: Core revision 20080609
[    0.027077] ACPI: Checking initramfs for custom DSDT
[    0.394837] ENABLING IO-APIC IRQs
[    0.395162] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.434864] CPU0: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[    0.436027] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5323.41 BogoMIPS (lpj=10646822)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.520500] CPU1: Intel(R) Pentium(R) D  CPU 2.66GHz stepping 07
[    0.520524] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.524031] Measured 6391192640 cycles TSC warp between CPUs, turning off TSC clock.
[    0.524031] Marking TSC unstable due to check_tsc_sync_source failed
[    0.524047] Brought up 2 CPUs
[    0.524053] Total of 2 processors activated (10646.33 BogoMIPS).
[    0.524115] CPU0 attaching sched-domain:
[    0.524119]  domain 0: span 0-1 level CPU
[    0.524124]   groups: 0 1
[    0.524133] CPU1 attaching sched-domain:
[    0.524136]  domain 0: span 0-1 level CPU
[    0.524139]   groups: 1 0
[    0.524237] net_namespace: 840 bytes
[    0.524237] Booting paravirtualized kernel on bare hardware
[    0.524454] Time: 16:26:22  Date: 06/26/09
[    0.524504] NET: Registered protocol family 16
[    0.524543] EISA bus registered
[    0.524543] ACPI: bus type pci registered
[    0.524543] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=1
[    0.524543] PCI: Using configuration type 1 for base access
[    0.529217] ACPI: EC: Look up EC in DSDT
[    0.548596] ACPI: Interpreter enabled
[    0.548603] ACPI: (supports S0 S1 S3 S4 S5)
[    0.548633] ACPI: Using IOAPIC for interrupt routing
[    0.568256] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.568256] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff]
[    0.568472] pci 0000:00:01.0: supports D1
[    0.568530] PCI: 0000:00:0b.0 reg 10 io port: [e800, e8ff]
[    0.568540] PCI: 0000:00:0b.0 reg 14 32bit mmio: [febfec00, febfecff]
[    0.568590] pci 0000:00:0b.0: supports D1
[    0.568593] pci 0000:00:0b.0: supports D2
[    0.568596] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.568603] pci 0000:00:0b.0: PME# disabled
[    0.568646] PCI: 0000:00:0f.0 reg 10 io port: [ec00, ec07]
[    0.568655] PCI: 0000:00:0f.0 reg 14 io port: [e480, e483]
[    0.568664] PCI: 0000:00:0f.0 reg 18 io port: [e400, e407]
[    0.568674] PCI: 0000:00:0f.0 reg 1c io port: [e080, e083]
[    0.568683] PCI: 0000:00:0f.0 reg 20 io port: [e000, e00f]
[    0.568692] PCI: 0000:00:0f.0 reg 24 io port: [d800, d8ff]
[    0.568779] PCI: 0000:00:0f.1 reg 20 io port: [fc00, fc0f]
[    0.568880] PCI: 0000:00:10.0 reg 20 io port: [dc00, dc1f]
[    0.568911] pci 0000:00:10.0: supports D1
[    0.568914] pci 0000:00:10.0: supports D2
[    0.568916] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.568923] pci 0000:00:10.0: PME# disabled
[    0.568984] PCI: 0000:00:10.1 reg 20 io port: [d480, d49f]
[    0.569015] pci 0000:00:10.1: supports D1
[    0.569017] pci 0000:00:10.1: supports D2
[    0.569020] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.569026] pci 0000:00:10.1: PME# disabled
[    0.569086] PCI: 0000:00:10.2 reg 20 io port: [d400, d41f]
[    0.569117] pci 0000:00:10.2: supports D1
[    0.569120] pci 0000:00:10.2: supports D2
[    0.569122] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.569128] pci 0000:00:10.2: PME# disabled
[    0.569188] PCI: 0000:00:10.3 reg 20 io port: [d080, d09f]
[    0.569219] pci 0000:00:10.3: supports D1
[    0.569222] pci 0000:00:10.3: supports D2
[    0.569224] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.569230] pci 0000:00:10.3: PME# disabled
[    0.569267] PCI: 0000:00:10.4 reg 10 32bit mmio: [febfe800, febfe8ff]
[    0.569324] pci 0000:00:10.4: supports D1
[    0.569326] pci 0000:00:10.4: supports D2
[    0.569329] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.569335] pci 0000:00:10.4: PME# disabled
[    0.569424] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.569479] PCI: 0000:00:11.5 reg 10 io port: [ee00, eeff]
[    0.569536] pci 0000:00:11.5: supports D1
[    0.569538] pci 0000:00:11.5: supports D2
[    0.569609] PCI: 0000:01:00.0 reg 10 32bit mmio: [f0000000, f3ffffff]
[    0.569618] PCI: 0000:01:00.0 reg 14 32bit mmio: [fd000000, fdffffff]
[    0.569646] PCI: 0000:01:00.0 reg 30 32bit mmio: [feaf0000, feafffff]
[    0.569665] pci 0000:01:00.0: supports D1
[    0.569667] pci 0000:01:00.0: supports D2
[    0.572049] PCI: bridge 0000:00:01.0 32bit mmio: [fca00000, feafffff]
[    0.572055] PCI: bridge 0000:00:01.0 32bit mmio pref: [eff00000, f7efffff]
[    0.572067] bus 00 -> node 0
[    0.572082] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.572663] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.589039] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.589039] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.589039] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.589039] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.589133] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.592131] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.592354] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.592576] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.592672] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 6B, should be 5C [20080609]
[    0.592672] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.592672] pnp: PnP ACPI init
[    0.592672] ACPI: bus type pnp registered
[    0.608674] pnp: PnP ACPI: found 14 devices
[    0.608679] ACPI: ACPI bus type pnp unregistered
[    0.608684] PnPBIOS: Disabled by ACPI PNP
[    0.608713] PCI: Using ACPI for IRQ routing
[    0.616048] NET: Registered protocol family 8
[    0.616052] NET: Registered protocol family 20
[    0.616100] NetLabel: Initializing
[    0.616104] NetLabel:  domain hash size = 128
[    0.616106] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.616128] NetLabel:  unlabeled traffic allowed by default
[    0.617652] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.617655]    actual entries 65620
[    0.617867] AppArmor: AppArmor Filesystem Enabled
[    0.617891] ACPI: RTC can wake from S4
[    0.624081] system 00:09: ioport range 0xa00-0xa0f has been reserved
[    0.624086] system 00:09: ioport range 0x290-0x29f has been reserved
[    0.624090] system 00:09: ioport range 0xa20-0xa2f has been reserved
[    0.624093] system 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.624097] system 00:09: ioport range 0xa40-0xa4f has been reserved
[    0.624109] system 00:0a: ioport range 0x3e0-0x3e7 has been reserved
[    0.624113] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.624116] system 00:0a: ioport range 0x800-0x87f has been reserved
[    0.624120] system 00:0a: ioport range 0x400-0x41f has been reserved
[    0.624130] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.624135] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.624146] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.624150] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.624154] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.624158] system 00:0d: iomem range 0x100000-0x4dffffff could not be reserved
[    0.624162] system 00:0d: iomem range 0xff380000-0xffffffff has been reserved
[    0.659755] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.659759] pci 0000:00:01.0:   IO window: disabled
[    0.659767] pci 0000:00:01.0:   MEM window: 0xfca00000-0xfeafffff
[    0.659774] pci 0000:00:01.0:   PREFETCH window: 0x000000eff00000-0x000000f7efffff
[    0.659800] pci 0000:00:01.0: setting latency timer to 64
[    0.659806] bus: 00 index 0 io port: [0, ffff]
[    0.659810] bus: 00 index 1 mmio: [0, ffffffff]
[    0.659813] bus: 01 index 0 mmio: [0, 0]
[    0.659816] bus: 01 index 1 mmio: [fca00000, feafffff]
[    0.659819] bus: 01 index 2 mmio: [eff00000, f7efffff]
[    0.659821] bus: 01 index 3 mmio: [0, 0]
[    0.659839] NET: Registered protocol family 2
[    0.660054] Switched to high resolution mode on CPU 0
[    0.660576] Switched to high resolution mode on CPU 1
[    0.672117] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.672630] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.673567] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.674333] TCP: Hash tables configured (established 131072 bind 65536)
[    0.674338] TCP reno registered
[    0.680211] NET: Registered protocol family 1
[    0.680411] checking if image is initramfs... it is
[    1.450505] Freeing initrd memory: 7949k freed
[    1.452443] audit: initializing netlink socket (disabled)
[    1.452477] type=2000 audit(1246033582.448:1): initialized
[    1.458950] highmem bounce pool size: 64 pages
[    1.458963] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.463485] VFS: Disk quotas dquot_6.5.1
[    1.463651] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.463835] msgmni has been set to 1757
[    1.464060] io scheduler noop registered
[    1.464065] io scheduler anticipatory registered
[    1.464067] io scheduler deadline registered
[    1.464086] io scheduler cfq registered (default)
[    1.464112] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.464213] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message
[    1.464225] pci 0000:01:00.0: Boot video device
[    1.464867] isapnp: Scanning for PnP cards...
[    1.656511] Clocksource tsc unstable (delta = 2401384836 ns)
[    1.816658] isapnp: No Plug & Play device found
[    1.882700] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.882894] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.883111] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.884141] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.884694] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.888289] brd: module loaded
[    1.888427] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.888670] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.888674] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.888937] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.892722] mice: PS/2 mouse device common for all mice
[    1.892963] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.893008] rtc0: alarms up to one year, y3k
[    1.893280] EISA: Probing bus 0 at eisa.0
[    1.893329] EISA: Detected 0 cards.
[    1.893334] cpuidle: using governor ladder
[    1.893337] cpuidle: using governor menu
[    1.894188] TCP cubic registered
[    1.894236] Using IPI No-Shortcut mode
[    1.894596] registered taskstats version 1
[    1.894769]   Magic number: 13:26:440
[    1.894975] rtc_cmos 00:02: setting system clock to 2009-06-26 16:26:23 UTC (1246033583)
[    1.894980] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.894983] EDD information not available.
[    1.895536] Freeing unused kernel memory: 424k freed
[    1.895612] Write protecting the kernel text: 2576k
[    1.895660] Write protecting the kernel read-only data: 936k
[    1.923360] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.104823] fuse init (API version 7.9)
[    2.259208] ACPI:   ï¿½ FFFF0000, 0000 (r0                        0             0)
[    2.259229] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f7412150), AE_BAD_HEADER
[    2.259509] processor ACPI0007:00: registered as cooling_device0
[    2.259520] ACPI: Processor [CPU1] (supports 16 throttling states)
[    2.313997] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f74121e0), AE_ALREADY_EXISTS
[    2.314012] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    2.314210] processor ACPI0007:01: registered as cooling_device1
[    2.314218] ACPI: Processor [CPU2] (supports 16 throttling states)
[    2.318410] thermal LNXTHERM:01: registered as thermal_zone0
[    2.318698] ACPI: Thermal Zone [THRM] (30 C)
[    2.717363] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.717411] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    2.717419] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[    2.720552] No dock devices found.
[    2.764450] SCSI subsystem initialized
[    2.851242] libata version 3.00 loaded.
[    2.851360] usbcore: registered new interface driver usbfs
[    2.851411] usbcore: registered new interface driver hub
[    2.851507] usbcore: registered new device driver usb
[    2.851651] 8139too Fast Ethernet driver 0.9.28
[    2.851718] 8139too 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.852640] eth0: RealTek RTL8139 at 0xe800, 00:16:ec:eb:75:a2, IRQ 17
[    2.852644] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    2.860564] pata_acpi 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.860660] pata_acpi 0000:00:0f.0: PCI INT B disabled
[    2.860688] pata_acpi 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.860753] pata_acpi 0000:00:0f.1: PCI INT A disabled
[    2.865188] pata_via 0000:00:0f.1: version 0.3.3
[    2.865206] pata_via 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.871137] scsi0 : pata_via
[    2.871357] scsi1 : pata_via
[    2.874646] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    2.874651] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    2.882925] USB Universal Host Controller Interface driver v3.0
[    3.200526] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H20N, 1.01, max UDMA/33
[    3.216403] ata2.00: configured for UDMA/33
[    3.218041] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H20N 1.01 PQ: 0 ANSI: 5
[    3.218462] sata_via 0000:00:0f.0: version 2.3
[    3.218487] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.218552] sata_via 0000:00:0f.0: routed to hard irq line 5
[    3.218921] scsi2 : sata_via
[    3.219038] scsi3 : sata_via
[    3.221991] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe480 bmdma 0xe000 irq 20
[    3.221996] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 20
[    3.358973] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[    3.377640] Driver 'sr' needs updating - please use bus_type methods
[    3.382864] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.382871] Uniform CD-ROM driver Revision: 3.20
[    3.383030] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.424028] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.588355] ata3.00: ATA-7: WDC WD800BD-22LRA0, 06.01D06, max UDMA/133
[    3.588360] ata3.00: 156301488 sectors, multi 16: LBA48 
[    3.596363] ata3.00: configured for UDMA/133
[    3.800026] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.964367] ata4.00: ATA-7: ST3250310AS, 3.AAF, max UDMA/133
[    3.964372] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.980363] ata4.00: configured for UDMA/133
[    3.980543] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800BD-22LR 06.0 PQ: 0 ANSI: 5
[    3.980862] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.981753] scsi 3:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    3.981937] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    3.982104] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.982120] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.982189] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.982235] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000dc00
[    3.982403] usb usb1: configuration #1 chosen from 1 choice
[    3.982449] hub 1-0:1.0: USB hub found
[    3.982463] hub 1-0:1.0: 2 ports detected
[    4.189214] uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.189232] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    4.189277] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    4.189309] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d480
[    4.189467] usb usb2: configuration #1 chosen from 1 choice
[    4.189514] hub 2-0:1.0: USB hub found
[    4.189528] hub 2-0:1.0: 2 ports detected
[    4.300026] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    4.396333] uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.396349] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    4.396390] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    4.396419] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d400
[    4.396565] usb usb3: configuration #1 chosen from 1 choice
[    4.396611] hub 3-0:1.0: USB hub found
[    4.396624] hub 3-0:1.0: 2 ports detected
[    4.475697] usb 1-1: configuration #1 chosen from 1 choice
[    4.604299] uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.604313] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    4.604355] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    4.604385] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000d080
[    4.604534] usb usb4: configuration #1 chosen from 1 choice
[    4.604580] hub 4-0:1.0: USB hub found
[    4.604595] hub 4-0:1.0: 2 ports detected
[    4.813009] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    4.813034] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    4.813085] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    4.813143] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebfe800
[    4.824030] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.824216] usb usb5: configuration #1 chosen from 1 choice
[    4.824263] hub 5-0:1.0: USB hub found
[    4.824277] hub 5-0:1.0: 8 ports detected
[    4.864081] usb 1-1: USB disconnect, address 2
[    5.090253] Driver 'sd' needs updating - please use bus_type methods
[    5.090485] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.090513] sd 2:0:0:0: [sda] Write Protect is off
[    5.090517] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.090887] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.091016] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.091046] sd 2:0:0:0: [sda] Write Protect is off
[    5.091050] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.091101] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.091108]  sda: sda1 sda2 sda3 sda4 < >
[    5.129304] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.129463] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    5.129505] sd 3:0:0:0: [sdb] Write Protect is off
[    5.129509] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.129576] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.129691] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    5.129727] sd 3:0:0:0: [sdb] Write Protect is off
[    5.129731] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.129796] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.129803]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 >
[    5.194129] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.352069] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    5.527577] usb 1-1: configuration #1 chosen from 1 choice
[    5.531074] usbcore: registered new interface driver hiddev
[    5.543723] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input2
[    5.544231] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.0-1
[    5.544265] usbcore: registered new interface driver usbhid
[    5.544271] usbhid: v2.6:USB HID core driver
[   10.637971] udevd version 124 started
[   11.082154] Linux agpgart interface v0.103
[   11.179201] agpgart: Detected VIA VT3314 chipset
[   11.184731] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   11.203121] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.258705] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.364255] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.380546] ACPI: Power Button (FF) [PWRF]
[   11.380817] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   11.412552] ACPI: Sleep Button (CM) [SLPB]
[   11.412721] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   11.444568] ACPI: Power Button (CM) [PWRB]
[   11.707399] parport_pc 00:08: reported by Plug and Play ACPI
[   11.707482] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.237880] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.288049] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   13.288214] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   14.706475] lp0: using parport0 (interrupt-driven).
[   16.581365] type=1505 audit(1246013798.091:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4115
[   16.803102] type=1505 audit(1246013798.311:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4120
[   16.803465] type=1505 audit(1246013798.311:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4120
[   16.972709] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.794947] ACPI: WMI: Mapper loaded
[   18.811523] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.884991] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.885004] apm: disabled - APM is not SMP safe.
[   19.039434] ppdev: user-space parallel port driver
[   20.840607] Bluetooth: Core ver 2.13
[   20.841061] NET: Registered protocol family 31
[   20.841069] Bluetooth: HCI device and connection manager initialized
[   20.841075] Bluetooth: HCI socket layer initialized
[   20.861918] Bluetooth: L2CAP ver 2.11
[   20.861928] Bluetooth: L2CAP socket layer initialized
[   20.875413] Bluetooth: SCO (Voice Link) ver 0.6
[   20.875424] Bluetooth: SCO socket layer initialized
[   20.900184] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.900197] Bluetooth: BNEP filters: protocol multicast
[   20.937031] Bridge firewalling registered
[   20.937608] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   20.987007] Bluetooth: RFCOMM socket layer initialized
[   20.988416] Bluetooth: RFCOMM TTY layer initialized
[   20.988426] Bluetooth: RFCOMM ver 1.10
[   23.196784] [drm] Initialized drm 1.1.0 20060810
[   23.219180] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.223123] [drm] Initialized via 2.11.1 20070202 on minor 0
[   23.247661] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   23.247707] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   23.247813] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   25.121200] eth0: link down



[B]-->Again i pluged my modem and gave ```
dmesg
```
Now the output is:[/B]

[  111.146617] type=1503 audit(1246013892.655:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5553/net/" pid=5553 profile="/usr/sbin/cupsd"
[  111.268541] NET: Registered protocol family 10
[  111.270813] lo: Disabled Privacy Extensions
[  111.273276] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  111.274598] type=1503 audit(1246013892.783:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274628] type=1503 audit(1246013892.783:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274658] type=1503 audit(1246013892.783:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274667] type=1503 audit(1246013892.783:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274675] type=1503 audit(1246013892.783:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274684] type=1503 audit(1246013892.783:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274693] type=1503 audit(1246013892.783:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274702] type=1503 audit(1246013892.783:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5553 profile="/usr/sbin/cupsd"
[  111.274850] type=1503 audit(1246013892.783:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5553/net/dev" pid=5553 profile="/usr/sbin/cupsd"
[  111.504307] ppdev0: registered pardevice
[  111.552371] ppdev0: unregistered pardevice
[  112.088572] ppdev0: registered pardevice
[  112.136325] ppdev0: unregistered pardevice
[  112.228141] ppdev0: registered pardevice
[  112.276034] ppdev0: unregistered pardevice
[  191.240026] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  191.402898] usb 2-2: configuration #1 chosen from 1 choice

---

### Post by ttsdinesh on 2009-06-28
ON your advice i gave the following command:
[code]sudo wvdialconf[\code]
 the output is:
dinesh@HOME:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

What shall i have to do now?

---

### Post by ttsdinesh on 2009-06-29
I gave the following command and got:
dinesh@HOME:~$ **sudo gedit /etc/udev/rules.d/50-cdma.rules**

** (gedit:6022): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.FEDHWU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
dinesh@HOME:~$ 


What migth be the reason?

---

### Post by rraj.be on 2009-06-29
> **ttsdinesh said:**
> I gave the following command and got:
dinesh@HOME:~$ **sudo gedit /etc/udev/rules.d/50-cdma.rules**

** (gedit:6022): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.FEDHWU': No such file or directory


This is really an unusual error.

You can try an alternative solution like

1) Press Alt+F2

2) Type gksu nautilus

3) Enter password

4) navigate to /etc/udev/rules.d/ and create a new file as you wish and enter the contents.

hope it helps buddy.

---

