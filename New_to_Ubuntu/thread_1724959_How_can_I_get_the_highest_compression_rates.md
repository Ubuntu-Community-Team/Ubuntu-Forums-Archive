---
title: "How can I get the highest compression rates?"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by pivotraze on 2011-04-09
Okay, so basically, this is my story:

I'm downgrading from Ubuntu 11.04 to Kubuntu 10.10, for multiple reasons.

I'm a developer, I need stability right now. Anyways, I am trying to backup my home folder (it's not a separate partition, STUPID ME! .-.) so what I need to backup totals 2.5GB.

I want to compress that 2.5GB into under 1GB, if possible. 

What is the smallest I can get 2.5GB?

Files included:
*.py
*.html
*.avi
*.mp3
*.doc
*.odt
*.pdf

Many different types, many different files. The amount of files is: 1,023. If I don't get a reply by the time the Kubuntu download is at 90%, currently at 80%, I'm using .tar.lzma :P
 

Thanks in advance!

-Cody

---

### Post by rosencrantz on 2011-04-09
I couldn't tell you about software comparisons, but with respect to file types:
Text files usually yield rather high compression factors, but with anything precompressed like .avi and .mp3 (or jpeg, btw.), you'll not be able to get to much smaller sizes.

---

### Post by sanderj on 2011-04-09
I don't understand: 2.5 GB is not that much; you can put it on one DVD or USB stick, then format your system, and get the stuff back.

So why the "1GB" constraint?

---

### Post by kyle6513 on 2011-04-09
I believe he may want the 1gb due to ubuntu one. I believe that only gives you 1gb? either way, you could use ubuntu one and dropbox in conjunction if thats the problem? (:

---

### Post by The Cog on 2011-04-09
I think -j (bzip2) instead of -z (gzip) might give a little better compression.

---

### Post by NightwishFan on 2011-04-09
I use LZMA/XZ. It seems like it gives as good of compression and faster compression/decompression than Bzip2 most of the time. Granted, you will not find miracles with any form of lossless compression.

I am also looking forward to seeing this: [http://ck-hack.blogspot.com/2011/04/quick-lrzip-comparison.html](http://ck-hack.blogspot.com/2011/04/quick-lrzip-comparison.html)

---

### Post by rudihawk on 2011-04-09
Get a bigger flash disk! :D

---

