---
title: "Primary partition vs. Logic partition"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by zhaotianwu on 2010-11-09
Hi everyone, I'm a newbie to linux. I'm currently contemplating dual-boot ubuntu with windows xp. One of the problems that I encounter is the partition.

Could anyone provide some advice in plain language on what the difference between a primary partition and a logic partition is? Why does somebody advice against the idea that make /home a logic partition?

Many thanks.

---

### Post by amjjawad on 2010-11-09
> **zhaotianwu said:**
> Hi everyone, I'm a newbie to linux. I'm currently contemplating dual-boot ubuntu with windows xp. One of the problems that I encounter is the partition.

Could anyone provide some advice in plain language on what the difference between a primary partition and a logic partition is? Why does somebody advice against the idea that make /home a logic partition?

Many thanks.

Hello and welcome :)

First of all, you need to understand the basics of Partitioning.
I suggest to start from here: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

The next step IMHO is: [https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

If you couldn't find the answer to your questions in step 1 and step 2 then in simple and plain language:

For Linux (Ubuntu), you need minimum TWO Partitions (Root and Swap). The recommended is to have 3 (Root, Swap and Home).
You you need to understand that it's not possible to have more than 4 Primary Partitions, thus you need to create Extended Partition and inside that, you could have many other Logical Partitions.

I believe the two links I provided will help you so much :)

Please don't hesitate to ask :)

---

### Post by walt.smith1960 on 2010-11-09
> **amjjawad said:**
> Hello and welcome :)

<snip>
For Linux (Ubuntu), you need minimum TWO Partitions (Root and Swap). The recommended is to have 3 (Root, Swap and Home).
You you need to understand that it's not possible to have more than 4 Primary Partitions, thus you need to create Extended Partition and inside that, you could have many other Logical Partitions.

I believe the two links I provided will help you so much :)

Please don't hesitate to ask :)

Au Contraire :).  The more recent kernels performance with a swap* file* is supposed to be as good as with a swap *partition*.  A swap file will not permit hibernation, a swap partition will. I've never experimented with hibernation in Ubuntu; in Windows XP I could see little benefit over simply cold booting. Perhaps hibernation works better in Ubuntu.  I use S5 suspend and that seems to work reliably on my newish machine. S3 suspend was reliable on my retired machine.  Using a swap file saves one partition.  It is also possible to have more than 4 primary partitions with a boot management program.  I use BootItNG from Terabyte Unlimited. It'll support up to 128 primary partitions or some outrageous number.  The biggest trick with installing Linux using BootItNG is to be sure to put GRUB in the partition, not HD root.  GRUB will overwrite the EMBR that BootIt creates.  Ask me how I know this :oops:.
[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

---

### Post by zhaotianwu on 2010-11-09
> **amjjawad said:**
> Hello and welcome :)

First of all, you need to understand the basics of Partitioning.
I suggest to start from here: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

The next step IMHO is: [https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

If you couldn't find the answer to your questions in step 1 and step 2 then in simple and plain language:

For Linux (Ubuntu), you need minimum TWO Partitions (Root and Swap). The recommended is to have 3 (Root, Swap and Home).
You you need to understand that it's not possible to have more than 4 Primary Partitions, thus you need to create Extended Partition and inside that, you could have many other Logical Partitions.

I believe the two links I provided will help you so much :)

Please don't hesitate to ask :)


Thank you. Could you also explain what, if any, is the difference between /boot and root in linux partition system? Are they the same? Thanks.

---

### Post by amjjawad on 2010-11-09
> **zhaotianwu said:**
> Thank you. Could you also explain what, if any, is the difference between /boot and root in linux partition system? Are they the same? Thanks.

You welcome!

To understand the differences:
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)


As for Ubuntu, you don't need /boot partition, you just need (recommended):
**/** which is the root partition
**/home** which is the home partition
(both are ext4 file system)
**swap** partition

The root partition will have all the information needed to boot your machine so that you don't need /boot partition.
/home is very useful to save your data like pictures, music, etc. It's recommended to put these data on a separate partition (/home) rather than / (root) but if you want, you could have only two partitions, root and swap but again, that's the minimum and as you may know, in Computer World, there are Minimum Requirements and Recommended Requirements.

---

