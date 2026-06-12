---
title: "Integrated Ethernet not working on ASUS M3A board (64-Bit)"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by _axiom_ on 2008-07-28
Just bought a new computer and am trying to set it up with Hardy.  It detects the network card, but can't reach any outside hosts.

The usual command I use for this seems to have no effect (ifconfig eth0 up)

Below is output from lspci, lshw, and lsmod.  What else should I be trying?  Anyone else have luck with this board?
```

ubuntu@ubuntu:~$ lspci | grep net
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:1e:8c:68:23:ad
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.0.7 duplex=full firmware=N/A latency=0 link=yes module=atl1 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
ubuntu@ubuntu:~$ ping google.com
ping: unknown host google.com


ubuntu@ubuntu:~$ lsmod 
Module                  Size  Used by
ipv6                  311848  14 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
ac                      8328  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
snd_hda_intel         440408  2 
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_ca0106             41728  2 
snd_ac97_codec        123224  1 snd_ca0106
snd_seq_midi           10688  0 
snd_pcm_oss            47648  0 
snd_rawmidi            29856  2 snd_ca0106,snd_seq_midi
snd_mixer_oss          20224  1 snd_pcm_oss
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_pcm                92168  4 snd_hda_intel,snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
atl1                   40460  0 
mii                     7552  1 atl1
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              11148  0 
snd                    70856  21 snd_hda_intel,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
ac97_bus                3840  1 snd_ac97_codec
button                 10912  0 
shpchp                 38172  0 
i2c_core               28544  1 i2c_piix4
snd_page_alloc         13200  3 snd_hda_intel,snd_ca0106,snd_pcm
evdev                  14976  3 
k8temp                  7680  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
pcspkr                  4992  0 
battery                16776  0 
squashfs               46352  1 
loop                   21508  2 
unionfs                87264  1 
nls_cp437               8320  1 
isofs                  39464  1 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
usbhid                 35296  0 
hid                    44992  1 usbhid
pata_atiixp            10496  0 
pata_acpi               9856  0 
ata_generic             9988  0 
sg                     41880  0 
sr_mod                 20132  1 
sd_mod                 33280  3 
cdrom                  41512  1 sr_mod
floppy                 69096  0 
atiixp                  6672  0 [permanent]
ide_core              136600  1 atiixp
ehci_hcd               41996  0 
ohci_hcd               27524  0 
usbcore               169904  4 usbhid,ehci_hcd,ohci_hcd
ahci                   33028  3 
libata                176432  4 pata_atiixp,pata_acpi,ata_generic,ahci
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
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

I have also tried modprobe atl1, and modprobe atl2, but to no avail.

Also, yes, I know there is a wireless card there, but am not using it.  I am trying to get some internet out of an RJ45 cable.

---

### Post by chili555 on 2008-07-29
There are a number of posts about the not-working *atl1* module. This one, for example: [http://ubuntuforums.org/showthread.php?t=842113](http://ubuntuforums.org/showthread.php?t=842113) and post #7 here refers to 64-bit: [http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

---

