---
title: "Can't enable surround sound"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by curmudgbuntu on 2010-09-14
I'm trying out Ubuntu Desktop 10.04 on a ASUS M4A89GTD PRO/USB3 motherboard and can't get surround sound.
I've an analog 4.0 speaker system; front speakers work but rear don't.  They work in other OS.

In the System > Preferences > Sound > Hardware tab
the Internal Audio device profile choices are (only!):
 Analog Stero Duplex (selected)
 Analog Stero Output
 Analog Stero Input
 off

Running alsamixer (F6, F5 view all) I see the internal sound card has only three things:
Master, PCM & Capture

Shouldn't I see more hardware profile choices and alsamixer 'things'?

I've edited /etc/pulse/daemon.conf for this line: 
default-sample-channels = 4
This made no change.

```
motherboard: ASUS M4A89GTD PRO/USB3 (AMD 890 GX chipset)

speaker-test -Dplug:surround40 -c4 -l1 -twav
front left and front right are there, but rear left and rear right are missing

uname -a
Linux       2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

lspci
...
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
...
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe3f8000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe5e8000 irq 19

cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa"
ii  alsa-base             1.0.22.1+dfsg-0ubuntu3
ii  alsa-utils            1.0.22-0ubuntu5
ii  bluez-alsa            4.60-0ubuntu8  
ii  gstreamer0.10-alsa    0.10.28-1  


head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 892

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
```

---

### Post by curmudgbuntu on 2010-09-15
:rolleyes: Alright, I finally stumbled into the ALSA upgrade script here:
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

I ran the 1.0.23-2 upgrade and now have hardware profiles like one would expect.
And the speaker test has that sultry voice in all corners.

Here's some things that look different now:
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC892

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
```Can anyone offer warnings or advice with this solution?

---

### Post by mastablasta on 2010-09-15
> **curmudgbuntu said:**
> Can anyone offer warnings or advice with this solution?
 
 
basically as i understand previous drivers recognised the card as "generic" while now with the upgrade they recognise it propperly.
 
so you should be fine. had a similar problem which was even wierder because my sound didn't play at all after install but played OK on the LiveCD.
 
Surround sound had an issue (stopped working, was working but the mix wasn't...) working on my card and i just use normal analog stereo.

---

### Post by curmudgbuntu on 2010-09-22
After every kernel patch I need to re-run the alsa install script.
Aside from that all the hardware profile settings are kept and it seems to work fine.

---

### Post by SlugSlug on 2010-09-22
I fix mine with 

apt-get remove pulseaudio
apt-get install alsa

sound is spot on then

---

