---
title: "Defragging Hard Drives"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by n4pgw on 2010-06-30
I understand that the Linux formats do not need to be defragmented, but I have an external hdd with two NTFS partitions so I can share them with Windows computers.  

So, how do I defrag them?

Thanks
Buck

---

### Post by okplayer02 on 2010-06-30
you just answered your own  question when in linux there is no thing such as defragging a drive. So no need to even worry about it. I guess when you use it with your windows machine then it may ask you to degfrag it.

---

### Post by Rubi1200 on 2010-06-30
You might want to consider using a USB stick with a portable defragmentation tool that you could plug in and point to the external HDD.

Here is one example:

[http://portableapps.com/apps/utilities/jkdefrag_portable](http://portableapps.com/apps/utilities/jkdefrag_portable)

Hope this helps.

---

### Post by victor9098 on 2010-06-30
This is from the thread [All about ureadahead]("http://ubuntuforums.org/showthread.php?t=1434502&highlight=ureadahead"), while its purpose is to explain what 'ureadahead' does doing start-up there is also a brief section on fragmentation in linux (quote below). So while it generally is not a problem, compared to other OS's, it does exist and will be further refined in future versions of ureadahead making Ubuntu even greater ;)

> **But Linux filesystems don't need defragmenting!**

Whoever told you that is deeply mistaken, this is one of the most common myths of Linux.

What is true is that Linux filesystems avoid, where possible, fragmenting their inode tables. This means that the index of how files are split up (fragmented) across the disk, and where those parts are, tends to be kept together as a whole.

That's a good thing; fragmentation of inode tables is a big problem for other filesystems (FATs in that filesystem, etc.) so by keeping them together, it wins a lot of performance.

But the data itself is still fragmented, and spread all over your disk in a random order. And unfortunately during boot, it's the data we need.

One of the future things we want to do is use the ureadahead analysis of what we need during boot to feed into a defragmenter, so everything we need is in one big block on the disk.

Have you tried using gparted to reformat the external HDD? I have used it to reformat external drives and USB keys so I can swap between windoh's and Ubuntu without any hitches.

---

### Post by bodhi.zazen on 2010-06-30
> **n4pgw said:**
> I understand that the Linux formats do not need to be defragmented, but I have an external hdd with two NTFS partitions so I can share them with Windows computers.  

So, how do I defrag them?

Thanks
Buck

Drefagment them with a defragmentation application run from Windows. Linux can rx fat/ntfs, but the linux tools to defragment or fix filesystem errors on fat or ntfs are, IMO, inferior to the tools available on Windows.

Makes sense if you think about it, people who run Linux have less interest in maintaining a NTFS file system.Personally if I share across computers, I use FAT, sure it is "old" but it is reliable and there are FAT drivers on most os (ntfs is catching up ... ).

---

### Post by linux18 on 2010-07-07
I actually made a shell script to defragment the ~/ directory, and with the help of some [www.commandlinefu.com]("http://www.commandlinefu.com") members it was shrunk to one line that works fast and efficiently. the original code:

 find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t

for flash drives ( and external hard drives ), replace the "~"  in "find ~ -maxdepth" with the location of the drive. 

example:

find /dev/sdb1 -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t
   
this works in most cases. the script basically re-copies most data under 16 mb from the drive back to the drive. it works because most filesystems (including fat 32 ) will always try to keep new data contiguous when it is saved. 

one last thought ( doesn't apply in your case ), flash drives really don't need ( and shouldn't be ) defragmented. solid state I/O is very consistent even with heavy fragmentation and defragging wears out the drive. but if you must defrag this script is effective and only gives the drive 2 R/W cycles

---

### Post by n4pgw on 2011-03-21
Thank you, I recorded the script and have it in the works to test at a later date.

---

### Post by Weatherlawyer on 2013-03-07
> **linux18 said:**
> I actually made a shell script to defragment the ~/ directory, and with the help of some [www.commandlinefu.com]("http://www.commandlinefu.com") members it was shrunk to one line that works fast and efficiently. the original code:

```
find ~ -maxdepth 20 -type f -size -16M -print > t; for ((i=$(wc -l < t); i>0; i--)) do a=$(sed -n ${i}p < t); mv "$a" /dev/shm/d; mv /dev/shm/d "$a"; echo $i; done; echo DONE; rm t
```

May I presume this will defrag a diferent OS to standard Ubuntu?
I am using an old version of Ultimate Edition.

---

### Post by Paqman on 2013-03-07
That should work on any Linux distro. The tools that make up that command are standard Linux stuff.

---

### Post by oldos2er on 2013-03-07
Old thread closed.

---

