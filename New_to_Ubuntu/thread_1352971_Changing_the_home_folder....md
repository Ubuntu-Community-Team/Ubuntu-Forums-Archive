---
title: "Changing the /home folder..."
date: 2009-12-12
forum: New to Ubuntu
---

### Post by fisteecuffs on 2009-12-12
Hey guys,

Very new to Ubuntu (trying to ween myself off Windows), love what I've seen so far but having a small problem that I'd greatly appreciate some help with.

Basically, I originally installed Ubuntu 9.10 a few weeks back, setting up separate partitions for the system and /home. Since then I reinstalled Ubuntu but didn't want it to overwrite my /home partition so I installed everything, including a new /home folder, onto the original system partition. How do I get Ubuntu to switch back to using the separate /home partition with all my settings etc on? 

I'm sure it's embarrassingly simple but can only find info on how to create a new home partition, which doesn't seem to be of much help!

Thanks,
Jack

---

### Post by fourthofjuly on 2009-12-12
i am not sure, but try this only if you don't mind breaking down the new installation...

the old home will have a username and pwd, which i guess you remember... in the new systemcan we create a new user with this username and pwd ?

now, backup your /etc/fstab file

**cp /etc/fstab /etc/fstab_backup**

the new home is on a partition say /dev/sda7... comment it out in /etc/fstab

the old home is on a separate partition say /dev/sda5... make changes to your fstab so it points to the old home in /dev/sda5...


**sudo gedit /etc/fstab**


# /dev/sda7	/home  ext3   relatime  0       0  #new home
  /dev/sda5	/home  ext3   relatime  0       0  #old home


reboot...

hope that helps...

ps: as per topic suggested by 73ckn797 below, instead of re-creating the old user in new system, we can even give ownership of old /home folder to the default user in your new installation

chown -R username:username /home/olduser

---

### Post by 73ckn797 on 2009-12-12
Check out this link:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

