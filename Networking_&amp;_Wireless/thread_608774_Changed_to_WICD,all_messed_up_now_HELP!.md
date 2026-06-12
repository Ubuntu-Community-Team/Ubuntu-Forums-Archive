---
title: "Changed to WICD,all messed up now HELP!"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by abishek22 on 2007-11-10
i use a D-Link** DWL-630** H/W version D1 F/W Version 4.10 PCMCIA Adapter Connecting to a Linksys WRT54GS Router

after installing UBUNTU gutsy when the card was plugged in it Detected all available WIFI networks (showed a window about a restriced driver in use)BUT failed to logon to my WEP enabled router,my ten digit HEx password wouldn't work.Despite it being 100% correct



> Having read up that WICD was a better alternative i installed it now the Wireless card doesn't seem to be detected in WICD HELP!!!!!!!




when i run DMESG it shows a ath0:

when i type IWConfig it shows a WIFI signal but no Channel is shown and my SSID just shows as "Nickname"



WHAT can i do or rather what do i do HELP should i go back to network manger? how do i do that?


network-manager-gnome package do i search for this in synaptic or try configuring the card no help seems forthcoming on Google regarding this card HELP!!!!!!!!!!


[COLOR="Black"][FONT="Courier New"][SIZE="4"]i can replace network manger using synaptic,but can some one tell me what to do how to connect to the internet it wasnt connecting using the password. if i reinstall network mager will IWSCAN command work then?[/SIZE][/FONT][/COLOR]

---

### Post by kevdog on 2007-11-10
Forget wicd for the time being and lets just troubleshoot your connection using the command line to see if its a driver problem, or network configuration problem

Can you post the following:
lshw -C network
iwlist scan

Also take a look at my guide in the signature about connecting from the command line.  Lets get it up and running this way first before moving onto WICD.

---

### Post by abishek22 on 2007-11-11
Can you post the following:
lshw -C network
iwlist scan



[B]
i have posted the following commands
sudo lshw -C network
sudo iwlist scan
lsmod
dmesg
lspci -nn

[/B]







abishek@Delllaptop:~$ sudo lshw -C network

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











abishek@Delllaptop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



wifi0     Interface doesn't support scanning.



ath0      Interface doesn't support scanning : Network is down








abishek@Delllaptop:~$ lsmod

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














abishek@Delllaptop:~$ dmesg

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

[  187.564509] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.

[  187.564516] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.

[  187.564519] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

[  187.565121] cs: memory probe 0xf6000000-0xfbffffff: excluding 0xf6000000-0xf65fffff 0xfae00000-0xfb3fffff













abishek@Delllaptop:~$ lspci -nn

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

03:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)

---

### Post by abishek22 on 2007-11-12
[SIZE="6"]Help.........[/SIZE]

---

### Post by SpiritIsReality on 2007-11-14
howdy
could you see if this is any help?
sorry, late night. see post #10
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+dwl-630+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+dwl-630+&btnG=Search&meta=) 
trails

---

### Post by SpiritIsReality on 2007-11-14
howdy 
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

trails

---

### Post by Peter09 on 2007-11-14
Note that in the preferences section of WICD there is the facility to change your driver. Make sure the right one is selected there.

---

### Post by SpiritIsReality on 2007-11-14
network-manager-gnome is in synaptic.

---

### Post by SpiritIsReality on 2007-11-14
sudo aptitude -s remove --purge wicd
will simulate the removal of wicd
if it looks alright, then you could run
sudo aptitude remove --purge wicd

sudo aptitude install network-manager-gnome
trails

---

### Post by abishek22 on 2007-11-14
> **SpiritIsReality said:**
> howdy
could you see if this is any help?
[http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=DWL+630&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=DWL+630&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images) 
trails

Well the only Search result is this thread itself

---

### Post by abishek22 on 2007-11-14
[B]I can do that, but whats the use in Reinstalling network manger when it won't work, can some one tell me how to connect to WIFI. i have tried connecting using command line the Results are in the post above


i dont know what to do,the Dmesg says i use a ATH0. what do i do after that to make it work.


i tried changing all the drivers one by one in WICD even then it doesn't show any available wireless networks

I have read the connecting wifi Documentation but when i run IWSCAN i don't see my network.HELP!!!

what exactly am i expected to do here?
what is madwifi,ndswraper?
Am i supposd to figure out a way to make it work using network manger itself or am i to figure out how to do it using MADWIFI NDS WRAPPER?

[FONT="Impact"][SIZE="7"][COLOR="Red"]HELP[/COLOR][/SIZE][/FONT]



[/B]

---

### Post by abishek22 on 2007-11-14
bump

---

### Post by SpiritIsReality on 2007-11-14
> **abishek22 said:**
> Well the only Search result is this thread itself

haha! I sure messed up there! here's what I trimmed, to get to you, haha!
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+dwl-630+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+dwl-630+&btnG=Search&meta=)
I thought so surely that the thread I found fit your problem so well, I didn't even look at it. haha!

---

### Post by patrickfromspain on 2007-11-14
probably you will need to use ndiswrapper. No sure if you card is supported with the driver included in ubuntu (happens with some new atheros chipsets..)

---

### Post by abishek22 on 2007-11-14
> **patrickfromspain said:**
> probably you will need to use ndiswrapper. No sure if you card is supported with the driver included in ubuntu (happens with some new atheros chipsets..)

