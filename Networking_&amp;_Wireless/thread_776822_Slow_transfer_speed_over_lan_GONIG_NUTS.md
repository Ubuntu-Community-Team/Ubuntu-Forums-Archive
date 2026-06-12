---
title: "Slow transfer speed over lan GONIG NUTS"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by YogiPaolo on 2008-05-01
Well, I'm embarrassed. It's a Yogipaolo problem and not a network problem. At least I learned a lot. The problem had to to with my lack of understanding the notation..... You may laugh at me accordingly, then look at this link...

[http://linux.omnipotent.net/article.php?article_id=11991](http://linux.omnipotent.net/article.php?article_id=11991)

Ok, 

I've scoured this forum and the internet for two solid weeks trying to solve this problem and so far, nothing has worked. I will spare you some of the details and just cut to the important parts.

No matter what I do, I cannot achieve more than 11.4mbps over my lan, and this , only if I'm lucky. Most of the time the speed is 10mbps.

I have a 16 port d-link switch that is 10/100 and i'm using cat5e cables that I made myself. Before someone flags this as the problem, I've swapped my cables for "store bought" cables and still, the same problem.

The problem exists with the onboard nvidia cards as well as the 3com tornados.

Here are the details of the cards I'm using right now:
Dserv1
```
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:01:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:70:d6:3b:8b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.11 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

```

LoDN1
```
*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 8
       bus info: pci@0000:04:08.0
       logical name: eth1
       version: 78
       serial: 00:0a:5e:42:f3:32
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=3c59x duplex=full ip=192.168.0.12 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s

```

Here is the result of ethtool with forced speed 100 and autoneg off
```
sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: off
	Current message level: 0x00000001 (1)
	Link detected: yes

```

Here is the result of lsmod for Dserv2:

```

Module                  Size  Used by
reiserfs              238720  1 
nfsd                  228464  13 
lockd                  67720  2 nfsd
nfs_acl                 4608  1 nfsd
auth_rpcgss            43424  1 nfsd
sunrpc                185756  9 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                6016  1 nfsd
ppdev                  10372  0 
ipv6                  272804  16 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
loop                   19076  0 
af_packet              23684  2 
snd_intel8x0           35356  0 
snd_ac97_codec        100772  1 snd_intel8x0
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
button                  9232  0 
i2c_nforce2             7680  0 
ac97_bus                3072  1 snd_ac97_codec
snd_rawmidi            25632  1 snd_mpu401_uart
snd_seq_device          9612  1 snd_rawmidi
nvidia_agp              9500  1 
agpgart                34760  1 nvidia_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport_pc             36644  1 
parport                37704  3 ppdev,lp,parport_pc
i2c_core               24832  1 i2c_nforce2
evdev                  12928  0 
snd_pcm                78596  2 snd_intel8x0,snd_ac97_codec
snd_timer              24836  1 snd_pcm
snd_page_alloc         11528  2 snd_intel8x0,snd_pcm
snd                    56868  8 snd_intel8x0,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore               8800  1 snd
analog                 13600  0 
gameport               16008  1 analog
pcspkr                  4224  0 
ext3                  136584  5 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
ata_generic             8324  0 
sg                     36496  0 
sd_mod                 30720  13 
sata_nv                27656  2 
pata_amd               14084  3 
8139too                27776  0 
floppy                 59332  0 
pata_acpi               8320  0 
sata_via               12548  2 
8139cp                 25088  0 
3c59x                  46248  0 
mii                     6400  3 8139too,8139cp,3c59x
libata                159344  5 ata_generic,sata_nv,pata_amd,pata_acpi,sata_via
scsi_mod              151180  4 sr_mod,sg,sd_mod,libata
ehci_hcd               38412  0 
ohci_hcd               25604  0 
usbcore               146028  3 ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37000  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

Here is the kernel version for Dserv2:

```

uname -a
Linux Dserv1 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

```

Here is the lsmod for LoDN1:
```

Module                  Size  Used by
nfsd                  282024  17 
auth_rpcgss            53280  1 nfsd
exportfs                7040  1 nfsd
nfs                   291576  4 
lockd                  76080  3 nfsd,nfs
nfs_acl                 5248  2 nfsd,nfs
sunrpc                213896  21 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
ipv6                  311720  16 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  0 
cpufreq_stats           8416  0 
freq_table              6464  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       3200  0 
cpufreq_conservative    10632  0 
sbs                    17808  0 
dock                   12960  0 
container               6656  0 
sbshc                   8960  1 sbs
video                  23444  0 
output                  5632  1 video
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
loop                   21508  0 
joydev                 15488  0 
nvidia               8858052  48 
snd_hda_intel         440408  4 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
serio_raw               9092  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                46236  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 10912  0 
soundcore              10400  1 snd
evdev                  14976  4 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
i2c_nforce2             8704  0 
i2c_core               28544  2 nvidia,i2c_nforce2
pcspkr                  4992  0 
ext3                  149264  2 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  5 
usbhid                 35168  0 
hid                    44992  1 usbhid
pata_amd               16772  1 
sata_nv                31624  2 
pata_acpi               9856  0 
floppy                 69096  0 
3c59x                  51764  0 
ata_generic             9988  0 
mii                     7552  1 3c59x
libata                176304  4 pata_amd,sata_nv,pata_acpi,ata_generic
ehci_hcd               41996  0 
forcedeth              55564  0 
ohci_hcd               27524  0 
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
usbcore               169904  4 usbhid,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  1 thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```

Here is the kernel info for LoDN1:
```

Linux LoDN1 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```


So far, i've tried to force speed using ethtool and mii-tool, disabling ipv6 (then re-enabling it because that's an urban myth), exchanging multiple nics, changing drivers and a number of other things I can't remember. I repeat: nothing f#*$@( works!

Please help. I really should be getting 10mbps , it just ain't right....

Thanks

---

### Post by YogiPaolo on 2008-05-02
Ok, so I'll respond to my own thread with more info.

When I use ethtool to change autonegotiation to off and the speed to 100, I can only reach speeds of 1mbps.

the driver for Dserv1 is: 8139too
the driver for LoDN1 is: forcedeth

I've moved past the angry stage and into curiosity. What could be causing this problem?

Is it just a measurement problem? I've used netperf as well as the network speed applets to confirm that I'm only getting 10 to 11mpbs speed.

Weird....

---

