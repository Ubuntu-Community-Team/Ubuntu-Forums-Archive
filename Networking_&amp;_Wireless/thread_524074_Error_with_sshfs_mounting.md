---
title: "Error with sshfs mounting"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by fieldstone on 2007-08-12
I've been trying to follow several different howtos on mounting via sshfs. My user account is a member of the fuse group, but I keep getting the following error message:

fusermount: failed to chdir to mountpoint: Permission denied

I've tried several different mount points, but it makes no difference, and there's nothing on google about this error either. Does anyone know what it means?

---

### Post by ken_fallon on 2007-09-24
You may have created the mount point as the root user so you wouldn't have permissions to change to that mount dir as a normal user.

You should try ans change the owner of the directory to your user name

e.g: asuming your login name is joe and the directory where you want to mount to is s/media/sshfs 

chown joe /media/sshfs

---

