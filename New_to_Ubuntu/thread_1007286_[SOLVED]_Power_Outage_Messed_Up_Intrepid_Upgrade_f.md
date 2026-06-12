---
title: "[SOLVED] Power Outage Messed Up Intrepid Upgrade for Gnome"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by crazy_lazy_bear on 2008-12-10
I left my computer to upgrade from Hardy to Intrepid overnight.  Unfortunately, we had a power outage in the middle of the upgrade.  I loaded the 2.6.24-22-generic (recovery mode) kernel.  That unpacked and configured the Intrepid packages.  I restarted the computer.  I now have a grub menu that includes the 2.6.27-10-generic kernel.  However, no matter which kernel I try, I can't get past the login screen when loading Gnome.  (I can load KDE with the 2.6.27-10-generic kernel with no problems.) I enter my username and password only to have the login screen reappear.  On the grub menu screen, when I press "e", I have three choices: root (hd0,0) (my Windows partition), savedefault, and chainloader +1.  Any help is greatly appreciated.  Thank you.

---

### Post by king_lear on 2008-12-10
I am just trying to guess the solution. You can go to Synaptic and search 'linux-image' and remove the kernel that fails to boot and reinstall it. Its an amateur solution but you can give it a try if you want.

---

### Post by billgoldberg on 2008-12-10
> **crazy_lazy_bear said:**
> I left my computer to upgrade from Hardy to Intrepid overnight.  Unfortunately, we had a power outage in the middle of the upgrade.  I loaded the 2.6.24-22-generic (recovery mode) kernel.  That unpacked and configured the Intrepid packages.  I restarted the computer.  I now have a grub menu that includes the 2.6.27-10-generic kernel.  However, no matter which kernel I try, I can't get past the login screen when loading Gnome.  (I can load KDE with the 2.6.27-10-generic kernel with no problems.) I enter my username and password only to have the login screen reappear.  On the grub menu screen, when I press "e", I have three choices: root (hd0,0) (my Windows partition), savedefault, and chainloader +1.  Any help is greatly appreciated.  Thank you.

I would just reinstall Ubuntu (8.10) if I were you. If you backed up your data before upgrading (you should have done that), you'll be up and running in 30 minutes.

---

### Post by crazy_lazy_bear on 2008-12-10
Thank you both for the prompt replies.  I tried to run Update Manager in KDE.  It gave me a message to run dpkg --configure -a.  I did so.  After a restart, Gnome loaded properly.  Again, thank you for the suggestions.

---

