---
title: "make mount point disappear if drive/share not accessible"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by SSzretter on 2009-12-14
is it possible (how) to make a mount point disappear if a drive or smb share is not available?

for example, if I have a drive or smb share mounted to  /mnt/myfiles , if the share is not available or goes away (or drive goes away), I want /mnt/myfiles to go away  ??

(or something similar)

the problem I see now is the directory is there, it just appears blank.   the problem with that is backup software sees that and assumes all the files were just deleted...   

but the software is smart enough to know if the entire directory is gone, it doesnt assume it was all deleted.

i suppose i could put everything in a subfolder, just wondering if there is a different way?

---

### Post by Bucky Ball on 2009-12-21
How is it mounting? When you switch it on? Right click and unmount it then switch it off. Or these are not local devices but remote?

---

### Post by mikechant on 2009-12-21
> is it possible (how) to make a mount point disappear if a drive or smb share is not available?

for example, if I have a drive or smb share mounted to /mnt/myfiles , if the share is not available or goes away (or drive goes away), I want /mnt/myfiles to go away ??

I don't know about SMB, but as far as external drives are concerned if you label the partition or partitions, and then use automounting (i.e. do not define the partitions in fstab) then when the drive is plugged in it will dynamically create a mountpoint /media/LABEL where LABEL is whatever value you labelled the partition with, and this mountpoint will disappear when you umount/disconnect the drive.

---

### Post by The Cog on 2009-12-22
If mikechant's idea doesn't work for you, the only other thing I can think of is to make the backup folder one level down in the backup disk, e.g. backing up to /mnt/backup/myfiles so that when the disk is unmounted, the /mnt/backup/myfiles folder disappears entirely.

For my own backups, I have a disk labelled BACKUP so that when I plug it in, a folder /media/BACKUP appears and I back up to there, which is basically mikechant's idea.

---

### Post by SSzretter on 2009-12-22
Thanks, yes, that is what I ended up deciding to do, my mount folder is
 /mnt/mydrive

so I added a directory  /mnt/mydrive/backup

so theoretically if the mount went away the backup directory would be gone... hopefully that should work

thanks!

---

