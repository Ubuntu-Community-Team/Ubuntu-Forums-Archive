---
title: "replacing grub-pc with normal grub?"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by daweefolk on 2010-04-21
what would happen if i replace grub-pc with grub in my wubi install? (i need to install grub for one of my other linux installs and grub-pc doesn't allow me to do that)
Would i be able to uninstall wubi if I did that or would i have to reinstall grub-pc beforehand?
Hope this isn't too confusing

---

### Post by oldfred on 2010-04-21
I do not understand your statement about not being able to install another grub for another install. Wubi boots thru the windows boot, you can totally install another linux install, install its boot loader, and then when booting into windows choose windows or wubi. There also are ways with grub2 to directly mount the wubi root.disk so you can copy your data.

---

### Post by QLee on 2010-04-21
[QUOTE=daweefolk]what would happen if i replace grub-pc with grub in my wubi install? (i need to install grub for one of my other linux installs and grub-pc doesn't allow me to do that)
Would i be able to uninstall wubi if I did that or would i have to reinstall grub-pc beforehand?
Hope this isn't too confusing[/QUOTE]

I agree with poster oldfred. 

You did not give us much information to work with but, from your post I would guess you have a multiboot system and some of the other linux kernel distros are still at the version level of legacy grub. Maybe you are trying to install or re-install a distro like that. The good news is that the grub-pc you are currently using sould be able to handle discovering and booting that, you would not need to install legacy GRUB (unless you are chainloading to that partition and trying to fix a corrupted GRUB installed to that partition but that probably isn't what you are trying to do) After the install and optioning the other OS to not install GRUB, boot into the system you installed grub-pc from and run the command update-grub, it should discover the OS and rewrite the menu to include it, grub-pc is already on the MBR, point to the boot partition so no need to reinstall that. 

However, I'm just guessing, if you want better help, give more detail of how your system exists and exactly what you want to do. Your general question, is hard to answer specifically but my guess above might help you to think about it.

---

### Post by daweefolk on 2010-04-21
as far as i can tell wubi has a special grub called grub-pc and i can't do grub-install. i have slackware on my usb drive with no bootloader. i want to put grub on my usb. if i install the normal grub package in wubi would i get the error 15 when uninstalling wubi? or would it not matter?

---

### Post by oldfred on 2010-04-21
Typically with an external drive you install a boot loader in the MBR of the external that boots the external drives operating system. You can add chainboot to the internal if it does not automatically find it. If you set BIOS to boot the external first it will boot that and let you choose what to boot. If the external is not plugged in the BIOS goes to the internal drive and boots - in your case windows that gives you the choice for wubi or windows.

You just have to be sure to install the slackware boot loader to the external.

---

### Post by daweefolk on 2010-04-21
is there a way to install grub to my external's mbr from inside my wubi install?

---

### Post by QLee on 2010-04-21
With the new information you gave it looks you want to have a bootloader on each drive and use the bios (or whether it's plugged in or not) to choose which to boot from. 

Once again, I agree with oldfred he's given a reasonable path to achieve what it seems you want. If what he wrote is not what you want, please be more specific.

---

### Post by QLee on 2010-04-21
> **daweefolk said:**
> is there a way to install grub to my external's mbr from inside my wubi install?

Yes, but it would be grub-pc not the legacy grub , maybe tell us which version of slack?

---

