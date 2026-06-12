---
title: "Access Ubuntu"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by anglicotre on 2009-04-11
i want to access ubuntu through windows command prompt can you help?

---

### Post by anglicotre on 2009-04-11
i want to access ubuntu through windows command prompt can you help?

---

### Post by overdrank on 2009-04-11
Hi and welcome, I have moved your post to its own thread.

---

### Post by skymera on 2009-04-11
Through Windows?

I use PuTTY to SSH into my Ubuntu machine :D

---

### Post by MrWES on 2009-04-11
> **anglicotre said:**
> i want to access ubuntu through windows command prompt can you help?

Install openssh-server on your Ubuntu machine. From a terminal type:
```
sudo apt-get install openssh-server
```

Then take a look at your /etc/ssh/sshd_config and configure accordingly

On your windows computer install PuTTy:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")

Bill

---

