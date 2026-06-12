---
title: "Mounting an Ext4 partition to /?"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Red Raven on 2011-01-07
I am trying to do my second install of 10.10 Ubuntu onto an old desktop. I have gotten as far as the final partitioning. What i'm doing is making an extended with a Swap and ext4 in it. i want the ext4 mounted to /. I have my laptop set up the same way (see attached image). so far on the desktop i have the extended and swap set up, but i still need to make the ext4. but when i try to make it, i don't see the option to mount it. how do i do this? (I'm using Gparted btw) also, once i have set it up, i need to install it. do i just click on install side-by-side with another OS, or custom install? in the past i've done custom install and set up the partitions there, but idk if it's different or what this time because im setting them up before hand.

Thanks!

---

### Post by -kg- on 2011-01-07
I assume you mean "setting the mount point."  Setting the mount point is done during installation, not when creating the partitions.

Having created the partitions with GParted prior to installation, you will need to choose the Manual Partitioning option when you get to the partitioning portion of the installer.  You select the partition that you wish to mark as "/" and, in the edit box, there is a drop-down box that allows you to specify what you want to set the mount point of that partition as.  "/" is one of the options.  In fact, you *must* mark at least the "/" mount point on a partition in order for the installer to be able to install Ubuntu.  The only partition you won't need to mark a mount point for is the swap partition.

Much easier to let the installer automatically set the partitions up, but since you're doing a custom installation, you can do it this way, too.  You can set your partitions up beforehand, but you can also set them up manually in the Manual Partitioning option.  You can create them, format them, and mark their mount point.  That's the way I usually set mine up, considering that I have several installations on both of my computers.

---

### Post by bodhi.zazen on 2011-01-07
> **Red Raven said:**
> I am trying to do my second install of 10.10 Ubuntu onto an old desktop. I have gotten as far as the final partitioning. What i'm doing is making an extended with a Swap and ext4 in it. i want the ext4 mounted to /. I have my laptop set up the same way (see attached image). so far on the desktop i have the extended and swap set up, but i still need to make the ext4. but when i try to make it, i don't see the option to mount it. how do i do this? (I'm using Gparted btw) also, once i have set it up, i need to install it. do i just click on install side-by-side with another OS, or custom install? in the past i've done custom install and set up the partitions there, but idk if it's different or what this time because im setting them up before hand.

Thanks!

Make the partitions. 

Personally I think it is best to then reboot, but you do need to.

The run the installer. When installing assign the ext4 partition to root. It will be re-formatted when you install.

but you do not mount it at root at this time.

---

