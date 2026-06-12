---
title: "help to choose a backup-ing software with these features"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by medya on 2010-08-14
guys,  recently I lost my data on Two hard disks and from now on I decided to back up all my data carefully .

what applicaton do you suggest for backing up ?

let say I have a music folder and everyweek I add 5-6 new albums to it , I want an intelegent software that backs up my data Weekly and only copy the New Files to the back up drive [instead of copying everything again]


tell me about your favorite back up software .

---

### Post by cj.surrusco on 2010-08-14
[Rsync]("http://www.samba.org/ftp/rsync/rsync.html") will do exactly what you want. I use a command that makes a directory on one drive exactly the same as a directory on another drive. It copies new files and deletes old ones.

The command would look like this:
```
rsync -vr --delete --ignore-existing /path/to/music/ /path/to/backup/
```

---

### Post by medya on 2010-08-14
how about other applications , do they also do the same?

---

### Post by cj.surrusco on 2010-08-14
I've never had to find out. I have always used rysnc because it works so well.

---

### Post by drdos2006 on 2010-08-14
+1 for rsynch. Very powerful. For instance :
Set up a bash script called "backup-to-server.sh" and from the terminal type : bash backup-to-server.sh
This is the script I use.

# start of script
#!/bin/bash
## remove old backup-log.txt
sudo rm 	/home/MyHome/Documents/backup-log.txt

# Mount the shares before updating
bash /home/MyHome/Documents/MountServerShares.sh

## sdc1 is 320 GB NTFS
sudo rsync --verbose --recursive  --archive --modify-window=1 --times --update --delete-before  --progress --itemize-changes --log-file=/home/MyHome/Documents/backup-log.txt   /media/sda1-320G/InstallationFiles     /media/sdc1-shared/    


	sudo umount    /media/sdc1-shared/ 
# end of script

regards
[edit]
Files are updated from InstallationFiles to sdc1-shared

---

### Post by ndstate on 2010-08-15
Give Backintime a whirl

---

### Post by jerenept on 2010-08-15
> **pmp6nl said:**
> Give Backintime a whirl

BackInTime is a graphical frontend to rsync, so I strongly suggest it. It's awesome.

you might want to try backing up more often than weekly.... maybe daily.

---

### Post by amac777 on 2010-08-15
-1 for rsync by itself. The reason is rsync is a syncronizer, not a backup. The difference is subtle but important. Syncronizing a folder on your computer with a "backup mirror" on a removable storage will work as a backup in some instances, like when your computer suddenly crashes all at once and you have recently done the synchrnoization. However, it will not help you if you accidently modify or delete a file and then do another sync to create a new backup. In this case, the backup will have the modified file and you can't get back the original. This is especially problematic if files are slowely becoming corrupted on your computer but you don't notice. As you keep "making backups", you are actually deleting your backups if you only use rsync to keep a mirror on an external drive.

The solution: look for something that keeps snapshots. I use 'rsnapshot' myself because I enjoy the command line, but Backintime recommended above looks good as a GUI option too. The point is to keep lots of snapshots of your system over time. Just keep making a new snapshots as your backups until your external drive becomes full and then buy a new one. Most snapshot backup programs (including rsnapshot and backintime) will only actually store files that change so space is conserved. If you accidently deleted a file a few months ago, you'll have lots of snapshots before that so you can still go find your file.

---

### Post by ndstate on 2010-08-15
Additionally backintime will allow you to do backups at specific intervals per folder.  Its a pretty powerful program.

---

### Post by HermanAB on 2010-08-15
You should also look at 'dervish'.

---

### Post by medya on 2010-08-15
could somebody tell me what is snapshot exactly ? I know almost what is it, but I want more accurate defenition and how it work

---

### Post by amac777 on 2010-08-15
A snapshot means a backup at a certain time. One example is to do monthly snapshots. In this case, each snapshot is a backup of your files as they appeared at a certain month. 

So the backup of your system might include a bunch of date associated snapshots like this:

```
snapshot-2010-08-01
snapshot-2010-07-01
snapshot-2010-06-01
snapshot-2010-05-01
etc
```

Each of those snapshots includes all the files as seen on that date. This may seem like you are storing a lot of repeated information that didn't change, but the backup program automatically makes sure the space on the harddrive is only used once for files that don't change.

---

### Post by medya on 2010-08-15
> **amac777 said:**
> A snapshot means a backup at a certain time. One example is to do monthly snapshots. In this case, each snapshot is a backup of your files as they appeared at a certain month. 

So the backup of your system might include a bunch of date associated snapshots like this:

```
snapshot-2010-08-01
snapshot-2010-07-01
snapshot-2010-06-01
snapshot-2010-05-01
etc
```

Each of those snapshots includes all the files as seen on that date. This may seem like you are storing a lot of repeated information that didn't change, but the backup program automatically makes sure the space on the harddrive is only used once for files that don't change.

thanks, a question , If I delete some of these snapshots will it affect other snapshots ? let say I have 10 snapshot of 10 months , then I delete 5 of them in the middle. do I look any data in my Last snapshot?

---

### Post by PhilGil on 2010-08-15
> **medya said:**
> thanks, a question , If I delete some of these snapshots will it affect other snapshots ? let say I have 10 snapshot of 10 months , then I delete 5 of them in the middle. do I look any data in my Last snapshot?
Another satisfied Back in Time user here.  If you use your backup program to manage the snapshots you won't have a problem, you'll only lose file versions that are specific to the dates you are deleting.

