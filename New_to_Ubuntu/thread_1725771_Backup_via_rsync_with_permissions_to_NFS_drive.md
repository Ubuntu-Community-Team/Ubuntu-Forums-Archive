---
title: "Backup via rsync with permissions to NFS drive"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by yanewby on 2011-04-10
I have just begun my first steps in maintaining a home server and have set up some backup drives on my server to allow desktop users to save things there via NFS.

My problem is I would like to be able to make some of these things "read-only" to the person who put them there.

I am currently using this rsync command to backup a folder and its contents:

```
rsync -avze ssh --progress /home/userondesktop/folderone/ useronserver@192.168.1.xxx:/BackupDisk1/folderone
```

When I log in to my server and check the permissions on the files in folder /Backupdisk1/folderone the owner is given as "useronserver" and the group as "1000".

On the desktop machine they were copied from the permissions for both owner and group were "userondesktop" which has a uid of 1000 and a gid of 1000.

Finally some questions (if you are still with me):

1) Why do the rsync'd files have the owner as "useronserver" and not "1000"?  Is this because I have SSH'd in as "useronserver"?  How do I SSH the files with a user that does not exist on the server or ensure that only root (and userondesktop) can read the files?  I understand that root on Ubuntu server does not have a password so [email]root@192.168.1.xxx[/email] did not work for me.

2) What is the easiest way of trying to backup the files/folders whilst maintaining all the permissions?  The backup server will *not* always be switched on.

3) Are there any books you would recommend to help me get started in Ubuntu server management?  The Ubuntu Server Guide ([https://help.ubuntu.com/10.10/serverguide/C/index.html](https://help.ubuntu.com/10.10/serverguide/C/index.html)) is very out of date with many of the things I have tried in it not working.

Thanks (and sorry for all the questions at once)!

---

