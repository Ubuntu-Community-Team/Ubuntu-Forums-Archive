---
title: "Audigy 4 sound not working..."
date: 2010-03-06
forum: New to Ubuntu
---

### Post by SecretFace on 2010-03-06
Been trying to figure why my sound does not work. I've been searching the forums with no luck...so now I'm asking for help. I did find this and not sure if this is what you need:
sf@sf:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sf@sf:~$

---

### Post by lidex on 2010-03-06
Right-click the alsa-info script link in my sig and "save as" into your user folder. Then run this command in a terminal ("Applications>Accessories>Terminal"):
```
sudo bash utils_alsa-info.sh
```

Post the output text here using code tags or provide the link if you upload it.

---

### Post by SecretFace on 2010-03-07
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" into your user folder. Then run this command in a terminal ("Applications>Accessories>Terminal"):
```
sudo bash utils_alsa-info.sh
```Post the output text here using code tags or provide the link if you upload it.

I did what you asked...Thank you. Sorry for double post...bottom post has the info...

---

### Post by SecretFace on 2010-03-07
I did it again and found it in my tmp folder. 

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sun Mar  7 05:44:45 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.31-20-generic-pae
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_emu10k1


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Audigy2        ]: Audigy2 - SB Audigy 4 [SB0610]
                      SB Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0x8c00, irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

01:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

01:01.0 0401: 1102:0008
    Subsystem: 1102:1021


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: snd_emu10k1
    enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
    enable_ir : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
    extin : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    extout : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
    id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
    index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
    max_buffer_size : 128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128,128
    max_synth_voices : 64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64,64
    seq_ports : 4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4,4
    subsystem : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: SigmaTel STAC9750,51

PCI Subsys Vendor: 0x0000
PCI Subsys Device: 0x0000

Flags: 0
Capabilities     : -headphone out-
DAC resolution   : 20-bit
ADC resolution   : 20-bit
3D enhancement   : SigmaTel 3D Enhancement

Current setup
Mic gain         : +0dB [+0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=1 AMAP DSA=0 SPDIF VRA
Extended status  : SPCV SPDIF=7/8
PCM front DAC    : 48000Hz
PCM ADC          : 48000Hz
SPDIF Control    : Consumer PCM Copyright Category=0x0 Generation=0 Rate=48kHz

0:00 = 6a90
0:02 = 0606
0:04 = 9f1f
0:06 = 801f
0:08 = 0000
0:0a = 801e
0:0c = 801f
0:0e = 801f
0:10 = 9f1f
0:12 = 8606
0:14 = 9f1f
0:16 = 9f1f
0:18 = 9f1f
0:1a = 0000
0:1c = 0000
0:1e = 0000
0:20 = 0000
0:22 = 0000
0:24 = 0000
0:26 = 800f
0:28 = 0605
0:2a = 0410
0:2c = bb80
0:2e = 0000
0:30 = 0000
0:32 = bb80
0:34 = 0000
0:36 = 0000
0:38 = 0000
0:3a = 2000
0:3c = 0000
0:3e = 0100
0:40 = 0000
0:42 = 0000
0:44 = 0000
0:46 = 0000
0:48 = 0000
0:4a = 0000
0:4c = 0003
0:4e = ffff
0:50 = 0000
0:52 = 0000
0:54 = 0000
0:56 = 0000
0:58 = 0000
0:5a = 0000
0:5c = 0000
0:5e = 0000
0:60 = 0000
0:62 = 0000
0:64 = 0000
0:66 = 0000
0:68 = 0000
0:6a = 0000
0:6c = 0002
0:6e = 1000
0:70 = 0000
0:72 = 0000
0:74 = 8800
0:76 = 0000
0:78 = 0000
0:7a = 0000
0:7c = 8384
0:7e = 7650
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 13 Mar  6 21:18 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 Mar  6 21:18 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 14 Mar  6 21:18 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116,  6 Mar  6 21:18 /dev/snd/midiC0D0
crw-rw----+ 1 root audio 116,  5 Mar  6 21:18 /dev/snd/midiC0D1
crw-rw----+ 1 root audio 116, 15 Mar  6 21:18 /dev/snd/midiC0D2
crw-rw----+ 1 root audio 116, 16 Mar  6 21:18 /dev/snd/midiC0D3
crw-rw----+ 1 root audio 116, 12 Mar  6 21:18 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 11 Mar  6 21:44 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 10 Mar  6 21:18 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  9 Mar  6 21:18 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116,  8 Mar  6 21:18 /dev/snd/pcmC0D2p
crw-rw----+ 1 root audio 116,  7 Mar  6 21:18 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  3 Mar  6 21:18 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Mar  6 21:18 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Mar  6 21:18 .
drwxr-xr-x 3 root root 360 Mar  6 21:18 ..
lrwxrwxrwx 1 root root  12 Mar  6 21:18 pci-0000:01:01.0 -> ../controlC0


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Audigy2]

