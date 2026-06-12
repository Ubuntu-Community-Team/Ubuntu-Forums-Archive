---
title: "how to repair this problem[connection, twinkle]"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Gigcsjcx on 2008-12-28
please check the pics for more detail.

---

### Post by Michael.Godawski on 2008-12-28
> **Gigcsjcx said:**
> please check the pics for more detail.

hi Gigcsjcx,

three options. 
First try to reinstall the application via Synaptic. If this does not work
try to remove the files shown in the error message
```
$ cd /home
$ rm .DCOPserver*
```If this does not work, change the ownership of this folder with
```
sudo chown linux:linux /home/linux/.kde
```assuming your username is linux.

---

### Post by namdung on 2008-12-28
[http://ubuntuforums.org/showthread.php?t=261872](http://ubuntuforums.org/showthread.php?t=261872)

---

### Post by Gigcsjcx on 2008-12-29
> **Michael.Godawski said:**
> hi Gigcsjcx,

three options. 
First try to reinstall the application via Synaptic. If this does not work
try to remove the files shown in the error message
```
$ cd /home
$ rm .DCOPserver*
```If this does not work, change the ownership of this folder with
```
sudo chown linux:linux /home/linux/.kde
```assuming your username is linux.

yes, my username is linux and thank you very much for your reply![COLOR="Teal"]it resolved the problem but was getting another issue. More help please.[/COLOR]

I can confirm that My [COLOR="Red"]Skype[/COLOR] works fine!



> linux@ubuntu:~$ sudo twinkle
[sudo] password for linux: 
Error: "/tmp/kde-linux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-linux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-linux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-linux" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-linux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-linux" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-linux" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-linux" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-linux" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-linux" is owned by uid 1000 instead of uid 0.


---

### Post by DarkSoul1984 on 2009-01-07
I have the same dcopserver error, and none of the above fixes it. I also don't have a dcopserver file.

Any ideas?

---

### Post by DarkSoul1984 on 2009-01-07
Double Post

My bad

---

