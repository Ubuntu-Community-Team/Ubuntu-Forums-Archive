---
title: "Username renaming issues"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by ben2000677 on 2010-02-18
Hi
I've been trying to change my ONLY user account name.
Lets say it's called 'Jimmy' and I want to call it 'Jambi'.
I managed to do this by making a root password, logging out, then using the root account to issue the
usermod -l Jambi Jimmy 
command

This has worked but in the new account there are two problems:
I can't change or rename the home dir
There is no networking icon at the top, so I can't get on the net

Please can someone help?
Thanks,
Ben

---

### Post by Satoru-san on 2010-02-18
> **ben2000677 said:**
> Hi
I've been trying to change my ONLY user account name.
Lets say it's called 'Jimmy' and I want to call it 'Jambi'.
I managed to do this by making a root password, logging out, then using the root account to issue the
usermod -l Jambi Jimmy 
command

This has worked but in the new account there are two problems:
I can't change or rename the home dir
There is no networking icon at the top, so I can't get on the net

Please can someone help?
Thanks,
Ben
```
usermod -d /home/Satoru -m -l satoru sakai

```I ran this just the other day. Here is how to fix your directorynow.

```
usermod -d /home/Jambi -m -l Jambi Jambi
```

A lot of things broke for me too. Things that pointed to /home/Jimmy intead of ~/

you will have to edit these manually.

---

