---
title: "Permission Problems Moutning Windows Share as Root"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by tendrousbeastie on 2008-11-01
Hello boys and girls,


I have a problem while mounting a share from a Windows server.

The mounts works fine, and I can access the Windows share via its mount point in /shares/server/sharename/

However, I have to run the mount command as root (i.e. sudo mount ....)

This seems to result in all files I subsequently create in the share folder being writable by root only. So if I create a new file in the share folder I cannont then save over it when editing that file with software on my linux box.

Is there any obvious way to fix this? Can I make my mount command cause files to be created with write permission for other users?

The mount command I'm running is (blanked out the passwords):

sudo mount -t smbfs -o username=xxxx,password=xxxx //10.0.0.6/www /shares/pilate/www


Thanks for any help.

---

