---
title: "question about the directory names"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by dagarshali on 2010-02-02
Hi,
I have a 64 bit karmic installed. I have a question about the directory names. On my laptop, the directory names are case sensitive, which is what i would expect. However, when I connect my external hard disk, I see that the directory is Reactor2, but i can go to that directory even with cd rEaCtoR2. How is it possible?

Regards,
Vishwa

---

### Post by audiomick on 2010-02-02
Hallo,
This is just a _guess_. If the external does not have a Linux file system on it, it might be because of that.

---

### Post by Flimm on 2010-02-02
> **audiomick said:**
> Hallo,
This is just a _guess_. If the external does not have a Linux file system on it, it might be because of that.
Good guess. Case sensitivity actually depends on the type of filesystem, not the operating system, although I recommend always treating filenames in a case sensitive way when using Linux.
Most external hard drives use NTFS or Fat32 for their filesystems, which are not case-sensitive, and compatible with most operating systems. You can double-check by running the Disk Utility (System, Administration) included in Ubuntu 9.10.

The filesystem installed by Ubuntu is ext3 or ext4, which *are* case sensitive.

EDIT: OK, I just tried this out on my laptop, and I'm properly confused. I managed to create two directories in an NTFS partition with identical names but different cases. I'll be back after a re-boot to see how Windows Vista reacts.

---

### Post by Funnnny on 2010-02-02
No, you can name something, Something, SOMETHING in a same directory in NTFS mounted by Ubuntu, just try it.
When booting in windows, it show 3 folder with same name right, but you can rename one, or copy all of them into another directory
Seems weird

---

### Post by Flimm on 2010-02-02
Yeah, I just tried it. It is weird. You can have multiple names that differ only in case in NTFS, Linux treats them correctly, but Windows lists them as separate entries and merges their contents.

Looks like I was wrong, [this article](http://support.microsoft.com/kb/100625) states that NTFS is in fact case sensitive, to be POSIX compatible. However, Windows can't handle this feature correctly, so treat it as if it can't.

Fat32 is *not* case sensitive, I just tried it now:
```
/media/Test$ mkdir Reactor
/media/Test$ cd reaCTOR
:/media/Test/reaCTOR$ cd ..
/media/Test$ cd Reactor/
:/media/Test/Reactor$ cd ..
:/media/Test$ mkdir reacTOr
mkdir: cannot create directory `reacTOr': File exists
:/media/Test$ ls
 Reactor

```

So the external drive of the OP is probably Fat32.

---

### Post by dagarshali on 2010-02-02
thank you guys for the responses.. I checked and the file system is FAT32...

Regards,
Vishwa

---

### Post by lisati on 2010-02-02
> **Flimm said:**
> 
EDIT: OK, I just tried this out on my laptop, and I'm properly confused. I managed to create two directories in an NTFS partition with identical names but different cases. I'll be back after a re-boot to see how Windows Vista reacts.

To confound the matter slightly in the hope of shedding some light: If I read things correctly, NTFS has at least TWO file naming conventions as part of its heritage. One of these is the 8.3 file name format inherited from CP/M and other sources that inspired MS-DOS and PC-DOS. On machines I have used, this convention has been case insensitive. AFAIK, support for longer file names allowing mixed case file names was introduced later.

---

### Post by Funnnny on 2010-02-02
Vista, XP can only see the folder. Never tried on Win7 yet.
IT should be something with Windows, NTFS have naming case then
btw most external harddisk use Fat, I rarely saw them formated with NTFS ( default factory settings )

---

