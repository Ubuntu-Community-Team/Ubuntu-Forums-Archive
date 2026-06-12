---
title: "cannot use dynamode 11g usb adaptor in ubuntu - can anyone help please?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by clumsytheclown on 2009-06-11
dear all,

i am trying to switch from my dodgy wireless sweex card (the internet connection keeps interrupting; the card has half come apart though) to a usb stick for wireless connection; i have bought the dynamode 802.11g usb adapter (wl-700g-m). i couldn't even open the install wizard, then i installed wine so it came up, but at the second slide it asks me to insert the usb and click 'next'. when i do that, it just keeps asking me again to insert it. i have tried inserting the usb stick before starting the computer, after starting it etc but nothing works - it just won't recognise it.

does anyone have any experience how to get this particular stick to work? it would be great if you could help :) (please step by step, as i'm not familiar with many what many of you probably deem to be easy commands). if you need any more info, please let me know. i run ubuntu heron 8.04

many thanks,

svenja

---

### Post by j-d33zy on 2009-06-12
I dont know if there is a driver built into linux for that specific usb dongle, but there are drivers for many. did you try just getting the driver for linux? It may already be installed, just connect the dongle, wait for about 20 seconds or so to recognise it if it needs to, then click on youir network manager and see if it finds it. And if you are going to use windows drivers, you shouldn't try to do it through wine, you should try to use ndiswrapper. it is a program that "unwraps" the windows drivers so you can use them on linux.

---

### Post by anewguy on 2009-06-12
First, let me correct one thing for you - you don't install the Windows drivers via Wine - that won't work.  What we would need you to do first is to open a terminal window and run the following commands and post the output back here.  We can go from there.  Be sure your USB adapter is plugged in when you do these.

lshw -C network

lsusb


If nothing else, we can have you use ndiswrapper to install the Windows drivers, but post the output of the above first.

Dave :)

---

### Post by clumsytheclown on 2009-06-13
Dave - cheers!

I posted the commands suggested and the outcome is:

svenja@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:a0:cc:dc:81:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:16:0a:00:0a:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=prism54pci ip=10.0.0.2 latency=64 maxlatency=28 mingnt=10 module=p54pci multicast=yes wireless=IEEE 802.11g
svenja@ubuntu:~$ lsusb
Bus 004 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 004 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Does that give you an idea of how to fix the problem?

Many thanks,

Svenja

---

### Post by clumsytheclown on 2009-06-13
j-d33zy - cheers for replying - i have installed the programme to run the windows driver (not sure where to search for the linux driver - cannot find network manager) but still cannot open the installation software with it or find the usb stick on my computer (even though it is definitely running, green light on)

any more ideas?

many thanks,

---

### Post by TeoBigusGeekus on 2009-06-13
Wicd!!!
When it comes to wireless, always use wicd.
```
sudo apt-get install wicd
```

---

### Post by cariboo on 2009-06-13
There is a driver listed as prism54pci, that looks like it is for your old device, you may have to blacklist it before your new device is detected properly. To blacklist the driver you need to edit /etc/modprobe.d/blacklist. to open /etc/modprobe.d/blacklist, press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

and add prism54pci to the bottom of the file. If you can I would suggest removing the old adapter all together.

Once you have blacklisted the old driver, you can check to make sure the new device is detected properly after you have plugged the device in by opneing a terminal and typing:

```
dmesg | tail -n15
```

Could you paste the output of the above command in your next post

---

### Post by clumsytheclown on 2009-06-14
Thanks cariboo907, dont think this has worked - not even sure if the blacklisting of the driver has worked, since I could just put the old wireless card back in and it worked again  - otherwise I probably wouldn't be writing this, since there was no sign of the computer recognising the new wireless usb.

so, the results are

