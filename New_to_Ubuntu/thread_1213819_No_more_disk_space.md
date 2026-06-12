---
title: "No more disk space"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by yangt299 on 2009-07-15
Hi, 

I am running Windows Vista along with Ubuntu 9.0.4 on my laptop. However, I am having trouble with Ubuntu. Every time I try to load it, it displays an error message GDM out of disk space or something. Does anyone know how to fix this problem? By looking at [http://ubuntuforums.org/showthread.php?t=348748](http://ubuntuforums.org/showthread.php?t=348748), I am pretty sure it is because I have Vista on that computer too. However, I cannot empty disk in Ubuntu or anything because I dont have access to it.

---

### Post by philinux on 2009-07-15
Either use this.
[http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista)

Or your live ubuntu cd.

---

### Post by Paqman on 2009-07-15
You should be able to boot up into recovery mode and drop to the command line. From there try clearing out some space with:
```

apt-get autoremove

```

You won't need "sudo" from the recovery mode command line. If that doesn't give you enough to boot into a graphical session then try temporarily removing a really big package like Open Office. Once you're booted up properly you can start really clearing out some junk, and hopefully expanding your Ubuntu partition. If you installed with Wub you can use the package LVPM to expand your virtual partition.

---

### Post by 3rdalbum on 2009-07-15
> **yangt299 said:**
> I am pretty sure it is because I have Vista on that computer too.

Vista uses its own partition that Ubuntu doesn't access, and vice-versa. It's like if you put a wall in the middle of a room, and have one person living on each side of the wall. A messy person might run out of space in his half of the room, but he wouldn't blame the person on the other side of the wall because they have their own space.

How much space did you allocate for Ubuntu? I hope you gave it more than the minimum 3 gigabytes?

---

### Post by yangt299 on 2009-09-15
> **3rdalbum said:**
> Vista uses its own partition that Ubuntu doesn't access, and vice-versa. It's like if you put a wall in the middle of a room, and have one person living on each side of the wall. A messy person might run out of space in his half of the room, but he wouldn't blame the person on the other side of the wall because they have their own space.

How much space did you allocate for Ubuntu? I hope you gave it more than the minimum 3 gigabytes?

LOL, sorry for replying 3 months later. I forget how many i gave the system, but whatever it was, I just set it to default. Is there a way that I can remove Ubuntu and then reinstall it, without removing Vista? 

Thanks!

---

### Post by k33bz on 2009-09-15
> **yangt299 said:**
> LOL, sorry for replying 3 months later. I forget how many i gave the system, but whatever it was, I just set it to default. Is there a way that I can remove Ubuntu and then reinstall it, without removing Vista? 

Thanks!

Use your live cd and re-install over your existing Ubuntu partition

---

