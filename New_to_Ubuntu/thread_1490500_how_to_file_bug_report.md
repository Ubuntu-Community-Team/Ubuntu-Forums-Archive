---
title: "how to file bug report"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-05-22
the sticky and every other documentation i read assume that i have a working system. What do i do when i can't even reach the livecd environment for installation?

---

### Post by ubudog on 2010-05-22
If you can't even reach the LiveCD, it is not an Ubuntu bug, your computer is messed up.  Will your computer not start?

---

### Post by jfreak_ on 2010-05-22
phew, finally by inserting the nomodtest option into the boot option got it to install. so its not a bug after all. anyway now that i have installed, the installed version is not booting, i guess nomodtest will have to be inserted in the boot as well . how?

---

### Post by oldfred on 2010-05-22
I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by jfreak_ on 2010-05-22
i don't see the bootloader , it goes directly to the ubuntu splash and gets stuck

---

### Post by ubudog on 2010-05-22
You may have to press ESC right before Ubuntu starts. (not at the bios screen)

---

### Post by oldfred on 2010-05-22
If it is old grub it is escape, if grub2 it is shift from the BIOS until menu comes up. If it only sees one operating system it skips the menu.

---

