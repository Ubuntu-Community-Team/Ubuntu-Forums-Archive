---
title: "Ripping a DVD with HandBrake fails"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by fraser_m on 2009-06-12
I'm trying to rip a DVD with HandBrake, and it scans the titles, sees them all, and starts ripping, but, a few seconds in, the DVD drive spins loudly, and HandBrake hangs. I have libdvdcss2 installed, and the DVD plays fine in VLC.

Any ideas?

---

### Post by jalirious on 2009-06-12
k9copy to decrypt/shrink k3b to burn.

---

### Post by fraser_m on 2009-06-12
I tried the k9copy assistant, and tries to rip it. I'm pretty sure I chose OK settings, but there are 99 titles on the DVD. I picked the first one, as it was 1 hr 33 mins, but k9copy crashed when I started ripping.

Help?

---

### Post by JohnAStebbins on 2009-06-12
It sounds like you might have one of those discs that the studio has deliberately put bad blocks on as a DRM measure (arccos).  You can either pre-rip it with something that knows how to handle such discs (anydvd is the gold standard). Or if you have any experience building applications from source, the latest handbrake SVN has a new option in preferences to use dvdnav for reading dvds.  dvdnav can read most discs that have been mastered this way. VLC uses dvdnav.

---

### Post by markharding557 on 2009-06-12
agree with the above you may get better luck running dvdfabdecypter on wine.
it works perfectly

---

### Post by donkyhotay on 2009-06-12
Have you tried acidrip? I've always had good luck ripping DVD's with that.

---

