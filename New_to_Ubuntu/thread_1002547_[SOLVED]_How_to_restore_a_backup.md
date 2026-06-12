---
title: "[SOLVED] How to restore a backup"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-05
I have read many posts saying to run a command to first backup a file like fstab. However I have never seen how to restore the backup if something goes wrong. 
I have never needed to restore one of these backups but I am curious on how I would if I needed to.

---

### Post by stephanvaningen on 2008-12-05
If people suggest to backup a file, mostly what they do is copy it to a file in the same directory, like:
 ```
sudo cp /etc/fstab /etc/fstab_backup20081204
```
*The 'sudo' since user has no write/create permissions in /etc/ normally.*

To restore, just copy-back:
 ```
sudo cp /etc/fstab_backup20081204 /etc/fstab
```

---

### Post by scorp123 on 2008-12-05
> **nakama85 said:**
>  However I have never seen how to restore the backup if something goes wrong This here should cover it all:
[http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

