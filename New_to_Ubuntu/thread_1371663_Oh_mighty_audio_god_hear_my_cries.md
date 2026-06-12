---
title: "Oh mighty audio god hear my cries"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by suncross on 2010-01-03
Ok I installed ubuntu 9.10 fresh and I do not have any audio.  It doesn't recognize any of my hardware but it is enabled in my bios and properly in the PCI slots (worked on windows just fine).  Now I just need to know if anyone can help, because I think I posted my first thread in the wrong forums.

Thanks in advance

-Suncross

---

### Post by spiderbatdad on 2010-01-03
If you've checked the volume settings in alsamixer and your audio still isn't working; it's a bad sign. :(
Copy the output of some terminal commands here to help us help you.
```
lspci | grep Audio
cat /proc/asound/cards
```
maybe pm a moderator and ask for your thread to be moved to ABT

---

### Post by suncross on 2010-01-03
For the first command:
```
lspci | grep Audio
```00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio

For the second command:
```
 cat /proc/asound/cards
```cat: /proc/asound/cards: No such file or directory

edit: What is ABT?

---

### Post by spiderbatdad on 2010-01-03
can you run ```
alsamixer
```in your terminal and check the level of master and pcm?

---

### Post by suncross on 2010-01-03
I ran it, however I do not know what PCM is.  The master is at 100 (max).

---

### Post by spiderbatdad on 2010-01-03
add this to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel probe_mask=1 model=6stack-dell
```

---

### Post by Zoot7 on 2010-01-03
Can you post the output of
```
aplay -l
```
?

---

### Post by suncross on 2010-01-03
I am not sure how to open that file.  The correct usage is:

```
 sudo grep /etc/modprobe.d/alsa-base.conf 
```Right?  Well I typed that in and it is just sitting there not doing anything (I have to close out of the terminal to open up a new command line, because clicking enter afterwards just moves the text thing down).

Edit:

Zoot7: aplay: device_list:223: no soundcards found...

---

### Post by spiderbatdad on 2010-01-03
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```The file should not be empty.

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> ```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```The file should not be empty.

Ok I did that, what should I do now?

---

### Post by spiderbatdad on 2010-01-03
assuming you have the right file...there should be text existing...copy paste the options line, save the file, then reboot.

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> assuming you have the right file...there should be text existing...copy paste the options line, save the file, then reboot.

I did that and nothing happened.

edit: And yes there was existing text.

---

### Post by spiderbatdad on 2010-01-03
ok lets try adding this to /etc/rc.local
```
rmmod snd_hda_intel
modprobe snd_hda_intel
```then restart.

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> ok lets try adding this to /etc/rc.local
```
rmmod snd_hda_intel
modprobe snd_hda_intel
```then restart.

I am not sure where to put that text, so my file looks like:

[quote=/etc/rc.local]
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod snd_hda_intel
modprobe snd_hda_intel

exit 0[/quote]

I restarted and nothing happened.

---

### Post by spiderbatdad on 2010-01-03
yes you got it right. Check your volume levels again in alsamixer. if that doesn't fix it I'm at a loss for the moment.

---

### Post by spiderbatdad on 2010-01-03
try removing -e from #!/bin/sh in /etc/rc.local

---

### Post by suncross on 2010-01-03
Everything is at max.  I even went and installed my motherboards audio drivers just now, and still nothing.

---

### Post by suncross on 2010-01-03
I tried that and still nothing.

---

### Post by Tulth on 2010-01-03
I'd run 
$ dmesg

and look over your messages for any snd errors

---

### Post by suncross on 2010-01-03
Wow my sound is totally borked now.  I tried to get esound because people with similar problems had them with pulseaudio.  Now I cant even get into my system - preferences - sound, and it gives me a message saying "Waiting for sound system to respond."

I did that command and it spit out this:

