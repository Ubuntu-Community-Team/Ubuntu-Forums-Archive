---
title: "file size limit problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by bbkingwithaj on 2009-01-23
This is a bit of a hard question to classify, but Ill try it here first, so I need to copy files that are 4.4 gb and 7.4 gb respectively to a usb2.0 16 gb key, now everytime it gets to 4 gbs it just gives me an error and cuts the file at 4.0 gb on the usb key.  is there any way around this?  does it mean the drive is fat32?  is there a way for me to make ubuntu ntfs cuz i heard they don't have limits on files?  sorry if these are dumb questions but i'm a noob.

---

### Post by bhaverkamp on 2009-01-23
That's what it sounds like. You can check the file system type using the mount command or fdisk -l.

---

### Post by diablo75 on 2009-01-23
You can format that thumb drive to whatever kind of file system you wish with a gparted live CD.  You can download an ISO of the latest version from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by ibuclaw on 2009-01-23
4GB is the file size limit on FAT32 filesystems.
Read here for citation: [http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32)

I concur with diablo, you can reformat the pendrive to another format more suitable for your needs using the gparted Partition Manager.

What you may consider doing though is splitting the files into 3GB or 4GB chunks (ie: in zip, tar or rar format) so you can workaround getting it put it onto your pendrive.

Regards
Iain

---

### Post by hyper_ch on 2009-01-23
I also think you use fat32 on that drive.

---

