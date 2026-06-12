---
title: "fstab file"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by rapaghgh on 2009-02-23
Hello

Here is part of my fstab file :
/dev/sda8 /home ext3 defaults 0 2
/dev/sda10 /mnt/document ext3 user,rw,dev,exec,suid,auto,async 0 2
/dev/sda12 /mnt/film ext3 user,rw,dev,exec,suid,auto,async 0 2
/dev/sda11 /mnt/music ext3 user,rw,dev,exec,suid,auto,async 0 2

But I cannot write anything to /mnt/document or others as a user.
cp: cannot create regular file `/mnt/document/a.tex': Permission denied

Could someone tell me how to correctly set the options that user can write on these partitions?

Thanks

---

### Post by Bölvaður on 2009-02-23
you need to give your self write permissions. Either by right clicking &#8594; properties &#8594; change user to you and perhaps allow other users to write and read the content of the directories.

if you want to do it the gui way : Alt+F2 &#8594; gksu nautilus /mnt

if you want to do it the cli (terminal) way:

```
cd /mnt
ls -l  [COLOR="Orange"] &#8592; this lets you see the user and permissions of files and directories, w = write, r = read, x = execute/list, first comes user, then group and then all others.[/COLOR]
sudo chown **rapaghgh** document/  [COLOR="Orange"] &#8592; this changes the owner of the directory to you[/COLOR]
sudo chmod 766 document/  [COLOR="Orange"] &#8592; this gives you full rights, and all others read/write permission[/COLOR]
ls -l  [COLOR="Orange"] &#8592; view the difference you have made[/COLOR]
```

*added*
you might need to change permissions recursively but I would try everything else before doing it.

---

### Post by ptn107 on 2009-02-23
You need to make sure you have write access to it.  See above post.  I recommend the terminal way, as giving your self root powers to nautilus just screams disaster if you mess with something your not supposed to.

---

### Post by hot_rod_hippie on 2009-02-23
It seems that your fstab options are good.  I'd guess your permissions/ownership needs to be changed

try this:
ls -l /mnt

the output should show something like the following:
drwxr-xr-x 2 user group 4096 2008-11-24 13:28 Documents

chown and chmod commands will fix that

Good luck

---

### Post by rapaghgh on 2009-02-23
yes, that works. Thanks a lot for all response.

---

