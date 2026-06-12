---
title: "I want to Install with Wubi, but I already have a dual boot"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by metalaxesucks on 2009-07-18
My main question/concern is that I already have a dual boot set up with 9.04 where when my computer starts up I select with Grub which system I want to use: Ubuntu or Vista

I plan on installing Ubuntu 8.10 on my Vista partition using Wubi. However, I saw video instructions where during setup you have to restart your PC a couple of times & select Ubuntu in the grub menu to allow it to finish setting up.

Here is where my concern comes in
Being that my PC already has Grub setup, will the process of of using Wubi (when Wubi sets up it own little grub to install Linux in Vista) will this mess up my already configured Grub?

---

### Post by jeppewinther on 2009-07-18
This question has been answered right [http://ubuntuforums.org/showthread.php?t=766039](http://ubuntuforums.org/showthread.php?t=766039) there.

The short answer is no it won't mess up Grub.
If you install Wubi on your Windows partition, you will first see the Grub boot loader, then if you choose to boot Windows, you will see the Wubi one prompting you whether you REALLY want to boot up Windows.

---

### Post by philcamlin on 2009-07-18
yeah i dont think that would go

---

### Post by metalaxesucks on 2009-07-18
Thank you guys sooooo much!!!
I'm going to try it!!!

---

