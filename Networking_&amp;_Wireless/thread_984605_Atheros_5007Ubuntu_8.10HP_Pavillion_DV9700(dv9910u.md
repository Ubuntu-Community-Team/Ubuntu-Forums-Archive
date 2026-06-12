---
title: "Atheros 5007/Ubuntu 8.10/HP Pavillion DV9700(dv9910us)"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by Baufrin on 2008-11-16
I have never been able to get the wireless to work under ubuntu since 8.04. Please help. this is the information that is mentioned for submiting a ticket. Thanks for taking a look ( I am a noob in ubuntu)
1 ) Machine Brand and Model (PC/Laptop):
Code: HP Pavilion 9700 laptop (label also calls it a dv9910)


2 ) Wireless Brand, Model and Wireless Chipset:
Code: $ lspci -nn | grep 'Wireless Brand'

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

3 ) check interface:
Code:

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:68:78:82:a5  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe78:82a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10851030 (10.8 MB)  TX bytes:571411 (571.4 KB)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.1 KB)  TX bytes:4100 (4.1 KB)

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


(hint) if the Wireless interface name is wlan0 you can also use
Code:

$ iwconfig wlan0

4 ) Check for modules:
Code:

$ lsmod

Module                  Size  Used by
ipv6                  263972  10 
ndiswrapper           196380  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  2 
l2cap                  30464  16 bnep,rfcomm
af_packet              25728  2 
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
serio_raw              13444  0 
nvidia               7103300  36 
agpgart                42184  1 nvidia
pcspkr                 10624  0 
psmouse                45200  0 
k8temp                 12416  0 
uvcvideo               62728  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
i2c_core               31892  1 nvidia
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
evdev                  17696  12 
btusb                  19736  3 
bluetooth              61924  11 bnep,sco,rfcomm,l2cap,btusb
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
video                  25104  5 
ricoh_mmc              11904  0 
output                 11008  1 video
snd_hda_intel         381488  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
wmi                    14504  0 
battery                18436  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
ac                     12292  0 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
pata_amd               18692  0 
ahci                   37132  2 
ohci1394               37936  0 
forcedeth              61328  0 
ohci_hcd               31888  0 
libata                177312  4 pata_acpi,ata_generic,pata_amd,ahci
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
ehci_hcd               43276  0 
ieee1394               96324  2 sbp2,ohci1394
usbcore               148848  7 ndiswrapper,uvcvideo,btusb,usbhid,ohci_hcd,ehci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  4 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

$ lsmod | grep "wlan_module_name"

5 ) Kernel boot messages
Code:

$ dmesg

