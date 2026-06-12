---
title: "rsync error"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by amarumayo on 2009-12-12
Hi,

I am trying to backup data to an external hard drive using the rsync command.  I am running 
sudo rsync -av /home/bird/ "/media/My Passport_/bird"

I get an original Permission denied error and then after every file I get an Operation not permitted error.

rsync: readlink_stat("/home/bird/.gvfs") failed: Permission denied (13)
./
rsync: chgrp "/media/My Passport_/bird/." failed: Operation not permitted (1)
.ICEauthority
rsync: chgrp "/media/My Passport_/bird/.Xauthority" failed: Operation not permitted (1)

Not sure what I am doing wrong.  
thanks for any help

---

### Post by The Cog on 2009-12-12
When you use sudo, you run rsync as root. But gvfs only allows the owner into the .gvfs filesystem - root doesn't have access there. But I don't think .gvfs contains anything you would want to back up anyway, so you can ignore that one.

Then chgrp errors are probably because you are copying the files to an ntfs or fat filesystem that doesn't support group ownership, so I guess you can ignore those warnings too.

If you want to save everything to a fat or ntfs filesystem, you might be better off using tar to create a tar file that can store the file ownership and permissions info as well.

---

### Post by Dennis N on 2009-12-12
> **amarumayo said:**
> Hi,

I am trying to backup data to an external hard drive using the rsync command.  I am running 
sudo rsync -av /home/bird/ "/media/My Passport_/bird"...

Not sure what I am doing wrong.  
thanks for any help

How is the external drive formatted? FAT, NTFS, EXT3/EXT4?

Also, I wouldn't use sudo with rsync.

---

