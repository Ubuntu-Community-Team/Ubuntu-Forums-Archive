---
title: "how to install ubuntu and xp on different partitions"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by wua on 2011-02-01
sorry for my english..

i'm using windows xp on my first partition. (C)

i want to use ubuntu on my second partition (D)

each partition is NTFS

how can i install ubuntu safely?

thanks...

---

### Post by [Snc] on 2011-02-01
> **wua said:**
> sorry for my english..

i'm using windows xp on my first partition. (C)

i want to use ubuntu on my second partition (D)

each partition is NTFS

how can i install ubuntu safely?

thanks...

Welcome to the forum!

Don't rush!

If you do not understand this post 100%, go to
```
http://translate.google.com/#
```
copy and paste this post into the translator.

Linux does not have "*c:*", "*d:*",... I guess, windows is on *"c:*" and "*d:*" is empty (no files).
That is the best option.

1. Get (if you haven't already) the Ubuntu ISO from [www.ubuntu.com](www.ubuntu.com) and burn it to a CD.

2. Reboot your computer with the CD inside and select "Try Ubuntu", to see how it looks like.
 
3. If you like it, on your desktop will be an "Install Ubuntu" icon, double-click it and the installation will start.

4. **THIS IS VERY IMPORTANT!!!**
[B]Make sure, you choose the right partition!!! 

Do not choose the windows partition!!![/B] 

Choose the one, that is currently **"d:"** (In windows, label the partition as something you can recognize or remember its size, anything, that can make it uniquely identifiable counts!!!)

5. Choose Ubuntu to install to that partition (currently "d:")
6. The install process **will** format that partition (**all data on it will be lost**)
7. Well, after that :) you have a dual booting system, the Ubuntu boot loader will let you choose Ubuntu/windows at startup.

---

### Post by Mark Phelps on 2011-02-01
OK ... from what I recall during installations, you're getting misleading information here ...

Ubuntu installs in one of two different wauys:
1) Using Wubi -- inside MS Windows, builds a large file on an existing NTFS partition
2) From the CD/DVD -- creates its own partition, formats that as Ext4, installs to that partition -- NOT inside Windows, NOT to an NTFS partition.

So, if you run the installation from inside Windows, using Wubi, you can install to "D:" but it will create a large file in that partition that will function as a Linux filesystem.

If you install from the CD/DVD, you can't install to "D:" because it's NTFS; instead, you would have to shrink your partitions to make room for new Linux filesystem partitions.

---

