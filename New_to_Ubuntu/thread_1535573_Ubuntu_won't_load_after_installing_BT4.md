---
title: "Ubuntu won't load after installing BT4"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by Zens on 2010-07-21
Hi all,

Recently, I installed BT4 by allocating it a 15GB partition and using the same swap space as my Ubuntu install.

I understand now that it wasn't the wisest decision since BT4 overrode the GRUB 2 files, and I'm now stuck using GRUB legacy.

When booting up, the GRUB menu presents me with 3 choices; Ubuntu, Ubuntu recovery mode, and Windows Vista / Longhorn (although I'm running Win 7, which was what was displayed prior to BT4's installation).

Upon choosing any of the 2 Ubuntu options, my laptop boots into BT4. I tried editing the menu.lst through BT4, but I'm not familiar with GRUB legacy, so I'm not sure what to do.

Was using the same swap space a mistake? How can I edit the menu.lst to boot into Ubuntu? Once I have Ubuntu running, can I execute update-grub to clean this mess and use GRUB 2 instead of the legacy version?

Thank you for any help :D

---

### Post by marshmallow1304 on 2010-07-21
Have a look at Section 13 on [The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275").

It's OK to use the same swap partition for multiple distros, but be careful if you use Hibernate, since it saves the contents of RAM into the swap partition.

---

### Post by ranch hand on 2010-07-21
The best things you can do is;

A>recover your ubuntu grub using these direction;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ignore the part about editing files, you should not need that.

B>if that does not work post the complete results of this;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

here and I am sure we can sort this out.

---

### Post by Zens on 2010-07-21
Success!

Marshmallow's link worked flawlessly.

Thank you both for your help.

I looked through that thread and various others, and I was able to add BT4 to the GRUB menu as well as delete old kernels. :D

---

