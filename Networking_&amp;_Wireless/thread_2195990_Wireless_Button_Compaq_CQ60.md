---
title: "Wireless Button Compaq CQ60"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by philipwrenn on 2013-12-27
Hi,

I have tried to follow the fixes for similar problems on this forum, but none of them seem to work.

I have a Compaq Presario CQ60.

When the machine starts, sometimes the wireless is on and sometimes it isn't. I have to keep restarting it, until it eventually starts "on". If the machine starts with the wireless "off", then no matter how many times I press the wireless button, it will never turn on.

Then, once I can get the machine to start with the wirelss "on", to make it pick up a WIFI signal, I need to press the wireless button twice. This sometimes works, and sometimes does not. I am guessing there is some kind of compatibility issue, but don't know how to fix it.


Apologies for my noobiness, and I must stress that I have tried fixes posted on this forum by other users, and they do not work for me.

---

### Post by philipwrenn on 2013-12-27
1 - ```
Compaq Presario CQ60 

```

2 -```
 Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
philip@philip-laptop:~$ 
```


3 - ```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:73:df:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5251 (5.2 KB)  TX bytes:5251 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:df:68:82  
          inet addr:192.168.43.139  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fedf:6882/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26764838 (26.7 MB)  TX bytes:4757295 (4.7 MB)


```

4 - ```
lsmod
Module                  Size  Used by
aes_i586                7268  3 
aes_generic            26863  1 aes_i586
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_conexant    22705  1 
binfmt_misc             6523  1 
ppdev                   5259  0 
snd_hda_intel          22069  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_hda_codec          74297  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_hwdep               5412  1 snd_hda_codec
vgastate                8961  1 vga16fb
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
nouveau               467048  2 
snd_seq_oss            26722  0 
joydev                  8740  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
ttm                    49847  1 nouveau
drm_kms_helper         29329  1 nouveau
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm                   163779  4 nouveau,ttm,drm_kms_helper
agpgart                31724  2 ttm,drm
snd_seq                47295  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
i2c_algo_bit            5028  1 nouveau
ath5k                 121632  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205434  1 ath5k
ath                     7611  1 ath5k
uvcvideo               57438  0 
lp                      7060  0 
shpchp                 28835  0 
snd                    54244  14 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126528  3 ath5k,mac80211,ath
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  1 ath5k
i2c_nforce2             5199  0 
video                  17375  0 
psmouse                63677  0 
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
output                  1871  1 video
parport                32635  2 ppdev,lp
usb_storage            40033  0 
forcedeth              49556  0 
ahci                   32680  4 
pata_amd                8766  0 

```

