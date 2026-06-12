---
title: "Wireless gone - Broadcom/Dell/Jaunty"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-08-21
I had posted this on the networking section but have zero replies, hopefully someone here can help.

I previousy had my wireless connection set up perfect previously (driver installed through "Hardware Drivers" update), however it has just disappeared completely - I think following a kernel update.  The previous kernel was deleted.

The following is as per the "HOWTO" ticket instructions.

**1 ) Machine Brand and Mode**l:  Dell Inspiron 530 Desktop

**2 ) Wireless Brand, Model and Wireless Chipset:**

lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:7604 Hewlett-Packard Deskjet 3940
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**3 ) check interface:**
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:9f:44:ae  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe9f:44ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2082277 (2.0 MB)  TX bytes:213913 (213.9 KB)
          Memory:fdfc0000-fdfe0000 
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

iwconfig wlan0
```
wlan0     No such device
```   :confused:

**4 ) Check for modules:**

lsmod
```
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   67844  2 
drm                    96424  3 i915
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
dcdbas                 15264  0 
pcspkr                 10496  0 
psmouse                61972  0 
intel_agp              34108  1 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw              13444  0 
ndiswrapper           193436  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                42696  3 drm,intel_agp
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usblp                  20224  0 
usbhid                 42336  0 
e1000e                121136  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

**5 ) Kernel boot messages**

dmesg  (not sure if this is the entire output of this command)
```
[    0.545889] pci 0000:00:01.0: PME# disabled
[    0.545917] pci 0000:00:02.0: reg 10 32bit mmio: [0xfdf00000-0xfdf7ffff]
[    0.545923] pci 0000:00:02.0: reg 14 io port: [0xff00-0xff07]
[    0.545928] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.545933] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfdb00000-0xfdbfffff]
[    0.546011] pci 0000:00:19.0: reg 10 32bit mmio: [0xfdfc0000-0xfdfdffff]
[    0.546018] pci 0000:00:19.0: reg 14 32bit mmio: [0xfdfff000-0xfdffffff]
[    0.546024] pci 0000:00:19.0: reg 18 io port: [0xfe00-0xfe1f]
[    0.546050] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.546055] pci 0000:00:19.0: PME# disabled
[    0.546106] pci 0000:00:1a.0: reg 20 io port: [0xfd00-0xfd1f]
[    0.546170] pci 0000:00:1a.1: reg 20 io port: [0xfc00-0xfc1f]
[    0.546234] pci 0000:00:1a.2: reg 20 io port: [0xfb00-0xfb1f]
[    0.546301] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.546341] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.546346] pci 0000:00:1a.7: PME# disabled
[    0.546388] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    0.546418] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.546422] pci 0000:00:1b.0: PME# disabled
[    0.546475] pci 0000:00:1d.0: reg 20 io port: [0xfa00-0xfa1f]
[    0.546541] pci 0000:00:1d.1: reg 20 io port: [0xf900-0xf91f]
[    0.546605] pci 0000:00:1d.2: reg 20 io port: [0xf800-0xf81f]
[    0.546672] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdffd000-0xfdffd3ff]
[    0.546711] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.546716] pci 0000:00:1d.7: PME# disabled
[    0.546833] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.546837] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.546879] pci 0000:00:1f.2: reg 10 io port: [0xf700-0xf707]
[    0.546886] pci 0000:00:1f.2: reg 14 io port: [0xf600-0xf603]
[    0.546892] pci 0000:00:1f.2: reg 18 io port: [0xf500-0xf507]
[    0.546898] pci 0000:00:1f.2: reg 1c io port: [0xf400-0xf403]
[    0.546904] pci 0000:00:1f.2: reg 20 io port: [0xf300-0xf30f]
[    0.546911] pci 0000:00:1f.2: reg 24 io port: [0xf200-0xf20f]
[    0.546948] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfdffc000-0xfdffc0ff]
[    0.546962] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.547006] pci 0000:00:1f.5: reg 10 io port: [0xf000-0xf007]
[    0.547012] pci 0000:00:1f.5: reg 14 io port: [0xef00-0xef03]
[    0.547018] pci 0000:00:1f.5: reg 18 io port: [0xee00-0xee07]
[    0.547024] pci 0000:00:1f.5: reg 1c io port: [0xed00-0xed03]
[    0.547031] pci 0000:00:1f.5: reg 20 io port: [0xec00-0xec0f]
[    0.547037] pci 0000:00:1f.5: reg 24 io port: [0xeb00-0xeb0f]
[    0.547096] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.547099] pci 0000:00:01.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.547105] pci 0000:00:01.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.547130] pci 0000:02:01.0: reg 10 32bit mmio: [0xfddfe000-0xfddfffff]
[    0.547206] pci 0000:00:1e.0: transparent bridge
[    0.547210] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.547214] pci 0000:00:1e.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.547221] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.547232] bus 00 -> node 0
[    0.547240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.547571] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.566140] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.566283] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.566423] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.566561] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.566697] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.566835] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.566972] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.567108] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.567328] ACPI: WMI: Mapper loaded
[    0.567546] SCSI subsystem initialized
[    0.567592] libata version 3.00 loaded.
[    0.567649] usbcore: registered new interface driver usbfs
[    0.567668] usbcore: registered new interface driver hub
[    0.567700] usbcore: registered new device driver usb
[    0.567828] PCI: Using ACPI for IRQ routing
[    0.567937] Bluetooth: Core ver 2.13
[    0.568020] NET: Registered protocol family 31
[    0.568023] Bluetooth: HCI device and connection manager initialized
[    0.568026] Bluetooth: HCI socket layer initialized
[    0.568029] NET: Registered protocol family 8
[    0.568031] NET: Registered protocol family 20
[    0.568044] NetLabel: Initializing
[    0.568046] NetLabel:  domain hash size = 128
[    0.568047] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.568061] NetLabel:  unlabeled traffic allowed by default
[    0.568075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.568080] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.572072] AppArmor: AppArmor Filesystem Enabled
[    0.572085] pnp: PnP ACPI init
[    0.572085] ACPI: bus type pnp registered
[    0.574226] pnp: PnP ACPI: found 12 devices
[    0.574229] ACPI: ACPI bus type pnp unregistered
[    0.574233] PnPBIOS: Disabled by ACPI PNP
[    0.574244] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.574247] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.574250] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.574253] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.574262] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.574268] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.574275] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.574278] system 00:0b: iomem range 0x3f600000-0x3f6fffff has been reserved
[    0.574281] system 00:0b: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.574284] system 00:0b: iomem range 0x3f590000-0x3f5fffff could not be reserved
[    0.574287] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.574290] system 00:0b: iomem range 0x100000-0x3f58ffff could not be reserved
[    0.574294] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.574297] system 00:0b: iomem range 0xfed14000-0xfed1dfff has been reserved
[    0.574300] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.574303] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.574306] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.574309] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.574312] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.576018] Switched to high resolution mode on CPU 0
[    0.609100] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.609103] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.609108] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdefffff
[    0.609112] pci 0000:00:01.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.609117] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.609121] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.609126] pci 0000:00:1e.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.609130] pci 0000:00:1e.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.609147] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.609152] pci 0000:00:01.0: setting latency timer to 64
[    0.609158] pci 0000:00:1e.0: setting latency timer to 64
[    0.609163] bus: 00 index 0 io port: [0x00-0xffff]
[    0.609165] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.609168] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.609170] bus: 01 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.609173] bus: 01 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.609175] bus: 01 index 3 mmio: [0x0-0x0]
[    0.609177] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.609180] bus: 02 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.609182] bus: 02 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.609184] bus: 02 index 3 io port: [0x00-0xffff]
[    0.609187] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.609198] NET: Registered protocol family 2
[    0.609331] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.609575] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.610133] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.610457] TCP: Hash tables configured (established 131072 bind 65536)
[    0.610461] TCP reno registered
[    0.610620] NET: Registered protocol family 1
[    0.610751] checking if image is initramfs... it is
[    1.357326] Freeing initrd memory: 7379k freed
[    1.357446] cpufreq: No nForce2 chipset.
[    1.357587] audit: initializing netlink socket (disabled)
[    1.357604] type=2000 audit(1250799666.356:1): initialized
[    1.366225] highmem bounce pool size: 64 pages
[    1.366232] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.367605] VFS: Disk quotas dquot_6.5.1
[    1.367673] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.368360] fuse init (API version 7.10)
[    1.368453] msgmni has been set to 1724
[    1.368654] alg: No test for stdrng (krng)
[    1.368669] io scheduler noop registered
[    1.368672] io scheduler anticipatory registered
[    1.368674] io scheduler deadline registered
[    1.368698] io scheduler cfq registered (default)
[    1.368714] pci 0000:00:02.0: Boot video device
[    1.370928] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.370965] pcieport-driver 0000:00:01.0: found MSI capability
[    1.370989] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.370999] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.371017] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.371075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.371085] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.371209] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.371212] ACPI: Power Button (FF) [PWRF]
[    1.371256] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.371259] ACPI: Power Button (CM) [PWRB]
[    1.371305] fan PNP0C0B:00: registered as cooling_device0
[    1.371310] ACPI: Fan [FAN] (on)
[    1.371575] processor ACPI_CPU:00: registered as cooling_device1
[    1.373726] thermal LNXTHERM:01: registered as thermal_zone0
[    1.374033] ACPI: Thermal Zone [THRM] (40 C)
[    1.374080] isapnp: Scanning for PnP cards...
[    1.727082] isapnp: No Plug & Play device found
[    1.728450] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.729580] brd: module loaded
[    1.729898] loop: module loaded
[    1.729986] Fixed MDIO Bus: probed
[    1.729992] PPP generic driver version 2.4.2
[    1.730056] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.730090] Driver 'sd' needs updating - please use bus_type methods
[    1.730100] Driver 'sr' needs updating - please use bus_type methods
[    1.730174] ata_piix 0000:00:1f.2: version 2.12
[    1.730193] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.730197] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.730246] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.730335] scsi0 : ata_piix
[    1.730442] scsi1 : ata_piix
[    1.731223] ata1: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf300 irq 19
[    1.731229] ata2: SATA max UDMA/133 cmd 0xf500 ctl 0xf400 bmdma 0xf308 irq 19
[    2.524059] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.524071] ata1.01: SATA link down (SStatus 0 SControl 300)
[    2.532305] ata1.00: ATA-8: SAMSUNG HD321KJ, CP100-12, max UDMA7
[    2.532308] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.540324] ata1.00: configured for UDMA/133
[    3.336055] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.336067] ata2.01: SATA link down (SStatus 0 SControl 300)
[    3.344193] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-H73N, B103, max UDMA/100
[    3.360227] ata2.00: configured for UDMA/100
[    3.360754] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD321KJ  CP10 PQ: 0 ANSI: 5
[    3.360865] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.360882] sd 0:0:0:0: [sda] Write Protect is off
[    3.360885] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.360913] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.360986] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.361002] sd 0:0:0:0: [sda] Write Protect is off
[    3.361005] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.361031] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.361035]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    3.426190] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.426242] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.427818] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H73N B103 PQ: 0 ANSI: 5
[    3.432419] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.432423] Uniform CD-ROM driver Revision: 3.20
[    3.432538] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.432585] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.432614] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.432619] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.432661] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.432718] scsi2 : ata_piix
[    3.432789] scsi3 : ata_piix
[    3.433150] ata3: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xec00 irq 19
[    3.433155] ata4: SATA max UDMA/133 cmd 0xee00 ctl 0xed00 bmdma 0xec08 irq 19
[    3.762667] ata3: SATA link down (SStatus 0 SControl 300)
[    4.090666] ata4: SATA link down (SStatus 0 SControl 300)
[    4.091290] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.091315] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.091339] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.091343] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.091410] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.095328] ehci_hcd 0000:00:1a.7: debug port 1
[    4.095334] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.095350] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    4.108008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.108092] usb usb1: configuration #1 chosen from 1 choice
[    4.108121] hub 1-0:1.0: USB hub found
[    4.108132] hub 1-0:1.0: 6 ports detected
[    4.108245] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.108260] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.108264] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.108319] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.112236] ehci_hcd 0000:00:1d.7: debug port 1
[    4.112243] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.112257] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    4.128009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.128073] usb usb2: configuration #1 chosen from 1 choice
[    4.128100] hub 2-0:1.0: USB hub found
[    4.128108] hub 2-0:1.0: 6 ports detected
[    4.128213] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.128232] uhci_hcd: USB Universal Host Controller Interface driver
[    4.128268] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.128276] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.128280] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.128329] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.128362] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fd00
[    4.128448] usb usb3: configuration #1 chosen from 1 choice
[    4.128479] hub 3-0:1.0: USB hub found
[    4.128487] hub 3-0:1.0: 2 ports detected
[    4.128575] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.128582] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.128585] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.128636] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.128666] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fc00
[    4.128744] usb usb4: configuration #1 chosen from 1 choice
[    4.128772] hub 4-0:1.0: USB hub found
[    4.128779] hub 4-0:1.0: 2 ports detected
[    4.128876] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.128883] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.128887] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.128931] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.128956] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fb00
[    4.129034] usb usb5: configuration #1 chosen from 1 choice
[    4.129061] hub 5-0:1.0: USB hub found
[    4.129070] hub 5-0:1.0: 2 ports detected
[    4.129160] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.129167] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.129171] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.129219] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.129242] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fa00
[    4.129320] usb usb6: configuration #1 chosen from 1 choice
[    4.129347] hub 6-0:1.0: USB hub found
[    4.129354] hub 6-0:1.0: 2 ports detected
[    4.129440] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.129446] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.129450] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.129506] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.129529] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000f900
[    4.129608] usb usb7: configuration #1 chosen from 1 choice
[    4.129635] hub 7-0:1.0: USB hub found
[    4.129642] hub 7-0:1.0: 2 ports detected
[    4.129738] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.129744] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.129748] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.129798] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.129820] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f800
[    4.129902] usb usb8: configuration #1 chosen from 1 choice
[    4.129930] hub 8-0:1.0: USB hub found
[    4.129937] hub 8-0:1.0: 2 ports detected
[    4.130094] PNP: No PS/2 controller found. Probing ports directly.
[    4.130398] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.130405] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.130541] mice: PS/2 mouse device common for all mice
[    4.130679] rtc_cmos 00:04: RTC can wake from S4
[    4.130717] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.130743] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.130825] device-mapper: uevent: version 1.0.3
[    4.130949] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.131007] device-mapper: multipath: version 1.0.5 loaded
[    4.131011] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.131106] EISA: Probing bus 0 at eisa.0
[    4.131133] EISA: Detected 0 cards.
[    4.131164] cpuidle: using governor ladder
[    4.131166] cpuidle: using governor menu
[    4.131660] TCP cubic registered
[    4.131769] NET: Registered protocol family 10
[    4.132184] lo: Disabled Privacy Extensions
[    4.132479] NET: Registered protocol family 17
[    4.132502] Bluetooth: L2CAP ver 2.11
[    4.132504] Bluetooth: L2CAP socket layer initialized
[    4.132507] Bluetooth: SCO (Voice Link) ver 0.6
[    4.132509] Bluetooth: SCO socket layer initialized
[    4.132548] Bluetooth: RFCOMM socket layer initialized
[    4.132556] Bluetooth: RFCOMM TTY layer initialized
[    4.132558] Bluetooth: RFCOMM ver 1.10
[    4.132610] Using IPI No-Shortcut mode
[    4.132711] registered taskstats version 1
[    4.132837]   Magic number: 5:460:397
[    4.132872] mem random: hash matches
[    4.132911] rtc_cmos 00:04: setting system clock to 2009-08-20 20:21:09 UTC (1250799669)
[    4.132914] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.132916] EDD information not available.
[    4.133122] Freeing unused kernel memory: 532k freed
[    4.133229] Write protecting the kernel text: 4116k
[    4.133263] Write protecting the kernel read-only data: 1528k
[    4.543679] FDC 0 is a post-1991 82077
[    4.557567] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    4.557571] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    4.557621] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.557632] e1000e 0000:00:19.0: setting latency timer to 64
[    4.557767] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[    4.658539] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1a:a0:9f:44:ae
[    4.658543] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    4.658566] 0000:00:19.0: eth0: MAC: 6, PHY: 7, PBA No: ffffff-0ff
[    4.784128] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    4.958799] usb 4-1: configuration #1 chosen from 1 choice
[    4.991492] usbcore: registered new interface driver hiddev
[    5.006023] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
[    5.006297] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.1-1/input0
[    5.006317] usbcore: registered new interface driver usbhid
[    5.006321] usbhid: v2.6:USB HID core driver
[    5.201104] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    5.223536] PM: Starting manual resume from disk
[    5.223540] PM: Resume from partition 8:6
[    5.223542] PM: Checking hibernation image.
[    5.223734] PM: Resume from disk failed.
[    5.260706] kjournald starting.  Commit interval 5 seconds
[    5.260722] EXT3-fs: mounted filesystem with ordered data mode.
[    5.379795] usb 4-2: configuration #1 chosen from 1 choice
[    5.396058] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
[    5.396178] generic-usb 0003:413C:3012.0002: input,hidraw1: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.1-2/input0
[    5.636022] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    5.825096] usb 5-1: configuration #1 chosen from 1 choice
[    9.745187] udev: starting version 141
[    9.960217] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7604
[    9.960243] usbcore: registered new interface driver usblp
[   10.057756] Linux agpgart interface v0.103
[   10.251729] iTCO_vendor_support: vendor-support=0
[   10.253507] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.253823] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   10.253938] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.306538] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   10.748096] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[   10.748353] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   10.751229] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   10.755226] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.756936] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.837803] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   10.837816] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   10.837833] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   10.837843] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   10.837856] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   10.837866] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   10.837879] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   10.837888] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   10.837902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   10.837911] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   10.837920] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   10.837952] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   10.837962] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   10.837971] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   10.837980] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   10.837990] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   10.838000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   10.838017] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   10.838026] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   10.838047] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   10.838057] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   10.838066] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   10.838075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   10.838085] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   10.838095] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   10.838102] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwl6'
[   10.838587] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   10.838725] usbcore: registered new interface driver ndiswrapper
[   10.920337] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.920451] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.195747] lp: driver loaded but no devices found
[   11.318970] Adding 2980016k swap on /dev/sda6.  Priority:-1 extents:1 across:2980016k
[   11.867056] EXT3 FS on sda5, internal journal
[   12.973426] type=1505 audit(1250796078.339:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1954
[   13.031601] type=1505 audit(1250796078.395:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1958
[   13.031759] type=1505 audit(1250796078.395:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1958
[   13.031824] type=1505 audit(1250796078.395:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1958
[   13.031878] type=1505 audit(1250796078.395:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1958
[   13.074791] type=1505 audit(1250796078.439:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=1963
[   13.234785] type=1505 audit(1250796078.599:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1967
[   13.235003] type=1505 audit(1250796078.599:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1967
[   13.269853] type=1505 audit(1250796078.635:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1971
[   17.248687] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[   17.304896] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[   17.305219] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.823544] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.823547] Bluetooth: BNEP filters: protocol multicast
[   17.863588] Bridge firewalling registered
[   18.992039] ppdev: user-space parallel port driver
[   19.451405] [drm] Initialized drm 1.1.0 20060810
[   19.463014] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.463021] pci 0000:00:02.0: setting latency timer to 64
[   19.463124] pci 0000:00:02.0: irq 2301 for MSI/MSI-X
[   19.463218] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   19.573183] [drm:i915_setparam] *ERROR* unknown parameter 4
[   19.573211] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.690929] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.758548] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[   20.758552] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   20.758793] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.108217] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[   24.164058] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[   24.164423] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.612764] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[   25.612768] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   25.613003] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.676011] eth0: no IPv6 routers present
[   38.250027] [drm:i915_getparam] *ERROR* Unknown parameter 6
```

**6 ) Network configuration**

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:9f:44:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.1-2 ip=192.168.0.5 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:fe:42:f4:31:93
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

**7 ) Scan for networks:**

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

**8 ) Ubuntu Version:**

lsb_release -d
```
Description:	Ubuntu 9.04
```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **

uname -mr
```
2.6.28-15-generic i686
```

**10 ) Restarting the network:**

sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
```

