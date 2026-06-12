---
title: "HELP pls HELP,HELP,HELP.................."
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by abishek22 on 2007-11-14
> **abishek22 said:**
> i use a D-Link** DWL-630** H/W version D1 F/W Version 4.10 PCMCIA Adapter Connecting to a Linksys WRT54GS Router

after installing UBUNTU gutsy when the card was plugged in it Detected all available WIFI networks (showed a window about a restriced driver in use)BUT failed to logon to my WEP enabled router,my ten digit HEx password wouldn't work.Despite it being 100% correct



Having read up that WICD was a better alternative i installed it no Wireless networks seem to be detected in WICD HELP!!!!!!!






-----------------------------------------------------------------------------------
> **abishek22 said:**
> Can you post the following:
lshw -C network
iwlist scan



[B]
[SIZE="5"]i have posted the following commands
sudo lshw -C network
sudo iwlist scan
lsmod
dmesg
lspci -nn[/SIZE]

[/B]






[B]
abishek@Delllaptop:~$ sudo lshw -C network[/B]

[sudo] password for abishek:

  *-network               

       description: AR5001-0000-0000

       product: Wireless LAN Reference Card

       vendor: Atheros Communications, Inc.

       physical id: 0

       version: 00

       slot: Socket 0

       resources: irq:11

  *-network DISABLED

       description: Wireless interface

       product: AR2413 802.11bg NIC

       vendor: Atheros Communications, Inc.

       physical id: 1

       bus info: pci@0000:03:00.0

       logical name: wifi0

       version: 01

       serial: 00:11:95:f9:dc:43

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b


> abishek@Delllaptop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.
wifi0     Interface doesn't support scanning.
ath0      Interface doesn't support scanning : Network is down



[QUOTE]abishek@Delllaptop:~$ lsmod
Module                  Size  Used by

ipv6                  273892  12 

radeon                125472  2 

drm                    83348  3 radeon

rfcomm                 42136  2 

l2cap                  26240  11 rfcomm

bluetooth              57060  4 rfcomm,l2cap

ppdev                  10244  0 

speedstep_lib           6404  0 

cpufreq_conservative     8072  0 

cpufreq_ondemand        9612  0 

cpufreq_stats           7232  0 

cpufreq_userspace       5280  0 

cpufreq_powersave       2688  0 

freq_table              5792  2 cpufreq_ondemand,cpufreq_stats

battery                11012  0 

ac                      6148  0 

button                  8976  0 

dock                   10656  0 

video                  18060  0 

container               5504  0 

sbs                    19592  0 

nls_iso8859_1           5120  1 

nls_cp437               6784  1 

vfat                   14080  1 

fat                    54300  1 vfat

sbp2                   24072  0 

parport_pc             37412  0 

lp                     12580  0 

parport                37448  3 ppdev,parport_pc,lp

wlan_scan_sta          15104  0 

ath_rate_sample        14208  1 

ath_pci                98336  0 

wlan                  206660  4 wlan_scan_sta,ath_rate_sample,ath_pci

ath_hal               192720  3 ath_rate_sample,ath_pci

joydev                 11328  0 

snd_intel8x0           34972  1 

snd_ac97_codec        100644  1 snd_intel8x0

ac97_bus                3200  1 snd_ac97_codec

snd_pcm_oss            44672  0 

snd_mixer_oss          17664  1 snd_pcm_oss

snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

snd_seq_dummy           4740  0 

snd_seq_oss            33152  0 

snd_seq_midi            9600  0 

snd_rawmidi            25728  1 snd_seq_midi

snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi

pcmcia                 41388  0 

snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              24324  2 snd_pcm,snd_seq

snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

serio_raw               8068  0 

snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               8800  1 snd

snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

iTCO_wdt               11940  0 

psmouse                39952  0 

pcspkr                  4224  0 

yenta_socket           27532  2 

rsrc_nonstatic         14080  1 yenta_socket

pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic

iTCO_vendor_support     4868  1 iTCO_wdt

intel_agp              25620  1 

agpgart                35016  2 drm,intel_agp

shpchp                 34580  0 

pci_hotplug            32704  1 shpchp

evdev                  11136  5 

ext3                  133896  1 

jbd                    60456  1 ext3

mbcache                 9732  1 ext3

sg                     36764  0 

sd_mod                 30336  5 

sr_mod                 17828  0 

cdrom                  37536  1 sr_mod

