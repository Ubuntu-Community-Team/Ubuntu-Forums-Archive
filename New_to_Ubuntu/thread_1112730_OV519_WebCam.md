---
title: "OV519 WebCam"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by KevinGallo on 2009-03-31
After doing some research, I've found out that I need the OV511 driver in order to make my 05a9:8519 OmniVision Technologies, Inc. OV519 WebCam work.

Downside to this seemingly easy fix is that the most recent edition of the OV511 is for 2.6.13 kernel, and I have the 2.6.27 kernel.

Is there any way to make this driver work with my kernel?

If not, is there another way to get my webcam to work. I can get a bit of an image, but it has horizontal lines, along with a completely messed up resolution, such as blue being red.

I've tried easycam2, which didn't work either.

My webcam does however, work correctly in Cheese. It seems to be a problem with Skype.

---

### Post by cariboo on 2009-04-01
I'm running Juanty, and the driver is included in the kernel. It would surprise if the driver is also included in the kernel you are using. Open an Applications-->Accessories-->Terminal and type:

```
lsmod | grep ov511
```

If the webcam is detected properly, the module should show up in the listing.

Jim

---

### Post by KevinGallo on 2009-04-01
When inputting 

lsmod | grep ov511

I get nothing, but putting in 

lsmod

gives me

```
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
rfcomm                 44432  0 
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
container              11520  0 
pci_slot               12680  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25232  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
evdev                  17696  6 
ov51x_jpeg            159224  0 
snd_ca0106             40480  3 
snd_ac97_codec        111652  1 snd_ca0106
snd_seq_dummy          10884  0 
usb_storage            82752  0 
snd_usb_audio          89728  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  5 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
gspca_ov519            23812  0 
gspca_main             29312  1 gspca_ov519
pcspkr                 10624  0 
libusual               30356  1 usb_storage
snd_seq_oss            38528  0 
usbhid                 35840  0 
snd_usb_lib            24192  1 snd_usb_audio
hid                    50560  1 usbhid
videodev               41344  2 ov51x_jpeg,gspca_main
v4l1_compat            22404  1 videodev
snd_hwdep              15236  1 snd_usb_audio
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_ca0106,snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ieee80211_crypt_tkip    17024  0 
nvidia               7103300  34 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  17 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
i2c_core               31892  1 nvidia
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16136  2 snd_ca0106,snd_pcm
wl                   1080212  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
agpgart                42184  2 nvidia,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
8139too                31616  0 
ata_piix               24580  2 
libata                178208  3 ata_generic,pata_acpi,ata_piix
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  11 ov51x_jpeg,usb_storage,snd_usb_audio,gspca_ov519,gspca_main,libusual,usbhid,snd_usb_lib,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
```

so I have the gspca OV519, but not the one you have...

---

