---
title: "file and folder permissions... ..."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by techno-mole on 2009-11-19
hello.

what would be the best way to change the permissions on a load of files and folders in one go, for example if i have a folder with several folders inside and various types of files in the folders (mp3 files, text files etc) and the permissions were different for some of the contents of the main folder ?

i know if you click on the properties tab of a folder or file you can set permissions that way, but i have found that clicking the " apply permissions to enclosed files " doesnt seem to work for me, even if i use "gksudo nautilus" to do it

the problem is that some how a back up folder (with the contents of a home directory) has had all the permissions mixed up, so some files with in it now can only be used by root, this is the same with some of the folders as well.

so what would be the best way to change the permissions of the entire folder and its contents from root to a user ?

cheers

---

### Post by viralmeme on 2009-11-19
> **techno-mole said:**
> so what would be the best way to change the permissions of the entire folder and its contents from root to a user ?
$sudo chown -hR user:group /directory

---

### Post by ~sHyLoCk~ on 2009-11-19
Try:


```
sudo chown username:username -R /pathtofolder
```

Guessing your username is a part of that group.

---

### Post by techno-mole on 2009-11-19
cheers for the help, all sorted now, no idea how the permissions got mixed up though, never mind.

many thanks

---

