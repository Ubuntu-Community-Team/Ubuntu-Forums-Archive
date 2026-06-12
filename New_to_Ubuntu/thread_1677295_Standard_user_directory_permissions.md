---
title: "Standard user directory permissions"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by awp2513_ on 2011-01-28
Hi,


As a standard user, I can create directories in my home directory and add files to them. However, when I list the permissions on the directory and the file, I get the following

drwr-xr-x /home/user/tempdir
-rw-r--r-- /home/user/tempdir/tempfile.txt

I can, however, edit the file and remove/rename both the directory and the file.

Why do the permissions appear this way (I would expect w permission)? Is there some restriction I have not run across?

I'm using Ubuntu 10.04 Netbook Remix if it makes a difference.

Thanks in advance!

---

### Post by luvshines on 2011-01-28
> **awp2513_ said:**
> Hi,


As a standard user, I can create directories in my home directory and add files to them. However, when I list the permissions on the directory and the file, I get the following

drwr-xr-x /home/user/tempdir
-rw-r--r-- /home/user/tempdir/tempfile.txt

I can, however, edit the file and remove/rename both the directory and the file.

Why do the permissions appear this way (I would expect w permission)? Is there some restriction I have not run across?

I'm using Ubuntu 10.04 Netbook Remix if it makes a difference.

Thanks in advance!

But there is a 'w' there in both directory and file. Do you want only 'w' ?

Those are the default permissions for directory and files with a umask of 0022 on the system

Have a look here [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

### Post by asmoore82 on 2011-01-28
The permissions summary is 3 triplets - {user}{group}{others}

drwxr-xr-x = directory, read/write for owner, read only for everyone else
-rw-r--r-- = file, read/write for owner, read only for everyone else
-rwxr-xr-x = program, execute/write for owner, execute only for everyone else

Your "umask" setting is the default mode of newly created files.
The normal "umask 022" means that all new files will be read-only to everyone else.

A "umask 077" would mean that all new files are completely denied to everyone else.
But, one only needs write permission to that folder in order to delete the files.

---

