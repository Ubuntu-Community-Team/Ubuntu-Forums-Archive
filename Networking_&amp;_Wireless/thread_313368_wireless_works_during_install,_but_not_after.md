---
title: "wireless works during install, but not after"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by scubacuda on 2006-12-05
I have a weird problem on Kubuntu that I didn't have when I had Ubuntu installed on the same laptop.

I installed Kubuntu, and during the installation, it recognized my eth0 wireless interface. I chose eth1 (regular ethernet) as my default, and when I booted back up, it didn't recognize eth0.

**lspci**, **lsmod**, **dmesg**, **iwconfig**, and **ifconfig** are below:

```
root@kabuntop:~# **lspci**
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:02.0 Communication controller: 3Com Corporation Mini PCI 56k Winmodem
02:03.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
02:04.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:05.0 CardBus bridge: Texas Instruments PCI1420
02:05.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 41)
root@kabuntop:~# **lsmod**
Module                  Size  Used by
ipv6                  272288  8
nls_cp437               6912  1
isofs                  38076  1
udf                    89348  0
rfcomm                 42260  0
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2
drm                    74644  3 radeon
acpi_cpufreq            8644  1
speedstep_lib           5764  0
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  1
cpufreq_conservative     8712  0
video                  17540  0
tc1100_wmi              8324  0
sbs                    16804  0
sony_acpi               6412  0
pcc_acpi               14080  0
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0
dock                    8716  0
dev_acpi               12292  0
button                  7952  0
battery                11652  0
container               5632  0
ac                      6788  0
asus_acpi              17688  0
lp                     12964  0
af_packet              24584  2
snd_maestro3           27524  2
snd_ac97_codec         97696  1 snd_maestro3
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0
snd_pcm                84612  4 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0
snd_seq_oss            36480  0
snd_seq_midi            9984  0
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
hostap_pci             59152  0
hostap                123012  1 hostap_pci
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 40380  0
ieee80211_crypt         7552  1 hostap
joydev                 11200  0
tsdev                   9152  0
orinoco_pci             8320  0
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
snd                    58372  13 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
prism2_pci             74752  0
floppy                 63044  0
soundcore              11232  1 snd
e100                   38020  0
mii                     6912  1 e100
parport_pc             37796  1
parport                39496  2 lp,parport_pc
intel_agp              26012  1
agpgart                34888  2 drm,intel_agp
serio_raw               8452  0
yenta_socket           28812  2
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11392  2
psmouse                41352  0
hw_random               7320  0
pcspkr                  4352  0
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142728  1
jbd                    62228  1 ext3
uhci_hcd               24968  0
usbcore               134912  2 uhci_hcd
ide_generic             2432  0
ide_disk               18560  3
ide_cd                 33696  1
cdrom                  38944  1 ide_cd
piix                   11780  1
generic                 5764  0
thermal                15624  0
processor              31560  2 acpi_cpufreq,thermal
fan                     6020  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability
root@kabuntop:~#**dmesg**
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000007f60000 (usable)
[17179569.184000]  BIOS-e820: 0000000007f60000 - 0000000007f73c00 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000007f73c00 - 0000000007f80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000007f80000 - 0000000008000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 127MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 32608
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 28512 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6620
[17179569.184000] ACPI: RSDT (v001 PTLTD  EBRSDT   0x02100000  LTP 0x00000000) @ 0x07f6830a
[17179569.184000] ACPI: FADT (v001 QUANTA EBmador  0x02100000 RT2  0x00000001) @ 0x07f73b64
[17179569.184000] ACPI: BOOT (v001 PTLTD  EBBFTBL$ 0x02100000  LTP 0x00000001) @ 0x07f73bd8
[17179569.184000] ACPI: DSDT (v001 HP-MCD EB DSDT  0x02100000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7b80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0110a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[17179569.184000] Detected 930.336 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.188000] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.188000] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.196000] Memory: 119768k/130432k available (1910k kernel code, 10124k reserved, 1070k data, 308k init, 0k highmem)
[17179573.196000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.276000] Calibrating delay using timer specific routine.. 1862.39 BogoMIPS (lpj=3724785)
[17179573.276000] Security Framework v1.0.0 initialized
[17179573.276000] SELinux:  Disabled at boot.
[17179573.276000] Mount-cache hash table entries: 512
[17179573.276000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.276000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179573.276000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179573.276000] CPU: L2 cache: 512K
[17179573.276000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179573.276000] Checking 'hlt' instruction... OK.
[17179573.292000] SMP alternatives: switching to UP code
[17179573.292000] Freeing SMP alternatives: 16k freed
[17179573.292000] checking if image is initramfs... it is
[17179574.240000] Freeing initrd memory: 5214k freed
[17179574.240000] ACPI: Core revision 20060707
[17179574.244000] ACPI: Looking for DSDT ... not found!
[17179574.248000] ACPI: setting ELCR to 0200 (from 0420)
[17179574.276000] CPU0: Intel(R) Pentium(R) III Mobile CPU       933MHz stepping 01
[17179574.276000] SMP motherboard not detected.
[17179574.276000] Local APIC not detected. Using dummy APIC emulation.
[17179574.276000] Brought up 1 CPUs
[17179574.276000] migration_cost=0
[17179574.276000] NET: Registered protocol family 16
[17179574.276000] EISA bus registered
[17179574.276000] ACPI: bus type pci registered
[17179574.276000] PCI: PCI BIOS revision 2.10 entry at 0xfd968, last bus=2
[17179574.276000] PCI: Using configuration type 1
[17179574.276000] Setting up standard PCI resources
[17179574.296000] ACPI: Interpreter enabled
[17179574.296000] ACPI: Using PIC for interrupt routing
[17179574.296000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179574.296000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179574.296000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 6)
[17179574.296000] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[17179574.300000] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[17179574.300000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[17179574.300000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[17179574.300000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10) *0, disabled.
[17179574.300000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.300000] PCI: Probing PCI hardware (bus 00)
[17179574.312000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179574.312000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179574.312000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.312000] Boot video device is 0000:01:00.0
[17179574.312000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.312000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179574.312000] Please report the result to linux-kernel to fix this permanently
[17179574.312000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179574.312000] Please report the result to linux-kernel to fix this permanently
[17179574.312000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.324000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179574.332000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[17179574.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179574.340000] ACPI: Power Resource [PFAN] (off)
[17179574.340000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.340000] pnp: PnP ACPI init
[17179574.356000] pnp: PnP ACPI: found 12 devices
[17179574.356000] PnPBIOS: Disabled by ACPI PNP
[17179574.356000] PCI: Using ACPI for IRQ routing
[17179574.356000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.360000] PCI: Bridge: 0000:00:01.0
[17179574.360000]   IO window: 2000-2fff
[17179574.360000]   MEM window: d0100000-d01fffff
[17179574.360000]   PREFETCH window: d8000000-dfffffff
[17179574.360000] PCI: Bus 3, cardbus bridge: 0000:02:05.0
[17179574.360000]   IO window: 00003800-000038ff
[17179574.360000]   IO window: 00003c00-00003cff
[17179574.360000]   PREFETCH window: 10000000-11ffffff
[17179574.360000]   MEM window: 12000000-13ffffff
[17179574.360000] PCI: Bus 7, cardbus bridge: 0000:02:05.1
[17179574.360000]   IO window: 00001400-000014ff
[17179574.360000]   IO window: 00001c00-00001cff
[17179574.360000]   PREFETCH window: 14000000-15ffffff
[17179574.360000]   MEM window: 16000000-17ffffff
[17179574.360000] PCI: Bridge: 0000:00:1e.0
[17179574.360000]   IO window: 3000-3fff
[17179574.360000]   MEM window: d0200000-d02fffff
[17179574.360000]   PREFETCH window: f0000000-f00fffff
[17179574.360000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.360000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179574.360000] PCI: setting IRQ 10 as level-triggered
[17179574.360000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179574.360000] PCI: Setting latency timer of device 0000:02:05.0 to 64
[17179574.364000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179574.364000] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179574.364000] PCI: Setting latency timer of device 0000:02:05.1 to 64
[17179574.364000] NET: Registered protocol family 2
[17179574.400000] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[17179574.400000] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.400000] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[17179574.400000] TCP: Hash tables configured (established 4096 bind 2048)
[17179574.400000] TCP reno registered
[17179574.400000] Simple Boot Flag at 0x36 set to 0x1
[17179574.400000] audit: initializing netlink socket (disabled)
[17179574.400000] audit(1165363707.400:1): initialized
[17179574.400000] VFS: Disk quotas dquot_6.5.1
[17179574.400000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.400000] Initializing Cryptographic API
[17179574.400000] io scheduler noop registered
[17179574.400000] io scheduler anticipatory registered
[17179574.400000] io scheduler deadline registered
[17179574.400000] io scheduler cfq registered (default)
[17179574.400000] isapnp: Scanning for PnP cards...
[17179574.752000] isapnp: No Plug & Play device found
[17179574.804000] Real Time Clock Driver v1.12ac
[17179574.804000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.804000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.804000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.804000] mice: PS/2 mouse device common for all mice
[17179574.804000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.808000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.808000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.808000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[17179574.812000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.812000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.812000] EISA: Probing bus 0 at eisa.0
[17179574.812000] Cannot allocate resource for EISA slot 1
[17179574.812000] Cannot allocate resource for EISA slot 2
[17179574.812000] Cannot allocate resource for EISA slot 3
[17179574.812000] EISA: Detected 0 cards.
[17179574.812000] TCP bic registered
[17179574.812000] NET: Registered protocol family 1
[17179574.812000] NET: Registered protocol family 8
[17179574.812000] NET: Registered protocol family 20
[17179574.812000] Using IPI No-Shortcut mode
[17179574.812000] ACPI: (supports S0 S3 S4 S5)
[17179574.812000] Freeing unused kernel memory: 308k freed
[17179574.852000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179576.012000] Capability LSM initialized
[17179576.068000] ACPI: Transitioning device [FAN] to D3
[17179576.068000] ACPI: Transitioning device [FAN] to D3
[17179576.068000] ACPI: Fan [FAN] (off)
[17179576.076000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179576.088000] ACPI: Thermal Zone [THRM] (38 C)
[17179576.756000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.756000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.760000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[17179576.760000] PCI: setting IRQ 5 as level-triggered
[17179576.760000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179576.760000] ICH3M: chipset revision 1
[17179576.760000] ICH3M: not 100% native mode: will probe irqs later
[17179576.760000]     ide0: BM-DMA at 0x1820-0x1827, BIOS settings: hda:DMA, hdb:pio
[17179576.760000]     ide1: BM-DMA at 0x1828-0x182f, BIOS settings: hdc:pio, hdd:pio
[17179576.760000] Probing IDE interface ide0...
[17179577.048000] hda: TOSHIBA MK2018GAP, ATA DISK drive
[17179577.720000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.088000] Probing IDE interface ide1...
[17179578.488000] hdc: QSI DVD-ROM SDR-081, ATAPI CD/DVD-ROM drive
[17179579.160000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.188000] hda: max request size: 128KiB
[17179579.188000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179579.188000] Uniform CD-ROM driver Revision: 3.20
[17179579.188000] hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(100)
[17179579.188000] hda: cache flushes supported
[17179579.188000]  hda: hda1 hda2 < hda5 >
[17179579.748000] usbcore: registered new driver usbfs
[17179579.752000] usbcore: registered new driver hub
[17179579.752000] USB Universal Host Controller Interface driver v3.0
[17179579.752000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179579.752000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.752000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.752000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.752000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001800
[17179579.756000] usb usb1: configuration #1 chosen from 1 choice
[17179579.756000] hub 1-0:1.0: USB hub found
[17179579.756000] hub 1-0:1.0: 2 ports detected
[17179579.944000] Attempting manual resume
[17179580.024000] kjournald starting.  Commit interval 5 seconds
[17179580.024000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.472000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.540000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.656000] input: PC Speaker as /class/input/input1
[17179595.680000] hw_random hardware driver 1.0.0 loaded
[17179596.300000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9b48b1, caps: 0x88479b/0x0
[17179596.300000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179596.340000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179596.744000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179596.744000] Yenta: CardBus bridge found at 0000:02:05.0 [103c:001a]
[17179596.744000] Yenta: Enabling burst memory read transactions
[17179596.744000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179596.744000] Yenta: Routing CardBus interrupts to PCI
[17179596.744000] Yenta TI: socket 0000:02:05.0, mfunc 0x012c1272, devctl 0x66
[17179596.976000] Yenta: ISA IRQ mask 0x0898, PCI irq 10
[17179596.976000] Socket status: 30000006
[17179596.976000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179596.976000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179596.976000] cs: IO port probe 0x3000-0x3fff: clean.
[17179596.976000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179596.976000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf00fffff
[17179597.024000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.028000] agpgart: Detected an Intel 830M Chipset.
[17179597.044000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179597.184000] ACPI: PCI Interrupt 0000:02:05.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179597.184000] Yenta: CardBus bridge found at 0000:02:05.1 [103c:001a]
[17179597.184000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179597.184000] Yenta: Routing CardBus interrupts to PCI
[17179597.184000] Yenta TI: socket 0000:02:05.1, mfunc 0x012c1272, devctl 0x66
[17179597.240000] parport: PnPBIOS parport detected.
[17179597.240000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179597.480000] Yenta: ISA IRQ mask 0x0818, PCI irq 10
[17179597.480000] Socket status: 30000006
[17179597.480000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179597.480000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179597.480000] cs: IO port probe 0x3000-0x3fff: clean.
[17179597.480000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179597.480000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf00fffff
[17179597.664000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179597.664000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179597.668000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179597.668000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179597.688000] e100: eth0: e100_probe: addr 0xd0200000, irq 10, MAC addr 00:C0:9F:05:EA:4F
[17179597.772000] Floppy drive(s): fd0 is 1.44M
[17179597.788000] FDC 0 is a National Semiconductor PC87306
[17179597.792000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[17179597.792000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179597.792000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179597.792000] A Prism2.5 PCI device found, phymem:0xf0018000, irq:10, mem:0xc88f0000
[17179598.744000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179598.744000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179598.816000] ts: Compaq touchscreen protocol output
[17179598.820000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17179599.180000] ieee80211_crypt: registered algorithm 'NULL'
[17179599.344000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179599.696000] PCI: Enabling device 0000:02:03.0 (0000 -> 0001)
[17179599.696000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[17179599.812000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179599.816000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179599.816000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.816000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.816000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.836000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[17179599.836000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179599.836000] cs: IO port probe 0x820-0x8ff: clean.
[17179599.836000] cs: IO port probe 0xc00-0xcf7: clean.
[17179599.836000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.936000] NET: Registered protocol family 17
[17179601.568000] input: PS/2 Generic Mouse as /class/input/input3
[17179602.464000] lp0: using parport0 (interrupt-driven).
[17179602.512000] Adding 369452k swap on /dev/disk/by-uuid/bcb144ab-7261-4b5c-a59b-8af91b8d0f2a.  Priority:-1 extents:1 across:369452k
[17179602.596000] EXT3 FS on hda1, internal journal
[17179604.684000] ACPI: AC Adapter [ACAD] (on-line)
[17179604.772000] ACPI: Battery Slot [BAT1] (battery present)
[17179604.772000] ACPI: Battery Slot [BAT2] (battery absent)
[17179604.808000] ACPI: Power Button (FF) [PWRF]
[17179604.808000] ACPI: Lid Switch [LID]
[17179604.808000] ACPI: Sleep Button (CM) [SLP]
[17179604.888000] ACPI: ACPI Dock Station Driver
[17179605.040000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179605.040000] ibm_acpi: http://ibm-acpi.sf.net/
[17179605.040000] ACPI Exception (evxface-0545): AE_BAD_PARAMETER, Removing notify handler [20060707]
[17179605.092000] pcc_acpi: loading...
[17179605.292000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179605.700000] cpufreq: change failed with new_state 2 and result 0
[17179605.700000] cpufreq: change failed with new_state 2 and result 0
[17179607.240000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179609.580000] [drm] Initialized drm 1.0.1 20051102
[17179609.676000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179609.680000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179611.208000] mtrr: 0xd8000000,0x8000000 overlaps existing 0xd8000000,0x1000000
[17179611.208000] mtrr: 0xd8000000,0x8000000 overlaps existing 0xd8000000,0x1000000
[17179611.208000] mtrr: 0xd8000000,0x8000000 overlaps existing 0xd8000000,0x1000000
[17179611.208000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179611.208000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179611.208000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179611.312000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179611.312000] apm: overridden by ACPI.
[17179611.528000] [drm] Setting GART location based on new memory map
[17179611.528000] [drm] writeback test succeeded in 1 usecs
[17179627.316000] Bluetooth: Core ver 2.8
[17179627.316000] NET: Registered protocol family 31
[17179627.316000] Bluetooth: HCI device and connection manager initialized
[17179627.316000] Bluetooth: HCI socket layer initialized
[17179627.424000] Bluetooth: L2CAP ver 2.8
[17179627.424000] Bluetooth: L2CAP socket layer initialized
[17179629.284000] Bluetooth: RFCOMM socket layer initialized
[17179629.284000] Bluetooth: RFCOMM TTY layer initialized
[17179629.284000] Bluetooth: RFCOMM ver 1.7
[17179700.916000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179701.384000] ISO 9660 Extensions: RRIP_1991A
[17179702.916000] VFS: busy inodes on changed media.
[17179703.080000] VFS: busy inodes on changed media.
[17179706.756000] VFS: busy inodes on changed media.
[17179708.352000] VFS: busy inodes on changed media.
[17179708.500000] VFS: busy inodes on changed media.
[17179708.760000] VFS: busy inodes on changed media.
[17179708.764000] VFS: busy inodes on changed media.
[17179718.804000] VFS: busy inodes on changed media.
[17179735.024000] VFS: busy inodes on changed media.
[17179735.024000] VFS: busy inodes on changed media.
[17179746.328000] VFS: busy inodes on changed media.
[17179809.192000] e100: eth1: e100_watchdog: link down
[17179811.192000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17179813.192000] e100: eth1: e100_watchdog: link down
[17182880.588000] VFS: busy inodes on changed media.
[17190932.668000] VFS: busy inodes on changed media.
[17190932.668000] VFS: busy inodes on changed media.
[17190932.808000] VFS: busy inodes on changed media.
[17190932.988000] VFS: busy inodes on changed media.
[17190932.988000] VFS: busy inodes on changed media.
[17190942.828000] VFS: busy inodes on changed media.
[17190965.192000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[17190987.032000] NET: Registered protocol family 10
[17190987.032000] lo: Disabled Privacy Extensions
[17190987.032000] IPv6 over IPv4 tunneling driver
[17190997.036000] eth1: no IPv6 routers present
[17192430.144000] VFS: busy inodes on changed media.
[17192430.144000] VFS: busy inodes on changed media.
[17192438.896000] VFS: busy inodes on changed media.
[17192476.992000] VFS: busy inodes on changed media.
[17192478.992000] VFS: busy inodes on changed media.
[17192489.016000] VFS: busy inodes on changed media.
root@kabuntop:~# **iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

root@kabuntop:~# **ifconfig**
eth1      Link encap:Ethernet  HWaddr 00:C0:9F:05:EA:4F
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe05:ea4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2532636 (2.4 MiB)  TX bytes:546837 (534.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@kabuntop:~#

```

---

### Post by ingo on 2006-12-06
Well, it appears to have found your eth0. Are the settings correct?

[17179597.688000] e100: eth0: e100_probe: addr 0xd0200000, irq 10, MAC addr 00:C0:9F:05:EA:4F

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

