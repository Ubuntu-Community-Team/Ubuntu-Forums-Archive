---
title: "able to use ubuntu but cannot install"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by fryc86 on 2010-02-28
I've been trying different things the last couple of days and haven't found a solution yet.  I have a copy of the iso of jaunty and a copy of the iso of karmic on cd.  I can use both of these cd's and in karmic I made a bootable usb via the built in tool and now have a copy of karmic on my usb flash drive.  

I can use these to boot into the OS and use it normally.  However I cannot install them to my main harddrive.  With all of these copies (and other cd attempts that I have given up on) it says something to the effect of - the installation cannot continue because the cd is faulty. this can be due to a dirty cd, bad download or overheating etc... I've used different, new cd's, tried burning the cd's at different speeds, and made sure it was cool while installing.  And the same thing is happening on all 3 installs.  

It could be something wrong with my hard drive as I am trying to install on my laptop which had recently died making my windows installation unusable and that also (via the installation cd) fails the installation part way through.  

If it is the hard drive I suppose I can use the OS via the cd and/or usb flash drive, although I will have to get a new laptop soon as that can't be a long-term option.

thanks

---

### Post by rbaleksandar on 2010-02-28
It might be a hard drive problem but it might be just a corrupted download. You said you've burned a couple of CDs, but did you do try downloading the image file again or just burned the same thing a couple of times. And another question - did you try reinstalling Windows again? You might want to try this too and see if the same problem occurs.

Greetings,
rbaleksandar


PS: Look in the internet for rescue CDs that have tools for diagnosing hardware. I usually use Hiren's Boot CD but you might want to use something else.

---

### Post by fryc86 on 2010-02-28
I'm thinking it might be the hard drive too, but I wanted to be sure before giving it up. 

 I'm not sure how it could be a corrupted download as both my 9.04 and 9.10 iso's came from the ubuntu main site (and they would both have to be corrupted as opposed to just one).  I've downloaded these iso's a couple of times to different cd's (did not just burn the same file to difference cd's.)  And yes, as I mentioned I did try to install windows again.  When it didn't work is when I turned to the ubuntu options.  Interestingly both ubuntu installs and the windows install cd all seem to start the install and make progress to about 2/3 of the way through and then the error occurs.  I don't know if that means the hard drive is fried or if one file (or set of files) which tries to install at 2/3 through the process is corrupted, or what.  

I just downloaded Hiren's Boot cd on your recommendation and I can boot it and accessed the "mini windows xp" option and it went into a stripped down version of windows.  I'm not really sure what to do with this tool, so any tips would be helpful.


p.s. as an aside I've also tried creating a usb install with unetbootin, but that also didn't work, but I think for some other unrelated issues (but who knows?)

---

