---
title: "Installing ubuntu 10 on laptops, grub"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by SG12010 on 2010-10-09
Hi

Installing Ubuntu 10 on laptops that the grub dose not load, also when the laptop tries to boot it gives a error message that the hard drive can not be found or mentions un used block.

This only happens with laptops, the boot sector dose not load, can this be fixed with resizing of the hard drive.


Thanks SG

---

### Post by oldfred on 2010-10-09
Some BIOS have a block on writing into the MBR, check your BIOS settings.

The MBR is not a partition just the beginning of the hard drive (before first partition) that the BIOS jumps to to continue booting, changing partitions around will not change MBR.

---

### Post by anewguy on 2010-10-10
+1 - and remember you will probably need to reinstall after doing so.  Since you don't have grub you obviously can't boot ubuntu now anyway.  Going through the installation process again after being sure the BIOS is not blocking access to the MBR will allow grub to install to the MBR.

Dave ;)

---

### Post by SG12010 on 2010-10-12
I have tried those, the Toshiba Satellite laptop dose this and the MSI U160, the only way I can get around it is by loading the DVD Ubuntu, the CD version just dose not work, but will work on Desktops.

Changing the Bios dose not make any difference.


Is it deliberate by the Manufactures not to allow Ubuntu to Load on Laptops?

I know some Laptops will allow Ubuntu CD versions to work.


Thanks SG1

---

### Post by SG12010 on 2010-10-14
Unsolved

---

