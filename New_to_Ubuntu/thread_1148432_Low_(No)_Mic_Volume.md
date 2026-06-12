---
title: "Low (No) Mic Volume"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by age99 on 2009-05-04
Hi, I'm having a heck of a time being able to use my mic.  
I can't for the life of me figure out how to record any sound from the mic.  
I have installed Pulse, and the sound seems ok, although since upgrading to 9.04, it seems lower than before.  But if I try to record anything from the Mic, I don't get anything at all, or so low that I can't hear it.  

I'm running 9.04, on a Dell XPS M1330.  

Thanks

EDIT: Oh, and I wanted to mention that I have reviewed some of the posts regarding this problem, and still couldn't get anything to work.

---

### Post by jbrown96 on 2009-05-04
My suggestion is to ditch pulseaudio and switch to alsa. System--->Admin-->Sound. Change all the devices to alsa. Reboot just to be safe. In a terminal (apps-->accessories) enter ```
alsamixer
``` your low sound is probably caused by having pcm or master at a low setting. Turn both all the way up (use the arrow keys). You will probably want to turn you mic channel up as well. I don't recommend turning up mic boost because it usually causes feedback.

---

### Post by age99 on 2009-05-04
I originally had only Alsa, and I couldn't get it to run either.  I've reverted to Alsa, but I have no luck with this either.

If I type in "alsamixer" I can see the mic, but there is no status bar above it like all the other devices.

If I try to adjust the setting through Volume Control (by right clicking the speaker icon in the tray) all the mics are muted.  If I un-mute them, it just changes back to muted.

---

### Post by aw4lly on 2009-05-04
Type alsamixer in the Command Line. Then to get to mic press the right arrow until it is selected. Then press 'm' to mute/unmute it. Then use the up and down arrows to change the volume.

---

### Post by age99 on 2009-05-04
Unfortunately, that didn't work either.  
I still don't understand why the mic is always muted if I try to adjust the volume under Volume Control / Recording.  If I un-mute it, it just reverts back.
The volume is so low that I can barely hear anything.  Just enough to make me curse Ubuntu.

---

