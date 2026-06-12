---
title: "backup help"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by natman on 2009-11-08
Hello,
I wish to start making backups of my laptop in a smart way ( ie better than drag and drop into external drive ). What are the best opinions in linux for this, i have heard of backula and rsync are they good? any good guide online if i end up using a terminal program. 
I am using Kubuntu  incase there is any nice KDE interface outthere.

Thanks:
Patrick

---

### Post by bluelamp999 on 2009-11-08
Take a look at Back In Time - [http://backintime.le-web.org/](http://backintime.le-web.org/)

Can't say what it looks like in KDE...

---

### Post by natman on 2009-11-08
Back in time seems to more of a roll back utility. All i want is to back up Document , music and few other folders in /home each week. In such a way that i dont waste time rewriting stuff that hasnt changed. any ideas?

---

### Post by mapes12 on 2009-11-08
I use Grsync to a separate, removable HDD. It only backs up stuff that has changed therefore very quick. You can use the Advanced tab to exclude stuff that you don't need. I exclude these 2 hidden files like this ```
--exclude=/.gvfs --exclude=/.thumbnails
```or you could exclude all the hidden stuff like this ```
--exclude=/.*
```which is a good option if you just want to backup your viewable Documents, Music etc. 

Grsync is in Synaptic.

---

### Post by entropy1 on 2009-11-08
I like rsync.  I wrote the script below to back up several different things to an external USB-connected hard drive.  Use "man rsync" to learn about rsync, in particular the "--delete" option, to make sure it is what you want.  Use "-n" to do a dry run.

The basic command
```
rsync -a /home/myname/dir /media/Iomega_HDD/rsyncBackups

```
puts the /dir directory in the /rsyncBackups directory so that you end up with /media/Iomega_HDD/rsyncBackups/dir containing your stuff.

In contrast, the extra / in
```
rsync -a /home/myname/dir/ /media/Iomega_HDD/rsyncBackups
```
puts the contents of the /dir directory in the /rsyncBackups directory; no /dir subdirectory is created in the rysncBackups directory.

Here is the basic script.  In backing up my Ubuntu files, I don't want to backup most hidden files, but there are some .files and .directories that I do want to backup.  That's why it's important to have the include options **before** the option to exclude all .files.

```
#! /bin/bash
# Backup Ubuntu
rsync -a --progress --delete \
--log-file=/home/myname/Desktop/$(date +%Y%m%d)_rsync.log \
--include=".gconf/" \
--include=".gnome2/" \
--include=".mozilla/" \
--include=".mozilla-thunderbird/" \
--include=".bashrc" \
--include=".gnomerc" \
--exclude=".*" \
--exclude="*Cache*" \
--exclude="softwareLinux/" \
/home/myname /media/Iomega_HDD/rsyncBackups


# Backup Flash Drive
rsync -a --progress --delete \
--log-file=/home/myname/Desktop/$(date +%Y%m%d)_rsync.log \
--exclude="*Cache*" \
--exclude="*.mov" \
/media/NAME_PRSNL/Documents/namehome /media/Iomega_HDD/rsyncBackups


# Backup Windows
rsync -a --progress --delete \
--log-file=/home/myname/Desktop/$(date +%Y%m%d)_rsync.log \
--exclude="*Cache*" \
/media/C/Users/Name/Documents /media/Iomega_HDD/rsyncBackups/C_Users_Name

rsync -a --progress --delete \
--log-file=/home/myname/Desktop/$(date +%Y%m%d)_rsync.log \
--exclude="*Cache*" \
/media/C/Users/Name/Downloads/downloadedDocuments /media/Iomega_HDD/rsyncBackups/C_Users_Name/Downloads
```
Before running the above script, you need to create the /rsyncBackups directory.  Inside that, you need to create the /C_Users_Name directory, and inside that you need to create the /Downloads directory.

---

### Post by dox_drum on 2009-11-08
I've just read in a magazine about couple of programs.

[COLOR="Navy"]KEEP[/COLOR]: programs your backup... so you can forget about doing it any week or so.

[COLOR="navy"]YADSync[/COLOR]: synchronizes folders (like the already suggested rsync).

You could try them... and comment you experience.

[CENTER]Regards.[/CENTER]

---

### Post by Norm24 on 2009-11-08
Grsync works fine for me.

---

### Post by Paqman on 2009-11-08
Once you've got a backup script that you like, you can just drop it into the appropriate folder in /etc/cron.daily/hourly/whatever to have anacron do the backup automatically.

---

### Post by coffee on 2009-11-13
I have a rsync script in Python that is working well for me.  It has 3 files the main backup.py and restformat.py used to formate my title and subtitles in the log file and backupexcluded.txt with the directories I do not what to backup.

**_backup.py_**
```
#!/usr/bin/python

import os
from time import asctime
import restformat

#Variables
backupruntime = asctime()
sourcedir = "/home/coffeeboy/"
backupdir = "/media/FreeAgent/backup/"
incrementsdir = '/media/FreeAgent/backup-increments/' + backupruntime

#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.title(backupruntime))
print >> backuplog, ('Making increments directory: "' + incrementsdir + '"\n')

#Make incrementsdir
os.mkdir(incrementsdir)

#Logging
print >> backuplog, (restformat.subtitle('BEGIN BACKUP'))
backuplog.close()

#Run rsync backup command with Linux logging
os.system('rsync -arEtb --delete --stats --log-file-format="%i %o %f %n" --exclude-from=/home/coffeeboy/bin/backupexcluded.txt --backup-dir=' + '"' + incrementsdir + '" ' + sourcedir + ' ' + backupdir + ' >> ' + '/media/FreeAgent/rsync-backup.log')


#Logging
backuplog = open('/media/FreeAgent/rsync-backup.log', 'a')
print >> backuplog, (restformat.subtitle('END BACKUP'))
print >> backuplog, ('\n\n')
backuplog.close()
```

enter your username for all *coffeeboys* and change */media/FreeAgent* to you desired backup location.  You will need to mkdir both an backup-increments folder and a backup folder and creat a rsync-backup.log in the backup location.


**_restformat.py_**
```
#!/usr/bin/python

def title(mytitle='reStructueredText Title'):
    'Retuns mytitle formatted as a restructeredText tilte.'
    return '======================================='+'\n'+ mytitle + '\n' + '======================================='

def subtitle(mysubtitle='reStructeredText Subtitle'):
    'Returns mysubtitle formatted as a reStructeredText substring.'
    return mysubtitle + '\n' + '---------------------------------'
```

This formates the title and subtitle lines used in the log file.

The *backupexcluded.txt* file is a list of all visible and hidden files and folders (one per line) that I do not want to backup. [i.e. I do not backup up my .VirtualBox directory because of the size.

[B]
An example log file output:[/B]
=======================================
Fri Nov 13 12:23:01 2009
=======================================
Making increments directory: "/media/FreeAgent/backup-increments/Fri Nov 13 12:23:01 2009"

BEGIN BACKUP
---------------------------------

Number of files: 14088
Number of files transferred: 4
Total file size: 9327826172 bytes
Total transferred file size: 767443 bytes
Literal data: 767443 bytes
Matched data: 0 bytes
File list size: 328252
File list generation time: 0.003 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 1111946
Total bytes received: 16066

sent 1111946 bytes  received 16066 bytes  150401.60 bytes/sec
total size is 9327826172  speedup is 8269.26
END BACKUP
---------------------------------

---