ata_piix               17540  4 

ohci1394               36528  0 

ieee1394               96312  2 sbp2,ohci1394

ata_generic             8452  0 

libata                125168  2 ata_piix,ata_generic

scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata

ehci_hcd               36492  0 

uhci_hcd               26640  0 

usbcore               138632  3 ehci_hcd,uhci_hcd

thermal                14344  0 

processor              32072  1 thermal

fan                     5764  0 

fuse                   47124  3 

apparmor               40728  0 

commoncap               8320  1 apparmor













> 
**abishek@Delllaptop:~$ dmesg**

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)

[    0.000000] BIOS-provided physical RAM map:

[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)

[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)

[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc9000 (usable)

[    0.000000]  BIOS-e820: 000000003ffc9000 - 0000000040000000 (reserved)

[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)

[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)

[    0.000000] 127MB HIGHMEM available.

[    0.000000] 896MB LOWMEM available.

[    0.000000] Entering add_active_range(0, 0, 262089) 0 entries of 256 used

[    0.000000] Zone PFN ranges:

[    0.000000]   DMA             0 ->     4096

[    0.000000]   Normal       4096 ->   229376

[    0.000000]   HighMem    229376 ->   262089

[    0.000000] early_node_map[1] active PFN ranges

[    0.000000]     0:        0 ->   262089

[    0.000000] On node 0 totalpages: 262089

[    0.000000]   DMA zone: 32 pages used for memmap

[    0.000000]   DMA zone: 0 pages reserved

[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

[    0.000000]   Normal zone: 1760 pages used for memmap

[    0.000000]   Normal zone: 223520 pages, LIFO batch:31

[    0.000000]   HighMem zone: 255 pages used for memmap

[    0.000000]   HighMem zone: 32458 pages, LIFO batch:7

[    0.000000] DMI 2.3 present.

[    0.000000] ACPI: RSDP signature @ 0xC00FDF00 checksum 0

[    0.000000] ACPI: RSDP 000FDF00, 0014 (r0 DELL  )

[    0.000000] ACPI: RSDT 3FFF0000, 0028 (r1 DELL    CPi R   27D40A12 ASL        61)

[    0.000000] ACPI: FACP 3FFF0400, 0074 (r1 DELL    CPi R   27D40A12 ASL        61)

[    0.000000] ACPI: DSDT 3FFF0C00, 25D8 (r1 INT430 SYSFexxx     1001 MSFT  100000E)

[    0.000000] ACPI: FACS 3FFFF800, 0040

[    0.000000] ACPI: PM-Timer IO Port: 0x808

[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:beda0000)

[    0.000000] Built 1 zonelists.  Total pages: 260042

[    0.000000] Kernel command line: root=UUID=0f7c81b2-c0ad-4c8a-9836-48af3c9d7176 ro quiet splash vga=792

[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"

[    0.000000] mapped APIC to ffffd000 (0180f000)

[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.

[    0.000000] Initializing CPU#0

[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)

[    0.000000] Detected 2657.902 MHz processor.

[    8.260000] Console: colour dummy device 80x25

[    8.260992] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

[    8.261963] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

[    8.294837] Memory: 1027740k/1048356k available (2015k kernel code, 19936k reserved, 916k data, 364k init, 130852k highmem)

[    8.294850] virtual kernel memory layout:

[    8.294851]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)

[    8.294852]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

[    8.294853]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

[    8.294854]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

[    8.294855]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)

[    8.294856]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)

[    8.294857]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)

[    8.294860] Checking if this processor honours the WP bit even in supervisor mode... Ok.

[    8.294921] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1

[    8.374898] Calibrating delay using timer specific routine.. 5320.19 BogoMIPS (lpj=10640392)

[    8.374944] Security Framework v1.0.0 initialized

[    8.374959] SELinux:  Disabled at boot.

[    8.374975] Mount-cache hash table entries: 512

[    8.375201] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000

[    8.375216] CPU: Trace cache: 12K uops, L1 D cache: 8K

[    8.375221] CPU: L2 cache: 512K

[    8.375224] CPU: Hyper-Threading is disabled

[    8.375228] CPU: After all inits, caps: bfebf9ff 00000000 00000000 0000b080 00004400 00000000 00000000

[    8.375245] Compat vDSO mapped to ffffe000.

[    8.375266] Checking 'hlt' instruction... OK.

[    8.391102] SMP alternatives: switching to UP code

