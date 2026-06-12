---
title: "Why do I have 6 ubuntus!!!"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by filifunk on 2009-08-20
When I turn on my computer (installed through dual boot), I get to choose what system I use, my trouble is that I have 6 ubuntus to choose from.  It used to be only 2 (I just installed a few days ago), but it's been growing! This is what I get when I turn on my computer...this is what I get to choose from.

Ubuntu 9.04 kernel 2.6.28-15-generic
Ubuntu 9.04 kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04 kernel 2.6.28-14-generic
Ubuntu 9.04 kernel 2.6.28-14-generic (recovery mode)
Ubuntu 9.04 kernel 2.6.28-11-generic
Ubuntu 9.04 kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04 memtest 86+

Other systems:
Windows Vista (loader)
Windows Vista (loader)

-------------------------------------------

so can someone explain what all these Ubuntu's for?  Also is it wierd that I have two Windows Vista?  Is there any way that all these Ubuntu's are taking up memory?

Thanks all

---

### Post by shylent on 2009-08-20
Oh, it's perfectly normal. You've probably installed some updates since the initial installation. Every time the kernel is updated, it doesn't get replaced, but actually, it retains the previous version (so that you can easily roll back to the version that used to work for you if something goes wrong).

By the way, that menu is controlled through the configuration file /boot/grub/menu.lst. But I'd rather you not touch it just yet :P

---

### Post by Keen101 on 2009-08-20
They are called Linux Kernels. Everytime you do an update ubuntu installs the latest kernel. Sometimes with a new kernel things get better support, and sometimes you can get regressions. By default it lets you choose an older kernel to boot from if there is the off chance you have a problem with a new kernel.

There are ways to remove them, and/or hide them so you only have 1 and 1 recovery option, but that would require editing you GRUB bootloader menu file.

/boot/grub/menu.lst

---

### Post by Papa-san on 2009-08-20
With that explained, I am left wondering why there are two Windows Vista loaders...?

---

### Post by credobyte on 2009-08-20
> **Papa-san said:**
> With that explained, I am left wondering why there are two Windows Vista loaders...?

It's Vista - if there's 2 of them, it's just supposed to be so :KS

---

### Post by filifunk on 2009-08-20
Oh thanks guys, my computer isn't so weird then...but why are there two windows vista loaders?  Is one like a recovery mode type loader?

---

### Post by ibutho on 2009-08-20
> **Papa-san said:**
> With that explained, I am left wondering why there are two Windows Vista loaders...?

Do you have two NTFS partitions? Some computers have a Windows rescue/revovery partition and then the main Windows partition. If you have such a setup, this could be why you have to Windows Vista loaders listed in grub.

---

### Post by Keen101 on 2009-08-20
yeah, most likely a recovery partition if your computer came from dell or hp.

---

### Post by bacardiandwatermelon on 2009-08-20
Just so you know, you can remove the old images from synaptic, my current is called linux-image-2.6.31-6-generic, because I am using grub2 I then ran update-grub and that removes them.

---

