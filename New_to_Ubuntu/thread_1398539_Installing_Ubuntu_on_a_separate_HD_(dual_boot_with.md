---
title: "Installing Ubuntu on a separate HD (dual boot with XP)"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Nermi on 2010-02-04
My computer:
Pentium Dual-Core CPU
E6300 @ 2.80GHz
2GB RAM
XP SP3
2 X 500GB SATA HDD's

I would like to install Ubuntu on this computer, on a separate hard drive, and create a dual boot Linux and XP.
I am not comfortable with installing Ubuntu on the same drive with Windows; I am afraid I could screw up my XP installation.

I already own another 500GB HDD but this one is IDE. I don't know if that matters? I would like to install Ubuntu on this one. The other two are SATA. The second one is used only to mirror the first one and protect me from a single drive failure; that one is not bootable and it doesn't show in Windows Explorer. 

My question is: when the installation starts, how will I know if I am installing Ubuntu on this third (IDE) drive, and not on the first HD with Windows on it? I am afraid I could accidentally overwrite my XP installation...

Second, do I need to make this Linux HD bootable? And what my boot sequence should be. I don't really understand how GRUB works when you have Ubuntu on a separate drive. 

Are there any known conflicts with XP that I might run into?

Thanks.

---

### Post by switch10 on 2010-02-04
The danger is just the same installing to a different disk, or a different partition on the same disk.  The people that mess up, mess up because they don't know what partition Windows is on.  It works the same with multiple disks.  My suggestion would be to run the Ubuntu live cd, and choose the option "dont make changes to my computer" or whatever the default option is and open up a terminal (applications>accessories>terminal) and type:

```
sudo fdisk -l
```

This will list all of your hard drives and the partitions on each drive.  Take a long look at this write down which partitions the NTFS file systems are on.  (i.e. /dev/sda1 dev/sda2 or something similar) Do not over write these partitions and you will be fine.  

When you choose to install it will ask you if you want to use the entire disk, or some other option.  click on the "manual" option near the bottom.  What you will want to do is resize your NTFS partition to make room for your EXT partition.

that 500 GB IDE drive might be kind of annoying to get working.  I am not positive, but I think there would be problems getting it to boot unless you keep switching it in your boot order in your BIOS.  it would have to be setup as a "Master" drive to boot.  SATA doesn't have those jumpers on the drive, you set up which drive boots in BIOS.  

I think your best option would be to just resize your NTFS filesystem, and make an EXT3 or EXT4 file system.  Just make sure you know what you are doing when you choose which partition you are installing ubuntu to, and you will be fine.  It will warn you before you make changes as well.

Good Luck

Dave

---

### Post by Nermi on 2010-02-05
Thank you for your suggestion not to add the IDE drive into this computer configuration and try to make it dual boot; I have done lot of research online and found out that you might be just right. 

However, I understand that SATA doesn't have jumpers, but what happens if I install it as the Secondary Master? 

I am so confused here...

---

