---
title: "Compilation of driver for DWL-g122 C1"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by ulriks on 2006-10-05
Hello All,

I am trying to compile the driver for the DWL-g122 C1 under a fresh install of Kubuntu on an old Compaq Presarion 1200.

Kubuntu was installed directly from the CD as delivered by Canonical. The driver was downloaded from [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm), and changes were made to the [FONT="Courier New"]rtmp_def.h[/FONT] file as suggested in the thread [http://ubuntuforums.org/archive/index.php/t-190422.html](http://ubuntuforums.org/archive/index.php/t-190422.html).

When runing [FONT="Courier New"]sudo make all[/FONT], I get the following error:

[FONT="Courier New"]make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/ulriks/download/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make: *** [all] Error 2[/FONT]

What do I need in order to build the driver?

I have installed and unpacked the kernel source, and made a symbolic link from [FONT="Courier New"]/lib/modules/2.6.15-23-386/build[/FONT] to where the source directory is in [FONT="Courier New"]/usr/src/[/FONT]

Thnaks in advance
Ulrik

---

