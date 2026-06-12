---
title: "I need help with a partitioning problem please"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by xhepera on 2010-08-07
I'm a rank newbie to Ubuntu and am attempting to install 10.04 in a dual boot configuration with Windows XP. I actually had it installed already and running fine except for the fact that I couldn't get audio through my headphones. While attempting to fix this I kind of munged up the audio altogether. In addition I had downloaded and installed some video drivers that kind of messed up the installation.

I decided to take the opportunity to reinstall and use a separate /home p[IMG]http://ubuntuforums.org/images/editor/menupop.gif[/IMG]artition configuration. I have about 32 G or so of disk space to work with which should be okay as I plan to let XP and Ubuntu share some data from a separate ntfs partition that XP uses. My plan is to have 10 G for /, 20G for /home and 2/G for a swap partition (I have 2 gigs of RAM).

Using GParted, I'm able to create a primary partition for /. I'm able to create an extended partition for /home. And I've got 2G left for the swap are but Gparted will not allow me to use the area and, in fact, says that it's unusable.

I'd appreciate it if someone can tell me what I might be doing wrong to cause this behavior. Thanks!

---

### Post by The Mighty Debo on 2010-08-07
Have you tried re-assigning the space back to your XP partition and then re-installing Ubuntu? That would allow it to automatically partition the space and install the OS + GRUB.

You can then create another partition to share data on w/ Gparted

---

### Post by sandyd on 2010-08-07
> **xhepera said:**
> I'm a rank newbie to Ubuntu and am attempting to install 10.04 in a dual boot configuration with Windows XP. I actually had it installed already and running fine except for the fact that I couldn't get audio through my headphones. While attempting to fix this I kind of munged up the audio altogether. In addition I had downloaded and installed some video drivers that kind of messed up the installation.

I decided to take the opportunity to reinstall and use a separate /home p[IMG]http://ubuntuforums.org/images/editor/menupop.gif[/IMG]artition configuration. I have about 32 G or so of disk space to work with which should be okay as I plan to let XP and Ubuntu share some data from a separate ntfs partition that XP uses. My plan is to have 10 G for /, 20G for /home and 2/G for a swap partition (I have 2 gigs of RAM).

Using GParted, I'm able to create a primary partition for /. I'm able to create an extended partition for /home. And I've got 2G left for the swap are but Gparted will not allow me to use the area and, in fact, says that it's unusable.

I'd appreciate it if someone can tell me what I might be doing wrong to cause this behavior. Thanks!
so your telling me you have the following partitons (not in order) on your drive right?
1. XP
2. Seperate NTFS
3. Ubuntu
4. Seperate Ubuntu Partiton
5. SWAP
^This above configuration will NOT work, unless you have an extended partiton containing the swap and the seperate NTFS
the partitons table is limited to 4 partitons (including any extended partitions)

---

### Post by Miljet on 2010-08-07
An extended partition is a type of primary partition that acts as a container for one or more logical partitions. If you used everything inside the extended partition for /home, there is no room for the swap.
 
All you have to do is expand the extended partition to include the unused space and create your swap INSIDE the extended partition.

If you can furnish the results of ```
sudo fdisk -l 
``` we would have a better idea of what you have.

---

### Post by xhepera on 2010-08-07
> **carlee said:**
> so your telling me you have the following partitons (not in order) on your drive right?
1. XP
2. Seperate NTFS
3. Ubuntu
4. Seperate Ubuntu Partiton
5. SWAP
^This above configuration will NOT work, unless you have an extended partiton containing the swap and the seperate NTFS
the partitons table is limited to 4 partitons (including any extended partitions)

Thanks for the replies! 'Cause I'mutterly lost at this point. ;)

Actually, it was originally like this:
1.XP on a Primary
2. Extended with 4 logical drives.
3. Ubuntu on a Prmary
4. 2 G swap area

What I am trying to do now doesn't involve touching the XP or NTFS partitions at all (well, except for Ubuntu manipulating the MBR).
1. XP on Primary
2. Extended with 4 NTFS Logicals
3. Ubuntu on Primary
4. /home on a logical
5. Swap area on a logical

GParted, whether in the installer on the Live CD or as a stand-alone, will not allow me to assign the swap area. I suppose I could just go ahead and install and add the swap area sometime later?

---

### Post by xhepera on 2010-08-07
> **Miljet said:**
> An extended partition is a type of primary partition that acts as a container for one or more logical partitions. If you used everything inside the extended partition for /home, there is no room for the swap.
 
