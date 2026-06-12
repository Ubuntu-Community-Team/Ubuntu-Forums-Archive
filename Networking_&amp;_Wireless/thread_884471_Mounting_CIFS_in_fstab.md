---
title: "Mounting CIFS in fstab ?"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by solariz on 2008-08-09
Hi,

im relatively new to Linux on my desktop. Working on serverside since some years but never had to mount a network drive. I have a NAS which use CIFS Network Protocol I want to mount hard each time I boot. Currently I use smbfs to mout it and I need to specify me USername + Password in the fstab. 
2nd is very unsecure because it is in cleartext.

My Questions:

a) Is there any option to natively support CIFS other then mounthing through smbfs ?


b) How should I enter it in the fstab that e.g. ubuntu ask me for a password when I first access the mounted device ? I dont want to leave my PWD in the fstab.


Currently I ust this for mounting but i do not know if it is 100% correct, I can access and rw but I experience some problems If I open files direktly on the remote side and try to save them. (Office e.g.) Some apps are telling me that htis file is currently in use by somebody and I cant override it. What I have to do is to save it asl test2.xls and after this delete the original and rename test2 back to the org. file.

I guess it have something todo with a wrong fstab mount call.


("server" is the hostname of my NAS)

**//server/projekte /mnt/projekte smbfs auto,owner,rw,username=solariz,password=#####,uid=1000,gid=1000 0 0**


Thanks alot

---

### Post by Iowan on 2008-08-09
From **dmizer**'s signature: [http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

In particular, notice the section about the credentials file.

---

