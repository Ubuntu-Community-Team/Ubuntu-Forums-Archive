---
title: "How to delete VirtualBox guest partition?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-05-25
I had Windows 7 as a guest with VirtualBox and deleted it, but I haven't recovered the disk space that it took (20GB). I tried uninstalling VB but only ~77MB was going to be freed. How do I get 20GB back from VB?

Thanks!

---

### Post by cerealtx on 2009-05-25
> **sylvainrb said:**
> I had Windows 7 as a guest with VirtualBox and deleted it, but I haven't recovered the disk space that it took (20GB). I tried uninstalling VB but only ~77MB was going to be freed. How do I get 20GB back from VB?

Thanks!

you sure it didn't just make a .vdi? and not install to a specific partition?

---

### Post by nhasian on 2009-05-25
look in ~/.VirtualBox/VDI or ~/.VirtualBox/Machines

> **sylvainrb said:**
> I had Windows 7 as a guest with VirtualBox and deleted it, but I haven't recovered the disk space that it took (20GB). I tried uninstalling VB but only ~77MB was going to be freed. How do I get 20GB back from VB?

Thanks!

---

### Post by BkkBonanza on 2009-05-25
You have deleted the machine but not the associated hard disk image. Check ~/.Virtualbox/HardDisks for a large .vdi file. Delete that file to recover space. It's the virtual disk container and of course anything in it from Win 7 will be gone.

---

### Post by sylvainrb on 2009-05-25
> **cerealtx said:**
> you sure it didn't just make a .vdi? and not install to a specific partition?

Lol yes .vdi is what I meant and not an actual partition.

---

### Post by sylvainrb on 2009-05-25
Ok got it. That was quick thanks!

---

