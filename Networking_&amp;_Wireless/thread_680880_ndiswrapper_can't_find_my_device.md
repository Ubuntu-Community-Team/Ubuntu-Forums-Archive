---
title: "ndiswrapper can't find my device"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by Game_boy on 2008-01-28
I have an rt2500usb-based USB wireless stick (Belkin F5D7050). I have loaded the rt2500usb driver from the installation disk correctly using ndiswrapper from the Gutsy repository.

```
alex@alex-desktop:~$ ndiswrapper -l
rt2500usb : driver installed
```

As you can see, ndiswrapper cannot detect my device.

lsusb can: 

```
 002 Device 002: ID 050d:705a Belkin Components
```


I am not using an alternate driver. I have in fact deleted /lib/modules/ubuntu/wireless to prevent any built-in drivers whatsoever interfering.


```
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
container               5504  0 
button                  8976  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
battery                11012  0 
ndiswrapper           185240  0 
lp                     12580  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                1476940  22 
i2c_nforce2             7040  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
i2c_core               26112  1 i2c_nforce2
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
agpgart                35016  1 fglrx
pcspkr                  4224  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
usb_storage            73024  0 
libusual               18448  1 usb_storage
ide_cd                 32672  1 
cdrom                  37536  1 ide_cd
sata_nv                20612  3 
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
floppy                 60004  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  4 sg,sd_mod,usb_storage,libata
amd74xx                15260  0 [permanent]
ide_core              116804  3 usb_storage,ide_cd,amd74xx
r8169                  32260  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  7 ndiswrapper,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

This is my last option, as I have tried the rt2500 driver from the Gutsy repository, the built-in rt2x00 driver in a Hardy installation, compiling rt2500 from rt2x00 myself and trying to use the Gutsy built-in rt2500usb which randomly disconnects.

How can I make ndiswrapper see or use my device?

---

