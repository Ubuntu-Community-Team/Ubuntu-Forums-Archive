---
title: "creating a data partition in ubuntu 9.10 and insatlling  ubuntu 10.10"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by vik.gelin on 2010-11-28
hello friends. i wanted to migrate from ubuntu 9.10 karmic  to the latest ubuntu 10.10, but i already have a lots of data on my hard disk in home directory. i was thinking if it is possible to transfer all the data to one directory and make a separate partition of it , so tht when i install a fresh copy of ubuntu 10.10 on my system i need not format this new partition ,which contains al my data. is it possible tht this new partition will  automatically get mounted on the new system without the need to execute commands from terminal every time i start my system. if there is any other alternative way for solving this problem i would love to follow tht too.the reason for my migration is that karmic  is really troubling me a lot and so many applications including my sound device have failed to work and i am not able to rectify them..help help ..urgent help

---

### Post by lmarmisa on 2010-11-28
> **vik.gelin said:**
> hello friends. i wanted to migrate from ubuntu 9.10 karmic  to the latest ubuntu 10.10, but i already have a lots of data on my hard disk in home directory. i was thinking if it is possible to transfer all the data to one directory and make a separate partition of it , so tht when i install a fresh copy of ubuntu 10.10 on my system i need not format this new partition ,which contains al my data. is it possible tht this new partition will  automatically get mounted on the new system without the need to execute commands from terminal every time i start my system. if there is any other alternative way for solving this problem i would love to follow tht too.the reason for my migration is that karmic  is really troubling me a lot and so many applications including my sound device have failed to work and i am not able to rectify them..help help ..urgent help

I agree. This is a good idea.

I do not recommend to move all your home directory (/home/yourusername) to a new destination in a new partition. You should move only your personal data (documents, photos, music, etc). Why?. Because you have stored in your home folder a lot of hidden files and directories containing data with configurations of many programs (gnome, firefox and many other). These config files are correct for the versions of programs of Ubuntu 9,10 but maybe they will wrong for Maverick.

  [Symbolic links]("http://en.wikipedia.org/wiki/Symbolic_link") could help you to move your data to other destination maintaining a link at its old location.

During the migration you will have some additional problems if the uid and gid of your username in 10.10 are not identical to those of your current user. This is a minor problem and it is easy to fix using the command **sudo chown**.

---

### Post by theozzlives on 2010-11-28
Hogwash! I've had a separate /home since gutzy (7.10). Just follow [these]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") instructions.

---

### Post by vik.gelin on 2010-11-28
yes u are right ,i just have to move my personal documents to the new partition and not the complete /home directory containing the configuration files and all other stuff.there is only 4 gb free disk space on my 40 gb hard disk and i have data size around 25 to 30 gb personal one ..is it still possible to do so ,without formatting it at all.

---

### Post by lmarmisa on 2010-11-28
> **vik.gelin said:**
> yes u are right ,i just have to move my personal documents to the new partition and not the complete /home directory containing the configuration files and all other stuff.there is only 4 gb free disk space on my 40 gb hard disk and i have data size around 25 to 30 gb personal one ..is it still possible to do so ,without formatting it at all.

Try to use an external USB hard drive.

---

