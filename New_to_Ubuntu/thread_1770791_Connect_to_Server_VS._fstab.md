---
title: "Connect to Server VS. fstab"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-05-29
Hey,

I was wondering if anyone knew the permissions difference between mounting a samba filesystem using "connect to server" and "fstab".

When mounting using "connect to server", I enter my username and and password and the servername, and it connects fine. I am able to manipulate, create, and delete files.

When mounting using fstab, I use the following line:
```
//<server>/<share>   /<path>/<to>/<mount>   cifs   username=<username>,password=<password>   0 0
```
and it mounts fine. However, I cannot create files with the proper permissions. Each file/folder has a little lock on it, and I cannot change newly created files, nor can I modify the contents of newly created directories.

Anyone know what the difference is between these two methods? I would like the mount using fstab to work the same way as it does with "connect to server".

All help is greatly appreciated.

-Kurt

---

### Post by jkurtisr32 on 2011-05-29
Found the answer. I needed to add a few more options.

Final fstab entry:
```
//<server>/<share>   /<path>/<to>/<mount>   cifs   username=<username>,password=<password>,uid=<localUser>,umask=0,rw,user   0 0
```

Legit.

-Kurt

---

