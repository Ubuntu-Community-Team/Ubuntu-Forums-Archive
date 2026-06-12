---
title: "HOWTO: delete Windows operating system to make ubuntu single boot"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by zeuso0 on 2010-10-26
I have dual boot, xp and ubuntu, on my computer.

I want to use linux operating system only.

how to do it?

---

### Post by ArgusVision on 2010-10-26
First of all, make sure you back up any files you intend to keep.
Then, there are several ways to handle what you are trying to do.
Probably the easiest is to toss in your live CD, fire up Gparted, delete the windows partition and expand the ubunutu partition to take up the space. That's not the cleanest, but the quickest. It leaves your sole booting partition as sda2 or 3 instead of sda1 and there's a small possibility of files getting messed up.

EDIT: I forgot to mention, you will need to update grub...

Another cleaner way, is backup your home directory. Get APTonCD and backup your apt downloads and upgrades. Then do a fresh install. It's up to you, but you might take this time to make a separate home partition.

---

### Post by zeuso0 on 2010-10-26
> **ArgusVision said:**
> First of all, make sure you back up any files you intend to keep.
Then, there are several ways to handle what you are trying to do.
Probably the easiest is to toss in your live CD, fire up Gparted, delete the windows partition and expand the ubunutu partition to take up the space. That's not the cleanest, but the quickest. It leaves your sole booting partition as sda2 or 3 instead of sda1 and there's a small possibility of files getting messed up.

Another cleaner way, is backup your home directory. Get APTonCD and backup your apt downloads and upgrades. Then do a fresh install. It's up to you, but you might take this time to make a separate home partition.


Thnks for your reply..but how to "get APT on CD"and "backup your apt downloads and upgrades"? what folders that specificly store apt and apt downloads in linux??

---

### Post by ArgusVision on 2010-10-26
You can get APTonCD from the Software center or synaptic. After you install just get a blank CD (or DVD), and run it from System > Administration.
Click "create", it finds the apt cache, and shows you what is available for backup. If you have multiple kernels I'd only backup the two most recent that you know work.

After the new install, rather than downloading a bunch of updates, and trying to remember which apps you downloaded, just install APTonCD, run it with the CD you made earlier, and click restore.

---

### Post by seventhsamurai on 2010-10-26
Anyway, your system by default will be booting up through grub. So when you are in Ubuntu, just open the disk utility, go to your windows partition and format it as a linux partition (after you have backed up important data that is). Dont think you need to do anything more. I wouldnt recommend extending your linux partition into your fresh empty space. Just use it as a separate storage disk. That way, in case your main linux partition gets corrupted, your data is still intact on another partition. That's often the whole idea of partitioning disks.

---

### Post by amjjawad on 2010-10-26
> **zeuso0 said:**
> I have dual boot, xp and ubuntu, on my computer.

I want to use linux operating system only.

how to do it?

First thing first:

[LIST]
[*]**If Ubuntu's Boot Loader (GRUB) was installed in the MBR of your HDD and you have GParted installed in Ubuntu then:**
[/LIST]

All what you need to do is:
1- Backup your important files on BOTH XP and Ubuntu.
2- Delete Windows XP's Partition 
3- From Terminal (Applications > Accessories > Terminal) you need to run 
```
sudo update-grub

```
4- Restart your machine.


[LIST]
[*]**If Ubuntu's Boot Loader (GRUB) was installed in the MBR of your HDD and you DO NOT have GParted installed in Ubuntu then:**
[/LIST]
A) Either
1- Backup your important files on BOTH XP and Ubuntu.
2- Boot from Ubuntu's LiveCD or LiveUSB.
3- Delete Windows XP's Partition.
4- Restart.
5- From Terminal (Applications > Accessories > Terminal) you need to run 
```
sudo update-grub

```
6- Restart
7- Perhaps you could do step (5) from the Live Session (someone please to confirm that).

B) Or
1- Install GParted from Synaptic Package Manager (System > Administration > Synaptic) 
2-  Backup your important files on BOTH XP and Ubuntu.
3- Delete Windows XP's Partition 
4- From Terminal (Applications > Accessories > Terminal) you need to run 
```
sudo update-grub

```
5- Restart your machine.


If GRUB (Ubuntu's Boot Loader) is NOT installed in the MBR, then it's different story.

If you want to format the whole thing and start from scratch, then it's another story too.

JUST make sure to BACKUP all your files before start doing anything :)

---

### Post by Megaptera on 2010-10-27
I found this basic (illustrated) partitioning guide very helpful when I ditched Vista/Ubuntu dualboot and went for Ubuntu 10.04 on its own:

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

I know there are differing views on partitioning but this was a good place to start.

---

