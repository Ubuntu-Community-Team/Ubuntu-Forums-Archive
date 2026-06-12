---
title: "Install TRENDnet USB Adapter TEW-648UB in Ubuntu 13.04."
date: 2013-09-13
forum: Networking &amp; Wireless
---

### Post by DianaRobledo on 2013-09-13
Hey!

I can't install my new TRENDnet USB Adapter TEW-648UB. Mi Ubuntu version is 13.04. And i'n absolutely new in ubuntu and don't know how to use the terminal. After I wrote:

lsusb

Appeared: 

Bus 002 Device 002: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter
Bus 005 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 005 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2013-09-13
I have asked that this be moved to Networking and Wireless, however, in the meantime, your device is covered by the driver r8712u that is already present in Ubuntu 13.04. Let's see if it loaded as expected. From the terminal Ctrl+Alt+t:```
lsmod | grep r8712u
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Did the module load? If not, load it explicitly:```
sudo modprobe r8712u
```Now is it working? Are there any clues in the message logs?```
dmesg | grep r8712u
```Copy and past the results here and we'll proceed.

---

### Post by DianaRobledo on 2013-09-13
It says:

r8712u                162545  0

---

### Post by chili555 on 2013-09-13
> **DianaRobledo said:**
> It says:

r8712u                162545  0Very good! Please proceed to the next steps. I think *dmesg* will tell us why it isn't working.

---

### Post by DianaRobledo on 2013-09-13
Ufff! It says all this stuff:

