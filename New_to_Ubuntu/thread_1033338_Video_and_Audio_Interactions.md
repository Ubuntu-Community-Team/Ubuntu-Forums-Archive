---
title: "Video and Audio Interactions"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by cwsnyder on 2009-01-07
Back when I was first getting started with Linux (November '07), I couldn't get my sound to work with a live CD (I tried Knoppix 5.1.1 and Ubuntu 7.04 and 7.10).  Since I had looked at Windows Vista RC1 before, I knew Windows Vista had problems with motherboard video.  I had nothing to lose at that point, so I put in a cheap nVidia GeForce 6200 256M video card to check it out. Viola! Sound worked!  Why it worked was not my problem at that point, so I went on and installed (at that point December '07) Ubuntu 7.10 Gutsy Gibbon which was the latest version available and have been fairly happy since.

Now we come to October '08.  I tried installing the Jack sound system software with Audacious as an alternative to Audacity, which I had used under Windows XP and continued to use under Ubuntu.  After I installed Audacious and Jack, neither Audacity nor Audacious worked.  During extensive research, I learned that Audacity and Jack don't play well together.  Both want to play at the hardware level rather than at the ALSA level, and conflict.  Even RhythmBox and other sound applications were broken.  I tried un-installing Jack and Audacious, but the damage remained.  I tried installing Pulse Audio applications, since there was a hint that Pulse Audio sound was independent of ALSA.  Still no luck.

Since I had working Mandriva One, Debian Lenny, and Windows XP partitions, I just dropped the problem for a while as I had other projects.  I checked back every once in a while, and tried a few things, but sound still didn't work.

This morning, I had an update to the nVidia driver software.  I installed the updates, and checked out the changes to the nVidia control panel.  I have no idea if this update fixed a problem which I reported as a bug report that prevented hard drive installs of Ubuntu (from 7.10, 8.04, & 8.10) from recognizing my Etronix 1280x1024 17" display as anything more than a 640x480 display without a custom xorg.conf file, although the Live CDs recognized that they could use 800x600.  At any rate, I try to check to see if anything breaks further after a driver update.

When I checked after the update, however, my Audacity works again, and RhythmBox works again.

Explanations anyone?:confused:

---

### Post by cwsnyder on 2009-01-23
My Ubuntu install finally deteriorated to the point where only system sounds and Audacity worked. (I have no idea why Audacity still worked. :p)

I finally went back to [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) entitled Comprehensive Sound Problem Solutions Guide, which showed me how to completely remove my sound configuration files and ALSA sound files, then re-install.

My sound applications all work, and although it replaced Ekiga and Evolution, which I don't use, I am leaving well enough alone for now.:D

---

### Post by cwsnyder on 2009-01-29
I think I finally found the problem: the Audacity in the Ubuntu repositories uses PortAudio which seems to eventually kill all other ALSA sound sources on my system except system sounds.  I am going to try installing Audacity from the Sourceforge.net page to see if that will work better.  If not, I may try compiling from source to see if I can set the options better.

---

