---
title: "Samba how to limit access to a folder just for 2 users?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by sapo on 2007-07-05
Hi,

I'm trying to configure a samba server and everything is working except for a folder.

I need this folder to be accessed by just 2 users, i already tried the following:


valid users = user1 user2

write list = user1 user2

read list = user1 user2


also a tried creating a group and using:

write list = @group
read list = @group

but nothing seens to work.

when i use valid uses, another uses can't log on, but the users i want to, after the log in they get a message saying that they don't have permissions to read that.. so... i'm completely lost...

Any ideas?

---

### Post by sapo on 2007-07-06
Please, any help is welcome.

I still didn't find a solution for the problem.

---

### Post by #Reistlehr- on 2007-07-06
did you restart samba after you made the changes?

sudo /etc/init.d/samba restart

---

### Post by sapo on 2007-07-06
> **#Reistlehr- said:**
> did you restart samba after you made the changes?

sudo /etc/init.d/samba restart

Sure, i tried /etc/init.d/samba reload to some times.

The problem the problem is that when i set the valid users to something the other users can't log in, but the user who is valid can login, but he gets an error just after login in saying that he doesn't have permission to read that folder.. wth?

---

