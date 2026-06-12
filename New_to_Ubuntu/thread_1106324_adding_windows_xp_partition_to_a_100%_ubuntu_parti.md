---
title: "adding windows xp partition to a 100% ubuntu partition"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by libihero on 2009-03-25
my partition is 100% ubuntu at the moment, and I want to add windows xp to it.  can someone show me a step by step guide to doing it?  last time i tried to do somethin like this i accidently erased my hard drive.

---

### Post by ibuclaw on 2009-03-25
Do you mean that you wish to install Windows XP alongside Ubuntu?

Or do you just want to have an NTFS filesystem for file/data backup?

Regards
Iain

---

### Post by halitech on 2009-03-25
Here's a link that might help you out.

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

---

### Post by libihero on 2009-03-25
ya i want to add windows xp to my ubuntu so i can dual boot (i really wanna just run xp from virtualbox).  on the guid it says to download gparted on a cd, but i already have it.... so do i need to do that?

---

### Post by halitech on 2009-03-25
if you want to run it from virtualbox then you don't need to install it in a dualboot, just install virtualbox and load it up there

---

### Post by Ms_Angel_D on 2009-03-25
Here's a great tutorial with screenshots on how to dual boot ubuntu and xp with ubuntu installed first

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by libihero on 2009-03-25
> **halitech said:**
> if you want to run it from virtualbox then you don't need to install it in a dualboot, just install virtualbox and load it up there
I would need to have the CD in though wouldnt i?

---

### Post by odinb on 2009-03-25
If all you want to do is to run XP in virtualbox, there is no need for GParted or to repartition your disk!

the XP disk will be a file in your home-directory.

Just install virtualbox, and then install XP following the wizard in virtualbox.

---

### Post by MysticGold04 on 2009-03-25
Yes, you do.. It will install just like normal.  I have VirtualBox setup with a 20gb space for XP.

---

### Post by odinb on 2009-03-25
> **libihero said:**
> I would need to have the CD in though wouldnt i?

Or you can mount the XP iso image in virtualbox if you have it. That is what I do!.

---

