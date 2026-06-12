---
title: "difficulties involving ubuntu and replacing HDD's."
date: 2010-07-10
forum: New to Ubuntu
---

### Post by Viremaster on 2010-07-10
I have using Ubuntu for a while on my desktop's slave drive (the master running XP). I've been trying to upgrade my master drive, but have run into many complications, one of which being I can't boot ubuntu without the old HDD. how do I set it so the OS can run independent of the other disk drive?

---

### Post by aeiah on 2010-07-10
either the hdd that you've removed has the 'boot' flag (check it out in gparted) or grub is installed on this removed hdd, or both.

---

### Post by Viremaster on 2010-07-10
I checked on gparted and the other HDD did have the boot flag. So, do I just put the same flag on the Ubuntu hard drive?

---

### Post by oldfred on 2010-07-10
Windows has to have a boot flag on a primary partition. Grub does not use a boot flag, but some BIOS require a boot flag on a primary partition.

It is more likely that grub is not installed to the Ubuntu drive if it was slave before. The boot loader has to be installed to the primary master and BIOS then jumps to the MBR of the primary master to boot.

Install grub to the Ubuntu drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you can still boot it you can install directly from inside the working Ubuntu. Do you have grub legacy or grub2. Instructions to install grub vary.

---

### Post by Viremaster on 2010-07-10
I am still able to run Ubuntu from the XP master/Ubuntu slave config. I have already installed grub onto the slave drive, but grub says that boot/grub/stage1 cannot be found. Now, which of these do I need to install it in?

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9556    76754944   83  Linux
/dev/sdb2            9556        9730     1393665    5  Extended
/dev/sdb5            9556        9730     1393664   82  Linux swap / Solaris

---

### Post by oldfred on 2010-07-10
Grub consists of several parts. The boot part is installed to the MBR to let you boot and that links the the rest of grub installed in the /boot/grub folder of your linux install in sdb1. If you are booting you already have grub installed. Then you just need to install the bootloader into the MBR of drive sdb. Grub is not normally installed to partitions PBR or boot sectors.

---

### Post by Viremaster on 2010-07-11
> **oldfred said:**
> Grub consists of several parts. The boot part is installed to the MBR to let you boot and that links the the rest of grub installed in the /boot/grub folder of your linux install in sdb1. If you are booting you already have grub installed. Then you just need to install the bootloader into the MBR of drive sdb. Grub is not normally installed to partitions PBR or boot sectors.

So, and I hate to sound slow, how exactly do I put the bootloader on the MBR?

---

### Post by oldfred on 2010-07-11
You never said which version of grub or grub2. The link in #4 has instructions for installing either from liveCD, just do not mix them up.

If you can boot into your Ubuntu then this will install to sdb if that is your external drive.

sudo grub-install /dev/sdb
sudo update-grub

---

### Post by Viremaster on 2010-07-11
I have Grub .97-29ubuntu60.
Well, I installed the boot loader onto the drive like you said and now I can boot ubuntu without the older disk drive. many thanks.

---

