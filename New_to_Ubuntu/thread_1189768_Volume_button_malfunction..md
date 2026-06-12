---
title: "Volume button malfunction."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-06-17
I've searched for thread with similar keywords but no matches found.

Long story short, I had been having a different sound problem which has now been fixed/solved. However yesterday before I solved that issue, I found that the volume keys have malfunctioned, they were working to start with, but now when I turn volume up, down and or mute it, the little volume bar displays these actions however the volume does not change.

The computer is Sony VAIO VGN-FW72JGB (Japanese version) and OS is 9.04 if that helps? 

If anyone could be of help I really would appreciate it.

---

### Post by Mark Phelps on 2009-06-17
Have the volume button EVER worked under 9.04?

I'm asking because I upgraded a laptop to 9.04 and ALL the special keys stopped working.  They were working fine in 8.04.

---

### Post by T4K3Z0U on 2009-06-17
> **Mark Phelps said:**
> Have the volume button EVER worked under 9.04?

I'm asking because I upgraded a laptop to 9.04 and ALL the special keys stopped working.  They were working fine in 8.04.

I'm pretty sure they have, but I only used the volume once or twice because, I normally use headphones most time but it was playing through the jack and speaker together. So I could be completely mistaken. But the play, stop, forward and reverse buttons which are on the same panel with the volume all work fine, I definitely remember using them before and just tried them now.

I've got a couple other Fn keys that don't seem to want to work but they aren't quite as important to me as the sound keys just yet.

---

### Post by T4K3Z0U on 2009-06-18
[center]bump![/center]

---

### Post by Mark Phelps on 2009-06-18
You need to quit bumping -- people will answer you when they're ready.  Bumping only ticks people off...

Since you don't really know if your special keys ever worked, you need to see if the kernel detects them.  To do that, open a terminal and type "xev".  This will open a small box on the desktop.  Place the mouse cursor in that box and press one of the special keys.  If the kernel detects the key, you will see event messages scrolling by in the larger terminal window. Try this for each special key.  If you see nothing scrolling by in the larger terminal window, that means the kernel is incapable of detecting the special key hardware -- and you're out of luck.

I had this very problem happen myself, and restored my tablet PC to 8.04 because none of the newer versions detected the special keys anymore.

---

### Post by mgmiller on 2009-06-18
Since the volume bar appears when you use the volume up down buttons, the keys are being detected, they are just adjusting the wrong thing.

Open System > Preferences > Sound

Near the bottom is the "Default Mixer Tracks" area.

There is a list of Devices to control with the keyboard.  Just click on the first one which should be "Master" to select it and try the keyboard buttons again.  You can try different ones without closing the window and try the keyboard buttons to see what happens.  The 2 that usually work best are master and PCM.

---

### Post by LightningCrash on 2009-06-18
Good thing you bumped this thread, you might not have gotten that last response!

---

### Post by T4K3Z0U on 2009-06-18
> **Mark Phelps said:**
> You need to quit bumping -- people will answer you when they're ready.  Bumping only ticks people off...


In my experience with large forums, if a thread has gone 24hrs without a reply, it has been buried by new threads or threads with new responses. 
Given this is a computer/OS forum, large doesn't begin to describe it and I felt a bump was necessary.


> **mgmiller said:**
> Since the volume bar appears when you use the volume up down buttons, the keys are being detected, they are just adjusting the wrong thing.

Open System > Preferences > Sound

Near the bottom is the "Default Mixer Tracks" area

There is a list of Devices to control with the keyboard.  Just click on the first one which should be "Master" to select it and try the keyboard buttons again.  You can try different ones without closing the window and try the keyboard buttons to see what happens.  The 2 that usually work best are master and PCM.

Thank you, this has work. I most likely altered the setting in there when trying to fix my original issue of sound through both the jack and speakers. 

> **LightningCrash said:**
> Good thing you bumped this thread, you might not have gotten that last response!

Indeed, but we'll never know for sure. ;)

---

### Post by shane2peru on 2009-06-23
> **mgmiller said:**
> Since the volume bar appears when you use the volume up down buttons, the keys are being detected, they are just adjusting the wrong thing.

Open System > Preferences > Sound

Near the bottom is the "Default Mixer Tracks" area.

There is a list of Devices to control with the keyboard.  Just click on the first one which should be "Master" to select it and try the keyboard buttons again.  You can try different ones without closing the window and try the keyboard buttons to see what happens.  The 2 that usually work best are master and PCM.

Thanks!!!  This solved my problem as well!!  I have used Buntu for a long time, and never new that little tip!

Shane

---

