---
title: "Cleanup and De-frag?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by medicalystoned on 2010-03-01
Biggest newb question of all time............. Is it necessary to de-frag and run cleanups using Linux operating systems?  Or isn't that one of the reasons we use Linux?

---

### Post by zeroseven0183 on 2010-03-01
No. It's not necessary. EXT filesystem is different from NTFS and FAT in some ways. One is this:

> 
Another common Windows practice that is not needed in  Unix is defragmenting the hard drive.  When NTFS and FAT write files to  the hard drive, they don't always keep pieces (known as blocks) of  files together.  Therefore, to maintain the performance of the computer,  the hard drive needs to be "defragged" every once in a while. ** This is  unnecessary** on Unix File systems due to the way it was designed. When  ext3 was developed, it was coded so that it would keep blocks of files  together or at least near each other. 

No true  defragmenting tools exist for the ext3 file system, but tools for  defragmenting will be included with the ext4 file system. 
To better understand File Systems, check out  [https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

For "cleanups", Linux still keeps temp files which are safe to delete for the most part.
And sometimes when you remove applications, there are packages that are not completely remove and just "sit" on your hard drive. These too can be removed, automatically, by running commands in the Terminal like ```
sudo apt-get autoremove
```

---

### Post by medicalystoned on 2010-03-01
Thanks a lot man..... i love terminal, i do all I can from terminal, makes me feel smart......thanks again, peace

---

