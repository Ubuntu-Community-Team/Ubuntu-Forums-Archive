---
title: "jaunty 32bit sound won't work. ICH7 chipset..any ideas?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by amsgwp on 2009-05-07
I'm kind of a newb but I've tried going through this sound troubleshooting guide and my stuff seems to be installed but not working.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Here is my output
[http://www.alsa-project.org/db/?f=a7b8e6bdd18ce0abeedac98a847586bf1bcd2dd7](http://www.alsa-project.org/db/?f=a7b8e6bdd18ce0abeedac98a847586bf1bcd2dd7)

Also when I open up the alsa-base.conf I added 

options snd-hda-intel model=asus

and also tried

options snd-hda-intel model=asus-w1v

I have a Asus W7J notebook with a Azalia compliant soundcard.  It seems to have all the exact same stuff as the example the soundtroubleshooting guy used.  Any ideas?

---

### Post by amsgwp on 2009-05-07
ok got it.

I'm not sure what it was but I *THINK* it was changing my alsa.conf last line to

options snd-hda-intel model=3stack

---

### Post by Didius Falco on 2009-05-07
That's great! Thanks for coming back and posting the answer - someone else with the same problem will appreciate it.

I read your initial post, but I don't use that kind of sound card, so I couldn't be of any help.

Mark this thread solved (see my sig for an easy how-to) and go listen to some music!!

Regards,

Didius

---

### Post by amsgwp on 2009-05-07
Thought I had it fixed.  If the audio is muted then I hear loud crackles through the speakers.  Speakers work fine if not on mute.  Any ideas?

---

