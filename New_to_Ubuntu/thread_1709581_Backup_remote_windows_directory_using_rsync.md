---
title: "Backup remote windows directory using rsync"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by japhyr on 2011-03-18
Hello,

I have been using rsync to maintain local backups for a while now.  Now I have a remote directory on a windows computer that I want to begin backing up.  I tried backing up that directory from ~/.gvfs, but that directory does not seem to consistently maintain a link to the remote directory.

I can access the directory in nautilus with an address like "smb://remote_host/path/to/directory".  Is there a way to use an address like that in an rsync command, something like```
rsync -av smb://remote_host/path/to/directory /local/path/to/backup
```Most of the online references seem to talk about backing up a remote linux machine to a local windows machine.

---

### Post by wizard10000 on 2011-03-18
> **japhyr said:**
> Is there a way to use an address like that in an rsync command, something like```
rsync -av smb://remote_host/path/to/directory /local/path/to/backup
```

The short answer is no  :(

It can be done but you've gotta do it a little differently, as rsync doesn't understand the path.  You've gotta mount the remote share into the local filesystem and then run rsync.

---

### Post by japhyr on 2011-03-18
> mount the remote share into the local filesystem and then run rsync

That makes sense; I have a number of partitions on my ubuntu desktop, and I use fstab to mount certain partitions.  How do I mount the remote share from a script?

---

### Post by wizard10000 on 2011-03-18
> **japhyr said:**
> That makes sense; I have a number of partitions on my ubuntu desktop, and I use fstab to mount certain partitions.  How do I mount the remote share from a script?

Depends on whether it's an attended or unattended backup as root has to mount the share - if it's gonna be an unattended backup you might want to mount the share as root in /etc/crontab, run your backup from the same place and then unmount the share.

If it's a manual backup you're gonna have to be there to cough up the superuser password  ;)

---

### Post by japhyr on 2011-03-18
It's an unattended backup.  I got the backup working through crontab yesterday, but that was only after I had logged in and accessed the remote directory manually.  I believe the initial manual access mounted the remote directory to .gvfs, which the script used as a source for the backups.  The cron jobs stopped working after I logged out, I believe because the remote directory was no longer mounted to .gvfs.

So, it sounds like I want to:
[LIST]
[*]mount the share as root, in crontab
[*]run the backup
[*]unmount the share
[/LIST]The only part of this I don't understand how to do is mount the share from a script.  How do I do that?

---

### Post by wizard10000 on 2011-03-18
Since you're backing up the Windows share you can mount it read-only.

Create a mount point - let's call this one /mnt/windows

then in crontab as root -

```
mount -t cifs //server-name/share-name /mnt/windows -o username=shareuser,password=sharepassword
```

then run your rsync job, then all you do is 

```
umount /mnt/windows
```

Try it from a terminal window so you get the hang of it before you put it in crontab, though.

---

### Post by japhyr on 2011-03-21
After installing smbfs, this worked perfectly.  Thank you!

---

### Post by wizard10000 on 2011-03-21
Oops.  I've had smbfs installed so long I forgot to tell you you had to install it  ;)

Glad you got it fixed.

---

