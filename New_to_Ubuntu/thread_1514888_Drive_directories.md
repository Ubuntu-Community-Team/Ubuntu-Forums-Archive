---
title: "Drive directories"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by snowmanman on 2010-06-21
How do I get to other drives from the Terminal? I wanted to access roms on another hard drive with ZSNES, but I don't know where it is. What I want to do is like in Windows, "C:\> E:" and get to another drive. How do I do this in Ubuntu?

---

### Post by nothingspecial on 2010-06-21
You have to mount them then use cd to get to them.

They should auto mount, probably to /media

See where they are in the file system then cd followed by the path 
eg
```

cd /media/disk
```

---

### Post by bodhi.zazen on 2010-06-21
> **snowmanman said:**
> How do I get to other drives from the Terminal? I wanted to access roms on another hard drive with ZSNES, but I don't know where it is. What I want to do is like in Windows, "C:\> E:" and get to another drive. How do I do this in Ubuntu?

Linux is not windows, and drives / partitions are not referred to by letter. 

You mount the partition somewhere, such as /media/windows, you the cd /media/windows.

See:

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by snowmanman on 2010-06-21
Thanks nothingspecial.

I know that bodhi.zazen, I was just giving an example in case i was hard to understand.

---

