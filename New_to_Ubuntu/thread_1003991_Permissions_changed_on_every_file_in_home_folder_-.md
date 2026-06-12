---
title: "Permissions changed on every file in home folder - Help!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by acl123 on 2008-12-06
I was following some instructions to get a program installed but I seem to have messed up the permissions on all the files in my home directory.
If I try to copy or move anything I get "permission denied".

What can I do?

This is an example of a directory in my home folder (when I run *ls -l*):

```
drwx------   2 andrew andrew  4096 2008-11-10 00:27 Scripts
```

(My username is *andrew*)

---

### Post by Paqman on 2008-12-06
This will restore everything to how it should be:
```

sudo chown -R andrew:andrew /home/andrew
chmod -R 755 /home/andrew
chmod 644 /home/andrew/.dmrc

```

---

### Post by utsuprainfra on 2008-12-06
> **acl123 said:**
> I was following some instructions to get a program installed but I seem to have messed up the permissions on all the files in my home directory.
If I try to copy or move anything I get "permission denied".

What can I do?

This is an example of a directory in my home folder (when I run *ls -l*):

```
drwx------   2 andrew andrew  4096 2008-11-10 00:27 Scripts
```

(My username is *andrew*)

well, the quick answer is:

sudo chown -R $yourusername /path/to/home
and
sudo chmod -R 700 /path/to/home

and then if you need to you can change the permissions to add them as you need them.


#edit#

you are andrew?  you may have to change the group as well, with

chgrp -R $yourusername /path/to/home

---

### Post by utsuprainfra on 2008-12-06
755 will allow everyone else to read and execute your files.

---

### Post by Paqman on 2008-12-06
> **utsuprainfra said:**
> 755 will allow everyone else to read and execute your files.

Which is the default, IIRC. 700 and 750 are both ok as well though.

644 for .dmrc is important though. It has to be set to that, or you won't be able to log in.

---

### Post by acl123 on 2008-12-06
Great thanks guys

---

### Post by Patrick793 on 2008-12-06
If you want these will restore all files and folders to the default permissions by finding all folders and changing permissions. Same with files.

Folders:
```
find . -type d -exec chmod 755 {} \;
```

Files:
```
find . -type f -exec chmod 644 {} \;
```

---

### Post by Paqman on 2008-12-06
> **Patrick793 said:**
> If you want these will restore all files and folders to the default permissions by finding all folders and changing permissions. Same with files.

Folders:
```
find . -type d -exec chmod 755 {} \;
```

Files:
```
find . -type f -exec chmod 644 {} \;
```

That's probably a better (ie: less heavy-handed) approach than what I posted. Cheers!

---

