---
title: "How to save Windows bootloader before installing UBUNTU?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by EMStudent on 2010-04-30
Situation: I've previously tried UBUNTU through WUBI. Now I'm ready to install UBUNTU 10.04 LTS in a separate partition on harddisk. I know that GRUB bootlader will be installed and it should let me boot both Windows Visa and UBUNTU. Windows is already installed, but I don't have the installion disk (it was preinstalled).
 
Request: **Before installing UBUNTU, I'd like to save Windows bootloader, so that if needed I can override GRUB, and return the machine to its current state.** As far as I understand it can be done entirery under Linux. I plan to run UBUNTU from LIVE CD, then save the Windows bootloader in a file. How exactly should I proceed? There should be one "dd" command to save the bootloder, and another one to put it back, right? What exactly are those commands? Thanks!

---

### Post by Jon Monreal on 2010-04-30
What version of Windows are you running? If you have a Windows installation CD of the same version, it would be trivial to "repair" your MBR so that you could boot back into Windows again, so there's no need to back it up.

At any rate, even if Windows doesn't show up in Grub, an entry could be added.

---

### Post by EMStudent on 2010-04-30
[QUOTE=Jon Monreal]What version of Windows are you running?[/QUOTE]
Windows Vista SP2
 
[QUOTE=Jon Monreal]If you have a Windows installation CD of the same version, it would be trivial to "repair" your MBR[/QUOTE]
I don't have the Windows installation CD. The Vista came preinstalled. Besides, the Windows bootloader is already present on harddrive, and it works fine.
 
Is it sufficient to save only Master Boot Record (MBR),
like:
> dd if=/dev/hda of=MBR.bin bs=446 count=1
and later restore it by 
> dd if=MBR.bin of=/dev/hda bs=446 count=1
or there is something more to deal with?

---

### Post by Jon Monreal on 2010-04-30
No, that should be fine. Just so you know, changing it to bs=512 would save your current partition table as well, but this would not have good results should you later modify partitions, and is unnecessary. What you're doing now will save what needs to be saved.

If you're concerned about data loss, perhaps you should backup Windows (which is best practice really, no matter what you're doing with your computer).

---

