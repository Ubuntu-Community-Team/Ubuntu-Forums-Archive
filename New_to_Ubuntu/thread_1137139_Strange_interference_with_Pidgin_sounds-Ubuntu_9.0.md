---
title: "Strange interference with Pidgin sounds-Ubuntu 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-04-25
Hi!  Whenever Pidgin makes one of it's notification sounds, there is a strange static/feedback-like noise.  I have tried changing volume settings, output, ALSA, Pulseaudio, etc.  But no avail.  What might be causing this?  Does it have something to do with the new Pulseaudio implementation?

Thanks in advance!

---

### Post by pi.boy.travis on 2009-04-25
This is bug: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/347544](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/347544)

---

### Post by pi.boy.travis on 2009-04-27
Anyone have any ideas?

---

### Post by koffeinöverdos on 2009-05-02
[http://ubuntuforums.org/showthread.php?t=1095499](http://ubuntuforums.org/showthread.php?t=1095499)
This seems to imply that it is in fact PulseAudio. I don't know what to do about it but until I find a solution i'm considering getting used to using Pidgin with sounds muted...

---

### Post by Dr.Vista on 2009-05-02
That happens to me too.

---

### Post by manpoole on 2009-05-05
I'm getting the same thing, with the volume up it was very unpleasant.

---

### Post by tmos22 on 2009-05-05
Is it only with Pidgin??

---

### Post by manpoole on 2009-05-05
Oddly enough yes... although I did have another audio source playing - Pandora

---

### Post by pi.boy.travis on 2009-05-05
Yeah, it is only with Pidgin.  I have tried using ALSA, different drivers, everything.  The flaw must be in pidgin itself.

---

### Post by Octagonal on 2009-06-18
I have this same problem and looked around on the 'net.
Couldn't find a real fix but I did just change the .wav files in the following folder:
/usr/share/sounds/purple 
used by pidgin.
No more annoying static.

---

### Post by pi.boy.travis on 2009-06-19
Awesome!  Thanks!

---

