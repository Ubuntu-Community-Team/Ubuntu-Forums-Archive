---
title: "Formatting external usb hard drive, what extention?"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by trooperchix on 2010-04-15
I have a new 500 Gb external hard drive.  I want to use it to hold backup files, old music, etc.  A catch all.  I have figured out how to find it on GParted, but it does not recommend how to format it, so I'm lost.  It doesn't automount either, but I imagine that the formatting or lack thereof is the issue there.  Can anyone walk me through this?  I've read a lot of posts, but none seem to address this issue specifically nor are they newbie friendly.  Your help would be appreciated.

---

### Post by Zzl1xndd on 2010-04-15
It would really depend how you intend to use the drive. Normally I do EXT4 on all my drives now, with the exception of the ones I also need to use on Windows or Mac. If I need to be able to read/write on Linux/Mac/Windows then FAT32.

---

### Post by 2hot6ft2 on 2010-04-15
I format my externals to NTFS so windows and ubuntu can both use it. I don't have/use a Mac so I don't have to consider that.
If the drive is empty and unpartitioned select the empty drive in GParted and select New and create a new partition.
Then right click on it and under format choose the formatting that you want.
Then click on Apply (The green check mark).

---

### Post by trooperchix on 2010-04-15
Ok, in Gparted, primary or extended partition, and I am not getting the option of ntfs.  am I missing something?

---

### Post by trooperchix on 2010-04-15
Ok, I did it as primary, and to fat32, since it wouldn't give me the ntfs option.  all seems well.  i did read somewhere that there is a problem with the size of a file that can be held under fat32 (something about the file has to be under 4 gb).  Is there any truth to this?  Also, I need this to be able to read and write under two laptops.  The one I'm on now is ok since I did all the fiddling on it so I assume the permissions are correct.  Now, how do I do I change the permissions to allow the other system to access it?  Let's say that system's name is "booger"...

---

### Post by srs5694 on 2010-04-16
Yes, FAT32 has a file-size limit of 4GiB.

To create an NTFS filesystem, you must install the ntfsprogs package. You can do this from Synaptic. (I don't recall the exact menu location, I'm afraid -- my systems' GUIs are set up very differently from the Ubuntu defaults.)

As to permissions, if you use either FAT or NTFS, that's handled on each system that accesses the disk, not on the disk itself. If you can access the disk for both reading and writing on your current system, and if your second system is similar (same version of Ubuntu, or otherwise similar in its options), then you should be fine on both systems.

---