svenja@ubuntu:~$ dmesg tail-n15
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dff8000 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff0ffff (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 122864) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122864
[    0.000000]   HighMem    122864 ->   122864
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122864
[    0.000000] On node 0 totalpages: 122864
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117841 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA340 checksum 0
[    0.000000] ACPI: RSDP 000FA340, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1DFF0000, 0028 (r1 AMIINT SiS645XX       10 MSFT  100000B)
[    0.000000] ACPI: FACP 1DFF0030, 0081 (r1 AMIINT SiS645XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 1DFF0110, 3283 (r1     UW Elfin2__     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1DFF8000, 0040
[    0.000000] ACPI: DMI detected: Fujitsu Siemens
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121905
[    0.000000] Kernel command line: root=UUID=f53cd39e-a4fa-4b0d-84ea-b7d5f87eda6a ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (013cd000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1804.106 MHz processor.
[   16.301910] Console: colour VGA+ 80x25
[   16.301917] console [tty0] enabled
[   16.302401] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.302838] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.318844] Memory: 475140k/491456k available (2177k kernel code, 15708k reserved, 1006k data, 368k init, 0k highmem)
[   16.318858] virtual kernel memory layout:
[   16.318860]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.318861]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.318863]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   16.318864]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[   16.318866]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.318867]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   16.318869]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   16.318874] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.318934] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.398883] Calibrating delay using timer specific routine.. 3612.12 BogoMIPS (lpj=7224242)
[   16.398923] Security Framework initialized
[   16.398933] SELinux:  Disabled at boot.
[   16.398955] AppArmor: AppArmor initialized
[   16.398963] Failure registering capabilities with primary security module.
[   16.398977] Mount-cache hash table entries: 512
[   16.399184] Initializing cgroup subsys ns
[   16.399192] Initializing cgroup subsys cpuacct
[   16.399210] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
[   16.399231] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   16.399235] CPU: L2 cache: 512K
[   16.399240] CPU: Hyper-Threading is disabled
[   16.399243] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000 00000000
[   16.399263] Compat vDSO mapped to ffffe000.
[   16.399284] Checking 'hlt' instruction... OK.
[   16.415464] SMP alternatives: switching to UP code
[   16.417873] Freeing SMP alternatives: 11k freed
[   16.418082] Early unpacking initramfs... done
[   16.881635] ACPI: Core revision 20070126
[   16.881734] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.883853] ACPI: setting ELCR to 0200 (from 0c20)
[   17.261868] CPU0: Intel Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz stepping 07
[   17.261880] SMP motherboard not detected.
[   17.261884] Local APIC not detected. Using dummy APIC emulation.
[   17.261964] Brought up 1 CPUs
[   17.261997] CPU0 attaching sched-domain:
[   17.262002]  domain 0: span 01
[   17.262005]   groups: 01
[   17.262387] net_namespace: 64 bytes
[   17.262403] Booting paravirtualized kernel on bare hardware
[   17.263235] Time: 21:48:47  Date: 06/14/09
[   17.263281] NET: Registered protocol family 16
[   17.263640] EISA bus registered
[   17.263662] ACPI: bus type pci registered
[   17.266072] PCI: PCI BIOS revision 2.10 entry at 0xfda41, last bus=1
[   17.266077] PCI: Using configuration type 1
[   17.266096] Setting up standard PCI resources
[   17.291702] ACPI: EC: Look up EC in DSDT
[   17.296235] ACPI: Interpreter enabled
[   17.296242] ACPI: (supports S0 S3 S4 S5)
[   17.296264] ACPI: Using PIC for interrupt routing
[   17.297935] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   17.302643] ACPI: EC: GPE = 0x2, I/O: command/status = 0x66, data = 0x62
[   17.302650] ACPI: EC: driver started in interrupt mode
[   17.302727] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.303011] Enabling SiS 96x SMBus.
[   17.304161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.374940] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   17.375088] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   17.375229] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   17.375372] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[   17.375515] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[   17.375660] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10 11 12 14 15)
[   17.375801] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *10 11 12 14 15)
[   17.375942] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   17.376118] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.376172] pnp: PnP ACPI init
[   17.376186] ACPI: bus type pnp registered
[   17.378303] pnp: PnP ACPI: found 7 devices
[   17.378307] ACPI: ACPI bus type pnp unregistered
[   17.378314] PnPBIOS: Disabled by ACPI PNP
[   17.378725] PCI: Using ACPI for IRQ routing
[   17.378730] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.393904] NET: Registered protocol family 8
[   17.393907] NET: Registered protocol family 20
[   17.394031] AppArmor: AppArmor Filesystem Enabled
[   17.397884] Time: tsc clocksource has been installed.
[   17.436646] PCI: Bridge: 0000:00:01.0
[   17.436653]   IO window: a000-afff
[   17.436661]   MEM window: dfe00000-dfefffff
[   17.436667]   PREFETCH window: cfc00000-dfcfffff
[   17.436676] PCI: Bus 2, cardbus bridge: 0000:00:08.0
[   17.436679]   IO window: 00001000-000010ff
[   17.436685]   IO window: 00001400-000014ff
[   17.436691]   PREFETCH window: 20000000-23ffffff
[   17.436698]   MEM window: 24000000-27ffffff
[   17.436949] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   17.436955] PCI: setting IRQ 10 as level-triggered
[   17.436959] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   17.436970] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.436991] NET: Registered protocol family 2
[   17.473947] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   17.474337] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   17.474462] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   17.474583] TCP: Hash tables configured (established 16384 bind 16384)
[   17.474587] TCP reno registered
[   17.486026] checking if image is initramfs... it is
[   17.937372] Switched to high resolution mode on CPU 0
[   18.397209] Freeing initrd memory: 7322k freed
[   18.398062] audit: initializing netlink socket (disabled)
[   18.398091] audit(1245016127.712:1): initialized
[   18.401523] VFS: Disk quotas dquot_6.5.1
[   18.401653] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.401893] io scheduler noop registered
[   18.401897] io scheduler anticipatory registered
[   18.401900] io scheduler deadline registered
[   18.401920] io scheduler cfq registered (default)
[   19.971073] Boot video device is 0000:01:00.0
[   19.971542] isapnp: Scanning for PnP cards...
[   20.325440] isapnp: No Plug & Play device found
[   20.373546] Real Time Clock Driver v1.12ac
[   20.373714] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.374994] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   20.375013] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   20.376078] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.376195] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.376370] PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.381935] i8042.c: Detected active multiplexing controller, rev 1.0.
[   20.383081] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.383089] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.383093] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.383097] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.383100] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.390752] mice: PS/2 mouse device common for all mice
[   20.390949] EISA: Probing bus 0 at eisa.0
[   20.390960] Cannot allocate resource for EISA slot 1
[   20.390992] EISA: Detected 0 cards.
[   20.390997] cpuidle: using governor ladder
[   20.391000] cpuidle: using governor menu
[   20.391180] NET: Registered protocol family 1
[   20.391239] Using IPI No-Shortcut mode
[   20.391293] registered taskstats version 1
[   20.391446]   Magic number: 13:68:854
[   20.391580]   hash matches device ptyv6
[   20.391663] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.391665] EDD information not available.
[   20.392263] Freeing unused kernel memory: 368k freed
[   20.395436] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   21.837154] fuse init (API version 7.9)
[   22.048809] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.048821] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.057241] ACPI: Thermal Zone [THRM] (75 C)
[   22.988760] SCSI subsystem initialized
[   23.081601] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   23.081610] PCI: setting IRQ 5 as level-triggered
[   23.081615] ACPI: PCI Interrupt 0000:00:02.3[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   23.133479] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[dfffb000-dfffb7ff]  Max Packet=[2048]  IR/IT contexts=[4/6]
[   23.199551] libata version 3.00 loaded.
[   23.216024] usbcore: registered new interface driver usbfs
[   23.216068] usbcore: registered new interface driver hub
[   23.247562] usbcore: registered new device driver usb
[   23.271465] sis900.c: v1.08.10 Apr. 2 2006
[   23.303453] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.333207] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   23.333215] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   23.334870] 0000:00:04.0: ICS LAN PHY transceiver found at address 1.
[   23.348749] 0000:00:04.0: Using transceiver found at address 1 as default
[   23.350261] eth0: SiS 900 PCI Fast Ethernet at 0xcc00, IRQ 10, 00:a0:cc:dc:81:ec
[   23.355001] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   23.355010] PCI: setting IRQ 11 as level-triggered
[   23.355014] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   23.355036] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   23.355622] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   23.355652] ohci_hcd 0000:00:03.0: irq 11, io mem 0xdfff7000
[   23.413570] usb usb1: configuration #1 chosen from 1 choice
[   23.413615] hub 1-0:1.0: USB hub found
[   23.413629] hub 1-0:1.0: 2 ports detected
[   23.515630] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[   23.515638] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[   23.515664] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   23.515709] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   23.515732] ohci_hcd 0000:00:03.1: irq 10, io mem 0xdfff8000
[   23.573348] usb usb2: configuration #1 chosen from 1 choice
[   23.573394] hub 2-0:1.0: USB hub found
[   23.573407] hub 2-0:1.0: 2 ports detected
[   23.675396] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   23.675405] ACPI: PCI Interrupt 0000:00:03.2[C] -> Link [LNKG] -> GSI 10 (level, low) -> IRQ 10
[   23.675432] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   23.675474] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   23.675496] ohci_hcd 0000:00:03.2: irq 10, io mem 0xdfff9000
[   23.733180] usb usb3: configuration #1 chosen from 1 choice
[   23.733228] hub 3-0:1.0: USB hub found
[   23.733242] hub 3-0:1.0: 2 ports detected
[   23.818885] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   23.835461] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   23.835469] ACPI: PCI Interrupt 0000:00:03.3[D] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[   23.835489] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   23.835540] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   23.835593] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   23.835606] ehci_hcd 0000:00:03.3: irq 5, io mem 0xdfffa000
[   24.010613] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.010833] usb usb4: configuration #1 chosen from 1 choice
[   24.010875] hub 4-0:1.0: USB hub found
[   24.010887] hub 4-0:1.0: 6 ports detected
[   24.115334] pata_sis 0000:00:02.5: version 0.5.2
[   24.117710] scsi0 : pata_sis
[   24.119658] scsi1 : pata_sis
[   24.120415] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   24.120420] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   24.282876] ata1.00: ATA-5: IC25N040ATCS04-0, CA4OA71A, max UDMA/100
[   24.282883] ata1.00: 78140160 sectors, multi 16: LBA 
[   24.298829] ata1.00: configured for UDMA/100
[   24.406161] usb 1-1: device not accepting address 2, error -62
[   24.602125] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000000000000000]
[   24.618194] ata2.00: ATAPI: Slimtype COMBO LSC-24082K, JKU5, max UDMA/33
[   24.790023] ata2.00: configured for UDMA/33
[   24.790240] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS04-0 CA4O PQ: 0 ANSI: 5
[   24.792752] scsi 1:0:0:0: CD-ROM            Slimtype COMBO LSC-24082K JKU5 PQ: 0 ANSI: 5
[   24.815720] Driver 'sd' needs updating - please use bus_type methods
[   24.815876] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   24.815899] sd 0:0:0:0: [sda] Write Protect is off
[   24.815903] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.815937] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.816021] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   24.816040] sd 0:0:0:0: [sda] Write Protect is off
[   24.816044] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.816075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.816082]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.829726] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   24.838310]  sda1 sda2 < sda5 >
[   24.870427] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.881411] sr0: scsi3-mmc drive: 15x/24x writer cd/rw xa/form2 cdda tray
[   24.881421] Uniform CD-ROM driver Revision: 3.20
[   24.881497] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.881694] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.881724] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   24.980159] usb 4-1: configuration #1 chosen from 1 choice
[   25.190667] Attempting manual resume
[   25.190674] swsusp: Resume From Partition 8:5
[   25.190677] PM: Checking swsusp image.
[   25.190964] PM: Resume from disk failed.
[   25.245640] kjournald starting.  Commit interval 5 seconds
[   25.245666] EXT3-fs: mounted filesystem with ordered data mode.
[   25.924474] Clocksource tsc unstable (delta = -288245035 ns)
[   25.928467] Time: acpi_pm clocksource has been installed.
[   35.982052] Linux agpgart interface v0.102
[   36.225882] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.367139] agpgart: Detected SiS chipset - id:1616
[   36.372579] agpgart: AGP aperture is 64M @ 0xe0000000
[   36.445597] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.513484] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   37.492472] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   37.565487] Yenta: CardBus bridge found at 0000:00:08.0 [1734:101f]
[   37.565522] Yenta O2: res at 0x94/0xD4: 00/ea
[   37.565525] Yenta O2: enabling read prefetch/write burst
[   37.605566] input: Power Button (FF) as /devices/virtual/input/input3
[   37.616140] ACPI: Power Button (FF) [PWRF]
[   37.616415] input: Lid Switch as /devices/virtual/input/input4
[   37.616505] ACPI: Lid Switch [LID]
[   37.616618] input: Power Button (CM) as /devices/virtual/input/input5
[   37.636118] ACPI: Power Button (CM) [PWRB]
[   37.636344] input: Sleep Button (CM) as /devices/virtual/input/input6
[   37.648087] ACPI: Sleep Button (CM) [SLPB]
[   37.692709] Yenta: ISA IRQ mask 0x0098, PCI irq 10
[   37.692717] Socket status: 30000007
[   39.130610] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   39.339655] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x848a1, caps: 0x0/0x0
[   39.376289] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input7
[   39.957521] intel8x0_measure_ac97_clock: measured 55410 usecs
[   39.957528] intel8x0: clocking to 48000
[   39.981737] ACPI: AC Adapter [AC0] (on-line)
[   40.093476] ACPI: Battery Slot [BAT0] (battery present)
[   42.792915] cs: IO port probe 0x100-0x3af: clean.
[   42.794962] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f 0x4d0-0x4d7
[   42.795792] cs: IO port probe 0x820-0x8ff: excluding 0x828-0x877 0x898-0x89f
[   42.796139] cs: IO port probe 0xc00-0xcf7: clean.
[   42.797014] cs: IO port probe 0xa00-0xaff: clean.
[   43.150407] loop: module loaded
[   43.233638] lp: driver loaded but no devices found
[   43.554683] Adding 1413680k swap on /dev/sda5.  Priority:-1 extents:1 across:1413680k
[   44.092343] EXT3 FS on sda1, internal journal
[   44.932871] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.502852] No dock devices found.
[   47.169835] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.169846] apm: overridden by ACPI.
[   47.319091] ppdev: user-space parallel port driver
[   47.444453] audit(1245016163.344:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4739 profile="/usr/sbin/cupsd" namespace="default"
[   48.558265] eth0: Media Link Off
[   48.689551] Bluetooth: Core ver 2.11
[   48.690710] NET: Registered protocol family 31
[   48.690718] Bluetooth: HCI device and connection manager initialized
[   48.690725] Bluetooth: HCI socket layer initialized
[   48.721538] Bluetooth: L2CAP ver 2.9
[   48.721547] Bluetooth: L2CAP socket layer initialized
[   48.820746] Bluetooth: RFCOMM socket layer initialized
[   48.820775] Bluetooth: RFCOMM TTY layer initialized
[   48.820778] Bluetooth: RFCOMM ver 1.8
[   63.164018] NET: Registered protocol family 10
[   63.164847] lo: Disabled Privacy Extensions
[   63.165882] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.072624] cdrom: sr0: mrw address space DMA selected
[   81.279788] cdrom: sr0: mrw address space DMA selected
[   82.558857] UDF-fs: No VRS found
[   82.595978] ISO 9660 Extensions: Microsoft Joliet Level 3
[   82.599365] ISOFS: changing to secondary root
svenja@ubuntu:~$ 

any ideas?

thanks a lot for your help,

svenja

---

