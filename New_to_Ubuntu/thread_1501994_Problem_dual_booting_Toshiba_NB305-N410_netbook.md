---
title: "Problem dual booting Toshiba NB305-N410 netbook"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by gnometorule on 2010-06-04
After following the usual instructions to create a simple dual boot (no shared drives), e.g., as in [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu) (partitiion from within Windows; allocate to maximal available continguous space when using live cd after for install) grub lets me load Windows 7, but when trying ubuntu 10.04, it leads to an error and I land in a simple shell that I am not familiar with. Probably the ubuntu recovery mode. Here is what I hear back:
 
```

"Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/a7a52a79-58d7-4115-bf3b-10eed8e359e2 does not exist. Dropping to a shell!" 
(Shell name is "(initramfs)")

```
 
Ideas? Kinda stuck here badly. :)
 
-----
 
My data:
 
Windows Starter of above Toshiba netbook
Ubuntu 10.04 from USB stick (burnt Live CD; then burnt ISO onto stick from within Ubuntu under Live CD)
Installed desktop version (as I like the look better), not netbook version. (which shouldn't be a problem, should it?)
I installed when the option is first popping up; not after first letting the Live CD boot ubuntu up, then hitting install from within.

---

### Post by gnometorule on 2010-06-05
bump

---

### Post by gnometorule on 2010-06-05
Ok, so all it takes, it seems, is to...
 
set in BIOS, 
under advanced, 
Sata/Controller Mode to 'compatibility'.

---

### Post by astigfighter on 2010-06-05
hey... did it worked? because i am worrying if i install ubuntu 10.04 desktop version in my acer aspire one netbook... is there any problem if i dual boot ubuntu with the windows 7 starter edition? tnx

---

### Post by naveen chakravarthy on 2010-09-22
Hi all,
Thanks to this community website, managed to solve the dul boot problem.

Have a new Toshiba MB 305, with windows 7 starter preloaded. After having tried over two days to installa a dual boot with UBUNTU finally suceeded....

Answer lies in  BISO modifications...Install UBUNTU using the recommended procedure.

1.  When u want to boot up Ubuntu 10.04, enter the BIOS and under SATA choose compatability.
2. When u want to boot up windows, in the same option choose ASII.

Pl note that if u do not make this change and boot windows in the compatibility mode, ull be taken thro a very long loop wherein windows starter will request to repair itself. Avoid this by re booting and making the changes in the BIOS.

Hope this helps somebody...
UBUNTU Rocks :)

---

### Post by mikeody on 2010-12-28
EUPHORIA HERE !!!!!
Problem solved thanks to a thread I found by chance on here - someone with the same issue.
It is nothing to do with UBUNTU.
Toshiba BIOS sets the hard drive controller to AHCI [as opposed to Compatability].
Change the BIOS for the controller to Compatability and the Remix installs at 10 times the speed and boots up in a reasonable time. Happiness !
A sincere thanks to everyone who had a go at the solution - a great forum and a great bunch of guys.
Thanks again.

---

