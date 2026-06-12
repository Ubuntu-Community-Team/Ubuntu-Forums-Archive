---
title: "Samba Create Mask = 0755 not working.  New files/folder are read-only"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by the_dingman on 2013-12-04
Greetings,

I have files on an Ubuntu desktop machine shared with samba.  Permissions are set to give full read/write access to all users accessing the share.  From a Windows machine, everything works fine.  However when accessing from another Ubuntu machine, I have full 777 permissions to all existing files and folders, however any new files or folders I create, I have read-only access to.

How do I change permissions in Ubuntu to set new files created in these shares to give me full access?

Thank you

---

### Post by the_dingman on 2013-12-04
Greetings,

I have a samba share that despite what appears to be proper settings, all new files or folders created end up as read-only.  Windows ignores the issue, but Ubuntu machines (including the host machine) see all new documents created remotely as set to read-only.

My smb.conf:

```

comment=Theta Shared Folder
path = /mnt/md0/theta
browsable = yes
guest ok = yes
read only = no
create mask = 0755

```

Permissions via ls on new files created:
```

drwxr-xr-x  2 1000 nogroup          0 Dec  4 20:14 Untitled Folder 2

```

Permissions via ls on old files:
```

drwxrwxrwx  2 1000 nogroup          0 Nov 25 19:48 thetadata

```

Thanks in advance.

---

### Post by sergey.sukhorukov on 2013-12-04
Did you try setup the share with user permissions. Try "valid users" for share and connect with this user to share. Why did you use "guest ok"?

---

### Post by CharlesA on 2013-12-04
Looks like you are missing directory mask.

Give [this]("http://charlesa.net/tutorials/ubuntu/samba3-ubuntu.php") a read.

---

