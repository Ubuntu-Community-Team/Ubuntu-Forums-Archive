---
title: "no video players work"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by libihero on 2009-11-04
none of my video files work.... i have no clue what happened

---

### Post by werecatomega on 2009-11-04
could you play them on ubuntu before? if you couldn't, or never have, you need to get some "restricted" codecs. you can find out how to do this with a simple google search. if you could play them before, i'm not sure.

---

### Post by libihero on 2009-11-04
well i used to be able to before i did a fresh install, and i have the restricted codes downloaded... :S
i cant remember if i played videos since the fresh install... but im almost sure i did

---

### Post by 3rdalbum on 2009-11-04
I'll guess: Did you install Openshot Video Editor from their PPA?

It's known to cause this problem.

There are two solutions:

1. Remove the PPA, remove Openshot, ffmpeg and the libav* packages. This will also remove lots of your software. After you've done that, reinstall the software that was removed, and it will bring in the regular Ubuntu ffmpeg as a dependency.

2. Remove the PPA, remove Openshot, and now use the "Force Version" function of Synaptic to downgrade the libav* packages to their normal Ubuntu versions. Try the first package, if it tells you that it's about to remove lots of software, then click Cancel and try the next one. It's possible to downgrade those packages without removing all ffmpeg-dependent software, but you have to Force Version them in the correct order.

If you need to be able to play video RIGHT NOW (for instance, you're going into a meeting or something where you need to play a video as part of a presentation), the ffplay command will still be able to play video.

---

### Post by libihero on 2009-11-05
haha ur right!
can u tell me what to put in the terminal to remove all of that in the first step please? :)

---

### Post by MelDJ on 2009-11-05
> **libihero said:**
> haha ur right!
can u tell me what to put in the terminal to remove all of that in the first step please? :)

why not remove it from synaptic by searching then removing. then going to software sources to remove the ppa?

---

### Post by libihero on 2009-11-05
so
its in the middle of the removal of software
and by the looks of things i wont have any software at all :|

---

### Post by libihero on 2009-11-05
i just got pwned. loool
another reinstall here i come...

---

