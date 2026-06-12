---
title: "Grub loader"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by tongueman on 2009-12-30
Can anyone explain why my grub loader keeps making duplicates and/or how do i get rid of some.

My grub loader look a bit like this(i'm guessing the exact details, just a bit frustrated with the duplicates)

ubuntu 22.1.167.10 kernel 9.10
ubuntu 22.1.167.10 kernel 9.10 (recovery mode)
ubuntu 22.1.167.10 kernel 9.10
ubuntu 22.1.167.10 kernel 9.10 (recovery mode)
ubuntu 22.1.167.10 kernel 9.10
ubuntu 22.1.167.10 kernel 9.10 (recovery mode)
ubuntu 22.1.167.10 kernel 9.10
ubuntu 22.1.167.10 kernel 9.10 (recovery mode)
Windows vista

Any help would be much appreciated.

Many thanks

---

### Post by LeifAndersen on 2009-12-30
It's because new versions of the linux kernel are being installed.  If it makes you feel any better, I also think it's not a good UI decision.  The easiest thing you can do is install "Startup Manager" from the Ubuntu Software Center, at that point, you can decide what you want to show up in the grub menu.  (I would recommend this rather than actually removing the kernels themselves, because you may find them useful later)

---

### Post by QIII on 2009-12-30
You can take careful notes about which kernels you don't want, remove them via Synaptic, and update GRUB.  (Look for both "-generic" and "-headers", but be sure they are the ones you want to get rid of).  Be careful!  You don't want to remove the wrong ones.

I usually keep the previous version just in case I run into problems with the newest.

Since you are using Karmic, be aware that SUM is a work in process and may not be the best route right now.

---

### Post by Howie Spitz on 2009-12-30
Here are some more ways to remove old kernels from your system and from the GRUB menu.I would at least keep the two most recent kernels and their (Recovery Mode) entries.
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)
I just used the CLI method, worked perfectly for me using GRUB2.

---

