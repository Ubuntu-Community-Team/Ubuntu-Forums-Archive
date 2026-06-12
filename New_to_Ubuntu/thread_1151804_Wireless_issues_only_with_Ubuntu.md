---
title: "Wireless issues only with Ubuntu"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by Aell on 2009-05-07
Lately I've been having a few issues with my wireless connection and it's only on my Ubuntu laptop. My family laptop, which has Windows, has been working fine.

Sometimes the connection will be great and then it will randomly disconnect me or take minutes for things to load. It's now just my internet browser; things like Pidgin and MUDs are slow, too.

Then today when I turned my laptop on there was no connection at all, and apparently the wireless driver that I downloaded, from MadWifi, isn't on the laptop anymore. I didn't uninstall it and it was there last night.

Any help would be appreciated.

---

### Post by RetchingRabbit on 2009-05-07
Post the output of the following commands:

```
lspci | grep -i net
```

and 

```
lsmod
```

---

### Post by Aell on 2009-05-07
```
grant@Moralitas:~$ lspci | grep -i net
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

```
grant@Moralitas:~$ lsmod
Module                  Size  Used by
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
snd_timer              29704  2 snd_pcm,snd_seq
psmouse                61972  0 
videodev               41600  1 uvcvideo
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  25360  0 
serio_raw              13316  0 
v4l1_compat            21764  2 uvcvideo,videodev
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
output                 11008  1 video
ath_pci                99224  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
r8169                  40836  0 
mii                    13312  1 r8169
usb_storage            82880  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

---

