---
title: "Wireless driver (proprietary required?)"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by ni ni on 2010-06-15
Hello all,

absolute beginner here.  My laptop has a wireless card.  Ubuntu doesn't know that.  How can i get a driver?

I don't know any of the commands to give the information about my wireless card.

```
lspci | grep -i net
```  gives me:

```
niamh@niamh-laptop:~$ lspci | grep -i net
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
niamh@niamh-laptop:~$
```

this is what i know about my laptop:
Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based

it's very old :-(


Thanks in advance xxx:KS:KS:KS

---

### Post by Bachstelze on 2010-06-15
Does System > Administration > Hardware Drivers say anything? If it doesn't, you can always try ndiswrapper.

*EDIT: btw, what you copied is your wired NIC. Your wireless iis somewhere else.*

---

### Post by ni ni on 2010-06-15
No, it's absolutely blank.

---

### Post by Bachstelze on 2010-06-15
Paste the full lspci listing, also with -nn:

```
lspci -nn
```

As I said, the VIA is your wired NIC.

---

### Post by mapes12 on 2010-06-15
In my experience ndiswrapper always regresses to a point of being unusable. Save your sanity and get hold of a Linux supported wifi adapter. Either USB or PCMCIA. I go for the latter. Here's a good source:- [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

OK, it means investing in new hardware but hey, you're getting the best OS on the planet for free!

---

### Post by Bachstelze on 2010-06-15
> **mapes12 said:**
> In my experience ndiswrapper always regresses to a point of being unusable;

In my experience, it does not. It even works better than the native drivers for some chips.

---

### Post by ni ni on 2010-06-15
[PHP]niamh@niamh-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:0259]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:1259]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 CPU Host Bridge [1106:2259]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:3259]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:4259]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN333/CN400/PM880 Host Bridge [1106:7259]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:06.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev ff)
00:09.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] [1106:3118] (rev 02)
niamh@niamh-laptop:~$[/PHP]

---

