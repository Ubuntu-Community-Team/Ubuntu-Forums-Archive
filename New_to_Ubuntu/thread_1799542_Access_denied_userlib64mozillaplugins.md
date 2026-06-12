---
title: "Access denied user/lib64/mozilla/plugins"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-07
Hi,

I was trying to move the .so file of Adobe Flash square into the directory in the topic name, but I get an errors saying "access denied". Why is that? I am the administrator, and I still am restricted from putting the downloaded file in there.

---

### Post by Theredbaron1834 on 2011-07-07
How are you trying to move it? With a term, nautilus, thunar, ect?

And this may be a stupid Q, but are you using sudo to start the command/program?

---

### Post by wildmanne39 on 2011-07-07
> **WubiAR said:**
> Hi,

I was trying to move the .so file of Adobe Flash square into the directory in the topic name, but I get an errors saying "access denied". Why is that? I am the administrator, and I still am restricted from putting the downloaded file in there.Hi, open the file manager with 
```
gksu nautilus
```

---

### Post by WubiAR on 2011-08-01
Hi I am trying this technique for Xubuntu 11.04 and it isn't working. Is there another way of editing the files in the File System?

---

### Post by pqwoerituytrueiwoq on 2011-08-01
gksu thunnar 
if i recall correctly

you can always use "flash aid" and it will do it just right

sudo mv ~/Downloads/libflashplayer.so /usr/lib64/mozilla/plugins

---

