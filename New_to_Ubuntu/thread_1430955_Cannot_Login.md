---
title: "Cannot Login"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by DancingFollower on 2010-03-16
I just installed ubuntu on my brother's formerly-WindowsVista computer.  A little background first:
Under windows, he couldn't login, it was trying to fix a crash, but it always failed and had to turn off. I was asked if it was something ubuntu could get around - which, sure, it's on a cd, installation shouldn't be a problem, right? So I installed it, though by the time it went through it looked like I was installing to an empty hard drive (no partitions labeled). That wouldn't contribute would it?

It booted from the cd fine, but once I installed it, it does not take me to the GUI screen to login, but a terminal-like screen asking for his login and password. The login part even works when I type, but we can't get the password.  What might be wrong with it that it doesn't go in to boot up normally? Also, what can I do from here?

Just a note, I am re-installing it now to see if that helps. But I thought I would get this going on the likely chance that it ... doesn't.

---

### Post by DancingFollower on 2010-03-16
Re-install worked, for whatever reason. :)

---

### Post by Gone fishing on 2010-03-16
To reset the password start up in recovery mode. At the first option screen select drop down to root shell then use the following command:

```
passwd username
```

and add the new password then confirm.

However, it strikes me that Ubuntu  has problems and as its new I'd be tempted just to reinstall.

---

