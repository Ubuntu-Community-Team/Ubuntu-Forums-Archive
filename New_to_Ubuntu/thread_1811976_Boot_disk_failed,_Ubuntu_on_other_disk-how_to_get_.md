---
title: "Boot disk failed, Ubuntu on other disk-how to get GRUB2 on new disk?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by emarkay on 2011-07-25
If Ubuntu (Lucid) is on sda, and WindowsXP and GRUB2 were on the now failed sdb, after I reinstall XPSP3 on the replacement sdb, how do I just get a new GRUB2 boot menu again?  I don't want to have to reinstall Ubuntu.  

Also, confirm for me - Ubuntu doesn't "need" an install - it just runs when called?  Thus, a  new boot menu will "find" the existing Ubuntu on sda and it will operate exactly as before?

---

### Post by oldfred on 2011-07-25
Not quite. The MBR has just enough code to know where on the hard drive to jump to, to continue booting whether Windows boot loader or grub2. Windows uses a boot flag (active partition) to know where to go. Grub has to know where the rest of grub is to jump to.

Do you have a BIOS that lets you choose boot drive. All newer BIOS that support SATA do, old IDE/PATA based BIOS may not and rely on jumpers on IDE drive or location on cable to know which drive to boot.

If you can set in BIOS which to boot, I would install grub2's boot loader to the Ubuntu drive and boot that in BIOS. 

IF windows is sdb not sda, It may install its boot loader to sda, if BIOS is set to boot sda. So you may have to reinstall either or both depending on which drive is the boot drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by emarkay on 2011-07-25
CORRECTION: the failed boot drive is sda.  Drive sdb has Ubuntu on it.

"Do you have a BIOS that lets you choose boot drive."

No, it's an old MSI board, and anyway, I am confused on why this matters; the boot drive failed, and I am replacing it with a new boot drive.

I want to reinstall a clean XPSP3 anyway, so let's presume it's already there on the new boot drive. 

Regarding the linked tutorial featuring "sudo grub-install...", will it autoconfigure (find the Ubuntu) automatically. If so, confirm that that's all I need to do to be able to boot into my existing Ubuntu on sdb once I have a booting XPSP3 on the new sda? 
Thanks!

---

### Post by oldfred on 2011-07-25
No it does not find Ubuntu automatically. You tell it where it is with the first command that mount the install.

There are some tools that may find install and let you boot it. Then you can just install grub to the MBR of sda.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Once booted into Ubuntu you can just run this to reinstall grub2's boot loader. Instructions below are for installing to same drive, but you can install to either or both drives if you want.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by emarkay on 2011-07-25
> **oldfred said:**
> No it does not find Ubuntu automatically. You tell it where it is with the first command that mount the install.

Confused - I am not installing Ubuntu - only Windows and GRUB2

Also, how can I repair a boot that is not there - or are you saying that the "repair" programs can also be used to create the GRUB2 boot?

Also, I won't be able to be booting into Ubuntu at that time, unless you mean from a LiveCD, to run the commands listed to generate the Grub2 menus.

See why I am confused?

---

### Post by oldfred on 2011-07-25
Yes you have to use Ubuntu's liveCD to reinstall grub2's boot loader to the windows MBR if that is the only one you can boot from.  Or you can use Supergrub which is its own liveCD.

You are not reinstalling grub normally.

---

### Post by amjjawad on 2011-07-26
> **oldfred said:**
> yes you have to use ubuntu's livecd to reinstall grub2's boot loader to the windows mbr if that is the only one you can boot from.  

+1

---

