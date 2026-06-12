---
title: "expand partition unallocated space 10.10"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Rhodee on 2011-04-28
Thanks for reading,

I dual boot x64 AMD (win 7/ 10.10) and decided I want to add space to the 10.10 partition. 

After much reading in the forum, I created unallocated space from win7 partition. Now how do I add the unallocated space to the sda4?

I have gparted installed on my machine and just want a tut on how to add the unallocated space without destroying my setup. 

Screen shots of partition table and gparted attached!

Thanks so much!

---

### Post by -kg- on 2011-04-28
Hello;

By the screenshot of your partitions, you have three Primary partitions (sda1-sda3) which are used for Windows 7, and then sda5, which is a Logical partition containing your Ubuntu installation, with sda6 being your swap partition.

sda4 is what is called an Extended partition.  This type of partition enables you to exceed the "4 Primary partition" limit, and the partitions created within the Extended partition are called Logical partitions.  You will need to expand sda4 into the free space created by shrinking your Windows partition and then expand sda5 into that space.

I suggest you boot into a Live CD or USB to the desktop, then launch "System/Administration/Gparted" from the menu bar.  This will launch Gparted, the graphical partition editor supplied with Ubuntu and used in its installation.

If you need further instructions in its use, you can read at the link in my signature block, or ask further questions here in this thread.

---

### Post by Hedgehog1 on 2011-04-28
Rhodee,

You will need to boot from a LiveCD/LiveUSB, and then use gparted from there.

Once in gparted, right click on the SWAP partition and if SwapOff is showing select it (to unmount the swap space).

Next, Right click on the /dev/sda4 extended partition and select 'Move/resize', you will then resize the extended partition to use all the new space you have added.

Press the check mark button to make the change real.

Next, Right click on the /dev/sda5 Linux partition and select 'Move/resize', you will then resize the this partition to use all the new space you have added into the extended partition.

Press the check mark button to make the change real.

You can then reboot and enjoy the extra disk space!


***The Hedge***

:KS

---

### Post by Rhodee on 2011-04-28
Problem solved.

Although I did get an error. It created a file in the gparted directory. 

The re-partitioning does however seem to have taken hold and nothing strange happened. All appears to be well!

Thank you!!!!

---

