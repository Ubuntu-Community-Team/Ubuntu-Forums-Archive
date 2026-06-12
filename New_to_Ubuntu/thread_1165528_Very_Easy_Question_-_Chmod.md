---
title: "Very Easy Question - Chmod"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by dazman19 on 2009-05-20
I am trying to add my /var/www folder so my user has r/w access to it. 
I wanted to do this by adding my user (daz) to a group called daz, and associating the files in this folder with the daz group.

I started off by adding the user to the group:

sudo usermod -a -G daz daz

Then associating the group with the folder:
chown root:daz /var/www/*

Then giving the group RWX access to the file. 
sudo chmod -R 755 /var/www/*

when i look at this folder it seems to look right, but i still cant write to the file when i am logged in as the user daz.

daz@darkstar:/var/www$ ls -l
total 4
-rw-rw-r-- 1 root daz 45 2009-05-21 09:45 index.html

Any ideas what I am doing wrong?

---

### Post by Mornedhel on 2009-05-20
Note that by default, users belong to a group containing themselves and called like the username (which you tried to achieve with your usermod command).

Also, 755 is octal for rwxr-xr-x, probably not what you tried to do. You'll need 76*.

---

