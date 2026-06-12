---
title: "Attempting to back up my data"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-11-02
Hey Everyone,

I upgraded to karmic from jaunty earlier this week and it seems the update has failed. Now I'm going to install from a CD, but first I need to backup my files.

I want to take my entire home directory and copy it to a USB drive. However, apparently this is not possible. Ubuntu complains of file permissions and is making a fuss out of it. 

Nautilus throws up various messages saying 
Error making symbolic link: Operation not permitted

Not permitted? I chowned -R the entire directory. How is it not permitted?
Is this going to affect anything?

Thanks! :popcorn:

---

### Post by LewRockwell on 2009-11-02
use clonezilla for cloning partitions and/or whole drives

don't make "images" if you need to manipulate data via direct access to the clone(images are compressed and generally unaccessible)

.

---

### Post by QLee on 2009-11-02
[QUOTE=asuastrophysics]I want to take my entire home directory and copy it to a USB drive. However, apparently this is not possible. Ubuntu complains of file permissions and is making a fuss out of it. 

Nautilus throws up various messages saying 
Error making symbolic link: Operation not permitted

Not permitted? I chowned -R the entire directory. How is it not permitted?[/QUOTE]

What type of filesystem is on that USB drive, is it one that allows permissions and symlinks?

---

### Post by asuastrophysics on 2009-11-02
> **QLee said:**
> What type of filesystem is on that USB drive, is it one that allows permissions and symlinks?

it's an apple ipod video. uhh fat32 i think! ;)

---

