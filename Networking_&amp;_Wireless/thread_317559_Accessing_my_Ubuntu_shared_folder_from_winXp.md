---
title: "Accessing my Ubuntu shared folder from winXp"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by gareththegeek on 2006-12-12
I have set up one of my folders to be shared on the network in Ubuntu dapper and I wanna know how to get at it from a winxp box.  I right clicked on the folder and chose to share it, leaving everything at its default setting.  If I try and access it through network places in windows it says I do not have permission.  I tried reading the wiki but it didn't seem to tell me what I needed to know!

Thanks for any help,
G!

---

### Post by ADT on 2006-12-14
This tutorial should help you [HTML]http://www.linux.com/article.pl?sid=06/11/20/207251[/HTML]

First make sure samba is installed and running.
check to see if it's installed in synaptic manager and check to see if its running in gnome-system-monitor.

You should create a new user account for accessing your ubuntu machine's shared folders from your win XP machine.
Example in the tutorial the new user account is called joel. Maybe you should use a user name like Winxpaccess for that account.
Example, write in the terminal:
useradd -c "Win XP access" winxpaccess
smbpasswd -a winxpaccess
New SMB password: put your password in here
Reenter SMB password: put your password in here
Added user winxpaccess

then in your /etc/samba/smb.conf file use winxpaccess or whatever user name you created instead of "joel" in the tutorial.

Then whenever you want to access your ubuntu shares from your win xp machine use the "winxpaccess" account.

Also your ubuntu shared folder will probably need to have read/write access for group and others enabled.
type in terminal 
gksudo nautilus
(becareful as it is easy to make mistakes in this mode.)

then locate your ubuntu share and right click, then go to properties, go to permissions tab and set group access to read/write and others to read/write.

---

### Post by Omegatron on 2007-01-01
> **ADT said:**
> Example, write in the terminal:


Surely there's a way to do this through Gnome's GUI instead of command-line...  

There's a **System --> Administration --> Shared Folders**, but you can't actually use it without editing the smb.conf by hand??

---

### Post by tagra123 on 2007-01-03
After a couple of months fiddling


I got it!!!!!!!!!!!

Letting some of the unanswered post know.

[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

