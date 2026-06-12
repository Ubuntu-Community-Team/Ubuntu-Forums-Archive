---
title: "prism3 usb laptop wireless problem w/7.04"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by trying_it_out on 2007-06-02
I am a newbie to Ubuntu & am having some problems getting my wireless working with 7.04. The hardware is a IEEE 802.11b PRISM3 USB, vender: AIRVAST Taiwan & the driver=prism2_usb. The drv Ubuntu loaded by default on install. Below is my output for lsmod, dmesg, ifconfig, iwconfig.

Any help with this would be greatly appreciated.

Module                  Size  Used by
usbhid                 26592  0 
hid                    27392  1 usbhid
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
longrun                 3592  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
container               5248  0 
ac                      6020  0 
video                  16388  0 
button                  8720  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
dock                   10268  0 
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
snd_ali5451            24460  1 
snd_ac97_codec         98464  1 snd_ali5451
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_timer              23684  2 snd_pcm,snd_seq
prism2_usb             74628  0 
p80211                 31884  1 prism2_usb
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    54020  12 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm
serio_raw               7940  0 
psmouse                38920  0 
i2c_ali1535             8324  0 
i2c_ali15x3             8964  0 
i2c_core               22656  3 i2c_ec,i2c_ali1535,i2c_ali15x3
efficeon_agp            9376  0 
agpgart                35400  1 efficeon_agp
af_packet              23816  4 
tsdev                   8768  0 
evdev                  11008  3 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
generic                 5124  0 [permanent]
alim15x3               13196  0 [permanent]
ohci_hcd               22532  0 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 usbhid,prism2_usb,ohci_hcd,ehci_hcd,uhci_hcd
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000eef0000 end: 000000000eff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000eff0000 size: 0000000000008000 end: 000000000eff8000 type: 3
[    0.000000] copy_e820_map() start: 000000000eff8000 size: 0000000000008000 end: 000000000f000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000eff0000 (usable)
[    0.000000]  BIOS-e820: 000000000eff0000 - 000000000eff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000eff8000 - 000000000f000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 239MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 61424) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    61424
[    0.000000]   HighMem     61424 ->    61424
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    61424
[    0.000000] On node 0 totalpages: 61424
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 447 pages used for memmap
[    0.000000]   Normal zone: 56881 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fad50
[    0.000000] ACPI: RSDT (v001 AMIINT AMIINT09 0x00000011 MSFT 0x00000097) @ 0x0eff0000
[    0.000000] ACPI: FADT (v001 AMIINT AMIINT09 0x00000011 MSFT 0x00000097) @ 0x0eff0030
[    0.000000] ACPI: DSDT (v001 TM5600    TMx86 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0f000000:f0fc0000)
[    0.000000] Detected 599.280 MHz processor.
[   14.657372] Built 1 zonelists.  Total pages: 60945
[   14.657422] Kernel command line: root=UUID=6bc829e5-ad22-4aef-8fc9-c3d535675eba ro quiet splash
[   14.662384] No local APIC present or hardware disabled
[   14.662685] mapped APIC to ffffd000 (011ea000)
[   14.663029] Initializing CPU#0
[   14.665885] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   14.671290] Console: colour VGA+ 80x25
[   14.674700] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.676321] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   14.720152] Memory: 232632k/245696k available (1992k kernel code, 12596k reserved, 896k data, 328k init, 0k highmem)
[   14.720236] virtual kernel memory layout:
[   14.720248]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.720259]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.720608]     vmalloc : 0xcf800000 - 0xff7fe000   ( 767 MB)
[   14.720632]     lowmem  : 0xc0000000 - 0xceff0000   ( 239 MB)
[   14.720643]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   14.720653]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   14.720663]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   14.720694] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.841968] Calibrating delay using timer specific routine.. 1213.51 BogoMIPS (lpj=2427032)
[   14.852313] Security Framework v1.0.0 initialized
[   14.852416] SELinux:  Disabled at boot.
[   14.854659] Mount-cache hash table entries: 512
[   14.874929] CPU: After generic identify, caps: 0084893f 0081813f 00000000 00000000 00000000 00000000 00000000
[   14.875040] CPU: After vendor identify, caps: 0084893f 0081813f 0000000e 00000000 00000000 00000000 00000000
[   14.875774] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (32 bytes/line)
[   14.875801] CPU: L2 Cache: 512K (128 bytes/line)
[   14.875833] CPU: Processor revision 1.3.2.0, 600 MHz
[   14.875990] CPU: Code Morphing Software revision 4.2.7-8-278
[   14.876430] CPU: 20011004 02:04 official release 4.2.7#7
[   14.876519] CPU serial number disabled.
[   14.876538] CPU: After all inits, caps: 0080893f 0081813f 0000000e 00000000 00000000 00000000 00000000
[   14.876655] Compat vDSO mapped to ffffe000.
[   14.876704] Remapping vsyscall page to ffffe000
[   14.877979] Checking 'hlt' instruction... OK.
[   14.894147] SMP alternatives: switching to UP code
[   14.897490] Freeing SMP alternatives: 11k freed
[   14.939807] Early unpacking initramfs... done
[   16.350766] ACPI: Core revision 20060707
[   16.364600] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.429185] ACPI: setting ELCR to 0008 (from 0e20)
[   16.436794] CPU0: Transmeta(tm) Crusoe(tm) Processor TM5600 stepping 03
[   16.436874] SMP motherboard not detected.
[   16.436899] Local APIC not detected. Using dummy APIC emulation.
[   16.439528] Brought up 1 CPUs
[   16.457867] Booting paravirtualized kernel on bare hardware
[   16.467226] Time:  5:54:48  Date: 05/02/107
[   16.468483] NET: Registered protocol family 16
[   16.477280] EISA bus registered
[   16.477348] ACPI: bus type pci registered
[   16.511375] PCI: PCI BIOS revision 2.10 entry at 0xfda61, last bus=0
[   16.511412] PCI: Using configuration type 1
[   16.511436] Setting up standard PCI resources
[   16.747234] ACPI: Interpreter enabled
[   16.747295] ACPI: Using PIC for interrupt routing
[   16.765046] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.765208] PCI: Probing PCI hardware (bus 00)
[   16.812024] Boot video device is 0000:00:09.0
[   16.815246] PCI quirk: region 0800-083f claimed by ali7101 ACPI
[   16.815385] PCI quirk: region 0c00-0c1f claimed by ali7101 SMB
[   16.816302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.891158] ACPI: Power Resource [URP1] (off)
[   16.893464] ACPI: Power Resource [URP2] (off)
[   16.894005] ACPI: Power Resource [FDDP] (off)
[   16.895504] ACPI: Power Resource [LPTP] (off)
[   16.906667] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14 *15), disabled.
[   16.909941] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   16.913551] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 12 14 15)
[   16.916005] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *9 10 11 12 14 15)
[   16.919718] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 14 15) *9, disabled.
[   16.922398] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15), disabled.
[   16.927899] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.932307] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 14 15)
[   16.934277] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   16.934800] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.935122] pnp: PnP ACPI init
[   16.968757] pnp: PnP ACPI: found 10 devices
[   16.968869] PnPBIOS: Disabled by ACPI PNP
[   16.969691] PCI: Using ACPI for IRQ routing
[   16.970114] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.981323] NET: Registered protocol family 8
[   16.981353] NET: Registered protocol family 20
[   16.988051] NET: Registered protocol family 2
[   17.025227] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   17.028408] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   17.029328] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   17.029953] TCP: Hash tables configured (established 8192 bind 4096)
[   17.030009] TCP reno registered
[   17.046413] checking if image is initramfs... it is
[   19.533487] Freeing initrd memory: 6771k freed
[   19.536727] audit: initializing netlink socket (disabled)
[   19.536918] audit(1180763691.048:1): initialized
[   19.539978] VFS: Disk quotas dquot_6.5.1
[   19.540307] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.541663] io scheduler noop registered
[   19.541703] io scheduler anticipatory registered
[   19.541727] io scheduler deadline registered
[   19.541796] io scheduler cfq registered (default)
[   19.542218] Activating ISA DMA hang workarounds.
[   19.549016] isapnp: Scanning for PnP cards...
[   19.912979] isapnp: No Plug & Play device found
[   20.062514] Real Time Clock Driver v1.12ac
[   20.062793] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.065173] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.075474] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.080476] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
[   20.080521] PCI: setting IRQ 9 as level-triggered
[   20.080542] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 9 (level, low) -> IRQ 9
[   20.094672] 0000:00:08.0: ttyS1 at I/O 0xda28 (irq = 9) is a 8250
[   20.108473] 0000:00:08.0: ttyS2 at I/O 0xda40 (irq = 9) is a 8250
[   20.117529] 0000:00:08.0: ttyS3 at I/O 0xda50 (irq = 9) is a 8250
[   20.118637] Couldn't register serial port 0000:00:08.0: -28
[   20.119676] mice: PS/2 mouse device common for all mice
[   20.138347] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.142475] input: Macintosh mouse button emulation as /class/input/input0
[   20.143356] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.144068] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.149903] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   20.152330] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.153823] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.153914] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.153960] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.154005] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.154050] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.155122] EISA: Probing bus 0 at eisa.0
[   20.156750] EISA: Detected 0 cards.
[   20.193491] TCP cubic registered
[   20.193594] NET: Registered protocol family 1
[   20.193990] Using IPI No-Shortcut mode
[   20.194696] ACPI: (supports S0 S1 S4 S5)
[   20.195513] Time: tsc clocksource has been installed.
[   20.195713]   Magic number: 11:566:920
[   20.198789] Freeing unused kernel memory: 328k freed
[   20.205961] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.015981] Capability LSM initialized
[   24.674339] ACPI: Processor [CPU1] (supports 8 throttling states)
[   28.496796] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   28.497021] 8139cp 0000:00:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   28.497041] 8139cp 0000:00:05.0: Try the "8139too" driver instead.
[   28.511130] 8139too Fast Ethernet driver 0.9.28
[   28.513876] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   28.513918] PCI: setting IRQ 5 as level-triggered
[   28.513939] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   28.517530] eth0: RealTek RTL8139 at 0xcf820e00, 00:0a:e6:ba:f1:23, IRQ 5
[   28.517556] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   28.546692] usbcore: registered new interface driver usbfs
[   28.546937] usbcore: registered new interface driver hub
[   28.547224] usbcore: registered new device driver usb
[   28.552991] USB Universal Host Controller Interface driver v3.0
[   28.556216] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   28.556258] PCI: setting IRQ 11 as level-triggered
[   28.556279] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   28.556404] uhci_hcd 0000:00:0a.0: UHCI Host Controller
[   28.557993] uhci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 1
[   28.558203] uhci_hcd 0000:00:0a.0: irq 11, io base 0x0000de80
[   28.562610] usb usb1: configuration #1 chosen from 1 choice
[   28.562994] hub 1-0:1.0: USB hub found
[   28.563183] hub 1-0:1.0: 2 ports detected
[   28.674917] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   28.675047] uhci_hcd 0000:00:0a.1: UHCI Host Controller
[   28.676066] uhci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 2
[   28.676261] uhci_hcd 0000:00:0a.1: irq 5, io base 0x0000df00
[   28.680672] usb usb2: configuration #1 chosen from 1 choice
[   28.681000] hub 2-0:1.0: USB hub found
[   28.681155] hub 2-0:1.0: 2 ports detected
[   28.709974] SCSI subsystem initialized
[   28.735776] libata version 2.20 loaded.
[   28.854536] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   28.856991] ACPI: PCI Interrupt Link [LNKP] enabled at IRQ 10
[   28.857033] PCI: setting IRQ 10 as level-triggered
[   28.857054] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LNKP] -> GSI 10 (level, low) -> IRQ 10
[   28.857453] ohci_hcd 0000:00:14.0: OHCI Host Controller
[   28.859004] ohci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[   28.859266] ohci_hcd 0000:00:14.0: irq 10, io mem 0xeffaf000
[   28.936593] usb usb3: configuration #1 chosen from 1 choice
[   28.936955] hub 3-0:1.0: USB hub found
[   28.937103] hub 3-0:1.0: 2 ports detected
[   29.050803] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   29.050859] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   29.051009] ehci_hcd 0000:00:0a.2: EHCI Host Controller
[   29.051898] ehci_hcd 0000:00:0a.2: new USB bus registered, assigned bus number 4
[   29.052627] ehci_hcd 0000:00:0a.2: irq 9, io mem 0xeffaef00
[   29.052676] ehci_hcd 0000:00:0a.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   29.054930] usb usb4: configuration #1 chosen from 1 choice
[   29.057345] hub 4-0:1.0: USB hub found
[   29.057514] hub 4-0:1.0: 4 ports detected
[   29.304158] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[   29.304458] ACPI: Unable to derive IRQ for device 0000:00:10.0
[   29.304480] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[   29.304917] ALI15X3: chipset revision 196
[   29.304940] ALI15X3: not 100% native mode: will probe irqs later
[   29.305121]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[   29.305464]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[   29.305608] Probing IDE interface ide0...
[   29.491334] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   29.595693] hda: FUJITSU MHS2030AT, ATA DISK drive
[   29.709528] usb 3-1: configuration #1 chosen from 1 choice
[   30.936320] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.938833] Probing IDE interface ide1...
[   31.674644] hdc: Slimtype COMBO LSC-24081, ATAPI CD/DVD-ROM drive
[   32.011068] ide1 at 0x170-0x177,0x376 on irq 15
[   32.096366] hda: max request size: 128KiB
[   32.496526] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[   32.497395] hda: cache flushes supported
[   32.499938]  hda: hda1 hda2 < hda5 >
[   32.611814] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   32.611894] Uniform CD-ROM driver Revision: 3.20
[   33.478886] Attempting manual resume
[   33.478924] swsusp: Resume From Partition 3:5
[   33.478934] PM: Checking swsusp image.
[   33.482686] PM: Resume from disk failed.
[   33.589448] kjournald starting.  Commit interval 5 seconds
[   33.590076] EXT3-fs: mounted filesystem with ordered data mode.
[   56.488639] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   58.924777] NET: Registered protocol family 17
[   66.735032] Linux agpgart interface v0.102 (c) Dave Jones
[   66.830559] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   66.830630] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   68.247816] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x1d48b1, caps: 0x904713/0x4006
[   68.281977] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   70.894079] input: PC Speaker as /class/input/input3
[   71.307470] prism2usb_init: prism2_usb.o: 0.2.5 Loaded
[   71.307493] prism2usb_init: dev_info is: prism2_usb
[   71.439105] usbcore: registered new interface driver prism2_usb
[   71.794590] parport: PnPBIOS parport detected.
[   71.794811] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   72.897919] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   72.897983] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[   75.972950] AC'97 1 does not respond - RESET
[   75.985047] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   75.985146] ali mixer 1 creating error.
[   76.968311] fuse init (API version 7.8)
[   77.080721] lp0: using parport0 (interrupt-driven).
[   77.406324] Adding 698788k swap on /dev/disk/by-uuid/33108970-767d-4ab7-bf87-6f0db031e6fb.  Priority:-1 extents:1 across:698788k
[   77.915698] EXT3 FS on hda1, internal journal
[   78.622952] NET: Registered protocol family 10
[   78.625083] lo: Disabled Privacy Extensions
[   88.025995] No dock devices found.
[   88.279075] Using specific hotkey driver
[   88.491310] input: Power Button (FF) as /class/input/input4
[   88.492946] ACPI: Power Button (FF) [PWRF]
[   88.523250] input: Power Button (CM) as /class/input/input5
[   88.525437] ACPI: Power Button (CM) [PWRB]
[   88.539429] input: Lid Switch as /class/input/input6
[   88.541841] ACPI: Lid Switch [LID0]
[   89.550573] eth0: no IPv6 routers present
[   89.553753] ibm_acpi: ec object not found
[   90.288035] pcc_acpi: loading...
[  136.004327] ppdev: user-space parallel port driver
[  147.499672] apm: BIOS not found.
[  149.157539] Bluetooth: Core ver 2.11
[  149.159136] NET: Registered protocol family 31
[  149.159200] Bluetooth: HCI device and connection manager initialized
[  149.159273] Bluetooth: HCI socket layer initialized
[  150.382160] Bluetooth: L2CAP ver 2.8
[  150.382273] Bluetooth: L2CAP socket layer initialized
[  150.454411] Bluetooth: RFCOMM socket layer initialized
[  150.454682] Bluetooth: RFCOMM TTY layer initialized
[  150.455114] Bluetooth: RFCOMM ver 1.8
[  155.499482] eth0: no IPv6 routers present
[  174.114838] usb 2-1: new low speed USB device using uhci_hcd and address 2
[  174.308718] usb 2-1: configuration #1 chosen from 1 choice
[  175.242842] usbcore: registered new interface driver hiddev
[  175.298016] input: Logitech USB Receiver as /class/input/input7
[  175.318352] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:0a.1-1
[  175.320100] usbcore: registered new interface driver usbhid
[  175.321680] drivers/usb/input/hid-core.c: v2.6:USB HID core driver


eth0      Link encap:Ethernet  HWaddr 00:0A:E6:BA:F1:23  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:feba:f123/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1914 (1.8 KiB)  TX bytes:4060 (3.9 KiB)
          Interrupt:5 Base address:0xe00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.


Thanks in advance, everyone ...

---

