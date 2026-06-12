---
title: "Struggling with Firefox Flash Please help"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by BeAllEndAll on 2009-10-18
I am new to Linux and have struggled with it for the last few days.  I have two things that don't seem to work.  Or at least, they take more knowledge than I have to get them working.

The first is that the Adobe Flash within Firefox is choppy.  It does not allow me to update the settings if I right click on whatever video is playing.  The settings are grayed out.  I am running Ubuntu version 8.10 but have also tried 9.04 and thought it best to try to go backwards to 8.10  Is there a way around using Adobe's Flash Player to maybe one that works?

The second is that Ubuntu Linux doesn't recognize my MP3 player - Sansa E200.  I did for about a day load Fedora - it seemed a little better at recognizing it - maybe one out of ten times.  With Ubuntu I have never gotten it to recognize it.

Its probably sacrilege in this forum to say this, but these are very basic and high use items for a home computer and I am surprised by this, given all of positive Linux hype.  If these problems existed with Windows there would be all kinds of negative press.

Sorry for the diatribe.  Any help would be appreciated.  

Thanks,

---

### Post by ikt on 2009-10-18
> **BeAllEndAll said:**
> The first is that the Adobe Flash within Firefox is choppy.  It does not allow me to update the settings if I right click on whatever video is playing.  The settings are grayed out.

Are the videos choppy just in regular mode, not full screen mode?

> **BeAllEndAll said:**
> The second is that Ubuntu Linux doesn't recognize my MP3 player - Sansa E200.  I did for about a day load Fedora - it seemed a little better at recognizing it - maybe one out of ten times.  With Ubuntu I have never gotten it to recognize it.

> SSS001 Connecting your Sansa e200 player to a Ubuntu (or any Linux) computer

Rhapsody player people should read this post about connecting and disconnecting.

While on the player, go to "Settings", then "USB Mode". Switch it to "MSC". 

Plug your player in the computer through the USB cord, and (in my experience) the player should say "Connected" and "Disconnected" a few times. After a few seconds, it should stay on "Connected" with arrows on it. If you change anything on the player, it should stay on "Writing" until disconnection.

[http://ubuntuforums.org/showthread.php?t=312196](http://ubuntuforums.org/showthread.php?t=312196)

When you plug the drive in, check syslog (system > admin > log file viewer) and see if it says anything about errors accessing the device etc.

> **BeAllEndAll said:**
> 
Its probably sacrilege in this forum to say this, but these are very basic and high use items for a home computer and I am surprised by this, given all of positive Linux hype.  If these problems existed with Windows there would be all kinds of negative press.,

These problems do exist in the windows world, and it does receive all sorts of negative press for it. (Note: vista driver debacle)

---

### Post by BeAllEndAll on 2009-10-18
Thanks, I'll give these a try.  You are right Windows has its issues - otherwise I wouldn't be here.  Thanks again.

---

