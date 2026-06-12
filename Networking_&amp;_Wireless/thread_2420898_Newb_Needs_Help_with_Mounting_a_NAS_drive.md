---
title: "Newb Needs Help with Mounting a NAS drive"
date: 2019-06-12
forum: Networking &amp; Wireless
---

### Post by ce_lloyd on 2019-06-12
I REALLY REALLY want to like and learn how to use linux but it's so frustrating.  NOTHING is intuitive for a new user.  I followed a video to mount a network share and cannot get the mount to run correctly.  Hopefully someone will take pity on me and help me figure this out.

The error message is:
root@chad-OptiPlex-790:~# mount -a
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

The NAS I'm trying to add is an older one so I don't know if there are version issues I'm not aware of or what.  Please let me know what else I can share on here to resolve this issue.  Thank you in advance!!!

---

### Post by TheFu on 2019-06-12
Linux is just as intuitive as every other OS, IMHO.  You should see kids who have only used Linux freak out with Windows the first time they see it. It is funny all the "why does it ... " questions.

So ... exactly which NAS do you have?  Which version of samba does it provide?  Does it have an option for NFS?  If so, that is probably much easier to use, since it is the native network file system for Unix computers.

I assume you modified the /etc/fstab on the client, yes?  Perhaps if you could post that here, someone could help?
Please wrap it in [code tags]("https://blog.jdpfu.com/code_tags") for readability.

Something like this:
```
//172.22.22.8/Data    /Data/win7ult     cifs     rw,iocharset=utf8,vers=2.1,uid=1000,gid=1000,file_mode=0664,dir_mode=0775,credentials=/root/win7lap-D.credentials      0     0 
```
Play with the version and the other stuff like mount point and IP to match your network and NAS. 
It is very important that the options never have spaces. The number of spaces between the other parts doesn't matter, provided there is at least 1.

Details about any option can be read with **man mount.cifs**, but that probably isn't needed.

Also, there are logs on both the client and the server for any issues.  They are in /var/log/samba/.  If you take an error line and put it into google, often that will provide the likely fix.

---

