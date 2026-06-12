---
title: "unrecognised dvd drive."
date: 2009-08-08
forum: New to Ubuntu
---

### Post by fidelandche on 2009-08-08
My Gateway ML6226B laptop with Jaunty installed as the only OS will not play DVD's. The drive will not recognize media, the DVD's work fine my another laptop with Jaunty installed as the only OS, what can I do?

---

### Post by halitech on 2009-08-08
do cds work? do you have a boot cd you can try booting from to see if it works?

---

### Post by fidelandche on 2009-08-08
I tried putting in a audio cd, it asked me what to open with, I went for rhythm box, but the cd did not play. It appears that the drive is unmountable.

---

### Post by halitech on 2009-08-08
do you have a data cd you can put in? with a data cd inserted, open a terminal and post the results of
```
sudo fdisk -l
```and ```
mount
```

---

### Post by Liolikas on 2009-08-08
Try:
```

sudo mkdir /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom

```
And post errors here.

---

### Post by fidelandche on 2009-08-08
from the first I get this
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a71cf53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9547    76686246   83  Linux
/dev/sda2            9548        9729     1461915    5  Extended
/dev/sda5            9548        9729     1461883+  82  Linux swap / Solaris

from the second I get this
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andy)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=andy)

I then get the following

mount: /dev/sr0: unknown device

 I think I should have  posted both the codes together in the terminal, this is the message,

andy@andy-laptop:~$ sudo mkdir /mnt/cdrom
mkdir: cannot create directory `/mnt/cdrom': File exists
andy@andy-laptop:~$ sudo mount /dev/cdrom /mnt/cdrom
mount: /dev/sr0: unknown device

---

### Post by Liolikas on 2009-08-08
It can mean that drive do not work at all...
Use pastebin.com to show 
```

dmesg

