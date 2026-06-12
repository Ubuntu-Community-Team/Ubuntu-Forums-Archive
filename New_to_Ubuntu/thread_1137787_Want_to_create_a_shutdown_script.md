---
title: "Want to create a shutdown script"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Mick8882003 on 2009-04-25
I want to create a script that will backup all my files when I shut down the computer.

It should: copy all the files in my home directory and then shut the computer down

The idea is I run the script when I am finished for the day and then I have daily backups.

Cheers Mick

---

### Post by some_random_noob on 2009-04-25
I've never written a backup script before, but these links might help:

[http://linuxcommand.org/](http://linuxcommand.org/)

[http://ubuntuforums.org/archive/index.php/t-80790.html](http://ubuntuforums.org/archive/index.php/t-80790.html)

Edit: It should be easy to do your home directory by itself. Also, be sure to check out:

* Man page
```
man shutdown
```

* Command to shutdown
```
sudo shutdown -h -P now
```

---

### Post by blueridgedog on 2009-04-25
Well, if you have the backup part down, then the shutdown part would be:

```
/sbin/shutdown -h now
```

So, by way of example, the script would look like this:
```

#!/bin/bash
rsync -av /documents/ /mnt/Backup/Documents --delete
/sbin/shutdown -h now
```

Obviously you will need to change your backup command to reflect your data and your target (I use a backup drive mounted as /mnt/Backup and I backup a dedicated data drive mounted at /documents).

---

### Post by Mick8882003 on 2009-04-25
would 
rsync -av /mick /sda1/backup --delete
work?

Also is it a good idea to copy the home directory for a backup? And would simply copying it back be a successful restore?

---

### Post by some_random_noob on 2009-04-25
> **Mick8882003 said:**
> 
Also is it a good idea to copy the home directory for a backup? And would simply copying it back be a successful restore?

A copy of the home folder would back up most of your application settings (for your browser, email, desktop environment, etc). So yes it's not a bad idea... but I would personally choose to backup data only, because the user settings don't really need backing up.

---

### Post by Mick8882003 on 2009-04-26
How do i dump it on the second hard disk

I tried /dev/sda1 in terminal to check if thats the right disk, but it says permission denied??

---

### Post by blueridgedog on 2009-04-26
You can't write to it unless it is mounted.  What is the output of the 

```
mount
```

command?

```
Also what is the output of 

sudo fdisk -l
```

---

### Post by blueridgedog on 2009-04-26
> **Mick8882003 said:**
> would 
rsync -av /mick /sda1/backup --delete
work?

Also is it a good idea to copy the home directory for a backup? And would simply copying it back be a successful restore?

No it will not unless you have a drive mounted at /sda1/backup.

You want to use rsync -av /sourcefiles /destination

So, perhaps:

```
rsync -av /home/mick /path/to/mounted/drive/mick 
```

Also, don't use the --delete option until it is debugged and working.

---

