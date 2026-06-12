---
title: "rt61 HELP ifconfig doesn't show ra0"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by joefie on 2006-10-26
```

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7211
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 10
        I/O ports at cc00 [size=256]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

```

I installed RT61_Linux_STA_Drv1.0.4.0 and loaded rt61

```
Module                  Size  Used by
rt61                  242432  0 
rt2500                188644  0 
wlan                  207580  0 
ipv6                  272288  8 
binfmt_misc            13448  1 
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
via                    48224  0 
drm                    74644  1 via
lp                     12964  0 
af_packet              24584  6 
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_mpu401_uart        10240  1 snd_via82xx
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tsdev                   9152  0 
snd                    58372  13 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sg                     37404  0 
floppy                 63044  0 
evdev                  11392  1 
via_rhine              26116  0 
mii                     6912  1 via_rhine
serio_raw               8452  0 
psmouse                41352  0 
pcspkr                  4352  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
arc4                    3200  1 
rate_control            6784  0 
rt61pci                37632  0 
80211                 175880  2 rate_control,rt61pci
crc_itu_t               3200  1 rt61pci
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
soundcore              11232  1 snd
i2c_viapro              9876  0 
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
i2c_core               23424  2 i2c_ec,i2c_viapro
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
sd_mod                 22656  3 
generic                 5764  0 
sata_via               10500  2 
libata                 74892  1 sata_via
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```


```
# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid boeh

iface wmaster0 inet dhcp
wireless-essid boeh

auto wmaster0

auto ra0
iface ra0 inet dhcp

```

```
/etc/Wireless# find .
.
./RT61STA
./RT61STA/rt2561.bin
./RT61STA/rt2561s.bin
./RT61STA/rt2661.bin
./RT61STA/rt61sta.dat
./RT2500STA
./RT2500STA/RT2500STA.dat

```

---

