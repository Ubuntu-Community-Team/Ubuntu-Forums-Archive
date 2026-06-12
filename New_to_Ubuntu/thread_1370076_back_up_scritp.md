---
title: "back up scritp"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-01-01
i want to be able to split the file into 659mb size so far i have after i have the script i want to be able to run it with crontab once a month or so

#!/usr/bin/bash
tar -cjvf /home/lance/backup/archive`date +%m%d%Y`.tar.bz2 /home/lance/bashscripts  /home/lance/.avast /home/lance/.config/deluge /home/lance/.gnome2/nautilus-scripts

the archive will be stored in my backup folder in my home dir with the current date as part of the file name. the listing that follow after .bz2 are the folders or files i want backup. i found [http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06](http://maketecheasier.com/how-to-compress-and-split-files-in-ubuntu/2008/10/06) it give dirttion on how to do split a single video file

---

### Post by Max_Mackie on 2010-01-01
To archive your system, run something along these lines:

```
tar -cvpzf backup.tar.gz -–exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media / 
```To split the archives, 

(after creation of backups)
```
split -d -b 3900m /path/to/backup.tar.gz /name/of/backup.tar.gz.

```(during creation of backups)
```
tar -cvpz <put options here> / | split -d -b 3900m - /name/of/backup.tar.gz.

```If you want to cron this task, make a new crontask and make it run on a monthly basis:

```

cron -e

``````
@monthly <command>
```Hope that helps.
Sources: 
[http://crunchbang.org/archives/2007/10/26/howto-setup-a-crontab-file/](http://crunchbang.org/archives/2007/10/26/howto-setup-a-crontab-file/)
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

