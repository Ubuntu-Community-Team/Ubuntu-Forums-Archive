---
title: "'no loaded kernel'"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by podkayne on 2009-12-27
I've recently fielded a number of bootloader errors, including apparently the total absence of a bootloader, since I stopped dual-booting Windows XP and Ubuntu 9.10 and tried running Ubuntu only.
 
The latest issue appears when I try to boot from the GRUB command line and receive the response 'no loaded kernel'. I simply don't understand why I receive this message, and can't seem to locate a way through the issue or understand the resources I find, since I never work at this level otherwise and am very ignorant of these workings. For the time being I can only boot from the CD drive, although apparently the contents of the hard drive are otherwise intact. Would anyone have advice for me? A pointer to a good primer on booting would be cool, too, since the whole topic is beginning to sound very intriguing.

---

### Post by drs305 on 2009-12-27
> **podkayne said:**
>  A pointer to a good primer on booting would be cool, too, since the whole topic is beginning to sound very intriguing.

Here is the community doc for Grub 2. You can see if that is the version you are running at the top of the boot menu. Grub 2 is currently at version 1.97 (beta4) for Ubuntu.

The message means that Grub hasn't loaded the linux kernel - normally because it is either looking in the wrong location or because the kernel isn't where it should be. Go through the Grub Command Line section carefully and try booting using the examples found in this section:
[https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

