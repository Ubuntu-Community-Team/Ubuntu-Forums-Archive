---
title: "How to disable hardware or peripherals?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-01-18
I want to disable floppy drive b/c it's of no use for me and its service light is continuously blinking. So required help......

---

### Post by Bachstelze on 2009-01-18
Most likely it will be as simple as unloading the kernel module that takes care of it. please paste the output of

```
lsmod
```

---

### Post by eshant_engineer on 2009-01-18
[B]this was the o/p
[/B]
Module                  Size  Used by
ipv6                  263972  14 
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
vboxnetflt             93832  0 
vboxdrv               120488  1 vboxnetflt
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  2 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
snd_hda_intel         381488  5 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
evdev                  17696  6 
pcspkr                 10624  0 
psmouse                45200  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
snd                    63268  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_vendor_support    11652  1 iTCO_wdt
parport_pc             39204  1 
soundcore              15328  1 snd
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
sd_mod                 42264  3 
cdrom                  43168  1 sr_mod
crc_t10dif              9984  1 sd_mod
sg                     39732  2 
pata_acpi              12160  0 
ata_piix               24580  4 
ata_generic            12932  0 
libata                177312  3 pata_acpi,ata_piix,ata_generic
ehci_hcd               43276  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
e100                   41356  0 
mii                    13440  1 e100
dock                   16656  1 libata
uhci_hcd               30736  0 
usbcore               148848  3 ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5

---

### Post by txcrackers on 2009-01-18
This is what I would personally characterize as a "dumb suggestion" ...

What about turning off the computer, opening it up, and simply disconnecting the cables going to the drive?

---

### Post by diablo75 on 2009-01-18
The best way to do this is through your BIOS.  Disconnecting the drive without disabling it in BIOS might produce an error message on some PCs at boot, requiring you to hit a key to tell it to proceed with the rest of POST and finally boot.

---

### Post by Bachstelze on 2009-01-18
> **txcrackers said:**
> What about turning off the computer, opening it up, and simply disconnecting the cables going to the drive?

Oh yeah, that is sooooo smart...

FYI, not everyone is comfortable with opening up his computer and fiddling in it. May I remind you this is **Absolute Beginner** Talk?

---

### Post by eshant_engineer on 2009-01-20
I found and used device manager in Add/Remove, but could not understand that what to do and where to do?

---

### Post by eshant_engineer on 2009-01-21
bump

---

