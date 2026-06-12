---
title: "Samba and Authentication"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by gantww on 2006-09-27
I created a folder on my desktop in Ubuntu called Backup. I then set it up as a samba share. However, when I try to map it as a drive in windows, it won't let me connect with either my password or even the root password. What do I need to do to give myself the ability to write to this directory?

Thanks,
Will

---

### Post by fstab on 2006-09-28
Samba doesn't authenticate from the system's user files.  It has its own set of users and passwords.  You create a samba user with ```
$ sudo smbpasswd -a username
```  Then set the password with ```
$ sudo smbpasswd username
```

---

