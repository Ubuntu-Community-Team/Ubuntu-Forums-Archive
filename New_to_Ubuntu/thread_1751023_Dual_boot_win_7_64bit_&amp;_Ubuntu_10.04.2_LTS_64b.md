---
title: "Dual boot win 7 64bit &amp; Ubuntu 10.04.2 LTS 64bit"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by 645dood on 2011-05-06
Hi, I have dual booted both of the OS's, Win 7 first, when I installed Ubuntu and was prompted to restart I did so but to my surprise there is no dual boot screen, the PC goes directly to Win 7......please help...Thank you, 645dood.

---

### Post by adit on 2011-05-06
First verify that you have installed ubuntu in a separate partition.
Boot from ubuntu live cd.  In Places menu find out the partition where ubuntu is installed.  Mount that partition and see if you have similar directories (bin,boot,etc,lib,...).  If everything is there then installing grub is sufficient.

---

### Post by Jonny87 on 2011-05-06
My guess is that you possibly have more than one hard drive and you installed grub to a hard drive different than the one with Win7, but the Win7 hard drive is set to boot first. If so change them round in the bios boot priority.

Other wise pressing shift during the boot. You need to press right at the start of the grub booting so I'd just keep taping it while the system is booting up.

---

### Post by 645dood on 2011-05-06
Hi Adit, I installed Ubuntu along side of win 7 during the installation. I have done this before without a problem, how to I get grub to work, Thanks Again, Alex

---

### Post by 645dood on 2011-05-06
Hi, Tried to reinstall the live cd but right at the end I received an error: Could not install fatal error installing GRUB...Please help..Thanks.

---

### Post by adit on 2011-05-06
All the following steps should be done from a live cd.
Download _[boot_info_script]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/boot_info_script055.sh/download")_
Change to the directory where you downloaded the file "boot_info_script055.sh".
Run the following command:```

sudo bash boot_info_script055.sh
```
This will create RESULTS.txt in the same directory.  Copy and paste the contents of RESULTS.txt.  This result has several pages.  So remember to use code tags when pasting the contents of this file.

---

