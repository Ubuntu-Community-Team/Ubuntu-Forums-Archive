---
title: "Invoking Nautilus generated a Share Message...What does this mean?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2009-04-05
Invoking Nautilus in Terminal mode got me this:

eld@House:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:8898): WARNING **: Unable to add monitor: Operation not supported

*******************************************************

Where/how do I enable user sharing?

Is unable to add monitor warning anything to be concerned about?

Also, I want to remove my original user account after I transfer some files since I set up a second one that cleared up some video problems. Is the correct/clean way to go under System>Admin>User Accounts and delete the original there?

Thnx,

Ed

---

### Post by cariboo on 2009-04-06
> Also, I want to remove my original user account after I transfer some files since I set up a second one that cleared up some video problems. Is the correct/clean way to go under System>Admin>User Accounts and delete the original there?

Yes, that is the gui way to do it. If you want to do it in a terminal use the deluser command:

```
sudo deluser <username>
```

for more info have a look at:

```
man deluser
```

Jim

---

