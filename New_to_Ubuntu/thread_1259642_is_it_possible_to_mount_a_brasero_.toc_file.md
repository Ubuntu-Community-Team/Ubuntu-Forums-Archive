---
title: "is it possible to mount a brasero *.toc file?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by macanudokiosko on 2009-09-06
does any way exists, to access a *toc cd-image, which was created by brasero?  (please say yes)  Honestly, I've been unable to create a proper *.iso file. All google hints are failing.  macanudokiosko

---

### Post by cwsnyder on 2009-09-06
The way I understand it, the *.toc file is simply a table of contents, not the actual file structures.  In other words, there is nothing to mount.

The simplest way to build an .iso file might be to burn the CD, then rip to an .iso.

---

### Post by Liolikas on 2009-09-06
> **cwsnyder said:**
> The way I understand it, the *.toc file is simply a table of contents, not the actual file structures.  In other words, there is nothing to mount.

The simplest way to build an .iso file might be to burn the CD, then rip to an .iso.
No mkisofs we have nice commmand.
Also try K3B.

---

### Post by h6w on 2010-04-11
You are supposed to be able to convert the .toc file to .cue with cueconvert (since both are just text files describing the layout of the .bin file).

However, there's currently a bug in cueconvert to do with '#' characters in the .toc file created by cdrdao.  I'm attempting to fix it, but cueconvert doesn't seem to have been actively maintained since 2007, so it looks unlikely that the fix will go upstream.  

I'm hoping that the package maintainer will be willing to take a patch that will fix it once I've fixed the problem.

---

