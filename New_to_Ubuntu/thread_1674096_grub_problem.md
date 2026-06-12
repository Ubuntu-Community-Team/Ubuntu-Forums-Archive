---
title: "grub problem"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by beew on 2011-01-23
Hi,

I made a really stupid mistake. I am making a multiboot system with Ubuntu, Fedora and another Linux distro called qomo which is kind of like Fedora but apparently uses grub2. I am only giving it 16 G because it is not a very mature distro and I am just trying it out (I may uninstall it in the future). Somehow I forgot to choose not to install a boot loader when I did the installation and now when I turn on the PC I see qomo's boot menu instead of Ubuntu's. 

I have no problem booting into Maverick as I can simply choose the right entry from qomo's boot menu, but I want to restore Ubuntu's boot menu instead. I have booted into Ubuntu and ran sudo update-grub but when I power the PC on I am still seeing qomo's boot menu.

Thanks in advance!

---

### Post by beew on 2011-01-23
Ok, can I simply delete the qomo partition using gparted from the Ubuntu partition, run sudo update-grub and reboot, or would I end up worse with an unbootable system?

---

### Post by QLee on 2011-01-23
> **beew said:**
> Hi,

I made a really stupid mistake. I am making a multiboot system with Ubuntu, Fedora and another Linux distro called qomo which is kind of like Fedora but apparently uses grub2. I am only giving it 16 G because it is not a very mature distro and I am just trying it out (I may uninstall it in the future). Somehow I forgot to choose not to install a boot loader when I did the installation and now when I turn on the PC I see qomo's boot menu instead of Ubuntu's. 

I have no problem booting into Maverick as I can simply choose the right entry from qomo's boot menu, but I want to restore Ubuntu's boot menu instead. I have booted into Ubuntu and ran sudo update-grub but when I power the PC on I am still seeing qomo's boot menu.

Thanks in advance!

Hi beew,

Try this,
Log in to Maverick and 
sudo grub-install --recheck /dev/sdX
sudo update-grub

I know you already understand to use the correct drive as the device.

---

### Post by beew on 2011-01-23
Hi, thanks. Just to clarify, the multi-system is in sdb, Maverick in sdb1. so I should replace sdx with sdb1?

---

### Post by beew on 2011-01-23
Hi, QLee

Sorry for the stupid question above. Of course it should be just sdb! It works perfectly. Thanks again. This is one lesson to remember.

---

### Post by beew on 2011-01-23
There is but a small problem. Now qomo has disappeared from the boot menu and Fedora appears twice (not two kernel versions) I ran sudo update grub in Maverick and qomo was detected, but it doesn't show up in the boot menu. This is not a big deal as I can simply reinstall qomo if I can't find another, better solution.

---

### Post by QLee on 2011-01-23
> **beew said:**
> There is but a small problem. Now qomo has disappeared from the boot menu and Fedora appears twice (not two kernel versions) I ran sudo update grub in Maverick and qomo was detected, but it doesn't show up in the boot menu. This is not a big deal as I can simply reinstall qomo if I can't find another, better solution.

It might be mistaking the gomo install for a Fedora I suppose. You could check if the partitions used match.


[Edit] It does seem like it should show up in the boot menu if it is identified in update-grub. If you run grub-mkconfig in a terminal it will do the same discovery as update-grub but run with no options it will just output to the terminal and not change the grub.cfg.

Are you using some kind of custom configuration in the maverick install, maybe a custom menu with OS prober turned off or something?

You could copy the stanza from the grub.cfg on the gomo install and use it in a custom entry for your Maverick boot menu.

---

### Post by beew on 2011-01-23
Hi, 

The Fedora entries on the boot menu are identical (both in /dev/sdb7, which is correct) and clicking either boots into Fedora, so I don't think one of them is actually qomo. qomo is in /dev/sdb9.

---

### Post by beew on 2011-01-23
Ok, this is really unbelievably stupid. Turns out the qomo entry was in the boot menu all along, but since there are too many items it just get pushed to the bottom and is hidden. Moving down the menu with a down arrow would find it.

---

### Post by QLee on 2011-01-24
> **beew said:**
> Ok, this is really unbelievably stupid. Turns out the qomo entry was in the boot menu all along, but since there are too many items it just get pushed to the bottom and is hidden. Moving down the menu with a down arrow would find it.

Good, glad you got it sorted out. Naturally, that part was something that we couldn't help with because only you are looking at your monitor, we have to rely on your description of what is happening.

---

