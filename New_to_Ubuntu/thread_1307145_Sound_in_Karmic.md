---
title: "Sound in Karmic"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by glennric on 2009-10-30
First Problem:  Where is System->Preferences->Sound in Karmic?
Second Problem:  If a sound hasn't played for a while I hear a crack before the next sound plays.  I deleted the ~/.pulse directory to clear the pulse cache, and rebooted, but that doesn't help.  Sound worked perfectly in Jaunty.

---

### Post by travmanx on 2009-10-30
> **glennric said:**
> First Problem:  Where is System->Preferences->Sound in Karmic?
Second Problem:  If a sound hasn't played for a while I hear a crack before the next sound plays.  I deleted the ~/.pulse directory to clear the pulse cache, and rebooted, but that doesn't help.  Sound worked perfectly in Jaunty.

I'm not sure why your icon isn't there. I've attached a picture of it for me.

Goto System->Preferences->Main Menu
Scroll down to the preferences folder (left side)
Check sound

---

### Post by glennric on 2009-10-30
That is odd.  What command does that menu item launch?

---

### Post by bug67 on 2009-10-30
> **glennric said:**
> "First Problem: Where is System->Preferences->Sound in Karmic?If a sound hasn't played for a while I hear a crack before the next sound plays.  I deleted the ~/.pulse directory to clear the pulse cache, and rebooted, but that doesn't help.  Sound worked perfectly in Jaunty."

1.  Can you right click on the sound icon that's in the upper right of the top panel and select preferences from there?

2.  Possible solution to the popping issue here:

[http://swiss.ubuntuforums.org/showthread.php?t=1290222](http://swiss.ubuntuforums.org/showthread.php?t=1290222)

---

### Post by travmanx on 2009-10-30
> **glennric said:**
> That is odd.  What command does that menu item launch?

gnome-volume-control

---

### Post by glennric on 2009-10-30
There is a good chance that will fix the audio popping.  I do have an HDA sound chip.  At least that is the kernel module that is loaded.  It does seem to happen after about 10 seconds of no sound too.

---

### Post by glennric on 2009-10-30
Yep, that fixed the popping.  Now the issue of where is System->Preferences->Sound.  I suppose I will boot to the live cd and see what .desktop file is supposed to provide it.  Most likely the package that provides that file and the executable got uninstalled or didn't get installed properly in the upgrade.

---

### Post by glennric on 2009-10-31
I figured out where System->Preferences->Sound is.  It shows up as System->Preferences->Volume Control.  The thing is I had opened this before and it no longer does what it used to do.  How do you set the sounds for events?

---

