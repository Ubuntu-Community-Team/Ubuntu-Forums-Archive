---
title: "What's the best app for finding and deleting duplicate files between two external HD?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by diablo75 on 2010-01-10
I have two external hard drives that I store a lot of different music and videos on.  I have a feeling there is probably a lot of stuff on both that are exactly the same, file wise.

I opened up Application>Add/Remove and found FSlint and Kleansweap.  The problem I've run into is:

FSlint seems to take forever.  I let it sit for 12 hours after limiting it's directories to the two folders in /media/ that represent the external hard drives, and the hard drive activity was never-ending.  What's it doing?  Why does it take so long?

Kleansweep seems to get closer to what I need, but it doesn't let me limit it's scope down to the external hard drives, so I get all kinds of results from all over the system for things  I don't want to remove.  If I tell it to limit it's search to /media/ and run a scan, it finds no files in a split second; as if it didn't even attempt to look at the subdirectories (devices).  So I just told it to scan all of / and I let it sit for 6 hours... and stopped it, with no results from my external hard drives reported.  What's going on here?  I'd like to find an app that can do what I need in under a few minutes, not a few days.

---

### Post by Barriehie on 2010-01-10
Check out **fdupes**; it's in the repos and the manpage suggests it might be what you're after.

---

