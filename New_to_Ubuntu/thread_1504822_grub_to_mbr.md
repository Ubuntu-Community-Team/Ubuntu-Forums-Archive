---
title: "grub to mbr"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by bj218 on 2010-06-08
How do I move grub to mbr? Also how do I check that it did move to the mbr?

---

### Post by oldfred on 2010-06-08
It is different for grub legacy and for grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

I use this to know where everything related to booting is at. It tells what is installed in every MBR. Also makes a good history of how system was configured, so I save a copy before doing major changes.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by bj218 on 2010-06-11
> **oldfred said:**
> It is different for grub legacy and for grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

I use this to know where everything related to booting is at. It tells what is installed in every MBR. Also makes a good history of how system was configured, so I save a copy before doing major changes.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

It looks to me like everything is OK ie grub & mbr are in the right place!! But please let me know  what you think. Also thank you for
giving me this help I learned a bit more about linux.

---

### Post by oldfred on 2010-06-11
It is ok, but I prefer to have the system install and the MBR on the same drive. You have a windows install in sda1 and a windows boot loader in the MBR of sdb. Ubuntu is in sdb1 but boots from sda. If one drive fails you cannot boot either.

You can boot into Ubuntu and reinstall grub from there and install a windows boot loader into sda. You then have to change BIOS to boot sdb - the 250GB drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
and to know grub will reinstall to sdb:
sudo dpkg-reconfigure grub-pc

Install generic windows style boot loader, It may give errors about the rest of lilo not installed but we just want the MBR part, so ignore any errors -and  in software sources have universe enabled:
sudo  apt-get install lilo
sudo lilo -M /dev/sda mbr
per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

You can test that windows boots by using your one time boot key often f12 but see what BIOS boot screen says.

 If everything is then installed change BIOS to boot sdb.

---

### Post by bj218 on 2010-06-14
> **oldfred said:**
> It is ok, but I prefer to have the system install and the MBR on the same drive. You have a windows install in sda1 and a windows boot loader in the MBR of sdb. Ubuntu is in sdb1 but boots from sda. If one drive fails you cannot boot either.

You can boot into Ubuntu and reinstall grub from there and install a windows boot loader into sda. You then have to change BIOS to boot sdb - the 250GB drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
and to know grub will reinstall to sdb:
sudo dpkg-reconfigure grub-pc

Install generic windows style boot loader, It may give errors about the rest of lilo not installed but we just want the MBR part, so ignore any errors -and  in software sources have universe enabled:
sudo  apt-get install lilo
sudo lilo -M /dev/sda mbr
per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

You can test that windows boots by using your one time boot key often f12 but see what BIOS boot screen says.

 If everything is then installed change BIOS to boot sdb.

I followed you'r inst & boy did improve my boot time THANK YOU. I ran another boot info script would ck it & let me know what you think!!

---

### Post by oldfred on 2010-06-14
Boot script looks fine. What really counts is that it boots. Good Luck

---

