---
title: "Can't install wine 1.0"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by kilo8001 on 2009-07-19
I am trying to install wine 1.0 and cant get past unzipping it using the terminal.

I have created a directory for the tar.bz2 file and i get to the point of extracting it and i get the following 
error:

" Can't create output file wine-1.0.tar: Permission denied."

Any ideas??

Linux newbie.

---

### Post by philcamlin on 2009-07-19
sudo apt-get install wine

---

### Post by kilo8001 on 2009-07-19
kilo@kilo-laptop:/usr/local/src$ sudo apt-get install wine
[sudo] password for kilo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kilo@kilo-laptop:/usr/local/src$ 

Apparently I have it already??

---

### Post by kilo8001 on 2009-07-19
Is version 1.0.1 the same as 1.0?

---

### Post by CatKiller on 2009-07-19
Essentially. 1.0.1 will be 1.0 with some small fixes that aren't enough for a full point release (actually, there are some translation fixes too, according to the [Release Notes]("http://www.winehq.org/announce/1.0.1")). I believe 1.0.1 is the current latest stable release, although I'm running 1.1.26 from [WineHQ's repository]("http://www.winehq.org/download/deb").

---

### Post by philcamlin on 2009-07-19
> **kilo8001 said:**
> Is version 1.0.1 the same as 1.0?

yup with bugfixes etc

---

### Post by /usr/sbin on 2009-07-20
Have you solved the problem?

---

