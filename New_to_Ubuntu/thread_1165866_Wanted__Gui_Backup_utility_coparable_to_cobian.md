---
title: "Wanted:  Gui Backup utility coparable to cobian"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by longtom on 2009-05-21
Hi,

I like cobian and I am using it for quite some time.  However, in order to move over to linux via Ubuntu, that file server needs to get Ubuntu as well.

Now, is there a backup utility out there similar to cobian, which can be used to make different types of backups of Ubuntu and WinXP machines on a mixed network.  A gui frontend would be highly appreciated as well.

Any suggestions welcome.

---

### Post by bacardiandwatermelon on 2009-05-21
You could always try and run it over wine?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12960&iTestingId=28390](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12960&iTestingId=28390)

---

### Post by longtom on 2009-05-21
> **bacardiandwatermelon said:**
> You could always try and run it over wine?
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12960&iTestingId=28390](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12960&iTestingId=28390)

I could - but for a backup system I'd like to look at something more "part of Ubuntu".

In other words, if I had to run Cobian over wine I'd rather have it run in Windows, which is what it appears to be made for.

Any *.deb files out there?  I didn't find any...but I am plagued by occasional blindness...

---

### Post by Didius Falco on 2009-05-21
Hi,

Have a look at NASBackup, it may suit your needs, including the GUI:

