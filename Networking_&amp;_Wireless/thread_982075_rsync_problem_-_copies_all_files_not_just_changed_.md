---
title: "rsync problem - copies all files not just changed files"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Littleton on 2008-11-14
Hi,

I'm hoping someone can shed some light on a problem I'm having with rsync whilst backing up my home directory to a network attached drive.

I run the following command:

rsync -av --delete --exclude=NAS/ --exclude=Videos/ --exclude=".*"  /home/ciaran/ /home/ciaran/NAS/Backups/Blue

and the directories & files are copied to the NAS drive as expected.  However, if I re-run the command immediately after it has finished rysnc starts to copy ALL of the files a second time.  Given that rsync is supposed to copy only the changes in a file and that none of the files were changed I wouldn't have exepcted any files to be copied.

Am I missing something?  Any ideas are very much appreciated.

Thanks in advance,

Ciaran

---

### Post by sockrebel on 2008-12-23
are you copying to a FAT32 filesystem?

seems to be a common problem on those systems.
[http://ubuntuforums.org/showpost.php?p=1218110&postcount=26](http://ubuntuforums.org/showpost.php?p=1218110&postcount=26)

---

