---
title: "No online sound"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by sprogmeister on 2009-01-18
I have reinstalled intrepid and all works fine except for sound online, I don't get any. Has anyone got any ideas?

---

### Post by gettinoriginal on 2009-01-18
Try these  :P

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by diablo75 on 2009-01-18
So when you start the PC (and login) you hear the start up sound with the singing angels and that bongo drum?  Or is that not working too?

Here's the two things I'd check first:

A lot of pre-fab PCs (from Dell in particular) come with an additional sound card.  Sometimes they'll take a little plug that blocks off the holes to the on-board sound that you can just pull out.  Try hooking your speakers up to that instead of the secondary sound card (if you have one).

If you don't have a second sound card, you should check the volume levels in the mixer via that little speaker icon on the top panel (double-click to bring the whole mixer up).  By default it probably isn't showing you all the available levels you can actually control.  (For example, if you have a surround sound card, it probably is only showing you levels for wave output, but not levels for your front speakers, the center channel, the rear/surround speakers, the LFE, etc.)  With the main mixer open, click the preferences button and check everything off.  Then make sure everything that appears to possible be a level for sound output is turned up.

If nothing else, refer to the links the previous poster has pasted in.  Good luck!

---

### Post by sprogmeister on 2009-01-18
the sound works fine except when on-line

---

### Post by tegnoto89 on 2009-01-18
If you start your internet browser before anything else does the sound work?  I had this issue and just removed pulseaudio and installed esound - fixed it.

---

### Post by sprogmeister on 2009-01-19
This only seems to happen with Totem movie player. Anyone got any ideas how to solve that?

---

### Post by gettinoriginal on 2009-01-19
It seems from the threads that a lot of people are uninstalling pulseaudio and going back to Alsa.

---

### Post by sprogmeister on 2009-01-20
Again there is no sound online. An example, I was sent me a birthday ecard and there is no sound here at all. The ponderey goes on

---

### Post by 3rdalbum on 2009-01-20
Are you running 64-bit, with Flash Player installed from the repositories?

If so, remove it and remove nspluginwrapper. Install Flash Player 64-bit from Adobe.

I've noticed that nspluginwrapper (necessary for 32-bit plugins on 64-bit browsers) can sometimes stop sound from getting through. Adobe now has a 64-bit version of Flash Player so that will take nspluginwrapper out of the equation.

---

### Post by sprogmeister on 2009-01-20
No it's not 64 bit. I think I have tried installing just about everything!

---