[http://www.nasbackup.com/wiki/Introduction](http://www.nasbackup.com/wiki/Introduction)

I hope it helps...

Regards,

Didius

---

### Post by longtom on 2009-05-21
> **Didius Falco said:**
> Hi,

Have a look at NASBackup, it may suit your needs, including the GUI:

[http://www.nasbackup.com/wiki/Introduction](http://www.nasbackup.com/wiki/Introduction)

I hope it helps...

Regards,

Didius

Looks interesting - but it only appears to be available as an exe file..?

I'd like to run the filse server from Ubuntu.

---

### Post by Didius Falco on 2009-05-21
Yeah, disregard that - that's what happens when I just quickly skim instead of really reading....

It has to be run from Windows, but will backup linux systems - not what you are after at all...

Have a look at Backup PC:

[http://backuppc.sourceforge.net/index.html](http://backuppc.sourceforge.net/index.html)

It definitely will install on linux. <G>

Another option is Bacula:

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Again, will install on linux.

Sorry for the timewaster before - hopefully one of these two will pique your interest.

Regards,

Didius

---

### Post by longtom on 2009-05-22
> **Didius Falco said:**
> Yeah, disregard that - that's what happens when I just quickly skim instead of really reading....

It has to be run from Windows, but will backup linux systems - not what you are after at all...

Have a look at Backup PC:

[http://backuppc.sourceforge.net/index.html](http://backuppc.sourceforge.net/index.html)

It definitely will install on linux. <G>

Another option is Bacula:

[http://www.bacula.org/en/](http://www.bacula.org/en/)

Again, will install on linux.

Sorry for the timewaster before - hopefully one of these two will pique your interest.

Regards,

Didius

Yeah - Bacula looked good.  I installed it - but somehow I don't know how to start it up.  No gui, and when I type "bacula" in the terminal, it says "program not found.  Very peculiar....

But thank you for your tips...

---

### Post by Tibuda on 2009-05-22
I use [grsync]("apt:grsync"). It is a GTK+ frontend for the powerful command-line rsync.

---

### Post by bacardiandwatermelon on 2009-05-22
Just had a look at Bacula myself and it seams the guis are separate. They show two of them on the screenshots page...
[http://www.bacula.org/en/?page=screenshot](http://www.bacula.org/en/?page=screenshot)

---

### Post by Didius Falco on 2009-05-22
I think I may have found your GUI:

[http://sourceforge.net/project/showfiles.php?group_id=50727&package_id=44845&release_id=679402](http://sourceforge.net/project/showfiles.php?group_id=50727&package_id=44845&release_id=679402)

It's a recent release, as well - 4/30/09 


I hope it helps...

Regards,

Didius

---

### Post by asmoore82 on 2009-05-22
> **danielrmt said:**
> I use [grsync]("apt:grsync"). It is a GTK+ frontend for the powerful command-line rsync.

[SIZE="3"]**+1**[/SIZE]

Grsync + Rsync + SSH + password-free public key authentication
it's almost too good to be of this Earth.

---

### Post by longtom on 2009-05-25
> **Didius Falco said:**
> I think I may have found your GUI:

[http://sourceforge.net/project/showfiles.php?group_id=50727&package_id=44845&release_id=679402](http://sourceforge.net/project/showfiles.php?group_id=50727&package_id=44845&release_id=679402)

It's a recent release, as well - 4/30/09 


I hope it helps...

Regards,

Didius

Thank you.  That would mean I have to compile....haven't done that in my short Ubuntu life....


> I use grsync. It is a GTK+ frontend for the powerful command-line rsync. 

Link goes to nowhere - but I'll check it out.  Thank you.

---

### Post by longtom on 2009-05-25
Checked out grsync.  Any way I can backup my network?  Any way I can schedule my backups?

I'm probably blind again - so please help.

---

### Post by wizard10000 on 2009-05-25
> **longtom said:**
> Checked out grsync.  Any way I can backup my network?  Any way I can schedule my backups?

I'm probably blind again - so please help.

I use rsync to do network backups - runs as a daily cron job and works just fine.

First let's look at my /etc/crontab -

```
0 2 * * * root mount -t smbfs -o username=wizard,password=******** //192.168.1.103/documents$ /home/wizard/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
15 2 * * * wizard sh /home/wizard/scripts/rsync_backup.sh >> /var/log/cron-output.log 2>&1
0 4 * * * root umount /home/wizard/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
```
Okay.  First, I tend to put cron jobs in /etc/crontab instead of using crontab -e just so I can go to one place to look at all scheduled tasks - you can run your system any way you like, though  :)

Line 1 mounts my wife's My Documents folder on my desktop.

Line 2 runs an rsync job we'll get into in a minute.

Line 3 unmounts the share we mounted at the beginning.

Okay, on to the rsync script.

```
rsync -rltEmqu --exclude-from=/home/wizard/.rsync/exclude /home/wizard /media/ARCHIVE/archive/home
rsync -rltEmqu /etc /media/ARCHIVE/archive
```
Everybody does rsync differently, but this copies my home and /etc directories to an external hard drive I keep mounted.  Here's what the command line options do -

rsync -rltEmqu

```
-r, --recursive             recurse into directories
-l, --links                 copy symlinks as symlinks
-t, --times                 preserve modification times
-E, --executability         preserve executability
-m, --prune-empty-dirs      prune empty directory chains from file-list
-q, --quiet                 suppress non-error messages
-u, --update                skip files that are newer on the receiver
```
and the --exclude-from= switch allows me to specify a text file where I can list stuff rsync is supposed to ignore.  My ~/.rsync/exclude looks like this -

```
.rnd
.gvfs/
.VirtualBox/
download/
temp/
```
Note that directory names have a trailing slash.

You can't back up .rnd, .gvfs/ contains symlinks to drives mounted on your desktop and prevents an endless backup loop, I don't back up .VirtualBox/ because I just use it to play with Windows 7, and my ~/download and ~/temp directories have stuff in there I'd rather not archive.

Anyway, maybe this will help get you started.  You can do a heck of a lot more with rsync than I have but this works for me and I have a hot backup of everything that's important  ;)

Good luck -

---

### Post by Tibuda on 2009-05-25
> **longtom said:**
> Checked out grsync.  Any way I can backup my network?  Any way I can schedule my backups?

I'm probably blind again - so please help.

To schedule your backups, I suggest you to use gnome-schedule (available on repositories). Setup your backup in grsync, but before running the backup copy the rsync command and use it in gnome-schedule.

---

### Post by longtom on 2009-05-25
Thank you, wizard10000.   Looks like I need to get some studying done before I attempt that....:o

---

### Post by longtom on 2009-05-25
> **danielrmt said:**
> To schedule your backups, I suggest you to use gnome-schedule (available on repositories). Setup your backup in grsync, but before running the backup copy the rsync command and use it in gnome-schedule.

So - if my backup project would be "bup_01", I'd use "rsync bup_01"?

And to backup network folders I first need to mount them?  There would be a lot of mounting and unmounting goimg on.

---

### Post by jereece on 2010-10-16
[http://www.diffingo.com/oss/fwbackups](http://www.diffingo.com/oss/fwbackups)

---

