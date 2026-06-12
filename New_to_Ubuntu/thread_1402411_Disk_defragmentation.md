---
title: "Disk defragmentation"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by sm_here on 2010-02-09
How to defragment hard drive in Ubuntu?

---

### Post by NightwishFan on 2010-02-09
Short answer: You don't. Linux filesystems resist fragmentation.

Slightly longer answer: Some filesystems support defragmentation, I believe XFS can. In the future ext4 and btrfs should support online deframentation.

---

### Post by mcduck on 2010-02-09
Linux filkesystems suffer very little from fragmentation, they try to place the fles into your drive in a way that alows them to change and grow without fragmentation. As a result they don't fragment easily, and if they do, it has very small effect on drive's perfomrance.

You really won't see any decrease in the drive performance because of fragmentation until the drive gets very full (around 90% and over). And at that point you'd just better off buying a new hard drive to get more space, so there's not much use for defragmenting tools. At least on any normal desktop use. :)

---

### Post by sm_here on 2010-02-16
Thank you.

---

### Post by audiomick on 2010-02-16
There is a rather good explanation here
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by sm_here on 2010-02-16
Thank you Michael. The explanation given in that link is really good.

---

### Post by linux18 on 2010-07-08
I actually made  a shell script to defragment the ~/ directory, and with the help of  some [www.commandlinefu.com]("http://www.commandlinefu.com/")  members it was shrunk to one line that works fast and efficiently:

 find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l  < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d;  mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t

for external hard drives, replace the "~"  in "find  ~ -maxdepth" with the location of the drive. 

example:

find /dev/sdb1 -maxdepth 20 -type f -size -16M -print > t; for  ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a"  /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t
   
this works in most cases. the script basically re-copies most data under  16 mb from the drive back to the drive. it works because most  filesystems (including fat 32 ) will always try to keep new data  contiguous when it is saved. 

but really, linux shouldn't ever need defragmentation, my shell script ( was a shell script, now its just one command ) is just a placebo, it does defrag, but on linux defraging won't really help because it doesn't really hurt

---

