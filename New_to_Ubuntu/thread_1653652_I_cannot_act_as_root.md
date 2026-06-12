---
title: "I cannot act as root"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by enverhoxha on 2010-12-27
I have to perform a simple task: in the /usr/share/sounds directory I want to add a sound file to be played by a timer program called sanduhr. So I need to right-click and use Paste. This does not work.
Ubuntu tells me that I am not the ”owner” (of the directory) and I have no permissions - the owner is ”root”. And this for the entire /usr directory. 
I know that in Terminal you use sudo to get root privilege, but this does not help me at all with my task. I dont know how to use the Terminal to enter commands for a copy/paste operation, its too DOS-like.
Is there any simpler way to do such things, like an average stupid Windows user?

---

### Post by Mr. ViC on 2010-12-27
Have you tried entering the command:

```
gksudo nautilus
```

And then try to copy/paste it again?

---

### Post by enverhoxha on 2010-12-27
Thanks. Works fine.

---

### Post by Mr. ViC on 2010-12-27
Glad to help buddy.

---

