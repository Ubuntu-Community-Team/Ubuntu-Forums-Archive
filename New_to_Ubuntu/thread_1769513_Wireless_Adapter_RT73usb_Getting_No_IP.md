---
title: "Wireless Adapter RT73usb Getting No IP"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2011-05-28
Hi,

So here is my issue at present, my USB wireless adapter is very temperamental with Linux.

The adapter is a New Zealand house brand using the rt73 chipset.

50% of the time it works without fault, whereas the other 50% of the time I have the following faults:

- Very Very Very Slow internet access, basic pages such as google take a minute or two to load.
- On a lot of occasions the adapter will connect to my wireless router but will not obtain an IP Address, instead showing 0.0.0.0

My broadband connection has speeds of 17MB Down / 1MB Up which works fantastic without fault on Windows 7.

PC Specs are:

Linux Mint 10 x64 & Ubuntu 11.04 x64

Hoping someone could shine some light as this is the only reason that I keep going back to Windows 7 at the moment, if I can sort this out I can remove Windows 7 altogether.

Some things that might help.

```

terry@ORACLE ~ $ lsmod
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
binfmt_misc             7984  1 
arc4                    1497  2 
snd_usb_audio         105727  1 
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_seq_midi            5932  0 
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
rt73usb                24308  0 
snd_hda_codec_realtek   299533  1 
rt2500usb              19651  0 
rt2x00usb              11316  2 rt73usb,rt2500usb
rt2x00lib              31575  3 rt73usb,rt2500usb,rt2x00usb
snd_hda_intel          26019  2 
nvidia              10221046  38 
led_class               3393  1 rt2x00lib
mac80211              266657  2 rt2x00usb,rt2x00lib
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
cfg80211              170293  2 rt2x00lib,mac80211
uvcvideo               62379  0 
serio_raw               4910  0 
videodev               49359  1 uvcvideo
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
usblp                  12700  0 
snd_timer              23850  2 snd_seq,snd_pcm
joydev                 11363  0 
snd                    64117  17 snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
i7core_edac            18090  0 
edac_core              46822  1 i7core_edac
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
xhci_hcd               58578  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
hid_logitech           10639  0 
ff_memless              5485  1 hid_logitech
dm_raid45              75026  0 
xor                     4709  1 dm_raid45
btrfs                 506518  0 
zlib_deflate           21866  1 btrfs
crc32c                  3007  1 
libcrc32c               1268  1 btrfs
firewire_ohci          24679  0 
usbhid                 42062  1 hid_logitech
firewire_core          54327  1 firewire_ohci
hid                    84678  2 hid_logitech,usbhid
r8169                  42222  0 
ahci                   21857  0 
crc_itu_t               1739  2 rt73usb,firewire_core
libahci                26167  1 ahci
pata_jmicron            2771  0 
mii                     5261  1 r8169

```

```

terry@ORACLE ~ $ inxi -N
Network:   Card-1 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller driver r8169
           Card-2 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller driver r8169

```

and /etc/modprobe.d/blacklist.conf

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

Cheers

---