[    8.391492] Freeing SMP alternatives: 11k freed

[    8.391830] Early unpacking initramfs... done

[    8.695942] ACPI: Core revision 20070126

[    8.695999] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

[    8.697184] ACPI: setting ELCR to 0200 (from 0800)

[    8.698002] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09

[    8.698008] SMP motherboard not detected.

[    8.698010] Local APIC not detected. Using dummy APIC emulation.

[    8.698054] Brought up 1 CPUs

[    8.698209] Booting paravirtualized kernel on bare hardware

[    8.698273] Time: 20:49:29  Date: 10/11/107

[    8.698299] NET: Registered protocol family 16

[    8.698409] EISA bus registered

[    8.698423] ACPI: bus type pci registered

[    8.750881] PCI: PCI BIOS revision 2.10 entry at 0xfcfae, last bus=2

[    8.750884] PCI: Using configuration type 1

[    8.750885] Setting up standard PCI resources

[    8.752358] ACPI: EC: Look up EC in DSDT

[    8.755121] ACPI: Interpreter enabled

[    8.755126] ACPI: (supports S0 S1 S3 S4 S5)

[    8.755149] ACPI: Using PIC for interrupt routing

[    8.759903] ACPI: PCI Root Bridge [PCI0] (0000:00)

[    8.759923] PCI: Probing PCI hardware (bus 00)

[    8.760327] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,

[    8.760328] * this clock source is slow. If you are sure your timer does not have

[    8.760330] * this bug, please use "acpi_pm_good" to disable the workaround

[    8.760375] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO

[    8.760378] PCI quirk: region 0880-08bf claimed by ICH4 GPIO

[    8.760756] PCI: Transparent bridge - 0000:00:1e.0

[    8.760840] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    8.761110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]

[    8.761189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]

[    8.766835] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)

[    8.766935] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11

[    8.767032] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)

[    8.767130] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)

[    8.767228] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[    8.767329] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)

[    8.767442] Linux Plug and Play Support v0.97 (c) Adam Belay

[    8.767455] pnp: PnP ACPI init

[    8.767467] ACPI: bus type pnp registered

[    8.776528] pnp: PnP ACPI: found 11 devices

[    8.776531] ACPI: ACPI bus type pnp unregistered

[    8.776537] PnPBIOS: Disabled by ACPI PNP

[    8.776603] PCI: Using ACPI for IRQ routing

[    8.776606] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

[    8.782617] NET: Registered protocol family 8

[    8.782659] NET: Registered protocol family 20

[    8.782746] pnp: 00:00: iomem range 0x0-0x9fbff could not be reserved

[    8.782750] pnp: 00:00: iomem range 0x9fc00-0x9ffff could not be reserved

[    8.782753] pnp: 00:00: iomem range 0xc0000-0xcffff could not be reserved

[    8.782755] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved

[    8.782763] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved

[    8.782765] pnp: 00:02: ioport range 0x800-0x805 has been reserved

[    8.782768] pnp: 00:02: ioport range 0x808-0x80f has been reserved

[    8.782774] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved

[    8.782777] pnp: 00:03: ioport range 0x806-0x807 has been reserved

[    8.782779] pnp: 00:03: ioport range 0x810-0x85f has been reserved

[    8.782782] pnp: 00:03: ioport range 0x860-0x87f has been reserved

[    8.782784] pnp: 00:03: ioport range 0x880-0x8bf has been reserved

[    8.782787] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved

[    8.782795] pnp: 00:08: ioport range 0x900-0x97f has been reserved

[    8.786623] Time: tsc clocksource has been installed.

[    8.813133] PCI: Bridge: 0000:00:01.0

[    8.813137]   IO window: c000-cfff

[    8.813142]   MEM window: fc000000-fdffffff

[    8.813146]   PREFETCH window: e8000000-efffffff

[    8.813156] PCI: Bus 3, cardbus bridge: 0000:02:04.0

[    8.813159]   IO window: 0000d000-0000d0ff

[    8.813163]   IO window: 0000d400-0000d4ff

[    8.813167]   PREFETCH window: 50000000-53ffffff

[    8.813171]   MEM window: 58000000-5bffffff

[    8.813175] PCI: Bridge: 0000:00:1e.0

[    8.813178]   IO window: d000-efff

[    8.813183]   MEM window: f6000000-fbffffff

[    8.813188]   PREFETCH window: 50000000-53ffffff

