---
title: "No sound using OSS 4.0 + ATI IXP AC97"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by hoptimusPrime on 2010-03-09
hello

i have no sound output from my speakers on my laptop.  i get sound output from the headphone jack but it is quiet.

as far as i know the driver is installed fine.  i tried alsa mixer with no luck, and now i am using open sound system (oss)


**ossmix** tells me that

Known controls are:
vol [<leftvol>:<rightvol>] (currently 75:75)
vol.rec ON|OFF (currently OFF)
pcm [<leftvol>:<rightvol>] (currently 75:75)
speaker <monovol> (currently 0)
line [<leftvol>:<rightvol>] (currently 32:32)

is there a way to turn speaker<monovol> up?

or else maybe it's because i have conflicting drivers installed, when i installed oss it gave me a message saying "failed to dasable coflicting sound drivers.  reboot and try running soundon again.  also check that you have not compiled sound support statistically into the kernel."

no idea what this means and i dont know how to run "soundon".

if i type [B]ossinfo

[/B]Version info: OSS 4.2 (b 2002/200911060735) (0x00040100) TRIAL
Platform: Linux/i686 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 (braden3-laptop)

Number of audio devices:    2
Number of audio engines:    7
Number of MIDI devices:        0
Number of mixer devices:    1


Device objects
 0: osscore0 OSS core services
 1: oss_atiaudio0 ATI IXP400 interrupts=31079 (70546)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: AC97 Mixer (ALC655) (Mixer 0 of device object 1)

Audio devices
ATI IXP400                        /dev/oss/oss_atiaudio0/pcm0  (device index 0)
ATI IXP400 (SPDIF out)            /dev/oss/oss_atiaudio0/spdout  (device index 1)

Nodes
  /dev/dsp -> /dev/oss/oss_atiaudio0/pcm0
  /dev/dsp_in -> /dev/oss/oss_atiaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_atiaudio0/pcm0
  /dev/dsp_ac3 -> /dev/oss/oss_atiaudio0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_atiaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_atiaudio0/pcm0


can somebody please help me get my speakers to work?

---

### Post by hoptimusPrime on 2010-03-10
Bump : )

---

