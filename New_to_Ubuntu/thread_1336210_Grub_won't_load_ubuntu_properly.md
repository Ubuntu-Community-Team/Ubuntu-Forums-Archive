---
title: "Grub won't load ubuntu properly"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-24
I installed ubuntu using wubi, and everything seemed to work fine, but when I use boot manager to select ubuntu, grub comes up on a black screen saying something like [Minimal BASH-like...] then has a spot for me to input commands.  It doesn't let me select ubuntu or anything like usual, can anyone help?  Thanks,.

---

### Post by drs305 on 2009-11-24
First, welcome to Ubuntu and the Ubuntu forums Space-Wolf. What version do you have installed? Karmic uses Grub 2, and it's possible you can boot from the command line. 

The Ubuntu community doc has instructions on how to boot from the grub prompt. For some reason, Grub cannot find or use the boot configuration files. I am not well-versed in wubi and Grub 2, but see if these commands work:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

If you can get to the Ubuntu desktop we can then try to fix the configuration files permanently.

---

