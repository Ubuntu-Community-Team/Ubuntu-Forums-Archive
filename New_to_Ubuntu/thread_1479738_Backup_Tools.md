---
title: "Backup Tools?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by McRat on 2010-05-11
Need to do unattended midnight backups of the data directory to another computer on the LAN.

Anyone have a favorite?

---

### Post by tgm4883 on 2010-05-11
rsync

---

### Post by McRat on 2010-05-11
> **tgm4883 said:**
> rsync

Thanks!

Now I just need to find something to package it.  Something like:

```
OnError 100                                                                                

NowDate$ = Date$()

Do
     If NowDate$ <> Date$() then
           Command$("[COLOR=Red]rsync[/COLOR] *.* Z:\backup")
           NowDate$ = Date$()
           Print "Backup successful on "; Date$()
     End If 
  
     Sleep 3600

Loop

100 Print "NFG.  Backup not complete."

End
```What scripting language is going to be the fastest to learn to do simple tasks?

---

### Post by CharlesA on 2010-05-11
I use rsync, but I use it to back to an external drive on the same machine.

The script I use is messy as hell, but it gets the job done.

This one is in a cronjob:

```
#!/bin/bash

ARRAYPATH="/array/"
DOCPATH="/docback/"
DVDPATH="/dvdback/"
DATE=`date +%D`
HOME="/home/charles/"

#Check if /array is mounted and email me if it is not
if ! mountpoint -q $ARRAYPATH
then
   echo "Array is not mounted" | mail -s "RAID Array is not mounted" email@domain.com
else
#Check if /docback is mounted and proceed with backup, otherwise email me that backup failed
if ! mountpoint -q $DOCPATH
then
   mount -t ext3 UUID=f00c8f27-7a11-42b0-96f9-0e04a261d682 $DOCPATH && bash $HOME"docbk"
else
   echo "Backup of Documents Failed for $DATE" | mail -s "Backup of Docs Failed for $DATE" email@domain.com
fi
fi
```

Which calls this script:

```
#!/bin/bash

DATE=`date +%m%d%Y`
DOCPATH="/docback/"
OLDDOCNAME=`cat /docback/latest`
NEWDOCDIR=$DOCPATH$DATE
OLDDOCDIR=$DOCPATH$OLDDOCNAME
DOCLOG=$DOCPATH"log/"$DATE".txt"

cp -al $OLDDOCDIR $NEWDOCDIR && echo $DATE > $DOCPATH"latest" && rsync -ai --delete --log-file $DOCLOG /array/ $NEWDOCDIR && umount $DOCPATH

```

You can probably modify it to fit your needs.

EDIT: What OS is running on the machine you need to backup to?

---

### Post by kalos on 2010-05-11
In short, you can do this:
[QUOTE=jwz]
[Backup] every morning at 5AM by creating a temporary text file containing this line:

0 5 * * * rsync -vaxE --delete --ignore-errors / /Volumes/Backup/

and then doing sudo crontab -u root that-file [/QUOTE]
(From [jwz's backup PSA]("http://www.jwz.org/doc/backups.html").)


Instead of a script on a timer, a [cronjob]("http://en.wikipedia.org/wiki/Cron") is the ideal way of doing this. Cron is already running, so you won't need a new process using your resources.

You can find the ubuntu wiki howto here: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Paqman on 2010-05-11
I would just use anacron personally. Cron is great for really fine-grained control of tasks, but the result is that it's pretty arcane and baffling. It's so much easier to just drop an rsync script into /etc/cron.daily (or whatever) and forget about it.

[/lazy]

---

### Post by McRat on 2010-05-11
CRON  / ANACRON sounds like what I'm looking for.  Thanks!

> **CharlesA said:**
> ...

EDIT: What OS is running on the machine you need to backup to?

It will be another Ubuntu machine on the LAN.

My LAN has a leg on it that goes to my house over a 5.8ghz wireless bridge.  If I aim the backup there, I kill two birds with one stone.  "Off-site" storage, and daily backup. 

I'm still studying and testing Linux to see if we can move over to it without hurting our business.  So far, so good.  I just need to play with the WINE stuff a bit more, and perhaps leave one WIN-XP platform on the network for problem software.  

PS - Very impressive stuff.  :guitar:

For all that have helped and supported the Ubuntu project and other Linux and Open Source projects, take a bow.

---

