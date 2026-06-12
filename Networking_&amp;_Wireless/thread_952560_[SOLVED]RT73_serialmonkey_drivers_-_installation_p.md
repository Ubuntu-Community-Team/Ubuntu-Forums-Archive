---
title: "[SOLVED]RT73 serialmonkey drivers - installation problems"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by georg_c on 2008-10-19
Hi everybody, hope this hasn't been posted already!

Anyway, here goes:

This is on Ubuntu/Hardy.
Some days ago I updated my system to the kernel 2.6.24-21 via the update manager. After the next boot, my wireless networking didn't work any more (D-Link DWL-G122 v.C1). Ah, well, I thought, I need to recompile the drivers against the new kernel header files. So I downloaded the latest driver sources from [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz"), which gave me '/usr/src/rt73-cvs-2008101906',
 and followed the steps in this excellent tutorial: [http://ubuntuforums.org/showthread.php?t=400236&highlight=RT73]("http://ubuntuforums.org/showthread.php?t=400236&highlight=RT73").
As usual, after compiling ('# make ') I got the warning about my files being too big as mentioned in the tutorial:
```
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
*** Module rt73.ko built successfully
```
So, as usual, I did '# strip rt73.ko'.
Then I proceeded to '# make install'.
This time I got a warning:
```
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.24-21-386/extra/rt73.ko
```
I ignored that warning and went on to the next step: '# modprobe rt73' and it refused to load the freshly compiled module:
```
FATAL: Error inserting rt73 (/lib/modules/2.6.24-21-386/extra/rt73.ko): Invalid module format
```:confused:

After some trial and error it turned out that the driver module will install and load properly if you DO NOT strip it!

Just to let anybody know who might have had the same trouble.

I wanted to post this as a follow-up to the abovementioned thread, but it seems to be archived and locked. Maybe this post can still be merged into that other thread?

G.

---

