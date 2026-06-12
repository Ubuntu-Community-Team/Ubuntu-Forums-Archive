---
title: "Why does linux/ubuntu use fat32?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by triunenature on 2009-05-06
fat32 vs ntfs

Why did they choose fat32?  NTFS is typically considered better.

Better security (permission system), able to handle large files better...

and just newer

so why fat32?

---

### Post by Temposs on 2009-05-06
Ubuntu does not use fat32. By default, Ubuntu uses ext3.

---

### Post by meindian523 on 2009-05-06
Linux(Ubuntu) uses ext3 or ext4.It supports both FAT32 and NTFS.

---

### Post by Temposs on 2009-05-06
Further, Ubuntu would not use ntfs because ntfs is what Windows uses by default, and that would just be weird :-)

---

### Post by Vunutus on 2009-05-06
A little clarification:

Ubuntu CAN use fat32 or NTFS as it's primary file system. That, however, is not the default choice (for good reason) and you must select it manually when installing the OS.

By default, Ubuntu and many other Linux distributions use the ext3 file system. ext3 is a journaling file system, which means it does not fragment like NTFS and others, therefor it never needs to be "defragmented" like is common under Windows.

If I had to guess, the OP probably mounted a thumbdrive or something similar and saw it listed as "fat32". Most portable USB storage devices use fat32.

---

### Post by triunenature on 2009-05-06
> **Temposs said:**
> Ubuntu does not use fat32. By default, Ubuntu uses ext3.

> **meindian523 said:**
> Linux(Ubuntu) uses ext3 or ext4.It supports both FAT32 and NTFS.

Thank you both for replying.

Any good reading material to catch me up on why it doesn't use ntfs?

I mean, i know windows uses it, and if its windows it must be "bad".  But really, why ext3 over ntsf?

---

### Post by meindian523 on 2009-05-06
well,no.It's not like anything Windows uses has to be bad.And here's a comparison of various file systems.
[http://en.wikipedia.org/wiki/File_system_comparison#Features](http://en.wikipedia.org/wiki/File_system_comparison#Features) and more details about file systems
[http://en.wikipedia.org/wiki/File_system](http://en.wikipedia.org/wiki/File_system)

---

### Post by atomizer on 2009-05-06
Linux doesn't use NTFS because it is microsoft close source.
MS won't tell the world how they own-made FS works, so the linux guys had to reverse-engeneer it to get it working under linux.
For a few years it was even impossible to write on NTFS without destroying the data on it.
Thanks to some pretty smart linux-engeneers it is now possible to read/write on a MS NTFS partition. (thank you guys)

---

### Post by Didius Falco on 2009-05-06
> **atomizer said:**
> Linux doesn't use NTFS because it is microsoft close source.
MS won't tell the world how they own-made FS works, so the linux guys had to reverse-engeneer it to get it working under linux.
For a few years it was even impossible to write on NTFS without destroying the data on it.
Thanks to some pretty smart linux-engeneers it is now possible to read/write on a MS NTFS partition. (thank you guys)

Which explains the name "Not Telling File System" :-$

---

### Post by 3rdalbum on 2009-05-06
It's partly because there was no NTFS write support until a couple of years ago, and partly because Linux and Unix already have a large number of very suitable filesystems.

The better question is "Why use NTFS"? I don't even think it natively supports the *nix-specific security features that are implemented at filesystem-level.

---

### Post by mcduck on 2009-05-06
Like 3rdalbum pointed out, even if we forget how NTFS is Microsoft's proprietary file system that simply cannot be used on free, open-source OS becasue of the limitations Microsoft puts on it's use, there's still the simple facts that:

a) it doesn't support the common features of Linux filesystems, it's not even able to store the normal file permissions that are pretty integral part of how Linux works. 

and 

b) It's just not any better than what Linux has been using for ages before people were even able to backwards-engineer NTFS to the point that read/write support for NTFS bcame even fairly reliable on anything else than Windows systems.

So even when NTFS might not be a bad filesystem, it's not any better than what we have, it's hard to support because of lack of information, it doesn't support the features we need and in the end, even if we wanted to we wouldn't be allowed to use it since Micrsoft owns it.

---

### Post by The Cog on 2009-05-06
> **Vunutus said:**
> A little clarification:

Ubuntu CAN use fat32 or NTFS as it's primary file system. That, however, is not the default choice (for good reason) and you must select it manually when installing the OS.


No it absolutely cannot. Linux must be installed on a filesystem that supports the storage of unix-type file permissions. FAT and NTFS are not suitable. Linux simply cannot work on them.

---

### Post by dacorr on 2009-05-06
FAT32 is Microsofts, built on the open FAT model. NTFS is built on FAT32 literally using additional layers.

including the security layer, Use windows XP encryption on a file then copy the file to fat32 if memory serves as fat32 does not support the NTFS security layer it is ignored and the file can be opened.

last checked that 2 years ago, let me know if it still works

Dac

---

### Post by MontelEdwards on 2009-05-06
NTFS is unsecure and slow as hell
compared to ext3 and ext4 which i use.
and fat32 blows
and that retarded thing when NTFS locks up when not shutdown is completly dumb to me.
and NTFS is not journaling

---

### Post by benj1 on 2009-05-06
linux supports both

because it cares about interoperability.

---

### Post by darth_indy on 2009-05-06
The main issue here seems to be the difference between the terms "use" and "access" - Most variants of Linux can read and write to both FAT32 and NTFS now, but it cannot use either as its main partition.

If you are asking as a precursor to installing Ubuntu on a system, you will want to know that the best way to go at the moment is ext3. I would recommend ext4, except for the fact that older versions of Ubuntu don't support it, and the ext2/ext3 drivers for Windows don't support ext4 (that's a concern only if you're dual-booting)

When I was setting up my first machine with Ubuntu, I tried to set the home partition as NTFS, so I could easily share the data between the two OSes on my computer (Ubuntu and XP). That is when I discovered that NTFS doesn't save the file permission data neccessary for a Linux system. So instead I set my home partition as ext3 formatted, and installed the ext3 driver in XP.

---

### Post by blueridgedog on 2009-05-06
> **triunenature said:**
> why it (Ubuntu) doesn't use ntfs?

Ubuntu can access NTFS, but since the file system format is closed source, it is impossible to reproduce it perfectly.  That said, some of the later community developed file systems are on par or superior.  More importantly from an Ubuntu standpoint, they are open.

---

### Post by theozzlives on 2009-05-06
> **triunenature said:**
> Thank you both for replying.

Any good reading material to catch me up on why it doesn't use ntfs?

I mean, i know windows uses it, and if its windows it must be "bad".  But really, why ext3 over ntsf?

NTFS stands for NT File System (NT as in Windows NT). ext3 and 4 are better file systems, and NTFS is probably covered by some patent or something.

---

