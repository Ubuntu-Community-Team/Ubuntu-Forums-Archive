---
title: "How Do I install Windows After Ubuntu"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by DizzyEwok on 2009-02-17
Hi,
Today I want to dual boot my DELL Latitude D600, with Windows & Ubuntu. Currently it has Ubuntu only running on it. I have read various forums and what  needs to be done seems quite complicated. 
Please could someone give me a step-by-step detailed but beginner friendly guide on how I would do it.

Thanks

By the way, I want to install Windows 2000 Server Edition.

---

### Post by albandy on 2009-02-17
sudo apt-get install virus

Ok, it was a joke:

First of all you need an unused partition, if don't you should use some resizing software as parted or partition magic

Then simply install windows in the unused partition, it will erase the boot manager, so ubuntu will disapear temporaly.

Boot with the ubuntu CD and run the recovery console, then reinstall grub by doing
grub-install /dev/sda (sda is the name of your first hard disk)

exit the console and reboot the machine

---

### Post by linux_tech on 2009-02-17
It is easier to have windows already installed, then install ubuntu but
here is something to help-
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by superprash2003 on 2009-02-17
here's another link [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by DizzyEwok on 2009-02-17
Thanks guys, I installed it successfully!

---

