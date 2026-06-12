---
title: "madwifi drivers"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by clutch| on 2009-09-01
Is there an easy way to view what drivers my wireless card is using?  

The short version of my problem is that I was attempting to switch over to madwifi as opposed to whatever the default wireless driver that Ubuntu 9.04 uses is.  I *think* I did everything right.  Thing is, I rebooted immediately afterward, and it wouldn't boot up at all.  Booting it in recovery mode brought it back (after 20 minutes of fiddling with things I don't understand and selecting options at random from the menu - I have no idea what I'm doing), except it wouldn't detect my wireless card (D-Link DWL-630 with Atheros chipset) at all.  Another reboot, and then it all worked again.  I just want to know if I was successfull in switching over the drivers or if it just reverted to the old ones because of something I did.

Again, sorry for n00bness, but I'm learning.  The upside is that I'm learning on my old extra laptop with nothing on it, so it doesn't bother me too much when I break it and nothing will run anymore.  Which reminds of another problem I'm having, but I'll put that in another thread for organization's sake.

Sorry, guess that was the long version.

SHORT SHORT VERSION: Is there a simple, n00b friendly way to check and see what wireless drivers my comp is using?

---

### Post by nothingspecial on 2009-09-02
run ```
lsmod
```

If you see ath_pci you are using madwifi, if you see ath5k you are using the one ubuntu supplied.

---

### Post by clutch| on 2009-09-08
I see both.  0_0

clutch@clutch-laptop:~$ lsmod
Module                  Size  Used by
aes_i586               15744  2 
aes_generic            35880  1 aes_i586
binfmt_misc            16776  1 
i915                   67844  2 
drm                    96424  3 i915
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
ath_pci                99224  0 
wlan                  210544  1 ath_pci
ath_hal               198864  1 ath_pci
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  1 ath5k
joydev                 18496  0 
cfg80211               38288  2 ath5k,mac80211
pcmcia                 44748  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
pcspkr                 10496  0 
serio_raw              13444  0 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 40212  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
video                  25360  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
output                 11008  1 video
e100                   41740  0 
mii                    13312  1 e100
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
clutch@clutch-laptop:~$

---

### Post by nothingspecial on 2009-09-09
It appears you have both drivers loaded. This can cause you problems. You ought to blacklist one of them.

If you need help doing that post back.

---