### Post by jocko on 2010-02-28
If this happens with any install media (cd and usb) you try to install from, your problem could be hardware related, but not necessarily the hard drive. I had the same problem a few months ago, and it turned out that it was caused by memory corruption, which was detected only after hours of running memtest.
In my case the real cause was that I had lowered the voltage to my cpu a little bit too much (trying to keep the cpu as cool as possible), but the same problem could probably be caused by a faulty stick of ram or if you are trying to overclock your cpu.
Run memtest (from the live cd's boot menu). If it doesn't find any problem immediately, let it run over night. If there are *any* errors, that's probably the cause of both your broken windows install and your failed install attempts (of both windows and ubuntu).

---

### Post by fryc86 on 2010-02-28
Is memtest in ubuntu somewhere?  or the Hiren's boot cd?  All I see in ubuntu is "System Testing"

---

### Post by jocko on 2010-02-28
It's in the ubuntu live cd's **boot menu**. Restart your computer with the live cd, and when you get to the boot menu you choose "test memory" instead of "try ubuntu.." or "install ubuntu".

---

### Post by fryc86 on 2010-02-28
> **jocko said:**
> It's in the ubuntu live cd's **boot menu**. Restart your computer with the live cd, and when you get to the boot menu you choose "test memory" instead of "try ubuntu.." or "install ubuntu".

oh ok, thanks.  I'll run it the rest of the night and see what shows up in the morning.  thanks

EDIT:  tried running memtest a couple of times.  It started and worked for a minute or two and then just completely turned off my computer.  This happens sometimes when my computer overheats, but was not hot this time.  Just turned off for no apparent reason.  Turns back on fine as I'm using it now, but still...  so I can't run that test.

---

### Post by 3rdalbum on 2010-02-28
If the memory is faulty and alters its contents, then this could cause the installer to fail as well.

The Linux kernel makes a note every time it tries to read data and fails. Open the terminal (Applications > Accessories > Terminal, or hit Control-Alt-F2 and log in with 'ubuntu' and no password) and type the following:

```
dmesg
```

This is the main kernel log. If it says anything about an I/O error, then it's a read or write error. It will also tell you a device - something like "/dev/sda" or "/dev/scd0" which will tell you whether it's an error on the CD or an error on the HDD.

---

### Post by fryc86 on 2010-02-28
thanks I did get I/O errors and they all seem to be pointing to /dev/sr0 which is the cd/dvd drive.  I'm not entirely sure what this means as I've tried burning the iso's using this drive and also a different unrelated drive on a different computer.  However, its not just the cd-dvd drive installs that aren't working.  The one from my usb flash isn't either, although that could be a separate problem of me not getting it bootable correctly or something.  Anyways, here is the message that I got in terminal:

_______________________________________





[    0.396328] hpet0: at MMIO 0xfed03000, IRQs 2, 8, 0
[    0.396340] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.416026] pnp: PnP ACPI init
[    0.416069] ACPI: bus type pnp registered
[    0.473510] pnp: PnP ACPI: found 11 devices
[    0.473517] ACPI: ACPI bus type pnp unregistered
[    0.473527] PnPBIOS: Disabled by ACPI PNP
[    0.473552] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.473560] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.473568] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.473575] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.473592] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.473607] system 00:09: ioport range 0x400-0x47f has been reserved
[    0.473615] system 00:09: ioport range 0x1180-0x119f has been reserved
[    0.473622] system 00:09: ioport range 0x500-0x53f has been reserved
[    0.473630] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.473637] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.473645] system 00:09: iomem range 0xfed20000-0xfed23fff has been reserved
[    0.473652] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.473660] system 00:09: iomem range 0xfc800400-0xfc800fff has been reserved
[    0.508517] AppArmor: AppArmor Filesystem Enabled
[    0.508579] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.508586] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.508596] pci 0000:00:1c.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.508604] pci 0000:00:1c.0:   PREFETCH window: 0x000000ffd00000-0x000000ffdfffff
[    0.508616] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.508620] pci 0000:00:1c.1:   IO window: disabled
[    0.508629] pci 0000:00:1c.1:   MEM window: 0xdfc00000-0xdfcfffff
[    0.508636] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.508644] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.508649] pci 0000:00:1e.0:   IO window: disabled
[    0.508657] pci 0000:00:1e.0:   MEM window: disabled
[    0.508663] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.508687]   alloc irq_desc for 16 on node -1
[    0.508692]   alloc kstat_irqs on node -1
[    0.508705] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.508715] pci 0000:00:1c.0: setting latency timer to 64
[    0.508728]   alloc irq_desc for 17 on node -1
[    0.508733]   alloc kstat_irqs on node -1
[    0.508741] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.508749] pci 0000:00:1c.1: setting latency timer to 64
[    0.508760] pci 0000:00:1e.0: setting latency timer to 64
[    0.508770] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.508776] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.508783] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.508789] pci_bus 0000:01: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.508796] pci_bus 0000:01: resource 2 pref mem [0xffd00000-0xffdfffff]
[    0.508802] pci_bus 0000:02: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    0.508809] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.508815] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.508890] NET: Registered protocol family 2
[    0.509099] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.509767] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.510745] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.511198] TCP: Hash tables configured (established 131072 bind 65536)
[    0.511205] TCP reno registered
[    0.511426] NET: Registered protocol family 1
[    0.511563] Trying to unpack rootfs image as initramfs...
[    0.897125] Switched to high resolution mode on CPU 1
[    0.900039] Switched to high resolution mode on CPU 0
[    3.519973] Freeing initrd memory: 5620k freed
[    3.525650] cpufreq-nforce2: No nForce2 chipset.
[    3.525713] Scanning for low memory corruption every 60 seconds
[    3.525937] audit: initializing netlink socket (disabled)
[    3.525967] type=2000 audit(1267351336.524:1): initialized
[    3.543588] highmem bounce pool size: 64 pages
[    3.543600] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.546966] VFS: Disk quotas dquot_6.5.2
[    3.547100] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.548416] fuse init (API version 7.12)
[    3.548611] msgmni has been set to 1732
[    3.549087] alg: No test for stdrng (krng)
[    3.549120] io scheduler noop registered
[    3.549125] io scheduler anticipatory registered
[    3.549130] io scheduler deadline registered
[    3.549248] io scheduler cfq registered (default)
[    3.549274] pci 0000:00:02.0: Boot video device
[    3.549667]   alloc irq_desc for 24 on node -1
[    3.549673]   alloc kstat_irqs on node -1
[    3.549690] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    3.549705] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    3.549891]   alloc irq_desc for 25 on node -1
[    3.549896]   alloc kstat_irqs on node -1
[    3.549909] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    3.549922] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    3.550090] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.550117] Firmware did not grant requested _OSC control
[    3.550149] Firmware did not grant requested _OSC control
[    3.550209] Firmware did not grant requested _OSC control
[    3.550234] Firmware did not grant requested _OSC control
[    3.550264] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.604150] ACPI: AC Adapter [ADP1] (on-line)
[    3.604293] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    3.604302] ACPI: Power Button [PWRF]
[    3.604420] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/PNP0C09:00/PNP0C0D:00/input/input1
[    3.660074] ACPI: Lid Switch [LID0]
[    3.660175] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    3.660183] ACPI: Power Button [PWRB]
[    3.660284] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    3.660291] ACPI: Sleep Button [SLPB]
[    3.661537] ACPI: SSDT 3f5e8c90 00253 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    3.662425] ACPI: SSDT 3f5e7690 00653 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    3.667137] Monitor-Mwait will be used to enter C-1 state
[    3.667215] Monitor-Mwait will be used to enter C-2 state
[    3.667274] Monitor-Mwait will be used to enter C-3 state
[    3.667296] Marking TSC unstable due to TSC halts in idle
[    3.667342] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.667403] processor LNXCPU:00: registered as cooling_device0
[    3.667413] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.668172] ACPI: SSDT 3f5e8f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    3.668734] ACPI: SSDT 3f611b10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    3.670446] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.670505] processor LNXCPU:01: registered as cooling_device1
[    3.670515] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.840153] thermal LNXTHERM:01: registered as thermal_zone0
[    3.840171] ACPI: Thermal Zone [THRM] (86 C)
[    3.840277] isapnp: Scanning for PnP cards...
[    4.193409] isapnp: No Plug & Play device found
[    4.196181] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.198817] brd: module loaded
[    4.199829] loop: module loaded
[    4.200004] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    4.200275] ata_piix 0000:00:1f.2: version 2.13
[    4.200303]   alloc irq_desc for 19 on node -1
[    4.200308]   alloc kstat_irqs on node -1
[    4.200321] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.200331] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.352040] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.352193] scsi0 : ata_piix
[    4.352391] scsi1 : ata_piix
[    4.352474] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe0a0 irq 14
[    4.352481] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe0a8 irq 15
[    4.354459] Fixed MDIO Bus: probed
[    4.354540] PPP generic driver version 2.4.2
[    4.354751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.354810]   alloc irq_desc for 23 on node -1
[    4.354816]   alloc kstat_irqs on node -1
[    4.354829] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.354859] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.354866] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.354967] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.358885] ehci_hcd 0000:00:1d.7: debug port 1
[    4.358896] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.358925] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdff40000
[    4.372032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.372212] usb usb1: configuration #1 chosen from 1 choice
[    4.372278] hub 1-0:1.0: USB hub found
[    4.372301] hub 1-0:1.0: 8 ports detected
[    4.372438] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.372484] uhci_hcd: USB Universal Host Controller Interface driver
[    4.372558] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.372571] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.372578] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.372660] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.372696] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    4.372869] usb usb2: configuration #1 chosen from 1 choice
[    4.372932] hub 2-0:1.0: USB hub found
[    4.372948] hub 2-0:1.0: 2 ports detected
[    4.373072] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.373086] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.373092] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.373176] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.373223] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    4.373387] usb usb3: configuration #1 chosen from 1 choice
[    4.373447] hub 3-0:1.0: USB hub found
[    4.373462] hub 3-0:1.0: 2 ports detected
[    4.373557]   alloc irq_desc for 18 on node -1
[    4.373563]   alloc kstat_irqs on node -1
[    4.373575] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.373586] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.373593] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.373665] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.373708] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    4.373872] usb usb4: configuration #1 chosen from 1 choice
[    4.373932] hub 4-0:1.0: USB hub found
[    4.373947] hub 4-0:1.0: 2 ports detected
[    4.374040] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.374052] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.374059] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.374124] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.374167] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e020
[    4.374331] usb usb5: configuration #1 chosen from 1 choice
[    4.374391] hub 5-0:1.0: USB hub found
[    4.374406] hub 5-0:1.0: 2 ports detected
[    4.374516] i8042: PNP detection disabled
[    4.393729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.393744] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.393916] mice: PS/2 mouse device common for all mice
[    4.394200] rtc_cmos 00:04: RTC can wake from S4
[    4.394292] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.394333] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.394643] device-mapper: uevent: version 1.0.3
[    4.394901] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.395086] device-mapper: multipath: version 1.1.0 loaded
[    4.395094] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.395412] EISA: Probing bus 0 at eisa.0
[    4.395450] EISA: Detected 0 cards.
[    4.395817] cpuidle: using governor ladder
[    4.396093] cpuidle: using governor menu
[    4.397229] TCP cubic registered
[    4.397607] NET: Registered protocol family 10
[    4.398605] lo: Disabled Privacy Extensions
[    4.399356] NET: Registered protocol family 17
[    4.399404] Bluetooth: L2CAP ver 2.13
[    4.399409] Bluetooth: L2CAP socket layer initialized
[    4.399415] Bluetooth: SCO (Voice Link) ver 0.6
[    4.399419] Bluetooth: SCO socket layer initialized
[    4.399514] Bluetooth: RFCOMM TTY layer initialized
[    4.399525] Bluetooth: RFCOMM socket layer initialized
[    4.399530] Bluetooth: RFCOMM ver 1.11
[    4.400638] Using IPI No-Shortcut mode
[    4.400806] PM: Resume from disk failed.
[    4.400839] registered taskstats version 1
[    4.401118]   Magic number: 14:100:23
[    4.401228] rtc_cmos 00:04: setting system clock to 2010-02-28 10:02:17 UTC (1267351337)
[    4.401237] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.401241] EDD information not available.
[    4.408266] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.685133] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.817866] usb 1-1: configuration #1 chosen from 1 choice
[    4.860303] ACPI: Battery Slot [BAT1] (battery present)
[    4.861650] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    4.861666] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.868692] ata1.00: configured for UDMA/133
[    4.869062] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    4.869411] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    4.869424] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.869564] sd 0:0:0:0: [sda] Write Protect is off
[    4.869572] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.869643] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.869992]  sda: sda1 sda2 <
[    4.896041] Clocksource tsc unstable (delta = -315031664 ns)
[    4.907911]  sda5 >
[    4.908713] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.928122] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    5.061869] usb 1-2: configuration #1 chosen from 1 choice
[    5.172125] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    5.268110] ACPI: EC: missing confirmations, switch off interrupt mode.
[    5.315226] usb 1-6: configuration #1 chosen from 1 choice
[    6.064471] Freeing unused kernel memory: 540k freed
[    6.065362] Write protecting the kernel text: 4568k
[    6.065512] Write protecting the kernel read-only data: 1836k
[    6.804178] Linux agpgart interface v0.103
[    6.936019] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[    6.936019] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[    6.939315] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[    6.939339] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
[    6.973006] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    6.973598] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    6.979182] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    7.045229] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.045298] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.045394] r8169 0000:01:00.0: setting latency timer to 64
[    7.045482]   alloc irq_desc for 26 on node -1
[    7.045496]   alloc kstat_irqs on node -1
[    7.045540] r8169 0000:01:00.0: irq 26 for MSI/MSI-X
[    7.049330] eth0: RTL8102e at 0xf8094000, 00:21:85:dc:69:99, XID 34a00000 IRQ 26
[    7.057082] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
[    7.057102] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[    7.060746] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
[    7.060769] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
[    7.077450] acpi device:1c: registered as cooling_device2
[    7.078017] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1a/input/input6
[    7.078194] ACPI: Video Device [IGD] (multi-head: yes  rom: no  post: no)
[    7.083262] Initializing USB Mass Storage driver...
[    7.083790] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.084341] usb-storage: device found at 2
[    7.084355] usb-storage: waiting for device to settle before scanning
[    7.084572] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.085785] usb-storage: device found at 3
[    7.085800] usb-storage: waiting for device to settle before scanning
[    7.091215] scsi4 : SCSI emulation for USB Mass Storage devices
[    7.091649] usbcore: registered new interface driver usb-storage
[    7.091672] USB Mass Storage support registered.
[    7.092708] usb-storage: device found at 4
[    7.092723] usb-storage: waiting for device to settle before scanning
[    7.198421] [drm] Initialized drm 1.1.0 20060810
[    7.269433] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.269460] i915 0000:00:02.0: setting latency timer to 64
[    7.380259] integrated sync not supported
[    7.498627] integrated sync not supported
[    7.507488] [drm] fb0: inteldrmfb frame buffer device
[    7.507517] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.846992] [drm] LVDS-8: set mode 1024x600 e
[    8.228738] Console: switching to colour frame buffer device 128x37
[    8.785242] xor: automatically using best checksumming function: pIII_sse
[    8.804027]    pIII_sse  :  2387.000 MB/sec
[    8.804040] xor: using function: pIII_sse (2387.000 MB/sec)
[    8.819533] device-mapper: dm-raid45: initialized v0.2594b
[    9.111698] kjournald starting.  Commit interval 5 seconds
[    9.111739] EXT3-fs: mounted filesystem with writeback data mode.
[   12.080388] usb-storage: device scan complete
[   12.081219] scsi 2:0:0:0: Direct-Access     LaCie    itsaKey          0.00 PQ: 0 ANSI: 2
[   12.083004] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   12.086961] sd 2:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)
[   12.087581] sd 2:0:0:0: [sdb] Write Protect is off
[   12.087603] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   12.087618] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   12.087911] usb-storage: device scan complete
[   12.088876] scsi 3:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462D UO00 PQ: 0 ANSI: 0
[   12.091830] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   12.091853]  sdb:
[   12.092977] usb-storage: device scan complete
[   12.093683] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   12.093698] Uniform CD-ROM driver Revision: 3.20
[   12.094093] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   12.094327] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   12.096288] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   12.099008] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   12.106577] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   12.243119]  sdb1
[   12.245459] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   12.245482] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   12.701098] aufs 2-standalone.tree-30-20090727
[   12.755327] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   86.786879] Adding 2971984k swap on /dev/sda5.  Priority:-1 extents:1 across:2971984k 
[   87.442269] udev: starting version 147
[   88.876789] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   88.961208] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   88.962045] 
[   88.962053] 
[   88.962057] === pAd = f8b6b000, size = 580808 ===
[   88.962064] 
[   88.962079] <-- RTMPAllocAdapterBlock, Status=0
[   88.962167] rt2860 0000:02:00.0: setting latency timer to 64
[   89.048682] intel_rng: FWH not detected
[   89.753545] psmouse serio1: ID: 10 00 64
[   90.167239] r8169: eth0: link up
[   90.167261] r8169: eth0: link up
[   90.318107] RX DESC f1cbb000  size = 2048
[   90.319136] <-- RTMPAllocTxRxRingMemory, Status=0
[   90.336753] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[   90.336775] 1. Phy Mode = 0
[   90.336787] 2. Phy Mode = 0
[   90.360006] 3. Phy Mode = 0
[   90.362151] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   90.362173] MCS Set = 00 00 00 00 00
[   90.363785] <==== RTMPInitialize, Status=0
[   90.363866] 0x1300 = 00073200
[   90.550990] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input7
[   90.927324] ip_tables: (C) 2000-2006 Netfilter Core Team
[   91.628635] usplash[326]: segfault at b75a374c ip 00d71de6 sp bfe95410 error 6 in libusplash.so.0 (deleted)[d4d000+29000]
[   92.691570] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   92.691674] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   92.925244] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   92.925618] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   93.929019] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x02043030
[   96.522308] integrated sync not supported
[   96.898341] integrated sync not supported
[   96.962246] lp: driver loaded but no devices found
[   97.173041] ppdev: user-space parallel port driver
[  101.513041] ra0: no IPv6 routers present
[  103.508215] CPU0 attaching NULL sched-domain.
[  103.508239] CPU1 attaching NULL sched-domain.
[  103.528185] CPU0 attaching sched-domain:
[  103.528202]  domain 0: span 0-1 level SIBLING
[  103.528216]   groups: 0 1
[  103.528238] CPU1 attaching sched-domain:
[  103.528248]  domain 0: span 0-1 level SIBLING
[  103.528259]   groups: 1 0
[  104.501505] sr 3:0:0:0: [sr0] Unhandled sense code
[  104.501525] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  104.501547] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  104.501572] Info fld=0x0
[  104.501583] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  104.501610] [B]end_request: I/O error, dev sr0, sector 1413064
[  104.501633] Buffer I/O error on device sr0, logical block 176633[/B]
[  107.368252] sr 3:0:0:0: [sr0] Unhandled sense code
[  107.368272] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  107.368294] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  107.368321] Info fld=0x0
[  107.368332] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  107.368359] [B]end_request: I/O error, dev sr0, sector 1413064
[  107.368382] Buffer I/O error on device sr0, logical block 176633[/B]
[  110.187796] sr 3:0:0:0: [sr0] Unhandled sense code
[  110.187812] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  110.187828] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  110.187848] Info fld=0x0
[  110.187855] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  110.187875] [B]end_request: I/O error, dev sr0, sector 1413064
[  110.187893] Buffer I/O error on device sr0, logical block 176633[/B]
[  111.760660] CPU0 attaching NULL sched-domain.
[  111.760680] CPU1 attaching NULL sched-domain.
[  111.773327] CPU0 attaching sched-domain:
[  111.773349]  domain 0: span 0-1 level SIBLING
[  111.773366]   groups: 0 1
[  111.773398] CPU1 attaching sched-domain:
[  111.773413]  domain 0: span 0-1 level SIBLING
[  111.773428]   groups: 1 0
[  112.460678] integrated sync not supported
[  112.611285] integrated sync not supported
[  112.769046] integrated sync not supported
[  112.974721] sr 3:0:0:0: [sr0] Unhandled sense code
[  112.974740] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  112.974762] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  112.974789] Info fld=0x0
[  112.974800] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  112.974826] [B]end_request: I/O error, dev sr0, sector 1413064
[  112.974849] Buffer I/O error on device sr0, logical block 176633[/B]
[  115.752329] sr 3:0:0:0: [sr0] Unhandled sense code
[  115.752349] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  115.752372] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  115.752398] Info fld=0x0
[  115.752410] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  115.752438][B] end_request: I/O error, dev sr0, sector 1413064
[  115.752462] Buffer I/O error on device sr0, logical block 176633[/B]
[  117.015997] integrated sync not supported
[  118.462809] sr 3:0:0:0: [sr0] Unhandled sense code
[  118.462829] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  118.462851] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  118.462877] Info fld=0x0
[  118.462888] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  118.462914][B] end_request: I/O error, dev sr0, sector 1413064
[  118.462938] Buffer I/O error on device sr0, logical block 176633[/B]
[  121.281861] sr 3:0:0:0: [sr0] Unhandled sense code
[  121.281881] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  121.281904] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  121.281930] Info fld=0x0
[  121.281941] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  121.281969] [B]end_request: I/O error, dev sr0, sector 1413064
[  121.281993] Buffer I/O error on device sr0, logical block 176633[/B]
[  125.584741] sr 3:0:0:0: [sr0] Unhandled sense code
[  125.584760] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  125.584783] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  125.584809] Info fld=0x0
[  125.584820] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  125.584846][B] end_request: I/O error, dev sr0, sector 1413064
[  125.584869] Buffer I/O error on device sr0, logical block 176633[/B]
[  128.398813] sr 3:0:0:0: [sr0] Unhandled sense code
[  128.398834] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  128.398857] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  128.398884] Info fld=0x0
[  128.398896] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  128.398925[B]] end_request: I/O error, dev sr0, sector 1413064
[  128.398949] Buffer I/O error on device sr0, logical block 176633[/B]
[  131.104331] sr 3:0:0:0: [sr0] Unhandled sense code
[  131.104352] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  131.104375] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  131.104403] Info fld=0x0
[  131.104414] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  131.104441] [B]end_request: I/O error, dev sr0, sector 1413064
[  131.104465] Buffer I/O error on device sr0, logical block 176633[/B]
[  133.852742] sr 3:0:0:0: [sr0] Unhandled sense code
[  133.852761] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  133.852783] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  133.852810] Info fld=0x0
[  133.852822] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  133.852849] [B]end_request: I/O error, dev sr0, sector 1413064
[  133.852873] Buffer I/O error on device sr0, logical block 176633[/B]
[  136.600437] sr 3:0:0:0: [sr0] Unhandled sense code
[  136.600457] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  136.600479] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  136.600505] Info fld=0x0
[  136.600516] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  136.600543][B] end_request: I/O error, dev sr0, sector 1413064
[  136.600567] Buffer I/O error on device sr0, logical block 176633[/B]
[  139.426558] sr 3:0:0:0: [sr0] Unhandled sense code
[  139.426577] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  139.426599] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  139.426625] Info fld=0x0
[  139.426636] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  139.426662] [B]end_request: I/O error, dev sr0, sector 1413064
[  139.426685] Buffer I/O error on device sr0, logical block 176633[/B]
[  142.211452] sr 3:0:0:0: [sr0] Unhandled sense code
[  142.211471] sr 3:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  142.211493] sr 3:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  142.211518] Info fld=0x0
[  142.211529] sr 3:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  142.211555] [B]end_request: I/O error, dev sr0, sector 1413064
[  142.211577] Buffer I/O error on device sr0, logical block 176633[/B]

