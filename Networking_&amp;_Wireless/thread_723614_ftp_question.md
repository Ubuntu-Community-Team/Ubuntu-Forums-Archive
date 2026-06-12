---
title: "ftp question"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2008-03-13
im running server 7.10 and webmin with proftpd and was wondering if there was a way to set up one user out of many to only have access to a particular folder and not the rest..... i dont know how clear im being.

basically if i want one person to have full access to a directory but another to only see like 3 folders in the same directory. can i do this... can you help :)

thanks in advance

---

### Post by evilbuntu on 2008-03-13
just bringing it back to the top, realy could use some info and cant find anything on google

---

### Post by handydan918 on 2008-03-13
Unix permissions 101.

You can make a user a member of a group. The group can be the owner of a file. OR a directory.  A user can be a member of multiple groups. A file (or directory) can have it's permissions set such that it can be read by UGO - user, group, and others.

Without sitting in front of your machine, I'd be hard pressed to do what you are talking about. But it can be done by applying appropriate permission to the files in question.

Man pages to look at :

chown

chmod

usermod

groupmod

groupadd

Good luck! Maybe somebody will weigh in who can do this in their head...

---

