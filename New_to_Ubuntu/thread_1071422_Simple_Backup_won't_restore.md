---
title: "Simple Backup won't restore"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Oliverkat on 2009-02-16
I have installed Ubuntu 8.10 on my main PC, with Pentium D dual-core 300Gb processor and 2Gb of RAM. I have had lots of trouble making it work properly, culminating in a complete system crash and reload, but I wasn't too worried because I had all my data backed up on external hard disk using sbackup. The problem comes now that it's all up and running, because sback will not restore anything – not even one file at a time. It “greys out” even though it isn't using more than 50% of the processor or a lot of RAM, then when it's finished all I have is an empty temp file where the restored file should be. I have also got Intrepid on a second computer on dual-boot, and with the relevant directories remade there too the result is the same, but without the “greying out”

I know the files are there, because sback lists them. I have tried re-installing it several times. Help!

---

### Post by celticbhoy on 2009-02-16
I dont use sbackup, but looking at the sourceforge page it says that it stores the files as .tgz archives, could you not manually extract the files???

---

### Post by freesitebuilder on 2009-02-16
I had terrible trouble with sbackup - it doesn't seem to tell you if a backup was successful or not. And when I came to restore, I found the answer was *not* - I had no backup. :( It also uses a lot more disk space than I wanted to!

I'm trying grsync at the moment, and also looking at remastersys.

---

### Post by Oliverkat on 2009-02-16
> **celticbhoy said:**
> I dont use sbackup, but looking at the sourceforge page it says that it stores the files as .tgz archives, could you not manually extract the files???

Hmmm I tried that with several different programmes, but all of them go through the extracting procedure then announce that - for one reason or another - they are unable to open, or the file is broken, or somesuch

Update: I have managed to recover nearly all system and config files by taking small bites at it, but the most important (to me) .doc and .odt files steadfastly refuse to return, and the program crashes even with just one file. Unfortunately after the last attempt it has now stopped recovering anything again. It would seem that the large amount of resources are being used by Gzip long after sbackup has been shut down

---

### Post by Oliverkat on 2009-02-26
After a lot more research I found that this is a known bug in sbackup - if the file is too big it just doesn't completely back it up, which renders the whole folder scrap. Unfortunately it doesn't give any error message

This is quite a problem with FAT32 backup disks, because if the backup is more than 4Gb sbackup looks as if it's done the job, but actually the whole backup is corrupt and parts of it won't restore

So the messqage is don't use sbackup unless you're happy to lose your data

---

### Post by lswest on 2009-02-26
> **Oliverkat said:**
> So the messqage is don't use sbackup unless you're happy to lose your data

No, not quite right.  The backup disk just can't be formatted as FAT32, which has a maximum file size of 4GB.  NTFS, ext3, jfs, etc. all have no issues with files larger than 4GB.  I would recommend just copying the contents of the backup disk onto another drive, reformatting it at NTFS and copying the contents back over.  Then it works.

---

### Post by kevinatkins on 2009-02-26
Sorry to hear of your sbackup woes Oliverkat.. I'm not fond of that program, either.

This may seem like 'overkill' if you're backing up a single PC, but what I'd suggest is looking at 'BackupPC' - it's what I use, and it's far and away the best backup system I've ever used, on Windows or Linux, free or otherwise. You'll need an external drive capable of being formatted as ext3, or why not pop a second hard drive into your desktop case purely for backup duties. BackupPC can backup a network of machines (including Windows clients), or just use it to backup your local PC - there are a few howto's out there - you may need to consult them because it's quite a serious bit of software. But well worth it once it's set up!

---

