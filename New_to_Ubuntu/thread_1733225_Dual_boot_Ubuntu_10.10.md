---
title: "Dual boot Ubuntu 10.10"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by honey_bee on 2011-04-19
hi,
        I am using UBUNTU 9 with dual boot windows 7.I want to delete the old UBUNTU and install new UBUNTU 10.10 without disturbing my windows 7.Kindly guide me that how can I do it ?

thanks
honey

---

### Post by matt_symes on 2011-04-19
Hi

Download the 10.10 iso from here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download). 

Burn to a CD or create a bootable USB. Insert the CD/USB and reboot your PC ensuring the device is the first bootable item.

Choose the advanced manual partition install on the partition dialog and select your existing Ubuntu partition as the root partition. You do this by selecting the partition and hitting the edit key. Change the mount point to /.

Select the option to format the partition and install Ubuntu into it.

It's pretty easy now. :D

Kind regards

---

### Post by shahmish on 2011-04-19
I assume you have Ubuntu and Windows installed on separate partitions (Unless you're using Wubi). If so, format the Ubuntu partition from Windows. Alternatively, if you have any data stored on the Ubuntu partition that you don't want to lose, get the new Ubuntu on a LiveCd and install it form there. There should be an upgarde or "install instead of current operation system" option somewhere there. Both of these options should leave your Windows intact. Make sure Ubuntu is on a separate partition before you do anything though.

---

### Post by Mark Phelps on 2011-04-19
> **honey_bee said:**
> hi,
        I am using UBUNTU 9 with dual boot windows 7.I want to delete the old UBUNTU and install new UBUNTU 10.10 without disturbing my windows 7.Kindly guide me that how can I do it ?

thanks
honey

FIRST thing you need to do is confirm whether or not you're running Ubuntu in a separate partition or inside Windows.

One way to do that is to open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one). That will list out your partitions, and if they are all NTFS, then you are running a Wubi installation.

SECOND, before you do anything about upgrading or replacing Ubuntu, go into the Win 7 Backup feature and create a burn a Win7 Repair CD.  If your Win7 boot loader gets damaged, you will need this to restore Win7 boot capability.

---

