---
title: "Backing up Home folder"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-17
I have Linux Mint 6, and a couple people have brought the fact up that if I back up my home folder, that I can basically have my files (other than actual programs) after doing a fresh install for upgrading the OS.

Can anyone explain how I would go about doing this? And where should I back it up to (flash drive, partition, etc.)

Thanks!

---

### Post by Therion on 2008-12-17
My suggestion would be to use Quickstart:

[http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html](http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html)

---

### Post by adobrakic on 2008-12-17
Thanks!
I'll try it and see how it goes.
:D

---

### Post by adobrakic on 2008-12-17
Okay, I've installed it, but it seems kinda confusing. 
I just wanna be able to have stuff like my firefox bookmarks, settings and pw, terminal aliases, etc. I don't wanna back up the actual programs, cause those arent too hard to download.

Not too sure how to get where I want from here.
:X

---

### Post by evilkastel on 2008-12-17
Quickstart is cool, but for the big picture you better backup your files and in the next upgrade, you should make a separate partition for your data. mos users set a / partition and a /home partition. I prefer a / and a /data , since home contains a lot of configuration files. Still by making a separate partition you'll save some time in the future, and it is just easier.  for config backup you need to do one of this:
There are many ways to back your system up. Here's a few: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) , [https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto) , [https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup) , [https://help.ubuntu.com/community/MondoMindi](https://help.ubuntu.com/community/MondoMindi)

---

### Post by Therion on 2008-12-17
> **adobrakic said:**
> I just wanna be able to have stuff like my firefox bookmarks, settings and pw, terminal aliases, etc. I don't wanna back up the actual programs, cause those arent too hard to download.
Well...  You asked how to backup your Home folder not how to save your bookmark's. 


> **adobrakic said:**
> Not too sure how to get where I want from here.
Me either.

---

### Post by donkyhotay on 2008-12-17
Personally when I'm getting ready to wipe my system I just store my entire /home folder on whatever backup media I'm using (usually a burnt DVD) and then copy over my personal files and preferences for my most important programs from the backup after doing the wipe. This isn't the nicest or cleanest way of doing a backup but it's fast and effective for the occasional wipe. The programs I reinstall from the repos after reformat is complete.

---

