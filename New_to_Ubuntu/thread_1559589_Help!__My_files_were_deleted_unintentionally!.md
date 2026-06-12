---
title: "Help!  My files were deleted unintentionally!"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by runeedge on 2010-08-23
I have an external hard drive (FAT32) which I used to store photos while on a trip abroad.  I connected it to my desktop (EXT4) running 9.10 and initiated the transfer (34 GB).

I ran to class.  When I came back the transfer was done.  I restarted the computer, went into my bios, and enabled Vt-d as I'm experimenting with virtualization.  Upon reloading my desktop I went back to my external hard drive, to copy over some other files.  At this point, I noticed that about 75% of the folders on the disk were empty, including the file of photos that I had copied over earlier.  Files at the root level and some of the folders seem to be completely unaffected.

To make matters worse, about 4/5 of the photos that I had transfered to my computer were corrupted.

I checked my message logs and around the time that I booted up my computer after setting Vt-d I have hundreds of messages that read something like:
Aug 23 16:46:07 tmahrt2-desktop kernel: [  195.554521] sdb1: rw=2, want=426043758, limit=268435392

According to Disk Utility the hard drive is healthy.  Furthermore, the harddrive states that the amount of memory being used is the same as what was used before all the folders were emptied (i.e. most of the files were deleted but the hard drive is still reporting that the hard drive is almost full).

Is it possible for me to get my files back?  Any idea on what happened to my harddrive?

I tried reading the harddrive from my laptop (ext4, Ubuntu 10.04) but it reads it no different from my desktop.

---

### Post by utnubuuser on 2010-08-24
sometimes there's a hidden trash folder on drives - use > cd /media/sdb (or whaterver the name of the drive is to move to the drives directory, then> ls -almight show if such a folder exists, and if any of your files/photos are in it.

---

### Post by redbook4574 on 2010-08-24
> **runeedge said:**
> I have an external hard drive (FAT32) which I used to store photos while on a trip abroad.  I connected it to my desktop (EXT4) running 9.10 and initiated the transfer (34 GB).

I ran to class.  When I came back the transfer was done.  I restarted the computer, went into my bios, and enabled Vt-d as I'm experimenting with virtualization.  Upon reloading my desktop I went back to my external hard drive, to copy over some other files.  At this point, I noticed that about 75% of the folders on the disk were empty, including the file of photos that I had copied over earlier.  Files at the root level and some of the folders seem to be completely unaffected.

To make matters worse, about 4/5 of the photos that I had transfered to my computer were corrupted.

I checked my message logs and around the time that I booted up my computer after setting Vt-d I have hundreds of messages that read something like:
Aug 23 16:46:07 tmahrt2-desktop kernel: [  195.554521] sdb1: rw=2, want=426043758, limit=268435392

According to Disk Utility the hard drive is healthy.  Furthermore, the harddrive states that the amount of memory being used is the same as what was used before all the folders were emptied (i.e. most of the files were deleted but the hard drive is still reporting that the hard drive is almost full).

Is it possible for me to get my files back?  Any idea on what happened to my harddrive?

I tried reading the harddrive from my laptop (ext4, Ubuntu 10.04) but it reads it no different from my desktop.

I can only give my favourite answer to these type of problems, try using testdisk to recover the partition.

---

### Post by afroman10496 on 2010-08-24
> **utnubuuser said:**
> sometimes there's a hidden trash folder on drives - use might show if such a folder exists, and if any of your files/photos are in it.

better yet, just go to the folder with nautilus (the file manager) and [ctrl H] once you're at the drive. see if there's a .trash folder or any other . folders.

---

