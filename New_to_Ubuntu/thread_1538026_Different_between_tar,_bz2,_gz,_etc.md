---
title: "Different between tar, bz2, gz, etc?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by masque7 on 2010-07-24
Compression formats. Of the main ones that are available to us (by default) on our Linux boxes, what is the difference?

---

### Post by davidmohammed on 2010-07-24
tar isnt a compression format - its a way to combine multiple files into one file.

bz2 and gz are compression formats - variations on a theme - similar compression ratio's I think.  The default archive manager with ubuntu can open most if not all of these type of files.

---

### Post by masque7 on 2010-07-24
I've heard that tar was just a container. I just wanted to know bz2 vs gz. I mainly come across gunzip (.gz) files.

---

### Post by Bachstelze on 2010-07-24
> **masque7 said:**
> I've heard that tar was just a container. I just wanted to know bz2 vs gz. I mainly come across gunzip (.gz) files.

bz2 generally compresses better than gz, but is slower.  gz is the de facto standard because it is older, and bz2 is not avaialble by default on some OSes (that's why you mostly find .gz files).

---

### Post by Simian Man on 2010-07-24
I'd like to see XZ catch on more.  It has as good or better compression as bz2 but is as fast as gzip.

---

### Post by masque7 on 2010-07-24
Is 7zip proprietary?

---

### Post by KIAaze on 2010-07-24
> **masque7 said:**
> Is 7zip proprietary?
No, it's GNU LGPL. :)

The 7-zip program that originally implemented it is LGPL + has a restriction on the unrar part of the code:
[http://en.wikipedia.org/wiki/7-Zip](http://en.wikipedia.org/wiki/7-Zip)
[http://www.7-zip.org/license.txt](http://www.7-zip.org/license.txt)

The format itself is open and under the LGPL:
[http://en.wikipedia.org/wiki/7z](http://en.wikipedia.org/wiki/7z)
[http://www.7-zip.org/7z.html](http://www.7-zip.org/7z.html)

---