All you have to do is expand the extended partition to include the unused space and create your swap INSIDE the extended partition.

If you can furnish the results of ```
sudo fdisk -l 
``` we would have a better idea of what you have.

Thank you. I'm not sure about what this output shows as the original installation no longer exists,

255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3754    30153973+   7  HPFS/NTFS
/dev/sda3            3755       15692    95885149+   f  W95 Ext'd (LBA)
/dev/sda5            3755        7579    30724281    7  HPFS/NTFS
/dev/sda6            7580        8854    10241406    7  HPFS/NTFS
/dev/sda7            8855       11404    20482843+   7  HPFS/NTFS
/dev/sda8           11405       15320    31455238+   7  HPFS/NTFS

Disk /dev/mmcblk0: 513 MB, 513277952 bytes
9 heads, 40 sectors/track, 2784 cylinders
Units = cylinders of 360 * 512 = 184320 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        2785      501131+   6  FAT16

---

### Post by xhepera on 2010-08-08
Well, I absolutely cannot figure this out. I thank you all for the tips, info and suggestions! But between this and not being able to get my headphones to work I guess perhaps I'm just not ready for Ubuntu. A shame because I really like what I can get to work in it! lol!

Thanks again.

---

### Post by Jmih on 2010-08-08
Hey u can search the drivers of ur hardware in synaptic package manager and if u have realtek ac97 hardware in ur pc it should work (bcoz i have 1) and dont worry if ur hardware dosent work on ubuntu.Mine video drivers are still not recognized by ubuntu but i am able to make my whole hardware work except my nokia n70 but will find a way of doing that .

---

### Post by xhepera on 2010-08-08
> **Jmih said:**
> Hey u can search the drivers of ur hardware in synaptic package manager and if u have realtek ac97 hardware in ur pc it should work (bcoz i have 1) and dont worry if ur hardware dosent work on ubuntu.Mine video drivers are still not recognized by ubuntu but i am able to make my whole hardware work except my nokia n70 but will find a way of doing that .

Hey Jmih, thanks for that info. I think the issue with the headphones may be related to the fact that Ubuntu is seeing my soundcard as a different brand than it actually is. I've seen the headphone problem referenced repeatedly but found no real resolution to the problem. In fact, following some directions from someone who allegedly got it to work is how I munged up my original Ubuntu installation in the first place. ;) I'll definitely check into your suggestion!

---

### Post by xhepera on 2010-08-08
Okay. . .I see what the problem is. Took me a while but, as I noted in my first post, I'm a rank newbie.
What I would like to do is have a Primary partition for Ubuntu. Within that Primary I'd like to create an Extended partition for /home. Within that Extended partition I would like to create a logical partition for /swap. Gparted is not giving me options for extended or logical partitions. . .only primary. So, of course, I end up wanting/needing too many Primaries. Can someone please tell me what I'm missing here as far as Gparted's functionality? I even booted from a Gparted Live CD thinking that maybe it was the version on the Ubuntu disc that was the problem. Same issue. 

Thanks!

I just need to know how to create extended and logical partitions I guess. ;)

---

### Post by Miljet on 2010-08-09
Obviously you need to better understand partitions before you totally crash your system.

You don't create an extended partition inside a primary partition. An extended partition IS a primary partition, one of the 4 total permitted.

Consider this; you are permitted up to 4 primary partitions. One of those primary partitions can be an extended partition. The extended partition can contain numerous logical partitions.

```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 3754 30153973+ 7 HPFS/NTFS
/dev/sda3 3755 15692 95885149+ f W95 Ext'd (LBA)
/dev/sda5 3755 7579 30724281 7 HPFS/NTFS
/dev/sda6 7580 8854 10241406 7 HPFS/NTFS
/dev/sda7 8855 11404 20482843+ 7 HPFS/NTFS
/dev/sda8 11405 15320 31455238+ 7 HPFS/NTFS
```

This output of fdisk indicates that you have two primary partitions, sda1 and sda3. Note that sda3 is an extended partition. Sda5, sda6, sda7, and sda8 are all logical partitions located inside sda3. One thing is notable--all your partitions are NTFS (Windows) partitions. Therefore, you either do not have Ubuntu installed on this drive, or it is installed inside Windows (using WUBI).