```
[    0.129023] system 00:0a: [mem 0x3f600000-0x3f6fffff] could not be reserved
[    0.129027] system 00:0a: [mem 0xfed00000-0xfed000ff] has been reserved
[    0.129032] system 00:0a: [mem 0x3f590000-0x3f5fffff] could not be reserved
[    0.129036] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.129040] system 00:0a: [mem 0x00100000-0x3f58ffff] could not be reserved
[    0.129045] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.129049] system 00:0a: [mem 0xfed14000-0xfed1dfff] has been reserved
[    0.129053] system 00:0a: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.129058] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.129062] system 00:0a: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.129066] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.129070] system 00:0a: [mem 0x000e0000-0x000effff] has been reserved
[    0.129076] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.129089] pnp: PnP ACPI: found 11 devices
[    0.129092] ACPI: ACPI bus type pnp unregistered
[    0.129096] PnPBIOS: Disabled by ACPI PNP
[    0.166290] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.166297] pci 0000:00:01.0:   bridge window [io  0xc000-0xcfff]
[    0.166304] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.166309] pci 0000:00:01.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.166316] pci 0000:00:1e.0: PCI bridge to [bus 02]
[    0.166320] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.166327] pci 0000:00:1e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.166333] pci 0000:00:1e.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.166364] pci 0000:00:1e.0: setting latency timer to 64
[    0.166370] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.166373] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.166377] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.166381] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.166385] pci_bus 0000:01: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.166389] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.166392] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.166396] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.166399] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.166403] pci_bus 0000:02: resource 5 [mem 0x00000000-0xfffffffff]
[    0.166452] NET: Registered protocol family 2
[    0.166678] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.166715] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.166747] TCP: Hash tables configured (established 8192 bind 8192)
[    0.166777] TCP: reno registered
[    0.166781] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.166792] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.166868] NET: Registered protocol family 1
[    0.166888] pci 0000:00:02.0: Boot video device
[    0.167112] PCI: CLS 64 bytes, default 64
[    0.167171] Trying to unpack rootfs image as initramfs...
[    0.590875] Freeing initrd memory: 15680k freed
[    0.599424] Initialise module verification
[    0.599489] audit: initializing netlink socket (disabled)
[    0.599507] type=2000 audit(1379087697.596:1): initialized
[    0.630464] bounce pool size: 64 pages
[    0.630481] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.632655] VFS: Disk quotas dquot_6.5.2
[    0.632726] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.633545] fuse init (API version 7.20)
[    0.633675] msgmni has been set to 1739
[    0.634190] Key type asymmetric registered
[    0.634194] Asymmetric key parser 'x509' registered
[    0.634249] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.634284] io scheduler noop registered
[    0.634288] io scheduler deadline registered (default)
[    0.634299] io scheduler cfq registered
[    0.634490] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.634586] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.634610] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.634696] intel_idle: does not run on family 6 model 15
[    0.634785] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.634792] ACPI: Power Button [PWRB]
[    0.634864] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.634869] ACPI: Power Button [PWRF]
[    0.634929] ACPI: Fan [FAN] (on)
[    0.635028] ACPI: Requesting acpi_cpufreq
[    0.639265] thermal LNXTHERM:00: registered as thermal_zone0
[    0.639270] ACPI: Thermal Zone [THRM] (40 C)
[    0.639317] GHES: HEST is not enabled!
[    0.639345] isapnp: Scanning for PnP cards...
[    0.640072] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.642010] Linux agpgart interface v0.103
[    0.642133] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.642195] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.642521] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.642657] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.644659] brd: module loaded
[    0.645666] loop: module loaded
[    0.645850] ata_piix 0000:00:1f.2: version 2.13
[    0.645867] ata_piix 0000:00:1f.2: MAP [
[    0.645870]  P0 P2 P1 P3 ]
[    0.645924] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.646258] scsi0 : ata_piix
[    0.648026] scsi1 : ata_piix
[    0.648364] ata1: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    0.648370] ata2: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    0.648397] ata_piix 0000:00:1f.5: MAP [
[    0.648399]  P0 -- P1 -- ]
[    0.648447] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.648682] scsi2 : ata_piix
[    0.648963] scsi3 : ata_piix
[    0.649025] ata3: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xec00 irq 19
[    0.649030] ata4: SATA max UDMA/133 cmd 0xee00 ctl 0xed00 bmdma 0xec08 irq 19
[    0.649464] libphy: Fixed MDIO Bus: probed
[    0.649572] tun: Universal TUN/TAP device driver, 1.6
[    0.649575] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.649638] PPP generic driver version 2.4.2
[    0.649702] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.649705] ehci-pci: EHCI PCI platform driver
[    0.649742] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.649748] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.649756] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.649773] ehci-pci 0000:00:1a.7: debug port 1
[    0.653676] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.653703] ehci-pci 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    0.664018] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.664063] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.664068] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.664071] usb usb1: Product: EHCI Host Controller
[    0.664075] usb usb1: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.664078] usb usb1: SerialNumber: 0000:00:1a.7
[    0.664218] hub 1-0:1.0: USB hub found
[    0.664225] hub 1-0:1.0: 6 ports detected
[    0.664410] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.664416] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.664424] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.664439] ehci-pci 0000:00:1d.7: debug port 1
[    0.668326] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.668348] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    0.680021] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.680042] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.680046] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680050] usb usb2: Product: EHCI Host Controller
[    0.680053] usb usb2: Manufacturer: Linux 3.8.0-29-generic ehci_hcd
[    0.680057] usb usb2: SerialNumber: 0000:00:1d.7
[    0.680182] hub 2-0:1.0: USB hub found
[    0.680190] hub 2-0:1.0: 6 ports detected
[    0.680355] ehci-platform: EHCI generic platform driver
[    0.680369] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.680396] uhci_hcd: USB Universal Host Controller Interface driver
[    0.680428] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.680433] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.680440] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.680481] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fd00
[    0.680521] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.680525] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680528] usb usb3: Product: UHCI Host Controller
[    0.680532] usb usb3: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.680535] usb usb3: SerialNumber: 0000:00:1a.0
[    0.680667] hub 3-0:1.0: USB hub found
[    0.680673] hub 3-0:1.0: 2 ports detected
[    0.680779] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.680784] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.680791] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.680828] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fc00
[    0.680867] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.680871] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680875] usb usb4: Product: UHCI Host Controller
[    0.680878] usb usb4: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.680881] usb usb4: SerialNumber: 0000:00:1a.1
[    0.681003] hub 4-0:1.0: USB hub found
[    0.681009] hub 4-0:1.0: 2 ports detected
[    0.681113] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.681117] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.681124] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.681150] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fb00
[    0.681188] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.681192] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681195] usb usb5: Product: UHCI Host Controller
[    0.681199] usb usb5: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.681202] usb usb5: SerialNumber: 0000:00:1a.2
[    0.681323] hub 5-0:1.0: USB hub found
[    0.681329] hub 5-0:1.0: 2 ports detected
[    0.681439] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.681443] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.681450] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.681476] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fa00
[    0.681515] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.681519] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681523] usb usb6: Product: UHCI Host Controller
[    0.681526] usb usb6: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.681530] usb usb6: SerialNumber: 0000:00:1d.0
[    0.681651] hub 6-0:1.0: USB hub found
[    0.681660] hub 6-0:1.0: 2 ports detected
[    0.681763] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.681768] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.681775] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.681801] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f900
[    0.681838] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.681842] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681846] usb usb7: Product: UHCI Host Controller
[    0.681849] usb usb7: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.681852] usb usb7: SerialNumber: 0000:00:1d.1
[    0.681970] hub 7-0:1.0: USB hub found
[    0.681976] hub 7-0:1.0: 2 ports detected
[    0.682079] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.682084] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.682091] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.682117] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f800
[    0.682153] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.682157] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.682161] usb usb8: Product: UHCI Host Controller
[    0.682164] usb usb8: Manufacturer: Linux 3.8.0-29-generic uhci_hcd
[    0.682168] usb usb8: SerialNumber: 0000:00:1d.2
[    0.682288] hub 8-0:1.0: USB hub found
[    0.682294] hub 8-0:1.0: 2 ports detected
[    0.682492] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.682887] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.682896] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.683043] mousedev: PS/2 mouse device common for all mice
[    0.683200] rtc_cmos 00:03: RTC can wake from S4
[    0.683328] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.683356] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.683499] device-mapper: uevent: version 1.0.3
[    0.683584] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.683612] EISA: Probing bus 0 at eisa.0
[    0.683646] EISA: Detected 0 cards.
[    0.683658] cpufreq-nforce2: No nForce2 chipset.
[    0.683661] cpuidle: using governor ladder
[    0.683664] cpuidle: using governor menu
[    0.683669] ledtrig-cpu: registered to indicate activity on CPUs
[    0.683672] EFI Variables Facility v0.08 2004-May-17
[    0.683907] ashmem: initialized
[    0.684107] TCP: cubic registered
[    0.684265] NET: Registered protocol family 10
[    0.684540] NET: Registered protocol family 17
[    0.684560] Key type dns_resolver registered
[    0.684806] Using IPI No-Shortcut mode
[    0.684905] Loading module verification certificates
[    0.690878] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3f91e9adadd74ee2134f443ced3a922f70cb07ef'
[    0.690896] registered taskstats version 1
[    0.694296] Key type trusted registered
[    0.697421] Key type encrypted registered
[    0.700941] rtc_cmos 00:03: setting system clock to 2013-09-13 15:54:58 UTC (1379087698)
[    0.701499] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.701502] EDD information not available.
[    0.982737] ata3: SATA link down (SStatus 0 SControl 300)
[    0.992446] isapnp: No Plug & Play device found
[    0.993513] ata4: SATA link down (SStatus 0 SControl 300)
[    1.468086] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.468107] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.468228] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.468243] ata2.01: SATA link down (SStatus 0 SControl 300)
[    1.468255] ata2.01: link offline, clearing class 3 to NONE
[    1.476235] ata2.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H493B, D200, max UDMA/33
[    1.476505] ata1.00: ATA-7: Hitachi HDS721680PLA380, P21OAB3A, max UDMA/133
[    1.476510] ata1.00: 156250000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.488033] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    1.492286] ata2.00: configured for UDMA/33
[    1.492427] ata1.00: configured for UDMA/133
[    1.492628] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72168 P21O PQ: 0 ANSI: 5
[    1.492801] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.492843] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.492874] sd 0:0:0:0: [sda] Write Protect is off
[    1.492879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.492911] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.493539] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRWDVD TS-H493B D200 PQ: 0 ANSI: 5
[    1.495432] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.495438] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.495581] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.495711] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.554584]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.555148] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.555238] Freeing unused kernel memory: 788k freed
[    1.555514] Write protecting the kernel text: 6260k
[    1.555620] Write protecting the kernel read-only data: 2436k
[    1.555622] NX-protecting the kernel data: 3980k
[    1.575024] udevd[105]: starting version 175
[    1.596096] tsc: Refined TSC clocksource calibration: 1595.999 MHz
[    1.596107] Switching to clocksource tsc
[    1.638337] Disabling lock debugging due to kernel taint
[    1.639231] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    1.639236] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.639299] e1000e 0000:00:19.0: setting latency timer to 64
[    1.639376] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.639421] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    1.661220] usb 5-1: New USB device found, idVendor=413c, idProduct=3200
[    1.661227] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.661232] usb 5-1: Product: Dell USB Mouse
[    1.661235] usb 5-1: Manufacturer: Dell
[    1.729698] FDC 0 is a post-1991 82077
[    1.819954] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1a:a0:99:c6:d1
[    1.819961] e1000e 0000:00:19.0 eth0: Intel(R) PRO/10/100 Network Connection
[    1.819990] e1000e 0000:00:19.0 eth0: MAC: 7, PHY: 7, PBA No: FFFFFF-0FF
[    1.904044] usb 5-2: new low-speed USB device number 3 using uhci_hcd
[    2.078205] usb 5-2: New USB device found, idVendor=413c, idProduct=2003
[    2.078213] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.078219] usb 5-2: Product: Dell USB Keyboard
[    2.078223] usb 5-2: Manufacturer: Dell
[    2.135299] usbcore: registered new interface driver usbhid
[    2.135305] usbhid: USB HID core driver
[    2.144809] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2
[    2.144971] hid-generic 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1a.2-1/input0
[    2.145724] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3
[    2.145846] hid-generic 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.2-2/input0
[    4.048906] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   14.315244] Adding 1998844k swap on /dev/sda5.  Priority:-1 extents:1 across:1998844k 
[   14.442450] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.485027] udevd[340]: starting version 175
[   14.714898] type=1400 audit(1379105712.510:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   14.715561] type=1400 audit(1379105712.510:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   14.715917] type=1400 audit(1379105712.510:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   14.724550] lp: driver loaded but no devices found
[   14.748567] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PM2S 1 (20121018/utaddress-251)
[   14.748579] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.748584] ACPI Warning: 0x000004b0-0x000004bf SystemIO conflicts with Region \GPO2 1 (20121018/utaddress-251)
[   14.748590] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.748593] ACPI Warning: 0x00000480-0x000004af SystemIO conflicts with Region \GPO_ 1 (20121018/utaddress-251)
[   14.748599] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.748601] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.782726] microcode: CPU0 sig=0x6fd, pf=0x1, revision=0xa1
[   14.849593] [drm] Initialized drm 1.1.0 20060810
[   14.959711] i915 0000:00:02.0: setting latency timer to 64
[   14.960405] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   14.960419] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.960422] [drm] Driver supports precise vblank timestamp query.
[   14.960464] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.963781] [drm] initialized overlay support
[   14.967421] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.200707] fbcon: inteldrmfb (fb0) is primary device
[   15.210971] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.276617] Console: switching to colour frame buffer device 180x56
[   15.284065] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   15.284068] i915 0000:00:02.0: registered panic notifier
[   15.315846] i915: No ACPI video bus found
[   15.315913] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.317219] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   15.438369] microcode: CPU1 sig=0x6fd, pf=0x1, revision=0xa1
[   15.438604] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   15.439381] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   15.439598] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   15.439796] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   15.439984] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.442058] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.444409] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.445167] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.493504] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.509076] coretemp coretemp.0: Using relative temperature scale!
[   15.509100] coretemp coretemp.0: Using relative temperature scale!
[   16.119223] init: failsafe main process (729) killed by TERM signal
[   16.626488] Bluetooth: Core ver 2.16
[   16.626528] NET: Registered protocol family 31
[   16.626531] Bluetooth: HCI device and connection manager initialized
[   16.627027] Bluetooth: HCI socket layer initialized
[   16.627034] Bluetooth: L2CAP socket layer initialized
[   16.627048] Bluetooth: SCO socket layer initialized
[   16.638893] Bluetooth: RFCOMM TTY layer initialized
[   16.638921] Bluetooth: RFCOMM socket layer initialized
[   16.638923] Bluetooth: RFCOMM ver 1.11
[   16.803112] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.803118] Bluetooth: BNEP filters: protocol multicast
[   16.803130] Bluetooth: BNEP socket layer initialized
[   17.198671] init: avahi-cups-reload main process (828) terminated with status 1
[   17.333012] ppdev: user-space parallel port driver
[   17.354105] type=1400 audit(1379105715.150:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=841 comm="apparmor_parser"
[   17.354873] type=1400 audit(1379105715.150:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=841 comm="apparmor_parser"
[   19.576324] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   19.680112] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   19.680246] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.680730] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.480470] type=1400 audit(1379105719.278:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=908 comm="apparmor_parser"
[   21.480490] type=1400 audit(1379105719.278:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=907 comm="apparmor_parser"
[   21.480972] type=1400 audit(1379105719.278:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=908 comm="apparmor_parser"
[   21.480985] type=1400 audit(1379105719.278:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=907 comm="apparmor_parser"
[   21.485576] type=1400 audit(1379105719.282:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=910 comm="apparmor_parser"
[   21.486092] type=1400 audit(1379105719.282:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=909 comm="apparmor_parser"
[   21.486258] type=1400 audit(1379105719.282:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=910 comm="apparmor_parser"
[   21.486594] type=1400 audit(1379105719.282:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=909 comm="apparmor_parser"
[   21.486610] type=1400 audit(1379105719.282:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=910 comm="apparmor_parser"
[   21.499674] type=1400 audit(1379105719.294:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=913 comm="apparmor_parser"
[   22.061375] init: gdm main process (976) killed by TERM signal
[   44.582261] audit_printk_skb: 36 callbacks suppressed
[   44.582268] type=1400 audit(1379105742.378:29): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1777/cmdline" pid=1720 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=118 ouid=0
[   44.604271] type=1400 audit(1379105742.402:30): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1781/cmdline" pid=1720 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=118 ouid=0
[   44.623307] type=1400 audit(1379105742.418:31): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1787/cmdline" pid=1720 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=118 ouid=0
[   44.627759] type=1400 audit(1379105742.422:32): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1788/cmdline" pid=1720 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=118 ouid=0
[   44.636401] type=1400 audit(1379105742.434:33): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/proc/1782/cmdline" pid=1720 comm="dbus-daemon" requested_mask="r" denied_mask="r" fsuid=118 ouid=0
[   44.927161] type=1400 audit(1379105742.722:34): apparmor="DENIED" operation="mount" parent=1 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/run/user/guest-C7wWoM/gvfs/" pid=1807 comm="gvfsd-fuse" fstype="fuse.gvfsd-fuse" srcname="gvfsd-fuse" flags="rw, nosuid, nodev"
[   45.550464] type=1400 audit(1379105743.346:35): apparmor="DENIED" operation="open" parent=1665 profile="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" name="/etc/compizconfig/unity.ini" pid=1813 comm="compiz" requested_mask="c" denied_mask="c" fsuid=118 ouid=0
[   47.383404] ISO 9660 Extensions: Microsoft Joliet Level 3
[   47.430787] ISOFS: changing to secondary root
[  314.784789] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[  314.784800] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[  314.784835] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  367.682205] systemd-hostnamed[2988]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3404.468090] usb 2-2: new high-speed USB device number 2 using ehci-pci
[ 3404.602445] usb 2-2: New USB device found, idVendor=0bda, idProduct=8171
[ 3404.602453] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3404.602459] usb 2-2: Product: 11n USB Adapter
[ 3404.602463] usb 2-2: Manufacturer: Manufacturer Realtek 
[ 3404.602468] usb 2-2: SerialNumber: 00e04c000001
[ 3405.667626] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[ 3405.668889] r8712u: Staging version
[ 3405.668920] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 3405.668923] r8712u: USB_SPEED_HIGH with 4 endpoints
[ 3405.669441] r8712u: Boot from EFUSE: Autoload OK
[ 3406.307187] r8712u: CustomerID = 0x0000
[ 3406.307195] r8712u: MAC Address from efuse = d8:eb:97:16:94:b1
[ 3406.307199] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 3406.307817] usbcore: registered new interface driver r8712u
[ 3407.752443] r8712u: 1 RCR=0x153f00e
[ 3407.753186] r8712u: 2 RCR=0x553f00e
[ 3407.860376] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3407.861002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3408.168368] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by Frogs Hair on 2013-09-13
***Moved Per Request ***

---

### Post by chili555 on 2013-09-13
Looks pretty solid so far! Do you see a wireless interface here, ideally wlan0?```
iwconfig
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```Please don't post dozens of lines of output here; just tell us that it does scan and sees your network or that it doesn't and what the error message is.

If it scans and sees your network, it ought to connect. Can you detach the ethernet, click the Network Manager icon at the top right, click your network, input the WPA password and connect?

---

### Post by DianaRobledo on 2013-09-13
Ok. Mmmm, no, it says that there is no wireless extensions. About wlan0 it says unassociated.

---

### Post by chili555 on 2013-09-13
> **DianaRobledo said:**
> Ok. Mmmm, no, it says that there is no wireless extensions. About wlan0 it says unassociated.And how about scanning?

[Short pizza break...]

---

### Post by DianaRobledo on 2013-09-13
Well... it can see my network. So I detached the ethernet. It's weird 'cause it says it is connected to the wireless network but! it's not really working, I can't use internet and i had to use the ethernet again.

---

### Post by varunendra on 2013-09-13
> **DianaRobledo said:**
> Well... it can see my network. So I detached the ethernet. It's weird 'cause it says it is connected to the wireless network but! it's not really working, I can't use internet and i had to use the ethernet again.

Hi,

Please disconnect the ethernet, get connected via wireless as you just did, and post back the output of -
```
nm-tool
ping -c4 <your router's IP address here>
```

If ping fails (returns no replies), then output of "nm-tool" from ethernet connection also. Thanks.

---

### Post by DianaRobledo on 2013-09-20
Hey! thanks for answering. Miraculously... it's working! I'm finally using internet normally!!!

Thanks a lot, you both! IOU!

:P

---

