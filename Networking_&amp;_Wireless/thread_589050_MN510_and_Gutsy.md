---
title: "MN510 and Gutsy"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by deepfriedarjun on 2007-10-23
Hello,
I installed Gutsy Gibson today on my desktop and got rid of Windows (finally!). However, I don't know how to connect to the internet under linux..I'm on my laptop right now.

Can someone walk me through the process, step by step?

I'm using a Microsoft MN510 USB adapter and it says the drivers (prism_2) are already installed with 7.1 Gusty Gibson, but I cannot connect to my wireless  network even though it has no password and I entered the SSID manually. It simply says "Attempting to connect to ...." but it never does, and then that too goes away. 

Can someone please help, ASAP? Thanks!

---

### Post by Lambert on 2007-10-24
> **deepfriedarjun said:**
> Hello,
I installed Gutsy Gibson today on my desktop and got rid of Windows (finally!). However, I don't know how to connect to the internet under linux..I'm on my laptop right now.

Can someone walk me through the process, step by step?

I'm using a Microsoft MN510 USB adapter and it says the drivers (prism_2) are already installed with 7.1 Gusty Gibson, but I cannot connect to my wireless  network even though it has no password and I entered the SSID manually. It simply says "Attempting to connect to ...." but it never does, and then that too goes away. 

Can someone please help, ASAP? Thanks!

Can you open a terminal and post the out of this command

```

sudo lsmod

```

There are a couple drivers for this card and it is possible two are loading and causing a conflict.

---

### Post by deepfriedarjun on 2007-10-24
> **Lambert said:**
> Can you open a terminal and post the out of this command

```

sudo lsmod

```

There are a couple drivers for this card and it is possible two are loading and causing a conflict.

I'm at school right now, but when I get home I will surely do that and let you know.

---

### Post by deepfriedarjun on 2007-10-24
> **Lambert said:**
> Can you open a terminal and post the out of this command

```

sudo lsmod

```

There are a couple drivers for this card and it is possible two are loading and causing a conflict.

```
arjun@arjunDesktop:~$ sudo lsmod
[sudo] password for arjun:
Module                  Size  Used by
ipv6                  273892  8 
af_packet              24840  0 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
button                  8976  0 
ac                      6148  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
prism2_usb             74756  0 
snd_seq_midi            9600  0 
p80211                 33036  1 prism2_usb
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
xpad                    9988  0 
usblp                  15104  0 
i2c_i810                5892  0 
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_algo_bit            7428  1 i2c_i810
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
i2c_core               26112  2 i2c_i810,i2c_algo_bit
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
floppy                 60004  0 
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
b44                    28300  0 
mii                     6528  1 b44
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  7 prism2_usb,xpad,usblp,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
arjun@arjunDesktop:~$ 
```

---

### Post by deepfriedarjun on 2007-10-25
I got it, i hadn't installed linux-wlan-ng. If you're having the same problem I had, open terminal and type:

sudo apt-get install linux-wlan-ng

and restart (hit control + alt + shift + backspace)

---

