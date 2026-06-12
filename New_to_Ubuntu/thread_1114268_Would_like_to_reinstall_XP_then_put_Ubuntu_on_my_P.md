---
title: "Would like to reinstall XP then put Ubuntu on my PC for Dual Boot a few questions"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by arce on 2009-04-02
I currently have my HD all Ubuntu. Due to some conflicts I would like to have both OS's on my HD. I already tried Virtual Box but it also has it's limits for my needs.

I originally had XP on the machine and messed up the Ubuntu install and it wiped out XP.

Ok now the question. I want to wipe out Ubuntu. Then reinstall XP and then install Ubuntu.

Can I just boot to my XP install CD and it will format the HD regardless of Ubuntu?

After XP is fully setup I will then install Ubuntu.

---

### Post by wolfen69 on 2009-04-02
> **arce said:**
> I already tried Virtual Box but it also has it's limits for my needs.


what limits are those? i have been able to do anything in virtualbox.

---

### Post by taurus on 2009-04-02
The best way is to boot your machine with Ubuntu LiveCD.  Then, run gparted (System -> Administration -> Partition Editor) and delete all the partitions.  You need to unmount the swap partition first though.  Highlight the swap partition and click the right button then swapoff.  

Once you've deleted all the partitions, create two new partitions, /dev/sda1 & /dev/sda2, and format the first one as ntfs filesystem.  You can format the second partition as ext3.  Now, boot your windows disc and install it on the first partition, leaving the second partition so you can install Ubuntu on it later.

---

### Post by kanikilu on 2009-04-02
> **arce said:**
> Can I just boot to my XP install CD and it will format the HD regardless of Ubuntu? Yes. When you get to that part of the installation, just delete any existing partitions (assuming this is what you want to do), and let XP install in the whole disk.

Alternatively, and I think more efficiently, you could use the Ubuntu Live CD (or a gparted live CD) and use gparted to remove all existing partitions, then just create one NTFS partition for Windows, and your Linux and Swap partitions. This would method would probably save you some time during the Ubuntu install, since it wouldn't need to shrink the XP installation.

// Edit - too slow, see above ^ ;)

---

### Post by halitech on 2009-04-02
> **arce said:**
> I currently have my HD all Ubuntu. Due to some conflicts I would like to have both OS's on my HD. I already tried Virtual Box but it also has it's limits for my needs.

I originally had XP on the machine and messed up the Ubuntu install and it wiped out XP.

Ok now the question. I want to wipe out Ubuntu. Then reinstall XP and then install Ubuntu.

Can I just boot to my XP install CD and it will format the HD regardless of Ubuntu?

After XP is fully setup I will then install Ubuntu.

Yes, you may need to delete the partitions that were created in order for XP to install but it will work. Make sure since you are planning on dual-booting that you create an actual partition for windows instead of using the entire disk.

---

### Post by arce on 2009-04-04
Limits were I couldn't get USB to work. I couldn't print to a networked printer. I also had the ability to use only 1 of 4 DVD burners.

---

### Post by rock_fan_09 on 2009-04-04
i had the same problem with my laptop - YES if you use your XP system restore disks it will return the computer to factory specs. After XP install just run ubuntu and set up your partition sizes when asked. You will be dual booting between them in a few hours after you start.

---

