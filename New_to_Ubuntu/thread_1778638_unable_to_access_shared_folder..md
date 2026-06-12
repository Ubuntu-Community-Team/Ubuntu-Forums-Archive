---
title: "unable to access shared folder."
date: 2011-06-09
forum: New to Ubuntu
---

### Post by anandan2u on 2011-06-09
dear friends,
 
i had ubuntu 10.10 and windows 7 dual boot. i created a shared folder in ubuntu (on windows partition). i copied some of my important data onto it.
then i upgraded ubuntu to 11.04. i replaced ubuntu 10.10 with 11.04
now i am not able to see any files and folders inside that shared folder.
can anyone help me?
 
regards,
Anandan V

---

### Post by _0R10N on 2011-06-09
> **anandan2u said:**
> dear friends,
 
i had ubuntu 10.10 and windows 7 dual boot. i created a shared folder in ubuntu (on windows partition). i copied some of my important data onto it.
then i upgraded ubuntu to 11.04. i replaced ubuntu 10.10 with 11.04
now i am not able to see any files and folders inside that shared folder.
can anyone help me?
 
regards,
Anandan V

You can't see your files from remote machines or from the local PC?
Probably some configuration got mixed up when you updated your system. You could try disabling the shared options for that folder, and then enabling them again.

Kind regards!

---

### Post by mrhhug on 2011-06-10
did you use a new username? does your current username have read permissions on this shared drive? ```
ll /media/shareddrivename
```

---

### Post by oldfred on 2011-06-10
If it is a shared partition, it is NTFS or FAT? How are you mounting it?

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

