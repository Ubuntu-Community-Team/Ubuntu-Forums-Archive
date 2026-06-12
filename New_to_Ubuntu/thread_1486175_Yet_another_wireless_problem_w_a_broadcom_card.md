---
title: "Yet another wireless problem w/ a broadcom card"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by rldavis on 2010-05-17
Okay, I've Googled around for three days and navigated a lot of confusing how-tos before writing here, but I can't figure out any solution to what is apparently a common problem. I installed Ubuntu 10 on a used, 2 year old Dell Inspiron e1405 I came across previously bricked by viruses and Win Vista. Everything works pretty nicely now except for the fact that I have a Broadcom BCM 4311 wireless card. I have no clue how to get it to work.

As of now, I have freshly reinstalled Ubuntu after all my failed attempts, and downloaded the Broadcom STA wireless driver. It says it is active and currently in use, but the applet says wireless is disabled. This is after a reboot.

Help please? Bear in mind please that while I have some experience with Ubuntu, it isn't much.

Thanks in advance.

---

### Post by lkraemer on 2010-05-17
You must have not searched for a HOWTO:

[http://ubuntuforums.org/showthread.php?t=1470146](http://ubuntuforums.org/showthread.php?t=1470146)

Try this, you may have to disable STA by blacklisting it as 10.04
defaults to the B43 Driver as shown by:
```

lsmod

```
Post your output!

lk

---

### Post by cariboo on 2010-05-17
Early on in Lucid testing I had the same problem, the b43 driver was installed by default. The way around it is to blacklist the driver. It should get blacklisted when you install the wl driver. Open nautilus (Places->Home Folder) and navigate to File System->etc->modprobe.d, and check if you have a file called blacklist-bcm43.conf, it supposed to be auto-generated.

---

### Post by rldavis on 2010-05-17
Hmm, I didn't find THAT how-to...

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
b44                    25542  0 
snd_hda_codec_idt      51914  1 
ssb                    37336  1 b44
mii                     4381  1 b44
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
lib80211_crypt_tkip     7596  0 
joydev                  8708  0 
wl                   1959598  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
drm_kms_helper         29297  1 i915
sdhci_pci               5470  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
lib80211                5046  2 lib80211_crypt_tkip,wl
sdhci                  15462  1 sdhci_pci
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               2864  1 sdhci
dell_wmi                1793  0 
intel_agp              24177  2 i915
lp                      7028  0 
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394


```Actually, it gave me a choice of two drivers to install, STA and b43. I chose STA.

And cariboo, I do have that file.

---

### Post by familyman101 on 2010-09-09
So wireless works now on that E1405?

---

