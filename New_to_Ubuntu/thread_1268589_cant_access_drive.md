---
title: "cant access drive"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by gridd on 2009-09-17
I have just formatted and partitioned a large drive with ext2 and ext3

but when mounted a locked lost& found folder denies access also root folder states i dont have privileges, to access folder.

After using gparted it asked me if i wanted to store a log file I think it was in root. Has this caused the problem.

---

### Post by rob-ward on 2009-09-17
I'm not 100% sure what you mean, is your drive mounting? if so to what directory is it mounting?

What output do you get when you run these commands?

```
mount
```

and

```
sudo fdisk -l
```

and

```
cat /etc/fstab
```

---

### Post by arapa on 2009-09-17
The root folder is the root user's home directory (like your /home/*your_user_name* ). 

You'll need to be authenticated as root to access the 'root' directory. Same goes for the lost&found directory. Lost & found is used to store bad files that are discovered after a filesystem check. 

see [The Linux filesystem explained http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")

The access denied message for these folders is normal and correct.

---