[    8.813206] PCI: Setting latency timer of device 0000:00:1e.0 to 64

[    8.813223] PCI: Enabling device 0000:02:04.0 (0000 -> 0003)

[    8.813394] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11

[    8.813398] PCI: setting IRQ 11 as level-triggered

[    8.813401] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

[    8.813421] NET: Registered protocol family 2

[    8.850647] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    8.850871] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)

[    8.853083] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    8.853735] TCP: Hash tables configured (established 131072 bind 65536)

[    8.853743] TCP reno registered

[    8.862785] checking if image is initramfs... it is

[    9.314297] Switched to high resolution mode on CPU 0

[    9.461585] Freeing initrd memory: 7061k freed

[    9.462029] audit: initializing netlink socket (disabled)

[    9.462051] audit(1194814168.996:1): initialized

[    9.462190] highmem bounce pool size: 64 pages

[    9.464399] VFS: Disk quotas dquot_6.5.1

[    9.464460] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    9.464575] io scheduler noop registered

[    9.464578] io scheduler anticipatory registered

[    9.464580] io scheduler deadline registered

[    9.464598] io scheduler cfq registered (default)

[    9.464675] Boot video device is 0000:01:00.0

[    9.464870] isapnp: Scanning for PnP cards...

[    9.817647] isapnp: No Plug & Play device found

[    9.847676] Real Time Clock Driver v1.12ac

[    9.847796] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[    9.849217] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

[    9.849489] input: Macintosh mouse button emulation as /class/input/input0

[    9.849587] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

[    9.849760] i8042.c: Warning: Keylock active.

[    9.853116] serio: i8042 KBD port at 0x60,0x64 irq 1

[    9.853124] serio: i8042 AUX port at 0x60,0x64 irq 12

[    9.853355] mice: PS/2 mouse device common for all mice

[    9.853490] EISA: Probing bus 0 at eisa.0

[    9.853519] EISA: Detected 0 cards.

[    9.853660] TCP cubic registered

[    9.853674] NET: Registered protocol family 1

[    9.853701] Using IPI No-Shortcut mode

[    9.853923]   Magic number: 15:765:851

[    9.854074]   hash matches device ptyv3

[    9.854696] Freeing unused kernel memory: 364k freed

[    9.897897] input: AT Translated Set 2 keyboard as /class/input/input1

[   11.096036] AppArmor: AppArmor initialized<5>audit(1194814170.496:2):  type=1505 info="AppArmor initialized" pid=1195

[   11.106020] fuse init (API version 7.8)

[   11.112730] Failure registering capabilities with primary security module.

[   11.135189] ACPI: Processor [CPU0] (supports 8 throttling states)

[   11.138480] ACPI: Thermal Zone [THM] (31 C)

[   11.814756] usbcore: registered new interface driver usbfs

[   11.814787] usbcore: registered new interface driver hub

[   11.814814] usbcore: registered new device driver usb

[   11.815822] USB Universal Host Controller Interface driver v3.0

[   11.815904] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

[   11.815918] PCI: Setting latency timer of device 0000:00:1d.0 to 64

[   11.815922] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[   11.816122] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

[   11.816151] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80

[   11.816288] usb usb1: configuration #1 chosen from 1 choice

[   11.816316] hub 1-0:1.0: USB hub found

[   11.816328] hub 1-0:1.0: 2 ports detected

[   11.887190] SCSI subsystem initialized

[   11.892835] libata version 2.21 loaded.

[   11.938828] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11

[   11.938834] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11

[   11.938848] PCI: Setting latency timer of device 0000:00:1d.1 to 64

[   11.938852] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[   11.938881] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

[   11.938908] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40

[   11.939026] usb usb2: configuration #1 chosen from 1 choice

[   11.939054] hub 2-0:1.0: USB hub found

[   11.939063] hub 2-0:1.0: 2 ports detected

[   12.040617] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11

[   12.040622] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11

[   12.040635] PCI: Setting latency timer of device 0000:00:1d.2 to 64

[   12.040639] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[   12.040668] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

[   12.040694] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20

[   12.040807] usb usb3: configuration #1 chosen from 1 choice

[   12.040837] hub 3-0:1.0: USB hub found

[   12.040846] hub 3-0:1.0: 2 ports detected

[   12.144620] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11

[   12.144625] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11

[   12.144641] PCI: Setting latency timer of device 0000:00:1d.7 to 64

[   12.144645] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[   12.144679] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4

