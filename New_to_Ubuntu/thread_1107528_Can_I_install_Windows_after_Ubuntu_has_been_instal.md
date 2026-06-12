---
title: "Can I install Windows after Ubuntu has been installed"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by sanjeevpunj on 2009-03-26
[Solved]I Installed Ubuntu, and I did not use a part of my disk, so the unallocated space is available for another OS. I want to install Windows in this unallocated space. Will it affect my Ubuntu Installation in any manner?

---

### Post by bhishan on 2009-03-26
Windows boot loader is not friendly to other operating systems. I think there is a way to do it, but I would recommend backing up ur data, installing windows and then installing ubuntu.

---

### Post by Bachstelze on 2009-03-26
No, but it will erase the Master Boot Record of your drive, so you will have to reinstall the GRUB bootloader.

---

### Post by kansasnoob on 2009-03-26
It's a slight problem. Not too bad.

With XP:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

With Vista:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by presence1960 on 2009-03-26
> **sanjeevpunj said:**
> I Installed Ubuntu, and I did not use a part of my disk, so the unallocated space is available for another OS. I want to install Windows in this unallocated space. Will it affect my Ubuntu Installation in any manner?

You certainly can do that. But as HymnToLife said you will need to reinstall GRUB because Windows will wipe it. I have installed Windows after Ubuntu a number of times on friend's machines who hastily wiped Windows then found the Linux learning curve a little steep. They were gonna wipe their drives again, install windows then Ubuntu, so I showed them how to install Windows after Ubuntu.

---

### Post by presence1960 on 2009-03-26
> **kansasnoob said:**
> It's a slight problem. Not too bad.

With XP:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

With Vista:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

+1 
kansasnoob, I remember using those when I first started.

---

### Post by sanjeevpunj on 2009-03-27
Thanks for all your replies,I understand that I must re-install grub after I install Windows, and I think the Grub is installed will be updated automatically or I mgiht have to update it. Thanks a lot guys, this is awesome, Ubuntu is a huge circle of friendly people.

Best wishes to you all, have a great day.

---

