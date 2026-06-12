---
title: "thunderbird emails"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-15
all of my emails in my inbox are empty from 11/12 and before. i open them and there is nothing there. 
once before i tried rebuilding my index but that deleted every thing completely any ideas what is happening.

---

### Post by Meskarune on 2009-11-15
Are you using pop3? You could be deleting the mails from the server...

---

### Post by DarinB on 2009-11-16
yes i am using pop3 but i have 4 email accounts, from different placed i never leave copy on server but i did have the folders retention policy at use server default so i changed it to never delete. not sure what else it could be. but now those empty emails are totally deleted. i think it is strange that the email would be empty but leave the email itself then at next reboot be gone totally. and why from 11/12 and before that is only 3 days ago???

---

### Post by ukripper on 2009-11-16
have you got backup of your home directory or ~/.mozilla-thunderbird folder anywhere?

---

### Post by DarinB on 2009-11-16
i do have a .mozilla_backup1 from a long time ago sitting in my /home folder.... it was recommended to do it once about a year ago to fix something, i don't remember what it was but it was not this. This same thing happened about a year ago i tried to fix it by rebuilding folder index and that wiped out all of my emails. I am not sure what happened or how i can keep this from happening again. i can understand the entire email being deleted but not the content only then the email later. and why only my inbox folder and not my other folders i have about 5 set up with mail filters. they are fine.

---

### Post by ukripper on 2009-11-16
you should have regular backups of such important data. in future you can avoid such problems easily by doing two things:
1. Create **backup** of home drive. you can use many applications to do that. If you like GUI then use Sbackup [http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)
For command line - very well explained tutorial here [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This way if anything goes wrong you can easily restore.

2.If you are using pop3 which is a good way to have extra protection keeping emails on the server for 30 days. There is option in thunderbird account settings to delete emails after certain period from server. This way if your re-index goes wrong you can always retrieve email from the server lasting -30 days.

Hope it helps.

---

### Post by DarinB on 2009-11-16
hmmm! i am wondering i just found an nstmp folder in my trash, i wonder if i hit the compress folder by mistake and then shut down thunderbird prematurely. thereby losing those files???? i deleted the nstmp folder since the compression was aborted. maybe that was not the best thing to do, i thought you could delete the nstmp if the compression was aborted. not sure now?

---

### Post by wrgb2 on 2009-11-16
I always Compact Folders on a regular (daily) basis in Thunderbird, otherwise the database will become corrupt.

---

### Post by DarinB on 2009-11-16
Is that true that if i do not compact it will get corrupted that does not sound logical

---

### Post by ukripper on 2009-11-16
> **DarinB said:**
> Is that true that if i do not compact it will get corrupted that does not sound logical

never happend to me and sqlite don't just corrupt like that. it is renowned RDBMS.

---

### Post by DarinB on 2009-11-16
sorry but what does.... it is renowned [COLOR="Red"]RDBMS.[/COLOR] mean?

---

### Post by ukripper on 2009-11-16
> **DarinB said:**
> sorry but what does.... it is renowned [COLOR="Red"]RDBMS.[/COLOR] mean?

sorry can't fit in one line so posting a link - [http://en.wikipedia.org/wiki/Relational_database_management_system](http://en.wikipedia.org/wiki/Relational_database_management_system)

> Short for relational database management system and pronounced as separate letters, a type of database management system (DBMS) that stores data in the form of related tables. Relational databases are powerful because they require few assumptions about how data is related or how it will be extracted from the database. As a result, the same database can be viewed in many different ways.

An important feature of relational systems is that a single database can be spread across several tables. This differs from flat-file databases, in which each database is self-contained in a single table.

Almost all full-scale database systems are RDBMS's. Small database systems, however, use other designs that provide less flexibility in posing queries. 

[http://www.webopedia.com/TERM/r/RDBMS.html](http://www.webopedia.com/TERM/r/RDBMS.html)

---

### Post by DarinB on 2009-11-16
thanks for the link,,,,but did i cause the loss by compacting by mistake then shutting down prematurely???
or is there a problem with my thunderbird. it did happen about 6 months ago and i could not retrieve them. I did try making /.mozilla a _backup then restarting mozilla to recreate the /.mozilla automatically. but not sure if that did anything because now after 6 months i have the same thing again.

---

### Post by ukripper on 2009-11-16
> **DarinB said:**
> thanks for the link,,,,but did i cause the loss by compacting by mistake then shutting down prematurely???
or is there a problem with my thunderbird. it did happen about 6 months ago and i could not retrieve them. I did try making /.mozilla a _backup then restarting mozilla to recreate the /.mozilla automatically. but not sure if that did anything because now after 6 months i have the same thing again.

what is the size of your ./mozilla-thunderbird folder?
Run this in terminal to find out:
```
du -cs ~/.mozilla-thunderbird
```

---

### Post by DarinB on 2009-11-16
darin@darin-desktop:~$ du -cs ~/.mozilla-thunderbird
1828176	/home/darin/.mozilla-thunderbird
1828176	total
darin@darin-desktop:~$

---

### Post by ukripper on 2009-11-17
> **DarinB said:**
> darin@darin-desktop:~$ du -cs ~/.mozilla-thunderbird
1828176	/home/darin/.mozilla-thunderbird
1828176	total
darin@darin-desktop:~$

sorry dude. can you post again with this command:
```
du -csh ~/.mozilla-thunderbird
```

---

### Post by DarinB on 2009-11-17
darin@darin-desktop:~$ du -csh ~/.mozilla-thunderbird
1.8G	/home/darin/.mozilla-thunderbird
1.8G	total
darin@darin-desktop:~$

---

