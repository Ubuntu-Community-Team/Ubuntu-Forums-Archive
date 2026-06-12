---
title: "Howto install grub into the linux installed partition insteed of the MBR?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by matiz on 2010-03-04
Hi, first, thanks for view this post.
I wonder howto install grub into the linux installad partition insteed of the MBR?

Awaiting the best answers.

---

### Post by spectralblue on 2010-03-04
> **matiz said:**
> Hi, first, thanks for view this post.
I wonder howto install grub into the linux installad partition insteed of the MBR?

Awaiting the best answers.


Are you talking about Grub or Grub 2 because setup's different for each I believe. 

For Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
For Grub 2: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It's definitely possible. For Grub, instead of typing setup (hd0) for example, you would type setup (hd0,0) for partition 1. Grub 2 names it differently so see the other guide.

---

