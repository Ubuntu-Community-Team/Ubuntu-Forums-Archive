---
title: "Deleting Groups?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-11-22
I made a new group so I now have two groups (main -- danielmillier, 2nd -- unknownfear)/ I wanted to make a new group, or more a less, a new user name to make the terminal display a different name than my main name. Now, I logged on to the default user account and deleted unknownfear, however, I restarted my computer and it still lists both user accounts. How can I permanently delete a user account without having to re-install Ubuntu?

---

### Post by anders_c_ on 2009-11-22
Not entirely sure if i understand you, are you trying to remove a group or a user??

delete user:
```
sudo userdel USERNAME
```

delete group:
```
sudo groupdel GROUPNAME
```

---

### Post by UnknownFear on 2009-11-22
[QUOTE=anders_c_;8365973]Not entirely sure if i understand you, are you trying to remove a group or a user??

delete user:
```
sudo userdel USERNAME
```

So, I did the terminal command and restarted the computer. When I booted back up, it gave me an error saying something like Kernel panic or something. Is there a way to fix this, or should I just re-install Ubuntu and not make a new user :)

---

### Post by anders_c_ on 2009-11-22
It sounds strange that you would get a kernel panic from deleting a user...but if you have an unbootable system now, and you don't think it's too much work to reinstall then just do it. 

Adding and deleting users is basic stuff in unix systems and shouldn't cause any problems at all, you probably have other problems with you system. 

Anyway a reinstall only takes like 15 minutes so go for it;)

---

### Post by UnknownFear on 2009-11-22
@anders_c_: Already did it :) On Ubuntu 9.10, installing all the basic things.

---

