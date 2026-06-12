---
title: "no folder highlighting in terminal!!"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by carrarin on 2010-11-19
Hello everyone,

For some reason, the folders in my terminal are not highlighted a different color from the files. I want back my highlighting!!

Thanks

---

### Post by DaithiF on 2010-11-19
in your .bashrc alias ls to ls --color=auto

---

### Post by carrarin on 2010-11-19
I dont have a .bashrc file... I created one and restarted my terminal. Still have no highlighting...

---

### Post by sisco311 on 2010-11-19
> **carrarin said:**
> I dont have a .bashrc file... I created one and restarted my terminal. Still have no highlighting...

You can copy the default .bashrc file from /etc/skel:
```
cp /etc/skel/.bashrc ~/.bashrc
```
source the file and see if it works:
```
. ~/.bashrc
ls ~
```

---

### Post by carrarin on 2010-11-19
That works!! 

Thanks Sisco

---

