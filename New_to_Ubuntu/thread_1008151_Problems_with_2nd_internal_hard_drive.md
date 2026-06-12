---
title: "Problems with 2nd internal hard drive"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-11
Hello, 

I have a few qeuries here and any advice would be much appreciated as I am pretty hopeless with computers.

I recently install a secondary 1TB hard drive which currently has about 400GB of media saved on it.

I have started to get an error message on boot up about an error with sdb 1 (my 2nd HDD) it then forces a scan which takes a while then stops half way and eventually says press 'ctrl and D' to disable something and continue. After this it runs as normal. It does take a long to to boot up tho because of this error. I would like to sort this error out but dont know where to start.

As a workaround I thought I could just unmount the 2nd HDD and mount it when I need to. However, when I try to unmount it it says I do not have permission and that it can only be unmounted through root. How do I do this? And is it quick and easy to mount and unmount the hard drive?

One more thing, I will eventually sort out a dual boot on my 1st hard drive and want the second as a shared drive. Will I have to format the drive into FAT32 or NTFS and can this be done with all the media already on it?

Sorry for waffling on and thanks in advance for any help!!!

Fletch :popcorn:

---

### Post by logos34 on 2008-12-11
you need to sudo it.  So for example if its an ext3 partition and the mount point is '/media/storage', then

sudo mount -t ext3 /dev/sdb1 /media/storage

and

sudo umount /media/storage

Formatting the shared drive will erase it. But you don't need to change fs types because linux can read and write to ntfs, and windows can do the same to linux with fs-driver.

---

