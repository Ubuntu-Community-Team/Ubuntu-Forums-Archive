---
title: "Backing Up HDD (Quick Question)"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-09-21
Whenever I back up my HDD, I've always just dragged and dropped all my files to an external drive.  Is there a more space-efficient way of doing this, such as an archived file type, or particular program?  Logic tells me no, but the way people talk about backing up their hard drive tells me yes...

---

### Post by apb2390 on 2009-09-21
Try backing it all up into a big .tar.gz file or .tar.bz2 file using archive manager. If it hangs and doesn't work, do it in sections (eg. documents and pictures, then videos and downloads, etc.)

---

### Post by kambrik on 2009-09-21
Have a look at clonezilla that may be another option

---

### Post by ded3d44 on 2009-09-21
Try incremental backups. This can be done using rsync.

If you like graphical user interfaces, maybe this is an option:
[http://www.getdeb.net/release.php?id=4757](http://www.getdeb.net/release.php?id=4757)

---

### Post by mapes12 on 2009-09-21
I use Grsync (GUI). It has a compression option and only backs up new or amended files so the backup takes no time at all after the first one has been done.

---

### Post by mikechant on 2009-09-21
These days the bulk of most people's data (by size, even if not by number of files) consists of multi-media files which are already efficienly compressed by algorithms tuned to the particular type of data. So adding another compression step typically saves very little or no space, wastes time and produces output which is more 'fragile'**. Personally I make all my backups to an external drive, using rsync with no compression.
This means that only changes are copied to the external drive, so it's fast, and the backup just mirrors the normal directory structure, so it's easy to recover individual files, entire folders or entire folder hierarchies with no messing about or special tools.

As per above, you can use grsync if you prefer a gui. Either way, I would recommend using the -a option or gui equivalent - this is 'archive mode' and does things like preserve file permissions etc.

Example: I have all my multimedia files stored in various folders and subfolders at the /mnt/data1 mount point. I want to backup the whole lot to my external USB drive which has a single partition labelled 'usba' and which mounts as /media/usba, so I use the following command:
```
sudo rsync -av --progress /mnt/data1 /media/usba 
```

Note that if you want to back up everything in your home directory, you may need to add the following --exclude option:
```
sudo rsync -av --progress --exclude *.gvfs /home /media/usba 
```

This is due to a bug which I won't go into here - the .gvfs files don't need backing up anyway.


** By this I mean that suppose you have (for example) 1000 seperate music tracks backed up and you get a one-sector disc error (or something equivalent) somewhere in that data, then a maximum of one file will get corrupted. If the 1000 music tracks are placed in a single compressed archive, a one-sector error somewhere in that archive could destroy all 1000 music tracks in one go.

---

