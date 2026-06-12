---
title: "Poor Sound Quality/Distortion Using Headphones"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by zanknits on 2011-05-16
Hi all,

I'm having a really weird problem. Basically if I try and play a movie and I have my headphones in, the background track audio will sound perfect but the foreground audio (dialogue and such) is horribly cracked and fuzzy/distorted.

Playing music in Rhythmbox also works perfectly, but I've tried several (.avi) movies and they all have this problem when my headphones are in. I've also played around with all the volume controls in alsamixer to see if that could be the problem.

I'm running 10.04 with ALSA 1.0.23 (just updated ALSA from .21 to see if it would help but no dice).

Here's the result of aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


EDIT: SOLVED!
the verdict is...I'm an idiot. It was the headphones. Apparently my fancy iPhone headphones do something to distort the sound that they don't do when connected to my phone and that was causing all the trouble. Duh :)

---

### Post by zanknits on 2011-05-16
Update! 

Just tried playing some audiobooks and language audio files in Rhythmbox, and those were garbled as well.

So current issue:
Music - awesome! totally working!
Human speech - not working at all.

Any thoughts? I will try with different headphones as well, but I'm pretty certain that's not the problem.

---

