---
title: "connecting to windows network"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by fsviza on 2008-09-05
Hi,
when browsing windows network no files appear to me, no login/pwd is asked when accessing the data server. any solution to this? thanks
(ubuntu 8.10 amd64)

---

### Post by Threbus5 on 2008-09-05
Well,
Can you access the files/folders from another windows machine on the network?
Are all of the networked computers on the same workgroup? 
Make sure that the windows machines have sharing enabled for the files and folders that you want to access. (select the file/folder and under properties enable sharing)
Determine that any firewalls allow sharing (usually windows share results in passage but depending upon your anti-virus software you may have other firewalls enabled).

Take care.

---

### Post by fsviza on 2008-09-05
hi,
i can access folders and files on other computers in that certain network in the same workgroup, i can access that machine from any other windows machine and from one other ubuntu-run machine. it has to be something with settings in my machine.
cheers

---

### Post by Crafty Kisses on 2008-09-05
Possibly be the permissions you think?

---

### Post by fsviza on 2008-09-05
shouldn't be, one ubuntu-run machine could access that server without any problem.

---

### Post by Iowan on 2008-09-05
> **fsviza said:**
> Hi,
when browsing windows network no files appear to me, no login/pwd is asked when accessing the data server. any solution to this? thanks
(ubuntu 8.10 amd64)
Might be a question for the Development Forum

---

### Post by linux_newbie101 on 2008-09-09
I had a similar Windows network access problem which I eventually was able to solve.  On my home network, I have a Windows Vista desktop and Ubuntu Hardy 8.04 and I was able to finally see my Vista PC files from Ubuntu. 

If you are running Firestarter firewall in your Ubuntu setup, make sure to disable this first to simplify your debugging. It is possible that Firestarter is blocking your Windows network access as I discovered on my setup.

---

### Post by jschramm97 on 2008-09-10
I am also experiancing this issue, mysetup is as follows:

Dell 1150 laptop - Ubuntu 8.04.1
Dell 9300 Laptop - XP Pro SP3
Media Server - Vista Ultimate

The 2 dells can see each other fine, the 9300 can see the media server. The 1150 when browsing the network see's the Media Server but when i click on it i'm not prompted for any creditals and then i see no files/folders. 

From the Ubuntu box i can ping and RDP to the Media Server by IP only not DNS name. Outside of that i really haven't done any more troubleshooting as i'm not very versed in the ways of Linux networking yet.

---