```

---

### Post by fidelandche on 2009-08-08
From that code, I get the following;

   0.551375] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.551443] pci 0000:00:1f.2: reg 10 io port: [0x18d0-0x18d7]
[    0.551451] pci 0000:00:1f.2: reg 14 io port: [0x18c4-0x18c7]
[    0.551460] pci 0000:00:1f.2: reg 18 io port: [0x18c8-0x18cf]
[    0.551468] pci 0000:00:1f.2: reg 1c io port: [0x18c0-0x18c3]
[    0.551477] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.551485] pci 0000:00:1f.2: reg 24 32bit mmio: [0xd4444400-0xd44447ff]
[    0.551507] pci 0000:00:1f.2: PME# supported from D3hot
[    0.551513] pci 0000:00:1f.2: PME# disabled
[    0.551582] pci 0000:00:1f.3: reg 20 io port: [0x18e0-0x18ff]
[    0.551700] pci 0000:02:00.0: reg 10 64bit mmio: [0xd2000000-0xd2003fff]
[    0.551711] pci 0000:02:00.0: reg 18 io port: [0x2000-0x20ff]
[    0.551763] pci 0000:02:00.0: supports D1 D2
[    0.551765] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.551772] pci 0000:02:00.0: PME# disabled
[    0.551841] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.551847] pci 0000:00:1c.0: bridge 32bit mmio: [0xd2000000-0xd3ffffff]
[    0.551856] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd1ffffff]
[    0.551927] pci 0000:03:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.551942] pci 0000:03:09.0: supports D1 D2
[    0.551944] pci 0000:03:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.551950] pci 0000:03:09.0: PME# disabled
[    0.552008] pci 0000:03:09.1: reg 10 32bit mmio: [0xd4005000-0xd40057ff]
[    0.552019] pci 0000:03:09.1: reg 14 32bit mmio: [0xd4000000-0xd4003fff]
[    0.552072] pci 0000:03:09.1: supports D1 D2
[    0.552074] pci 0000:03:09.1: PME# supported from D0 D1 D2 D3hot
[    0.552080] pci 0000:03:09.1: PME# disabled
[    0.552132] pci 0000:03:09.2: reg 10 32bit mmio: [0xd4004000-0xd4004fff]
[    0.552193] pci 0000:03:09.2: supports D1 D2
[    0.552195] pci 0000:03:09.2: PME# supported from D0 D1 D2 D3hot
[    0.552201] pci 0000:03:09.2: PME# disabled
[    0.552262] pci 0000:00:1e.0: transparent bridge
[    0.552270] pci 0000:00:1e.0: bridge 32bit mmio: [0xd4000000-0xd40fffff]
[    0.552317] bus 00 -> node 0
[    0.552325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.552771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.552955] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.555288] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.555421] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.555551] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.555680] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.555818] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.555949] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.556089] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.556217] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11 12 14 15)
[    0.556566] ACPI: WMI: Mapper loaded
[    0.556756] SCSI subsystem initialized
[    0.556798] libata version 3.00 loaded.
[    0.556846] usbcore: registered new interface driver usbfs
[    0.556864] usbcore: registered new interface driver hub
[    0.556893] usbcore: registered new device driver usb
[    0.557014] PCI: Using ACPI for IRQ routing
[    0.557135] Bluetooth: Core ver 2.13
[    0.557135] NET: Registered protocol family 31
[    0.557135] Bluetooth: HCI device and connection manager initialized
[    0.557135] Bluetooth: HCI socket layer initialized
[    0.557135] NET: Registered protocol family 8
[    0.557135] NET: Registered protocol family 20
[    0.557135] NetLabel: Initializing
[    0.557135] NetLabel:  domain hash size = 128
[    0.557135] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.557135] NetLabel:  unlabeled traffic allowed by default
[    0.557135] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.557135] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.560077] AppArmor: AppArmor Filesystem Enabled
[    0.560086] pnp: PnP ACPI init
[    0.560086] ACPI: bus type pnp registered
[    0.562015] pnp: PnP ACPI: found 9 devices
[    0.562017] ACPI: ACPI bus type pnp unregistered
[    0.562024] PnPBIOS: Disabled by ACPI PNP
[    0.562035] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.562038] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.562041] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.562044] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.562048] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.562051] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.562054] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.562061] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.562068] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.562071] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.562074] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.562077] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.562080] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.562084] system 00:05: iomem range 0xff000000-0xffffffff has been reserved
[    0.564017] Switched to high resolution mode on CPU 0
[    0.597929] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.597933] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.597940] pci 0000:00:1c.0:   MEM window: 0xd2000000-0xd3ffffff
[    0.597946] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.597962] pci 0000:03:09.0: CardBus bridge, secondary bus 0000:04
[    0.597964] pci 0000:03:09.0:   IO window: 0x003000-0x0030ff
[    0.597970] pci 0000:03:09.0:   IO window: 0x003400-0x0034ff
[    0.597976] pci 0000:03:09.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.597982] pci 0000:03:09.0:   MEM window: 0x34000000-0x37ffffff
[    0.597988] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.597992] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.597999] pci 0000:00:1e.0:   MEM window: 0xd4000000-0xd40fffff
[    0.598005] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
[    0.598024] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.598031] pci 0000:00:1c.0: setting latency timer to 64
[    0.598037] pci 0000:00:1e.0: enabling device (0004 -> 0007)
[    0.598044] pci 0000:00:1e.0: setting latency timer to 64
[    0.598054] pci 0000:03:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.598062] bus: 00 index 0 io port: [0x00-0xffff]
[    0.598064] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.598067] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.598069] bus: 02 index 1 mmio: [0xd2000000-0xd3ffffff]
[    0.598072] bus: 02 index 2 mmio: [0xd0000000-0xd1ffffff]
[    0.598074] bus: 02 index 3 mmio: [0x0-0x0]
[    0.598076] bus: 03 index 0 io port: [0x3000-0x3fff]
[    0.598079] bus: 03 index 1 mmio: [0xd4000000-0xd40fffff]
[    0.598081] bus: 03 index 2 mmio: [0x30000000-0x33ffffff]
[    0.598083] bus: 03 index 3 io port: [0x00-0xffff]
[    0.598086] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.598088] bus: 04 index 0 io port: [0x3000-0x30ff]
[    0.598090] bus: 04 index 1 io port: [0x3400-0x34ff]
[    0.598093] bus: 04 index 2 mmio: [0x30000000-0x33ffffff]
[    0.598095] bus: 04 index 3 mmio: [0x34000000-0x37ffffff]
[    0.598106] NET: Registered protocol family 2
[    0.598226] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.598441] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.598509] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.598579] TCP: Hash tables configured (established 16384 bind 16384)
[    0.598581] TCP reno registered
[    0.598656] NET: Registered protocol family 1
[    0.598787] checking if image is initramfs... it is
[    1.346271] Freeing initrd memory: 7368k freed
[    1.346322] Simple Boot Flag at 0x36 set to 0x1
[    1.346425] cpufreq: No nForce2 chipset.
[    1.346586] audit: initializing netlink socket (disabled)
[    1.346609] type=2000 audit(1249735696.344:1): initialized
[    1.355235] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.356619] VFS: Disk quotas dquot_6.5.1
[    1.356675] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.357326] fuse init (API version 7.10)
[    1.357418] msgmni has been set to 975
[    1.357599] alg: No test for stdrng (krng)
[    1.357612] io scheduler noop registered
[    1.357615] io scheduler anticipatory registered
[    1.357617] io scheduler deadline registered
[    1.357633] io scheduler cfq registered (default)
[    1.357651] pci 0000:00:02.0: Boot video device
[    1.361862] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.361918] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.361958] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.361975] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.361993] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.362006] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.362093] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.362135] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.363477] ACPI: AC Adapter [ACAD] (off-line)
[    1.408136] ACPI: Battery Slot [BAT1] (battery present)
[    1.408218] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.408221] ACPI: Power Button (FF) [PWRF]
[    1.408270] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.408273] ACPI: Power Button (CM) [PWRB]
[    1.408316] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.408319] ACPI: Sleep Button (CM) [SLPB]
[    1.408366] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.409730] ACPI: Lid Switch [LID]
[    1.410407] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.410432] processor ACPI_CPU:00: registered as cooling_device0
[    1.417061] thermal LNXTHERM:01: registered as thermal_zone0
[    1.425178] ACPI: Thermal Zone [TZ00] (30 C)
[    1.425227] isapnp: Scanning for PnP cards...
[    1.779194] isapnp: No Plug & Play device found
[    1.780546] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.781623] brd: module loaded
[    1.781935] loop: module loaded
[    1.782005] Fixed MDIO Bus: probed
[    1.782012] PPP generic driver version 2.4.2
[    1.782076] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.782108] Driver 'sd' needs updating - please use bus_type methods
[    1.782118] Driver 'sr' needs updating - please use bus_type methods
[    1.782159] ahci 0000:00:1f.2: version 3.0
[    1.782171] ahci 0000:00:1f.2: power state changed by ACPI to D0
[    1.782186] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.782231] ahci 0000:00:1f.2: irq 2302 for MSI/MSI-X
[    1.782312] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.782316] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.782322] ahci 0000:00:1f.2: setting latency timer to 64
[    1.782574] scsi0 : ahci
[    1.782761] scsi1 : ahci
[    1.783006] scsi2 : ahci
[    1.783210] scsi3 : ahci
[    1.783306] ata1: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444500 irq 2302
[    1.783309] ata2: DUMMY
[    1.783312] ata3: SATA max UDMA/133 abar m1024@0xd4444400 port 0xd4444600 irq 2302
[    1.783314] ata4: DUMMY
[    2.100022] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.101017] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.101089] ata1.00: ATA-7: ST980811AS, 3.ALB, max UDMA/133
[    2.101092] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.102236] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.102330] ata1.00: configured for UDMA/133
[    2.436019] ata3: SATA link down (SStatus 0 SControl 300)
[    2.452133] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    2.452242] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.452260] sd 0:0:0:0: [sda] Write Protect is off
[    2.452263] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.452289] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.452359] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.452374] sd 0:0:0:0: [sda] Write Protect is off
[    2.452377] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.452402] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.452405]  sda: sda1 sda2 < sda5 >
[    2.502002] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.502053] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.502109] ata_piix 0000:00:1f.1: version 2.12
[    2.502121] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.502161] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.502248] scsi4 : ata_piix
[    2.502307] scsi5 : ata_piix
[    2.502959] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.502962] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.664504] ata5.00: ATAPI: Optiarc DVD RW AD-7530A, EX32, max UDMA/33
[    2.680445] ata5.00: configured for UDMA/33
[    2.681049] ata6: port disabled. ignoring.
[    2.682381] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX32 PQ: 0 ANSI: 5
[    2.692198] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.692204] Uniform CD-ROM driver Revision: 3.20
[    2.692313] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.692358] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.692937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.692962] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.692984] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.692988] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.693055] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.696959] ehci_hcd 0000:00:1d.7: debug port 1
[    2.696968] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.696984] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4444000
[    2.712010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.712093] usb usb1: configuration #1 chosen from 1 choice
[    2.712121] hub 1-0:1.0: USB hub found
[    2.712130] hub 1-0:1.0: 8 ports detected
[    2.712247] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.712262] uhci_hcd: USB Universal Host Controller Interface driver
[    2.712291] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.712299] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.712303] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.712345] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.712373] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.712449] usb usb2: configuration #1 chosen from 1 choice
[    2.712477] hub 2-0:1.0: USB hub found
[    2.712487] hub 2-0:1.0: 2 ports detected
[    2.712570] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.712577] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.712580] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.712621] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.712657] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.712734] usb usb3: configuration #1 chosen from 1 choice
[    2.712759] hub 3-0:1.0: USB hub found
[    2.712765] hub 3-0:1.0: 2 ports detected
[    2.712856] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.712863] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.712867] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.712908] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.712944] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.713020] usb usb4: configuration #1 chosen from 1 choice
[    2.713045] hub 4-0:1.0: USB hub found
[    2.713053] hub 4-0:1.0: 2 ports detected
[    2.713137] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.713144] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.713148] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.713196] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.713231] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.713307] usb usb5: configuration #1 chosen from 1 choice
[    2.713333] hub 5-0:1.0: USB hub found
[    2.713342] hub 5-0:1.0: 2 ports detected
[    2.713486] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2P] at 0x60,0x64 irq 1,12
[    2.715273] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.715279] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.715404] mice: PS/2 mouse device common for all mice
[    2.715613] rtc_cmos 00:06: RTC can wake from S4
[    2.715651] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.715684] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.715756] device-mapper: uevent: version 1.0.3
[    2.715866] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.715911] device-mapper: multipath: version 1.0.5 loaded
[    2.715914] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.715987] EISA: Probing bus 0 at eisa.0
[    2.715995] Cannot allocate resource for EISA slot 1
[    2.715998] Cannot allocate resource for EISA slot 2
[    2.716009] Cannot allocate resource for EISA slot 3
[    2.716032] EISA: Detected 0 cards.
[    2.716088] cpuidle: using governor ladder
[    2.716136] cpuidle: using governor menu
[    2.716613] TCP cubic registered
[    2.716714] NET: Registered protocol family 10
[    2.717095] lo: Disabled Privacy Extensions
[    2.717384] NET: Registered protocol family 17
[    2.717404] Bluetooth: L2CAP ver 2.11
[    2.717406] Bluetooth: L2CAP socket layer initialized
[    2.717409] Bluetooth: SCO (Voice Link) ver 0.6
[    2.717411] Bluetooth: SCO socket layer initialized
[    2.717440] Bluetooth: RFCOMM socket layer initialized
[    2.717447] Bluetooth: RFCOMM TTY layer initialized
[    2.717449] Bluetooth: RFCOMM ver 1.10
[    2.717490] Using IPI No-Shortcut mode
[    2.717568] registered taskstats version 1
[    2.717683]   Magic number: 5:671:834
[    2.717771] rtc_cmos 00:06: setting system clock to 2009-08-08 12:48:18 UTC (1249735698)
[    2.717775] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.717777] EDD information not available.
[    2.718060] Freeing unused kernel memory: 532k freed
[    2.718157] Write protecting the kernel text: 4116k
[    2.718191] Write protecting the kernel read-only data: 1528k
[    2.758908] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.024022] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    3.162620] usb 1-5: configuration #1 chosen from 1 choice
[    3.331185] sky2 driver version 1.22
[    3.331232] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.331245] sky2 0000:02:00.0: setting latency timer to 64
[    3.331294] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    3.395062] sky2 0000:02:00.0: Marvell Yukon 88E8038 Fast Ethernet Controller
[    3.395065]  Part Number: Yukon 88E8038
[    3.395067]  Engineering Level: Rev. 1.4
[    3.395069]  Manufacturer: Marvell
[    3.395147] sky2 0000:02:00.0: irq 2301 for MSI/MSI-X
[    3.400285] sky2 eth0: addr 00:e0:b8:c6:19:25
[    3.436572] ohci1394 0000:03:09.1: enabling device (0000 -> 0002)
[    3.436582] ohci1394 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.436592] ohci1394 0000:03:09.1: setting latency timer to 64
[    3.486342] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[d4005000-d40057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.769971] Marking TSC unstable due to TSC halts in idle
[    3.991910] PM: Starting manual resume from disk
[    3.991914] PM: Resume from partition 8:5
[    3.991916] PM: Checking hibernation image.
[    3.992085] PM: Resume from disk failed.
[    4.038340] kjournald starting.  Commit interval 5 seconds
[    4.038351] EXT3-fs: mounted filesystem with ordered data mode.
[    4.760151] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80366097302]
[   10.372180] udev: starting version 141
[   10.671473] Linux agpgart interface v0.103
[   10.726368] acpi device:0a: registered as cooling_device1
[   10.726719] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/input/input6
[   10.752223] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.777054] intel_rng: FWH not detected
[   10.924137] cfg80211: Calling CRDA to update world regulatory domain
[   11.145519] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   11.145763] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.149042] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.216434] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.217516] cfg80211: World regulatory domain updated:
[   11.217520]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.217523]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.217526]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.217529]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.217532]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.217534]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.307047] yenta_cardbus 0000:03:09.0: CardBus bridge found [107b:0366]
[   11.307074] yenta_cardbus 0000:03:09.0: Using CSCINT to route CSC interrupts to PCI
[   11.307077] yenta_cardbus 0000:03:09.0: Routing CardBus interrupts to PCI
[   11.307083] yenta_cardbus 0000:03:09.0: TI: mfunc 0x01ac1b22, devctl 0x64
[   11.419076] iTCO_vendor_support: vendor-support=0
[   11.444970] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.445134] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   11.445229] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.463257] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.537084] yenta_cardbus 0000:03:09.0: ISA IRQ mask 0x0cf8, PCI irq 17
[   11.537090] yenta_cardbus 0000:03:09.0: Socket status: 30000006
[   11.537094] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   11.537102] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   11.537106] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   11.537350] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd40fffff
[   11.537353] yenta_cardbus 0000:03:09.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   11.537848] tifm_7xx1 0000:03:09.2: enabling device (0000 -> 0002)
[   11.537857] tifm_7xx1 0000:03:09.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.537866] tifm_7xx1 0000:03:09.2: setting latency timer to 64
[   12.079074] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.200682] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.200844] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.227687] nf_conntrack version 0.5.0 (8041 buckets, 32164 max)
[   12.227923] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   12.227927] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.227929] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.272127] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.274189] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.275051] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.275769] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.276678] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.357025] phy0: Selected rate control algorithm 'pid'
[   12.360607] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   12.393427] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   12.481767] phy0: hwaddr 00:c0:a8:e0:94:ca, RTL8187vB (default) V1 + rtl8225z2
[   12.481792] usbcore: registered new interface driver rtl8187
[   12.642493] lp: driver loaded but no devices found
[   12.713648] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[   12.730745] EXT3 FS on sda1, internal journal
[   13.180293] type=1505 audit(1249735708.962:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2005
[   13.235667] type=1505 audit(1249735709.014:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2009
[   13.235823] type=1505 audit(1249735709.014:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2009
[   13.235877] type=1505 audit(1249735709.014:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2009
[   13.235924] type=1505 audit(1249735709.014:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2009
[   13.270193] type=1505 audit(1249735709.050:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2014
[   13.425879] type=1505 audit(1249735709.206:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2018
[   13.426117] type=1505 audit(1249735709.206:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2018
[   13.458479] type=1505 audit(1249735709.238:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2022
[   16.348293] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.348297] Bluetooth: BNEP filters: protocol multicast
[   16.362118] Bridge firewalling registered
[   17.834136] ppdev: user-space parallel port driver
[   19.346478] [drm] Initialized drm 1.1.0 20060810
[   19.353218] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.353225] pci 0000:00:02.0: setting latency timer to 64
[   19.353395] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   19.433212] [drm:i915_setparam] *ERROR* unknown parameter 4
[   19.433238] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.966751] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   21.222957] sky2 eth0: enabling interface
[   21.223020] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.897451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.872687] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   38.481442] wlan0: authenticate with AP 00:23:4e:9e:f5:19
[   38.483812] wlan0: authenticated
[   38.483816] wlan0: associate with AP 00:23:4e:9e:f5:19
[   38.486448] wlan0: RX AssocResp from 00:23:4e:9e:f5:19 (capab=0x411 status=0 aid=1)
[   38.486452] wlan0: associated
[   38.487419] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.011566] padlock: VIA PadLock not detected.
[   44.339760] CPU0 attaching NULL sched-domain.
[   44.339845] CPU0 attaching NULL sched-domain.
[   48.856027] wlan0: no IPv6 routers present
[ 2914.754874] end_request: I/O error, dev sr0, sector 0
[ 2914.754881] Buffer I/O error on device sr0, logical block 0
[ 2914.754885] Buffer I/O error on device sr0, logical block 1
[ 2914.754890] Buffer I/O error on device sr0, logical block 2
[ 2914.754893] Buffer I/O error on device sr0, logical block 3
[ 2914.754895] Buffer I/O error on device sr0, logical block 4
[ 2914.754898] Buffer I/O error on device sr0, logical block 5
[ 2914.754901] Buffer I/O error on device sr0, logical block 6
[ 2914.754904] Buffer I/O error on device sr0, logical block 7
[ 2914.760745] end_request: I/O error, dev sr0, sector 0
[ 2914.760752] Buffer I/O error on device sr0, logical block 0
[ 2914.760756] Buffer I/O error on device sr0, logical block 1
[ 3624.853312] CPU0 attaching NULL sched-domain.
[ 3624.853399] CPU0 attaching NULL sched-domain.
[ 4225.419392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4226.493617] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 5809.261969] UDF-fs: No VRS found
[ 6924.666657] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 6925.184929] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 7524.930307] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 8124.969146] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 8725.219211] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9325.148615] [drm:i915_getparam] *ERROR* Unknown parameter 6

---

### Post by fidelandche on 2009-08-08
Just tried an audio CD again and this works using the VLC media player. It was a bit choppy at the start but the play back was good in the end. So I think it appears to be a problem with DVD's. Update, just tried playing DVD's and guess what             its now working!!!!!!!!!! So unsure of what has happened.

---

