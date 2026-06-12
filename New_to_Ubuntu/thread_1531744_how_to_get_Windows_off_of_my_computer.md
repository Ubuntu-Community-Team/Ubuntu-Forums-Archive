---
title: "how to get Windows off of my computer"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-07-15
I have a doule-boot with Ubuntu and Windows XP I was wondering how to get rid of XP. Do I have to run the install disk to reformat it.

---

### Post by Anxious Nut on 2010-07-15
You dont have to reformat the whole thing! all you need it to delete the windows partition! Which can be done by booting off the live installation cd, then go to system --> administration --> partition editor. Once you're there make sure it's your HDD and right click on it and choose unmount!

Now is the tricky part, look for an NTFS partition and right click on THE PARTITION (not the whole HDD) and choose delete! After making sure everything is alright, click the apply button on the top! Of course you can either create another partition on the HDD, which i suggest, or you can enlarge the main partition space WHICH I DONT SUGGEST! has a higher possibility of data loss!

After finished you'll need to boot into your Ubuntu and run from the command line (terminal) the command: ```
sudo update-grub
``` to update you'r boot loader OSs entries!

---

### Post by cj.surrusco on 2010-07-15
> **Chad Olson said:**
> I have a doule-boot with Ubuntu and Windows XP I was wondering how to get rid of XP. Do I have to run the install disk to reformat it.

If you are using the grub bootloader, you can just use GParted to delete your Windows partition. However, If you want to resize your Ubuntu partition fill the free space, you will need to boot into a GParted live CD or just a Ubuntu live CD (and use GParted on that).

You can use other tools to do the partitioning, but I recommend GParted.

---

### Post by pastalavista on 2010-07-15
Install gparted (partition editor) from the software center and just reformat the Windows partition to Linux (ext4 or ext3) filesystem (you'll need to unmount it first) and you can make it part of Ubuntu. This will erase all the data on the partition, so back-up whatever you want to keep.

edit: also run 'sudo update-grub' afterwards

---

### Post by Anxious Nut on 2010-07-15
> **pastalavista said:**
> Install gparted (partition editor) from the software center and just reformat the Windows partition to Linux (ext4 or ext3) filesystem (you'll need to unmount it first) and you can make it part of Ubuntu. This will erase all the data on the partition, so back-up whatever you want to keep.

edit: also run 'sudo update-grub' afterwards

i think editing partitions on the same hard disk drive which ubuntu is running on is not possible! So I think he'll need to do that from a liveCD which already has gparted, no need to install!

---

### Post by pastalavista on 2010-07-15
> **Anxious Nut said:**
> i think editing partitions on the same hard disk drive which ubuntu is running on is not possible! So I think he'll need to do that from a liveCD which already has gparted, no need to install!It is possible as long as no Ubuntu partitions are changed. The reformatted partition will just have to stay the same size and remain a separate partition.

---

### Post by Anxious Nut on 2010-07-15
actually i dont think you'll be able to unmount the volume in the first place!! You cant edit the HDD without unmounting it! and unmounting the HDD which ubuntu is running on is something wrong, it wont be able to load anything then! Am i getting it wrong?

---

### Post by pastalavista on 2010-07-15
You don't unmount the HDD, you unmount the Windows partition only.

UNLESS (the OP didn't say) you are dual booting via a Wubi install.

---

### Post by Chad Olson on 2010-07-15
xp was on first I installed ubuntu with a live cd. I was just playing with ubuntu If I knew how much I would like ubuntu I would have wiped the hard drive.

---

### Post by pastalavista on 2010-07-15
> **Chad Olson said:**
> xp was on first I installed ubuntu with a live cd. I was just playing with ubuntu If I knew how much I would like ubuntu I would have wiped the hard drive.
Actually, since you're running Lucid, you don't even need to install gparted. You can do the job with System-> Administration-> Disk Utility. 
As long as you can see the Windows partition and unmount it, you can reformat it however you like.

Did you install Ubuntu with Windows running the CD or did you boot from the disk and partition the drive? Because all this is pointless if you installed inside Windows with wubi.

---