---

### Post by lbrty on 2010-09-06
> **medya said:**
> guys,  recently I lost my data on Two hard disks and from now on I decided to back up all my data carefully .

what applicaton do you suggest for backing up ?

let say I have a music folder and everyweek I add 5-6 new albums to it , I want an intelegent software that backs up my data Weekly and only copy the New Files to the back up drive [instead of copying everything again]


tell me about your favorite back up software .

I use FreeFileSync. In my opinion, I think it works the best and is the simplest to use. I highly recommend it!

[http://sourceforge.net/projects/freefilesync/](http://sourceforge.net/projects/freefilesync/)

---

### Post by baddnady23 on 2010-09-06
I recently got into the backup game and have been using rsync.  If your scared of the command line, I do believe that there is a GUI for it in the repo's.  If you use the "--delete" switch, it will do exactly as you wanted from your origional post.  It is also very simple to set up in CRON and run everyday.  After the initial backup, subsequent backups should only take a minute or two.

---

### Post by amac777 on 2010-09-06
> **baddnady23 said:**
> I recently got into the backup game and have been using rsync.  If your scared of the command line, I do believe that there is a GUI for it in the repo's.  If you use the "--delete" switch, it will do exactly as you wanted from your origional post.  It is also very simple to set up in CRON and run everyday.  After the initial backup, subsequent backups should only take a minute or two.

Questions: What do you do if you realize you accidentally deleted an important file right before you ran the rysnc command? How does your backup system help in this situation?

---

### Post by cj.surrusco on 2010-09-06
> **baddnady23 said:**
> I recently got into the backup game and have been using rsync.  If your scared of the command line, I do believe that there is a GUI for it in the repo's.  If you use the "--delete" switch, it will do exactly as you wanted from your origional post.  It is also very simple to set up in CRON and run everyday.  After the initial backup, subsequent backups should only take a minute or two.

The GUI is called BackInTime.

> **amac777 said:**
> Questions: What do you do if you realize you accidentally deleted an important file right before you ran the rysnc command? How does your backup system help in this situation?
Well, that's a different problem. If you choose to use the --delete option, then you need to be very weary of what you delete. The --delete option is for people that want to keep a drive the same way as another, in case of drive failure. If you want to keep all of the files, even if they are deleted from the original drive, then you wouldn't use the --delete option. BackInTime may easier to understand as opposed to the cli options.

---

### Post by amac777 on 2010-09-06
Yup, although to me, it's the same problem that is the subject of this thread. That example just illustrates the repeatedly proposed rsync solution is not adequate. 

Another example: what if you modify a file or it gets corrupted right before you do a "backup" with rsync? Even if you don't use the -delete option, you're still in trouble.....

Like you said, BackInTime solves all these problems. It's all been mentioned earlier in this thread. I just didn't want the last post to be a recommendation to rysnc (again) without taking into the account the flaws with using that as a backup system. It's almost as bad as using RAID as a backup, in my humble opinion.

---

### Post by cj.surrusco on 2010-09-06
> **amac777 said:**
> Yup, although to me, it's the same problem that is the subject of this thread. That example just illustrates the repeatedly proposed rsync solution is not adequate. 
BackInTime *is* rsync. It is just the GUI frontend for it. So anything that BackInTime can do, can be done with rsync, you just need to find the options that suit your needs.
> **amac777 said:**
> Another example: what if you modify a file or it gets corrupted right before you do a "backup" with rsync? Even if you don't use the -delete option, you're still in trouble.....

Like you said, BackInTime solves all these problems. It's all been mentioned earlier in this thread. I just didn't want the last post to be a recommendation to rysnc (again) without taking into the account the flaws with using that as a backup system. It's almost as bad as using RAID as a backup, in my humble opinion.

Again, you're looking at two different ways of backup. You can have the type of backup that you want, which will preserve a lot, maybe more that is necessary. 

RAID, or using rsync with the --delete option, ***can*** be used as a backup. In fact, it's what I use. It's for people that are looking to protect large amounts data in case of a drive failure. Therefore, anybody using this approach isn't planning to accidentally delete a file, or save changes made to files. It's still an efficient way of backup, just for a different purpose.

---

### Post by amac777 on 2010-09-06
I belive BackInTime is more than just rsync... In fact, a quick google search shows: 

> Keep in mind that Back In Time is just a GUI. The real magic is done by rsync (take snapshots and restore), diff (check if somethind changed) and cp (make hardlinks).


from here: [http://backintime.le-web.org/documentation/](http://backintime.le-web.org/documentation/)

Those hard links are the key since they make keeping tons and tons of snapshots very efficient. 

Anyway, if you are sure that you will never need a backup for anything that you (accidentally), a hacker, a software crash, or malware will do to your files, Then, yes, RAID and other syncronization and mirroring techniques *may* work as a backup in your situation, if you are lucky and the drive failure is instantaneous rather than slowly corrupting your files over time. However, if you want to also protect yourself from the more common situation where it is you yourself who accidentally delete or modify a file and then realize some period of time later that you did it, I'd suggest using something with snapshots. Once you get bitten, you'll realize it's better to be safe than sorry. I speak from experience.

---

