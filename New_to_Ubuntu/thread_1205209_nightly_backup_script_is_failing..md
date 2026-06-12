---
title: "nightly backup script is failing."
date: 2009-07-05
forum: New to Ubuntu
---

### Post by ant2ne on 2009-07-05
I'm executing my script with root's cron
```
ant2ne@2ne-buntu:/backup$ sudo crontab -l
# m h  dom mon dow   command
1 23 * * * /bin/bkupnow.sh
11 19 * * * /etc/webmin/cron/tempdelete.pl

```
here is my script
```

ant2ne@2ne-buntu:/backup$ cat /bin/bkupnow.sh
#!/bin/sh
chown -R ant2ne:root /backup/*
chmod -R 771 /backup/*
tar cvpf  /backup/media/pictures.tar /data/shares/media/pictures
tar cvpf  /backup/media/MorePictures.tar /data/shares/media/MorePictures
tar cvpf  /backup/media/music.tar /data/shares/media/music
tar cvpf  /backup/mandi.tar /data/shares/mandi

date >> /backup/log.txt
ls -l /backup/*.tar >> /backup/log.txt

chown -R ant2ne:root /backup/*
chmod -R 771 /backup/*
ant2ne@2ne-buntu:/backup$ 
```
The script executes, but creates target .tar files, but with 0kb of size. I'm thinking this is a permissions issue.
```
ant2ne@2ne-buntu:/$ ls -l | grep back
drwxrwx---   6 ant2ne root        4096 2009-07-01 23:01 backup
ant2ne@2ne-buntu:/$ ls -l /back*
total 24789200
-rwxrwx--x 1 ant2ne root 25359308800 2009-07-01 23:03 ant2ne.tgz
drwxrwx--x 2 ant2ne root        4096 2009-06-21 08:54 archive
-rwxrwx--x 1 ant2ne root        4348 2009-07-04 23:01 log.txt
drwxrwx--x 2 ant2ne root       16384 2009-05-25 16:33 lost+found
-rwxrwx--x 1 ant2ne root           0 2009-07-04 23:01 mandi.tar
drwxrwx--x 2 ant2ne root        4096 2009-07-05 17:41 media
ant2ne@2ne-buntu:/$ 

```

---

### Post by Boondoklife on 2009-07-05
Might I suggest adding >> /logfilehere to each of the lines so that you can capture what is going on. Make sure the first line that captures has a > instead of >>

```
echo `date` > /logfilehere
tar cvpf tar.tar >> /logfilehere
```

---

### Post by ant2ne on 2009-07-06
Thanks for that suggestion. I went ahead and made that change. As you can see though, the log.txt section already screwed as it wont list the contents of /backup/media/*  I'm more interested in fixing the 0 file size problem before fine tuning the log section.

---

### Post by dixonstalbert on 2009-07-06
some things to try;

1. split the script into a chunk that does chown and chmod, and one that does the tarring. run the chown/chmod script then examine the directory permissions to see if it does what you want. If it is okay then try the tar script and see if that is problem where lies.

2. Not sure if it is still a problem, but tar used to choke if target file started with a forward slash; you had to cd into the directory where you wanted the archive to end up and then run tar command. maybe try this if first test shows its a tar problem.

3. here is the backup script I am using right now. first comment shows where I got it from. I currently have commented out the lines for separate /home /var and /usr backups because my current install has all these mounted under root directory.

hope this is helpful

```
#!/bin/bash

#based on http://linuxmint.com/forum/viewtopic.php?t=3969 
#need to be root to run this
# ***and you need to be in directory where you want these


dpkg --get-selections > packagelist.txt
#tar --one-file-system -pzcvf BootFS_backup.tar.gz /boot
tar --one-file-system --exclude=/tmp/* --exclude=/dev/* --exclude=/home/dixon2/.thumbnails/* --exclude=/home/dixon2/.Trash/* --exclude=/proc/* -pzcvf mintbackup.tar.gz /
#tar --one-file-system --exclude=/var/tmp/* -pzcvf VarFS_backup.tar.gz /var
#tar --one-file-system -pzcvf UsrFS_backup.tar.gz /usr
#tar --one-file-system -pzcvf HomeFS_backup.tar.gz /home

```

---

### Post by Boondoklife on 2009-07-06
Riiight that is why I suggested the addition as it is prolly a tar issue (rights,location,syntax,etc)

What does your log show now that you have added those lines?

---

### Post by ant2ne on 2009-07-06
> **dixonstalbert said:**
> some things to try;

1. split the script into a chunk that does chown and chmod, and one that does the tarring. run the chown/chmod script then examine the directory permissions to see if it does what you want. If it is okay then try the tar script and see if that is problem where lies.

2. Not sure if it is still a problem, but tar used to choke if target file started with a forward slash; you had to cd into the directory where you wanted the archive to end up and then run tar command. maybe try this if first test shows its a tar problem.

3. here is the backup script I am using right now. first comment shows where I got it from. I currently have commented out the lines for separate /home /var and /usr backups because my current install has all these mounted under root directory.

1. Ok, did that. the chown chmod section seems to be working fine. I've got that section, mainly because i think my tar section's problem is a permissions issue. I'll probably do away with it, or tighten the permissions once i get the tar part to work.

2. That actually sounds plausible. I've modified my script to cd /backup before executing, and then all tar are written strait to that directory.

3. I'm curious about the --one-file-system parameter. I've gone ahead and used it, but I don't think I need it.

my current script
```
ant2ne@2ne-buntu:/backup$ cat /bin/bkupnow1.sh
#!/bin/sh
cd /backup

dpkg --get-selections > packagelist.txt
#tar pcvpf  ant2ne.tar /data/shares/ant2ne
#tar pcvpf  open.tar /data/shares/open
tar --one-file-system pcvf pictures.tar /data/shares/media/pictures
tar --one-file-system pcvf MorePictures.tar /data/shares/media/MorePictures
tar --one-file-system pcvf music.tar /data/shares/media/music
tar --one-file-system pcvf mandi.tar /data/shares/mandi


echo 'date' > /backup/log.txt
#date >> /backup/log.txt
ls -l /backup/*.tar >> /backup/log.txt

```I'll go ahead and let cron run this tonight and report back in the morning.

---

### Post by Boondoklife on 2009-07-06
Correct me if I am wrong but the one-file-system make sure that it does not follow mounts and symlinks to other filesystems

---

### Post by ant2ne on 2009-12-22
ok, after lots of struggle, i got it to work. I put the final script on my blog site. [http://www.ant2ne.com]("http://www.ant2ne.com/?p=48") To make a long story short do not try to tar accross volumes. It seems to cause problems. Also ```
tar cvpjf ant2ne.tar.bz2 ./ant2ne
```is not the same as ```
tar cvpjf ant2ne.tar.bz2 ./ant2ne/*
``` the first one was failing on me a few MB to a few hundred MB into the process.

---

