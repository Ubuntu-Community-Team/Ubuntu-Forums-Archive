---
title: "Permissions messed up, can't run sudo"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by CompBio on 2008-12-10
I really seem to have stepped in it last night.  I was trying to run some python code and got a permissions error on one of the installed packages.  So I went to /usr/bin/python2.5 and started to do a "sudo chmod -R 755", but my sleepy head said, "hey, let's do that for everything!"  So I did "cd .." and then did "sudo chmod -R 755".

Now I can't use sudo -- I get a permissions error.  Also, when I shut down, I now get a message saying that an assertion failed: the hash table is null when it shouldn't be.

How can I get my system back the way it was?  I have no idea what the permissions should be on the /usr tree.

---

### Post by Titan8990 on 2008-12-10
That kind of user error pretty much makes the system toast. Backup what you need and reformat.


Edit: Added missing word so my post makes more sense.

---

### Post by Michael.Godawski on 2008-12-10
Well this is my /usr permission tree:
```
michael@michael-laptop:/usr$ ls -la
total 184
drwxr-xr-x  12 root root  4096 2008-10-31 11:55 .
drwxr-xr-x  20 root root  4096 2008-11-30 10:14 ..
drwxr-xr-x   2 root root 57344 2008-12-10 14:56 bin
drwxr-xr-x   2 root root  4096 2008-11-19 13:53 games
drwxr-xr-x  36 root root  4096 2008-11-21 18:58 include
drwxr-xr-x 200 root root 65536 2008-12-10 14:56 lib
drwxr-xr-x   3 root root  4096 2008-10-31 11:55 lib64
drwxr-xr-x  10 root root  4096 2008-10-29 23:53 local
drwxr-xr-x   2 root root 12288 2008-12-04 22:12 sbin
drwxr-xr-x 322 root root 12288 2008-12-04 10:36 share
drwxrwsr-x   8 root src   4096 2008-11-30 10:13 src
drwxr-xr-x   2 root root  4096 2008-10-29 23:58 X11R6
michael@michael-laptop:/usr$ 
```

But like Titan8990 eloquently pointed out, your system is nuked...

I do not know if you want to manually restore the permissions via the LiveCD sessions and if this is will work in the frist place...

---

### Post by CompBio on 2008-12-10
That was my first inclination, but I was hoping there was some lovely utility I didn't know about that would restore correct file permissions.

---

### Post by pfoff on 2011-03-06
Look there for that kind of buggy users:P
[http://ubuntuforums.org/showthread.php?p=10528468#post10528468](http://ubuntuforums.org/showthread.php?p=10528468#post10528468)

---

