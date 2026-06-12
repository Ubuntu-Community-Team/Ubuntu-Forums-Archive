---
title: "Networking Ubuntu and Xp"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by theemrsweets on 2007-05-12
I am having a hard time networking an ubuntu comp and an xp comp.  I can see shared folders from my xp comp on my ubuntu but when I try to see shared folders from my ubuntu cd on the xp comp, I am having problems.  XP asks me for a user name and password.  I've tried my ubuntu user name and password but they do not work.  Any help is greatly appreciated.  Thank you in advance.

---

### Post by theemrsweets on 2007-05-12
OK I got it to work by just changing the password for samba by doing this

sudo smbpasswd -a 'myusername'

and enetering my password and then a new pssword with the confirm

---

