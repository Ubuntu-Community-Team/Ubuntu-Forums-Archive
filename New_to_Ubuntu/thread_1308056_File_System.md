---
title: "File System"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by ChappyHappy on 2009-10-31
Hi, 

If my mp3 are in ntfs format, could I just transfer them to /home (ext4) and it'll play on etaile or rthymbox? I'm still installing now so I cant actually try it out myself.

If it wont work, what are some solutions?

Thanks

---

### Post by Liolikas on 2009-10-31
etaile or rthymbox will play mp3 no matter where they are (ntfs, ext3 ext4 etc. as long as you have fs drivers and with stock Ubuntu kernel you have huge amount of them) you just have to point program to mp3 correctly.

---

### Post by Joe Ker1086 on 2009-10-31
Yes, Linux is pretty smart at reading NTFS and HFS partitions even though they are not native to Linux. (Windows not so much....) Plus, your file extensions themselves are what matter, as long as it can read the drive it should have no problem opening whatever is in there as long as it is a valid file format for Linux.

---

### Post by ChappyHappy on 2009-10-31
Oops, I think I left some info out...or I'm misunderstanding something.

My current mp3s are in my external (ntfs). Im planning to put them on my /home partition (ext4) of my laptop.
I guess my real question, is that possible since they are two different file system.

I know ubuntu can read ntfs with ntfs-g. Im not worried about that. 
I just dunno if it's possible to put a ntfs file in a ext4 partition and still be able to use the ntfs file. Like are there some file system rules/incompatibility preventing this.

Thanks

---

### Post by ikacer on 2009-10-31
it will work fine. I have a ntfs external harddrive and ext4 internal hard drive and I transfer files between the two all the time with no problems.

---

### Post by QLee on 2009-10-31
[QUOTE=ChappyHappy]
My current mp3s are in my external (ntfs). Im planning to put them on my /home partition (ext4) of my laptop.
I guess my real question, is that possible since they are two different file system.[/QUOTE]

They are merely stored on volumes with two different filesystems, the MP3s are in MP3 file format and they are saved in MP3 format regardless of the Filesystem on which they are stored.

---

