---
title: "Remove Windows from Dual-boot machine"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Newbie2910 on 2011-03-06
My pc came with Vista and I installed Ubuntu 10.04 about a year ago.  At this point I no longer use Windows and would like to give the Windows partitions over to Ubuntu.

Attached is a map of my hard drive.  I guess I should be able to remove everything to the left of the extended partition (the one that Ubuntu is using)?

What are the steps to do this (I will make sure I have Ubuntu on a CD just in case!).

Is there a way to make it all one big partition or is that not the way to go?  I have read that some people like to use a separate partition for Home, is that a good recommendation and how is that accomplished?

Thanks!

---

### Post by turtle153 on 2011-03-06
You can just remove all the Windows partitions (there will be at least two: one of them is a boot partition), and run```

sudo update-grub
```
te remove it from the bootloader.

---

### Post by grahammechanical on 2011-03-06
What are those Dell Utilities? Do you run them under Windows? Or can you run them outside of Windows? If so, you might want to keep them.

You can use the partitioner program on the Live CD to expand the 214GB NTFS partition to the left to take over the space of the 16BG NFTS recovery partition. That will effectively remove the recovery partition.

You can the shrink the new 230 GB NTFS partition from the right to about 20GB. You then expand the Extended partition to the left until it meets the boundary of the new 20GB partition.

You then expand 87GB ext4 partition to the left until it meets the boundary of the extended partition. The partitioner will make all these changes at the same time. You can quit any time you get nervous.

Then you re-install Ubuntu giving the 20GB partition the mount point of / and the large ext4 partition the mount point of /home. You set the partitions to be formatted.

You will loose all your data in both Windows and Ubuntu, so save what you want. Note down your passwords and your network connection settings, backup your browser profile and your email data.

Think and plan before you do anything. Write down step by step what you plan to do and double check your method.

The advantage of having a separate home partition or even a disc is that you do not loose your data or browser/email settings if you need to reinstall Ubuntu. So long as you do not make the /home partition to be formatted.

Regards.

---

### Post by Newbie2910 on 2011-03-07
I'd rather not have to reload Ubuntu if I don't have to.

I should have mentioned that I plan to install Virtualbox to run some ham radio software on Windows XP.

With that in mind, should I just format the current Windows partition and use that space to install XP?  I would like to give some more room to Ubuntu though.

---

