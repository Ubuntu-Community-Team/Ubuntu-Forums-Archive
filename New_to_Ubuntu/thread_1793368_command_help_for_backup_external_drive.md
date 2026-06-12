---
title: "command help for backup external drive"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by sewbiz on 2011-06-29
What do you type in the terminal to get your files backed up to the e drive?

Thank you for your help!

---

### Post by mobius129a on 2011-06-29
To backup your home directory:

1. change to the directory
```
cd /home
```2. compress the home directory (recommended)```

tar -cvzf homeBak$(date +%d%m%y).tar.gz *
```3. move the zip file to the destination directory
```

mv homeBak$(date +%d%m%y).tar.gz /media/path/to/external/drive

```The external drive is nearly always mounted in either /media or /mnt.

---

### Post by seawolf167 on 2011-06-29
You have a [lot of options]("https://help.ubuntu.com/community/BackupYourSystem"). [Clonezilla]("http://www.clonezilla.org"), tar, rsync, sbackup, etc.

An *rsync *example (assuming the drive is formatted in ext3/4)

```
rsync -r -u --delete-before /source /destination
```then just place that command as a *crontab* entry to run it on a schedule.

---

