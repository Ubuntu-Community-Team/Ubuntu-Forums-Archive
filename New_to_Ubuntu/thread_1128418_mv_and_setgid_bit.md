---
title: "mv and setgid bit"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by bikrus on 2009-04-17
Hi everybody!

Please, explain next behavior.

Create 2 directories: a and b. Set setgid bit on a.

```
tuser@rnb:/$ cd /home
tuser@rnb:/home$ sudo mkdir a
[sudo] password for tuser: 
tuser@rnb:/home$ sudo chown tuser.tuser a
tuser@rnb:/home$ sudo chmod g+s a
tuser@rnb:/home$ ls -la
total 60
drwxr-xr-x   13 root   root    4096 2009-04-17 21:12 .
drwxr-xr-x   23 root   root    4096 2009-04-17 08:42 ..
drwxr-sr-x    2 tuser  tuser   4096 2009-04-17 21:12 a
tuser@rnb:/home$ sudo mkdir b
tuser@rnb:/home$ sudo chown tuser.tuser b
tuser@rnb:/home$ ls -la
total 64
drwxr-xr-x   14 root   root    4096 2009-04-17 21:13 .
drwxr-xr-x   23 root   root    4096 2009-04-17 08:42 ..
drwxr-sr-x    5 tuser  tuser   4096 2009-04-17 21:17 a
drwxr-xr-x    3 tuser  tuser   4096 2009-04-17 21:17 b
```

Create dir c in b and move it to dir a.

```
tuser@rnb:/home$ cd b
tuser@rnb:/home/b$ mkdir c
tuser@rnb:/home/b$ ls -la
total 12
drwxr-xr-x  3 tuser tuser 4096 2009-04-17 21:14 .
drwxr-xr-x 14 root  root  4096 2009-04-17 21:13 ..
drwxr-xr-x  2 tuser tuser 4096 2009-04-17 21:14 c
tuser@rnb:/home/b$ mv c /home/a
tuser@rnb:/home/b$ cd /home/a
tuser@rnb:/home/a$ ls -la
total 12
drwxr-sr-x  3 tuser tuser 4096 2009-04-17 21:14 .
drwxr-xr-x 14 root  root  4096 2009-04-17 21:13 ..
drwxr-xr-x  2 tuser tuser 4096 2009-04-17 21:14 c
```

Setgid bit have been not applied to c... Create dir d in dir with setgid:

```
tuser@rnb:/home/a$ mkdir d
tuser@rnb:/home/a$ ls -la
total 16
drwxr-sr-x  4 tuser tuser 4096 2009-04-17 21:14 .
drwxr-xr-x 14 root  root  4096 2009-04-17 21:13 ..
drwxr-xr-x  2 tuser tuser 4096 2009-04-17 21:14 c
drwxr-sr-x  2 tuser tuser 4096 2009-04-17 21:14 d
```

Setgid bit applied... Ok. Move on as c dir not moving it but copy:

```
tuser@rnb:/home/a$ cd /home/b
tuser@rnb:/home/b$ mkdir e
tuser@rnb:/home/b$ cp -r e /home/a
tuser@rnb:/home/b$ ls -la /home/a
total 20
drwxr-sr-x  5 tuser tuser 4096 2009-04-17 21:17 .
drwxr-xr-x 14 root  root  4096 2009-04-17 21:13 ..
drwxr-xr-x  2 tuser tuser 4096 2009-04-17 21:14 c
drwxr-sr-x  2 tuser tuser 4096 2009-04-17 21:14 d
drwxr-sr-x  2 tuser tuser 4096 2009-04-17 21:17 e
tuser@rnb:/home/b$
``` 

Setgid applied to copied dir too. But not to moved.

Please explain. Is it bug or I've misunderstood something.

---

### Post by ibuclaw on 2009-04-17
OK, time to explain the difference between Copy and Move ;)

If you **copy** a file from one area of the filesystem to another, or across different filesystems, that file inherits the ownership of the user copying it, and the sticky permissions of the directory it is being copied to (if you are copying a directory).

ie:
[PHP]
$ ls -ld /usr/share/pixmaps/
drwxr-xr-x 15 root root 12288 2009-04-17 08:46 /usr/share/pixmaps/
$ cp $_ ./
$ ls -l
drwxr-sr-x 15 iain iain 12288 2009-04-17 20:20 pixmaps
[/PHP]

If you **move** a file from one area of the filesystem to another or from one filesystem to another, then that file keeps its ownership and permission attributes.

Regards
Iain

---

### Post by bikrus on 2009-04-18
Thanks for explanation. 

But could you (someone) please point me the place in mans or OFFICIAL(!) documentation on file/dir permissions behavior with copy, move or delete operations? Or is it kernel behavior? Or is it depends on filesystem? (in my case ext3)

---

### Post by ibuclaw on 2009-04-19
This behaviour that you see is true to all OS's, even Windows (if you use business/server editions that has enforced NTFS file permissions).

Best way to think about it is this:

**cp** is a tool to create a new file that contains the exact same encapsulated data of the file you are copying.

**mv** is just a renaming tool.

Regards
Iain

---