[    0.516692] PCI: 0000:00:09.0 reg 14 io port: [30e4, 30e7]
[    0.516696] PCI: 0000:00:09.0 reg 18 io port: [30e8, 30ef]
[    0.516700] PCI: 0000:00:09.0 reg 1c io port: [30e0, 30e3]
[    0.516704] PCI: 0000:00:09.0 reg 20 io port: [30d0, 30df]
[    0.516708] PCI: 0000:00:09.0 reg 24 32bit mmio: [f6484000, f6485fff]
[    0.516748] PCI: 0000:00:0a.0 reg 10 32bit mmio: [f6488000, f6488fff]
[    0.516752] PCI: 0000:00:0a.0 reg 14 io port: [30f8, 30ff]
[    0.516756] PCI: 0000:00:0a.0 reg 18 32bit mmio: [f6489c00, f6489cff]
[    0.516761] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [f6489800, f648980f]
[    0.516779] pci 0000:00:0a.0: supports D1
[    0.516780] pci 0000:00:0a.0: supports D2
[    0.516782] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516787] pci 0000:00:0a.0: PME# disabled
[    0.516816] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516819] pci 0000:00:0c.0: PME# disabled
[    0.516845] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516848] pci 0000:00:0d.0: PME# disabled
[    0.516866] PCI: 0000:00:12.0 reg 10 32bit mmio: [f5000000, f5ffffff]
[    0.516870] PCI: 0000:00:12.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.516877] PCI: 0000:00:12.0 reg 1c 64bit mmio: [f4000000, f4ffffff]
[    0.516883] PCI: 0000:00:12.0 reg 30 32bit mmio: [0, 1ffff]
[    0.516986] PCI: 0000:02:05.0 reg 10 32bit mmio: [0, 7ff]
[    0.517017] pci 0000:02:05.0: supports D1
[    0.517019] pci 0000:02:05.0: supports D2
[    0.517021] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517025] pci 0000:02:05.0: PME# disabled
[    0.517046] PCI: 0000:02:05.1 reg 10 32bit mmio: [f6100800, f61008ff]
[    0.517077] pci 0000:02:05.1: supports D1
[    0.517078] pci 0000:02:05.1: supports D2
[    0.517080] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517084] pci 0000:02:05.1: PME# disabled
[    0.517105] PCI: 0000:02:05.2 reg 10 32bit mmio: [f6100c00, f6100cff]
[    0.517136] pci 0000:02:05.2: supports D1
[    0.517137] pci 0000:02:05.2: supports D2
[    0.517140] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517144] pci 0000:02:05.2: PME# disabled
[    0.517164] PCI: 0000:02:05.3 reg 10 32bit mmio: [f6101000, f61010ff]
[    0.517195] pci 0000:02:05.3: supports D1
[    0.517197] pci 0000:02:05.3: supports D2
[    0.517199] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517203] pci 0000:02:05.3: PME# disabled
[    0.517225] PCI: 0000:02:05.4 reg 10 32bit mmio: [f6101400, f61014ff]
[    0.517256] pci 0000:02:05.4: supports D1
[    0.517258] pci 0000:02:05.4: supports D2
[    0.517260] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.517264] pci 0000:02:05.4: PME# disabled
[    0.517293] pci 0000:00:08.0: transparent bridge
[    0.517298] PCI: bridge 0000:00:08.0 32bit mmio: [f6100000, f61fffff]
[    0.517337] PCI: bridge 0000:00:0c.0 io port: [4000, 4fff]
[    0.517340] PCI: bridge 0000:00:0c.0 32bit mmio: [f2000000, f3ffffff]
[    0.517344] PCI: bridge 0000:00:0c.0 64bit mmio pref: [f0000000, f1ffffff]
[    0.517379] PCI: 0000:03:00.0 reg 10 64bit mmio: [f6000000, f600ffff]
[    0.517449] PCI: bridge 0000:00:0d.0 32bit mmio: [f6000000, f60fffff]
[    0.517459] bus 00 -> node 0
[    0.517466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.517575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.517600] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.517640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.557911] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.557911] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.557911] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.557911] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.557911] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.557911] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.557911] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.558139] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.558405] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.558671] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.558938] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.559210] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.559478] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.559745] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.560021] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.560299] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.560567] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.560838] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.561110] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.564161] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.564183] pnp: PnP ACPI init
[    0.564183] ACPI: bus type pnp registered
[    0.569276] pnp: PnP ACPI: found 12 devices
[    0.569276] ACPI: ACPI bus type pnp unregistered
[    0.569276] PnPBIOS: Disabled by ACPI PNP
[    0.569276] PCI: Using ACPI for IRQ routing
[    0.572045] NET: Registered protocol family 8
[    0.572047] NET: Registered protocol family 20
[    0.576040] NetLabel: Initializing
[    0.576040] NetLabel:  domain hash size = 128
[    0.576040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.576055] NetLabel:  unlabeled traffic allowed by default
[    0.576064] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.576069] hpet0: 3 32-bit timers, 25000000 Hz
[    0.577648] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.577651]    actual entries 65620
[    0.577797] AppArmor: AppArmor Filesystem Enabled
[    0.577825] ACPI: RTC can wake from S4
[    0.580051] Switched to high resolution mode on CPU 0
[    0.580065] Switched to high resolution mode on CPU 1
[    0.580095] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.580102] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.580106] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.580109] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.580112] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.580115] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.580118] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.580125] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.580128] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.580139] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.580143] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.580146] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.580150] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.580153] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.615468] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.615471] pci 0000:00:08.0:   IO window: disabled
[    0.615475] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.615478] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.615483] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.615486] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.615489] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.615493] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.615497] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.615499] pci 0000:00:0d.0:   IO window: disabled
[    0.615503] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.615506] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.615516] pci 0000:00:08.0: setting latency timer to 64
[    0.615521] pci 0000:00:0c.0: setting latency timer to 64
[    0.615526] pci 0000:00:0d.0: setting latency timer to 64
[    0.615530] bus: 00 index 0 io port: [0, ffff]
[    0.615532] bus: 00 index 1 mmio: [0, ffffffff]
[    0.615534] bus: 02 index 0 mmio: [0, 0]
[    0.615536] bus: 02 index 1 mmio: [f6100000, f61fffff]
[    0.615539] bus: 02 index 2 mmio: [0, 0]
[    0.615541] bus: 02 index 3 io port: [0, ffff]
[    0.615543] bus: 02 index 4 mmio: [0, ffffffff]
[    0.615545] bus: 04 index 0 io port: [4000, 4fff]
[    0.615548] bus: 04 index 1 mmio: [f2000000, f3ffffff]
[    0.615550] bus: 04 index 2 mmio: [f0000000, f1ffffff]
[    0.615553] bus: 04 index 3 mmio: [0, 0]
[    0.615555] bus: 03 index 0 mmio: [0, 0]
[    0.615557] bus: 03 index 1 mmio: [f6000000, f60fffff]
[    0.615559] bus: 03 index 2 mmio: [0, 0]
[    0.615561] bus: 03 index 3 mmio: [0, 0]
[    0.615574] NET: Registered protocol family 2
[    0.625077] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.625380] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.626181] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.626632] TCP: Hash tables configured (established 131072 bind 65536)
[    0.626636] TCP reno registered
[    0.629120] NET: Registered protocol family 1
[    0.629249] checking if image is initramfs... it is
[    1.322651] Freeing initrd memory: 7932k freed
[    1.322824] Simple Boot Flag at 0x36 set to 0x1
[    1.324095] audit: initializing netlink socket (disabled)
[    1.324111] type=2000 audit(1226798723.324:1): initialized
[    1.330205] highmem bounce pool size: 64 pages
[    1.330211] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.333130] VFS: Disk quotas dquot_6.5.1
[    1.333232] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.333364] msgmni has been set to 1726
[    1.333495] io scheduler noop registered
[    1.333497] io scheduler anticipatory registered
[    1.333500] io scheduler deadline registered
[    1.333512] io scheduler cfq registered (default)
[    1.333545] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.333705] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.333721] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.333737] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.333754] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.333769] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.333785] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.333800] pci 0000:00:12.0: Boot video device
[    1.333940] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.333965] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.333987] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.334045] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.334133] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.334159] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.334177] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.334231] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.334636] isapnp: Scanning for PnP cards...
[    1.687211] isapnp: No Plug & Play device found
[    1.730977] hpet_resources: 0xfed00000 is busy
[    1.731088] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.733837] brd: module loaded
[    1.733921] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.734064] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.762783] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.762790] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.763178] mice: PS/2 mouse device common for all mice
[    1.763330] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.763364] rtc0: alarms up to one year, y3k, hpet irqs
[    1.763502] EISA: Probing bus 0 at eisa.0
[    1.763508] Cannot allocate resource for EISA slot 1
[    1.763513] Cannot allocate resource for EISA slot 3
[    1.763516] Cannot allocate resource for EISA slot 4
[    1.763530] EISA: Detected 0 cards.
[    1.763534] cpuidle: using governor ladder
[    1.763537] cpuidle: using governor menu
[    1.764034] TCP cubic registered
[    1.764062] Using IPI No-Shortcut mode
[    1.764280] registered taskstats version 1
[    1.764421]   Magic number: 0:709:407
[    1.764577] acpi PNP0800:00: hash matches
[    1.764589] acpi ACPI0003:00: hash matches
[    1.764635] rtc_cmos 00:07: setting system clock to 2008-11-16 01:25:24 UTC (1226798724)
[    1.764638] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.764641] EDD information not available.
[    1.764953] Freeing unused kernel memory: 424k freed
[    1.765039] Write protecting the kernel text: 2576k
[    1.765080] Write protecting the kernel read-only data: 936k
[    1.784619] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.900407] fuse init (API version 7.9)
[    2.026738] ACPI: processor limited to max C-state 1
[    2.026931] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.027021] processor ACPI0007:00: registered as cooling_device0
[    2.027027] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.027245] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.027319] processor ACPI0007:01: registered as cooling_device1
[    2.027324] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.030097] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
[    2.504261] No dock devices found.
[    2.542304] usbcore: registered new interface driver usbfs
[    2.542327] usbcore: registered new interface driver hub
[    2.542397] usbcore: registered new device driver usb
[    2.545603] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    2.545616] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    2.545628] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.545631] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.545681] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.545710] ehci_hcd 0000:00:02.1: debug port 1
[    2.545715] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.545731] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    2.559461] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.559624] usb usb1: configuration #1 chosen from 1 choice
[    2.559657] hub 1-0:1.0: USB hub found
[    2.559667] hub 1-0:1.0: 7 ports detected
[    2.560227] SCSI subsystem initialized
[    2.579472] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.579614] libata version 3.00 loaded.
[    2.765893] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    2.765901] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    2.765917] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.765920] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.765947] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    2.765976] ehci_hcd 0000:00:04.1: debug port 1
[    2.765981] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    2.765989] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    2.777030] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.777219] usb usb2: configuration #1 chosen from 1 choice
[    2.777247] hub 2-0:1.0: USB hub found
[    2.777257] hub 2-0:1.0: 2 ports detected
[    8.188951] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    8.188964] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    8.188979] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    8.188982] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    8.189012] Clocksource tsc unstable (delta = 4398044243638 ns)
[    8.189031] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    8.189055] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    8.432377] usb usb3: configuration #1 chosen from 1 choice
[    8.432407] hub 3-0:1.0: USB hub found
[    8.432418] hub 3-0:1.0: 7 ports detected
[    8.616378] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    8.663985] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    8.663991] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    8.664006] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    8.664009] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    8.664039] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    8.664053] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    8.743512] usb usb4: configuration #1 chosen from 1 choice
[    8.743541] hub 4-0:1.0: USB hub found
[    8.743552] hub 4-0:1.0: 2 ports detected
[    8.871849] usb 2-2: configuration #1 chosen from 1 choice
[    8.961117] pata_amd 0000:00:06.0: version 0.3.10
[    8.961165] pata_amd 0000:00:06.0: setting latency timer to 64
[    8.961590] scsi0 : pata_amd
[    8.961981] scsi1 : pata_amd
[    8.962392] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    8.962396] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    9.053828] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    9.148076] ata1.00: ATAPI: PIONEER DVDRW  DR-KD08HB, 1K09, max MWDMA2
[    9.148090] ata1: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    9.210577] ata1.00: configured for MWDMA2
[    9.210619] ata2: port disabled. ignoring.
[    9.249308] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW  DR-KD08HB 1K09 PQ: 0 ANSI: 5
[    9.249497] ahci 0000:00:09.0: version 3.0
[    9.249918] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    9.249929] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    9.250019] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    9.250024] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    9.250027] ahci 0000:00:09.0: setting latency timer to 64
[    9.251038] scsi2 : ahci
[    9.251496] scsi3 : ahci
[    9.251952] scsi4 : ahci
[    9.253126] scsi5 : ahci
[    9.253242] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
[    9.253245] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
[    9.253248] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
[    9.253252] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
[    9.291704] usb 3-5: configuration #1 chosen from 1 choice
[    9.491949] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    9.776574] usb 4-1: configuration #1 chosen from 1 choice
[    9.804218] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.804635] ata3.00: ATA-8: TOSHIBA MK2552GSX, LV012C, max UDMA/100
[    9.804638] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    9.805128] ata3.00: configured for UDMA/100
[   10.179628] ata4: SATA link down (SStatus 0 SControl 300)
[   10.554500] ata5: SATA link down (SStatus 0 SControl 300)
[   10.930645] ata6: SATA link down (SStatus 0 SControl 300)
[   10.930754] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2552GS LV01 PQ: 0 ANSI: 5
[   10.930861] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   10.931297] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   10.931308] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[   10.931313] forcedeth 0000:00:0a.0: setting latency timer to 64
[   11.493107] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:78:82:a5
[   11.493111] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   11.494949] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[   11.495376] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   11.495389] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[   11.547123] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   11.593228] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[   11.594230] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   11.615666] Driver 'sr' needs updating - please use bus_type methods
[   11.626710] usbcore: registered new interface driver hiddev
[   11.632231] Driver 'sd' needs updating - please use bus_type methods
[   11.636694] input: Razer Razer Diamondback Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-5/3-5:1.0/input/input2
[   11.654718] input,hidraw0: USB HID v1.10 Mouse [Razer Razer Diamondback Optical Mouse] on usb-0000:00:02.0-5
[   11.654746] usbcore: registered new interface driver usbhid
[   11.654750] usbhid: v2.6:USB HID core driver
[   11.743384] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.743390] Uniform CD-ROM driver Revision: 3.20
[   11.743493] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   11.743619] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   11.743640] sd 2:0:0:0: [sda] Write Protect is off
[   11.743643] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.743679] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.743750] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   11.743767] sd 2:0:0:0: [sda] Write Protect is off
[   11.743770] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.743802] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.743806]  sda: sda1 sda2 sda3 < sda5 sda6 >
[   11.870576] sd 2:0:0:0: [sda] Attached SCSI disk
[   13.740127] PM: Starting manual resume from disk
[   13.740131] PM: Resume from partition 8:6
[   13.740133] PM: Checking hibernation image.
[   13.740268] PM: Resume from disk failed.
[   13.796622] kjournald starting.  Commit interval 5 seconds
[   13.796648] EXT3-fs: mounted filesystem with ordered data mode.
[   14.013217] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00311f0001]
[   25.267244] udevd version 124 started
[   25.853160] ACPI: AC Adapter [ACAD] (on-line)
[   25.925195] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   25.949035] ACPI: Power Button (FF) [PWRF]
[   25.949167] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   25.981060] ACPI: Sleep Button (CM) [SLPB]
[   25.981150] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   25.981610] ACPI: Lid Switch [LID]
[   25.981708] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   26.009044] ACPI: Power Button (CM) [PWRB]
[   26.329541] ACPI: Battery Slot [BAT0] (battery present)
[   26.329829] ACPI: WMI: Mapper loaded
[   26.931657] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   26.931671] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   26.931700] HDA Intel 0000:00:07.0: setting latency timer to 64
[   26.952170] ricoh-mmc: Ricoh MMC Controller disabling driver
[   26.952174] ricoh-mmc: Copyright(c) Philip Langdale
[   26.971601] acpi device:25: registered as cooling_device2
[   26.971806] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input7
[   26.975085] sdhci: Secure Digital Host Controller Interface driver
[   26.975089] sdhci: Copyright(c) Pierre Ossman
[   26.992031] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   26.994523] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   26.994539] ricoh-mmc: Controller is now disabled.
[   27.022773] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   27.023199] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   27.023211] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   27.026267] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   27.093785] Bluetooth: Core ver 2.13
[   27.094344] NET: Registered protocol family 31
[   27.094347] Bluetooth: HCI device and connection manager initialized
[   27.094351] Bluetooth: HCI socket layer initialized
[   27.138228] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   27.138335] usbcore: registered new interface driver btusb
[   27.378111] Linux video capture interface: v2.00
[   27.450762] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.455928] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.502658] uvcvideo: Found UVC 1.00 device HP Webcam (0c45:62c0)
[   27.506268] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8
[   27.525247] usbcore: registered new interface driver uvcvideo
[   27.525268] USB Video Class driver (v0.1.0)
[   27.687141] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   27.697227] Linux agpgart interface v0.103
[   27.758966] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   28.522465] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   28.522480] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   28.522487] nvidia 0000:00:12.0: setting latency timer to 64
[   28.522745] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   28.525437] usbcore: registered new interface driver ndiswrapper
[   28.532540] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   28.609564] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   29.266480] lp: driver loaded but no devices found
[   29.444744] Adding 2602488k swap on /dev/sda6.  Priority:-1 extents:1 across:2602488k
[   73.198487] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   73.198673] EXT3 FS on sda5, internal journal
[   74.252977] type=1505 audit(1226816797.167:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4798
[   74.456521] type=1505 audit(1226816797.368:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4803
[   74.456781] type=1505 audit(1226816797.368:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4803
[   74.617254] ip_tables: (C) 2000-2006 Netfilter Core Team
[   75.422192] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[   75.422838] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[   75.422843] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   75.422845] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   75.422848] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   76.175752] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   76.260037] apm: BIOS not found.
[   76.373312] ppdev: user-space parallel port driver
[   79.766222] NET: Registered protocol family 17
[   82.081519] Bluetooth: L2CAP ver 2.11
[   82.081536] Bluetooth: L2CAP socket layer initialized
[   82.100503] Bluetooth: RFCOMM socket layer initialized
[   82.100552] Bluetooth: RFCOMM TTY layer initialized
[   82.100558] Bluetooth: RFCOMM ver 1.10
[   82.148121] Bluetooth: SCO (Voice Link) ver 0.6
[   82.148141] Bluetooth: SCO socket layer initialized
[   82.216834] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   82.216856] Bluetooth: BNEP filters: protocol multicast
[   82.278172] Bridge firewalling registered
[   82.279149] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  131.326959] CPU0 attaching NULL sched-domain.
[  131.326977] CPU1 attaching NULL sched-domain.
[  131.328821] CPU0 attaching sched-domain:
[  131.328828]  domain 0: span 0-1 level CPU
[  131.328832]   groups: 0 1
[  131.328839] CPU1 attaching sched-domain:
[  131.328842]  domain 0: span 0-1 level CPU
[  131.328845]   groups: 1 0
[55620.706975] usbcore: deregistering interface driver ndiswrapper
[55620.764746] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[55620.825079] ndiswrapper (link_pe_images:603): DLL initialize failed for athw.sys
[55620.825911] ndiswrapper: driver netathw (,06/27/2008,7.6.0.239) loaded
[55620.830047] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[55620.830083] ndiswrapper 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[55620.830105] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[55620.840939] usbcore: registered new interface driver ndiswrapper
[55723.661908] NET: Registered protocol family 10
[55723.664562] lo: Disabled Privacy Extensions
[55733.764021] eth0: no IPv6 routers present

