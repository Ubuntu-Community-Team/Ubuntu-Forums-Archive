---
title: "MacBook Pro: my sound won't work on Ubuntu"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by ProginoskesLives on 2009-02-09
Ubuntu knows I have a sound card, but for some reason it won't use it.  I'm not sure how to explain, but when I adjust the volume, there is no change, and when I test to see whether the sound is working or not, I don't hear anything.  I checked, and my sound isn't muted/the volume is all the way up.  I've looked everywhere for a way to fix it, but I can't find anything.  Does anyone know what to do?

---

### Post by ac90b671 on 2009-02-10
I think i'm having the same problem. I have the santa rosa mbp on 8.10. No matter which "device" I test the sound on, nothing happens. Headphones don't work either.

---

### Post by ac90b671 on 2009-02-10
Ok, i think i have a solution, at least it worked for me. run "sudo gedit /etc/modprobe.d/options" in the term and then add "options snd_hda_intel model=mbp3" to the end of the document that was called up. Save it and restart.

---

### Post by ProginoskesLives on 2009-02-11
I tried opening that, but it already had that exact set of text listed.  There must be some weird problem somewhere else.  Thanks for your advice, though.  And, on the bright side, I just discovered that F11 is the key that makes my scrolly-mouse thing appear because I was trying to turn the sound up and down.  :D

---

### Post by almahtar on 2010-05-02
> **ac90b671 said:**
> Ok, i think i have a solution, at least it worked for me. run "sudo gedit /etc/modprobe.d/options" in the term and then add "options snd_hda_intel model=mbp3" to the end of the document that was called up. Save it and restart.

That worked for me -  17" Macbook pro Santa Rosa (3.1). Thanks for posting.

---

