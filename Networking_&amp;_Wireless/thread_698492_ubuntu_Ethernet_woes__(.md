---
title: "ubuntu Ethernet woes  :("
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Dirkzen on 2008-02-16
Hey guys ^^  Complete linux noob here.  Runnin the newest version of Ubuntu,  just installed it earlier today!  I'm loving it sooo much! <3   Got it dual booting with windows xp.

   I read around the forums, an learned how to get my sound card workin perfectly, and everythings runnin smooth, except for my internet connection.  I've tried to google, an search around the forums here , but I can't quite get it.

Ubuntu boots up a bit too quickly for me to see the dmesg | grep  or anything, so I can't really tell anything from there.
My ethernet card is VIA Rhine II fast ethernet adapter

-----------------heres the output of lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---------and heres the output of lsmod
Module                  Size  Used by
ipv6                  273892  8 
via                    43904  2 
drm                    83348  3 via
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
lp                     12580  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
container               5504  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
snd_via82xx            29336  0 
usblp                  15104  0 
gameport               16776  1 snd_via82xx
snd_mpu401_uart         9600  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_ca0106             34720  1 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_via82xx_modem      16264  0 
snd_rawmidi            25728  3 snd_mpu401_uart,snd_ca0106,snd_seq_midi
snd_ac97_codec        100644  3 snd_via82xx,snd_ca0106,snd_via82xx_modem
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  5 snd_via82xx,snd_ca0106,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_viapro             10004  0 
i2c_core               26112  1 i2c_viapro
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
serio_raw               8068  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_via82xx,snd_mpu401_uart,snd_ca0106,snd_seq_oss,snd_via82xx_modem,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
shpchp                 34580  0 
via_agp                11264  1 
soundcore               8800  1 snd
ac97_bus                3200  1 snd_ac97_codec
snd_page_alloc         11400  4 snd_via82xx,snd_ca0106,snd_via82xx_modem,snd_pcm
pci_hotplug            32704  1 shpchp
agpgart                35016  2 drm,via_agp
evdev                  11136  3 
battery                11012  0 
squashfs               48132  1 
loop                   19076  2 
unionfs                77096  1 
isofs                  36412  1 
sd_mod                 30336  1 
sg                     36764  0 
sr_mod                 17828  1 
ext3                  133896  0 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
nls_iso8859_1           5120  0 
nls_cp437               6784  1 
vfat                   14080  0 
fat                    54300  1 vfat
ide_cd                 32672  0 
cdrom                  37536  2 sr_mod,ide_cd
ide_disk               18560  2 
usb_storage            73024  2 
libusual               18448  1 usb_storage
via_rhine              25992  0 
mii                     6528  1 via_rhine
ehci_hcd               36492  0 
via82cxxx              10372  0 [permanent]
ide_core              116804  4 ide_cd,ide_disk,usb_storage,via82cxxx
uhci_hcd               26640  0 
usbcore               138632  6 usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
sata_via               12548  0 
ata_generic             8452  0 
libata                125168  2 sata_via,ata_generic
scsi_mod              147084  5 sd_mod,sg,sr_mod,usb_storage,libata
ohci1394               36528  0 
ieee1394               96312  1 ohci1394
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

Any hints on how to get this darn thing to work?  :)

---

### Post by Dirkzen on 2008-02-16
Oh, sorry,  and in case this is of any importance,   i'm runnin off of the livecd version of it right now to connect an get all this  :)    Everything works perfectly right now for some reason,  but just running it normally without the cd here causes it to go into 'non internet' mode.   

Pc specs if its needed too ^^

Compaq presario
2.08 ghz
1gig of ram
30gig hd
kinda old, crappy via unichrome onboard graphics card  >.>
Dsl internet
Touchstone Telephony modem
linksys wileless-g broadband router   WRT54GS
((connects to the router first, then the modem. if thats of any importance))

---

### Post by oilchangeguy on 2008-02-16
> **Dirkzen said:**
> Oh, sorry,  and in case this is of any importance,   i'm runnin off of the livecd version of it right now to connect an get all this  :)    Everything works perfectly right now for some reason,  but just running it normally without the cd here causes it to go into 'non internet' mode.   

Pc specs if its needed too ^^

Compaq presario
2.08 ghz
1gig of ram
30gig hd
kinda old, crappy via unichrome onboard graphics card  >.>
Dsl internet
Touchstone Telephony modem
linksys wileless-g broadband router   WRT54GS

go to system, admin, networking. and highlight the nic card, properties, and uncheck roaming. select auto config.

---

### Post by Dirkzen on 2008-02-16
That worked  :)  Thank you very much.

---