I'm no ubuntu experts but I picked up the lack of a wlan0 in there and a few ERROR messages so I'm hoping someone can look at this and make a quick diagnostic.

All advice gratefully received - am having to endure Vista while this is ongoing :(

---

### Post by LewRockwell on 2009-08-21
did you do a clean and fresh Jaunty install or just a dirty upgrade?

we're thinking you've got a conflict between ndiswrapper and "native" BCM43xx support

we're using Jaunty without a wrapper and the broadcom works well

.

---

### Post by aquascrotum on 2009-08-21
The wireless was working on a clean Jaunty install - I think there was an update to a newer kernel (.15 I think?) a few days ago.

When I initially installed Jaunty I'd tried messing about with ndiswrapper before I'd realised that I just needed to use the hardware driver search function - after I let Jaunty download and install the native driver, everything worked fine. Until now :(.

---

### Post by aquascrotum on 2009-08-22
Bump.

---

### Post by LewRockwell on 2009-08-22
> **aquascrotum said:**
> The wireless was working on a clean Jaunty install - I think there was an update to a newer kernel (.15 I think?) a few days ago.

When I initially installed Jaunty I'd tried messing about with ndiswrapper before I'd realised that I just needed to use the hardware driver search function - after I let Jaunty download and install the native driver, everything worked fine. Until now :(.

uninstall ndiswrapper via Synaptic and see what that does

.

---

### Post by aquascrotum on 2009-08-22
Tried that and it didnt work.

Ended up doing a wipe and reinstalling Jaunty from scratch, everything working well again - but having to reinstall does seem to be a bit of overkill.

---

### Post by Bartender on 2009-08-22
There's a bombproof hardware fix - buy an Intel wireless card and replace that crappy Broadcom.

---

