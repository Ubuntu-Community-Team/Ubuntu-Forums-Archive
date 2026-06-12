---
title: "Operation not permitted"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by rybaxs on 2009-05-20
```

user@user-desktop:/media/disk/home/user/.purple/logs$ sudo su
root@user-desktop:/media/disk/home/user/.purple/logs# chmod 777 -R *
chmod: changing permissions of `jabber': Operation not permitted
chmod: changing permissions of `yahoo/ccc/.system/2008-12-05.163444+0800PHT.txt': Operation not permitted
chmod: changing permissions of `yahoo/ccd/.system/2008-11-29.172537+0800PHT.txt': Operation not permitted
chmod: cannot access `yahoo/cce/.system/2008-11-26.163704+0800PHT.txt': No such file or directory

```

I can't copy and paste the file to another disk, how can the system does not permitted this operation even I use the root access.

---

### Post by iaculallad on 2009-05-20
What about:

```
sudo chmod -R 777 /media/disk/home/user/.purple/logs/*
```

For the Copy-and-Paste operation, try using:

```
gksudo nautilus
```

HTH.

Regards,

Ian

---

### Post by BaldwinLouis on 2009-05-20
hallo hai you thank so mchie

---

### Post by elliotn on 2009-05-20
U need to be root to paste in system files 

I use

Code

sudo su

---

### Post by rybaxs on 2009-05-20
this is the result. thanks iaculallad


```

Error while copying "2008-12-05.163444+0800PHT.txt".

There was an error copying the file into /home/user/.purple/logs/yahoo/ccc/.system.

Error reading from file: Invalid argument

```


is this file corrupted? does Ubuntu files possible from crashing and corruption? many of my files gives me "Operation not permitted and Omitting error"...

---

### Post by iaculallad on 2009-05-20
How could that be. That's your home directory so you could copy the files/folders and transfer it to another location.
Had you tried doing Ctrl+H (Show all hidden folders) while on your Home directory and Copy-Paste the .puple folder to another location? You don't need to use sudo for that, Only if you're transferring to a restricted location which requires permission.

---

### Post by rybaxs on 2009-05-20
> **iaculallad said:**
> How could that be. That's your home directory so you could copy the files/folders and transfer it to another location.
Had you tried doing Ctrl+H (Show all hidden folders) while on your Home directory and Copy-Paste the .puple folder to another location? You don't need to use sudo for that, Only if you're transferring to a restricted location which requires permission.

Yup, I've already did..

You will see a file name named jabber(see below): please do check the permission,
there is a question mark, and the owner is unknown. I can't open this file either, and lots of files are same like this. any idea?


```

root@user-desktop:/media/disk/home/user/.purple/logs# ls
aim  jabber  yahoo
root@user-desktop:/media/disk/home/user/.purple/logs# ls -l
total 2147483656
drwxrwxrwx     3 user       user             4096 2008-11-17 19:21 aim
?rwsrwsrwt 65535 4294967295 4294967295 4294967295 1970-01-01 07:59 jabber
drwxrwxrwx     5 user       user             4096 2008-12-03 19:22 yahoo
root@user-desktop:/media/disk/home/user/.purple/logs# chmod 777 jabber 
chmod: changing permissions of `jabber': Operation not permitted
root@user-desktop:/media/disk/home/user/.purple/logs# chown user jabber 
chown: changing ownership of `jabber': Operation not permitted
root@user-desktop:/media/disk/home/user/.purple/logs# 

```

---

### Post by rybaxs on 2009-05-20
[http://forum.openwrt.org/viewtopic.php?pid=51868]("http://forum.openwrt.org/viewtopic.php?pid=51868")

They said that the file is crashed or corrupted. is there any proof about this " ?rwsrwsrwt 65535 4294967295 4294967295 4294967295 " mystery?




some links:

[http://ubuntuforums.org/archive/index.php/t-135213.html](http://ubuntuforums.org/archive/index.php/t-135213.html)
[http://ubuntuforums.org/archive/index.php/t-144830.html](http://ubuntuforums.org/archive/index.php/t-144830.html)
[http://lists.debian.org/debian-user/2006/10/msg00066.html](http://lists.debian.org/debian-user/2006/10/msg00066.html)
[http://www.review-ninja.com/2009/04/fix-corrupted-volume-or-directory.html](http://www.review-ninja.com/2009/04/fix-corrupted-volume-or-directory.html)


I believed the file is being corrupted..
huhuhuhu :'(

---