Card hw:0 'Audigy2'/'SB Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0x8c00, irq 22'
  Mixer name    : 'SigmaTel STAC9750,51'
  Components    : 'AC97a:83847650'
  Controls      : 202
  Simple ctrls  : 37
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined cvolume cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 31
  Mono: Playback 80 [80%] [-8.00dB]
  Front Left: Capture 25 [81%] [-9.00dB] [on]
  Front Right: Capture 25 [81%] [-9.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'Bass',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'Treble',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 20 [50%]
  Front Right: 20 [50%]
Simple mixer control 'PCM',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 100
  Front Left: Capture 80 [80%] [-8.00dB]
  Front Right: Capture 80 [80%] [-8.00dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'PCM Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB] Capture 80 [80%] [-8.00dB]
Simple mixer control 'Wave',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 25 [81%] [3.00dB] [off]
  Front Right: Capture 25 [81%] [3.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Phone',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-34.50dB] [off]
  Front Right: Capture 0 [0%] [-34.50dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'AMic',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]


!!Alsactl output
!!-------------

--startcollapse--
state.Audigy2 {
    control.1 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM Front Playback Volume'
        value.0 100
        value.1 100
    }
    control.2 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM Surround Playback Volume'
        value.0 100
        value.1 100
    }
    control.3 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM Side Playback Volume'
        value.0 100
        value.1 100
    }
    control.4 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM Center Playback Volume'
        value 100
    }
    control.5 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM LFE Playback Volume'
        value 100
    }
    control.6 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Wave Playback Volume'
        value.0 80
        value.1 80
    }
    control.7 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Synth Playback Volume'
        value.0 80
        value.1 80
    }
    control.8 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'PCM Capture Volume'
        value.0 80
        value.1 80
    }
    control.9 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Synth Capture Volume'
        value.0 80
        value.1 80
    }
    control.10 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'AMic Playback Volume'
        value.0 0
        value.1 0
    }
    control.12 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Audigy CD Playback Volume'
        value.0 0
        value.1 0
    }
    control.13 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Audigy CD Capture Volume'
        value.0 0
        value.1 0
    }
    control.14 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 Optical Playback Volume'
        value.0 0
        value.1 0
    }
    control.15 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'IEC958 Optical Capture Volume'
        value.0 0
        value.1 0
    }
    control.18 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Analog Mix Playback Volume'
        value.0 0
        value.1 0
    }
    control.19 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Analog Mix Capture Volume'
        value.0 0
        value.1 0
    }
    control.20 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Aux2 Playback Volume'
        value.0 0
        value.1 0
    }
    control.21 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Aux2 Capture Volume'
        value.0 0
        value.1 0
    }
    control.22 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Front Playback Volume'
        value.0 100
        value.1 100
    }
    control.23 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Surround Playback Volume'
        value.0 100
        value.1 100
    }
    control.24 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Center Playback Volume'
        value 100
    }
    control.25 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'LFE Playback Volume'
        value 100
    }
    control.26 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Side Playback Volume'
        value.0 100
        value.1 100
    }
    control.27 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 40'
        iface MIXER
        name 'Tone Control - Bass'
        value.0 20
        value.1 20
    }
    control.28 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 40'
        iface MIXER
        name 'Tone Control - Treble'
        value.0 20
        value.1 20
    }
    control.29 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'Tone Control - Switch'
        value.0 false
        value.1 false
    }
    control.30 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 100'
        comment.dbmin -4000
        comment.dbmax 0
        iface MIXER
        name 'Master Playback Volume'
        value 80
    }
    control.31 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 2
        iface MIXER
        name 'IEC958 Optical Raw Playback Switch'
        value.0 false
        value.1 false
    }
    control.32 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 64
        iface PCM
        device 2
        name 'Captured FX8010 Outputs'
        value.0 false
        value.1 false
        value.2 false
        value.3 false
        value.4 false
        value.5 false
        value.6 false
        value.7 false
        value.8 false
        value.9 false
        value.10 false
        value.11 false
        value.12 false
        value.13 false
        value.14 false
        value.15 false
        value.16 false
        value.17 false
        value.18 false
        value.19 false
        value.20 false
        value.21 false
        value.22 false
        value.23 false
        value.24 false
        value.25 false
        value.26 false
        value.27 false
        value.28 false
        value.29 false
        value.30 false
        value.31 false
        value.32 true
        value.33 true
        value.34 true
        value.35 true
        value.36 true
        value.37 true
        value.38 true
        value.39 true
        value.40 true
        value.41 true
        value.42 true
        value.43 true
        value.44 true
        value.45 true
        value.46 true
        value.47 true
        value.48 false
        value.49 false
        value.50 false
        value.51 false
        value.52 false
        value.53 false
        value.54 false
        value.55 false
        value.56 false
        value.57 false
        value.58 false
        value.59 false
        value.60 false
        value.61 false
        value.62 false
        value.63 false
    }
    control.33 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Master Capture Switch'
        value true
    }
    control.34 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -4650
        comment.dbmax 0
        iface MIXER
        name 'Master Capture Volume'
        value.0 25
        value.1 25
    }
    control.39 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'PC Speaker Capture Switch'
        value false
    }
    control.40 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 15'
        comment.dbmin -4500
        comment.dbmax 0
        iface MIXER
        name 'PC Speaker Capture Volume'
        value 0
    }
    control.41 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Phone Capture Switch'
        value false
    }
    control.42 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Phone Capture Volume'
        value 0
    }
    control.43 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Capture Switch'
        value false
    }
    control.44 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 1
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Mic Capture Volume'
        value 0
    }
    control.45 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Mic Boost (+20dB)'
        value false
    }
    control.46 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Line Capture Switch'
        value false
    }
    control.47 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Line Capture Volume'
        value.0 0
        value.1 0
    }
    control.48 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'CD Capture Switch'
        value false
    }
    control.49 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'CD Capture Volume'
        value.0 25
        value.1 25
    }
    control.50 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Video Capture Switch'
        value false
    }
    control.51 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Video Capture Volume'
        value.0 0
        value.1 0
    }
    control.52 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Aux Capture Switch'
        value false
    }
    control.53 {
        comment.access 'read write'
        comment.type INTEGER
        comment.count 2
        comment.range '0 - 31'
        comment.dbmin -3450
        comment.dbmax 1200
        iface MIXER
        name 'Aux Capture Volume'
        value.0 0
        value.1 0
    }
    control.59 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 'pre 3D'
        comment.item.1 'post 3D'
        iface MIXER
        name 'PCM Out Path & Mute'
        value 'pre 3D'
    }
    control.61 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mix
        comment.item.1 Mic
        iface MIXER
        name 'Mono Output Select'
        value Mix
    }
    control.62 {
        comment.access 'read write'
        comment.type ENUMERATED
        comment.count 1
        comment.item.0 Mic1
        comment.item.1 Mic2
        iface MIXER
        name 'Mic Select'
        value Mic1
    }
    control.65 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'External Amplifier'
        value false
    }
    control.210 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.211 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        index 1
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.212 {
        comment.access read
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Mask'
        index 2
        value ffffffff00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
    }
    control.213 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.214 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        index 1
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.215 {
        comment.access 'read write'
        comment.type IEC958
        comment.count 1
        iface PCM
        name 'IEC958 Playback Default'
        index 2
        value '0492100200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
    }
    control.216 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Audigy Analog/Digital Output Jack'
        value false
    }
    control.217 {
        comment.access 'read write'
        comment.type BOOLEAN
        comment.count 1
        iface MIXER
        name 'Analog Capture Boost'
        value false
    }
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
binfmt_misc
ipt_REJECT
ipt_LOG
xt_limit
xt_tcpudp
xt_state
ipt_addrtype
snd_emu10k1_synth
snd_emux_synth
snd_seq_virmidi
snd_seq_midi_emul
snd_emu10k1
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_util_mem
snd_hwdep
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
joydev
soundcore
ip6table_filter
ip6_tables
nf_nat_irc
nf_conntrack_irc
nf_nat_ftp
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack_ftp
nf_conntrack
iptable_filter
ip_tables
x_tables
ppdev
nvidia
agpgart
psmouse
serio_raw
i82975x_edac
edac_core
parport_pc
asus_atk0110
lp
parport
hid_logitech
ff_memless
usbhid
floppy
ohci1394
ieee1394
sky2


