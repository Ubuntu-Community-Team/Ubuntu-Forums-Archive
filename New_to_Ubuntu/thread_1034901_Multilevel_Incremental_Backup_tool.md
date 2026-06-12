---
title: "Multilevel Incremental Backup tool"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by any.linux12 on 2009-01-09
HI

I need a tool do make Multilevel Incremental Backup tool. 

> 
Multilevel incremental

A more sophisticated incremental backup scheme involves multiple numbered backup levels. A full backup is level 0. A level n backup will back up everything since the most recent level n-1 backup. Assume a level 0 backup was taken on a Sunday. A level 1 backup taken on Monday would only include changes made since Sunday. A level 2 backup taken on Tuesday would only include changes made since Monday. A level 3 backup taken on Wednesday would only include changes made since Tuesday. If a level 2 backup was taken on Thursday, it would include all changes made since Monday because Monday was the most recent level n-1 backup.

from wikipedia.org

---

### Post by kristofer_l on 2009-01-09
Perhaps this could be done with rsync?
[http://rsync.samba.org/](http://rsync.samba.org/)
[http://en.wikipedia.org/wiki/Rsync](http://en.wikipedia.org/wiki/Rsync)

---

### Post by hyper_ch on 2009-01-09
rsync and hardlinks...

---

### Post by any.linux12 on 2009-01-12
I need some more help. I know how to use rsync but not with multilevels. And how do I use hardlinks??

thanks!

---

### Post by any.linux12 on 2009-01-12
Hi!

I found a nice tool in the synaptic package manager, flexbackup, and I think it works like I want. Anyway should be nice to have a tutorial in this forum...if it works with me I promiss I do something but maybe I'm not the right person..lol
:lolflag:

---

### Post by talsemgeest on 2009-01-12
I have a feeling this might be exactly what you are looking for: [https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by hyper_ch on 2009-01-12
you use somethign like this:

```

#!/bin/bash
unset PATH

# USER VARIABLES
BACKUPDIR=/backup        # Folder on the backup server
MYSQLUSER=root
MYSQLPWD=**********************
MYSQLHOST=localhost
MYSQLBACKUPDIR=/mysql_backup
EXCLUDES=/backup/backup_exclude        # File containing exludes
DAYS=90         # After how many days shall the backups be deleted?

# PATH VARIABLES
CP=/bin/cp;
MK=/bin/mkdir;
DATE=/bin/date;
RM=/bin/rm;
GREP=/bin/grep;
MYSQL=/usr/bin/mysql;
MYSQLDUMP=/usr/bin/mysqldump;
RSYNC=/usr/bin/rsync;
TOUCH=/bin/touch;
FIND=/usr/bin/find;

##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##

# CREATING CURRENT DATE / TIME
$MK $BACKUPDIR/current
$MK $BACKUPDIR/old
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
MKDIR=$BACKUPDIR/old/$NOW/
$MK $MKDIR

# CREATE MYSQL BACKUP
# Remove existing backup dir
$RM -Rf $MYSQLBACKUPDIR

# Create new backup dir
$MK $MYSQLBACKUPDIR

#Dump new files
for i in $(echo 'SHOW DATABASES;' | $MYSQL -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST|$GREP -v '^Database$'); do
  $MYSQLDUMP                                                    \
  -u$MYSQLUSER -p$MYSQLPWD -h$MYSQLHOST                         \
  -Q -c -C --add-drop-table --add-locks --quick --lock-tables   \
  $i > $MYSQLBACKUPDIR/$i.sql;
done;

# RUN RSYNC INTO CURRENT
$RSYNC                                                          \
        -avzp --delete --delete-excluded                        \
        --exclude-from="$EXCLUDES"                              \
        /                                                       \
        /$BACKUPDIR/current ;

# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current

# MAKE HARDLINK COPY
$CP -al $BACKUPDIR/current/* $MKDIR

# REMOVE OLD BACKUPS
for file in "$( $FIND $BACKUPDIR/old/ -maxdepth 1 -type d -mtime +$DAYS )"
do
  $RM -Rf $file
done

exit 0

```

remove the mysql part if it's not needed...

---

### Post by any.linux12 on 2009-01-12
hey!

I'm greatfull for the support but I can't find nothing like I want and I'm sorry was my misstake in the 1° thread couse I thought I wanted a multilevel backup but doesn't work like I want :-( and I'm getting depressed couse I realy need that and I already lost a lot of time.

So what I want is a backup system that makes a full backup Saturday (for ex.)

then on Monday after work it will check which file were moddified and then will backup those files. And then the same for tuesday ... until fryday then Saturday another fullbackup. 

I know that the name is incremental backup but I never saw any that works like my idea.

> ex.
Saturday   ( doc1 doc2 doc3 ) ( c++1 c++2 c++3 ) ( jpg1 and jpg2 )
.
.
.
files doc1 and c++2 were moddified
Monday  (doc1) (c++2) just that....

Is that possible??????

---

### Post by hyper_ch on 2009-01-12
looked at what I posted?

---

### Post by any.linux12 on 2009-01-12
ups! sorry I will try. Danke
Where do I save that??

---

### Post by any.linux12 on 2009-01-12
I need some more help (sorry I'm new in Here). Where do I chose the files to backup??

---

### Post by beercz on 2009-01-12
has anyone looked at [http://rsnapshot.org](http://rsnapshot.org)

I use it all the time.

---

### Post by hyper_ch on 2009-01-12
> **any.linux12 said:**
> I need some more help (sorry I'm new in Here). Where do I chose the files to backup??

had a look at that script?

---

### Post by any.linux12 on 2009-01-12
ok but I not seeing some thing. Is that some kind of conf?
where is the folder include?

---

### Post by any.linux12 on 2009-01-12
hmm. So now the script is running thanks but is copying all my "/". I just want to backup /esp-server-data for example.

and I'm still not sure about the multilevels but lets try

---

### Post by any.linux12 on 2009-01-12
Man!! I think you made me lose my time. The program is running, but I always creates a folder with all data, like:


> ex.
Saturday ( doc1 doc2 doc3 ) ( c++1 c++2 c++3 ) ( jpg1 and jpg2 )
.
.
.
files doc1 and c++2 were moddified
Monday ( doc1(version2) doc2 doc3 ) ( c++1 c++2(version2) c++3 ) ( jpg1 and jpg2 )....

and I wanted

> ex.
Saturday ( doc1 doc2 doc3 ) ( c++1 c++2 c++3 ) ( jpg1 and jpg2 )
.
.
.
files doc1 and c++2 were moddified
Monday (doc1) (c++2) just that....

Please correct me if I'm wrong but I think that doesn't work

---

### Post by hyper_ch on 2009-01-12
I have no clue what you want... I can't understand those examples you give up there

---

### Post by Tews on 2009-01-12
Have a look at Quick Start...[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11).. sounds like just what you need

---

### Post by ChildOfMana on 2009-01-12
You can also try [Back-In-Time]("http://www.le-web.org/back-in-time/").

This is a GUI program that is very easy to use.

The premise is basically that the first time you run it it will make a complete 'snapshot' of the directory or directories you specify and back them up to a location of your choosing (you can even specify NFS shares and external storage). After the initial snapshot it will monitor the directories for any changes and will back-up *only* the changed files. You can specify the frequency of the back-ups and it runs in the background to keep tabs on the schedule.

To install you need to add the repository to your sources.list file.

Open a Terminal and type;

> sudo gedit /etc/apt/sources.list

Then append the following to your sources.list file (but just the line that corresponds to your version of Ubuntu - and not the bit in bold);

> **for Hardy**
deb [http://le-web.org/repository/stable](http://le-web.org/repository/stable) hardy/

**for Intrepid**
deb [http://le-web.org/repository/stable](http://le-web.org/repository/stable) intrepid/

then save the file and type the following into a Terminal;

> sudo apt-get update && sudo apt-get install backintime-common backintime-gnome

Once installed you should find the application under 'Applications > System Tools'

---

### Post by any.linux12 on 2009-01-12
I like to have such a very good support but sometimes is a little to much. I don't want a simple Gui backup software. I want a complex terminal multilevels backup application with scripts that I can configurate. I don't want to be missunderstand but I also don't like to lose my time with simple applications like "Back in time"

---

### Post by scorp123 on 2009-01-12
> **any.linux12 said:**
> I don't want a simple Gui backup software. Then please read here and learn:

"How to backup your stuff UNIX-style"
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)


EDIT: Having the commands (see link) perform an incremental backup instead of a full backup (I'm paranoid; I therefore prefer full backups) is just a matter of slightly modifying some of the parameters of "tar".

---

### Post by any.linux12 on 2009-01-12
But I don't think that is possible to backup 200GB everyday for 3 mounths (that my goal to have restoring material for 3 mounths), so thats why I need some special incremental differencial multilevel thing whatever. This is not even for me I don't backup :)

---

### Post by scorp123 on 2009-01-12
> **any.linux12 said:**
> But I don't think that is possible to backup 200GB everyday Why not? 200 GB is not much, not by a wide stretch :D

My laptop has a 250 GB disk. A complete backup takes less than one hour (I backup to an external USB disk). A complete backup, total wipe (simulating catastrophic failure where everything is lost) and complete restore takes me about two hours ... and most of the time is lost for copying the data back.

So you say you want a daily backup of 200 GB? Well that should be easy :D  You make a first full backup, and make sure you keep it safe somewhere, e.g. put it on magnetic tape, and then lock the tape away into a bank safe. From there on you make incremental backups which from there onwards should take less time than a full backup.

If you schedule that e.g. around midnight every day ... I fail to see why it should not be possible??

---

### Post by talsemgeest on 2009-01-12
> **any.linux12 said:**
> hey!

I'm greatfull for the support but I can't find nothing like I want and I'm sorry was my misstake in the 1° thread couse I thought I wanted a multilevel backup but doesn't work like I want :-( and I'm getting depressed couse I realy need that and I already lost a lot of time.

So what I want is a backup system that makes a full backup Saturday (for ex.)

then on Monday after work it will check which file were moddified and then will backup those files. And then the same for tuesday ... until fryday then Saturday another fullbackup. 

I know that the name is incremental backup but I never saw any that works like my idea.
Did you check out the link I posted as well?

[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)

---

### Post by scorp123 on 2009-01-12
> **any.linux12 said:**
> I know that the name is incremental backup but I never saw any that works like my idea. Does it have to be Linux?

You could use **OpenSolaris 2008.11** and "TimeSlider". Add a few 1 TB disks and "TimeSlider" and the ZFS snapshots behind it will handle it all for you.

See here:

"ZFS snapshot visualization in GNOME"
[http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs](http://blogs.sun.com/erwann/entry/zfs_on_the_desktop_zfs)

"Time Slider: OpenSolaris 2008.11 Killer Feature"
[http://java.dzone.com/news/killer-feature-opensolaris-200](http://java.dzone.com/news/killer-feature-opensolaris-200)

"Time Slider Screencast"
[http://blogs.sun.com/erwann/entry/time_slider_screencast](http://blogs.sun.com/erwann/entry/time_slider_screencast)

OpenSolaris Download:
[http://opensolaris.org/os/downloads/](http://opensolaris.org/os/downloads/)


OpenSolaris pretty much looks and feels like Linux, eg. there is a GNOME desktop, there is the Nautilus file manager, there is SSH, there is a packet manager which is pretty much a 1:1 "Synaptic" copy ... So from that point of view it should be no problem.

So when you write ....:
> **any.linux12 said:**
>  So what I want is a backup system that makes a full backup Saturday (for ex.) OK, fine - you do this: ```
rsync -av --progress /stuff/you/want/to/backup yourusername@opensolaris:/backup
```

Just make sure TimeSlider is taking snapshots of that. That's it.

> **any.linux12 said:**
>  Then on Monday after work it will check which file were moddified and then will backup those files.  "rsync" already does that automatically. All you need to do is to repeat the command above. "rsync" would only transfer the deltas, the few changes that were made. TimeSlider on OpenSolaris would then auto-archive the changes .... you'd just have to make sure that you have enough disk space. The more the better.

Most of this stuff -if not even all of it- could also more or less easily be achieved on Ubuntu. e.g. hyper's method which he already mentioned early on in this thread. I kindly suggest that you should read what people suggest to you and not just write "this is not what I want" when it is evident that you haven't even read the suggestion, let alone: tried it out. ;)

---