### Post by zhaotianwu on 2010-11-09
Thank you very much. Should I make /root, /home and swap, all of them, primary partition? What's the benefit of primary partition. I'm a history major so sometimes a little bit slow :) sorry

---

### Post by ImaLamer on 2010-11-09
More info can be found on this page;

[http://en.kioskea.net/contents/repar/partitio.php3](http://en.kioskea.net/contents/repar/partitio.php3)

zhaotianwu, in response to your private message here is the relevant info;

> ...there are three types of partitions: primary partitions, extended partitions and logical drives. A disk may contain up to four primary partitions (only one of which can be active), or three primary partitions and one extended partition. In the extended partition, the user can create logical drives (i.e. create the impression that there are several smaller-sized hard drives). 

---

### Post by srs5694 on 2010-11-09
> **zhaotianwu said:**
> Thank you very much. Should I make /root, /home and swap, all of them, primary partition? What's the benefit of primary partition.

First, don't confuse the root (/) directory with the /root directory. The former is the base of the Linux directory tree -- all files and filesystems are referenced relative to it. The /root directory, OTOH, is the home directory for the root user (the main administrative account). Although the two directories are pronounced the same, they're very different. The /root directory is seldom or never split off into its own partition, although theoretically it could be.

For Linux, there's no practical benefit to primary partitions over logical partitions, and lots of benefit to logical partitions. This is because, as noted in an earlier post, you can have at most four primary partitions on disks that use the common Master Boot Record (MBR) partitioning system (or three primaries and one extended partition, which in turn houses logical partitions); but the number of logical partitions is virtually limitless, provided the disk has an extended partition. Many computers today ship with 2-4 primary partitions already in use, so you're likely to be forced to use logical partitions for some or all Linux partitions.

Windows requires primary partitions for certain purposes, including booting Windows. This is a Windows design limitation; Linux can boot just fine from a logical partition.

---

### Post by amjjawad on 2010-11-10
> **zhaotianwu said:**
> Thank you very much. Should I make /root, /home and swap, all of them, primary partition? What's the benefit of primary partition. I'm a history major so sometimes a little bit slow :) sorry

You welcome :)

You could do that if and only if:
You have 
1) Windows on Primary Partition 1
2) Ubuntu (/) Partition on Primary Partition 2
3) Ubuntu (/home) Partition on Primary Partition 3
4) Ubuntu (swap) Partition on Primary Partition 4.

The disadvantage of the above scheme is you will NOT be able to add any other partition UNLESS you delete one, make it Extended and create Logical Partition inside.
I believe the previous links that I posted in my first post should explained that.

To make it easier for you, even though I have no idea what's the capacity of your Hard Disc but that doesn't matter much, I'll suggest a scheme to use:

Let's assume your hard is 80GB (even though it's larger, but it's just an example). and let's assume your RAM is 1 GB. Here's what you need to have:

Total size: 80GB

Partition 1 (sda1): Primary Partition for Windows (*Windows **MUST** be installed on Primary Partition*) - Size = 30GB - File System = NTFS.

Partition 2 (sda2): Primary Partition for Ubuntu (/) Partition (Ubuntu could be installed on any type, Primary or Logical, doesn't matter) - Size = 20GB - File System = ext4.

Extended Partition (sda5)
      Partition 3 (sda6): Logical Partition for Ubuntu (/home) Partition - Size 18GB - File System = ext4

Partition 4 (sda7): Logical Partition for Ubuntu (swap) Partition - Size = [COLOR=Red]**2GB***[/COLOR] - File System = Linux Swap

Partition 5 (sda8): Logical Partition for Data (this partition can be used as a shared partition between Windows and Ubuntu to store some data) - Size = 10GB - File System = NTFS (so that both Windows and Ubuntu could access it without any extra effort).

*** OR ***
You could have 1 Primary Partition and all the others are Logical. It's all up to you. As I mentioned and someone else did, Ubuntu has no problem to be installed on any type (Primary or Logical).

The MAIN benefit of the Logical Partition actually is that you can't have more than 4 Primary Partitions, this is why you could solve this with Logical Partitions. For me, I always keep 1 - 3 Primary and the other are Logical.
If I'm not wrong, I have 14 partition on 500GB HDD, only 3 are Primary and the other are Logical. It up to you. Again, Ubuntu doesn't mind to be installed on Logical but Windows will freak out :)

