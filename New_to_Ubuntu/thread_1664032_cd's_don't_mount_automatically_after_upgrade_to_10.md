---
title: "cd's don't mount automatically after upgrade to 10.10"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by sarv_jeet on 2011-01-10
I recently upgrade to ubuntu 10.10 from 10.04 using a alternate cd iso. i mounted that iso as a cd for upgrade , i followed the instructions given  on ubuntu.com. After the upgrade every thing is fine except that cds don't mount automatically when inserted in to the drive, I have to manually mount cd by using following command. sudo mount /dev/sr0 /media/cdrom.
writing this command is not a problem but the user has to be root for it.
my son also uses this computer and his account is not root.

i hope someone help me. thanks in advance.

---

### Post by brandibran on 2011-01-10
I'm a very fresh, very "NEW(bie)" to this.

I want one of my drives to mount automatically too.   

I just loaded 10.10 onto my laptop, and I have a partition on my Win7 side that holds all of my media... I want this to mount automatically every time I log in to Linux... I want linux to use this partition just as much as Win7.  

What's the best way to mount automatically?
AND...
Is this NOT the best way to share media between Win7 & Linux runningon the same machine?  Let me know... What's the best formatting (NTFS?) for both to share this partition (mostly for movies and music) ????

---

### Post by brandibran on 2011-01-10
I guess no one loves us sarv_jeet... I'll research this tonight after work... and let you know what I find out.

---

### Post by clhsharky on 2011-01-10
sarv_jeet

Welcome to Ubuntu forums.

Go to  - System> Administration> Users and Groups(your self and or other user)>Advanced Settings>User Privileges
Tick to use cd-rom device.

Sharky

---

### Post by sarv_jeet on 2011-01-11
thanks clhsharky but use cdrom in users and groups is already checked. but it is not working.

---

### Post by sarv_jeet on 2011-02-05
i found a ad-hoc solution to my problem. I installed screenlets and used mount widget. when ever i insert cd. i click on /media/cdrom button on the mount screenlet. cd gets mounted.:guitar:

---

