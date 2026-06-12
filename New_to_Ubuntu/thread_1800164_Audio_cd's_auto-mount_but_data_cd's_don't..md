---
title: "Audio cd's auto-mount but data cd's don't."
date: 2011-07-08
forum: New to Ubuntu
---

### Post by thatrobguy on 2011-07-08
Hi, I am using ubuntu 11.04. I was using my computer fine the other day to burn some iso images using brasso. 
  Today when I insert a data cd it doesn't show up but audio cd's are fine.  I can find the dvd-rom using disk utility and mount it but it just makes it part of the file system. It mounts at /mnt/cdrom. 
  

The problem is when I mount it manually it doesn't show up in the  places menu and brasso doesn't see it as a separate drive so I can't use  it properly.


Maybe if I choose a different mount point brasso will see the cd if so does anybody know what that is? Although It would still be nice if it just mounted cds properly.

  

Can somebody help to lead me in the right direction with this problem? Thanks, rob.

---

### Post by dcsoldschool53 on 2011-07-08
> **thatrobguy said:**
> Hi, I am using ubuntu 11.04. I was using my computer fine the other day to burn some iso images using brasso. 
  Today when I insert a data cd it doesn't show up but audio cd's are fine.  I can find the dvd-rom using disk utility and mount it but it just makes it part of the file system. It mounts at /mnt/cdrom. 
  

The problem is when I mount it manually it doesn't show up in the  places menu and brasso doesn't see it as a separate drive so I can't use  it properly.


Maybe if I choose a different mount point brasso will see the cd if so does anybody know what that is? Although It would still be nice if it just mounted cds properly.

  

Can somebody help to lead me in the right direction with this problem? Thanks, rob.

[SIZE=2]**Put the CD back into your system and post the output of this command```
[SIZE=3]df -h[/SIZE]
``` **[/SIZE]

---

### Post by thatrobguy on 2011-07-08
ok 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              66G  4.0G   59G   7% /
none                  3.9G  712K  3.9G   1% /dev
none                  3.9G  272K  3.9G   1% /dev/shm
none                  3.9G   92K  3.9G   1% /var/run
none                  3.9G     0  3.9G   0% /var/lock
/dev/sdd1             932G  150G  782G  17% /media/Iomega HDD

The output to this command is the same weather I put an audio cd or a data cd in. However whenI insert an audio cd an icon is placed in my places menu and on my desktop and brasso pops-up and asks if I want to burn a cd.

---

### Post by dcsoldschool53 on 2011-07-08
Sorry I gave you the wrong command to use. I meant```
ls -l /mnt/cdrom
```I want to see if you can see into the disk from the terminal.

---

### Post by thatrobguy on 2011-07-08
same reply for both audio and data cds again.

total 0

---

### Post by dcsoldschool53 on 2011-07-08
> **thatrobguy said:**
> same reply for both audio and data cds again.

total 0If your audio mounts, and your Data disk don't. It maybe the disk itself. have you tried other disk.

---

### Post by thatrobguy on 2011-07-08
Yes. I mean I i put a disk in I can still go to disk utility and click on "mount volume". then the output of "ls -l /mnt/cdrom" shows the disk.

total 1377
dr-xr-xr-x 1 root root   2048 2009-07-20 17:25 0-PreInstall
dr-xr-xr-x 1 root root   2048 2009-07-20 17:25 1a-Updater
dr-xr-xr-x 1 root root   2048 2009-07-20 17:24 1b-SetPoint
dr-xr-xr-x 1 root root   2048 2009-07-20 17:24 2-Updater
dr-xr-xr-x 1 root root   2048 2009-07-20 17:24 3-PostInstall
dr-xr-xr-x 1 root root   2048 2009-07-20 17:24 5-EREG
-r-xr-xr-x 1 root root     41 2008-10-14 07:00 autorun.inf
dr-xr-xr-x 1 root root   2048 2009-07-20 17:24 ext
-r-xr-xr-x 1 root root  16067 2009-04-17 07:00 LEAME.htm
...

but it still doesn't show up on the desktop or in the places menu and brasso says no disk available when I go to "Disk copy".

---

### Post by dcsoldschool53 on 2011-07-08
You will have to sudo mount it yourself. Mount the folder that your cd is in

---

### Post by thatrobguy on 2011-07-08
I can do that and yes, it still mounts at /mnt/cdrom. How come the Ubuntu's gui cant see that it is there and brasso wont recognize that i have a cd in the drive? Is this a bug from a new update i installed? Is there somewhere where I can register the mounted cd so I can use brasso to make an iso copy of my cds and access them with ease from the gui?

Thanks for your help so far anyway.

---

### Post by dcsoldschool53 on 2011-07-08
I say it is a bug. But the good news is you can still create .iso files with the mkisofs command and burn them with cdrecord in a terminal. Also try a program called, I think, k3b it another burning program in Ubuntu software center.

---

### Post by thatrobguy on 2011-07-08
Does anybody know how brasso or the Ubuntu gui knows a cd has been mounted? I noticed that an audio cd doesn't get mounted at /mnt/cdrom but they both know it is there. maybe that is the answer to my problem.

---

### Post by thatrobguy on 2011-07-08
[dcsoldschool53]("http://ubuntuforums.org/member.php?u=1010604") thanks for the advise I will try that program.

---

