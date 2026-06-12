---
title: "Alternative backup application"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by MaxVK on 2011-02-05
Hi.

For ages now Iv been using Quickstart as a backup program, and its always been very good, however the Quickstart project now seems to have died and I'm looking for something similar to take its place.

Backups need to be compressed and stored on an external HD and restoring should be simple, specifically I need to be able to backup /home so that it can be restored (either as it was, or on a new installation (Id re-install the software required)).

Incremental backups would be nice (so it only backs up files that have changed or been added to certain folders etc).

Iv looked around at a few programs and Id like to hear opinions/favorites etc

Cheers

Max

---

### Post by Zill on 2011-02-05
MaxVK:  [Simple Backup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") (sbackup) works for me :-)

---

### Post by tea for one on 2011-02-05
I would have a quick look at Grsync via the Software Centre

---

### Post by MaxVK on 2011-02-05
Thanks guys.

Simple backup was one that I was looking at myself - I thought it looked pretty good and I like the ability to manually backup rather than have set times (Which really don't fit into my lifestyle at all!).

Ill check out Grsync too, thanks TFO.

Ill be upgrading soon so Ill need this functionality, but if anyone has any other ideas id be glad to hear them and compare the programs. Id also be interested if anyone has any good or bad experiences with a particular piece of software.

Cheers all

Max

---

### Post by kellemes on 2011-02-05
[LuckyBackup]("http://luckybackup.sourceforge.net/")

---

### Post by MaxVK on 2011-02-06
Thanks kellemes but that looks just a bit too complicated for the kind of backups I do. I'm still liking the look of Simple Backup so Ill give it a go and if I don't get along with it Ill try the other two.

Thanks for your efforts

regards

Max

---

### Post by Zill on 2011-02-06
> **MaxVK said:**
> ...I'm still liking the look of Simple Backup so Ill give it a go and if I don't get along with it Ill try the other two...
Just a word of advice on SBackup... By default it saves the archive to /var/backup but I have always thought this isn't much use if the hdd crashes ;)

The moral is to *always* save the archive somewhere else - such as a separate PC, optical disk or, as you intend doing, an external hdd.

Also, carefully check that the config options detailed on the "Include" and "Exclude" tabs are *exactly* what you require.  The default configuration is quite sensible for most users but if/when you need to restore a backup it is too late to find you do not have an "essential" file archived!

The SBackup configuration file is /etc/sbackup.conf and can be quickly viewed with the command:
```
cat /etc/sbackup.conf
```
Although it is best to edit this file using the "Simple Backup Config" GUI, the terminal command does give a quick confidence check that everything looks right.

---

### Post by MaxVK on 2011-02-06
Cheers Zill - I'm pretty careful about backups, and tend to backup everything and then exclude some things - that way the worst I can do is archive something that I didn't need and I always backup onto external media.

I just did a backup and it seems pretty straight forward, although because I do manual backups its a little odd not having a "Finished" window pop-up or something.

Cheers

Max

---

### Post by Zill on 2011-02-06
> **MaxVK said:**
> ...I just did a backup and it seems pretty straight forward, although because I do manual backups its a little odd not having a "Finished" window pop-up or something...
SBackup runs as a "background" process and so does not give a progress report or indicate when it has finished.  This doesn't bother me as I save incremental backups automatically every night to another PC and just manually save the weekly full backups to DVD.

Other than monitoring the process ID I don't think there is any easy method of knowing when the backup process has actually finished.

---

### Post by Paqman on 2011-02-06
> **Zill said:**
> Just a word of advice on SBackup... By default it saves the archive to /var/backup but I have always thought this isn't much use if the hdd crashes ;)


Another caveat to go with this: if you are saving to an external location, sbackup doesn't check that it's actually mounted before it does the backup. This can mean it will dump the backup into that mount point (for example: /media/backupdrive) on your local hard drive. Again, this is a bit pointless, and it can fill up your drive very quickly.

I used to use sbackup, but now I've just dropped a couple of tiny wee scripts into anacron that check the location is mounted and if it is rsync away. Much more reliable IMO.

---

### Post by MaxVK on 2011-02-06
> Another caveat to go with this: if you are saving to an external location, sbackup doesn't check that it's actually mounted before it does the backup. This can mean it will dump the backup into that mount point (for example: /media/backupdrive) on your local hard drive

Understood, however sbackup is set to manual only and I specifically plug the external drive in to do a backup.

I did take a look at Grsync as suggested by tea for one and *that* looked much too complex for what I need to do, let alone using rsync on its own from the command line!

I tend to backup once a week and I'm planning an upgrade to 10.04 soon so I want something nice and simple so that I can just restore my /home folder once the upgrade is done and get to the business of installing all my apps again.

I don't suppose there is something that lists the apps you have installed so you can install them all again in one go is there?

Cheers
Max

---

### Post by hhlp on 2011-02-06
Déjà Dup is a simple backup tool. It hides the complexity of backing up the Right Way (encrypted, off-site, and regular) and uses duplicity as the backend.

Features:
 • Support for local, remote, or cloud backup locations, such as Amazon S3 or Rackspace Cloud Files
 • Securely encrypts and compresses your data
 • Incrementally backs up, letting you restore from any particular backup
 • Schedules regular backups
 • Integrates well into your GNOME desktop

---

### Post by Paqman on 2011-02-06
> **MaxVK said:**
> 
I don't suppose there is something that lists the apps you have installed so you can install them all again in one go is there?


[Yup]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by MaxVK on 2011-02-06
Déjà Dup looks fine but I really don't want to get into scheduled backups or for that matter backing up to some online service or other (Didn't read far enough to find out if it can back up to an external drive etc).

Paqman: Nice one thanks.

Regards

Max

---

### Post by MaxVK on 2011-02-11
Hey guys - I have another question about simple backup:

It runs in the background - got that, but what if I carry on working and have a file open and being edited and saved frequently during the backup?

Will SB be able to backup a file that is open and being edited?
Will this file be backed up?
What about if the file is backed up and then edited again? (Id presume that I have a backup of it as it was when it was first backed up)

Sorry, might be daft questions, but I'm not used to background backups like this - I don't know if I can keep working and if I cant I don't know when the backup finishes so I can start working again.

cheers

Max

---

### Post by Zill on 2011-02-12
> **MaxVK said:**
> Hey guys - I have another question about simple backup:

It runs in the background - got that, but what if I carry on working and have a file open and being edited and saved frequently during the backup?...
A good question but, unfortunately, I don't know the answer to it!  I would have *thought* that SBackup simply takes a "snapshot" of the latest file(s) in whatever state they are in when they are archived.  If you really need to know more about this then you could "[Ask a question]("https://launchpad.net/sbackup")" via Launchpad and, hopefully, the developers will give the correct answer.

Alternatively, you could just do what I do and only run a backup while you are not actually using the PC ;-)

