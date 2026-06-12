---
title: "How many levels of directories can we create?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-04
I'm trying to set up a organized way of sorting my files (up until now I just chucked them in whichever folder was convenient).  So I am curious how many directory levels I can create before I run up against the limits of the ext3 file system.  For instance I might have a directory structure that looks like this:

/home/ubuntu/Documents/Work-related/Writing/2009/Free-lance-work/Company-1/Project-1/Draft-1/Research/

I heard that the maximum path length is different between Linux, Windows and Mac OS as well, so this sounds like I might run into problems trying to sync long directory structures.

Also a related question: how long can I make my filenames?

---

### Post by Celauran on 2009-06-04
> **learningcurb said:**
> Also a related question: how long can I make my filenames?

255 characters. Not sure about directory depth.

---

### Post by gmjs on 2009-06-04
I believe the limit for ext3 filesystem directory depth is 32,000, so you should be OK ;)

I read somewhere that ext4 supports up to 64,000 levels!

---

### Post by SunnyRabbiera on 2009-06-04
I heard its quite a lot for ext3 and 4, just dont overdo it.

---

### Post by Bios Element on 2009-06-04
ext3 was 64k I believe, ext4 doesn't have a limit IIRC.

---

### Post by learningcurb on 2009-06-04
So for ext3, does that mean we can create 32,000 (or 64,000 levels) of directories each with a maximum directory name of 255 characters?

---

### Post by MasterNetra on 2009-06-04
> **learningcurb said:**
> So for ext3, does that mean we can create 32,000 (or 64,000 levels) of directories each with a maximum directory name of 255 characters?

Yeap, provided you have the hard drive space to handle it all ;)

---

