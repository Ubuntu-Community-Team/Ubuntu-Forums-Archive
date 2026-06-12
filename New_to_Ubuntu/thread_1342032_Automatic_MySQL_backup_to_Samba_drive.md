---
title: "Automatic MySQL backup to Samba drive"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Xilver on 2009-11-30
Hi,

In our company we have an internal Ubuntu server on which we test software and websites which will run on linux machines at our clients. We would like to schedule daily backups of several of these databases, however, since this is the only linux machine in our network, they have to be backed up to a network drive on our Windows network.

I installed mysql-admin, and it works perfect when backing up databases to a local path, whenever I enter a samba-path, mysql administrator flashes an error, and then closes itself.

Is there a way to let mysql administrator back up to samba drives, or is there any other solution.

I would be very grateful for you help. Thanks.

---

### Post by ukripper on 2009-11-30
you need to make sure your samba share is working first. try copying file to your samba share using below command:
```
scp -v **testfile.txt //192.0.x.x/samba-share-whereever-it-is/**
```
replace above in bold  accordinly.

if it copies file then it means your samba share is mounting otherwise you will need to mount your samba share first either in fstab or manually.

---

### Post by Xilver on 2009-11-30
Indeed it wasn't mounted. However, now I'm having problems mounting the drive.

I'm using:
```
sudo mount -t cifs -o username=xxxx password=xxxx //x.x.x.x/Admin/DB /mnt/samba
```But it won't work. Sorry for being a total noob here :)

Edit: forgot the -o before password, however it's mounting read-only, even when specifying username and password?

---

### Post by ukripper on 2009-11-30
It will be hard for me to explain all that in here. i suggest you read this excellent guide here  - [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

skip to permanent mount section of this guide. your answer is there.



.

---

### Post by Xilver on 2009-12-01
Thanks, I'm gonna check it out.

---

### Post by Xilver on 2009-12-01
Indeed it worked, thank you for your help. Now to find why my scheduled backup isn't working :)

---

### Post by ukripper on 2009-12-01
how did you schedule it, did you do it via crontab?

---

### Post by Xilver on 2009-12-01
I'm using the Schedule Backup option in MySQL Administrator. The note at the bottom of the dialog says backups are scheduled using the standard cron system.

---

### Post by ukripper on 2009-12-01
can you post your cron schedule using below command:

if using under your username:
```
crontab -e
```

if under root then:
```
sudo crontab -e

```

---

### Post by Xilver on 2009-12-01
Seems rather empty :)

# m h  dom mon dow    command

---

### Post by ukripper on 2009-12-01
I never used mysql administrator. i use phpmyadmin to administer and normal shell script to backup mysql securely.
i use this sort of script - [http://openconcept.ca/mysql_permissions_for_backup](http://openconcept.ca/mysql_permissions_for_backup)   to backup which is much more cutomizable than any backup software. Not sure if you like scripting.

---

### Post by Xilver on 2009-12-02
Apparently I got a mail from the Cron Daemon, with the following error message inside it:

Cannot load profile '/home/webadmin/.mysqlgui/backup_profiles/dbname.mbp': Unknown object in backup file

---

### Post by Xilver on 2009-12-02
Maybe a dumb question, but what is the usual location where one would put shell scripts like a backup script?

---

### Post by ukripper on 2009-12-02
> **Xilver said:**
> Maybe a dumb question, but what is the usual location where one would put shell scripts like a backup script?

i'd put in my /home/username folder

---

### Post by Cheesemill on 2009-12-02
For all my MySQL backup jobs I use the excellent [AutoMySQLBackup]("http://sourceforge.net/projects/automysqlbackup/") script on SourceForge:

> 
A script to take daily, weekly and monthly backups of your MySQL databases using mysqldump. Features - Backup mutiple databases - Single backup file or to a seperate file for each DB - Compress backup files - Backup remote servers - E-mail logs
You should check it out, just look at the script it's all pretty well documented. All you need to do is edit a couple of lines for user, password etc and your ready to go.

---

