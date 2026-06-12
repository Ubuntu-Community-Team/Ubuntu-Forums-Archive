---
title: "Pulseaudio woes"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by DrDevice on 2010-09-20
Hokay, so I recently did a clean install of 10.04 from 9.04, and it looks pretty spiffy, figured most of the new methods pretty quickly, and overall I'm pretty happy.

BUT...

I own ET Quake Wars, a lovely game with a native client that runs uber-smooth on my humble system.  I am quite addicted.  But in 9.04 the game kept crashing with a segmentation fault whenever I tried to use the in-game VOIP.  After reading and fiddling, I figured out that Pulseaudio was to blame, for some reason.  Many posts suggested using 'killall pulseaudio' but that never seemed to work as it kept coming back by itself (which shouldn't happen I think).  The 'padsp' wrapper didn't work either.  Oh well, I've used ALSA and it's never let me down, so I made sure it was installed, then 'apt-get remove pulseaudio' and done.  No more problems with ETQW, and everything  worked fine.

With 10.04, it seems Pulseaudio is even more tightly integrated into the system.  I did the above with it, but this time I've gotten a lot of problems with other programs, usually in the form of either no sound or having sound until another program pre-empts the first (often without my noticing it. I run Mangler and missed people talking to me.)

With Ubuntu now really preferring Pulseaudio, it now becomes imperative that I find a solution that lets me run ETQW without having to remove and reinstall Pulseaudio every time.  Thoughts, please?

---

### Post by oldos2er on 2010-09-20
> **DrDevice said:**
>   Many posts suggested using 'killall pulseaudio' but that never seemed to work as it kept coming back by itself (which shouldn't happen I think). 

No, it shouldn't. This tutorial will allow you to reliably kill and restart pulseaudio: [http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

---

### Post by DrDevice on 2010-09-20
> **oldos2er said:**
> No, it shouldn't. This tutorial will allow you to reliably kill and restart pulseaudio: [http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

THANK YOU!  Yes!!  Worked like a charm!  I'm putting that link into my sig!

I just edited the */etc/pulse/client.conf* the way the article suggested to turn off the respawn effect, I left the */etc/rc2.d/S50pulseaudio* alone since I do want it to start at boot.  Now I got a script setup that kills pulseaudio, runs my game, and turns pulseaudio back on when I'm done.

I'm marking this thread solved, however, I would like to know others' thoughts on **why** they've got pulseaudio set up to where the *--kill* option does not keep it killed.  Seems to be the antithesis of "total user control", IMHO.

---

### Post by oldos2er on 2010-09-20
You're welcome. As to why pulseaudio is setup not to die, you'd probably need to ask the devs.

---

### Post by MichiganMan on 2010-10-11
> **oldos2er said:**
> You're welcome. As to why pulseaudio is setup not to die, you'd probably need to ask the devs.

Oh I don't think they could possibly care less about breaking several of the few retail games that went out of their way to support Linux.  I mean seriously, is there a single shred of evidence to the contrary?  Silly game designers, that'll teach them, what do we need them for anyways?

---

