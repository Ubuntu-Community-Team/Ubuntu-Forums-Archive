---
title: "File permissions"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by child on 2009-11-23
Hi!

My problem is simple: I would like to ask about file permissions.
I read tutorials of course, but I think I'm not getting it. I wanted a program to have right to write into those files which it uses. But I don't know how to do this. Please, if you have a little time, help me.

---

### Post by MrReaper on 2009-11-23
> **child said:**
> Hi!

My problem is simple: I would like to ask about file permissions.
I read tutorials of course, but I think I'm not getting it. I wanted a program to have right to write into those files which it uses. But I don't know how to do this. Please, if you have a little time, help me.

Could you be more specific? Are you trying to write to file which only root can access? If so, try one of these:
```
sudo gedit /filepath
sudo nano /filepath
```Otherwise explain your problem a bit, I don't get it.

---

### Post by emigrant on 2009-11-23
you mean for a script you wrote?

---

### Post by child on 2009-11-23
It's in the /usr folder. And only root can access to it. And I want the program to be able to read and write the files are in that directory.

---

### Post by halitech on 2009-11-23
> **MrReaper said:**
> Could you be more specific? Are you trying to write to file which only root can access? If so, try one of these:
```
sudo gedit /filepath
sudo nano /filepath
```Otherwise explain your problem a bit, I don't get it.

for using graphical apps you should use gksudo, not sudo

```
gksudo gedit /path/to/file
```

---

### Post by child on 2009-12-02
Thank you.

---

