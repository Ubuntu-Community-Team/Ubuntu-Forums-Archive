---
title: "install on external drive hangs at 22%"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by geek_overlord on 2009-02-07
Hi. I'm attempting to install Ubuntu 8.10 on my sata 2 external drive. The drive already has Windows XP on it however I want to install Ubuntu on the whole thing. I go thru the setup wizard where it checks the time zone, language, comp name, partition size etc. It gives me a choice between internal or external and allows me to select the whole drive. When the machine reboots it goes right back to Windows. Arrrgh what gives? Does anyone have an idea what happened? Thanks in advance for the help.

---

### Post by drs305 on 2009-02-07
The 22% mark is where ubuntu starts to copy files to the new partition and this step is probably failing for some reason. You might try booting to the LiveCD and formatting/setting the partitions the way you want them before you start the installation. You should also make sure your system 'sees' the SATA drive ( *sudo fdisk -l )* although if you haven't received an error before it starts to copy the files that shouldn't be the case.

You can use *gparted* from the System, Administration, Partition Editor menu. Make sure there is at least a system partition ( / ) formatted to ext3 and a swap partition formatted as 'swap'. You should decide before installation if you want a separate /home partition.

Once you have the partitions set the way you want, try installing again and select "manual" when you get to the partition setup.

---

