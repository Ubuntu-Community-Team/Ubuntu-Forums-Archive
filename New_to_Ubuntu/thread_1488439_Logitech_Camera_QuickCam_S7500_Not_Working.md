---
title: "Logitech Camera QuickCam S7500 Not Working"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by rlogan on 2010-05-20
This camera was working fine on Jaunty out of the box and remained working after an update to Karmic. But I have now a fresh install of Lucid and all I get is a black screen when the camera turns on, it does have the white light on when enabled. 

The DVB card I have works out of the box but didn't before.

Anyway here is what I have found so far
***lsusb*** reveals

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0079:0006 DragonRise Inc. Generic USB Joystick
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
Bus 002 Device 006: ID 1b80:e395 Afatech 
Bus 002 Device 002: ID 03f0:5d11 Hewlett-Packard PhotoSmart C5200 series
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***lsmod*** shows (extract below)

usblp                  12407  0 
uvcvideo               62403  0 
softcursor              1565  1 bitblit
dvb_usb                16709  1 dvb_usb_af9015
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
dvb_core              102929  1 dvb_usb
v4l2_compat_ioctl32    12020  1 videodev

***dmesg | grep uvcvideo*** shows

[    9.786108] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a2)
[    9.800701] usbcore: registered new interface driver uvcvideo
[35592.880474] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a2)

When I run ***gstreamer-properties*** I find under the video tab the default input is using v4l2 and it also has the correct Camera (appears as UVC Camera (046d:09a2). The test reveals a black screen as in Cheese.

If anyone has anymore thoughts it would be appreciated!!!

Cheers

Richard

---

### Post by stefanadelbert on 2010-09-28
Same problem here. I have had the Logitech webcam working, but somewhere along the line it stopped working.

$lsusb
...
Bus 001 Device 002: ID 046d:09a2 Logitech, Inc. QuickCam Communicate Deluxe/S7500
...

$lsmod
snd_hda_codec_realtek   279040  1 
tuner_xc2028           20800  2 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37367  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
zl10353                 7793  2 
snd_emu10k1           148561  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hda_intel          25677  2 
gspca_sn9c20x          25686  0 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
gspca_main             25031  1 gspca_sn9c20x
dvb_usb_cxusb          55729  27 
dib7000p               18348  1 dvb_usb_cxusb
dibx000_common          3570  1 dib7000p
dvb_usb                16709  1 dvb_usb_cxusb
snd_usb_audio          92747  2 
snd_usb_lib            19193  1 snd_usb_audio
snd_hwdep               6924  4 snd_emux_synth,snd_emu10k1,snd_hda_codec,snd_usb_audio
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
dvb_core              102993  2 dib7000p,dvb_usb
dib0070                 8549  1 dvb_usb_cxusb
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  6 snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62467  0 
videodev               40518  2 gspca_main,uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11956  1 videodev
lirc_mceusb            14054  0 
lirc_dev               11302  1 lirc_mceusb
joydev                 11072  0 
nls_cp437               6351  2 
cifs                  278948  4 
ppdev                   6375  0 
snd                    71187  29 snd_hda_codec_realtek,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             29958  1 
emu10k1_gp              1964  0 
asus_atk0110           10033  0 
gameport               10966  2 emu10k1_gp
psmouse                64576  0 
serio_raw               4918  0 
nvidia              10832442  28 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_nforce2             6099  0 
soundcore               8052  1 snd
snd_page_alloc          8500  3 snd_emu10k1,snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
hid_logitech            8820  0 
ff_memless              5109  1 hid_logitech
usbhid                 41084  1 hid_logitech
hid                    83440  2 hid_logitech,usbhid
ohci1394               30260  0 
pata_amd               11962  0 
ieee1394               94771  1 ohci1394
forcedeth              55592  0 
ahci                   37870  4

$dmesg | grep uvcvideo

[   19.573731] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a2)
[   19.590431] usbcore: registered new interface driver uvcvideo

---

### Post by js31 on 2010-09-28
Hi,

I don't know if this is of any help, but -> it works if you install Jaunty, then follow the official tutorial (meanwhile offline), and after setting back to v4l1 do the online-upgrade to Karmic (ld.so.preload-manager missing in repositories, there). Just found it out [by accident]("http://ubuntuforums.org/showthread.php?t=1581854"), and of course, I wouldn't say it's a real solution. :D

Update/November 6th, 2010:
Well, actually, I just tried Jaunty-package "ld.so.preload-manager_0.3.3-3_all.deb" in Meerkat. "#sudo ld.so.preload-manager /usr/lib/libv4l/v4l1compat.so" + set in video-tab of "gstreamer-properties" v4l1. Seems ok.

---