### Post by ni ni on 2010-06-15
i went back to System > Administration > Hardware Drivers and it let me get the proprietary driver, but i still only have the option for 'Auto eth0' :-(

---

### Post by Bachstelze on 2010-06-15
You have an Atheros chip, it should work out of the box. What does this return?

```
sudo iwconfig
```

---

### Post by ni ni on 2010-06-15
it returns:
```
lo     no wireless extensions

eth0    no wireless extensions
```

---

### Post by Bachstelze on 2010-06-15
That is very weird, an AR2413 should definitely work OOTB. Are you using an older release of Ubuntu, by any chance?

---

### Post by ni ni on 2010-06-15
no it's Lucid Lynx.

is there a way to disable wireless?

I just turned it on one day and there was no option for wireless.

---

### Post by Bachstelze on 2010-06-15
Yeah, older laptops sometimes have a switch of sorts that is used to disable the wireless card, that's probably why Ubuntu can't see yours. Also have a look in your BIOS, though changes there generally don't happen accidentally.

---

### Post by ni ni on 2010-06-15
Are we talking about a physical switch????

There certainly isn't one on the outside!

---

### Post by marcoftheknight on 2010-06-15
You should use this code to dignose your networking settings mroe acurately

Thanks

sudo lshw -C *network*

---

### Post by Bachstelze on 2010-06-15
> **ni ni said:**
> Are we talking about a physical switch????

There certainly isn't one on the outside!

Yes, so I guess it's not that either... Paste the output of [font=monospace]dmesg[/font], then. Yes, it's big, but paste it all, maybe we'll see a problem there.

---

### Post by sthilaire on 2010-06-16
Just to add 2 cents - I have had a bummer of a time with Ubuntu 10.04 and wireless drivers.  I have an IBM laptop that I have been using with a PCMCIA card since Ubuntu 7.  Has always worked.  When I upgraded it to 10.04 - the wireless card was no longer picked up.  I went back to v8.1 (clean install) and it worked just fine without any additional work.

A newer DELL laptop (Latitude) I have with an internal card - also did not work with 10.0.4 with a fresh install.  I needed to be WIRED - get the latest updates - then load a hardware driver (via the Ubuntu - you need a driver helper)  For the DELL, I needed to load the Broadcom B43 wireless driver.

The older IBM with the PCMCIA "b" network adapter - I didn't go back to try and fix.  Determined I didn't really need Ubuntu 10.04 - Version 8.1 and Chrome do most of what I need on that one.

-- Tim

---

### Post by harry003 on 2010-06-16
I went through an enormous amount of pain recently. I bought a new laptop with an Atheros wireless card and Windows 7 pre-installed.

After much work I discovered that the newer drivers did not accept my card. When I found a Windows XP driver and used ndiswrapper to install it, it worked perfectly.

---

### Post by pous on 2010-06-16
i just recently solved a similar issue aprox a month after upgrading to 10.04, although mine was a broadcom chip, i finally after tweaking a lot of things and unistalling and installing others, went though a ndiswraper (sp?) tutorial here right at the very top of the wireless section of the forum and got it recognised... after that for some reason the wi-fi light didnt turn on, which was solved by going in bios and turning my wireless on again.... hope this is of any use.

---

### Post by mapes12 on 2010-06-17
> Are we talking about a physical switch????

There certainly isn't one on the outside!Take a look at the keyboard. Across the top are the "F" keys. One of these may have a blue icon on it (or similar colour) indicating wireless. Then, on my laptop, there is a key in the same colour labelled "Fn" in the bottom L/H corner. Holding down the FN key and then pressing the F key with the wireless symbol toggles the wireless device on and off.

---

### Post by ni ni on 2010-06-21
thanks for all the help.

output of dmesg: [PHP][    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113674
[    0.000000] Kernel command line: root=UUID=62b506f1-3049-46c3-88ef-ff082a960ea8 ro quiet splash 
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2293420 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 435924k/458684k available (4673k kernel code, 22168k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdc7ef000 - 0xff7fe000   ( 560 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdbfef000   ( 447 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1592.557 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3185.11 BogoMIPS (lpj=6370228)
[    0.008032] Security Framework initialized
[    0.008067] AppArmor: AppArmor initialized
[    0.008078] Mount-cache hash table entries: 512
[    0.008253] Initializing cgroup subsys ns
[    0.008259] Initializing cgroup subsys cpuacct
[    0.008264] Initializing cgroup subsys memory
[    0.008277] Initializing cgroup subsys devices
[    0.008280] Initializing cgroup subsys freezer
[    0.008284] Initializing cgroup subsys net_cls
[    0.008316] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008320] CPU: L2 cache: 1024K
[    0.008327] mce: CPU supports 5 MCE banks
[    0.008339] CPU0: Thermal monitoring enabled (TM1)
[    0.008352] Performance Events: p6 PMU driver.
[    0.008375] ... version:                0
[    0.008377] ... bit width:              32
[    0.008380] ... generic registers:      2
[    0.008382] ... value mask:             00000000ffffffff
[    0.008385] ... max period:             000000007fffffff
[    0.008388] ... fixed-purpose events:   0
[    0.008390] ... event mask:             0000000000000003
[    0.008397] Checking 'hlt' instruction... OK.
[    0.025187] SMP alternatives: switching to UP code
[    0.034144] Freeing SMP alternatives: 19k freed
[    0.034161] ACPI: Core revision 20090903
[    0.044013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044024] ftrace: allocating 21771 entries in 43 pages
[    0.048121] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052352] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.092070] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (3185.11 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time:  6:27:12  Date: 06/21/10
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096001] PCI: PCI BIOS revision 2.10 entry at 0xe9c04, last bus=1
[    0.096001] PCI: Using configuration type 1 for base access
[    0.096001] bio: create slab <bio-0> at 0
[    0.096001] ACPI: EC: Look up EC in DSDT
[    0.096986] ACPI: Executed 1 blocks of module-level executable AML code
[    0.100481] ACPI: Interpreter enabled
[    0.100494] ACPI: (supports S0 S3 S4 S5)
[    0.100523] ACPI: Using IOAPIC for interrupt routing
[    0.111159] ACPI: EC: GPE = 0x1, I/O: command/status = 0x66, data = 0x62
[    0.111353] ACPI: No dock devices found.
[    0.111545] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.111608] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xa0000000-0xa7ffffff]
[    0.111980] pci 0000:00:01.0: supports D1
[    0.112048] pci 0000:00:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.112070] pci 0000:00:09.0: supports D1 D2
[    0.112074] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112080] pci 0000:00:09.0: PME# disabled
[    0.112148] pci 0000:00:10.0: reg 20 io port: [0x1200-0x121f]
[    0.112180] pci 0000:00:10.0: supports D1 D2
[    0.112183] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112189] pci 0000:00:10.0: PME# disabled
[    0.112248] pci 0000:00:10.1: reg 20 io port: [0x1220-0x123f]
[    0.112280] pci 0000:00:10.1: supports D1 D2
[    0.112282] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112288] pci 0000:00:10.1: PME# disabled
[    0.112347] pci 0000:00:10.2: reg 20 io port: [0x1240-0x125f]
[    0.112379] pci 0000:00:10.2: supports D1 D2
[    0.112382] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112387] pci 0000:00:10.2: PME# disabled
[    0.112427] pci 0000:00:10.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.112479] pci 0000:00:10.3: supports D1 D2
[    0.112482] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112487] pci 0000:00:10.3: PME# disabled
[    0.112567] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.112576] pci 0000:00:11.0: quirk: region 1000-107f claimed by vt8235 PM
[    0.112581] pci 0000:00:11.0: quirk: region 1400-140f claimed by vt8235 SMB
[    0.112660] pci 0000:00:11.1: reg 20 io port: [0x1100-0x110f]
[    0.112738] pci 0000:00:11.5: reg 10 io port: [0xe000-0xe0ff]
[    0.112792] pci 0000:00:11.5: supports D1 D2
[    0.112833] pci 0000:00:11.6: reg 10 io port: [0xe100-0xe1ff]
[    0.112926] pci 0000:00:12.0: reg 10 io port: [0xe200-0xe2ff]
[    0.112935] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0000000-0xd00000ff]
[    0.112984] pci 0000:00:12.0: supports D1 D2
[    0.112987] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.112992] pci 0000:00:12.0: PME# disabled
[    0.113059] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x90000000-0x93ffffff]
[    0.113067] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc0ffffff]
[    0.113091] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.113113] pci 0000:01:00.0: supports D1 D2
[    0.113159] pci 0000:00:01.0: bridge io port: [0xc000-0xdfff]
[    0.113165] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xcfffffff]
[    0.113171] pci 0000:00:01.0: bridge 32bit mmio pref: [0x90000000-0x9fffffff]
[    0.113200] pci_bus 0000:00: on NUMA node 0
[    0.113207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.130631] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.130778] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[    0.130921] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.131070] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[    0.131191] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.131313] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.131434] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.131555] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.131691] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[    0.131849] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[    0.132095] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[    0.132176] ACPI Warning for \_SB_.PCI0.ALKD._CRS: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    0.132185] ACPI Error (uteval-0307): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db417648), AE_TYPE
[    0.132195] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 (20090903/uteval-313)
[    0.132202] ACPI Exception: AE_TYPE, Evaluating _CRS (20090903/pci_link-282)
[    0.132207] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[    0.132340] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.132343] vgaarb: loaded
[    0.132514] SCSI subsystem initialized
[    0.132609] libata version 3.00 loaded.
[    0.132706] usbcore: registered new interface driver usbfs
[    0.132723] usbcore: registered new interface driver hub
[    0.132754] usbcore: registered new device driver usb
[    0.132936] ACPI: WMI: Mapper loaded
[    0.132939] PCI: Using ACPI for IRQ routing
[    0.133153] NetLabel: Initializing
[    0.133155] NetLabel:  domain hash size = 128
[    0.133158] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.133184] NetLabel:  unlabeled traffic allowed by default
[    0.133229] Switching to clocksource tsc
[    0.135968] AppArmor: AppArmor Filesystem Enabled
[    0.136001] pnp: PnP ACPI init
[    0.136001] ACPI: bus type pnp registered
[    0.139659] pnp: PnP ACPI: found 9 devices
[    0.139663] ACPI: ACPI bus type pnp unregistered
[    0.139669] PnPBIOS: Disabled by ACPI PNP
[    0.139690] system 00:05: iomem range 0xe0000-0xfffff could not be reserved
[    0.139694] system 00:05: iomem range 0xfff80000-0xffffffff has been reserved
[    0.139698] system 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.139702] system 00:05: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.139711] system 00:07: ioport range 0x330-0x331 has been reserved
[    0.139715] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.139718] system 00:07: ioport range 0x1000-0x107f has been reserved
[    0.139722] system 00:07: ioport range 0x1400-0x140f has been reserved
[    0.174486] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.174491] pci 0000:00:01.0:   IO window: 0xc000-0xdfff
[    0.174498] pci 0000:00:01.0:   MEM window: 0xc0000000-0xcfffffff
[    0.174504] pci 0000:00:01.0:   PREFETCH window: 0x90000000-0x9fffffff
[    0.174513] pci 0000:00:09.0: CardBus bridge, secondary bus 0000:02
[    0.174516] pci 0000:00:09.0:   IO window: 0x001800-0x0018ff
[    0.174522] pci 0000:00:09.0:   IO window: 0x001c00-0x001cff
[    0.174528] pci 0000:00:09.0:   PREFETCH window: 0x1c000000-0x1fffffff
[    0.174534] pci 0000:00:09.0:   MEM window: 0x20000000-0x23ffffff
[    0.174555] pci 0000:00:01.0: setting latency timer to 64
[    0.174570]   alloc irq_desc for 17 on node -1
[    0.174573]   alloc kstat_irqs on node -1
[    0.174582] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.174593] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.174596] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.174600] pci_bus 0000:01: resource 0 io:  [0xc000-0xdfff]
[    0.174603] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xcfffffff]
[    0.174607] pci_bus 0000:01: resource 2 pref mem [0x90000000-0x9fffffff]
[    0.174611] pci_bus 0000:02: resource 0 io:  [0x1800-0x18ff]
[    0.174614] pci_bus 0000:02: resource 1 io:  [0x1c00-0x1cff]
[    0.174618] pci_bus 0000:02: resource 2 pref mem [0x1c000000-0x1fffffff]
[    0.174621] pci_bus 0000:02: resource 3 mem: [0x20000000-0x23ffffff]
[    0.174674] NET: Registered protocol family 2
[    0.174811] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.175162] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.175320] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.175483] TCP: Hash tables configured (established 16384 bind 16384)
[    0.175487] TCP reno registered
[    0.175588] NET: Registered protocol family 1
[    0.175616] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.175675] pci 0000:01:00.0: Boot video device
[    0.175906] cpufreq-nforce2: No nForce2 chipset.
[    0.175946] Scanning for low memory corruption every 60 seconds
[    0.176123] audit: initializing netlink socket (disabled)
[    0.176148] type=2000 audit(1277101632.174:1): initialized
[    0.189255] Trying to unpack rootfs image as initramfs...
[    0.203286] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.208832] VFS: Disk quotas dquot_6.5.2
[    0.208923] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.209733] fuse init (API version 7.13)
[    0.209852] msgmni has been set to 851
[    0.215300] alg: No test for stdrng (krng)
[    0.215446] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.215451] io scheduler noop registered
[    0.215454] io scheduler anticipatory registered
[    0.215456] io scheduler deadline registered
[    0.215516] io scheduler cfq registered (default)
[    0.215698] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.215730] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.219088] ACPI: AC Adapter [AC] (on-line)
[    0.219206] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.223306] ACPI: Lid Switch [LID]
[    0.223404] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.223413] ACPI: Sleep Button [SBTN]
[    0.223474] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.223478] ACPI: Power Button [PBTN]
[    0.223550] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.223553] ACPI: Power Button [PWRF]
[    0.223855] Marking TSC unstable due to TSC halts in idle
[    0.223926] processor LNXCPU:00: registered as cooling_device0
[    0.230602] Switching to clocksource acpi_pm
[    0.231097] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.233987] isapnp: Scanning for PnP cards...
[    0.240517] brd: module loaded
[    0.241159] loop: module loaded
[    0.241306] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.241640] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[    0.241714] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.241718] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.241727]   alloc irq_desc for 20 on node -1
[    0.241730]   alloc kstat_irqs on node -1
[    0.241742] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.241809] pata_acpi 0000:00:11.1: PCI INT A disabled
[    0.242227] Fixed MDIO Bus: probed
[    0.242275] PPP generic driver version 2.4.2
[    0.242356] tun: Universal TUN/TAP device driver, 1.6
[    0.242359] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.242473] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.242501] ehci_hcd 0000:00:10.3: enabling device (0000 -> 0002)
[    0.242592] ACPI Error (uteval-0307): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db417648), AE_TYPE
[    0.242604] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 (20090903/uteval-313)
[    0.242638] ACPI Exception: AE_TYPE, Evaluating _CRS (20090903/pci_link-282)
[    0.242644] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.242647] ehci_hcd 0000:00:10.3: PCI INT D: no GSI - using IRQ 10
[    0.245850] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.245944] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.246032] ehci_hcd 0000:00:10.3: irq 10, io mem 0x24001000
[    0.291948] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.292137] usb usb1: configuration #1 chosen from 1 choice
[    0.292178] hub 1-0:1.0: USB hub found
[    0.292190] hub 1-0:1.0: 6 ports detected
[    0.292276] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.292304] uhci_hcd: USB Universal Host Controller Interface driver
[    0.292510] ACPI Error (uteval-0307): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db417648), AE_TYPE
[    0.292522] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 (20090903/uteval-313)
[    0.292529] ACPI Exception: AE_TYPE, Evaluating _CRS (20090903/pci_link-282)
[    0.292535] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.292538] uhci_hcd 0000:00:10.0: PCI INT A: no GSI - using IRQ 11
[    0.292568] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.292621] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.292677] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[    0.292796] usb usb2: configuration #1 chosen from 1 choice
[    0.292828] hub 2-0:1.0: USB hub found
[    0.292839] hub 2-0:1.0: 2 ports detected
[    0.292971] ACPI Error (uteval-0307): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db417648), AE_TYPE
[    0.292981] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 (20090903/uteval-313)
[    0.292988] ACPI Exception: AE_TYPE, Evaluating _CRS (20090903/pci_link-282)
[    0.292993] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.292996] uhci_hcd 0000:00:10.1: PCI INT B: no GSI - using IRQ 7
[    0.293018] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.293059] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.293108] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[    0.293222] usb usb3: configuration #1 chosen from 1 choice
[    0.293270] hub 3-0:1.0: USB hub found
[    0.293280] hub 3-0:1.0: 2 ports detected
[    0.293414] ACPI Error (uteval-0307): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node db417648), AE_TYPE
[    0.293423] ACPI Error: Type returned from _CRS was incorrect: Integer, expected Btypes: 4 (20090903/uteval-313)
[    0.293430] ACPI Exception: AE_TYPE, Evaluating _CRS (20090903/pci_link-282)
[    0.293436] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.293439] uhci_hcd 0000:00:10.2: PCI INT C: no GSI - using IRQ 5
[    0.293459] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.293503] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.293551] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[    0.293670] usb usb4: configuration #1 chosen from 1 choice
[    0.293704] hub 4-0:1.0: USB hub found
[    0.293714] hub 4-0:1.0: 2 ports detected
[    0.293841] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.306132] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.334399] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.336615] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.336697] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.336727] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.336755] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.336981] mice: PS/2 mouse device common for all mice
[    0.337285] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.337345] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.337535] device-mapper: uevent: version 1.0.3
[    0.340611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.342461] device-mapper: multipath: version 1.1.0 loaded
[    0.342466] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.342699] EISA: Probing bus 0 at eisa.0
[    0.342711] Cannot allocate resource for EISA slot 1
[    0.342746] EISA: Detected 0 cards.
[    0.344517] cpuidle: using governor ladder
[    0.344596] cpuidle: using governor menu
[    0.345184] TCP cubic registered
[    0.345399] NET: Registered protocol family 10
[    0.346021] lo: Disabled Privacy Extensions
[    0.346401] NET: Registered protocol family 17
[    0.346489] Using IPI No-Shortcut mode
[    0.346625] PM: Resume from disk failed.
[    0.346651] registered taskstats version 1
[    0.346983]   Magic number: 14:138:469
[    0.347143] rtc_cmos 00:03: setting system clock to 2010-06-21 06:27:12 UTC (1277101632)
[    0.347148] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.347151] EDD information not available.
[    0.364217] ACPI: Battery Slot [BAT0] (battery present)
[    0.413643] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.793293] Freeing initrd memory: 7787k freed
[    0.891146] isapnp: No Plug & Play device found
[    0.891184] Freeing unused kernel memory: 656k freed
[    0.892189] Write protecting the kernel text: 4676k
[    0.892237] Write protecting the kernel read-only data: 1840k
[    0.914420] udev: starting version 151
[    1.149069] pata_via 0000:00:11.1: version 0.3.4
[    1.149098] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.155269] scsi0 : pata_via
[    1.155796] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.155830] scsi1 : pata_via
[    1.159448] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    1.159452] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    1.159827] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[    1.159830] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[    1.159838]   alloc irq_desc for 23 on node -1
[    1.159841]   alloc kstat_irqs on node -1
[    1.159852] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKB] -> GSI 23 (level, low) -> IRQ 23
[    1.164807] eth0: VIA Rhine II at 0xd0000000, 00:40:d0:8d:b0:13, IRQ 23.
[    1.165521] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    1.320575] ata1.00: ATA-7: FUJITSU MHV2080AT, 000000A0, max UDMA/100
[    1.320579] ata1.00: 156301488 sectors, multi 16: LBA 
[    1.336441] ata1.00: configured for UDMA/100
[    1.336637] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2080A 0000 PQ: 0 ANSI: 5
[    1.336855] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.337264] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.337325] sd 0:0:0:0: [sda] Write Protect is off
[    1.337328] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.337360] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.337558]  sda: sda2 < sda5 sda6 sda7 >
[    1.398669] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.500462] ata2.00: ATAPI: _NEC DVD_RW ND-6750A, 2.41, max UDMA/33
[    1.516349] ata2.00: configured for UDMA/33
[    1.518371] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-6750A  2.41 PQ: 0 ANSI: 5
[    1.521839] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.521844] Uniform CD-ROM driver Revision: 3.20
[    1.521979] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.522055] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.954490] kjournald starting.  Commit interval 5 seconds
[    1.954506] EXT3-fs: mounted filesystem with ordered data mode.
[   33.989442] Adding 3903752k swap on /dev/sda5.  Priority:-1 extents:1 across:3903752k 
[   34.042825] udev: starting version 151
[   34.230944] lp: driver loaded but no devices found
[   34.487222] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.556061] EXT3 FS on sda6, internal journal
[   34.625644] irda_init()
[   34.625674] NET: Registered protocol family 23
[   34.641292] Linux agpgart interface v0.103
[   34.652681] ACPI: resource vt596_smbus [0x1400-0x1407] conflicts with ACPI region SM06 [0x1406-0x1406]
[   34.652688] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   34.668969] yenta_cardbus 0000:00:09.0: CardBus bridge found [1734:10ab]
[   34.668998] yenta_cardbus 0000:00:09.0: Using CSCINT to route CSC interrupts to PCI
[   34.669002] yenta_cardbus 0000:00:09.0: Routing CardBus interrupts to PCI
[   34.669008] yenta_cardbus 0000:00:09.0: TI: mfunc 0x01001002, devctl 0x44
[   34.675898] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input6
[   34.676216] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[   34.714884] vga16fb: initializing
[   34.714893] vga16fb: mapped to 0xc00a0000
[   34.715119] fb0: VGA16 VGA frame buffer device
[   34.876747] type=1505 audit(1277101667.028:2):  operation="profile_load" pid=494 name="/sbin/dhclient3"
[   34.877512] type=1505 audit(1277101667.028:3):  operation="profile_load" pid=494 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   34.877927] type=1505 audit(1277101667.028:4):  operation="profile_load" pid=494 name="/usr/lib/connman/scripts/dhclient-script"
[   34.980465] yenta_cardbus 0000:00:09.0: ISA IRQ mask 0x0058, PCI irq 17
[   34.980470] yenta_cardbus 0000:00:09.0: Socket status: 30000006
[   34.989604] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[   35.029777] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xa0000000
[   35.250740] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   35.250959] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[   35.250962] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   35.250971]   alloc irq_desc for 22 on node -1
[   35.250974]   alloc kstat_irqs on node -1
[   35.250985] VIA 82xx Modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   35.252064] VIA 82xx Modem 0000:00:11.6: setting latency timer to 64
[   35.271246] Console: switching to colour frame buffer device 80x30
[   35.499888] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   35.502036] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   35.502935] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   35.503681] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   35.504468] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[   35.505467]  clean.
[   35.505643] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   35.556719] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input7
[   35.762372] VIA 82xx Audio 0000:00:11.5: power state changed by ACPI to D0
[   35.762395] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   35.762550] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   36.025014] type=1505 audit(1277101668.176:5):  operation="profile_load" pid=661 name="/usr/share/gdm/guest-session/Xsession"
[   36.041888] type=1505 audit(1277101668.192:6):  operation="profile_replace" pid=662 name="/sbin/dhclient3"
[   36.042657] type=1505 audit(1277101668.192:7):  operation="profile_replace" pid=662 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   36.043073] type=1505 audit(1277101668.192:8):  operation="profile_replace" pid=662 name="/usr/lib/connman/scripts/dhclient-script"
[   36.045754] eth0: link down
[   36.058919] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.076932] type=1505 audit(1277101668.228:9):  operation="profile_load" pid=664 name="/usr/bin/evince"
[   36.111910] type=1505 audit(1277101668.260:10):  operation="profile_load" pid=664 name="/usr/bin/evince-previewer"
[   36.130598] type=1505 audit(1277101668.280:11):  operation="profile_load" pid=664 name="/usr/bin/evince-thumbnailer"
[   36.532925] apm: BIOS not found.
[   36.760981] ppdev: user-space parallel port driver
[   36.909404] [drm] Initialized drm 1.1.0 20060810
[   37.412087] pci 0000:01:00.0: power state changed by ACPI to D0
[   37.412114]   alloc irq_desc for 16 on node -1
[   37.412118]   alloc kstat_irqs on node -1
[   37.412130] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   37.413758] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   37.417092] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   37.417126] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   37.417135] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   37.417217] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[  151.924482] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  151.924557] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  162.064031] eth0: no IPv6 routers present
niamh@niamh-laptop:~$ 
[/PHP]

---

### Post by ni ni on 2010-06-21
> **mapes12 said:**
> Take a look at the keyboard. Across the top are the "F" keys. One of these may have a blue icon on it (or similar colour) indicating wireless. Then, on my laptop, there is a key in the same colour labelled "Fn" in the bottom L/H corner. Holding down the FN key and then pressing the F key with the wireless symbol toggles the wireless device on and off.

Thanks mapes, The wireless symbol is lit! i turned it off and on again to see whether that would make a difference or not.

---

