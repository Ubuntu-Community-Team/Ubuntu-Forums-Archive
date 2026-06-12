---
title: "I messed up partioninig - is it simple to start again?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by listerdl on 2009-12-05
Hi, I am trying to partition my system: I'm aiming to set up a system with three partitions: One lean partition for the Windows operating system and applications running from it, another just-big-enough partition for Ubuntu and its own applications, and then a much larger data partition that houses all the data like documents. 

[COLOR="DarkOrange"]Am I correct in thinking that if I use GParted I will need to create partitions for Linux and the storage space, but not Windows since it is possible to let the Windows installation carve out its own recovery partition and operating space?[/COLOR]

[COLOR="DarkOrange"]My second question is - is it ok to give Windows 15 GB of unallocated space, and Ubuntu another 15 GB of space right after it, with whatever's left kept as storage space?[/COLOR]

THANKS ALL HELP VERY APPRECIATED!

---

### Post by whoop on 2009-12-05
I've found installing windows first, then installing ubuntu after that the best method.

This because with linux you have more control on what you are doing..

I would therefore install windows, boot your distro livecd, shrink the windows partition, and start the distro installer, create a /, swap and /home partition (required to adhere to your requirements). Then you are done....

---

### Post by listerdl on 2009-12-05
thanks...thata sounds like a simple plan.

But - is it possible to share the same data - so if you are in windows you can access a document and vica versa?

Thanks!

---

### Post by whoop on 2009-12-05
> **listerdl said:**
> thanks...thata sounds like a simple plan.

But - is it possible to share the same data - so if you are in windows you can access a document and vica versa?

Thanks!

Well, there are ext drivers for windows with which you can access your /home partition from windows, but if you intend to use files seamlessly in both OS's I would recommend creating an additional partition (filesystem fat32 or ntfs) to add/edit/delete files from both OS's.
In windows this partition will automatically be recognized (because of the file system), in linux you can add if via /etc/fstab

You could omit creating a /home partition, although creating a /home partition has various advantages altogether.

---

### Post by Anuovis on 2009-12-05
[COLOR=DarkOrange][/COLOR]I am not really sure how or what you messed up but as the above poster said, installing Windows first and then Ubuntu is the safe and simple way to do this.

Here is the simple way to do it:

1. Install Windows formatting the whole drive to NTFS (or whatever default file system for your Windows, this one is for the XP)

2.Burn Ubuntu CD, insert it and reboot. Then check the disk for defects and run the setup. There are many ways to make partitions, but you can stick with the simple things first. Go to **manual partitioning** when prompted.

Shrink the Windows file system. The size depends on how much you want to install and keep things there.

>Make SWAP partition. This should be twice the amount of you RAM. Consider this if you want to add more RAM in the near future.

>Then make Ubuntu system partition, **ext4** and mount point as **/** . Size also depends on how much you want to install, I would think 15-20 GB is a safe bet.

>And make the last one for your documents, **ext4** mount point as **/home **, use all the space that is left.

You can create up to 3 or 4 primary partitions, the rest have to be logical.

Hope this helps.

EDIT: I know Windows XP had drivers that enabled you to read/write ext2 and ext3. But the writing of files from Windows was rather slow. I have no idea if these will work with ext4.

If you have a small hard drive, you might want to check the finer estimates for the size of the partitions. Mine are very rogue.

In the case of Windows it is simple, check the used space right after fresh installation and you will see how much the OS itself needs. Then leave some space for the software you are planning to install.

---

### Post by wilee-nilee on 2009-12-05
Any windows install disc will allow you to install a specific size I believe so that you don't have to shrink it. Or you can have a partition ready of a specific size for windows to install into. Leaving a blank for the next operating system.

---

### Post by listerdl on 2009-12-05
> **anuovis said:**
> [i]i am not really sure how or what you messed up but as the above poster said, installing windows first and then ubuntu is the safe and simple way to do this.

Here is the simple way to do it:

1. Install windows formatting the whole drive to ntfs (or whatever default file system for your windows, this one is for the xp)

2.burn ubuntu cd, insert it and reboot. Then check the disk for defects and run the setup. There are many ways to make partitions, but you can stick with the simple things first. Go to **manual partitioning** when prompted.

