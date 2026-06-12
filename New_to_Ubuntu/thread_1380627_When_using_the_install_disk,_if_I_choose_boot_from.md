---
title: "When using the install disk, if I choose boot from 1st disk"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Devilham on 2010-01-13
The last option on the install disk is 'boot from 1st disk', I have windows on my first disk, will that force my machine to boot to windows?

---

### Post by Barriehie on 2010-01-13
> **Devilham said:**
> The last option on the install disk is 'boot from 1st disk', I have windows on my first disk, will that force my machine to boot to windows?

Yes, you'll be bypassing the install.  Go ahead and install and it will find windows and add it to your boot options in GRUB.  Good idea to partition your drive(s) so that your home partition is seperate from your boot partition.  This means you won't lose your stuff if you have to reinstall!  I've been running Ubuntu for 2 years and had to reinstall today and didn't lose a thing! 8)

---

### Post by Devilham on 2010-01-13
yeah, that's the problem, went ahead and installed, and now GRUB won't recognize my XP install.  I can't even mount the XP partition in Ubuntu (oddly I can if I boot to CD, just not in the full install).  If I can mount the drive, I am certain I can then get GRUB to see it too, but until then I am SOL

---

### Post by Barriehie on 2010-01-13
Post your /etc/fstab file and your /boot/grub/menu.lst file.  If you've got the legacy version of grub I can help.  Notice I'm still using 8.04!  What version did you install?

---

### Post by garvinrick4 on 2010-01-13
Here is a link to fix your XP boot. Not to tough at all.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Devilham on 2010-01-14
Thanks that fixed the XP install, now GRUB is no longer the bootloader, can I run a repair of Ubuntu to get GRUB back as the bootloader, hopefully recognizing the XP install

---