---

### Post by fryc86 on 2010-03-01
still no luck

---

### Post by teward on 2010-03-01
this tracks back to a bad image, the image is corrupted.  Go redownload, reburn, try again.

Those I/O errors are relating to sectors on the disc, as such, the issue means "bad image".

---

### Post by qyot27 on 2010-03-01
To comment a little on the issue of corruption:
> **fryc86 said:**
> I'm not sure how it could be a corrupted download as both my 9.04 and 9.10 iso's came from the ubuntu main site (and they would both have to be corrupted as opposed to just one).  I've downloaded these iso's a couple of times to different cd's (did not just burn the same file to difference cd's.)
The protocol often has a lot to do with it.  HTTP, while rare, is prone to corruption in transmission.  So it's not that the site's download is bad, it's that something interferes between the site and you.  This is why the md5sum files for the ISOs are distributed - to independently verify that the download didn't corrupt.  If you went with BitTorrent to download the ISO, then this wouldn't be an issue - the BT protocol handles error checking and will redownload the packet if the check fails (and continue to do so until it stops failing), although independently testing it against the md5sum isn't a bad thing to do anyway.

When burning a CD-R that is meant for sensitive data like this, *always* let the program do verification.  Most burning apps allow you to do this (ImgBurn does, as does Nero, and every other burning app I can remember that I've tried).  It will check if there were any problems that arose in the burning process by checking the burnt copy against the original ISO.




EDIT: If you don't want to waste time, then after downloading the .torrent file, point the BitTorrent client (uTorrent, Halite, Azureus, Deluge, Transmission...whichever one you use) at the directory the existing 9.04 or 9.10 image is in.  It should pick it up, do the error check, and complete the download properly.  If everything checks out, then the problem is with the burn, and you need to find a burning drive that will give you a reliable burn (which is what the Verify pass is meant to protect against).

EDIT #2:  
You can find the torrents here:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Or here (scroll down to the big file list):
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

---

### Post by fryc86 on 2010-03-01
okay thanks.  I'll try downloading again.  does burn speed help or not, should I burn at lowest speed?

---

### Post by qyot27 on 2010-03-01
> **fryc86 said:**
> okay thanks.  I'll try downloading again.  does burn speed help or not, should I burn at lowest speed?
Depends more on what the drive is capable of, IMO.  The lowest speed certainly won't hurt, though.  My rule of thumb when burning CDs or DVDs is to use **at most** the speed that is 1/2 of the maximum burn speed.  In other words, if the drive supports up to 24x, use 12x or slower speeds.

I also added the links for the BitTorrent downloads to my previous post, just in case.

---

### Post by fryc86 on 2010-03-01
thank you :) It's installed now.

---