Here is a link to start learning how partitions work.  [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by xhepera on 2010-08-09
> **Miljet said:**
> Obviously you need to better understand partitions before you totally crash your system.
 
You don't create an extended partition inside a primary partition. An extended partition IS a primary partition, one of the 4 total permitted.
 
Consider this; you are permitted up to 4 primary partitions. One of those primary partitions can be an extended partition. The extended partition can contain numerous logical partitions.
 
```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 3754 30153973+ 7 HPFS/NTFS
/dev/sda3 3755 15692 95885149+ f W95 Ext'd (LBA)
/dev/sda5 3755 7579 30724281 7 HPFS/NTFS
/dev/sda6 7580 8854 10241406 7 HPFS/NTFS
/dev/sda7 8855 11404 20482843+ 7 HPFS/NTFS
/dev/sda8 11405 15320 31455238+ 7 HPFS/NTFS
```
 
This output of fdisk indicates that you have two primary partitions, sda1 and sda3. Note that sda3 is an extended partition. Sda5, sda6, sda7, and sda8 are all logical partitions located inside sda3. One thing is notable--all your partitions are NTFS (Windows) partitions. Therefore, you either do not have Ubuntu installed on this drive, or it is installed inside Windows (using WUBI).
 
Here is a link to start learning how partitions work. [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
 
Thank you. I actually figured out my problem last evening. As you pointed out, I didn't have Ubuntu installed on the drive any longer because, as I said, I had wiped it so that I could create a separate /home partition which I hadn't in my original install. The fdisk output was done using the Live CD.
 
Actually, I understand partitioning fairly well, having done it often for Windows installs. It's just been a while. :) But I was operating under a couple of misconceptions. One was that I had forgotten that an extended partition actually counts as one of the primaries. DUH! Shoulda been smacked for that one. The other issue is that an alleged Ubuntu "guru" (yeah right) had told me that Linux installs had to go on a primary, as in Windows. Once I did some looking around and realized that Linux really doesn't care where it's installed for the most part, I simply created more logicals in the extended partition and all was well.
 
Lessons learned. Do a refresher on things you haven't done in a while. And be wary of "gurus." lol! 
 
Thanks again for your help and information. It's VERY much appreciated.
 
*sigh* Now to figure out why the headphones get no sound and why Ubuntu refuses to come out of suspend or do a proper restart. :(

---

### Post by Miljet on 2010-08-10
Sure glad you got it sorted out. Sure sounded like you were thrashing around in the dark there for a while. Good luck with the other problems. I can't be much help there. Might help to start another thread on those.

---

### Post by KROwen1959 on 2010-08-10
I to am a newbie. I love Linux. I have learned a lot through trial and error. I have windows 7 and I shrank my hard drive to add Linux on. To make a long story short I install Linux 3 times. When I do    sudo fdisk this is what I see and I would love to get rid of 2 of them                                                         
kenneth@kenneth-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92d292d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24014   192891412    7  HPFS/NTFS
/dev/sda2           82560      121601   313604865    7  HPFS/NTFS
/dev/sda3           24014       82559   470262785    5  Extended
/dev/sda5           69811       82036    98191360   83  Linux
/dev/sda6           82036       82559     4206592   82  Linux swap / Solaris
/dev/sda7           39622       55317   126076724   83  Linux
/dev/sda8           68583       69810     9862144   82  Linux swap / Solaris
/dev/sda9           24014       38982   120227840   83  Linux
/dev/sda10          38982       39621     5134336   82  Linux swap / Solaris

Partition table entries are not in disk order
kenneth@kenneth-desktop:~$

 Anyone knowing how I would be very greatful

---

### Post by Miljet on 2010-08-10
To KROwen1959

What exactly do you want to get rid of? Obviously you need to get rid of two of the three swap partitions. You only need one swap partition even if you have more than one Linux installation. If you have 3 identical Ubuntu installs, you can delete two of them and include the space in the remaining install.

But here is something else to think about. I keep two partitions for Ubuntu on my computer. Whenever a new version is released, I install it on the partition that I am not currently using. That way I can thoroughly test the new version and make sure it is compatable with all my hardware before I totally commit to it. You seem to have plenty of disk space to do that if it interests you.

In any case, you will need to boot from a Live CD to make any changes to partitions. Partitions need to be unmounted (not in use) to be resized or deleted.

And lastly, you might get more responses by starting your own thread instead of tacking on to a thread that has been solved.

---

