---
title: "Permissions on /etc/fstab"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by acmebcn on 2011-01-16
Hi all,

In a dual Vista - Ubuntu 10.10 system, i'm trying to setup the Vista partitions (ntfs) to be mounted on startup in order to allow some linux applications to access data. The fstab line looks like this:
```
#Entry for /dev/sda5 :
#UUID=4CD4AEBBD4AEA6A4      /media/win_d  ntfs-3g  users,nosuid,nodev,default_permissions,locale=es_ES.utf8
```It works almost fine. The only issue is that its owned by root and the gnome recycle bin utility doesn't work. When I delete any file from gnome explorer, the system complains about not being allow to access the trash directory.

What can I do to mount it with the right  permissions? I tried to switch the default_permissions to umask=777 but it's not working.

Thanks

---

### Post by srs5694 on 2011-01-16
The umask (and fmask and dmask) options set the permissions that are *removed* from files and directories (or files only for fmask or directories only for dmask), so if you wanted 777 permissions, you'd set umask=0, not umask=777. Less extreme permissions are of course possible, too, and may be appropriate. (For files, I'd remove execute permissions, since Linux binaries aren't likely to be stored on an NTFS partition, so fmask=111 or higher, depending on your needs.)

---

### Post by acmebcn on 2011-01-17
Perfect. Now it works!

Thanks a lot,

Acmebcn

---