> [    0.195894] libata version 3.00 loaded.
[    0.195894] usbcore: registered new interface driver usbfs
[    0.195894] usbcore: registered new interface driver hub
[    0.195894] usbcore: registered new device driver usb
[    0.196036] ACPI: WMI: Mapper loaded
[    0.196036] PCI: Using ACPI for IRQ routing
[    0.208009] Bluetooth: Core ver 2.15
[    0.208022] NET: Registered protocol family 31
[    0.208022] Bluetooth: HCI device and connection manager initialized
[    0.208022] Bluetooth: HCI socket layer initialized
[    0.208022] NetLabel: Initializing
[    0.208022] NetLabel:  domain hash size = 128
[    0.208022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.208030] NetLabel:  unlabeled traffic allowed by default
[    0.208060] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.208065] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.223987] pnp: PnP ACPI init
[    0.223995] ACPI: bus type pnp registered
[    0.226033] pnp: PnP ACPI: found 15 devices
[    0.226035] ACPI: ACPI bus type pnp unregistered
[    0.226037] PnPBIOS: Disabled by ACPI PNP
[    0.226043] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.226048] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.226052] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.226054] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.226056] system 00:07: ioport range 0x500-0x57f could not be reserved
[    0.226058] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.226060] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.226062] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.226064] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.226069] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
[    0.226074] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.226076] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.226079] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.226083] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.226085] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.226087] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.226089] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.226091] system 00:0e: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.260668] AppArmor: AppArmor Filesystem Enabled
[    0.260709] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.260712] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.260715] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.260718] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.260722] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    0.260723] pci 0000:00:1c.0:   IO window: disabled
[    0.260727] pci 0000:00:1c.0:   MEM window: disabled
[    0.260731] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.260736] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.260739] pci 0000:00:1c.3:   IO window: 0xd000-0xdfff
[    0.260743] pci 0000:00:1c.3:   MEM window: 0xfeb00000-0xfebfffff
[    0.260746] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.260750] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.260752] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.260756] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.260760] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.260763] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.260766] pci 0000:00:1c.5:   IO window: 0xb000-0xbfff
[    0.260770] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.260773] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.260777] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.260779] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.260783] pci 0000:00:1e.0:   MEM window: disabled
[    0.260786] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.260793]   alloc irq_desc for 16 on node -1
[    0.260794]   alloc kstat_irqs on node -1
[    0.260797] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.260800] pci 0000:00:01.0: setting latency timer to 64
[    0.260804]   alloc irq_desc for 17 on node -1
[    0.260806]   alloc kstat_irqs on node -1
[    0.260808] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.260811] pci 0000:00:1c.0: setting latency timer to 64
[    0.260815]   alloc irq_desc for 19 on node -1
[    0.260817]   alloc kstat_irqs on node -1
[    0.260819] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.260822] pci 0000:00:1c.3: setting latency timer to 64
[    0.260827] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.260830] pci 0000:00:1c.4: setting latency timer to 64
[    0.260835] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.260838] pci 0000:00:1c.5: setting latency timer to 64
[    0.260842] pci 0000:00:1e.0: setting latency timer to 64
[    0.260845] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.260847] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.260848] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.260850] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.260852] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.260854] pci_bus 0000:05: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.260855] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.260857] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.260859] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.260860] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.260862] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.260864] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.260865] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.260867] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.260869] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.260888] NET: Registered protocol family 2
[    0.260944] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.261124] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.261355] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.261469] TCP: Hash tables configured (established 131072 bind 65536)
[    0.261470] TCP reno registered
[    0.261514] NET: Registered protocol family 1
[    0.261545] Trying to unpack rootfs image as initramfs...
[    0.386161] Freeing initrd memory: 7488k freed
[    0.388301] cpufreq-nforce2: No nForce2 chipset.
[    0.388323] Scanning for low memory corruption every 60 seconds
[    0.388390] audit: initializing netlink socket (disabled)
[    0.388401] type=2000 audit(1262565564.387:1): initialized
[    0.394257] highmem bounce pool size: 64 pages
[    0.394261] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.395184] VFS: Disk quotas dquot_6.5.2
[    0.395223] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.395579] fuse init (API version 7.12)
[    0.395631] msgmni has been set to 1638
[    0.395764] alg: No test for stdrng (krng)
[    0.395773] io scheduler noop registered
[    0.395775] io scheduler anticipatory registered
[    0.395776] io scheduler deadline registered
[    0.395802] io scheduler cfq registered (default)
[    0.395910] pci 0000:01:00.0: Boot video device
[    0.395997]   alloc irq_desc for 24 on node -1
[    0.395999]   alloc kstat_irqs on node -1
[    0.396005] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.396009] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.396080]   alloc irq_desc for 25 on node -1
[    0.396081]   alloc kstat_irqs on node -1
[    0.396086] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.396092] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.396176]   alloc irq_desc for 26 on node -1
[    0.396177]   alloc kstat_irqs on node -1
[    0.396182] pcieport-driver 0000:00:1c.3: irq 26 for MSI/MSI-X
[    0.396188] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.396270]   alloc irq_desc for 27 on node -1
[    0.396271]   alloc kstat_irqs on node -1
[    0.396276] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    0.396282] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.396364]   alloc irq_desc for 28 on node -1
[    0.396365]   alloc kstat_irqs on node -1
[    0.396370] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.396376] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.396439] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.396527] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.396616] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.396618] ACPI: Power Button [PWRF]
[    0.396658] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.396660] ACPI: Power Button [PWRB]
[    0.397147] ACPI: SSDT cff880d0 00277 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    0.397386] processor LNXCPU:00: registered as cooling_device0
[    0.397659] ACPI: SSDT cff88350 00277 (v01 DpgPmm  P002Ist 00000012 INTL 20060113)
[    0.397886] processor LNXCPU:01: registered as cooling_device1
[    0.399467] isapnp: Scanning for PnP cards...
[    0.501388] Switched to high resolution mode on CPU 1
[    0.503905] Switched to high resolution mode on CPU 0
[    0.752222] isapnp: No Plug & Play device found
[    0.752944] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.753028] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.753326] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.753982] brd: module loaded
[    0.754272] loop: module loaded
[    0.754319] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.754368] ahci 0000:03:00.0: version 3.0
[    0.754379] ahci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.754401] ahci 0000:03:00.0: JMB361 has only one port, port_map 0x3 -> 0x1
[    0.772025] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x1 impl SATA mode
[    0.772028] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    0.772034] ahci 0000:03:00.0: setting latency timer to 64
[    0.772119] scsi0 : ahci
[    0.772184] scsi1 : ahci
[    0.772241] ata1: SATA max UDMA/133 abar m8192@0xfeafe000 port 0xfeafe100 irq 16
[    0.772243] ata2: DUMMY
[    0.772272] ata_piix 0000:00:1f.2: version 2.13
[    0.772279] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.772282] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.772311] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.772345] scsi2 : ata_piix
[    0.772379] scsi3 : ata_piix
[    0.773149] ata3: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 19
[    0.773153] ata4: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 19
[    0.773168] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.773171] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.773198] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.773238] scsi4 : ata_piix
[    0.773274] scsi5 : ata_piix
[    0.774091] ata5: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 19
[    0.774094] ata6: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 19
[    0.774352] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    0.774357] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.774379] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    0.774425] scsi6 : pata_jmicron
[    0.774487] scsi7 : pata_jmicron
[    0.774969] ata7: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 17
[    0.774971] ata8: PATA max UDMA/100 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 17
[    0.775327] Fixed MDIO Bus: probed
[    0.775349] PPP generic driver version 2.4.2
[    0.775398] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.775409]   alloc irq_desc for 18 on node -1
[    0.775410]   alloc kstat_irqs on node -1
[    0.775413] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.775420] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.775422] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.775452] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.779333] ehci_hcd 0000:00:1a.7: debug port 1
[    0.779337] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.779346] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe7ffc00
[    0.792008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.792071] usb usb1: configuration #1 chosen from 1 choice
[    0.792098] hub 1-0:1.0: USB hub found
[    0.792104] hub 1-0:1.0: 6 ports detected
[    0.792156]   alloc irq_desc for 23 on node -1
[    0.792158]   alloc kstat_irqs on node -1
[    0.792162] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.792170] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.792173] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.792201] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.796116] ehci_hcd 0000:00:1d.7: debug port 1
[    0.796120] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.796129] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7ff800
[    0.812007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.812071] usb usb2: configuration #1 chosen from 1 choice
[    0.812096] hub 2-0:1.0: USB hub found
[    0.812101] hub 2-0:1.0: 6 ports detected
[    0.812154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.812172] uhci_hcd: USB Universal Host Controller Interface driver
[    0.812189] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.812194] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.812197] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.812226] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.812244] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009800
[    0.812293] usb usb3: configuration #1 chosen from 1 choice
[    0.812310] hub 3-0:1.0: USB hub found
[    0.812314] hub 3-0:1.0: 2 ports detected
[    0.812344]   alloc irq_desc for 21 on node -1
[    0.812346]   alloc kstat_irqs on node -1
[    0.812349] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.812353] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.812355] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.812374] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.812398] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
[    0.812445] usb usb4: configuration #1 chosen from 1 choice
[    0.812461] hub 4-0:1.0: USB hub found
[    0.812465] hub 4-0:1.0: 2 ports detected
[    0.812496] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.812500] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.812502] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.812520] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.812538] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00009c00
[    0.812585] usb usb5: configuration #1 chosen from 1 choice
[    0.812603] hub 5-0:1.0: USB hub found
[    0.812607] hub 5-0:1.0: 2 ports detected
[    0.812636] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.812640] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.812642] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.812660] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.812678] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009080
[    0.812728] usb usb6: configuration #1 chosen from 1 choice
[    0.812746] hub 6-0:1.0: USB hub found
[    0.812749] hub 6-0:1.0: 2 ports detected
[    0.812778] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.812783] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.812785] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.812804] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.812822] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
[    0.812872] usb usb7: configuration #1 chosen from 1 choice
[    0.812889] hub 7-0:1.0: USB hub found
[    0.812892] hub 7-0:1.0: 2 ports detected
[    0.812926] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.812930] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.812932] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.812953] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.812970] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009480
[    0.813019] usb usb8: configuration #1 chosen from 1 choice
[    0.813035] hub 8-0:1.0: USB hub found
[    0.813038] hub 8-0:1.0: 2 ports detected
[    0.813104] PNP: No PS/2 controller found. Probing ports directly.
[    0.815314] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.815318] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.815352] mice: PS/2 mouse device common for all mice
[    0.815409] rtc_cmos 00:03: RTC can wake from S4
[    0.815429] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.815448] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.815511] device-mapper: uevent: version 1.0.3
[    0.815570] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.815608] device-mapper: multipath: version 1.1.0 loaded
[    0.815610] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.815675] EISA: Probing bus 0 at eisa.0
[    0.815692] Cannot allocate resource for EISA slot 7
[    0.815694] Cannot allocate resource for EISA slot 8
[    0.815695] EISA: Detected 0 cards.
[    0.815739] cpuidle: using governor ladder
[    0.815740] cpuidle: using governor menu
[    0.816053] TCP cubic registered
[    0.816154] NET: Registered protocol family 10
[    0.816443] lo: Disabled Privacy Extensions
[    0.816661] NET: Registered protocol family 17
[    0.816671] Bluetooth: L2CAP ver 2.13
[    0.816673] Bluetooth: L2CAP socket layer initialized
[    0.816674] Bluetooth: SCO (Voice Link) ver 0.6
[    0.816675] Bluetooth: SCO socket layer initialized
[    0.816689] Bluetooth: RFCOMM TTY layer initialized
[    0.816691] Bluetooth: RFCOMM socket layer initialized
[    0.816692] Bluetooth: RFCOMM ver 1.11
[    0.817054] Using IPI No-Shortcut mode
[    0.817089] PM: Resume from disk failed.
[    0.817095] registered taskstats version 1
[    0.817181]   Magic number: 10:396:657
[    0.817185] block ram10: hash matches
[    0.817220] rtc_cmos 00:03: setting system clock to 2010-01-04 00:39:25 UTC (1262565565)
[    0.817223] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.817224] EDD information not available.
[    0.944537] ata7.00: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[    0.960548] ata7.00: configured for UDMA/33
[    1.092028] ata1: SATA link down (SStatus 0 SControl 300)
[    1.102537] ata5: SATA link down (SStatus 0 SControl 300)
[    1.256038] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.264375] ata6.00: ATA-8: ST3500418AS, CC38, max UDMA/133
[    1.264378] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.280392] ata6.00: configured for UDMA/133
[    1.422553] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.422564] ata4.01: SATA link down (SStatus 0 SControl 300)
[    1.433080] ata3.00: SATA link down (SStatus 0 SControl 300)
[    1.433092] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.433183] scsi 5:0:0:0: Direct-Access     ATA      ST3500418AS      CC38 PQ: 0 ANSI: 5
[    1.433252] sd 5:0:0:0: Attached scsi generic sg0 type 0
[    1.433275] sd 5:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.433304] sd 5:0:0:0: [sda] Write Protect is off
[    1.433305] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.433320] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.433397]  sda:
[    1.434750] scsi 6:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.05 PQ: 0 ANSI: 5
[    1.437834] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.437837] Uniform CD-ROM driver Revision: 3.20
[    1.437902] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    1.437938] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    1.448654]  sda1 sda2 < sda5 >
[    1.472785] sd 5:0:0:0: [sda] Attached SCSI disk
[    1.488507] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    1.603315] Freeing unused kernel memory: 544k freed
[    1.603507] Write protecting the kernel text: 4592k
[    1.603557] Write protecting the kernel read-only data: 1836k
[    1.673539] Linux agpgart interface v0.103
[    1.689559] usb 6-1: configuration #1 chosen from 1 choice
[    1.711034] ohci1394 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.711040] ohci1394 0000:04:00.0: setting latency timer to 64
[    1.718748] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.718757] ATL1E 0000:02:00.0: setting latency timer to 64
[    1.735144] usbcore: registered new interface driver hiddev
[    1.738777] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
[    1.738834] generic-usb 0003:046D:C049.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1/input0
[    1.742546] generic-usb 0003:046D:C049.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-1/input1
[    1.742559] usbcore: registered new interface driver usbhid
[    1.742562] usbhid: v2.6:USB HID core driver
[    1.766523] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.936506] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    2.104440] usb 6-2: configuration #1 chosen from 1 choice
[    2.107426] hub 6-2:1.0: USB hub found
[    2.109403] hub 6-2:1.0: 4 ports detected
[    2.379159] PM: Starting manual resume from disk
[    2.379161] PM: Resume from partition 8:5
[    2.379163] PM: Checking hibernation image.
[    2.379343] PM: Resume from disk failed.
[    2.412066] EXT4-fs (sda1): barriers enabled
[    2.417338] usb 6-2.1: new low speed USB device using uhci_hcd and address 4
[    2.427383] kjournald2 starting: pid 412, dev sda1:8, commit interval 5 seconds
[    2.427388] EXT4-fs (sda1): delayed allocation enabled
[    2.427391] EXT4-fs: file extents enabled
[    2.451551] EXT4-fs: mballoc enabled
[    2.451560] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.553371] usb 6-2.1: configuration #1 chosen from 1 choice
[    2.570518] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.0/input/input4
[    2.570569] generic-usb 0003:046D:C226.0003: input,hidraw2: USB HID v1.10 Keyboard [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input0
[    2.606337] input: G15 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.1/6-2.1:1.1/input/input5
[    2.606410] generic-usb 0003:046D:C226.0004: input,hiddev97,hidraw3: USB HID v1.10 Device [G15 Gaming Keyboard] on usb-0000:00:1d.0-2.1/input1
[    2.682278] usb 6-2.4: new full speed USB device using uhci_hcd and address 5
[    2.817309] usb 6-2.4: configuration #1 chosen from 1 choice
[    2.840327] input: G15 GamePanel LCD as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2.4/6-2.4:1.0/input/input6
[    2.840401] generic-usb 0003:046D:C227.0005: input,hiddev98,hidraw4: USB HID v1.11 Keypad [G15 GamePanel LCD] on usb-0000:00:1d.0-2.4/input0
[    2.905923] type=1505 audit(1262565567.586:2): operation="profile_load" pid=442 name=/usr/share/gdm/guest-session/Xsession
[    2.908144] type=1505 audit(1262565567.590:3): operation="profile_load" pid=447 name=/sbin/dhclient3
[    2.908678] type=1505 audit(1262565567.590:4): operation="profile_load" pid=447 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    2.908939] type=1505 audit(1262565567.590:5): operation="profile_load" pid=447 name=/usr/lib/connman/scripts/dhclient-script
[    2.953753] type=1505 audit(1262565567.634:6): operation="profile_load" pid=448 name=/usr/bin/evince
[    2.961559] type=1505 audit(1262565567.643:7): operation="profile_load" pid=448 name=/usr/bin/evince-previewer
[    2.966101] type=1505 audit(1262565567.647:8): operation="profile_load" pid=448 name=/usr/bin/evince-thumbnailer
[    2.982355] type=1505 audit(1262565567.663:9): operation="profile_load" pid=450 name=/usr/lib/cups/backend/cups-pdf
[    2.982954] type=1505 audit(1262565567.663:10): operation="profile_load" pid=450 name=/usr/sbin/cupsd
[    3.044144] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0000aa490c]
[    3.707202] Adding 9831740k swap on /dev/sda5.  Priority:-1 extents:1 across:9831740k 
[    3.961285] EXT4-fs (sda1): internal journal on sda1:8
[    4.496260] udev: starting version 147
[    5.704216] lp: driver loaded but no devices found
[    5.728572] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    5.728575] Disabling lock debugging due to kernel taint
[    5.743084] [fglrx] Maximum main memory to use for locked dma buffers: 3861 MBytes.
[    5.743261] [fglrx]   vendor: 1002 device: 9442 count: 1
[    5.743589] [fglrx] ioport: bar 4, base 0xa000, size: 0x100
[    5.743599] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.743603] pci 0000:01:00.0: setting latency timer to 64
[    5.743775] [fglrx] Kernel PAT support is enabled
[    5.743789] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[    6.635268] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.056729]   alloc irq_desc for 29 on node -1
[    7.056731]   alloc kstat_irqs on node -1
[    7.056742] ATL1E 0000:02:00.0: irq 29 for MSI/MSI-X
[    7.056871] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[    7.056947] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.057067] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.372260] __ratelimit: 3 callbacks suppressed
[    8.372262] type=1505 audit(1262565573.051:12): operation="profile_replace" pid=994 name=/usr/share/gdm/guest-session/Xsession
[    8.373334] type=1505 audit(1262565573.055:13): operation="profile_replace" pid=995 name=/sbin/dhclient3
[    8.373814] type=1505 audit(1262565573.055:14): operation="profile_replace" pid=995 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.374074] type=1505 audit(1262565573.055:15): operation="profile_replace" pid=995 name=/usr/lib/connman/scripts/dhclient-script
[    8.376387] type=1505 audit(1262565573.055:16): operation="profile_replace" pid=996 name=/usr/bin/evince
[    8.384073] type=1505 audit(1262565573.063:17): operation="profile_replace" pid=996 name=/usr/bin/evince-previewer
[    8.388698] type=1505 audit(1262565573.071:18): operation="profile_replace" pid=996 name=/usr/bin/evince-thumbnailer
[    8.394747] type=1505 audit(1262565573.075:19): operation="profile_replace" pid=999 name=/usr/lib/cups/backend/cups-pdf
[    8.395308] type=1505 audit(1262565573.075:20): operation="profile_replace" pid=999 name=/usr/sbin/cupsd
[    8.396870] type=1505 audit(1262565573.079:21): operation="profile_replace" pid=1000 name=/usr/sbin/tcpdump
[   10.298269] ppdev: user-space parallel port driver
[   10.749190]   alloc irq_desc for 30 on node -1
[   10.749192]   alloc kstat_irqs on node -1
[   10.749200] fglrx_pci 0000:01:00.0: irq 30 for MSI/MSI-X
[   10.749596] [fglrx] Firegl kernel thread PID: 1251
[   11.265376] CPU0 attaching NULL sched-domain.
[   11.265379] CPU1 attaching NULL sched-domain.
[   11.304031] CPU0 attaching sched-domain:
[   11.304033]  domain 0: span 0-1 level MC
[   11.304035]   groups: 0 1
[   11.304038]   domain 1: span 0-1 level CPU
[   11.304039]    groups: 0-1 (__cpu_power = 2048)
[   11.304043] CPU1 attaching sched-domain:
[   11.304044]  domain 0: span 0-1 level MC
[   11.304045]   groups: 1 0
[   11.304048]   domain 1: span 0-1 level CPU
[   11.304049]    groups: 0-1 (__cpu_power = 2048)
[   12.565120] [fglrx] Gart USWC size:1256 M.
[   12.565123] [fglrx] Gart cacheable size:499 M.
[   12.565127] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   12.565128] [fglrx] Reserved FB block: Unshared offset:fc11000, size:3ef000 
[   12.565130] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   15.657961] CPU0 attaching NULL sched-domain.
[   15.657964] CPU1 attaching NULL sched-domain.
[   15.672044] CPU0 attaching sched-domain:
[   15.672048]  domain 0: span 0-1 level MC
[   15.672050]   groups: 0 1
[   15.672055] CPU1 attaching sched-domain:
[   15.672057]  domain 0: span 0-1 level MC
[   15.672059]   groups: 1 0
[   17.280504] eth0: no IPv6 routers present


