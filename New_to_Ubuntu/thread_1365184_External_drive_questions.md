---
title: "External drive questions"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by heavyd5 on 2009-12-26
I am about to install Ubuntu on my machine that already has Windows XP installed. I have about 100 gb of media files that I want to put on a usb external hard drive to free some space for the Ubuntu install. Will I be able to access these files from Linux once it is installed? Should I do anything to the drive before using it? And finally, a lot of the files are .rar files. Should they be unzipped first or does it make any difference? This may be just the first in a long line of questions but try to bear with me. Thanks. Heavy

---

### Post by taurus on 2009-12-26
You should be able to access those files from your USB drive from Ubuntu.  Just plug it in and it should automount for you.  Just don't forget to use the safely remove hardware option in windows to unmount it before you unplug it (same as in Ubuntu, right click the icon on the desktop).

There is unrar in Ubuntu that can unrar your files.  Just install it from the repos.

---

### Post by jflaker on 2009-12-26
> **heavyd5 said:**
> I am about to install Ubuntu on my machine that already has Windows XP installed. I have about 100 gb of media files that I want to put on a usb external hard drive to free some space for the Ubuntu install. Will I be able to access these files from Linux once it is installed? Should I do anything to the drive before using it? And finally, a lot of the files are .rar files. Should they be unzipped first or does it make any difference? This may be just the first in a long line of questions but try to bear with me. Thanks. Heavy

You should be able to access the files.  FAT32 is likely your best bet to ensure readability between windows and Linux...There are extras you can add to Linux to enable NTFS access...

I have an external drive that used to be in a laptop, now is in a USB enclosure, I add/read files between my work and home (XP and Ubuntu respectively) all the time.

---

