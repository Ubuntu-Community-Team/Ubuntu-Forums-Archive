---
title: "Advice on reformatting and reinstalling Ubuntu/WinXP"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by aihre on 2009-02-17
Hello everyone.  First post here!

I've been playing on Ubuntu (Wubi installation) for a little while and am liking Linux more and more.  So I'm planning to reformat my laptop, partition the HD with GParted, and install fresh WinXP and Ubuntu, with the goal of eventually migrating completely to Ubuntu for day-to-day computing, and just maintaining a "skeleton crew" in WinXP.

I've already read articles about partitioning/dual booting, but I'd like some advice on how to partition my single 40GB hard disk (effectively 38GB).  I'm thinking of splitting the drive this way (from left->right):

Ubuntu OS --- shared partition --- Windows XP --- swap

...is this a good order?  (I may one day end up deleting WinXP completely)  Can you advise me on how big these partitions should be?  Would you recommend that I have more of them?

I also have an external HD (300GB) that I'm planning to use strictly as storage, so the size of the shared partition is not an issue.

And apart from backing up data and drivers etc, any last words for someone about to embark on reformatting her computer?  (I've never done it, but I'm reasonably confident of my computer skills. :) )

Thanks in advance for your help!

---

### Post by MyR on 2009-02-17
I would install winxp on the entire drive then install ubuntu on the last 70% of it using the guided partitioning.
peace

---

### Post by era86 on 2009-02-17
> **MyR said:**
> I would install winxp on the entire drive then install ubuntu on the last 70% of it using the guided partitioning.
peace

I would do:

xp -> ubuntu -> shared -> swap

Make sure shared is FAT32 and you have ample space on each for installing programs.

---

### Post by Paqman on 2009-02-17
> **era86 said:**
> 
Make sure shared is FAT32

NTFS would work fine, too. As for sizes, i'd be inclined to give Windows 20GB or so if it's going to have any sizeable apps installed. Swap needs to be equal size to RAM to support hibernation, otherwise 1GB is usually a good size. All the rest can go to the shared partition and Ubuntu. Ubuntu will realistically want at least about 8GB. More is good, as it gives you room for any apps that might need to create a big temp file.

---

### Post by konqueror7 on 2009-02-17
i would go for winxp > shared > ubuntu > swap...just a habit for me to group partitions...

---

### Post by ckonrad on 2009-02-17
> **aihre said:**
> Hello everyone.  First post here!

I've been playing on Ubuntu (Wubi installation) for a little while and am liking Linux more and more.  So I'm planning to reformat my laptop, partition the HD with GParted, and install fresh WinXP and Ubuntu, with the goal of eventually migrating completely to Ubuntu for day-to-day computing, and just maintaining a "skeleton crew" in WinXP.

I've already read articles about partitioning/dual booting, but I'd like some advice on how to partition my single 40GB hard disk (effectively 38GB).  I'm thinking of splitting the drive this way (from left->right):

Ubuntu OS --- shared partition --- Windows XP --- swap

...is this a good order?  (I may one day end up deleting WinXP completely)  Can you advise me on how big these partitions should be?  Would you recommend that I have more of them?

I also have an external HD (300GB) that I'm planning to use strictly as storage, so the size of the shared partition is not an issue.

And apart from backing up data and drivers etc, any last words for someone about to embark on reformatting her computer?  (I've never done it, but I'm reasonably confident of my computer skills. :) )

Thanks in advance for your help!

Install Windows on the entire drive and then boot from your Ubuntu Disc into the live CD and click the install icon on the desktop then when the partition loads you can resize the Windows partition to whatever you want and install Ubuntu on the rest of the drive, the swap parition and Grub will be installed automatically.

---

### Post by aihre on 2009-02-17
Hey everyone, thanks for your advice.  Someone suggested sizing partitions while installing Ubuntu... what benefit would that have over, say, making partitions beforehand using GParted?

*edited to add:* I'm also thinking of making my shared partition Ext3 instead of FAT32 or NTFS, and just use FS-Driver for WinXP access.  Good idea?

---

### Post by MyR on 2009-02-17
> **aihre said:**
> Hey everyone, thanks for your advice.  Someone suggested sizing partitions while installing Ubuntu... what benefit would that have over, say, making partitions beforehand using GParted?

No, there's no real advantage; it's just less work.

---

### Post by crho85 on 2009-02-17
> **deuphil.kaufmann said:**
> i would go for winxp > shared > ubuntu > swap...just a habit for me to group partitions...


This is the way I did it. I gave ubu about 9, swap 1, xp 9, and the rest if shared. Only reason I mention numbers is my hd is also 40 gb. It seems to be working well so far.

I would recommend ntfs for your shared. The ubuntu handles it very well. All you need to do is run a ntfs config to make it mount the shared on start up


best of luck

---

### Post by Metallion on 2009-02-17
> **aihre said:**
> I'm also thinking of making my shared partition Ext3 instead of FAT32 or NTFS, and just use FS-Driver for WinXP access.  Good idea?

It works fine but you need to install a driver for it in WinXP. You can find one here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

I am using this one and it works really well for me. You can assign drive letters to your ext3 partition from the windows control panel. The driver is actually for ext2 but that's no problem. Ext3 is backwards compatible and can thus be mounted as ext2.

---

### Post by vanadium on 2009-02-17
Unless the drive is really large, I would not bother for a shared partition. In a dual-boot configuration, I would go for an Ubuntu install of only about 12 GB, a swap (2-3 GB) and leave all remaining space for Windows. I would then keep all my user data on the Windows partition and symlink it to my Ubuntu home directory for quick and convenient access from within Ubuntu.

For installation, I would prefer installing Windows in a partition that leaves sufficient free space for ubuntu (about 15 GB). After that, you can run the ubuntu installer and select "largest free space". Then Ubuntu automatically will configure the root and the swap in the free space.

Having Windows take the entire drive will also work, but then you need to resize the Win partition later, which is slightly more complicated (and perhaps slightly more risky).

It is finally your choice. With Linux, there are many ways to skin a cat.

---

### Post by Paqman on 2009-02-17
> **aihre said:**
> 
*edited to add:* I'm also thinking of making my shared partition Ext3 instead of FAT32 or NTFS, and just use FS-Driver for WinXP access.  Good idea?

Unfortunately not. Ext2ifs is considerably less widely tested and seems (annecdotally) to be less stable than ntfs3g (which is what Linux uses to write to NTFS) It also doesn't work at all if you use a newer version of Ubuntu than Hardy to format the partition.

I agree with Vanadium though. If you're storing your data on an external drive, do you really need a shared partition at all? The data drive is already a shared partition.

---

### Post by era86 on 2009-02-17
> **vanadium said:**
> I would then keep all my user data on the Windows partition and symlink it to my Ubuntu home directory for quick and convenient access from within Ubuntu.


This is currently how I have one of my systems set up.  I don't think there is a big need for a shared partition since both of the OS's can read NTFS at this point.

If you have an external, do you need a shared partition?

---

### Post by aihre on 2009-02-19
Hi everyone - thanks so much for your advice, I should be set for reformatting my laptop now.

@Paqman and era86: You're right, but I've had an external HD (which was a quasi-backup) die on me, and I'm a bit wary now of keeping everything on it.  I suppose it's no big deal though.

@vanadium: I recall reading somewhere (maybe at Psychocats.net) that it's not good to write directly to a WinXP partition from Ubuntu, and vice versa, something about the risk of messing up the OS you're writing to.  Is this true?

---