Shrink the windows file system. The size depends on how much you want to install and keep things there.[/i]

[color="lime"]>make swap partition. This should be twice the amount of you ram. Consider this if you want to add more ram in the near future.

What should this be - also ext4?[/color]

[i]>then make ubuntu system partition, **ext4** and mount point as **/** . Size also depends on how much you want to install, i would think 15-20 gb is a safe bet.

>and make the last one for your documents, **ext4** mount point as **/home **, use all the space that is left.

You can create up to 3 or 4 primary partitions, the rest have to be logical.

Hope this helps.

Edit: And yes, like whoop said, you can make your shared partition a fat32. That would be **/home**. It will be simpler to share files between the two. Although it depends on how much and often you want to do that. I know windows xp had drivers that enabled you to read/write ext2 and ext3. But the writing of files from windows was rather slow. I have no idea if these will work with ext4.

If you have a small hard drive, you might want to check the finer estimates for the size of the partitions. Mine are very rogue.

In the case of windows it is simple, check the used space right after fresh installation and you will see how much the os itself needs. Then leave some space for the software you are planning to install.[/i]

thanks!

---

### Post by Anuovis on 2009-12-05
No, swap is just swap. You will see in the partition manager there, you can not specify any file system for it. And you don't have to.

---

### Post by ajgreeny on 2009-12-05
Whilst not wishing to confuse you even more than you possibly are already, I think there are a few points worth making that have largely been overlooked so far.  The result of all this is that I suggest:-

1.  If it is not already installed, do the Windows installation first, using enough space to accommodate the OS only; forget about your own docs, music, videos and photos, etc etc, we will deal with a data partition for those in a minute.  I do not know how big the Windows partition will need to be any more, but suspect that 10-15GB will be more than enough for XP, perhaps more needed for Vista, but no idea at all about Win7.  If you have to use the whole disk, do not worry, it can be shrunk when Ubuntu is installed.

2.  If you have WinXP you can safely shrink the partition with gparted on the Ubuntu live CD.  If you have Vista it is probably safer to use its own disk management utility to shrink its partition after installing Vista, rather than gparted.  Again, I have no knowledge of Win7 so can not comment on that.

3.  Install Ubuntu with a 10GB / (root) partition, and a swap partition of about 2GB, depending on your ram size and whether or not you want to suspend and hibernate, but don't bother with a separate /home partition.  I say this because you should also make a /data partition of the rest of your disk which you format to NTFS, making it usable by both your windows and Ubuntu OSs.  **You can not use an NTFS or fat32 partition as home in ubuntu** so this suggested way will keep all your home configuration files and folders in home within the / partition, but all your files of personal data, photos etc etc will be separate, and you will be able to share them between the two OSs without problem.

4.  Install and use **ntfs-config** in ubuntu to make the ntfs data partition available at boot time and to give you read/write permissions to it.

5.  Should you use hibernate or suspend to ram, just make sure you don't restart the machine to the other different OS from that state or you could suffer huge problems of data loss.

Sorry if that all sound very complicated; it is not really as difficult as it probably sounds, but if you want more help along the way, ask again.

---

### Post by Anuovis on 2009-12-05
> **ajgreeny said:**
>   **You can not use an NTFS or fat32 partition as home in ubuntu** 
I am sorry for the possible confusion, I did not know that. 

You should surely take [ajgreeny]("http://ubuntuforums.org/member.php?u=27747")'s advice into consideration. Unless you plan using Ubuntu for most of the time and Windows only occasionally, the shared partition that he described should work better. 
If the majority of your time will be spent in Ubuntu, you might consider keeping all the data in ext4, but the access will be slow on the Windows side. And have you to check if the drivers for ext4 exist for Windows at all. If they do not, do not bother with this.

Ajgreeny's post is probably the way to go.

---

### Post by Greenwidth on 2009-12-05
Hopefully this won't add to any confusion , but you do not need a swap partition - you can make a swap file instead -"With the 2.6 kernel, "a swap file is just as fast as a swap partition." + you can easily resize it / delete if you need to.

Swap info &c:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by listerdl on 2009-12-05
thanks for all the help!!

Ill let you know how i get on!!

---

### Post by issih on 2009-12-05
I didn't know that swap files were now as good as a partition...thanks for that bit of info :)

---

