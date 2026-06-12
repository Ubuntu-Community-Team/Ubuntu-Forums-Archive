---
title: "Root user"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by mikxa on 2010-05-04
Hello everybody

I've installed  Desktop 10.04 LTS (32-bit) Ubuntu a few hours ago, and the installation procedure offered me to create user (and i did that), but there was no question about root password. When i want to do su command i don't know what to type as root password. Any help? Thanks.

---

### Post by garvinrick4 on 2010-05-04
> **mikxa said:**
> Hello everybody

I've installed  Desktop 10.04 LTS (32-bit) Ubuntu a few hours ago, and the installation procedure offered me to create user (and i did that), but there was no question about root password. When i want to do su command i don't know what to type as root password. Any help? Thanks.
When you installed it asked you for your password twice to confirm it.

---

### Post by oldos2er on 2010-05-04
Ubuntu disables the root account by default; if you need a persistent root terminal, use **sudo -i**. If you only need to run one or two commands as root, prepend with **sudo**.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mikxa on 2010-05-04
yes, that's correct, as i mentioned i created user blablabla with some password and that user exist, but when i do "su" command in terminal, i am asked to type root password - and i don't know root password (because nobody asked me for root password during installation procedure). i tried to create root user (i know that sounds ridiculous) and i was informed that root user exist. Also, i tried with password associated with user blablabla but doesn't work. So, the problem i have is: i don't know how to log as root user, because i don't know password.

---

### Post by mikxa on 2010-05-04
ok, thanks oldos2er

---

### Post by juancarlospaco on 2010-05-04
sudo -i

*remember that sudo dont work properly for graphical apps*

---

### Post by techunit on 2010-05-04
Yeah that had me for a few minutes when I first started with ubuntu 2 and a half years ago! I didn't even have any understanding of root control. It is a funny thing linux. I love it. Now I can have an install up in running on almost any system in less than an hour.

---

