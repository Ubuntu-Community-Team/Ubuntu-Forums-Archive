---
title: "How can i get my Mic to work with Audacity?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-02-20
i'm trying to get the installed mic on an Acer AS5672 laptop. here is the output of "**Help/Audio Device Info...**"
```
==============================
Default capture device number: 0
Default playback device number: 0
==============================
Device ID: 0
Device name: OSS: /dev/dsp
Input channels: 16
Output channels: 16
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    8000
    9600
    11025
    12000
    15000
    16000
    22050
    24000
    32000
    44100
    48000
    88200
    96000
    192000
==============================
Device ID: 1
Device name: ALSA: HDA Intel: ALC883 Analog (hw:0,0)
Input channels: 2
Output channels: 2
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 2
Device name: ALSA: HDA Intel: ALC883 Analog (hw:0,4)
Input channels: 2
Output channels: 0
Low Input Latency: 0.011610
Low Output Latency: -1.000000
High Input Latency: 0.046440
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 3
Device name: ALSA: front
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 4
Device name: ALSA: surround40
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 5
Device name: ALSA: surround51
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 6
Device name: ALSA: surround71
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
    44100
    48000
    96000
    192000
==============================
Device ID: 7
Device name: ALSA: dmix
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.042667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
    48000
==============================
Selected capture device: 1 - ALSA: HDA Intel: ALC883 Analog (hw:0,0)
Selected playback device: 0 - OSS: /dev/dsp
Supported Rates:    44100
    48000
    96000
```

and this is **lspci**
```
ry@n:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

Audacity is giving me three options for my default recording device, only one won't give an error when i try to record with it selected, but i don't get any input from it. here are the recording input options:

> OSS: /dev/sdp
ALSA: HDA Intel: ALC883 Analog (hw:0,0)
ALSA: HDA Intel: ALC883 Analog (hw:0,4)

---

### Post by superprash2003 on 2009-02-20
have you tried the various options for sound capture under system->preferences->sound

---

