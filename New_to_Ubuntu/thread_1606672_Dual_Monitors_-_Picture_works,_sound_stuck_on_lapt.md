---
title: "Dual Monitors - Picture works, sound stuck on laptop"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by scratchysaurus on 2010-10-26
I'm running 10.10 with a NVIDIA card and the default sound card. I've downloaded and installed the Nvidia program, put it on Twinview and the picture works fine, however the sound keeps coming out of my laptop's speakers. I've gone into sound settings and there is only one device, and changing the options away from Analog Stereo just results in me getting nothing. Any ideas how to make the sound come out of my computer?

---

### Post by papibe on 2010-10-26
Not all nvidia's card can pass the audio through it. Also, it would need a HMDI connection. Which card do you have? How are you connecting to the other sound-capable monitor (probably a TV right)?

Regards.

---

### Post by scratchysaurus on 2010-10-26
It's a GeForce 9600M GS card, using HDMI - Before using Ubuntu I was making the connection successfully with Win 7

---

### Post by papibe on 2010-10-26
Could you post the result of this 2 commands:
```
$ aplay -l
```
and
```
$ aplay -L
```

Regards.

---

### Post by scratchysaurus on 2010-10-26
```
andrew@andrew-Aspire-6930G:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Sorry - I should maybe say, it's not currently hooked up to the TV
```
andrew@andrew-Aspire-6930G:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, NVIDIA HDMI
    HDMI Audio Output

```

---

### Post by papibe on 2010-10-26
It's looks you're all set. Connect your extra monitor. Go to System -> Preferences -> Sound. Go to the hardware and select your audio card (I think it should be just one). Go to the below part of the window and in the profile field select *HDMI* (HDMI Audio or NVIDIA HDMI).

Test several sounds files.

Good Luck!

---

