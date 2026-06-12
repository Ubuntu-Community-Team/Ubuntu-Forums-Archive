---
title: "Beginner Questions"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Crgthom on 2009-08-21
I am running Windows 7 on a hard disk with 120gb capacity. I also had a 20gb partition of ubuntu.

I could not select the partition during the ubuntu install, so it ended up going on the main partition. When I load Windows my main hard disk no registers a capacity of 118gb. The 2gb is taken up by ubuntu and therefore I cannot install anything with it.

Can I move ubuntu to the specially created partition, or do I have to uninstall it and reinstall it?

Thank you.

---

### Post by Lavaeagle on 2009-08-21
In your situation you will have to Uninstall and Reinstall.

---

### Post by ithinkitschad on 2009-08-21
> **Lavaeagle said:**
> In your situation you will have to Uninstall and Reinstall.

yeah.. thats a bummer

---

### Post by ithinkitschad on 2009-08-21
...unless you know witchcraft...

---

### Post by perce on 2009-08-21
> **ithinkitschad said:**
> ...unless you know witchcraft...

It's actually possible: I did it once with cp -a a few years ago, when installing was a long and painful story. But now it's surely simpler to reinstall.

---

### Post by tarps87 on 2009-08-21
Did you install it using wubi (through windows), if so not you can't and reinstalling will not work as it installs it on the windows hard drive (unless the other partition is a windows format). If you want it on a separate partition it would suggest a proper install on a Linux base file system and you will need to reinstall to do this.
If it is a proper install then yes you can move it. Boot the live cd and use gparted (I believe it is called partition editor under System -> admin) to find the new partition you set up and delete it now just extend the partition created by Ubuntu.

---

