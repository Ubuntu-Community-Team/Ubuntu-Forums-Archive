---
title: "Error messages when unpacking .tgz"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Torri on 2009-11-18
I am attempting to download the driver that (hopefully) will fix my oversized resolution. When I download the file and try to open from firefox, I get "<file>.tgz could not be opened, because the associated helper file does not exist. Change the association in your preferences." I don't know what association it's talking about.
 
When I try to unpack the file manually, I get: An error occurred while loading the archive.
 
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure due to previous errors.
 
I'm lost. I don't know what any of this means. I just want my display to fit on my screen! Oh, and it's a Gateway mx3215 laptop, with CN700/P4M800 Unichrome Pro. Anyone know what to do?? Thanks!

---

### Post by nathan726 on 2009-11-19
This error happens when the file is not in gzip archive format.
Where did you download the file from? What is the size of it?

Sometimes if you rename it, you will be able to open it.
So try changing .tgz part to each of the following and attempt to open the file:
```
.tar
.tar.bz2
.zip
.
```

---

### Post by PGScooter on 2009-11-19
In cases like these, I find the ```
file
``` command useful. It can sometimes tell you the exact compression.

---

### Post by Pgtest70 on 2009-11-19
Hi,

If you downloaded it from VIA linux portal or their main site it may be broken ... I just tried to download the Ubuntu 9.04 unified driver (binary) for my CX700. Get the same result for all 9.04 drivers and source code but all other versions are unpackaged correctly.

Have reported it to VIA.

Best regards
Pgtest70

---

