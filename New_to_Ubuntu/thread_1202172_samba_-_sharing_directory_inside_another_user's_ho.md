---
title: "samba - sharing directory inside another user's home directory?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by OM NOM NOM on 2009-07-01
Hi There, 

I'm at a loss on this one...I'm trying to use a spare box as an Ubuntu home file server. I have two users on the system - joe and jane. Joe is an admin, jane is a user. I'd like to have jane have read-write access to a directory inside joe's home folder but no others. Reason being is that for archiving and admin purposes i'd like to have joe maintain ownership of the directory. 

The issue I'm having is that jane cannot access the directory, even though it is visible on the network as its own share. 

What I've done so far is to create a group called homegroup, make jane a member of that group, and gave homegroup permission (chmod 775) to the directory inside joe's home directory. All that took but jane still cannot acess the share. 

So I'm wondering...

1. Is this even possible

and

2. If so what did I miss? 

Thanks for any guidance on this!

---

### Post by Boondoklife on 2009-07-03
did you specify in the smb.conf that the homegroup has access to write to that directory?

write user = @GROUPNAME

---

### Post by Celauran on 2009-07-03
You specifically mentioned chmod 755, but said nothing about ownership. Is /home/joe/share owned by joe:joe or joe:homegroup?

---

### Post by OM NOM NOM on 2009-08-19
good point. It is owned by joe:joe...should jane be a member of the "group" joe?

---

### Post by linux6994 on 2009-08-19
The easiest way to control your Samba shares is via the System > Administration > Samba Gui that cam be installed via 'sudo apt-get install system-config-samba'. This will allow you to choose the directories and users.

Good luck.

---

### Post by OM NOM NOM on 2009-08-20
Thanks! For now since it's just for my girl and I, I just created a folder to put her files into that has open permissions. I'll install the Samba utility and se if I can use it to keep the kids out :-)

---

