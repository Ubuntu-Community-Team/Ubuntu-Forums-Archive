---
title: "Need help with updates"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by MPX11 on 2009-01-28
I am having problems installing updates, every time I want to do the updates I receive this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 then when I go to the terminal and run this: 'dpkg --configure -a' 
I get this message:

bet@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
 
what does it mean? Am I doing something wrong?

---

### Post by billgoldberg on 2009-01-28
> **MPX11 said:**
> I am having problems installing updates, every time I want to do the updates I receive this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 then when I go to the terminal and run this: 'dpkg --configure -a' 
I get this message:

bet@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
 
what does it mean? Am I doing something wrong?

Yes you did something wrong :p.

This error usually occurs when you close a package manager while it's installing something.

It is however very easy to fix.

Go to "applications -> accessories -> terminal".

Enter:

```
sudo dpkg --configure -a
```

Then enter your password and press enter. (you won't see anything as you type your password)

Fixed.

--

Sudo is used when you need to enter a command with root privileges.

---

### Post by MPX11 on 2009-01-28
thanks a lot Billgoldberg, your advice fix the problem and now I am downloading the updates.

---

