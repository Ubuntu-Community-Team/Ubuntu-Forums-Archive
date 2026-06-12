---
title: "Is it possible to change the primary accounts username?"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-18
I just finished helping someone setup a dual-ubuntu installation.  They have two installations of Ubuntu running from separate partitions but they both share the same /home partition.  The theory behind this is that, if he screws something up with one of them, he'll have the other to immediately fall back on so he can continue working until the primary install is repaired.

During the installation I told him to make sure his username matches the username he has in the original install, but he failed to do this.  So now there are two separate user folders found within /home/ instead of just one being shared between the two.

Rather than reinstall and make sure the username is set correctly, I was wondering if there's a quicker way to either change the accounts username or perhaps just create a new account with that name, login to it, and then remove the original account... but I don't know if either of these things are possible.

---

### Post by jtarin on 2010-10-18
Basically, you have four commands to type as root to change the username and group. They are as follows:
```
# mv /home/oldname /home/newname
```
```
# usermod -l newname oldname
```
```
# usermod -d /home/newname newname
```
If you want to change the group also:
```
# groupmod -n newname oldname
```
If you want to see what each command is doing, check out the manpages for usermod and groupmod.
Gotchas

---

### Post by diablo75 on 2010-10-18
> **jtarin said:**
> 
```
# usermod -l newname oldname
```
```
# usermod -d /home/newname newname
```


From the looks of it, these are the only two commands I really want.  According to the man page, the first command changes the actual username that will be used at login, and the second command specifies the default location for that user's home folder.  I will test this out.  Thanks!

---

### Post by jtarin on 2010-10-18
Your welcome. These were the only possible scenarios I could think of to apply in this situation. There might be others but I'm not aware of them.

---

