---
title: "Ubuntu recognizes soundcard, but no sound is coming"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-20
Hi everyone, 
 
Ubuntu recognizes soundcard etc. Everything seems to be in order but still there is no sound. 

When using```
aplay -l
``` it says [CODE] **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 [CODE]

When testing my soundcard it says (SEE ATTACHED PICTURE)

[CODE]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback. [CODE]



CAN ANYONE PLS HELP

---

### Post by Xiong Chiamiov on 2009-03-23
Done [this](http://ubuntuforums.org/showthread.php?t=205449)?

---