---

### Post by quadproc on 2011-02-12
> **MaxVK said:**
> Hey guys - I have another question about simple backup:

It runs in the background - got that, but what if I carry on working and have a file open and being edited and saved frequently during the backup?
That is a good question and I *think* that the answer is that _sbackup_ will try to open the file to read it; if it can open it then it will save it as it is *at that time*.  The reason why I think this is that _sbackup_ is actually a script and the simplest way to write such a script is as I described.

I used to use _sbackup_ but right at this moment I am not sure what to do.  Reason: _sbackup_ used to allow me to save the backups to an external SATA drive which I would mount for the purpose but, in Ubuntu 10.10, that functionality has been broken.  I haven't figured out a way to make sbackup use my external drive.

I have read that _sbackup_ is essentially unsupported now because the effort is going into _nssbackup_ instead.

quadproc

---

### Post by MaxVK on 2011-02-14
Hmm thanks guys - I can do backups when I'm not working, although without something to tell me when the backup has finished the only thing I can do is to watch the CPU activity in the CPU monitor, but the whole idea is a bit pointless if the software doesn't work on newer versions!

I was about to update to 10.04 but if sbackup is broken on 10.10 there doesn't seem to be much point even starting with it!

Iv a feeling that Ill be casting around again to try and find some suitable software, or if all else fails I might have to resort to writing a python script or something - Not what I want to do, because while its fun, its taking time out of other things I need to be doing!

Anyway, thanks for your time everyone - further suggestions and ideas would be gratefully received.

regards

Max

---

### Post by linux4me on 2011-02-14
I do manual backups just like you do, and use Grsync with an exclude file, backing up to a USB-connected LVM-encrypted hard drive or to another PC. I run it while I'm working on files it's backing up all the time; in fact, I usually have a bunch of programs running at the same time just to see what happens, and it's never had a problem. The setup isn't as complicated as it appears. In fact, running it from the command line (CL) isn't as complicated as it appears, either. I use the CL to do backups from some web sites via SSH to an external drive as well. I've been using Grsync now since 8.04, and it's great for transferring your /home directory to new machines on new installs. You can also use it to [sync two (or more) PCs via OpenSSH]("http://ubuntuforums.org/showthread.php?t=795668&highlight=grsync+exclude"), like your laptop and desktop. The Grsync GUI also shows you progress of the backup and tells you when it's done.

I'd bite the bullet and go with it.;)

If you want some suggestions on what to exclude in your exclude file and how to set up Grsync, you can get plenty of help here.

---

### Post by MaxVK on 2011-02-15
Thanks linux4me - Iv been looking at Grsync again and its not that I'm worried about the complexity of the program its more about adding complexity to something that should be nice and simple! That was the main reason I started to use Quickstart - couple of clicks then go and make a drink while the backup gets done!

I like the idea of a script to do a backup though so I think Ill look a little harder at Grsync this time.

Thanks for your time (I might post back and ask a question or two related to Grsync)

regards

Max

---

### Post by kellemes on 2011-02-15
> **MaxVK said:**
> Thanks linux4me - Iv been looking at Grsync again and its not that I'm worried about the complexity of the program its more about adding complexity to something that should be nice and simple! That was the main reason I started to use Quickstart - couple of clicks then go and make a drink while the backup gets done!

I like the idea of a script to do a backup though so I think Ill look a little harder at Grsync this time.

Thanks for your time (I might post back and ask a question or two related to Grsync)

regards

Max

Grsync (just as Luckybackup) let you set up your backup scheme (can be but doesn't have to be complex) from comfortable GUI and let the backups run as scheduled. This means a one time setting up and after this you can make drinks without ever have to think about your backups.
Wel, it's my personal preference anyway, it's all up to you, lot of options..

---

### Post by mastablasta on 2011-02-15
what about mintbackup tool? their releases are upgraded by doing fresh install so they made this backup tool that backs up home and settings. haven't tried it myself yet, but it seems i will have to soon.

---

### Post by jchw on 2011-02-20
I use Deju Dup for my backups and in the last six months have had to do two complete restores. Deju Dup saved my Ubuntu life both times and I was amazed how easy and complete was the restore process. One of the backups from 10.04 Wubi restored successfully into 10.10 and was probably less painful than doing an upgrade or a move from Wubi to a full installation.

I use a 32G flash drive and do backup's as and when I remember. I see a bug was reported about the Deja Dup restore but I have experienced no problems.

---

### Post by MaxVK on 2011-02-21
Thanks guys - Iv not seen the Mint backup tool - Ill check that out, cheers.

I did look at Deja already but Ill take another look - people keep mentioning it so there must be something more to see.

Thanks all

regards 

Max

---

