---
title: "plymouth themes comes up with brokem pixles"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by frozenflames on 2010-05-29
so i used this commnad to change the Plymouth theme

msi@msi-desktop:~$ sudo update-alternatives --config default.plymouth
[sudo] password for msi: 
There are 5 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                               Priority   Status
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth                       10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                             10        manual mode
  3            /lib/plymouth/themes/solar/solar.plymouth                           10        manual mode
  4            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth               100       manual mode
  5            /lib/plymouth/themes/ubuntustudio-logo/ubuntustudio-logo.plymouth   150       manual mode

Press enter to keep the current choice
[*], or type selection number: 4
update-alternatives: using /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in manual mode.
msi@msi-desktop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
till this point no error 
when system reboots and plymouth theme comes up with broken pixles every where 
any help using ubuntu lucid

---

### Post by frozenflames on 2010-05-30
any help guys the screen goes black with pixels scattered every where:confused:

---

