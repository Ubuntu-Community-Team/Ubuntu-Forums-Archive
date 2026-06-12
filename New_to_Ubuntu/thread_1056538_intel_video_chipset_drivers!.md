---
title: "intel video chipset drivers??!"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by nubix on 2009-01-31
both my lspci and lsmod output

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
family@ubuntu:~$ lsmod
Module                  Size  Used by
usblp                  20480  0 
af_packet              25728  2 
binfmt_misc            16904  1 
i915                   38144  2 
drm                    86056  3 i915
sco                    18308  2 
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ipv6                  263972  14 
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
loop                   23180  0 
snd_intel8x0           37532  6 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
psmouse                45200  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13444  0 
intel_agp              33724  1 
snd                    63268  22 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42184  4 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
pcspkr                 10624  0 
evdev                  17696  6 
dcdbas                 15008  0 
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  2 
b44                    35984  0 
pata_acpi              12160  0 
libata                177312  3 ata_generic,ata_piix,pata_acpi
ssb                    40580  1 b44
mii                    13440  1 b44
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
dock                   16656  1 libata
usbcore               148848  4 usblp,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 




im assuming i still have vesa installed as my primary driver for my intel graphics card. i would like to know if there is a driver crafted specificly for my video card, and possibly explicit instructions on how to locate, and install it. =P also i was having problems with booting up into intrepid ibex for the first time and i was told that my chipset was not compatible with the current compiz version, so i disabled it and it worked! but i would like compiz on this machine, id like to here a second opinion on that, it would be great!

like always you guys are the best! and i thank you in advance!

---

### Post by mikewhatever on 2009-01-31
I don't quite understand the assumption that vesa is the primary driver. Is there any indication that it is? Is there also any indication that there is a secondary graphics driver installed? Assuming that you are on Intrepid, your graphics driver would be **xserver-xorg-video-intel** package. As for your info, it is not in the restricted repository and should be installed by default. You can verify that wit <dpkg -s xserver-xorg-video-intel>.

---

### Post by nubix on 2009-02-01
well it appears that a driver is installed for my chipset. but this box is running A little slow even after i installed extra ram.that can only help right? my experience with linux is that it tends to use system resources better than windows.

---

### Post by empty_spaces on 2009-02-01
Are you on Intrepid? Is yours an Intel X3100 graphics card?

You might want to read this other thread of mine - [http://ubuntuforums.org/showthread.php?t=1051319](http://ubuntuforums.org/showthread.php?t=1051319)

---