[   12.144723] ehci_hcd 0000:00:1d.7: debug port 1

[   12.144730] PCI: cache line size of 128 is not supported by device 0000:00:1d.7

[   12.144739] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00

[   12.148613] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[   12.148712] usb usb4: configuration #1 chosen from 1 choice

[   12.148743] hub 4-0:1.0: USB hub found

[   12.148753] hub 4-0:1.0: 6 ports detected

[   12.254825] ata_piix 0000:00:1f.1: version 2.11

[   12.254843] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

[   12.254856] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

[   12.254908] PCI: Setting latency timer of device 0000:00:1f.1 to 64

[   12.255013] scsi0 : ata_piix

[   12.255071] scsi1 : ata_piix

[   12.255233] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14

[   12.255237] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15

[   12.572018] ata1.00: ATAPI: QSI CD-RW/DVD-ROM SBW-242, UD30, max UDMA/33

[   12.743887] ata1.00: configured for UDMA/33

[   12.907928] ata2.00: ATA-6: ST98823A, 3.04, max UDMA/100

[   12.907932] ata2.00: 156301488 sectors, multi 8: LBA48 

[   12.923874] ata2.00: configured for UDMA/100

[   12.924485] scsi 0:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UD30 PQ: 0 ANSI: 5

[   12.925001] scsi 1:0:0:0: Direct-Access     ATA      ST98823A         3.04 PQ: 0 ANSI: 5

[   12.925435] ACPI: PCI Interrupt 0000:02:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

[   12.975630] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafff800-faffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]

[   12.999549] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray

[   12.999555] Uniform CD-ROM driver Revision: 3.20

[   12.999858] sr 0:0:0:0: Attached scsi CD-ROM sr0

[   13.004722] sr 0:0:0:0: Attached scsi generic sg0 type 5

[   13.004746] scsi 1:0:0:0: Attached scsi generic sg1 type 0

[   13.020343] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   13.020530] sd 1:0:0:0: [sda] Write Protect is off

[   13.020533] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   13.021828] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   13.022006] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)

[   13.022018] sd 1:0:0:0: [sda] Write Protect is off

[   13.022021] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00

[   13.022039] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[   13.022045]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >

[   13.085031] sd 1:0:0:0: [sda] Attached SCSI disk

[   13.476717] Attempting manual resume

[   13.476722] swsusp: Resume From Partition 8:7

[   13.476724] PM: Checking swsusp image.

[   13.476994] PM: Resume from disk failed.

[   13.513615] kjournald starting.  Commit interval 5 seconds

[   13.513629] EXT3-fs: mounted filesystem with ordered data mode.

[   14.246690] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc0000fb58081]

[   21.562415] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   21.603132] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   21.625963] Linux agpgart interface v0.102 (c) Dave Jones

[   21.634329] agpgart: Detected an Intel 830M Chipset.

[   21.640156] agpgart: AGP aperture is 128M @ 0xe0000000

[   22.411196] iTCO_vendor_support: vendor-support=0

[   22.443162] Yenta: CardBus bridge found at 0000:02:04.0 [1028:0149]

[   22.443182] Yenta: Using CSCINT to route CSC interrupts to PCI

[   22.443185] Yenta: Routing CardBus interrupts to PCI

[   22.443190] Yenta TI: socket 0000:02:04.0, mfunc 0x00001002, devctl 0x64

[   22.463363] input: PC Speaker as /class/input/input2

[   22.525493] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)

[   22.672934] Yenta: ISA IRQ mask 0x04f8, PCI irq 11

[   22.672940] Socket status: 30000020

[   22.672943] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

[   22.672951] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff

[   22.672954] cs: IO port probe 0xd000-0xefff: clean.

[   22.673360] pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff

[   22.673363] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff

[   22.957230] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7

[   22.957235] PCI: setting IRQ 7 as level-triggered

[   22.957239] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7

[   22.957266] PCI: Setting latency timer of device 0000:00:1f.5 to 64

[   23.112597] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0

[   23.153103] input: SynPS/2 Synaptics TouchPad as /class/input/input3

[   23.156149] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)

[   23.156216] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[   23.177019] intel_rng: FWH not detected

[   23.311771] pccard: CardBus card inserted into slot 0

[   23.359228] ath_hal: module license 'Proprietary' taints kernel.

[   23.360473] cs: IO port probe 0x100-0x3af: clean.

