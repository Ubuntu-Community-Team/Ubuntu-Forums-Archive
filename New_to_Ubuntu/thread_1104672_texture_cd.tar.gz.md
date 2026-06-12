---
title: "texture_cd.tar.gz"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by sadicote on 2009-03-23
Hi, I am sorry that even after six months with Ubuntu, and having upgraded to Jaunty, i still have to trouble you'll in this beginner's category. I have downloaded this tarball and done a tar xzvf '/home/sade/Documents/texture_cd.tar.gz. After that i did a cd texture_cd/ and managed to get into that directory. Now when i do a ./configure, i get the following: sade@sade-desktop:~/texture_cd$ ./configure
bash: ./configure: No such file or directory
sade@sade-desktop:~/texture_cd$ 

Call me an idiot if you will, but please tell me what i am doing wrong, and how i should go on from here.
:)

I forgot to add, the package does not have a 'Read Me'

---

### Post by sandyd on 2009-03-23
> **sadicote said:**
> Hi, I am sorry that even after six months with Ubuntu, and having upgraded to Jaunty, i still have to trouble you'll in this beginner's category. I have downloaded this tarball and done a tar xzvf '/home/sade/Documents/texture_cd.tar.gz. After that i did a cd texture_cd/ and managed to get into that directory. Now when i do a ./configure, i get the following: sade@sade-desktop:~/texture_cd$ ./configure
bash: ./configure: No such file or directory
sade@sade-desktop:~/texture_cd$ 

Call me an idiot if you will, but please tell me what i am doing wrong, and how i should go on from here.
:)

I forgot to add, the package does not have a 'Read Me'

give me a ```
ls
```
of that directory

---

### Post by oldos2er on 2009-03-23
From within the texture_cd directory, run ls -l and post the output here.

---

### Post by sadicote on 2009-03-23
Thanks! Here it is:

sade@sade-desktop:~/texture_cd$ ls -l
total 32
-rwxr-xr-x  1 sade sade   31 2000-07-14 23:08 autorun.inf
drwxr-xr-x 11 sade sade 4096 2006-05-17 20:55 html
-rwxr-xr-x  1 sade sade 2386 2006-05-18 00:30 index.html
drwxr-xr-x  3 sade sade 4096 2006-05-17 20:40 material
drwxr-xr-x  4 sade sade 4096 2006-05-17 20:40 plugin
drwxr-xr-x  3 sade sade 4096 2006-05-17 20:47 quickstart
drwxr-xr-x  2 sade sade 4096 2006-05-17 21:17 shop
drwxr-xr-x 15 sade sade 4096 2006-05-17 21:05 texture
sade@sade-desktop:~/texture_cd$

---

### Post by sadicote on 2009-03-23
I tried skipping the ./configure step and directly trying make, (as advised on some sites), i got: No targets specified and no makefile found

---

### Post by oldos2er on 2009-03-24
No, there's nothing there to compile. Open index.html in Firefox (or whatever your favorite browser is), and see if that gives you any useful info.

 Do you have a URL to download this program?

---

### Post by sadicote on 2009-03-24
[http://blenderartists.org/forum/showthread.php?p=1344393&posted=1](http://blenderartists.org/forum/showthread.php?p=1344393&posted=1). 

Please don't kill me after reading the post.

---

### Post by oldos2er on 2009-03-25
Glad you found the answer. Now you know that things other than source code come in tarballs!

---

