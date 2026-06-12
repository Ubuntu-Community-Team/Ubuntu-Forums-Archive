---
title: "Daemon Tools Lite equivalent in Linux"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by 1337Mastermind on 2010-07-19
Although I am fairly technically savy, I am almost clueless when it comes to linux. Please bear with me. I have tried Googling for the answer to this issue, but I have not found anything that helps me. When I used to use Windows I used a program called Daemon Tools Lite to mount disc images and emulate the copy protection so that I could run video games without having the original disk (don't have to juggle CD's and protects the originals so they stay in good quality). Recently I have been running many of the games I played in Windows under Wine in Linux. My question is; is there an equivalent for Daemon Tools Lite in Linux? It would be nice to not have to use my original disks. I understand there are ways to mount images. the mount command, Furious ISO Mount, GMount, etc, but so far I have not been able to find one that will bypass the copy protection. If anyone knows of something that will do what I need it to, the help would be appreciated. Thank you in advance for your assistance.

---

### Post by tekkidd on 2010-07-19
Ubuntu has an archive mounter built into it.

---

### Post by 1337Mastermind on 2010-07-19
I know, and I have tried using it. So far, the video games I have tried have noticed that it is not the original disk though. Daemon Tools Lite used to be a workaround for this.

---

### Post by debjit_bis08 on 2010-07-19
If you are talking about .iso files, they can be mounted using the mount command.

$ sudo mount -o loop disk1.iso /mnt/disk

/mnt/disk is the directory where the files in the CD image will be visible.

Hope that helps.

---

### Post by bodhi.zazen on 2010-07-19
> **1337Mastermind said:**
> Although I am fairly technically savy, I am almost clueless when it comes to linux. Please bear with me. I have tried Googling for the answer to this issue, but I have not found anything that helps me. When I used to use Windows I used a program called Daemon Tools Lite to mount disc images and emulate the copy protection so that I could run video games without having the original disk (don't have to juggle CD's and protects the originals so they stay in good quality). Recently I have been running many of the games I played in Windows under Wine in Linux. My question is; is there an equivalent for Daemon Tools Lite in Linux? It would be nice to not have to use my original disks. I understand there are ways to mount images. the mount command, Furious ISO Mount, GMount, etc, but so far I have not been able to find one that will bypass the copy protection. If anyone knows of something that will do what I need it to, the help would be appreciated. Thank you in advance for your assistance.

[https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

gisomount is a graphical front end.

---

### Post by 1337Mastermind on 2010-07-19
> **debjit_bis08 said:**
> If you are talking about .iso files, they can be mounted using the mount command.

$ sudo mount -o loop disk1.iso /mnt/disk

/mnt/disk is the directory where the files in the CD image will be visible.

Hope that helps.


I already found out about this command, and have used it, but it does not emulate the copy protection and such like DTL does. When I play games they recognize that it is not the original disk.

---

### Post by 1337Mastermind on 2010-07-19
> **bodhi.zazen said:**
> [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso)

gisomount is a graphical front end.

Thanks, that will prove useful I am sure, but it still does not solve my problem.

---

### Post by dv3500ea on 2010-07-19
> **1337Mastermind said:**
> I already found out about this command, and have used it, but it does not emulate the copy protection and such like DTL does. When I play games they recognize that it is not the original disk.

I'm pretty sure that's illegal (though I know DRM sucks). Is this a legal copy you have? Is it a Windows or Linux game?

---

### Post by Telengard C64 on 2010-07-19
I'm currently using [_AcetoneISO_](http://en.wikipedia.org/wiki/AcetoneISO#Limitations) which can do quite a lot more than simply mount ISO files. But if your problem really is copy protection then it won't solve that.

I do agree with the sentiment that something comparable to Daemon Tools is needed for Linux.

---

### Post by bodhi.zazen on 2010-07-19
> **1337Mastermind said:**
> I already found out about this command, and have used it, but it does not emulate the copy protection and such like DTL does. When I play games they recognize that it is not the original disk.

I guess I did not read your OP close enough. 

We do not support circumventing copy protection on these forums.

---