[   23.361526] cs: IO port probe 0x3e0-0x4ff: clean.

[   23.361960] cs: IO port probe 0x820-0x8ff: clean.

[   23.362033] cs: IO port probe 0xc00-0xcf7: clean.

[   23.362505] cs: IO port probe 0xa00-0xaff: clean.

[   23.364487] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

[   23.461074] wlan: 0.8.4.2 (0.9.3.2)

[   23.486551] ath_pci: 0.9.4.5 (0.9.3.2)

[   23.783412] intel8x0_measure_ac97_clock: measured 55294 usecs

[   23.783417] intel8x0: clocking to 48000

[   23.787777] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)

[   23.787794] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

[   24.408752] ath_rate_sample: 1.2 (0.9.3.2)

[   24.409846] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

[   24.409853] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

[   24.409865] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

[   24.409869] wifi0: mac 7.8 phy 4.5 radio 5.6

[   24.409876] wifi0: Use hw queue 1 for WME_AC_BE traffic

[   24.409878] wifi0: Use hw queue 0 for WME_AC_BK traffic

[   24.409880] wifi0: Use hw queue 2 for WME_AC_VI traffic

[   24.409882] wifi0: Use hw queue 3 for WME_AC_VO traffic

[   24.409885] wifi0: Use hw queue 8 for CAB traffic

[   24.409886] wifi0: Use hw queue 9 for beacons

[   24.482095] wifi0: Atheros 5212: mem=0x58000000, irq=11

[   25.660957] lp: driver loaded but no devices found

[   25.737759] Adding 1951856k swap on /dev/sda7.  Priority:-1 extents:1 across:1951856k

[   27.647815] EXT3 FS on sda6, internal journal

[   31.724961] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

[   31.725235] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)

[   31.725287] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)

[   31.738545] No dock devices found.

[   31.813753] input: Lid Switch as /class/input/input4

[   31.819017] ACPI: Lid Switch [LID]

[   31.858977] input: Power Button (CM) as /class/input/input5

[   31.864244] ACPI: Power Button (CM) [PBTN]

[   31.903529] input: Sleep Button (CM) as /class/input/input6

[   31.908764] ACPI: Sleep Button (CM) [SBTN]

[   31.923814] ACPI: AC Adapter [AC] (off-line)

[   32.217119] ACPI: Battery Slot [BAT0] (battery present)

[   33.417219] ppdev: user-space parallel port driver

[   33.658598] audit(1194794393.765:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4575 profile="/usr/sbin/cupsd"
[   33.735096] apm: BIOS not found.
[   34.312215] Failure registering capabilities with primary security module.
[   34.526335] Bluetooth: Core ver 2.11
[   34.526489] NET: Registered protocol family 31
[   34.526492] Bluetooth: HCI device and connection manager initialized
[   34.526497] Bluetooth: HCI socket layer initialized
[   34.539000] Bluetooth: L2CAP ver 2.8
[   34.539005] Bluetooth: L2CAP socket layer initialized
[   34.590159] Bluetooth: RFCOMM socket layer initialized
[   34.590288] Bluetooth: RFCOMM TTY layer initialized
[   34.590291] Bluetooth: RFCOMM ver 1.8
[   35.449546] [drm] Initialized drm 1.1.0 20060810
[   35.458208] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   35.458215] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   35.461815] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   36.069079] NET: Registered protocol family 10
[   36.069279] lo: Disabled Privacy Extensions
[   37.173142] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   37.173303] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   37.173480] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   38.599916] [drm] Setting GART location based on new memory map
[   38.599969] [drm] writeback test succeeded in 1 usecs
[ 187.564509] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  187.564516] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  187.564519] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[  187.565121] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff

------------------------------------------------------------
> abishek@Delllaptop:~$ lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:04.0 CardBus bridge [0607]: Texas Instruments PCI4510 PC card Cardbus Controller [104c:ac44] (rev 02)
02:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4510 IEEE-1394 Controller [104c:8029]
03:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)[/QUOTE]

[B][I][COLOR="Red"]
COULD SOME ONE POINT ME IN THE DIRECTION I SHOULD BE GOING TO GET THIS TO WORK,I DONT HAVE THE SLIGHTEST IDEA WHAT TO DO RT NOW
[/COLOR][/I][/B]

---

### Post by Sef on 2007-11-14
Closed duplicate post.  [ Original Post]("http://ubuntuforums.org/showthread.php?t=608774").

---

