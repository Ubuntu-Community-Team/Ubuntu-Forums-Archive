---
title: "copying files from different users"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by 29732 on 2010-08-08
hey guys..
i am trying to copy this .vdi file to my mothers acct. on ubuntu and i cant
how can i do it without it saying permission denied?

NOTE:  i am admin and she isnt

---

### Post by ezsit on 2010-08-08
Well,

This command would copy the file and using sudo would give you root privileges to do the copy.

**sudo cp /home/myhome/file.vdi /home/mother/file.vdi**

However, the file would be owned by root and not your mother. you could then do:

**sudo chown mother:mother /home/mother/file.vdi**

to change the ownership of the file to your mother's account. chown command changes ownership and the mother:mother argument specifies your mother's username and groupname. Do a man lookup of the command for more info.

---

### Post by 29732 on 2010-08-08
ok 

thanks!

---

