---
title: "PLEASE HELP! Sound card is acting up!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by R500evoL on 2009-01-07
hey. i just switched from vista to Intrepid today and the first thing i noticed is that i cannot get sound to come out of the headphone jack. i am still getting sound through the speakers built into my laptop but the only way they will work is if im using OSS. ALSA and Pulse will not work. when i do a " aplay -l " it says no sound cards found. when i do a " lspci -v " it sees that there is an Intel Audio Controller.  i am not a complete idiot when it comes to computers, but if anyone has any advice, PLEASE put it in laments terms. please dont make me switch back to Vista. if anyone needs anymore info, let me know. im more than happy to give you whatever you need to know. (and if it helps, its a Sony FZ-series laptop w/ decent specs)

---

### Post by linux_tech on 2009-01-07
You can try this, in a terminal type:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
``` 

This should restore your sound back to original state.

Comprehensive sound guide here may also help-
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by R500evoL on 2009-01-08
I tried that and it did nothing. When i first installed Intepid on my laptop, it recognized that i had the SigmaTel driver for the sound card(which is the one that was used w/ windows). it is now absent from my list of devices that i can control. the only one that works is HDA STAC9872A (OSS v4 audio mixer). this one will give me sound but only through the speakers built-in to the laptop. would re-installing ubuntu or installing windows and immediately installing ubuntu do the trick?

---

