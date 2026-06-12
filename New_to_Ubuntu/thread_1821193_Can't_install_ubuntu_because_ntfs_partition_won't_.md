---
title: "Can't install ubuntu because ntfs partition won't unmount"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by jotiho on 2011-08-08
I have a system with XP on sda (15G) and want to install ubuntu on sdb (150G).  There's an ntfs partition on sdb with back-up data which I want to preserve.

I've created ext3 partitions for / and /home and a swap partition.  But when I try to install I get an error saying that the ntfs partition can't be unmounted.  Trying to unmount it manually gives the message 

"Cannot unmount volume
Error  org.freedesktop.Hal.Device.InterfaceLocked
Details  The encloding drive for the volume is locked"

I found a post that looked promising, and involved using an ntfs configuration tool, but I can't identify this in the synaptic list.

I'm working with Hardy, since I don't have enough RAM for later versions on this old machine.

Thanks for any help.

---

### Post by elgordodude on 2011-08-08
Are you trying to install off of wubi or a live cd?

---

### Post by oldfred on 2011-08-08
If it needs chkdsk or is hibernated gparted will not work with a NTFS partition. 

Suggest running chkdsk on you d: drive or whatever it is seen as in Windows from windows or a window repair CD.

chkdsk d: /r

---

### Post by jotiho on 2011-08-08
I'm installing from a live cd.

The gparted bit seems to work, since this is how I created the ext3 and swap partitions.
I'll try the chkdisk and see what happens.

---

### Post by jotiho on 2011-08-08
chkdsk gave the following

The type of the file system is NTFS.
Volume label is ntfs on big disk.

CHKDSK is verifying files (stage 1 of 5)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 5)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3 of 5)...
Security descriptor verification completed.
CHKDSK is verifying file data (stage 4 of 5)...
File data verification completed.
CHKDSK is verifying free space (stage 5 of 5)...
Free space verification is complete.
Windows has checked the file system and found no problems.

  30884617 KB total disk space.
  10535484 KB in 43240 files.
     10112 KB in 4250 indexes.
         0 KB in bad sectors.
    103717 KB in use by the system.
     54236 KB occupied by the log file.
  20235304 KB available on disk.

      4096 bytes in each allocation unit.
   7721154 total allocation units on disk.
   5058826 allocation units available on disk.

---

### Post by JC Cheloven on 2011-08-08
If the above didn't solve the problem (did it?), simply booting windows, accesing the disk, and PROPERLY shutting down windows, should fix it.

Note.- Your case is usually due to a bad win2 shutdown, which leaves the filesystem as "in use", and thus unusable by other OS.

---

### Post by jotiho on 2011-08-09
Looks like this was the problem -- incomplete XP shutdown.  Restarted into XP and made sure close down was clean.  On restarting live CD the ntfs partition was not shown as mounted, and installation went through wihout problem. All fine now.  Thanks to all posters.

---

### Post by JC Cheloven on 2011-08-09
Glad you got it sorted :)
If you have a minute, please mark thread as solved (please use "thread tools" at the top), so that other users can search more efficiently. Thank you so much.

---

