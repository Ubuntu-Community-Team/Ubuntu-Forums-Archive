---
title: "Replace Windows 7 with Kubuntu 11.04 in Windows 7/Ubuntu 10.10 dual boot"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by veroslav on 2011-05-07
Hi all,

I am currently running a dual boot between Windows 7 and Ubuntu 10.10, and as I am not booting the Windows partition at all,
I would like to replace it with a fresh install of Kubuntu 11.04. Have a look at the attached image for my current set-up.

/dev/sda1 (boot) and /dev/sda2 is the Windows 7 installation, /dev/sda4 partition contains the Ubuntu 10.10 logical partition (/dev/sda5 for "root" and /dev/sda6 for swap). 
/dev/sda3 is utilized by the HP recovery software.

Now, I would like to double-check with you guys, that I have understood everything correctly before getting to work:

1. I am thinking of installing Kubuntu on /dev/sda2 (main Windows 7 installation), is this ok? Do I need to delete or
only format this partition to ext4 from within GParted before installing Kubuntu?

2. After formatting, the next step would be to create a new extended partition on /dev/sda2, containing one logical partition
for the Kubuntu installation, and another logical partition for the swap (ca 2690 MiB). Do I really need to create a new swap
partition or is it possible to let Kubuntu use the Ubuntu's swap (/dev/sda6)?

3. Boot from the Kubuntu Live CD and choose to "Manually specify partitions" from within the installer. Here, I should change
the mount point for the "root" logical partition of /dev/sda2 to "/" and also select to format the partition.

4. The final and most important question: Which device should I specify for the boot loader installation? Currently, this is
/dev/sda, which is the hard drive containing all of the partitions. Should I select it again? Will GRUB be updated
automatically with the new partition information, so that I can choose between Kubuntu and Ubuntu on the boot?
Anything else I should take care of or watch out for?

5. This might be Kubuntu related but I might as well post it here: While I was running Kubuntu from Live CD, I noticed that there were
no proprietary drivers for my video card (nVidia GTX 260). However, the proprietary drivers are found in Ubuntu 10.10 and I have
them enabled. Is this only an issue when running from the Kubuntu Live CD and can I expect the proprietary drivers to be found
after the installation, or should I be worried?

If you could shed some light on the points above, I would be very thankful as I am quite eager to remove Windows 7 and start
exploring Kubuntu.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by mikewhatever on 2011-05-07
1. Formatting is enough.

2.No. Formatting will create the partition. Furthermore, /dev/sda2 is outside the extended partition, so if formatted, it will remain a primary partition which will do just fine. One swap partition is enough, don't create another one.

3. Correct.

4. /dev/sda should work. Grub should be updated and offer both Ubuntu and Kubuntu at boot.

5. All proprietary drivers should be in the so called restricted repository. To get the Nvidia driver, install the 'nvidia-current' package.

Do make sure you have a way to recover the W7 installation in case you ever need to.

---

### Post by veroslav on 2011-05-07
Hi mikewhatever,

thank you for your fast reply. It does make me feel more comfortable ahead of the installation.

So, just to confirm, it will be possible for Kubuntu being installed on /dev/sda2/ to use the swap on /dev/sda6 and thus I dont need to create another swap on /dev/sda2?

I appologize for my lacking knowledge, I am just trying to understand how Kubuntu will know about the swap at /dev/sda6.

I really appreciate your answers, thank you again.

/Veroslav

---

### Post by mikewhatever on 2011-05-07
Yes to all. The installer should autodetect and use the existing swap partition.

---

### Post by veroslav on 2011-05-07
Thanks again, I will have a go later today and I will come back with the results. Hopefully, everything will be fine :)

/Veroslav

---

### Post by oldfred on 2011-05-07
+1 on mikewhatever comments.

You only can have one extended partition. So leaving it as sda2 is fine. If you are deleting windows the the 100MB sda1 is worthless. It is just a boot/recovery for the main partition.

You may just want to to a complete backup of your windows. Your windows restore partition lets you create restore DVDs but those normally erase entire drive and restore to as purchased. You would have to do all updates & reinstall everything.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Normally whichever system you install last will install its grub2 boot loader into the MBR and its grub menu will be the one you see with its entries at the top. A sudo update-grub finds all other systems and lets you boot them, but if you are often booting the other one then new kernels in that one require you to rerun the update-grub in the first one to find the new kernels. A run of sudo update-grub does not update both systems. There are some work arounds to just boot a partition and then you can boot just the newest kernel, if you want.

---

### Post by veroslav on 2011-05-07
Thank you for your reply oldfred.

Your reply led me to a couple of new questions:

- When you say that I should "leave the extended partition as it is", you meant to say /dev/sda4, right? Because that is the extended partition I created before and I will be installing Kubuntu on /dev/sda2.

- I agree that having such a small and useless partition as /dev/sda1 is unnecessary, is there a simple way of removing it or somehow merging it with /dev/sda2 in order to reclaim the space and possibly open up for making an additional primary partition instead?

Thanks.

/Veroslav

---

### Post by veroslav on 2011-05-07
Just to add, I have burned the recovery DVD:s for Windows 7 so I think I should be fine in case I need to re-install Windows. Thank you for suggesting that.

I have also made a back-up of all data I have in my home directory in Ubuntu.

/Veroslav

---

### Post by oldfred on 2011-05-07
It is good to have make the recovery DVDs, but if you every have to use them it will totally erase drive. May only be useful if you later decide to sell computer.

You should be able to just delete sda1 with gparted on the LiveCD. You could move sda2 left to include the 100MB, but 100MB is not much. I might format sda2 before moving it left as it will try to move all the data left and that will take hours. If it has no data it should be quick. If you ever want another primary you could then add a new sda1. It will not be in order on the drive but that is not a requirement (just  may look strange).

The extended partition is sda4 and it will not change unless you also want to make changes to it also.

---

### Post by veroslav on 2011-05-07
I have one final question: when installing Kubuntu on ext4-formatted /dev/sda2 partition, how will the installer know to install to this partition and NOT to /dev/sda5 partition, which is where my current Ubuntu installation is? I mean, they are both ext4-formatted.

My guess is that by checking the "format" option for the /dev/sda2 before installing is a hint to the installer where Kubuntu should be installed, but I am not sure.

/Veroslav

---

### Post by mikewhatever on 2011-05-07
The installer will not know, but you are going to tell it, by assigning the / mount point to the appropriate partition.

---

### Post by oldfred on 2011-05-07
You have to use manual install to select partitions yourself. I think they renamed it.
With Natty Manual partitioning is Something Else

Those of use who want control over our computers only partition in advance and use the manual install. Auto install goes off and shrinks something if it can and create new partitions.

If you think you may be using both installs, you may want a separate /data partition. You should not share /home as too many settings may be different but all your data is just data and can be in a common partition.

---

