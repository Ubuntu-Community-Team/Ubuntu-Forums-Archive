---
title: "n00b trying to get his VX-3000 webcam to work in 9.10"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by risephoenixrise on 2009-11-19
Can someone walk me through getting Karmic to work my VX-3000 webcam?

I installed the latest kernel, but it's still displaying that green screen.

---

### Post by zeroseven0183 on 2009-11-19
Did you install Cheese already?

---

### Post by ukripper on 2009-11-19
> **risephoenixrise said:**
> Can someone walk me through getting Karmic to work my VX-3000 webcam?

I installed the latest kernel, but it's still displaying that green screen.

can you plug your cam in and post output of the following  from terminal:
```
lsusb
```

```
lsmod
```

---

### Post by risephoenixrise on 2009-11-19
> **zeroseven0183 said:**
> Did you install Cheese already?

Yes.  It just shows a green screen.

---

### Post by risephoenixrise on 2009-11-19
> **ukripper said:**
> can you plug your cam in and post output of the following  from terminal:
```
lsusb
``````
lsmod
```


Here is what it reads:

alliesdaddy@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

alliesdaddy@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         102976  1 
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
arc4                    2144  2 
ecb                     3296  2 
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_usb_lib            19648  1 snd_usb_audio
iptable_filter          3872  0 
joydev                 13088  0 
ip_tables              21200  1 iptable_filter
snd_seq_oss            33440  0 
ath9k                 278176  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_hwdep               9352  2 snd_hda_codec,snd_usb_audio
gspca_sonixj           24160  0 
gspca_main             26816  1 gspca_sonixj
x_tables               25832  1 ip_tables
snd_timer              26992  2 snd_pcm,snd_seq
mac80211              210104  1 ath9k
ath                    10304  1 ath9k
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               43360  1 gspca_main
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
snd                    77096  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_hwdep,snd_timer,snd_seq_device
sdhci_pci               8928  0 
psmouse                57124  0 
jmb38x_ms              11300  0 
cfg80211              109144  3 ath9k,mac80211,ath
soundcore               9088  1 snd
sdhci                  20484  1 sdhci_pci
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
serio_raw               6596  0 
memstick               12528  1 jmb38x_ms
led_class               5256  2 ath9k,sdhci
lp                     11908  0 
parport                40528  2 ppdev,lp
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
r8169                  38884  0 
mii                     6368  1 r8169
i915                  246984  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video

---

### Post by ukripper on 2009-11-20
> videodev 43360 1 gspca_main
v4l1_compat 16804 1 videodev
v4l2_compat_ioctl32 13344 1 videodev

Your driver modules seems to be loaded fine.

Canyou run cheese in terminal and post any error/output here.

---

### Post by risephoenixrise on 2009-11-20
cheese is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alliesdaddy@ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffd9
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 2 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 1 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 6 more bits
libv4lconvert: Error decompressing JPEG: fill_nbits error: need 3 more bits

---

### Post by ukripper on 2009-11-20
I found a thread which can help you with your webcam on 9.10 [http://ubuntuforums.org/showthread.php?t=885795&page=12](http://ubuntuforums.org/showthread.php?t=885795&page=12)

---

### Post by Muskegman on 2009-11-20
I have a VX 3000 webcam and i gave up trying to get it to work months ago.
Your best bet is to go out and buy a Logitech webcam , that will work right out of the box with ubuntu.

---

