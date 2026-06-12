---
title: "What is a dangling symlink ?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-23
I have one that points to my nonworking cdrom drive.

I cant seem to change permissions on it.

How do you handle these ?


thx

---

### Post by snova on 2009-02-23
A dangling symlink is just a symlink with an invalid target (that is, the target file doesn't exist).

> **mistypotato said:**
> I cant seem to change permissions on it.

That's normal. The effective permissions are the same as the file it points to.

> How do you handle these ?

Depends on what you want to do with it... it's just a file, albeit a file that acts strangely when you read from it.

---

### Post by mistypotato on 2009-02-24
I found that when I restored 8.10 server from my MondoRescue backup, the file that configured the cdrom media (forgot which file already) was using the scsi line and once I commented it out...all was well again.

thx

---

