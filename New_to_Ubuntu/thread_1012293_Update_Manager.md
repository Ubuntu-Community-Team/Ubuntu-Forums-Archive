---
title: "Update Manager"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by bakentake on 2008-12-15
Well a while ago I canceled an update in the middle because I wasn't gone for as long as I thought I would be and didn't want to wait for it to finish... now when I try to update it gives me this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I figure, I can just open terminal and type "dpkg --configure -a":

zach@zach-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


I was wrong. Anyone know how to solve this problem?

---

### Post by jay li on 2008-12-15
I think you forgot to put "sudo" before the line "dpkg --configure -a".

---

### Post by 67GTA on 2008-12-15
You need to use sudo in front of that command. Sudo gives you temporary administrator powers. ```
sudo dpkg --configure -a
```

---

### Post by bakentake on 2008-12-15
heh, I need to do more in terminal, been so long that I forgot sudo comes infront of most everything done in the terminal, thanks.

---

### Post by ahmedmsmh on 2008-12-17
thank you

---

### Post by nandemonai on 2008-12-17
> **bakentake said:**
> heh, I need to do more in terminal, been so long that I forgot sudo comes infront of most everything done in the terminal, thanks.

Only if your making system changes ;)

---

