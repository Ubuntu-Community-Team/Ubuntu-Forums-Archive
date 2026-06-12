---
title: "Odd permission behaviour"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by MockY on 2009-03-31
This is some of the files on my test server:

```

-rw-r--r-- 1 user1 www-data  154 2009-03-23 16:49 config.php
drwxr--r-- 2 user1 www-data 4096 2009-03-23 16:42 css
drwxr--r-- 4 user1 www-data 4096 2009-03-31 19:42 demo
drwxr--r-- 2 user1 www-data 4096 2009-03-23 16:42 images
-rw-r--r-- 1 user1 www-data 3086 2009-03-23 16:57 index.php
-rw-r--r-- 1 user1 www-data  179 2009-03-23 17:03 logout.php

```

Hitting the root directory ([http://localhost/](http://localhost/)) works fine. The index.php is displayed just fine through a browser and the css file is loaded. However, if I try [http://localhost/demo/](http://localhost/demo/) I get a 403 permission error. It has the same permissions as you can see from what I posted. I have to do a chmod -R 755 in order for the browser to show the content.

What is going on here? This does not make any sense what so ever.

---

### Post by asmoore82 on 2009-03-31
for Directories only, read *& execute* permissions go hand in hand
```
chmod a+rX */
```

---

### Post by rybaxs on 2009-03-31
403 is forbidden, the files are there..

try
[http://localhost/demo/index.php](http://localhost/demo/index.php)

-rw-r--r-- this is not 755

chmod -R 755

try with * asterisk

---

### Post by rybaxs on 2009-03-31
try 
```

~$ chmod 777 -R *

```

---

### Post by MockY on 2009-03-31
I just want the files to be readable for the user. I don't want any higher than 7444, which is what I have on all the files and folders that works. And since the .css file is located in a read only directory and it works, why does the demo directory need to be executable?

---

### Post by asmoore82 on 2009-03-31
Oops, sorry I just the rest here

> **MockY said:**
> I have to do a chmod -R 755 in order for the browser to show the content.

you should never combine the -R "recursive" switch of `chmod` with literal permissions such as "=rwx" or "755"
the reason being that directories need execute permissions to behave as you would expect but files do not

a capital ``X'' to chmod is the key to recursive commands -
it means execute only on directories ...
to repair the damage done by a recursive 755:
```
sudo chmod -R a-rwx *dir*
sudo chmod -R u+rwX,go+rX *dir*
```
-OR-
```
find *dir* -type f -print0 | xargs -0 chmod a-x
```

---

### Post by MockY on 2009-03-31
Thank you for the information asmoore82. Very educational.
But how is it possible to have read only permissions on the css folder and yet the css file inside it is displayed? The same with the images directory. The images that are called for in the index.php file are displayed without any execute permissions on the folder. I have to have execute permissions in the demo directory in order to display the index file within it.

I'm a bit confused.

---

### Post by asmoore82 on 2009-03-31
the way it was originally explained to me was that
"read" permissions for a directory will let you "see/list" the files in it; but
"execute" permission is required to "descend into" the directory and manipulate those files**

I can't think of a case where one would ever want "read" *without* "execute" on a directory;
even write-only access to directory is more common in comparison - for a "Dropbox" effect -
and even then, "execute" permission is required for it to behave as expected.

**what is important to note here is that even taking a quick little glance in a file
*technically* constitutes **opening** the file for *reading* - 
and you have be able to "descend into" that parent directory before you can open the file.

---

### Post by rybaxs on 2009-03-31
great!
asmoore82..

---

### Post by Meson on 2009-03-31
Maybe this will shed some light on the situation:

Setup:
```

tmp$ mkdir testdir
tmp$ echo Hello, World! > testdir/testfile
tmp$ chmod 500 testdir

```

Read and Execute:
```

tmp$ ll 
total 4
dr-x------ 2 matt matt 4096 2009-03-31 23:36 testdir
tmp$ ll testdir
total 4
-rw------- 1 matt matt 14 2009-03-31 23:36 testfile
tmp$ cat testdir/testfile
Hello, World!

```

Read only:
```

tmp$ chmod 400 testdir
tmp$ ll
total 4
dr-------- 2 matt matt 4096 2009-03-31 23:36 testdir
tmp$ ll testdir
ls: cannot access testdir/testfile: Permission denied
total 0
-????????? ? ? ? ?                ? testfile
tmp$ cat testdir/testfile
cat: testdir/testfile: Permission denied

```

Execute only:
```

tmp$ chmod 100 testdir
tmp$ ll
total 4
d--x------ 2 matt matt 4096 2009-03-31 23:36 testdir
tmp$ ll testdir
ls: cannot open directory testdir: Permission denied
tmp$ cat testdir/testfile
Hello, World!

```

In each case, "ll" displays the permissions on the directory, "ll testdir" displays info about the files within the directory, and "cat testdir/testfile" attempts to access a file within the directory.

---

### Post by MockY on 2009-03-31
> **asmoore82 said:**
> the way it was originally explained to me was that
"read" permissions for a directory will let you "see/list" the files in it; but
"execute" permission is required to "descend into" the directory and manipulate those files**


Thanks for the information. That explains it.

---

### Post by asmoore82 on 2009-03-31
I really like that "execute only" example :lol:

"Do what you will with the file but you had better know its name well"

---

### Post by MockY on 2009-04-01
Once in a while I get a lower s or capital S in the permissions. I read it is special permissions, but what kind of special permissions, and how do I go about to remove it?

---

### Post by Meson on 2009-04-01
An 's' where the 'x' typically goes for the owner means that when an "other user" executes the file, it will be executed as if the owner was doing it.  An 's' where the 'x' typically goes for the group means that when an "other user" executes the file, it will have the permissions of the group.

When a directory has the setgid permission set, any file created in the directory will inherit the group of the directory, not the user's default group.

An upper case 'S' in either case means that the setuid/setgid permission is set, but NOT the execute permission.

Also note that the setuid and setgid bits are not effective for shell scripts.  They only work for binary executables.

---

