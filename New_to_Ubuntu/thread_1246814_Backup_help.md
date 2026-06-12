---
title: "Backup help"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by kc9jse on 2009-08-22
I am new to Ubuntu and would appreciate some help with backing up my system. I have 3 questions.

1). I am going to backup to a hard drive on another machine that is running Windows XP. How do I automatically mount that drive?

2) What software do you recommend to use. I would like to have increment as well as an occasional full backup.

3) What do I need to backup. I am new and don't totally understand the file system yet.

Thanks, 
Al

---

### Post by khelben1979 on 2009-08-22
I actually don't do any backups at the present (except my blog), but I made a simple google search and [here's the result]("http://linux.about.com/od/softbackup/Linux_Software_Backup_Solutions.htm"). You can also use Wikipedia if you feel uncertain about these programs.

Then you have the famous SourceForge.Net. Made a search over there as well, [look here]("http://sourceforge.net/search/?type_of_search=soft&words=backup").

---

### Post by Sidewinder1 on 2009-08-22
You may want to check into *Grsync*, it's a GUI front end to the rsync command that can be issued in your terminal, open a terminal and type:
```
man rsync
```
to view all of the options available.
IMHO you only need to back up your *Home* directory as, if anything borks the ubuntu OS, you can simply reinstall Ubuntu and update. Or, of course, you could back-up the entire drive if you wish...
Side

---

### Post by mapes12 on 2009-08-22
Backups can be easier if you have /home on its own partition:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then you have all kinds of options for backing up "/" and /home. I use Partimage for "/" and Grsync for /home.

Clonezilla is also very good. Particularly if you want to create an image of the entire HDD, including all partitions.

If you use Grsync or any syncing application for /home then beware the hidden .gvfs file. It's caused me all kinds of problems with restoring so I exclude it from the backup routine these days.

If you use Partimage or Clonezilla you will need to understand mounting virtual directories. Clonezilla does it automatically but you still need to understand what's going on. If you need any help on this then please post back.

---

### Post by Zill on 2009-08-22
Welcome to the forums.

1)  Read up on [Samba]("https://help.ubuntu.com/community/SettingUpSamba").

2)  [SimpleBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") (menu System, Administration, Simple Backup Config).

3)  SBackup defaults are quite a good start!  Just remember to change the destination to your newly mounted WinPC folder. ;-)

These are all FAQ's - Google is your friend!

---

### Post by LewRockwell on 2009-08-22
we use Clonezilla

.

---

### Post by Gen2ly on 2009-08-22
All these are good suggestions, personally I prefer rsync too. grsync can be used as a front end.  Generally now because clean installs are sometimes necessary I just backup my documents and configs (and because I have limited hard drive space) with a couple of [tar-helpers]("http://linuxtidbits.wordpress.com/2009/07/18/backup-configurations-with-tar-helpers/").

---

