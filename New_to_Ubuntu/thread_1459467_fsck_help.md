---
title: "fsck help"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Michael Di Fulvio on 2010-04-21
I do a lot of Torrent downloads for research on various subjects. I have a small 36gb disk drive mounted as 1 file-system. I put old stuff in Trash and remove the same to keep enough room on my disk. This has seemed to work for many months now.

Yesterday I 'trashed' what should have made free at least 15gb or more. The files are gone as I removed them from the Trash folder were I placed them but it does NOT look like I have the file-system space returned even after a restart.

I have much UNIX experience but have not used this kernel very long. I think I may still have some Torrent files somewhere on the system that are not being removed. Or perhaps just a clean fsck would fix this.

For fsck my memory is to go single user with a init 1 and run fsck aganst the file system. Or do you know of the files being retained by the Torrent client?



------mikeD

---

### Post by quadproc on 2010-04-21
> **Michael Di Fulvio said:**
> 
For fsck my memory is to go single user with a init 1 and run fsck aganst the file system. Or do you know of the files being retained by the Torrent client?

To safely run fsck, the usual recommendation is to unmount the file system in question.  This usually means running from some other volume such as a Live CD.  The normal boot process mounts the file system as read only first, then after fsck has finished the file system is remounted read/write.  Sorry, I don't know about Torrent.

You might have use for the _find_ command - you can search for files based on pretty much anything, including size, date, etc. so you might be able to target the characteristics of suspected files.

quadproc

---

