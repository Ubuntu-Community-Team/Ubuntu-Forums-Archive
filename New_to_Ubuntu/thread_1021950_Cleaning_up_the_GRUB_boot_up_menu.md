---
title: "Cleaning up the GRUB boot up menu"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Steve05TSX on 2008-12-26
I currently have a dual boot setup using Ubuntu 8.10 and Vista.  I'd like to get rid of the 2 other boot options that Ubuntu has in there if possible.

There is the Memtest one, and recovery mode 

any ideas?

Thanks

---

### Post by zvacet on 2008-12-26
If you have just one Ubuntu kernel **don´t touch that**.

---

### Post by northern lights on 2008-12-26
The GRUB menu resides in */boot/grub/menu.lst*. You could comment out or delete the memtest entry, but I'd highly recommend keeping the Recovery Mode at least. You don't know when it might come in handy.

Should you need more in-depth instructions than the above, I'd advise you to refrain from altering system files.

If you're interested, here's the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html").

---

### Post by hamofgrey on 2008-12-26
Hi there,

Here is a tutorial on how to clean GRUB up. Enjoy:

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

This will show you how to get rid of different options from grub. Makesure that you test everything works in the kernel upgrades before you delete the other older kernel options from the list. 

Also I personally think it's important **not** get rid of things like the Recovery and MemTest options, otherwise if anything major goes wrong you have no real way of being to sort the problem out. You are still able to boot into these options using grub but it will require a little bit of extra effort by typing something into the command line.

Perhaps a better way of explaining it is, that when you use Windows Vista on a laptop or PC and there is a power cut on the next boot Vista will ask you if you want to boot up in the regular fashion or boot up in other recovery modes (e.g. with command-line etc). It would be dangerous to get rid of all the options as you may depend on some of the recovery features in certain situations. The same can be applied to Ubuntu, there may be certain situations where some of the recovery features are also needed.

I hope this helps :)

---

### Post by drs305 on 2008-12-26
Install StartUp-Manager. It's a gui app that will let you tweak many of grub's menu settings.

I wrote a tutorial specifically about limiting the number of kernels displayed in the menu, but expanded it to include other options of StartUp-Manager, including menu timeout, default kernel, colors, etc.

Here is the link: [URL="http://ubuntuforums.org/showthread.php?t=818177"] HOWTO: Grub Menu Kernel Display Options
[/URL]

If you would prefer to manually edit menu.lst there is information for doing that as well.

---