**how do i check if the card is supported?**

---

### Post by SpiritIsReality on 2007-11-14
[http://www.serverwatch.com/tutorials/article.php/3703926](http://www.serverwatch.com/tutorials/article.php/3703926)
[http://www.google.ca/search?hl=en&q=linux+hardware+discovery+commands&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+hardware+discovery+commands&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+supported+wireless+chips&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+supported+wireless+chips&btnG=Google+Search&meta=)
[http://www.google.ca/search?as_q=ubuntu+wifi++beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=howto+guides+tutorials+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.ca/search?as_q=ubuntu+wifi++beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=howto+guides+tutorials+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by abishek22 on 2007-11-14
> **SpiritIsReality said:**
> [http://www.serverwatch.com/tutorials/article.php/3703926](http://www.serverwatch.com/tutorials/article.php/3703926)
[http://www.google.ca/search?hl=en&q=linux+hardware+discovery+commands&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+hardware+discovery+commands&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=linux+supported+wireless+chips&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+supported+wireless+chips&btnG=Google+Search&meta=)
[http://www.google.ca/search?as_q=ubuntu+wifi++beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=howto+guides+tutorials+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.ca/search?as_q=ubuntu+wifi++beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=howto+guides+tutorials+&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)




[COLOR="Blue"]i Already posted the LSHW command[/COLOR],can u tell me what the output says,I'm not a Techie Geek. i can run commands thats fine. i don't have the tech know how to do a Hardware discovery.

What do i need to be doing here. google says this WIFI card works with MADWIFI .. what exactly am i to do next???i don't have the slightest idea what MADwifi is in fact this is the first time i'm even hearing of it.

---

### Post by SpiritIsReality on 2007-11-14
I'm not very good at wireless, sorry

---

### Post by SpiritIsReality on 2007-11-14
> **SpiritIsReality said:**
> I'm not very good at wireless, sorry
[http://www.google.ca/search?hl=en&q=ubuntu+%22wireless+consultants%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+%22wireless+consultants%22&btnG=Search&meta=)

---

### Post by abishek22 on 2007-11-15
> **SpiritIsReality said:**
> [http://www.google.ca/search?hl=en&q=ubuntu+%22wireless+consultants%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+%22wireless+consultants%22&btnG=Search&meta=)
You exoect me to hire a Wireless Consultant?
C Mon' 

[FONT="Impact"][SIZE="5"][COLOR="Red"] HELP [/COLOR][/SIZE][/FONT]

---

### Post by abishek22 on 2007-11-22
[B][COLOR="Blue"][SIZE="4"]GOT MY WIFI TO WORK? 

WICD NOW CONNECTS TO MY UNSECURED NETWORK,BUT I CANNOT BROWSE ANY WEBPAGES UNLESS ITS  ENTERED IN THE NUMERICAL FORM I.E   4343.343.2342.2423 

EVERY THING ELSE WORKS I CAN ACCESS MY WIFI ROUTER CONFIG PAGE VIA 198.168.1.1 AND MY ADSL ROUTER CONNECTED TO IT. I CAN PING THE ROUTER ALSO



WHEN I RUN A DHCLIENT COMMAND FROM TERMINAL PROMPT I GET THE CORRECT OUTPUT ALSO, I UNDERSTAND THIS IS A DHCP PROBLEM IS THERE ANY WAY TO FIX IT?
[/SIZE][/COLOR][/B]

---

### Post by abishek22 on 2007-11-22
bump

---

### Post by abishek22 on 2007-11-22
bump

---

### Post by raiwo on 2007-11-22
check your ISP's DNS server addresses & enter them manually

---

### Post by abishek22 on 2007-11-22
NETGEAR ADSL MODEM 


status page


> Account Name 	mygateway
Firmware Version 	V3.4.0_ap
 
ADSL Port
MAC Address 	00:0F:B5:33:E2:13
Network Type 	PPPOE
IP Address 	122.xxx.xxx.89
IP Subnet Mask 	255.255.255.255
Gateway IP Address 	61.95.227.225
Domain Name Server 	203.145.184.40
203.145.184.32
 
LAN Port
MAC Address 	00:0F:B5:33:E2:10
IP Address 	192.168.0.1
DHCP 	On
IP Subnet Mask 	255.255.255.0
 
Modem
ADSL Firmware Version 	3.00.12.00
Modem Status 	Connected
Connect Mode 	G.DMT
Down Stream 	576kbps
Up Stream 	576kbps
VPI 	1
VCI 	32






> 
abishek@Delllaptop:~$ sudo dhclient ath0
[sudo] password for abishek:
There is already a pid file /var/run/dhclient.pid with pid 8177
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:f9:dc:43
Sending on   LPF/ath0/00:11:95:f9:dc:43
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 35071 seconds.




> 
abishek@Delllaptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:F9:DC:43  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fef9:dc43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4306541 (4.1 MB)  TX bytes:824779 (805.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:0D:56:AE:87:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 

eth1:avah Link encap:Ethernet  HWaddr 00:0D:56:AE:87:EB  
          inet addr:169.254.9.119  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138906 (135.6 KB)  TX bytes:138906 (135.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-F9-DC-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32321 errors:0 dropped:0 overruns:0 frame:1560
          TX packets:7667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:7187679 (6.8 MB)  TX bytes:1007045 (983.4 KB)
          Interrupt:11 




> LINSYS WIFI ROUTER STATUS PAGE

Firmware Version:   	v1.06.1, Apr. 11, 2006  	   	 
  	  	  	Current Time:  	Thu, 22 Nov 2007 14:00:32 	  	 
  	  	  	MAC Address:  	00:16:B6:2A:7D:78 	  	 
  	  	  	Router Name:  	WRT54GSV4  	  	 
  	  	  	Host Name:  	  	  	 
  	  	  	Domain Name:  		  	 

Internet
	  	  	 

Configuration Type
	  	  	Login Type:  	Automatic Configuration - DHCP 	  	 
  	  	  	IP Address:  	192.168.0.2 	  	 
  		  	Subnet Mask:  	255.255.255.0 	  	
  		  	Default Gateway:  	192.168.0.1 	  	
  	  	  	DNS 1:  	192.168.0.1 	  	 
  	  	  	DNS 2:  		  	 
  	  	  	DNS 3:  		  	 
  	  	  	MTU:  	1500

---

### Post by raiwo on 2007-11-22
> Atheros AR5005GChipset:	AR5005G = (AR2413) 
Chip:	AR2413 (802.11b+g) 
URL:	[http://www.atheros.com/pt/AR5005G.htm](http://www.atheros.com/pt/AR5005G.htm) 
Supports:	IEEE 802.11b, 802.11g 
Working: 	not working with version 0.9.2, dmesg reports: "unable to attach hardware: 'Hardware revision not supported' (HAL status 13)" 
Notes: 	Several tickets indicate this; no response was ever given. However, some users have reported success, but could not confirm this. 
Notes: 	Works perfectly on Slackware 11 (kernel 2.6.18.3) and madwifi 0.9.2. Just modprobe ath_pci after compiling/installing. (this on an Acer 3102 wlmi) 
Notes: 	For Kernel 2.6.22.1 use trunk version (madwifi 0.9.3.1 release doesn't compile): svn checkout [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi . That works perfectly (I'm running Slackware 12 on Acer 3102wlmi). 
Notes: 	I can confirm that this chipset works great with the madwifi-ng drivers on Debian Testing. Also monitor mode. 
Notes: 	chipset is AR1423, as you can see through URL 
Notes: 	This chipset works on the Acer Aspire 5040 if you install the acer_acpi driver [http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html) 
Notes: 	Works on the Acer Aspire 3053 if you reload the modules (see [http://rik.rikva.nl/?q=node/10](http://rik.rikva.nl/?q=node/10)) and then run depmod -a (as root) 
Notes: 	Works on the Acer Aspire 5051 using madwifi source pulled 2006-12-18 (OpenSuSE 10.2/x86_64) 
Notes: 	Works on the Acer Aspire 5100 using madwifi source (Mandriva 2007.0/x86_64) 
Notes: 	Cheap Ativa card works ok in gentoo. /etc/init.d/net.athx start does not ifconfig athx up the device, so preferred wireless won't work
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

---

### Post by abishek22 on 2007-11-22
> **raiwo said:**
> [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

is that supposed to mean my card won't work?

---

### Post by raiwo on 2007-11-22
I assume your wireless worked with network manager? if so it should work with wicd. Can you see any wireless networks in wicd?post what** ifconfig **gives. Check in wicd preferences that you got correct wireless interface chosen (in my case it's wlan0) ifconfig tells you the correct one.

---

### Post by abishek22 on 2007-11-22
> **raiwo said:**
> I assume your wireless worked with network manager? if so it should work with wicd. Can you see any wireless networks in wicd?post what** ifconfig **gives. Check in wicd preferences that you got correct wireless interface chosen (in my case it's wlan0) ifconfig tells you the correct one.



i'm already there wifi network is detected and connected, wicd says connected also.. only problem cannot open anything in firefox, i can even download things via synaptic.

i think it means there is a DNS error, i can open google by typing in 64.233.167.104 

google won't open if i type in google.com 

[SIZE="7"]HELP[/SIZE]

---

### Post by raiwo on 2007-11-22
only advice i can give you is double check if your dns settings is in automatic dhcp in system->administration->network-wireless & asking your isp those DNS server addresses & enter them manually

---

### Post by abishek22 on 2007-11-22
is this there in the router status info that i posted

---

### Post by raiwo on 2007-11-22
should be 203.145.184.40 & 203.145.184.32 but i would check these if i were you

---

### Post by dead_end on 2007-11-22
> LINSYS WIFI ROUTER STATUS PAGE

Firmware Version: v1.06.1, Apr. 11, 2006
Current Time: Thu, 22 Nov 2007 14:00:32
MAC Address: 00:16:B6:2A:7D:78
Router Name: WRT54GSV4
Host Name:
Domain Name:

Internet


Configuration Type
Login Type: Automatic Configuration - DHCP
IP Address: 192.168.0.2
Subnet Mask: 255.255.255.0
[B]Default Gateway: 192.168.0.1
DNS 1: 192.168.0.1[/B]
DNS 2:
DNS 3:
MTU: 1500 

From looking at this I'd say your router is trying to use itself as a dns server. It sends out a dns query and it loops back to it self. I'd contact your ISP and ask them for the correct DNS server address. And then enter it manually into you router.



EDIT:
> Account Name mygateway
Firmware Version V3.4.0_ap

ADSL Port
MAC Address 00:0F:B5:33:E2:13
Network Type PPPOE
IP Address 122.xxx.xxx.89
IP Subnet Mask 255.255.255.255
Gateway IP Address 61.95.227.225
[B]Domain Name Server 203.145.184.40
203.145.184.32[/B]

LAN Port
MAC Address 00:0F:B5:33:E2:10
IP Address 192.168.0.1
DHCP On
IP Subnet Mask 255.255.255.0

Modem
ADSL Firmware Version 3.00.12.00
Modem Status Connected
Connect Mode G.DMT
Down Stream 576kbps
Up Stream 576kbps
VPI 1
VCI 32

Am I correct in thinking that this is pulled from your modem. if  so try inputing the dns addresses from this into your router. **MAKE SURE YOU WRITE DOWN THE ORIGINAL SETTINGS ON PAPER BEFORE YOU DO THIS! ** That way if it does not work you can go back to your original settings.

Before you do that, though Check the WICD panel and see if you can specify the settings that could be the problem.

---

### Post by abishek22 on 2007-11-22
> **dead_end said:**
> From looking at this I'd say your router is trying to use itself as a dns server. It sends out a dns query and it loops back to it self. I'd contact your ISP and ask them for the correct DNS server address. And then enter it manually into you router.



EDIT:


Am I correct in thinking that this is pulled from your modem. if  so try inputing the dns addresses from this into your router. [B]MAKE SURE YOU WRITE DOWN THE ORIGINAL SETTINGS ON PAPER.

 BEFORE YOU DO THIS! [/B] That way if it does not work you can go back to your original settings.



NO,IF I DUAL BOOT INTO XP IT WORKS FINE,so do two ther computer logged into the same linksys router.

so i think the problem is with ubuntu.

MY TELEPHONE LINE>SPLITTER> ADSL NETGEAR MODEM>VIA ETHERNET>LINKSYS WIFI ROUTER

?203.145.184.40 & 203.145.184.32 what do i do with  it

---

### Post by dead_end on 2007-11-22
open the WICD config panel. There should be a link for your wireless network. click on it. it should give you the option the change the dns settings. I don't use WICD so I am sorry if I can't be more specific

---

### Post by abishek22 on 2007-11-22
> **dead_end said:**
> open the WICD config panel. There should be a link for your wireless network. click on it. it should give you the option the change the dns settings. I don't use WICD so I am sorry if I can't be more specific

CHANGE DNS TO?

---

### Post by dead_end on 2007-11-22
203.145.184.40

If that does not work contact your ISP to get the correct dns address

---

### Post by abishek22 on 2007-11-23
203.145.184.40 

 203.145.184.32

changed dns in wicd still not workling

---

### Post by caricc on 2007-11-23
Post what kevdog has asked you to post. He is the BEST with WICD and the other networking problems.

---

### Post by abishek22 on 2007-11-24
> **caricc said:**
> Post what kevdog has asked you to post. He is the BEST with WICD and the other networking problems.

[COLOR="Black"]**i posted what he asked in the next post,within the day!1 week back**[/COLOR]

---

### Post by kevdog on 2007-11-24
If you post one more thing on this thread in large font or with exclamation points, or bold type I am no longer responding --- there is no fire going on in the building!!!

I dont understand this output:
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

There are two adapters listed -- one disabled and the other without a driver listed.  Is this still what this statement shows??

---

### Post by wieman01 on 2007-11-24
Buddy, avoid fonts bigger than the standard size. It annoys people...

You have a DNS issue, that's all. Since you can connect and browse the web using IP addresses, you are very close to solving your problem.

Please do this:
> sudo gedit /etc/resolv.conf
Enter your password and replace the contents with:
> nameserver 192.168.0.1
Remove everything else. Then restart the network:
> sudo /etc/init.d/network restart
You should have a working connect by now.

---

### Post by abishek22 on 2007-11-25
my laptop has a built in Ethernet port, which i had disabled via bios i think it must be referring to that, i'm not using it 


as for the commands i hv run them again after being able to conect this is the output below


> BEFORE I CONNECT TO WIFI USING WICD THIS IS THE OUTPUT FOR lshw -C network

abishek@Delllaptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 01
       serial: 00:0d:56:ae:87:eb
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=32 link=no module=b44 multicast=yes port=twisted pair
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
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


> BEFORE I CONNECT TO WIFI USING WICD THIS IS THE OUTPUT FOR IWLIST SCAN 


abishek@Delllaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.






> AFTER I CONNECT TO WIFI USING WICD THIS IS THE OUTPUT FOR IWLIST SCAN 


abishek@Delllaptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:16:B6:2A:7D:79
                    ESSID:"Home_Wifi_Network_1St_floor"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-55 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100


> AFTER I CONNECT TO WIFI USING WICD THIS IS THE OUTPUT FOR lshw -C network


abishek@Delllaptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 01
       serial: 00:0d:56:ae:87:eb
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 latency=32 link=no module=b44 multicast=yes port=twisted pair
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
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
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.101 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g





as for sudo gedit /etc/resolv.conf i tried it,  the line was already there AS nameserver 192.168.0.1.

---

### Post by abishek22 on 2007-11-25
can u give me the i.p address for this site i.e this forum, how can i find the i.p address for a few other sites that i want to browse to?

---

### Post by kevdog on 2007-11-25
Ok 

Your wireless card is using the madwifi driver (ath_pci).  Your interface name is ath0.  Try turning off encryption (WPA/WEP) on the router and try establishing a manual connection from the command line.  The link is in my signature.  We can turn WPA/WEP on later.

If you are having problems please list
route -n
/etc/dhcp3/dhclient.conf

---

### Post by abishek22 on 2007-11-25
> Ran folowing commands and a few pings


sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
abishek@Delllaptop:~$ route -n
sudo iwconfig ath0 essid "Home_Wifi_Network_1St_floor"
sudo iwconfig ath0 mode Managed
sudo dhclient ath0



> connected manually


abishek@Delllaptop:~$ sudo ifconfig ath0 down
[sudo] password for abishek:
abishek@Delllaptop:~$ sudo dhclient -r ath0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:f9:dc:43
Sending on   LPF/ath0/00:11:95:f9:dc:43
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
abishek@Delllaptop:~$ sudo ifconfig ath0 up
abishek@Delllaptop:~$ sudo iwconfig ath0 essid "Home_Wifi_Network_1St_floor"
abishek@Delllaptop:~$ sudo iwconfig ath0 mode Managed
abishek@Delllaptop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:f9:dc:43
Sending on   LPF/ath0/00:11:95:f9:dc:43
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 37594 seconds.
abishek@Delllaptop:~$ 



> route -n
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:95:f9:dc:43
Sending on   LPF/ath0/00:11:95:f9:dc:43
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 37594 seconds.
abishek@Delllaptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0




> contents dhclient.conf 
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}





contents of resolv.conf
nameserver 192.168.0.1

> 
abishek@Delllaptop:~$ ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from google.com (64.233.187.99): icmp_seq=1 ttl=239 time=260 ms
64 bytes from google.com (64.233.187.99): icmp_seq=2 ttl=239 time=254 ms
64 bytes from google.com (64.233.187.99): icmp_seq=3 ttl=239 time=251 ms
64 bytes from google.com (64.233.187.99): icmp_seq=4 ttl=239 time=254 ms
64 bytes from google.com (64.233.187.99): icmp_seq=5 ttl=239 time=255 ms

--- google.com ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5000ms
rtt min/avg/max/mdev = 251.560/255.186/260.054/2.875 ms
abishek@Delllaptop:~$ ping yahoo.com
PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from yahoo.com (66.94.234.13): icmp_seq=1 ttl=50 time=243 ms
64 bytes from yahoo.com (66.94.234.13): icmp_seq=2 ttl=50 time=242 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2001ms
rtt min/avg/max/mdev = 242.912/243.450/243.988/0.538 ms
abishek@Delllaptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=254 time=4.47 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=254 time=1.64 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=254 time=1.71 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 1.642/2.608/4.473/1.319 ms
abishek@Delllaptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=6.86 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.825 ms

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 0.825/3.842/6.860/3.018 ms
abishek@Delllaptop:~$ tracert google.com
The program 'tracert' is currently not installed.  You can install it by typing:
sudo apt-get install traceroute

---

### Post by abishek22 on 2007-11-25
oh,forgot still the same I'm connected & can access Google via ip address not Google.com


can you give me the i.p address for this forum. each time i'm forced to copy data/output from my laptop on to a pen drive then go to my desktop and paste into the forum.

---

### Post by kevdog on 2007-11-25
91.189.94.186  - Thats ubuntu forums

Here is your problems

Your subnet is 192.168.1.x
Your computer thinks your DNS server is 192.168.0.1  which is a totally different subnet.

Im not sure why this is happening.  What you might want to do is to manually specify the IP address's of your ISP DNS servers.  If you do not want to do this, or do not know the IP addresses, you can use OpenDNS.

Here are two posts how to do this:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)
[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by wieman01 on 2007-11-25
Change your DNS setting to "192.168.1.1" rather than "192.168.0.1" by editing "/etc/resolv.conf".
[U]
Then 2 more things:[/U]

A. Uninstall Firestarter if you have previously installed it.
B. Remove any Ethernet cable running from your PC to the router when you try to connect via wireless.

---

### Post by kevdog on 2007-11-25
Wieman -- is resolve.conf re-written every network connection or is it a constant?

---

### Post by wieman01 on 2007-11-25
> **kevdog said:**
> Wieman -- is resolve.conf re-written every network connection or is it a constant?
Usually it's overwritten every time you reconnect. But you can make the changes stick by changing permissions, etc. Just want to test if the DNS setting is the real issue. 

The connection is fine as he has pointed out, it's just that the DNS setting is somehow wrong. Overwriting "resolve.conf " should have immediate effect without the need to restart the network. At least that's the way it works on my computer(s).

Do you have an idea what else could be root cause of this problem?

---

### Post by kevdog on 2007-11-25
I think you are right on the money.  Ive found also the resolv.conf is the fastest way to make the changes as you suggested, however the changes don't stick.  I thought the proper way to make it stick was to edit the dhclient.conf file.

---

### Post by wieman01 on 2007-11-25
> **kevdog said:**
> I think you are right on the money.  Ive found also the resolv.conf is the fastest way to make the changes as you suggested, however the changes don't stick.  I thought the proper way to make it stick was to edit the dhclient.conf file.
Actually both of these aren't... at least that's what I would think. The right way would be to assign a (static) IP address in my opinion. 

So you'd make "/etc/resolv.conf" immutable by issuing:
> sudo chattr +i /etc/resolv.conf
That way you would not lose the setting even after a restart.

Last thing we could try is entering a public DNS' IP address (not the router's). Would you know one by chance? I don't...

---

### Post by kevdog on 2007-11-25
Not on the Ubuntu box right now, but Comcast's DNS servers are open (although they will not tell you this)

---

### Post by wieman01 on 2007-11-25
> **kevdog said:**
> Not on the Ubuntu box right now, but Comcast's DNS servers are open (although they will not tell you this)
Cool. Perhaps you can post their IP address later on. :-)

---

### Post by imdano on 2007-11-25
Make sure firestarter is off.  I've seen it cause problems like this before. ```
sudo firestarter --stop
```

---

### Post by abishek22 on 2007-11-25
> Change your DNS setting to "192.168.1.1" rather than "192.168.0.1" by editing "/etc/resolv.conf".



i tried changing the /etc/resolv.conf file to 1.1 from 0.1 earlier. it  still didn't work


> Then 2 more things:

A. Uninstall Firestarter if you have previously installed it.
B. Remove any Ethernet cable running from your PC to the router when you try to connect via wireless.


A  NO FIRESTARTER
B  ETHERNET TOTALLY DISABLED from bios

---

### Post by abishek22 on 2007-11-25
1
how do i add open dns to ubuntu?

2
do i need a static i.p address?

3
by doing this will this spoil my other working modem connection also?




> 
The OpenDNS nameservers are 208.67.222.222 and 208.67.220.220

Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

---

### Post by wieman01 on 2007-11-25
Hang on... you can ping Google and get a reply, don't you?
> ping [www.google.com](www.google.com)
But you cannot browse the web... what browser have you got?

---

### Post by wieman01 on 2007-11-25
Is Dansguardian enabled? If yes, please disable it.

---

### Post by abishek22 on 2007-11-25
> **wieman01 said:**
> Hang on... you can ping Google and get a reply, don't you?

But you cannot browse the web... what browser have you got?

firefox & opera

posted the ping comand in  previous page

---

### Post by abishek22 on 2007-11-25
> **imdano said:**
> Make sure firestarter is off.  I've seen it cause problems like this before. ```
sudo firestarter --stop
```

output

sudo firestarter:command not found




> **wieman01 said:**
> Is Dansguardian enabled? If yes, please disable it.


i don't think i have Dansguardian installed

---

### Post by kevdog on 2007-11-25
If you can get to google -- have the google web page -- but not others, try disabling ipv6.  The instructions were contained in the links I gave you earlier.

Right now you are not exactly clear what the problem is.

---

### Post by wieman01 on 2007-11-25
Yes, Kevdog could be right. You need to disable IPV6 in Firefox. The browser is the culprit.

---

### Post by abishek22 on 2007-11-25
> IPv6 Quick (Firefox) Fix

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router try the following:

Enter about:config in Firefox's address field.

Enter ipv6 in the new Filter: field.

Double click on the line left in the display window to change it's boolean value to true.

Restart Firefox.

& that should be that..


[COLOR="Red"][SIZE="4"]I HAVE IT WORKING[/SIZE][/COLOR]!!!!!!!!!!!now the building/(my laptops) on fire!!!!!!!!!!!!!!!!!]
[COLOR="Lime"]THANX---->>>kevdog,wieman01[/COLOR]:)
so, do i have to disable this globally?

> Disable IPv6 Globally

Unlike the method of editing /etc/modprobe.d/aliases, the following method does not run the risk of being overwritten.

Do the following to disable IPv6 globally:

1. To verify that the IPv6 module is loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
ipv6 265856 10

2. Then from a terminal type:

handy@birdfish:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

4. To verify that the IPv6 module is not loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
handy@birdfish:~$

If for whatever reason the above method does not work, type sudo nano -w /etc/modprobe.d/blacklist & enter the line blacklist-ipv6, then do steps 3. & 4. as above.

____________________

The reason for the first (DNS) problem which strikes lots of modem/routers is due to their windows centric design.

The reason for the second (IPv6) problem is due to the cheap quality of the router, which is also responsible for the first problem...

[Edit:] After having used other Linux distro's & PC-BSD, I have had to modify my conclusions as I have only experienced the above three problems when using *buntu, last verified on kubuntu 7.10.

---

### Post by wieman01 on 2007-11-25
> **abishek22 said:**
> [COLOR="Red"][SIZE="4"]I HAVE IT WORKING[/SIZE][/COLOR]!!!!!!!!!!!now the building/(my laptops) on fire!!!!!!!!!!!!!!!!!]
[COLOR="Lime"]THANX---->>>kevdog,wieman01[/COLOR]:)
so, do i have to disable this globally?
Not necessarily. If browsing performance is ok, then don't disable it globally. :-) Glad you got it working.

---

### Post by abishek22 on 2007-11-25
> **wieman01 said:**
> Not necessarily. If browsing performance is ok, then don't disable it globally. :-) Glad you got it working.

opera won't open pages with .com same problem persists...synaptic won't download either now,firefox works superb browsing speed.


just one thing. whats the best way to back up ubuntu via synaptic?

---

### Post by wieman01 on 2007-11-25
> **abishek22 said:**
> opera won't open pages with .com same problem persists...synaptic won't download either now,firefox works superb browsing speed.


just one thing. whats the best way to back up ubuntu via synaptic?
Then disable it globally.

Back up via Synaptic? I cannot quite follow... If you are looking for a backup solution, please have a crack at my Partimage tutorial (see signature).

---

### Post by abishek22 on 2007-11-25
> **wieman01 said:**
> Then disable it globally.

Back up via Synaptic? I cannot quite follow... If you are looking for a backup solution, please have a crack at my Partimage tutorial (see signature).

backup my whole ubuntu installation,after a lot of trouble every thing's working, don't want to go throu it again

---

### Post by wieman01 on 2007-11-25
> **abishek22 said:**
> back my whole ubuntu installation,after a lot of trouble every thing working, don't want to go throu it again
The my tutorial is definitely worthwhile. 

But that said, disabling IPV6 globally is recommended under the circumstances. Kevdog will agree with that.

---

### Post by abishek22 on 2007-11-25
1. To verify that the IPv6 module is loaded type the following from a terminal:

handy@birdfish:~$ lsmod | grep ipv6
> 
abishek@Delllaptop:~$ lsmod | grep ipv6
ipv6                  273892  22 





2. Then from a terminal type:

handy@birdfish:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

3. Restart

MY OUTPUT

> abishek@Delllaptop:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
bash: /etc/modprobe.d/blacklist-ipv6: Permission denied






abishek@Delllaptop:~$ sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied

---

### Post by abishek22 on 2007-11-25
Disabling ipv6 on Ubuntu 7.10

We’ll simply need to change a line in one of the configuration files that loads the ipv6 module to the kernel. As of yet I have not figured out a way to update this change outside of restarting the machine. If anyone has any suggestions on removing ipv6 “live” I would appreciate it.

Change the line is /etc/modprobe.d/aliases from:

    alias net-pf-10 ipv6

to

    alias net-pf-10 off


 command->    sudo gedit /etc/modprobe.d/aliases 

Again, at this point you’ll need to restart your machine for the change to take place

---

### Post by abishek22 on 2007-11-25
i'm stuck synaptic manger can't download anything now..

via aptget if i try this is the output

abishek@Delllaptop:~$ sudo apt-get install i8kutils gkrellm gkrellm-i8k
Reading package lists... Done
Building dependency tree       
Reading state information... Done
i8kutils is already the newest version.
The following packages were automatically installed and are no longer required:
  apache2-utils libapr1 libarchive-zip-perl apache2 apache2.2-common
  apache2-mpm-worker libfile-rsyncp-perl libaprutil1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gkrellm gkrellm-i8k
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 814kB of archives.
After unpacking 2310kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gkrellm gkrellm-i8k
Install these packages without verification [y/N]? y
0% [Connecting to archive.ubuntu.com (1.0.0.0)]


hangs at 0%



synaptic
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gkrellm/gkrellm_2.2.10-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gkrellm/gkrellm_2.2.10-2ubuntu1_i386.deb)
  


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gkrellm-i8k/gkrellm-i8k_2.5-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gkrellm-i8k/gkrellm-i8k_2.5-1_i386.deb)
  



Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.



[http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg)
[http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_IN.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2)
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2)
[http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release.gpg](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release.gpg)
[http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/i18n/Translation-en_IN.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/i18n/Translation-en_IN.bz2)
[http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release.gpg](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release.gpg)
[http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/i18n/Translation-en_IN.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/i18n/Translation-en_IN.bz2)
[http://wicd.longren.org/dists/feisty/Release.gpg](http://wicd.longren.org/dists/feisty/Release.gpg)
[http://wicd.longren.org/dists/feisty/extras/i18n/Translation-en_IN.bz2](http://wicd.longren.org/dists/feisty/extras/i18n/Translation-en_IN.bz2)


when ii click reload it shows //cdrom as a repository

---

### Post by kevdog on 2007-11-25
Edit your /etc/apt/sources list (could be sources.list) and remove the line that adds your ubuntu installation cd as a repository.  Should be fairly obvious.

---

### Post by abishek22 on 2007-11-26
sudo gedit /etc/apt/sources.list



> 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
# deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://wicd.longren.org](http://wicd.longren.org) feisty extras




WHEN I USE A DIAL UP MODEM SYNAPTIC AND APTGET STILL WORK PERFECTLY,PROBLEM IS ONLY PRESENT WITH MY WIFI CARD

---

### Post by kevdog on 2007-11-26
Not sure what the problem is b/c I don't understand what you are telling me.  Can you rephrase your problem without using a bunch of code for examples?

---

### Post by abishek22 on 2007-11-26
simple initial problem of me not being able to connect to internet via my wifi card is solved i.e can browse the internet now after following ur advice on ipv6 .. now my problem is synaptic has stopped working. when i try to install via apt get the same program

for example

abishek@Delllaptop:~$ sudo apt-get update
0% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubunt
abishek@Delllaptop:~$ 


i'm stuck at -> 0% until i press control+c



but then

if i try to ping
abishek@Delllaptop:~$ ping archive.canonical.com
PING archive.canonical.com (91.189.90.142) 56(84) bytes of data.
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=1 ttl=46 time=338 ms




let me say both synaptic and apet still work if i connect to the internet using another internet connection like my GPRS modem, so all probability synaptic and aptget still work but fail to work when i use the wifi  connection.. do u get me?

---

### Post by wieman01 on 2007-11-26
Ok, first of all we need to clean up your source list:
> sudo gedit /etc/apt/sources.list
The replace(!) the contents with:
```

deb http://archive.canonical.com/ubuntu gutsy partner
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted

```
That's all you need. 

Are you behind a proxy or do you have a direct connection to the Internet? Please do again (and post the output of):
> sudo apt-get update
> sudo apt-get upgrade
Let's see what happens.

---

### Post by abishek22 on 2007-11-26
> abishek@Delllaptop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for abishek:
edited sources list and filled in

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted

> 
abishek@Delllaptop:~$ sudo apt-get update
0% [Connecting to archive.canonical.com (1.0.0.0)] [Connecting to archive.ubunt


> 
abishek@Delllaptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  azureus bittorrent capplets-data compiz compiz-core compiz-gnome
  compiz-plugins cupsys cupsys-bsd cupsys-client cupsys-common eog evince
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins file-roller firefox
  firefox-gnome-support gcalctool gdm gedit gedit-common ghostscript
  ghostscript-x gnome-about gnome-cards-data gnome-control-center
  gnome-desktop-data gnome-games gnome-games-data gnome-menus gnome-panel
  gnome-panel-data gnome-screensaver gnome-session gnome-system-monitor
  gnome-system-tools gtk2-engines gtkhtml3.14 hwdb-client-common
  hwdb-client-gnome kdelibs-data kdelibs4c2a libc6 libc6-dev libc6-i686
  libcamel1.2-10 libcupsimage2 libcupsys2 libdecoration0 libebook1.2-9
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libflac8
  libgnome-desktop-2 libgnome-menu2 libgnome-window-settings1 libgnomeui-0
  libgnomeui-common libgs8 libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpango1.0-dev libpng12-0 libpng12-dev libpoppler-glib2
  libpoppler2 libqt3-mt libsmbclient libssl0.9.8 libwnck-common libwnck22
  linux-restricted-modules-2.6.22-14-generic linux-restricted-modules-common
  mencoder mplayer mplayer-doc openssl poppler-utils python-bittorrent
  python-gmenu samba-common smbclient sound-juicer tzdata ubufox
98 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 145MB of archives.
After unpacking 1843kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6-dev libc6 libc6-i686 tzdata libssl0.9.8 azureus bittorrent
  python-bittorrent capplets-data libdecoration0 libpango1.0-dev
  libpango1.0-common libpango1.0-0 libgnomeui-common libgnomeui-0
  libgnome-desktop-2 libedataserver1.2-9 libcamel1.2-10 libebook1.2-9
  libgnome-menu2 libpanel-applet2-0 libpng12-dev libpng12-0 gnome-menus
  python-gmenu gnome-desktop-data gnome-control-center
  libgnome-window-settings1 libwnck-common libwnck22 compiz-gnome
  compiz-plugins compiz-core compiz libcupsys2 libcupsimage2 libpoppler2
  poppler-utils libgs8 ghostscript cupsys-common cupsys cupsys-bsd
  cupsys-client eog libpoppler-glib2 ghostscript-x evince libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13
  evolution-data-server evolution-data-server-common libedataserverui1.2-8
  libexchange-storage1.2-3 libgtkhtml3.14-19 evolution evolution-common
  gtkhtml3.14 evolution-plugins file-roller firefox-gnome-support firefox
  gcalctool gdm gnome-session libgtksourceview2.0-common libgtksourceview2.0-0
  gedit-common gedit gnome-about gnome-games gnome-games-data gnome-cards-data
  gnome-panel-data gnome-panel gnome-screensaver gnome-system-monitor
  gtk2-engines hwdb-client-common hwdb-client-gnome kdelibs-data libqt3-mt
  kdelibs4c2a libflac8 linux-restricted-modules-common
  linux-restricted-modules-2.6.22-14-generic openssl smbclient samba-common
  sound-juicer ubufox gnome-system-tools libsmbclient mencoder mplayer
  mplayer-doc
Install these packages without verification [y/N]? y
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.
abishek@Delllaptop:~$ 






i did what ever u asked still stuck at 0% so i press control+c 
it works fine when using alternate internet connection via a MODEM,so i don't think sypnatic is spolit or broken

---

### Post by abishek22 on 2007-11-26
help ,th e whole point of getting wifi to work was, to b able to use synaptic to download things using broadband..

---

### Post by wieman01 on 2007-11-27
> **abishek22 said:**
> help ,th e whole point of getting wifi to work was, to b able to use synaptic to download things using broadband..
Update once again and wait a few minutes before you press "ctrl+c". If that does not work, please post back. I might have another idea.

---

### Post by abishek22 on 2007-11-27
No,tried again .It stay's at 0% for five minutes , any other ideas

---

### Post by kevdog on 2007-11-27
Can you ping the IP address of the repository??

---

### Post by wieman01 on 2007-11-27
> **kevdog said:**
> Can you ping the IP address of the repository??
He did so earlier in the thread, so that does not seem to be the problem. Let me think...

---

### Post by wieman01 on 2007-11-27
Please open the source list...
> sudo gedit /etc/apt/sources.list
...and paste this (replacing the contents once again):
```
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse
```
Then update:
> sudo apt-get update
> sudo apt-get upgrade

---

### Post by abishek22 on 2007-12-05
dude sorry 
 'Ive gone on a holiday once I'm back ill try it thnx again

---

