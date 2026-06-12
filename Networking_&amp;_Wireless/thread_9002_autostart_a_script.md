---
title: "autostart a script"
date: 2004-12-23
forum: Networking &amp; Wireless
---

### Post by dobricchi on 2004-12-23
hello,

i'm having some difficulties about this kind of target:
i'd like to start a script that mounts windows shares in a static path by taking dynamic user and password, the one used by session.

i joined my windows 2000 AD native mode domain by using samba and winbind, and i can login to my ubuntu box with domain+user and password with no problems.

what i'm using now is /etc/fstab by picking credentials in /root/.smbcredentials file, but i don't like to have a password written on a simple text file.  

the goal is to autolaunch a script that after the login uses username and password given to set correct file and folders permissions.

any helpful idea?
tnx in adv.

---

