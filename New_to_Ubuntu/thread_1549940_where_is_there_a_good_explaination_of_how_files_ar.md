---
title: "where is there a good explaination of how files are arranged"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Spacestationmax on 2010-08-10
where is there a good explanation of how files are arranged in ubuntu?  I am familiar with file locations on a windows system but after having ubuntu for about a year I still don't know where anything is.

---

### Post by oldos2er on 2010-08-10
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Spacestationmax on 2010-08-10
This is a nice Wiki post but Im looking for less jargon something in the "a cow goes moo!" catagory ... binaries?? Moduels?? huh

Thanks

---

### Post by MasterGamerJK on 2010-08-10
ROUGHLY!!!!:

/ - root aka c:/
/bin - program files
/etc - control pannel (kinda)
/mnt - where usb (ect) are mounted
/tmp - temp folder
/boot - c:/windows
/home - document and settings


is this what you were looking for??

---

### Post by fancypiper on 2010-08-10
[Linux File systems]("http://lmgtfy.com/?q=linux+file+systems")

For future questions, geeky but very thorough: [LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz)

[The Windows/Linux Alternative Project](http://www.linuxalt.com/)

[The table of equivalents / replacements / analogs of Windows software in Linux](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by Spacestationmax on 2010-08-10
Thanks everyone

---

### Post by Spacestationmax on 2010-08-10
> **MasterGamerJK said:**
> ROUGHLY!!!!:

/ - root aka c:/
/bin - program files
/etc - control pannel (kinda)
/mnt - where usb (ect) are mounted
/tmp - temp folder
/boot - c:/windows
/home - document and settings


is this what you were looking for??

Are all of these in USER or SYSTEM??

---

### Post by baddnady23 on 2010-08-10
specific user data and configuration files for the programs you use, your firefox bookmarks, music libraries, etc are stored under the /home/"your_user_name" directory.  Everything else would be considered system files

---

### Post by Spacestationmax on 2010-08-10
thanks

---

### Post by fancypiper on 2010-08-10
Having a separate partition for /home will save you lots of time in the future if you are like me (a distro hopper).  I can install/upgrade/change distros and not lose any important information.  I just choose the advanced option and set up the new install to use my current filesystem layout and I only format the / partition.

---

### Post by theboxseat on 2010-08-11
> **fancypiper said:**
> ...[Linux File systems]("http://lmgtfy.com/?q=linux+file+systems")...

9.2 million hits:

Is this link supposed to be useful?

There is an increasingly huge problem with google, in that there is so much data; ( I did not say information, as this implies usefullness!)

Sometimes it can be very difficult to get a meaningful result.

The purpose of a forum such as this is to answer questions that the poster cannot seem to readily find

---

### Post by bodhi.zazen on 2010-08-12
This is my favorite :

[img]http://media.brajeshwar.com/i/technology/linux-file-tree.jpg[/img]

There is some variation across distros, but that gets you in the ball park =)

For applications installed outside of the standard repositories, rpm systems tend to use /opt and .deb systems tend to use /usr/local

---

