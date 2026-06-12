---
title: "How to set group and permissions when partition mounts"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by medic8ted on 2009-02-16
I have been messing with this fstab for too long now so I'm throwing in the towel and asking for help.  I have been on every fstab help site I can find and its just not working for me.  I want to have /dev/sda1 mount at boot as owner=root and group=root and /dev/sda3 mount as owner=me and group=users.  Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda2
UUID=5db1a871-d0e9-4508-bce2-561121ef213e  /              ext3         relatime,errors=remount-ro          0  1  
# /dev/sda5
UUID=f784271a-f6bf-46a7-aaf9-7448497e60d8  none           swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/sda1                                  /media/sda1    ext3         auto,nouser  0  0  
/dev/sda3                                  /media/sda3    ext3         auto,nouser  0  0  
```

I have changed the options from user, nouser, gid=, nosuid, etc, etc...for hours and they wont mount as I want it.  I don't want to chown or chmod it every time it mounts.

---

### Post by vanadium on 2009-02-16
fstab is not the place to regulate that. Just change the ownership of the directories on the drives, or the mount point itself if the entire drive is to belong to a single user.

Your fstab lines for sda1 and sda3 are neat and simple, and all right. You can still remove "nouser", because this is already implied by "defaults". Moreover, I advise you to change the trailing 0 to 2 to have the drives checked (quickly, and only once in a while slowly) during startup.

To change ownership and permissions, you can use a nautilus instance with super user (administrator) permissions. Launch that with the command "gksudo nautilus". Close that nautilus window as soon as you are done.

---

### Post by medic8ted on 2009-02-16
Will the same ownership and group reappear each time its mounted in the future?

---

