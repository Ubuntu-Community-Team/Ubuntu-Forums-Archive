---
title: "how to resize /, home, usr"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by atulchavan on 2010-04-30
i have dual boot system windows and ubuntu. while installing ubuntu i used manual partition and assign 80gb for root, 20gb for home,3gb for usr.... but i am not using root at all. my usr and home partition is full. can i increase the size of home,usr and decrease the size of root. i think for installation of new packages i need space in usr.
how to achieve this?

---

### Post by laffinet on 2010-04-30
Boot into a liveCD (you can use the one you installed from), start gparted (Partition Editor under System, Administration), resize your partitions accordingly.

Remember to back up your important data before you do this. Problems rarely occur, but better safe than sorry.

---

### Post by rajhanschinmay on 2010-05-03
I want to install Ubuntu 10.04 upgrade. Error I am getting is of space,
I have about 1.6GB free on /. It is asking for 2.0+ GB of free space.

Is there any way by which I can resize the partition keeping my original OS as it is.

Typically repartitioning any drive and that too OS first drive is very risky. Sometimes u have to re-install OS.

I saw some solution of using live CD and using gparted. Will this work on existing machine and how much is the risk?

I also have dual boot with Ubuntu 9.10 and Windows XP. So will repartitioning affect any of these.

Please help me asap.

---

