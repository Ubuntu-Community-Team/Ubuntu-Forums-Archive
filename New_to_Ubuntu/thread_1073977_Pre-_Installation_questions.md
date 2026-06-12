---
title: "Pre- Installation questions"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by conman5 on 2009-02-18
Hi,

I'm interested in installing Ubuntu onto my computer, mainly to learn about an operating system other than Windows. I have some computer experience, but non with having multiple operating systems on the same systems.

1) If I install Ubuntu, will it make Windows XP inaccessible?
2) How would I change between operating systems?
3) I can do this on a separate harddrive and/or partition?

Thank you for your time,
Conman5

---

### Post by taurus on 2009-02-18
1.  No.  You can access your windows partition with read/write under Ubuntu with ntfs-3g driver.

2.  When you install Ubuntu, it will install GRUB to MBR, giving you an option which OS you want to boot when you turn on your machine.

3.  You can install Ubuntu on it own partition (probably best) or you can install it under windows using wubi.

For more info, here is something you might want to have a look.

[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

---

### Post by OutOfReach on 2009-02-18
1. No you can dual-boot safely. Just be careful and read the instructions if you don't understand the instructions, post here and we'll help you!
2. You would need to reboot into that operating system.
3. Yes of course! :)

Hope that helped a bit.

---

### Post by Old_Grey_Wolf on 2009-02-18
You can also install Ubuntu within Windows using Wubi [http://wubi-installer.org/](http://wubi-installer.org/) or using Virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by conman5 on 2009-02-18
First, thank you for responding to my questions.


After reading some of the documentation posted (thanks Taurus), I just have one question.

So, if I place in a new harddrive and/or partition and attempt to install Ubuntu, the installation will create some form of boot menu that allows me to choose which operating system I want to choose?

---

### Post by Pollox on 2009-02-18
> **conman5 said:**
> First, thank you for responding to my questions.


After reading some of the documentation posted (thanks Taurus), I just have one question.

So, if I place in a new harddrive and/or partition and attempt to install Ubuntu, the installation will create some form of boot menu that allows me to choose which operating system I want to choose?

Yes.  It's called GRUB.

---

### Post by taurus on 2009-02-18
Yes, GRUB is what you have in mind or want.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by conman5 on 2009-02-18
Ok thanks for the info.

Also, one more question. If I try Ubuntu out for a while and decide that it is no for me, is it possible to remove this GRUB utility?

---

### Post by taurus on 2009-02-18
You can boot into windows and run /fixmbr from the DOS prompt to remove GRUB from MBR.  Or use Super GRUB Disk, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by conman5 on 2009-02-18
Ok, thank you everyone for helping me understand. Now all I need to do is grab a harddrive (my current one is to full) and install ubuntu. :)

Conman5

---

