---
title: "File system, symlinks, mounting"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by outleradam on 2010-04-01
I have a NAS which becomes disconnected sometimes.  I put about 30 gigabytes of videos on this mount per day.  It is mounted at /home/mythtv/NAS.    When the NAS is disconnected, it records to my local hard disk.  Where do those files go when I mount my NAS back up?

I could not find what I needed when I searched, partially because I  don't know the terminology.  A good link would help.

---

### Post by capscrew on 2010-04-02
> **outleradam said:**
> I have a NAS which becomes disconnected sometimes.  I put about 30 gigabytes of videos on this mount per day.  It is mounted at /home/mythtv/NAS.    When the NAS is disconnected, it records to my local hard disk.  Where do those files go when I mount my NAS back up?
...

This really doesn't appear to have anything to do with symlinks.  But...

All partitions that are mounted to the local file system (i.e. your NAS) are mounted on directories in the local system.  There is no difference between a directory (folder) and a mount point.  It is more about how the directory is used (e.g mount point or directory).

So if we have the directory [FONT="Courier New"]/home/mythtv/NAS [/FONT]that has a partition mounted to it, all data is saved to the partition (in the appropriate files and folders).  If the partition is *unmounted* the data is stored in the directory that is the mountpoint (e.g [FONT="Courier New"]/home/mythtv/NAS[/FONT] in your case).  The side effect of this is that the files in the directory (/home/mythtv/NAS) hare hidden when the partition is mounted.

I use this set of circumstances to my advantage.  I purposely have 1 file in the directory I am using as a mount point 9describing what is supposed to be mounted there.  I then write a script that checks if that file is there.  If it returns true then I stop my backup.  If it returns false then the partition is mounted and the backup continues.

You could do the same thing in a script.  Sort of like this:
```

if the file is found 
  put the data elsewhere.  
else 
  put he data here # on this partition

```

or you could do this
```

if the file is found 
  mount the partition
  put he data on the partition 
else 
  put he data on the partition

```

---

### Post by outleradam on 2010-04-03
Thank you.   I was hoping to get some info on symlinks as well.  I would really like some reading on the filesystem.  I've read and understand the FS guidelines,  but that dosent really help me understand why my ext 2 filesystem supports symlinks but my fat32 NAS does not.   I just know how things act.  I would like to know why.

---

### Post by capscrew on 2010-04-03
> **outleradam said:**
> Thank you.   I was hoping to get some info on symlinks as well.  I would really like some reading on the filesystem.


See [**_here_**]("http://tldp.org/HOWTO/Filesystems-HOWTO-6.html") for information on ***ext ***file systems.

You can read [**_this _**]("http://www.ntfs.com/fat-systems.htm")for information on ***FAT ***file systems.
> 

I've read and understand the FS guidelines,  but that dosent really help me understand why my ext 2 filesystem supports symlinks but my fat32 NAS does not.   I just know how things act.  I would like to know why.

I'm not sure what FS guidelines you are referring to...

The specific reason EXT file systems support symlinks is in its basic design.  Symlinks are pointers to the files inode (the reference to the files location on the disk).  The FAT32 file system does not use the inode as a reference.  It uses the FAT (File Allocation Table).  Symlinks (or hard links) are not shortcuts.

---

