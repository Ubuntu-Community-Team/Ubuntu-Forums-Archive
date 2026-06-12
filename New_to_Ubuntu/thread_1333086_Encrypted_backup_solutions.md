---
title: "Encrypted backup solutions"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-11-21
I've been using Areca for most of the year until I started having issues with it a couple of months ago.

Anyway, wondering what else there is besides Areca that provides encrypted backups. Have been using file backup manager but can't see any encryption option with it. Any ideas appreciated.

---

### Post by lavinog on 2009-11-21
7z can create encrypted archives.

---

### Post by LunaticHiatus on 2009-11-21
If your looking for encrypted online backup. Ubuntu offers one wit Ubuntu One.

---

### Post by lavinog on 2009-11-21
Spideroak also offers encrypted online backups.
Currently Ubuntu one requires that you move everything to your ubuntu one folder.

---

### Post by paulchinnz on 2009-11-21
Thanks for the suggestions. I guess with my substandard interwebs access and >30GB to backup cloud backups are not really what I'm after. Anyway, clouds depend on internet access, and I'm after a solution that allows backups on to my USB pen drive for access anywhere there's a USB port.

Is 7z actually 7zip? I couldn't find 7z otherwise.

---

### Post by paulchinnz on 2009-11-21
Using deja dup backup. Doesn't memorise multiple backup protocols but looks to be doing the job.

---

### Post by lavinog on 2009-11-22
> **paulchinnz said:**
> 
Is 7z actually 7zip? I couldn't find 7z otherwise.
yes

---

### Post by Puzzled Guy on 2009-11-22
Install 7-zip with:
```
sudo apt-get install p7zip-full
```
Then right-click the backup and choose "create archive"

Then choose tar.7z as the compression method (with tar, the file permissions will be preserved)

Expand "Details"
Here you can choose to add a password (creating a password is optional but if you want it encrypted, go ahead!)

Hope this helps

---

### Post by paulchinnz on 2009-11-23
Thanks for the 7z suggestion. What's the difference between this and simply using rar with password and encryption of the file list?

---

### Post by lavinog on 2009-11-23
> **paulchinnz said:**
> Thanks for the 7z suggestion. What's the difference between this and simply using rar with password and encryption of the file list?

pretty much the same. 7z is open source.

---