edit

I am uninstalling esound and puting pulseaudio back.  I need help!

---

### Post by suncross on 2010-01-03
edit nvm it installed ok.

Still having problems

---

### Post by Chris Edgell on 2010-01-03
Would you like to read my post about "How I got my sound back"?

[http://ubuntuforums.org/showpost.php?p=8581418&postcount=3](http://ubuntuforums.org/showpost.php?p=8581418&postcount=3)

I will consider any feedback in a positive light.  I would even like any questions that I asked to be answered.  

Suncross, I am sending my post to you for you to see if there is anything that comes clear that hasn't been clear so far.

Best wishes to you...

---

### Post by suncross on 2010-01-03
None of that helped me, and I am still having problems.

---

### Post by spiderbatdad on 2010-01-03
can you show the return of this command?
```
modinfo soundcore
```
Also please post your alsa-base.conf, inside code tags...use the # symbol in the reply editor.
Also the return of
```
lsmod | grep snd
```

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> can you show the return of this command?
```
modinfo soundcore
```Also please post your alsa-base.conf, inside code tags...use the # symbol in the reply editor.


filename:       /lib/modules/2.6.31-16-generic-pae/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-16-generic-pae SMP mod_unload modversions 586 

That is what it showed.  Also, where is the alsa-base.conf located?

---

### Post by spiderbatdad on 2010-01-03
one more thing please:
```
lsmod | grep snd
```
In /etc/modprobe.d/

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> one more thing please:
```
lsmod | grep snd
```In /etc/modprobe.d/

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel probe_mask=1 model=6stack-dell
```That was the /etc/modprobe.d/alsa-base.conf

And now for the 

lsmod | grep snd
Nothing happened when I typed that code in.

I thought I might add a picture of my alsa mixer, as there is no PCM.

---

### Post by spiderbatdad on 2010-01-03
ok. Put a # in front of options snd-hda-intel power_save=10 power_save_controller=N

So:```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Make it look like.
```
#options snd-hda-intel power_save=10 power_save_controller=N

```
Then run in terminal:
```
sudo modprobe snd-hda-intel && sudo modprobe snd-pcm-oss && sudo modprobe snd-mixer-oss && sudo modprobe snd-seq-oss

```
Then create a file called .asoundrc in your home directory.
Paste in this:
```
  pcm.hda-intel {
          type hw
          card 0
       }
       
       ctl.hda-intel {
          type hw
          card 0
       }

```
Restart and recheck all your volume levels in alsamixer and on your panel. Make sure you are not muted.

---

### Post by Eisenwinter on 2010-01-03
Might help you if you install ALSA from source.

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> ok. Put a # in front of options snd-hda-intel power_save=10 power_save_controller=N

So:```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Make it look like.
```
#options snd-hda-intel power_save=10 power_save_controller=N

```Then run in terminal:
```
sudo modprobe snd-hda-intel && sudo modprobe snd-pcm-oss && sudo modprobe snd-mixer-oss && sudo modprobe snd-seq-oss

```Then create a file called .asoundrc in your home directory.
Paste in this:
```
  pcm.hda-intel {
          type hw
          card 0
       }
       
       ctl.hda-intel {
          type hw
          card 0
       }

```Restart and recheck all your volume levels in alsamixer and on your panel. Make sure you are not muted.

the code 
sudo modprobe snd-hda-intel && sudo modprobe snd-pcm-oss && sudo modprobe snd-mixer-oss && sudo modprobe snd-seq-oss
does not work.  it says 

```
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

```
[FONT=monospace]


[/FONT]

---

### Post by sandyd on 2010-01-03
> **suncross said:**
> the code 
sudo modprobe snd-hda-intel && sudo modprobe snd-pcm-oss && sudo modprobe snd-mixer-oss && sudo modprobe snd-seq-oss
does not work.  it says 

```
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.31-16-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory

```[FONT=monospace]


[/FONT]
i think i have the problem. but im not sure.
Why are you using the generic-pae kernel?

i **think** the generic-pae kernel has different modules than the generic kernel, or the kernel is missing some of the kernel modules. This is because all of those files above exist on my system (even though its a x64 bit system).
Another theory is that alsa was incorrectly installed. those are all modules that are placed there and provided by ALSA

---

### Post by spiderbatdad on 2010-01-03
well that looks bad. You may have to build alsa from source or  check synaptic package manager for packages like
alsa-base
alsa-utils
libasound2
libasound2-plugins
libsdl1.2-alsa
linux-sound-base
gstreamer0.10-alsa
liblash2

Sorry you're having this problem.

---

### Post by suncross on 2010-01-03
> **carlee said:**
> i think i have the problem. but im not sure.
Why are you using the generic-pae kernel?

i **think** the generic-pae kernel has different modules than the generic kernel, or the kernel is missing some of the kernel modules. This is because all of those files above exist on my system (even though its a x64 bit system).
Another theory is that alsa was incorrectly installed. those are all modules that are placed there and provided by ALSA

What does that mean?  Should I reinstall ubuntu or alsa?

---

### Post by suncross on 2010-01-03
> **spiderbatdad said:**
> well that looks bad. You may have to build alsa from source or  check synaptic package manager for packages like
alsa-base
alsa-utils
libasound2
libasound2-plugins
libsdl1.2-alsa
linux-sound-base
gstreamer0.10-alsa
liblash2

Sorry you're having this problem.

Ok liblash2 was not installed, so I am doing that now

Also, there was no libsdl1.2-alsa, but variations of it.

---

### Post by suncross on 2010-01-03
Its not even recognizing hardware :/

---

### Post by spiderbatdad on 2010-01-03
That package is not going to make the diff. I believe carlee hit on the problem. And I'm not sure how to advise you. You can rebuild alsa from source. It's tricky the first time you try, but not impossible. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
That link should have instruction near the end called update to latest version of alsa. Sorry I've exhausted my ideas beyond that.
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by suncross on 2010-01-03
Ok well stay tuned because I might need some help compiling or whatever.  I am a complete noob.

However if this doesn't make you laugh I dont know what will: I booted from a live cd and sound works...  What does that mean lol?

---

### Post by spiderbatdad on 2010-01-03
by the time you're done with all this, you'll have definitely gotten your feet wet in linux.

---

### Post by suncross on 2010-01-03
I cant get past the first step in that how to...

```

cat /proc/asound/card0/codec#* | grep Codec
```

It returns:

```
cat: /proc/asound/card0/codec#*: No such file or directory

```

What does this mean?

---

### Post by sandyd on 2010-01-03
> **suncross said:**
> I cant get past the first step in that how to...

```

cat /proc/asound/card0/codec#* | grep Codec
```It returns:

```
cat: /proc/asound/card0/codec#*: No such file or directory

```What does this mean?
oh no......
are you very. extremely. extrodinarily true youve installed ubuntu properly. with all updates that is.

because that file exists on 4 computers. - all thaat ive checked

alright.
run this.
```

sudo dpkg --purge alsa-base alsa-utils alsa-tools pulseaudio pulseaudio-*
sudo apt-get install alsa-base alsa-utils alsa-tools

```

---

### Post by suncross on 2010-01-03
OMG I think that alsa script thing sort of worked.  I heard the bongos on the log in page, but not the audio while logged in.

---

### Post by suncross on 2010-01-03
Holy crap holy crap I can hear stuff, but now everything is mega quiet...  Trying alsamixer

Edit.  I am in alsamixer, but I do not know how to increase the volume?

edit, added a screenshot

---

### Post by sandyd on 2010-01-03
good to see it worked out.
have fun!
hey wait... what in the world... i just removed pulseaudio and it still says pulseaudio on the alsamixer screenshot lol.
oh well. as long as its working im not going to touch it...

---

### Post by sandyd on 2010-01-03
> **suncross said:**
> Holy crap holy crap I can hear stuff, but now everything is mega quiet...  Trying alsamixer

Edit.  I am in alsamixer, but I do not know how to increase the volume?

edit, added a screenshot
push the up key
screenshot looking good.
to move from one control to the other, use the left/right keys

---

### Post by suncross on 2010-01-03
> **carlee said:**
> push the up key
screenshot looking good.
to move from one control to the other, use the left/right keys

It doesn't work though.  When I try to click up, it doesn't go up.

Edit.

I almost had a heart attack.  I put numlock on and did the up key from the num pad.  Wow that was loud.

Thank you so much everyone, you all have been a great help.  My install is working 100% now and I am very very happy.  Till next time, audio gods.

---