6 ) Network configuration
Code:

$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:78:82:a5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.195 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:a8:1d:c8:21:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


7 ) Scan for networks:
Code:

$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


8 ) Ubuntu Version:
Code:

$ lsb_release -d
Description:	Ubuntu 8.10



9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

$ uname -mr

2.6.27-7-generic i686

10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by acreech on 2008-11-16
Have you tried running these commands?
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

This is how I get my Atheros 5007 card working.

---

### Post by Baufrin on 2008-11-16
thanks for the reply i will try this now.
> **acreech said:**
> Have you tried running these commands?
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*

wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip

(remove the space between ftp &:, i.e. ftp://)

unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules 

```

This is how I get my Atheros 5007 card working.

---

### Post by acreech on 2008-11-16
I forgot to put on there that you need to restart the computer after running the commands.

---

### Post by Baufrin on 2008-11-17
figured that part out. BTW you post was helpful in getting me to look in the right places. another post about how to reinstall the net work manager sealed the deal and i am now happily posting from wireless WPA encrypted ubuntu. Thanks for the help. your driver worked better and then from there it was a network manager issue.
> **acreech said:**
> I forgot to put on there that you need to restart the computer after running the commands.


Up and surfing good for 2 hours wireless now i also got mp3s dvd playback with menus and Citrix metaframe client up and running.

---

### Post by acreech on 2008-11-17
I am glad that it worked for you.

---

### Post by mastermesh on 2010-05-30
any updates to this that work with the newest version of ubuntu?  I seem to be having same problem... and did what's suggested but it didn't help.  Wifi Radar still sees nothing, and the switch on the wifi slider on computer still is red/orange, not blue.

---

