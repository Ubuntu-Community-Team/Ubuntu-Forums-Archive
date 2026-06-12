---
title: "Problem Mounting First CIFS Share in fstab"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by KentonS on 2008-11-01
In fstab on my laptop (running Ubuntu 7.10) I have two virtually identical lines to mount shares that reside on a networked Windows XP. Regardless of the order of the lines, the first one fails to mount at boot up, and the second mounts successfully. Once I log in and issue a "sudo mount -a" command, the first share mounts successfully. This happens whether the Windows machine has just been powered up or has been sitting idle for some time. (The power settings on the Windows machine are set to not power down the hard drives after a period of inactivity.)

Here are the relevant lines in fstab:
######
//192.168.1.100/Share1 /mnt/Share1 cifs credentials=<file>,_netdev,uid=<user>,gid=<group>,file_mode=0600,dir_mode=0700 0 0
//192.168.1.100/Share2 /mnt/Share2 cifs credentials=<file>,_netdev,uid=<user>,gid=<group>,file_mode=0600,dir_mode=0700 0 0
######

where <file> is my credentials file, <user> is my user name, and <group> is my group number.

Does anyone have any idea what's going on and how to fix it? Is there a log file I can look at to see what happened at boot up? (In case it isn't already obvious, I'm new to Linux.)

Thanks in advance for any help,
Kenton

---

### Post by KentonS on 2008-11-06
Should I have posted this question somewhere else? Where?

---

### Post by KentonS on 2009-09-15
OK. Well, thanks very much anyway for the overwhelming response to my question. This Community Support idea really rocks! (Not!)

---

### Post by Iowan on 2009-09-15
I remember seeing a similar problem in an earlier version.  Wait, 7.10 IS an earlier version.  Seems like the first mount (or two) worked, it was the last that failed... don't remember the solution, though.
There is [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To that might be helpful.

---

### Post by mattalexx on 2010-11-27
> **KentonS said:**
> OK. Well, thanks very much anyway for the overwhelming response to my question. This Community Support idea really rocks! (Not!)

Who do you think you are? These people are here to help you for free.

---

### Post by KentonS on 2010-11-27
> **mattalexx said:**
> Who do you think you are? These people are here to help you for free.

LOL at your self-righteous outrage!

Look at the dates. I posted my question in September, 2008. After almost a year with no response from the "people ... here to help", I posted my message expressing my disappointment in the lack of response from the so-called community. Now - almost a year later(!) - along comes you. LOL again!

Thanks for proving my point.

---