[COLOR=Red][B]2GB* = Your Swap Partition must be 
Either: equal to your RAM - if your RAM is 1GB then Swap must be 1GB too.

Or: Double your RAM - if your RAM is 1GB then Swap must be 2GB.

If your RAM is more than 2GB, I suggest to give 2GB to your SWAP or a bit more if you like. 


[/B][/COLOR]

---

### Post by zhaotianwu on 2010-11-10
> **amjjawad said:**
> You welcome :)

Total size: 80GB

Partition 1 (sda1): Primary Partition for Windows (*Windows **MUST** be installed on Primary Partition*) - Size = 30GB - File System = NTFS.

Partition 2 (sda2): Primary Partition for Ubuntu (/) Partition (Ubuntu could be installed on any type, Primary or Logical, doesn't matter) - Size = 20GB - File System = ext4.

Extended Partition (sda5)
      Partition 3 (sda6): Logical Partition for Ubuntu (/home) Partition - Size 18GB - File System = ext4

Partition 4 (sda7): Logical Partition for Ubuntu (swap) Partition - Size = [COLOR=Red]**2GB***[/COLOR] - File System = Linux Swap

Partition 5 (sda8): Logical Partition for Data (this partition can be used as a shared partition between Windows and Ubuntu to store some data) - Size = 10GB - File System = NTFS (so that both Windows and Ubuntu could access it without any extra effort).

[COLOR=Red][/COLOR]

For the last "shared partition between Windows and Ubuntu" (NTFS) that is used for both Windows and Ubuntu accessing it without any extra effort, should I create it when I install windows xp, or should I create it under Ubuntu installlation? thanks.

---

### Post by amjjawad on 2010-11-10
> **zhaotianwu said:**
> For the last "shared partition between Windows and Ubuntu" (NTFS) that is used for both Windows and Ubuntu accessing it without any extra effort, should I create it when I install windows xp, or should I create it under Ubuntu installlation? thanks.

That is totally optional :)
Usually when I reply, I try my best to give the answer my best so I cover all the aspects or potential questions that one might have. It's up to you to create that partition or not and it's totally up to you whether to create that upon Windows Installation or Ubuntu.
I love Gparted that comes with Ubuntu LiveCD BUT not after you install it (starting from Ubuntu 10.04 as it was installed by default in 9.10). You could wipe the whole HDD, start booting from Ubuntu's LiveCD, use GParted to create your partitions and then Install Windows then Ubuntu.
By the way, that "optional" partition the one which is shared between Ubuntu and Windows, you also could leave that space unallocated or unpartitioned for future consideration. I have around 100GB not allocated and unused. I keep it for future usage. I have a bit of complicated setup (9 OS's installed) so I don't want to mess with that :)

In my signature, there's a simple guide of how to use GParted. Actually, you could always use Google and you'll find a lot of useful HOWTO or Articles :)

The scheme that I suggested, should cover all your needs (I suppose) but of course you just need to replace the numbers with what you have. For example, instead of 80GB HDD (Hard Disc Drive), you could use your real size of HDD which I don't know yet but that's not a problem :)

Let me know if you need more info :)

---

### Post by zhaotianwu on 2010-11-10
Thank you so much for this detailed answer. Indeed I do have one more question here. For the /home folder, which is used for storing personal documents etc., can I personalize the name, for example instead of "/home", I call it "Zhaotianwu", without messing its purposes up?

---

### Post by amjjawad on 2010-11-10
> **zhaotianwu said:**
> Thank you so much for this detailed answer. Indeed I do have one more question here. For the /home folder, which is used for storing personal documents etc., can I personalize the name, for example instead of "/home", I call it "Zhaotianwu", without messing its purposes up?

You're welcome as always :)

If I'm not mistaken, you can't but I'm not sure about that. However, after you install Ubuntu, you'll have something like that

/home/yourusername

The name that you'll provide upon installation will be used so when you go to ***Places > Computer***  you'll find your name on the left hand side as the first item.
Also, when you go to ***Applications > Accessories > Terminal*** and type

```
pwd

```
You'll have something like above "/home/yourusername".

:)

---

