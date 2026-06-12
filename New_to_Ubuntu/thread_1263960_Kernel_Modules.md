---
title: "Kernel Modules"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-09-11
Trying to lighten my minimal ubuntu install as much as possible. I know how to find modules with lsmod. and how to blacklist them. I'm just completely unaware of which modules I need and which ones I don't and google is not helping.

---

### Post by Liolikas on 2009-09-11
Maybe just try to solve this in funny way just:
sudo modprobe -r module_name
And check what happens. If nothing bad then blacklist it. :D

---

### Post by LunaticHiatus on 2009-09-11
and if something does happen?

---

### Post by Bachstelze on 2009-09-11
> **LunaticHiatus said:**
> and if something does happen?

At worst, you will have to reboot.

---

### Post by NoaHall on 2009-09-11
Post the output on here ;)

---

### Post by cak3 on 2009-09-11
the reboot, and don't blacklist that one.

---

### Post by LunaticHiatus on 2009-09-11
i915                   67844  2 
drm                    96424  3 i915
input_polldev          11912  0 
lp                     17156  0 
parport                42220  1 lp
snd_hda_intel         434100  0 
arc4                    9856  2 
snd_pcm_oss            46336  0 
ecb                    10752  2 
snd_mixer_oss          22656  1 snd_pcm_oss
joydev                 18496  0 
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
ath9k                 280760  0 
snd_rawmidi            29696  1 snd_seq_midi
uvcvideo               63368  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
compat_ioctl32          9344  1 uvcvideo
mac80211              217592  1 ath9k
videodev               41600  1 uvcvideo
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0 
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
usb_storage            99648  0 
pcspkr                 10496  0 
serio_raw              13444  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               38288  1 mac80211
atl1e                  40212  0 
led_class              12036  1 ath9k
video                  25360  0 
snd                    62756  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                 11008  1 video
soundcore              15200  1 snd
intel_agp              34108  1 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
eeepc_laptop           18452  0 
agpgart                42696  3 drm,intel_agp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

Its a minimal install

---

### Post by Whiffle on 2009-09-11
Learned this one the other day...

lspci -k

---

### Post by LunaticHiatus on 2009-09-11
problem with the sudo modprobe -r module_name
Since I still don't know what Im stopping, It might turn out I needed that mod later. For example, I saw one called "usb_storage" while I could do sudo modprobe -r usb_storage. Im pretty sure I will need that later at some point. While others whose name I couldn't guess at did nothing when I turned it off

---

### Post by Liolikas on 2009-09-11
You can modprobe it again in place or reboot and boot modprobe everything back to default but what is still not in blacklist.

In other words:
```

sudo modprobe -r usb_storage
sudo modprobe usb_storage

```
Those commands opposite and if you enter like here no result at all. But in middle you can get info what you want.

---

### Post by LunaticHiatus on 2009-09-11
> **Liolikas said:**
> You can modprobe it again in place or reboot and boot modprobe everything back to default but what is still not in blacklist.

In other words:
```

sudo modprobe -r usb_storage
sudo modprobe usb_storage

```
Those commands opposite and if you enter like here no result at all. But in middle you can get info what you want.

yeah, that would save a lot of time. Still, I would need to have pretty much everything I would ever intend to use running all at the same time just to make sure I wouldn't have any conflicts.

---

### Post by Liolikas on 2009-09-11
Actually it is difficult... I remember I spend 1 hour trying to find out what module I need for my custom compiled kernel for my laptop wireless. Of course it was working for ages and I only wanted 5 seconds faster boot. :D

From my exp. the best way to find everything is just grab Linux source code from kernel.org and you see lots of documentation in it and in folders with drivers and more info even code files have comments and more info ... you can use find etc.

---

### Post by LunaticHiatus on 2009-09-11
you would think someone would document this somewhere...

---

### Post by Whiffle on 2009-09-11
So are you trying to figure out which module does what?

---

### Post by LunaticHiatus on 2009-09-11
pretty much

---

### Post by Whiffle on 2009-09-11
"lspci -k"   lists hardware, and what module belongs to it, and you can use "modinfo" to get detailed information about individual modules.

---

### Post by Liolikas on 2009-09-11
> **Whiffle said:**
> "lspci -k"   lists hardware, and what module belongs to it, and you can use "modinfo" to get detailed information about individual modules.

Wow Thanks. ;)

---

