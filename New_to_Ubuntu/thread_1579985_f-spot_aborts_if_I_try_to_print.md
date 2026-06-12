---
title: "f-spot aborts if I try to print"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by Ralph L on 2010-09-22
I tried f-spot for the first time.  It aborted most times, when I tried to print from it.  A couple of times it worked, but has completely stopped working now.  The same photo (taken from f-spot's Photo folder) prints fine with Gnome Image Viewer.  I updated to the latest version of f-spot 0.8-1--same problem.

I thought about deleting .config/f-spot/photos.db to make f-spot start over.  Would this be a good idea or would I just make things worse.  There are no photos in f-spot that I care about--other copies.

I am running lucid and using an hp photosmart c-6180 all-in-one-printer.

Any help would be appreciated

---

### Post by lkjoel on 2010-09-22
> **Ralph L said:**
> I tried f-spot for the first time.  It aborted most times, when I tried to print from it.  A couple of times it worked, but has completely stopped working now.  The same photo (taken from f-spot's Photo folder) prints fine with Gnome Image Viewer.  I updated to the latest version of f-spot 0.8-1--same problem.

I thought about deleting .config/f-spot/photos.db to make f-spot start over.  Would this be a good idea or would I just make things worse.  There are no photos in f-spot that I care about--other copies.

I am running lucid and using an hp photosmart c-6180 all-in-one-printer.

Any help would be appreciated
That will not make it worse.
Try it.

---

### Post by Ralph L on 2010-09-23
Thanks for the input.  I uninstalled f-spot (using Synaptic) deleted the f-spot folder in .config and in .gconf, and reinstalled f-spot.  It still aborted, when I tried to print a picture.

Does anybody else have this problem, or is it just me?  I couldn't find any reference to an f-spot printing problem on google.  I am running Lucid Lynx with f-spot 0.8.0.  This is supposed to be the latest version.  I don't know of anything I have messed with that would cause this problem.  Would somebody else try to print with f-spot and get back to me?

Appreciate any help

Ralph

---

### Post by drknot on 2010-12-10
There is a bug report for this currently open - click on the "this affects me" to increase it's priority.  Reverting to 0.6.x works :(  . 0.8.0 is causing me problems too. I still have one machine on Lucid/f-spot 0.6.x so can use that. It is possible to share the f-spot db between machines, which is helpful as I use a NAS for photos and manage them from there.

---

