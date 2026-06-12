---
title: "HP Pavillion Kernel Panic"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Koobelakahn on 2010-04-24
Hello fellow Ubuntu lovers.
I am currently attempting to install my beloved Ubuntu (version 9.04) on a laptop. It boots from the live CD, and it goes through the entire installation process without a hitch. Then, on reboot, thats when I receive it. The error that makes me cringe in frustration. The dreaded KERNEL PANIC *cue scary music*

Ok, all joking aside, this kernel panic is causing quite a fuss. The error is exactly as you see it.
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
``` The computer is a HP Pavillion Entertainment Notebook PC (the sticker on the back says HP Pavillion dv1000)

So my question is, what is going on, and how can I fix this. I can take apart the computer, but that would be a last resort.

---

### Post by MrWES on 2010-04-24
Try this:

Restore Grub

 find /boot/grub/stage1

root (hd1,0) <-- wherever stage1 was found

setup (hd1)

---