5 - ```
 [    0.084005] ACPI: EC: Look up EC in DSDT
[    0.085412] ACPI: BIOS _OSI(Linux) query ignored
[    0.096142] ACPI: Interpreter enabled
[    0.096142] ACPI: (supports S0 S3 S4 S5)
[    0.096142] ACPI: Using IOAPIC for interrupt routing
[    0.118012] ACPI: EC: GPE = 0x2a, I/O: command/status = 0x66, data = 0x62
[    0.118246] ACPI: No dock devices found.
[    0.118488] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.118839] pci 0000:00:01.0: reg 10 io port: [0x1a00-0x1aff]
[    0.118896] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.118912] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.118918] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.118954] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.118961] pci 0000:00:01.1: PME# disabled
[    0.118996] pci 0000:00:01.3: reg 10 32bit mmio: [0xc0080000-0xc00fffff]
[    0.119159] pci 0000:00:02.0: reg 10 32bit mmio: [0xc0006000-0xc0006fff]
[    0.119200] pci 0000:00:02.0: supports D1 D2
[    0.119202] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119206] pci 0000:00:02.0: PME# disabled
[    0.119240] pci 0000:00:02.1: reg 10 32bit mmio: [0xc0007000-0xc00070ff]
[    0.119292] pci 0000:00:02.1: supports D1 D2
[    0.119295] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119299] pci 0000:00:02.1: PME# disabled
[    0.119335] pci 0000:00:04.0: reg 10 32bit mmio: [0xc0008000-0xc0008fff]
[    0.119377] pci 0000:00:04.0: supports D1 D2
[    0.119379] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119383] pci 0000:00:04.0: PME# disabled
[    0.119416] pci 0000:00:04.1: reg 10 32bit mmio: [0xc0007400-0xc00074ff]
[    0.119468] pci 0000:00:04.1: supports D1 D2
[    0.119470] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119474] pci 0000:00:04.1: PME# disabled
[    0.119523] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.119586] pci 0000:00:07.0: reg 10 32bit mmio: [0xc0000000-0xc0003fff]
[    0.119640] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.119644] pci 0000:00:07.0: PME# disabled
[    0.119744] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.119749] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.119755] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.119760] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.119765] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.119771] pci 0000:00:09.0: reg 24 32bit mmio: [0xc0004000-0xc0005fff]
[    0.119845] pci 0000:00:0a.0: reg 10 32bit mmio: [0xc0009000-0xc0009fff]
[    0.119850] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.119856] pci 0000:00:0a.0: reg 18 32bit mmio: [0xc0007c00-0xc0007cff]
[    0.119861] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xc0007800-0xc000780f]
[    0.119905] pci 0000:00:0a.0: supports D1 D2
[    0.119907] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119912] pci 0000:00:0a.0: PME# disabled
[    0.119980] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.119984] pci 0000:00:0b.0: PME# disabled
[    0.120334] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.120342] pci 0000:00:14.0: PME# disabled
[    0.120573] pci 0000:00:08.0: transparent bridge
[    0.120606] pci 0000:02:00.0: reg 10 32bit mmio: [0xc1000000-0xc1ffffff]
[    0.120615] pci 0000:02:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.120623] pci 0000:02:00.0: reg 1c 64bit mmio pref: [0xc4000000-0xc5ffffff]
[    0.120628] pci 0000:02:00.0: reg 24 io port: [0x4000-0x407f]
[    0.120634] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.120686] pci 0000:00:0b.0: bridge io port: [0x4000-0x4fff]
[    0.120690] pci 0000:00:0b.0: bridge 32bit mmio: [0xc1000000-0xc1ffffff]
[    0.120695] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xc4000000-0xdfffffff]
[    0.120751] pci 0000:07:00.0: reg 10 64bit mmio: [0xc2000000-0xc200ffff]
[    0.120905] pci 0000:00:14.0: bridge 32bit mmio: [0xc2000000-0xc20fffff]
[    0.120941] pci_bus 0000:00: on NUMA node 0
[    0.120946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.121041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.121134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.141502] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.141670] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.141834] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.141999] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.142164] ACPI: PCI Interrupt Link [Z012] (IRQs 19 20 21 22 23) *10
[    0.142328] ACPI: PCI Interrupt Link [Z013] (IRQs 19 20 21 22 23) *0, disabled.
[    0.142496] ACPI: PCI Interrupt Link [Z014] (IRQs 19 20 21 22 23) *0, disabled.
[    0.142661] ACPI: PCI Interrupt Link [Z015] (IRQs 19 20 21 22 23) *0, disabled.
[    0.142825] ACPI: PCI Interrupt Link [LSMB] (IRQs 18) *10
[    0.142988] ACPI: PCI Interrupt Link [LUS0] (IRQs 17) *11
[    0.143151] ACPI: PCI Interrupt Link [LUS2] (IRQs 17) *7
[    0.143321] ACPI: PCI Interrupt Link [LMAC] (IRQs 19 20 21 22 23) *11
[    0.143485] ACPI: PCI Interrupt Link [LAZA] (IRQs 19 20 21 22 23) *10
[    0.143650] ACPI: PCI Interrupt Link [LGPU] (IRQs 19 20 21 22 23) *10
[    0.143813] ACPI: PCI Interrupt Link [LPID] (IRQs 19 20 21 22 23) *0, disabled.
[    0.143978] ACPI: PCI Interrupt Link [LSI0] (IRQs 19 20 21 22 23) *11
[    0.144151] ACPI: PCI Interrupt Link [LSI1] (IRQs 19 20 21 22 23) *0, disabled.
[    0.144315] ACPI: PCI Interrupt Link [Z010] (IRQs 16) *5
[    0.144484] ACPI: PCI Interrupt Link [Z011] (IRQs 16) *10
[    0.144647] ACPI: PCI Interrupt Link [LPMU] (IRQs 18) *11
[    0.144754] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.144757] vgaarb: loaded
[    0.144870] SCSI subsystem initialized
[    0.144942] libata version 3.00 loaded.
[    0.145016] usbcore: registered new interface driver usbfs
[    0.145028] usbcore: registered new interface driver hub
[    0.145053] usbcore: registered new device driver usb
[    0.145196] ACPI: WMI: Mapper loaded
[    0.145198] PCI: Using ACPI for IRQ routing
[    0.145360] NetLabel: Initializing
[    0.145362] NetLabel:  domain hash size = 128
[    0.145364] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.145377] NetLabel:  unlabeled traffic allowed by default
[    0.145406] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.145414] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.145419] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.148032] Switching to clocksource tsc
[    0.149699] AppArmor: AppArmor Filesystem Enabled
[    0.149718] pnp: PnP ACPI init
[    0.149737] ACPI: bus type pnp registered
[    0.153723] pnp 00:0b: [Firmware Bug]: [0x000000-0xffffffff] covers only part of AMD MMCONFIG area [0xe0000000-0xefffffff]; adding more reservations
[    0.153757] pnp: PnP ACPI: found 12 devices
[    0.153759] ACPI: ACPI bus type pnp unregistered
[    0.153762] PnPBIOS: Disabled by ACPI PNP
[    0.153776] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.153782] system 00:03: ioport range 0x360-0x361 has been reserved
[    0.153785] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.153789] system 00:03: iomem range 0xff800000-0xff800fff has been reserved
[    0.153795] system 00:0a: ioport range 0x1000-0x107f has been reserved
[    0.153799] system 00:0a: ioport range 0x1080-0x10ff has been reserved
[    0.153806] system 00:0a: ioport range 0x1200-0x127f has been reserved
[    0.153809] system 00:0a: ioport range 0x1280-0x12ff has been reserved
[    0.153812] system 00:0a: ioport range 0x1400-0x147f has been reserved
[    0.153815] system 00:0a: ioport range 0x1480-0x14ff has been reserved
[    0.153820] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.153824] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.153827] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.153831] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.153834] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.188553] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.188555] pci 0000:00:08.0:   IO window: disabled
[    0.188560] pci 0000:00:08.0:   MEM window: disabled
[    0.188563] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.188572] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.188575] pci 0000:00:0b.0:   IO window: 0x4000-0x4fff
[    0.188579] pci 0000:00:0b.0:   MEM window: 0xc1000000-0xc1ffffff
[    0.188583] pci 0000:00:0b.0:   PREFETCH window: 0x000000c4000000-0x000000dfffffff
[    0.188809] pci 0000:00:14.0: PCI bridge, secondary bus 0000:07
[    0.188811] pci 0000:00:14.0:   IO window: disabled
[    0.188822] pci 0000:00:14.0:   MEM window: 0xc2000000-0xc20fffff
[    0.188829] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.188850] pci 0000:00:08.0: setting latency timer to 64
[    0.188858] pci 0000:00:0b.0: setting latency timer to 64
[    0.189143] ACPI: PCI Interrupt Link [Z012] enabled at IRQ 23
[    0.189147]   alloc irq_desc for 23 on node -1
[    0.189149]   alloc kstat_irqs on node -1
[    0.189159] pci 0000:00:14.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[    0.189168] pci 0000:00:14.0: setting latency timer to 64
[    0.189174] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.189177] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.189180] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.189183] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.189186] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.189189] pci_bus 0000:02: resource 1 mem: [0xc1000000-0xc1ffffff]
[    0.189191] pci_bus 0000:02: resource 2 pref mem [0xc4000000-0xdfffffff]
[    0.189195] pci_bus 0000:07: resource 1 mem: [0xc2000000-0xc20fffff]
[    0.189233] NET: Registered protocol family 2
[    0.189321] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.189641] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.190317] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.190630] TCP: Hash tables configured (established 131072 bind 65536)
[    0.190633] TCP reno registered
[    0.190717] NET: Registered protocol family 1
[    0.191110] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    0.191114]   alloc irq_desc for 17 on node -1
[    0.191116]   alloc kstat_irqs on node -1
[    0.191127] pci 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    0.243947] pci 0000:00:02.0: PCI INT A disabled
[    0.244215] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 17
[    0.244218] pci 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17
[    0.244232] pci 0000:00:02.1: PCI INT B disabled
[    0.244493] ACPI: PCI Interrupt Link [Z010] enabled at IRQ 16
[    0.244496]   alloc irq_desc for 16 on node -1
[    0.244497]   alloc kstat_irqs on node -1
[    0.244505] pci 0000:00:04.0: PCI INT A -> Link[Z010] -> GSI 16 (level, low) -> IRQ 16
[    0.299812] pci 0000:00:04.0: PCI INT A disabled
[    0.300077] ACPI: PCI Interrupt Link [Z011] enabled at IRQ 16
[    0.300080] pci 0000:00:04.1: PCI INT B -> Link[Z011] -> GSI 16 (level, low) -> IRQ 16
[    0.300093] pci 0000:00:04.1: PCI INT B disabled
[    0.300221] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.300345] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.300481] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.300625] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    0.300770] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.300846] pci 0000:02:00.0: Boot video device
[    0.300920] Simple Boot Flag at 0x38 set to 0x1
[    0.301036] cpufreq-nforce2: No nForce2 chipset.
[    0.301061] Scanning for low memory corruption every 60 seconds
[    0.301173] audit: initializing netlink socket (disabled)
[    0.301187] type=2000 audit(1388045349.299:1): initialized
[    0.310882] Trying to unpack rootfs image as initramfs...
[    0.323732] highmem bounce pool size: 64 pages
[    0.323739] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.325129] VFS: Disk quotas dquot_6.5.2
[    0.325190] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.325735] fuse init (API version 7.13)
[    0.325814] msgmni has been set to 1696
[    0.331792] alg: No test for stdrng (krng)
[    0.331878] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.331881] io scheduler noop registered
[    0.331883] io scheduler anticipatory registered
[    0.331885] io scheduler deadline registered
[    0.331924] io scheduler cfq registered (default)
[    0.332281]   alloc irq_desc for 24 on node -1
[    0.332283]   alloc kstat_irqs on node -1
[    0.332305] pcieport 0000:00:14.0: irq 24 for MSI/MSI-X
[    0.332327] pcieport 0000:00:14.0: setting latency timer to 64
[    0.332501] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.332522] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.333985] ACPI: AC Adapter [ADP1] (on-line)
[    0.334051] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.335698] ACPI: Lid Switch [LID0]
[    0.335752] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.335759] ACPI: Sleep Button [SLPB]
[    0.335817] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.335820] ACPI: Power Button [PWRB]
[    0.335858] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.335861] ACPI: Power Button [PWRF]
[    0.336132] processor LNXCPU:00: registered as cooling_device0
[    0.353381] thermal LNXTHERM:01: registered as thermal_zone0
[    0.353393] ACPI: Thermal Zone [TZS0] (50 C)
[    0.360115] thermal LNXTHERM:02: registered as thermal_zone1
[    0.360125] ACPI: Thermal Zone [TZS1] (50 C)
[    0.361656] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.362818] brd: module loaded
[    0.363234] loop: module loaded
[    0.363322] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.363490] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.368056] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 22
[    0.368064]   alloc irq_desc for 22 on node -1
[    0.368066]   alloc kstat_irqs on node -1
[    0.368078] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 22 (level, low) -> IRQ 22
[    0.368117] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.368130] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.368451] Fixed MDIO Bus: probed
[    0.368484] PPP generic driver version 2.4.2
[    0.368545] tun: Universal TUN/TAP device driver, 1.6
[    0.368547] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.368638] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.368655] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 17 (level, low) -> IRQ 17
[    0.368674] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.368677] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.368708] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.368738] ehci_hcd 0000:00:02.1: debug port 1
[    0.368748] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.368771] ehci_hcd 0000:00:02.1: irq 17, io mem 0xc0007000
[    0.368872] isapnp: Scanning for PnP cards...
[    0.379548] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.379697] usb usb1: configuration #1 chosen from 1 choice
[    0.379726] hub 1-0:1.0: USB hub found
[    0.379737] hub 1-0:1.0: 3 ports detected
[    0.379787] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z011] -> GSI 16 (level, low) -> IRQ 16
[    0.379808] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.379812] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.379850] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.379887] ehci_hcd 0000:00:04.1: debug port 1
[    0.379896] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.379921] ehci_hcd 0000:00:04.1: irq 16, io mem 0xc0007400
[    0.423392] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.423464] usb usb2: configuration #1 chosen from 1 choice
[    0.423486] hub 2-0:1.0: USB hub found
[    0.423493] hub 2-0:1.0: 4 ports detected
[    0.423553] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.423568] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    0.423578] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.423581] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.423611] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.423624] ohci_hcd 0000:00:02.0: irq 17, io mem 0xc0006000
[    0.513429] usb usb3: configuration #1 chosen from 1 choice
[    0.513460] hub 3-0:1.0: USB hub found
[    0.513472] hub 3-0:1.0: 3 ports detected
[    0.513530] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z010] -> GSI 16 (level, low) -> IRQ 16
[    0.513551] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.513554] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.513592] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.513609] ohci_hcd 0000:00:04.0: irq 16, io mem 0xc0008000
[    0.601391] usb usb4: configuration #1 chosen from 1 choice
[    0.601425] hub 4-0:1.0: USB hub found
[    0.601437] hub 4-0:1.0: 4 ports detected
[    0.601495] uhci_hcd: USB Universal Host Controller Interface driver
[    0.601580] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.618016] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.651788] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.651802] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.655749] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.655795] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.655818] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.655959] mice: PS/2 mouse device common for all mice
[    0.656129] rtc_cmos 00:06: RTC can wake from S4
[    0.656173] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.656233] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.656354] device-mapper: uevent: version 1.0.3
[    0.656469] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.656524] device-mapper: multipath: version 1.1.0 loaded
[    0.656527] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.659524] EISA: Probing bus 0 at eisa.0
[    0.659531] Cannot allocate resource for EISA slot 1
[    0.659537] Cannot allocate resource for EISA slot 3
[    0.659539] Cannot allocate resource for EISA slot 4
[    0.659552] EISA: Detected 0 cards.
[    0.661804] cpuidle: using governor ladder
[    0.661807] cpuidle: using governor menu
[    0.662199] TCP cubic registered
[    0.662363] NET: Registered protocol family 10
[    0.663055] NET: Registered protocol family 17
[    0.663087] powernow-k8: Found 1 AMD Sempron(tm) SI-42 processors (1 cpu cores) (version 2.20.00)
[    0.663175] powernow-k8:    0 : pstate 0 (2100 MHz)
[    0.663177] powernow-k8:    1 : pstate 1 (1050 MHz)
[    0.663362] Using IPI No-Shortcut mode
[    0.663455] PM: Resume from disk failed.
[    0.663468] registered taskstats version 1
[    0.663971]   Magic number: 9:454:170
[    0.664101] rtc_cmos 00:06: setting system clock to 2013-12-26 08:09:10 UTC (1388045350)
[    0.664104] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.664106] EDD information not available.
[    0.719715] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.727629] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.747454] Freeing initrd memory: 7819k freed
[    0.926811] isapnp: No Plug & Play device found
[    1.184296] usb 1-1: configuration #1 chosen from 1 choice
[    1.300480] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.470811] usb 2-2: configuration #1 chosen from 1 choice
[   10.456253] ACPI: Battery Slot [BAT0] (battery present)
[   10.456267] Freeing unused kernel memory: 664k freed
[   10.456715] Write protecting the kernel text: 4708k
[   10.456745] Write protecting the kernel read-only data: 1848k
[   10.475818] udev: starting version 151
[   10.695588] pata_amd 0000:00:06.0: version 0.4.1
[   10.695639] pata_amd 0000:00:06.0: setting latency timer to 64
[   10.701999] scsi0 : pata_amd
[   10.710192] scsi1 : pata_amd
[   10.710307] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[   10.710310] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[   10.710421] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[   10.710766] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[   10.710771]   alloc irq_desc for 21 on node -1
[   10.710774]   alloc kstat_irqs on node -1
[   10.710785] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[   10.710791] forcedeth 0000:00:0a.0: setting latency timer to 64
[   10.711662] Initializing USB Mass Storage driver...
[   10.711757] scsi2 : SCSI emulation for USB Mass Storage devices
[   10.711879] usbcore: registered new interface driver usb-storage
[   10.711881] USB Mass Storage support registered.
[   10.711955] usb-storage: device found at 2
[   10.711957] usb-storage: waiting for device to settle before scanning
[   10.864113] ata2: port disabled. ignoring.
[   11.229414] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:16:73:df:a3
[   11.229419] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt lnktim msi desc-v3
[   11.229442] ahci 0000:00:09.0: version 3.0
[   11.229458] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 22 (level, low) -> IRQ 22
[   11.229504]   alloc irq_desc for 25 on node -1
[   11.229506]   alloc kstat_irqs on node -1
[   11.229516] ahci 0000:00:09.0: irq 25 for MSI/MSI-X
[   11.229568] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl IDE mode
[   11.229572] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part boh 
[   11.229577] ahci 0000:00:09.0: setting latency timer to 64
[   11.230247] scsi3 : ahci
[   11.230362] scsi4 : ahci
[   11.230455] ata3: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004100 irq 25
[   11.230458] ata4: SATA max UDMA/133 abar m8192@0xc0004000 port 0xc0004180 irq 25
[   11.712236] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   11.712251] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   11.713503] ata4.00: ATA-8: Hitachi HTS543225L9A300, FBEOC40F, max UDMA/100
[   11.713506] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   11.714802] ata4.00: configured for UDMA/100
[   11.732743] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L633M, 0200, max UDMA/100
[   11.751377] ata3.00: configured for UDMA/100
[   11.755766] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633M  0200 PQ: 0 ANSI: 5
[   11.770603] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   11.770607] Uniform CD-ROM driver Revision: 3.20
[   11.770714] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   11.770776] sr 3:0:0:0: Attached scsi generic sg0 type 5
[   11.771037] scsi 4:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[   11.771144] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   11.771313] sd 4:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[   11.771357] sd 4:0:0:0: [sda] Write Protect is off
[   11.771360] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   11.771383] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   11.771500]  sda: sda1 sda2 < sda5 >
[   11.816230] sd 4:0:0:0: [sda] Attached SCSI disk
[   12.141018] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.708817] usb-storage: device scan complete
[   15.711295] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   15.711716] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   15.715401] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   26.065978] Adding 5275640k swap on /dev/sda5.  Priority:-1 extents:1 across:5275640k 
[   26.092894] udev: starting version 151
[   26.672207] type=1505 audit(1388045376.507:2):  operation="profile_load" pid=556 name="/sbin/dhclient3"
[   26.672498] type=1505 audit(1388045376.507:3):  operation="profile_load" pid=556 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.672664] type=1505 audit(1388045376.507:4):  operation="profile_load" pid=556 name="/usr/lib/connman/scripts/dhclient-script"
[   26.678339] type=1505 audit(1388045376.511:5):  operation="profile_replace" pid=564 name="/sbin/dhclient3"
[   26.678640] type=1505 audit(1388045376.511:6):  operation="profile_replace" pid=564 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.678812] type=1505 audit(1388045376.511:7):  operation="profile_replace" pid=564 name="/usr/lib/connman/scripts/dhclient-script"
[   26.833145] Linux video capture interface: v2.00
[   27.025482] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   27.025504] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   27.077013] acpi device:11: registered as cooling_device1
[   27.077158] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input6
[   27.077215] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.209413] cfg80211: Calling CRDA to update world regulatory domain
[   27.223456] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.270139] cfg80211: World regulatory domain updated:
[   27.270143]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.270147]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.270151]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.270154]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   27.270156]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.270159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   27.291268] lp: driver loaded but no devices found
[   27.316406] uvcvideo: Found UVC 1.00 device CNF7047 (04f2:b091)
[   27.332992] input: CNF7047 as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input7
[   27.333148] usbcore: registered new interface driver uvcvideo
[   27.333906] USB Video Class driver (v0.1.0)
[   27.560993] ath5k 0000:07:00.0: PCI INT A -> Link[Z012] -> GSI 23 (level, low) -> IRQ 23
[   27.561006] ath5k 0000:07:00.0: setting latency timer to 64
[   27.561047] ath5k 0000:07:00.0: registered as 'phy0'
[   28.067856] ath: EEPROM regdomain: 0x67
[   28.067860] ath: EEPROM indicates we should expect a direct regpair map
[   28.067865] ath: Country alpha2 being used: 00
[   28.067867] ath: Regpair used: 0x67
[   28.196658] type=1505 audit(1388045378.031:8):  operation="profile_load" pid=718 name="/usr/share/gdm/guest-session/Xsession"
[   28.200247] type=1505 audit(1388045378.035:9):  operation="profile_replace" pid=719 name="/sbin/dhclient3"
[   28.200550] type=1505 audit(1388045378.035:10):  operation="profile_replace" pid=719 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   28.200720] type=1505 audit(1388045378.035:11):  operation="profile_replace" pid=719 name="/usr/lib/connman/scripts/dhclient-script"
[   28.245526] Linux agpgart interface v0.103
[   28.365893] [drm] Initialized drm 1.1.0 20060810
[   28.372667] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000/0x20000
[   28.438443] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   28.670524] phy0: Selected rate control algorithm 'minstrel'
[   28.671231] Registered led device: ath5k-phy0::rx
[   28.671250] Registered led device: ath5k-phy0::tx
[   28.671253] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   28.851309] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 20
[   28.851319]   alloc irq_desc for 20 on node -1
[   28.851322]   alloc kstat_irqs on node -1
[   28.851334] nouveau 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 20 (level, low) -> IRQ 20
[   28.851339] nouveau 0000:02:00.0: setting latency timer to 64
[   28.853691] [drm] nouveau 0000:02:00.0: failed to evaluate _DSM: 5
[   28.853997] [drm] nouveau 0000:02:00.0: Detected an NV50 generation card (0x0aa280a2)
[   28.854910] [drm] nouveau 0000:02:00.0: Attempting to load BIOS image from PRAMIN
[   28.917378] [drm] nouveau 0000:02:00.0: ... appears to be valid
[   28.917383] [drm] nouveau 0000:02:00.0: BIT BIOS found
[   28.917386] [drm] nouveau 0000:02:00.0: Bios version 62.77.2f.00
[   28.917390] [drm] nouveau 0000:02:00.0: TMDS table revision 2.0 not currently supported
[   28.917394] [drm] nouveau 0000:02:00.0: Found Display Configuration Block version 4.0
[   28.917398] [drm] nouveau 0000:02:00.0: DCB connector table: VHER 0x40 5 16 4
[   28.917402] [drm] nouveau 0000:02:00.0:   0: 0x00000040: type 0x40 idx 0 tag 0xff
[   28.917405] [drm] nouveau 0000:02:00.0:   1: 0x00000100: type 0x00 idx 1 tag 0xff
[   28.917408] [drm] nouveau 0000:02:00.0:   2: 0x00001261: type 0x61 idx 2 tag 0x07
[   28.917412] [drm] nouveau 0000:02:00.0: Raw DCB entry 0: 01000323 00010034
[   28.917416] [drm] nouveau 0000:02:00.0: Raw DCB entry 1: 02011300 0000001e
[   28.917418] [drm] nouveau 0000:02:00.0: Raw DCB entry 2: 02022332 00020010
[   28.917421] [drm] nouveau 0000:02:00.0: Raw DCB entry 3: 0000000e 00000000
[   28.929425] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 0 at offset 0xD5C5
[   29.020378] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 1 at offset 0xD824
[   29.020383] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 2 at offset 0xD826
[   29.020390] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 3 at offset 0xD90B
[   29.020402] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table 4 at offset 0xDA5A
[   29.020405] [drm] nouveau 0000:02:00.0: Parsing VBIOS init table at offset 0xDABF
[   29.044551] [drm] nouveau 0000:02:00.0: 0xDABF: Condition still not met after 20ms, skipping following opcodes
[   29.044563] [drm] nouveau 0000:02:00.0: 0xC1D2: parsing output script 0
[   29.044567] [drm] nouveau 0000:02:00.0: 0xC38E: parsing output script 0
[   29.151431] [TTM] Zone  kernel: Available graphics memory: 438630 kiB.
[   29.151434] [TTM] Zone highmem: Available graphics memory: 900874 kiB.
[   29.151448] [drm] nouveau 0000:02:00.0: 256 MiB VRAM
[   29.820830] [drm] nouveau 0000:02:00.0: 512 MiB GART (aperture)
[   29.831904]   alloc irq_desc for 26 on node -1
[   29.831908]   alloc kstat_irqs on node -1
[   29.831920] forcedeth 0000:00:0a.0: irq 26 for MSI/MSI-X
[   29.832010] eth0: no link during initialization.
[   29.832978] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.838661] [drm] nouveau 0000:02:00.0: Allocating FIFO number 1
[   29.961876] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc: initialised FIFO 1
[   29.972505] [drm] nouveau 0000:02:00.0: Detected a LVDS output
[   29.972512] [drm] nouveau 0000:02:00.0: Detected a DAC output
[   29.972515] [drm] nouveau 0000:02:00.0: Detected a TMDS output
[   29.972520] [drm] nouveau 0000:02:00.0: Detected a LVDS connector
[   30.076084] [drm] nouveau 0000:02:00.0: Detected a VGA connector
[   30.076379] [drm] nouveau 0000:02:00.0: Detected a DVI-D connector
[   31.200792] [drm] nouveau 0000:02:00.0: allocated 1366x768 fb: 0x40250000, bo f3003a00
[   31.200962] fb0: nouveaufb frame buffer device
[   31.200964] registered panic notifier
[   31.200972] [drm] Initialized nouveau 0.0.15 20090420 for 0000:02:00.0 on minor 0
[   31.283257] vga16fb: initializing
[   31.283262] vga16fb: mapped to 0xc00a0000
[   31.283269] vga16fb: not registering due to another framebuffer present
[   31.328594] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.539831] [drm] nouveau 0000:02:00.0: 0xC1D6: parsing output script 1
[   31.540194] [drm] nouveau 0000:02:00.0: 0xC069: parsing clock script 0
[   31.540341] Console: switching to colour frame buffer device 170x48
[   31.559510] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[   31.559517]   alloc irq_desc for 19 on node -1
[   31.559520]   alloc kstat_irqs on node -1
[   31.559532] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 19 (level, low) -> IRQ 19
[   31.559536] hda_intel: Disable MSI for Nvidia chipset
[   31.559590] HDA Intel 0000:00:07.0: setting latency timer to 64
[   31.593693] ppdev: user-space parallel port driver
[   31.816992] [drm] nouveau 0000:02:00.0: 0xC1CD: parsing clock script 1
[   32.493084] [drm] nouveau 0000:02:00.0: Allocating FIFO number 2
[   32.634886] [drm] nouveau 0000:02:00.0: nouveau_channel_alloc: initialised FIFO 2
[   32.772156] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   32.772251] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10
[   32.772317] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input11
[  239.834747] wlan0: deauthenticating from 00:eb:2d:96:bb:74 by local choice (reason=3)
[  239.841118] wlan0: direct probe to AP 00:eb:2d:96:bb:74 (try 1)
[  239.843760] wlan0: direct probe responded
[  239.843763] wlan0: authenticate with AP 00:eb:2d:96:bb:74 (try 1)
[  239.845583] wlan0: authenticated
[  239.845601] wlan0: associate with AP 00:eb:2d:96:bb:74 (try 1)
[  239.847854] wlan0: RX AssocResp from 00:eb:2d:96:bb:74 (capab=0x431 status=0 aid=1)
[  239.847856] wlan0: associated
[  239.848720] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  240.062388] padlock: VIA PadLock not detected.
[  250.596016] wlan0: no IPv6 routers present

```

6 - ```
~$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:73:df:a3
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:df:68:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.43.139 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

```

7 - ```
 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:EB:2D:96:BB:74
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Xperia E_bfc3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008e862e2c
                    Extra: Last beacon: 956ms ago
                    IE: Unknown: 000D58706572696120455F62666333
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C0001FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


```

8 - ```
 lsb_release -d
Description:    Ubuntu 10.04.4 LTS


```

9 - ```
 uname -mr
2.6.32-54-generic i686


```

10 - ```
 sudo service networking restart
restart: Unknown instance: 

```

---

### Post by wildmanne39 on 2013-12-27
I recommend upgrading to 12.04 or above because 10.04 is no longer supported and you can not even receive security updates, after you upgrade if you still have issues with wifi then post back.
Thanks

---

