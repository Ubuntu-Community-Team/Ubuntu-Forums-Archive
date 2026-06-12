---
title: "Upgraded to the newest release and..."
date: 2009-05-09
forum: New to Ubuntu
---

### Post by RavagerX on 2009-05-09
...now the sound isn't working. I've played around with all the settings that I know. The files play, I just don't hear anything. Any ideas?

---

### Post by kostkon on 2009-05-09
What exactly have you tried? Nevertheless, could you open a terminal and give the following command
```
aplay -l
```
and post the output here?

---

### Post by RavagerX on 2009-05-09
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm still quite noobish at all of this, so forgive me if I get confused easily. Lol.

I've made sure that my volume settings are actually set high, lol. Switched to pulse audio and back, forth to other settings, but still nothing. I don't even hear the startup sound. All was working fine till I updated.

---

### Post by raymondh on 2009-05-09
see if this thread can help

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by RavagerX on 2009-05-09
I followed steps in that thread closely, thanks for posting it. :)

I am still faced with no sound though. Everything should be playing full blast, but only silence. :(

---

### Post by RavagerX on 2009-05-09
When I set my sound preferences to Alsa and click test, I get this....

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by RavagerX on 2009-05-09
If all else fails, should I just go back to the previous version and install the updates 1 by 1?

---

### Post by Sef on 2009-05-09
> If all else fails, should I just go back to the previous version and install the updates 1 by 1?


No, do a clean install.  But have patience, someone should be able to help you resolve your problem.

---

### Post by RavagerX on 2009-05-09
I'm patient, lol. I remember having a similar problem before, but it went away when I installed Ubuntu again.

---

