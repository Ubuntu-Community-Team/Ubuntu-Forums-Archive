---
title: "Complete System &amp; Setting Backup"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by tanmoykrthakur on 2010-12-17
tell me the process or application for Complete System & Setting Backup, which i use on system failure or virus infection or unknowingly change system setting which create a problem

---

### Post by JC Cheloven on 2010-12-17
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)
Consider always having a look on the ubuntu contributed docs when you face a problem, it's a great source of info ;)

Or, depending on your needs, something as [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
fsarchiver comes in [system rescue cd]("http://www.sysresccd.org/Main_Page"), if you like to use that.

---

### Post by K.J. on 2010-12-17
I highly recommend Duplicati ([http://code.google.com/p/duplicati/]("http://code.google.com/p/duplicati/")).

It's just a clone of duplicity, but also has a nice graphical interface and is cross-platform. It supports incremental and full backups. It doesn't have all the bells and whistles required for an enterprise solution like Amanda, but has plenty for the home user.

It uses rsync on the backend for the heavy lifting and I have had 0 problems with it.

---

### Post by seawolf167 on 2010-12-17
I highly recommend creating an image of your hard drive every so often just in case the hard drive fails or similar, you can simply burn the image to a new drive without worrying about reinstalling everything (especially if you are dual booting).
[URL="http://clonezilla.org/"]
http://clonezilla.org/[/URL]

If you want to get your hands dirty, [read about using tar here]("https://help.ubuntu.com/community/BackupYourSystem/TAR").

There are GUI programs available as well, for example, [Sbackup ]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")is a GUI that creates full & incremental backups (and schedules backups and stores in a log pattern for you)

---

