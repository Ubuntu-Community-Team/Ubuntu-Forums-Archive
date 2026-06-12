---
title: "Copying a dvd to an iso"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by boards-of-canada on 2009-05-13
I used k9copy in the past a few times and it worked. I'm trying 9.04 and k9copy keeps crashing. What can I use to copy a movie dvd to n iso?

---

### Post by Absolut Newbee on 2009-05-13
try Brasero Disc burner, works for me

---

### Post by MrWES on 2009-05-13
> **boards-of-canada said:**
> I used k9copy in the past a few times and it worked. I'm trying 9.04 and k9copy keeps crashing. What can I use to copy a movie dvd to n iso?

I used K9Copy in Jaunty and it runs fine. Remove and reinstall K9 and that might help. FWIW, there are command line options and ripping/shrinking/burning dvd's, although it surely isn't as easy at K9copy. If your interested in the command line technique, let me know. The commands involved are:

vobcopy - this will rip the dvd, into one large vob

vamps - this will shrink the original vob down to 4.3gb, for burning on a single layer DVDR

dvdauthor - this will create a standard dvd directory structure from the 4.3gb vob file

mkisofs - creates the iso file

growisofs - burns iso to dvd 

I don't have a script to do all of this, but I have some small scripts and/or aliases that help out.

~Bill

---

### Post by MrWES on 2009-05-13
> **Absolut Newbee said:**
> try Brasero Disc burner, works for me

Brasero will not shrink a DVD9 to a DVD5. And, IMHO, Brasero is not as robust and reliable as K9Copy and K3B.

~Bill

---

