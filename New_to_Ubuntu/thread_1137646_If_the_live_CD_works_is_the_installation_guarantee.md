---
title: "If the live CD works is the installation guaranteed?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-04-25
If all looks good with a live CD is the installation going to be 100% sure?

---

### Post by wizard10000 on 2009-04-25
> **tahitiwibble said:**
> If all looks good with a live CD is the installation going to be 100% sure?

Um - most of the time  :)

I ran the live CD, blew away / but kept /home and swap and clean installed - ran into the grub ext4 issue that's only supposed to happen with an upgrade.  /home was an ext3 partition.

Since I had a good backup of /etc and /home I just wiped the whole drive - that worked.

---

### Post by tahitiwibble on 2009-04-25
Wizard, why do you need a backup of /etc? I thought it was only /home that counted?

---

### Post by wizard10000 on 2009-04-25
> **tahitiwibble said:**
> Wizard, why do you need a backup of /etc? I thought it was only /home that counted?

I generally back up /etc to my home directory before I do any kind of install - I have a crontab, mysql and apache configuration, some nfs mappings and exports, all kindsa stuff that's handy to have if you're putting things back they way they were.

You only have to restore the stuff you need and I generally only need a handful of files - but I think it's a real timesaver.

---

### Post by steve101101 on 2009-04-25
+1 I make a weekly backup to my secondary drive of my entire computer.

---

### Post by tahitiwibble on 2009-04-25
Steve, just out of curiosity, how? Do you copy/paste?

---

### Post by steve101101 on 2009-04-25
i run a cron command that does this task weekly:

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

---

### Post by tahitiwibble on 2009-04-25
Hmmmm what's 'cron"? Is that similar to perl?

---

### Post by steve101101 on 2009-04-25
[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

### Post by tahitiwibble on 2009-04-25
Thanks for that. Couldn't have wanted for more. Cheers.

---

### Post by camnor on 2009-04-25
cron is not like perle, because perle is a programming language where as cron is a command.  What cron does is it is a command that will run periodically any tesk you assign it,  which can be regulated to happen every hour, day, week, etc.

---

### Post by wizard10000 on 2009-04-25
> **tahitiwibble said:**
> Steve, how? Do you just copy/paste?

I'm not Steve, but I use rsync to just keep a live backup to an external drive.  Looks like this -

First, I have a crontab that mounts the My Documents folder on mrs' wiz' Windows machine and calls a shell script that runs the backup -

```
0 0 * * * wizard10000 sh /home/wizard10000/scripts/vbulletin-dump.sh >> /var/log/cron-output.log 2>&1
0 1 * * * root mount -t smbfs -o username=wizard10000,password=xxxxxxxx //192.168.1.103/documents$ /home/wizard10000/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
15 1 * * * wizard10000 sh /home/wizard10000/scripts/rsync_backup.sh >> /var/log/cron-output.log 2>&1
0 4 * * * root umount /home/wizard10000/mrs-wiz-pc >> /var/log/cron-output.log 2>&1
```

The first task calls a script that grabs a mysql dump of my vBulletin board and puts it in my home directory.

The second task mounts mrs. wiz' My Documents folder in my home directory.

The third runs an rsync script that looks like this -

```
rsync -rltEmqu --exclude-from=/home/wizard10000/.rsync/exclude /home/wizard10000 /media/ARCHIVE/home
rsync -rltEmqu /etc /media/ARCHIVE
find /media/ARCHIVE/home/wizard10000/vbulletin/mysql/*.gz -mtime +6 -exec rm {} \;
```

The last line in the script just deletes any sql dump that's more than a week old.

Last but not least the exclude file looks like this -

```
.rnd
.gvfs/
.VirtualBox/
```

You can't back up .rnd, .gvfs/ contains symlinks to mounted drives or shares on your desktop and prevents an endless backup loop - and .VirtualBox/ is just a toy and I don't back it up.

---

### Post by steve101101 on 2009-04-25
does rsync skip files that haven't been changed since last update and if so what command would i run to backup everything on the computer like my previous command.

---

### Post by wizard10000 on 2009-04-25
> **steve101101 said:**
> does rsync skip files that haven't been changed since last update and if so what command would i run to backup everything on the computer like my previous command.

Yeah, by default rsync will only back up files that have changed or don't exist on the target.  The stuff I posted above will get you started but you're still gonna have to read a man page or two  ;-)

The hardest part for me was the exclude file - took me awhile to understand that directory names have to have a trailing slash - but you can exclude stuff on the command line too.

The stuff I posted meets my needs but probably wouldn't meet yours - but the simple line that copies my /etc directory to another folder would be a good place to start.  Get that working, then learn how to use an exclude file, then set rsync options - and there are a lot of them.

---

### Post by Wiebelhaus on 2009-04-25
It's safe bet , but you may run into issues from time to time but this thing is so tight now it's very rare to have a complicated problem that can't be fixed.

Cheers!

---

### Post by presence1960 on 2009-04-25
> **steve101101 said:**
> i run a cron command that does this task weekly:

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

another fast way is to back up using rsync or the GUI version grsync. Both are in Synaptic.

---

### Post by Yed Ied on 2009-04-26
I don't want to butt in but I was on an old Emachine and Ubuntu 8.10 live CD worked great but would not install, 8 day project.  The only thing I could come up with was a problem with the CHIP SET.  The Emachine is still in my closet without the HDD, moved on.

---