!!ALSA/HDA dmesg
!!------------------



```

---

### Post by lidex on 2010-03-07
This might get ugly.
Go into synaptic "applications>system>administration>synaptic"
and search "alsa". Mark for installation any packages with alsa + firmware. Go to the "settings>repositories" menu and on the updates tab check the box for "unsupported updates" or backports. Close that and hit "reload" button. Click apply. once done open a terminal and enter this command:
```
sudo apt-get install linux-backports-modules-alsa-karmic-generic
```

Reboot.

---

### Post by lidex on 2010-03-07
This next one, if needed, I'm not sure will stick but it's worth trying.
Open terminal and enter:
```
gksudo nautilus
```
!!Be very careful in this mode!!
Navigate to /lib/modules/<your current kernel>/
Double-click the "modules.alias" file and scroll to the bottom. Now copy and paste these lines at the end:
```

alias char-major-116 snd
alias snd-card-0 snd-emu10k1

```
Save and close. Close nautilus. Reboot. 
Now you're back up. Open terminal. Command:
```
alsamixer
```

Make sure your volume levels are up and not muted.

---

### Post by SecretFace on 2010-03-07
I just want to say THANKS to "[lidex]("http://ubuntuforums.org/member.php?u=577099")"! It worked perfectly...You are Awesome! ;)

---

### Post by lidex on 2010-03-07
You're welcome. Glad we got it done in less than 36 posts ;)

---

### Post by SecretFace on 2010-03-07
> **lidex said:**
> You're welcome. Glad we got it done in less than 36 posts ;)
LOL :D! Me too. I'm pretty proficient...I learn quick. ;)

---

