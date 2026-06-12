---
title: "Getting rid of Windows Vista entirely"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by EvanWilliams on 2010-08-18
Hello everyone,

So I'm pretty much a complete newbie to Ubuntu. Here is my situation:

The machine I am using is a 3-year old Dell Latitude D820 that came with Windows Vista Business. I have repartitioned my 100 GB hard drive to allow for 15.0 gigs to go to Ubuntu 10.04. I now find myself wanting to get rid of the Windows Vista partition entirely, devoting all the space to Ubuntu. 

I am soon getting a Windows 7 machine anyway, so I want to have a lower grade rig to learn Linux on and use the Windows 7 machine for school work until I'm more comfortable with Linux, after which I may install another distro on the Windows 7 machine to get some experience with other Linux flavors. Enough rambling though...

So, what is the easiest way to completely obliterate Windows Vista from my system and give Ubuntu the remaining space? In effect, I want to turn this machine from dual boot Vista/Ubuntu into purely Ubuntu.

---

### Post by Ms_Angel_D on 2010-08-18
Hi Evan,

The easiest way is to boot into your ubuntu live cd and from the system menu open gparted.

Select your windows partition and delete it, then apply those changes, then after that's done right click on swap and select swap off, then you'll be able to select your ubuntu partition and use the slider to expand the partition and make the ubuntu partition bigger using the free space you just created. 

This may take a while, but when it's done you'll have all your space, Make sure you turn swap back on when and then you can reboot the computer without cd.

---

### Post by EvanWilliams on 2010-08-18
Actually, nevermind, I just found out about GParted and realized how easy it is to just do:

sudo apt-get install gparted

I'm a little leery of using this program though; kinda having second thoughts about seriously mucking up my machine. If anyone has any advice on how to go about using GParted effectively to completely erase Windows, I'd be most appreciative.

---

### Post by EvanWilliams on 2010-08-18
Thanks for the advice, Ms. Angel =)

Okay so it's coming up with a number of things:

/dev/sda1, fat16, DellUtility 

Am I supposed to get rid of that too or just leave it?

/dev/sda2, NTFS, RECOVERY

This?

/dev/sda3, my Windows Partition

/dev/sda4, with two subsets, sda5 (ext4) which looks like my Linux partition, and sda6 with something called linux-swap. Can you explain these two things to me? I don't quite understand them.

---

### Post by Kazade on 2010-08-18
Evan, Make sure you back everything up before you use Gparted to alter the disk, you could quite easily lose your data.

You could probably leave the Dell recovery and utility partitions, but when you installed Ubuntu dual boot you probably overwrote the boot sector that allows access to them so they are probably just sitting there wasting space. It's up to you.

Ubuntu (well, Linux) has a swap partition which serves the same purpose as Windows' virtual memory. That's why there are two. If you delete the sda3 partition you might be able to expand the Ubuntu partition.

But, make sure your data is safe before you do anything!

---

### Post by Ms_Angel_D on 2010-08-18
Kazade has given sound advice, It's late and I'm sleepy I'm sorry I forgot to mention backing up. if you need any more help, feel free to ask away ;)

Angel

---

### Post by Pogeymanz on 2010-08-18
> **EvanWilliams said:**
> Thanks for the advice, Ms. Angel =)

Okay so it's coming up with a number of things:

/dev/sda1, fat16, DellUtility 

Am I supposed to get rid of that too or just leave it?

/dev/sda2, NTFS, RECOVERY

This?

/dev/sda3, my Windows Partition

/dev/sda4, with two subsets, sda5 (ext4) which looks like my Linux partition, and sda6 with something called linux-swap. Can you explain these two things to me? I don't quite understand them.

I've deleted my recovery partitions because I never plan on having to use them. I'll just pop in my Linux install CD if I ever need to "recover." That being said, just leave them for now. It wont hurt and they don't take up too much space.

Your Ubuntu system is installed in sda5, which is called a logical partition (I'll get to that later). And linux-swap is an area of the disk set aside for just in case you use all of your RAM while you're working on something (transcoding multimedia files, compiling big software, etc). Once your RAM is almost full, Linux will treat that partition like it is also RAM, so that you can at least get the job done. Reading/writing to the hard drive is slower than from RAM, but in a pinch it's better than nothing.

Swap is also used for suspend and hibernate functions. All of the contents of your RAM are written to the swap space and when you unsuspend/unhibernate, the data is read from swap and put back into RAM.

Now, in your partition table you have sda4 and it has two sub-partitions. This is because the PC architecture only allow for 4 real partitions. To get around this limit, we now have "primary" partitions and "logical" partitions. The primary partitions are the "real" partitions. In your case, sda 1-3 are primary and sda4 is called an "extended" partition. It is a primary partition whose sole purpose is to be divided into logical partitions so that now we can have many more partitions while your hardware still thinks you only have four.

---

### Post by mastablasta on 2010-08-18
this is quite complicted... i am sayign because i will probably do something similar. in windows you would just format the partition then with partition magic you would add it. i know because i've done it with an old nonworking Redhat.

---

### Post by takisan on 2010-08-18
I'm sure this has probably been answered, but here goes mine.
> **EvanWilliams said:**
> .../dev/sda1, fat16, DellUtility
That's up to you, If you want to have a Dell Recovery Utility on your system.
> **EvanWilliams said:**
> /dev/sda2, NTFS, RECOVERY
Windows Recovery Partition. Personally, I think it's completely useless, because it can't back up the entire Windows Partition.
> **EvanWilliams said:**
> /dev/sda3, my Windows Partition
Depends if you want to keep Windows or not
> **EvanWilliams said:**
> /dev/sda4, with two subsets, sda5 (ext4) which looks like my Linux partition, and sda6 with something called linux-swap. Can you explain these two things to me? I don't quite understand them.
The Filesystem for UNIX-based systems, instead of having a C:\ drive and a D:\ drive is instead C is / (root) and D (cdrom) is /media/cdrom. Swap is the equivalent of having a paging file on the filesystem, but it saves you the trouble of having to set up a paging file on the fs.
I'm also assuming that the Linux Partition is in a logical drive instead of a main partition. If that is true, than you'd have to do a complete reinstall if you delete all of the /dev/sda1 to dev/sda3. 

Sure hope this helps.

---

### Post by neilms on 2010-08-18
The easiest way for you is to reinstall ubuntu. The installation program will ask you if you want to devote the whole disk to Linux. It will automatically partition your disk for you.

---

### Post by pizza-is-good on 2010-08-18
> **neilms said:**
> The easiest way for you is to reinstall ubuntu. The installation program will ask you if you want to devote the whole disk to Linux. It will automatically partition your disk for you.

If that is feasible then maybe yes. Go for it. But it shouldn't be any different than deleting the windows partition. And it makes you feel more accomplished to completely change all the partitions than to just install an OS again.:lolflag:

Do this for me. Type ```
sudo fdisk -l
```on your terminal and post the output to us using CODE tags. I think you gave us all the info that will give us already, but just in case.

I'll write up the GParted step by step guide when you give me that.

Please do backup! I have been messing with partitions for LONG time and I have never lost any data, but the possibility is always there.

As for the dell recovery partition, I would personally leave it. If you ever decide you want to reinstall Vista (not likely by what you said in your post), it might come in handy. Up to you.

~pizza

---

### Post by EvanWilliams on 2010-08-18
Thank you everyone for your help.

If I have to reinstall Ubuntu, that's not a big deal really. My original plan was to turn the machine into a dual boot, get Ubuntu on there and see if I like it (which I do), transfer my important docs from Windows to Ubuntu via flash drive, and finally obliterate Windows and give the rest of the space to Ubuntu. 

Pizza-is-good, as you asked, here is the output from the fdisk command:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         271     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda4           10199       12161    15767797+   5  Extended
/dev/sda5           10199       12073    15060906   83  Linux
/dev/sda6           12074       12161      706828+  82  Linux swap / Solaris

```

I should point out that at this point all I have done with GParted is deallocate the Windows Partition (what used to be sda3), assuming that I could just do "swapoff" and then be able to resize the partition. The key icon next to the swap drive disappeared, but the key icon is still there for sda4 and sda5, so I'm guessing that means I cannot resize them. Like I said, I'm not too good with partitioning yet, so I'm cautious of doing anything else until I know what everything GParted is showing me actually means.

I would just reinstall Ubuntu and be done with it, but I would like to learn more about partitioning and get some hands-on experience with it.

---

### Post by pizza-is-good on 2010-08-18
> **EvanWilliams said:**
> Thank you everyone for your help.

If I have to reinstall Ubuntu, that's not a big deal really. My original  plan was to turn the machine into a dual boot, get Ubuntu on there and  see if I like it (which I do), transfer my important docs from Windows  to Ubuntu via flash drive, and finally obliterate Windows and give the  rest of the space to Ubuntu. 

Pizza-is-good, as you asked, here is the output from the fdisk command:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         271     2097152    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda4           10199       12161    15767797+   5  Extended
/dev/sda5           10199       12073    15060906   83  Linux
/dev/sda6           12074       12161      706828+  82  Linux swap / Solaris

```I should point out that at this point all I have done with  GParted is deallocate the Windows Partition (what used to be sda3),  assuming that I could just do "swapoff" and then be able to resize the  partition. The key icon next to the swap drive disappeared, but the key  icon is still there for sda4 and sda5, so I'm guessing that means I  cannot resize them. Like I said, I'm not too good with partitioning yet,  so I'm cautious of doing anything else until I know what everything  GParted is showing me actually means.

I would just reinstall Ubuntu and be done with it, but I would like to  learn more about partitioning and get some hands-on experience with  it.

Thanks for the output of fdisk.

Well, if you want to do a reinstall, go for it. If you don't then go through the following steps.

1. Backup all your data. Just in case.

2. Boot from a LiveCD or Live USB of Ubuntu.

3. Now, open up GParded.

4.  On the right side of the GParted window, you will see a drop down menu  of all the HDD and storage devices attached to your PC. Click on it and  select the HDD you want to edit. (It will be to 100 GB one)

I  made one of my USBs look like your HDD. So, I hope I do it all right  lol. Let me know if there is anything that doesn't make sense.

5.  Now, right click on all the partitions you want to delete. It will be  /dev/sdb2 (the b is just what it is in my laptop. While it may be b in  yours as well, it may also be /dev/sda or sdc. It will most likely be b,  but just make sure it is the 100 GB HDD and you'll be OK.)

[LIST]
[*]/dev/sdb1 - This is the Dell one. I would not delete it.
[*]/dev/sdb2 - Windows Recovery partition. It is completely worthless.
[*]/dev/sdb2 - Windows partition. You said you already deleted it, and the output from fdisk agrees with that. Just in case.
[*]/dev/sdb4 - This is the extended partition. DO NOT DELETE IT.
[*]/dev/sdb5 - Your Ubuntu. DO NOT DELETE IT.
[*]/dev/sdb6 - Swap. DO NOT DELETE IT EITHER.
[/LIST]
6.  After you have told it to delete all of them, click on the green check  mark in the upper part of GParted. When you hover it, it will say "Apply  All Operations". A warning message will pop up. Click "Apply". When it  is done, click "close".

7. Right click on /dev/sdb4 on the list  of partitions (not on the graph). Click on "Resize/Move". A new window  will pop up. Click and drag the LEFT-pointing arrow on the graph in the  pop up window all the way to the left. Click on the Resize/Move button.

8. Apply the operations one again.

9.  Now right click on /dev/sdb5 on the list (not on the graph, again).  Click on resize/move. Now, click on the middle of the graph and drag it  all the way to the left. Click on resize/move. Apply the operations  again. THIS STEP WILL TAKE THE LONGEST, possibly a while, since it is  copying all the data...

10. Now, right click on /dev/sdb5 again.  Click on resize/move again. Now click and drag the RIGHT-pointing arrow  all the way to the right. Click on resize/move, and apply the operations  again. This one might take a while, but not at all as long as the  previous one.

Guess what? You are done! Reboot the PC into your normal Ubuntu and hope it works.:lolflag:

Let me know if there is anything that is not clear, or if something doesn't work.

All the best,

~pizza

---

### Post by EvanWilliams on 2010-08-18
Pizza-is-good,

I followed your instructions, and it worked like a charm. Booted from the CD that came with Ubuntu Unleashed (bought that book after trying Ubuntu under Wubi), loaded up GParted, and went to work.

I deleted the recovery partition, left my Dell Utility intact, moved Ubuntu to the left and grew it out to fill the newly unallocated space. No more Windows Vista =D

Just one question though: does it matter whether or not my ubuntu and swap partitions are real or logical? I have two real partitions now, one with the Dell Utility stuff and the other a real partition with two logical partitions, ubuntu and swap. I might be wrong though, so here is the fdisk output again:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda4              10       12161    97610940    5  Extended
/dev/sda5              10       12073    96904048+  83  Linux
/dev/sda6           12074       12161      706828+  82  Linux swap / Solaris


```

I'm just wondering if it matters at all whether it's real or logical. Or is it supposed to be logical?

---

### Post by liedan on 2010-08-18
Hi.
Same question here, is there a difference whether system is on primary or extended partition? 

btw: Ewan, from my (somehow limited,still newbie:) ) experience, I  recommend dedicating separate partion for your /home folder next time you install Ubuntu. You have to do it manualy during instalation. It is very handy if you ever need to reinstall the system, because all your basic program settings are stored in /home/$USER. Therefore, after proper reinstall, /home is untouched and your settings are safe and sound. In compare with Windows, reinstalling Ubuntu was a piece of cake:)

btw2:some more info about partitioning can be found here:

[https://help.ubuntu.com/10.04/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/10.04/installation-guide/amd64/partitioning.html)

---

### Post by pizza-is-good on 2010-08-18
> **EvanWilliams said:**
> Pizza-is-good,

I followed your instructions, and it worked like a charm. Booted from the CD that came with Ubuntu Unleashed (bought that book after trying Ubuntu under Wubi), loaded up GParted, and went to work.

I deleted the recovery partition, left my Dell Utility intact, moved Ubuntu to the left and grew it out to fill the newly unallocated space. No more Windows Vista =D

Just one question though: does it matter whether or not my ubuntu and swap partitions are real or logical? I have two real partitions now, one with the Dell Utility stuff and the other a real partition with two logical partitions, ubuntu and swap. I might be wrong though, so here is the fdisk output again:

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda4              10       12161    97610940    5  Extended
/dev/sda5              10       12073    96904048+  83  Linux
/dev/sda6           12074       12161      706828+  82  Linux swap / Solaris


```I'm just wondering if it matters at all whether it's real or logical. Or is it supposed to be logical?

I'm glad it worked! fdisk output looks real nice.

> **liedan said:**
> Hi.
Same question here, is there a difference whether system is on primary or extended partition? 

btw: Ewan, from my (somehow limited,still newbie:) ) experience, I  recommend dedicating separate partion for your /home folder next time you install Ubuntu. You have to do it manualy during instalation. It is very handy if you ever need to reinstall the system, because all your basic program settings are stored in /home/$USER. Therefore, after proper reinstall, /home is untouched and your settings are safe and sound. In compare with Windows, reinstalling Ubuntu was a piece of cake:)

btw2:some more info about partitioning can be found here:

[https://help.ubuntu.com/10.04/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/10.04/installation-guide/amd64/partitioning.html)

A separate /home is a good idea. I have not gotten around to doing it myself, but I plan to some time soon.

To answer the partition question:

PC architecture does not allow a hard drive to be split into more than 4 sections, or 4 'real' partitions. Because of this limitation, someone came up with the concept of extended partitions, which would merely act as 'cases' for more partitions. Because these partitions within partitions are not 'real' partitions, they are called logical partitions. In all honesty there is no practical difference between a real or logical.

The nice thing about the logicals is you can have as many of those as you want :D!
So don't worry about it, you will never notice a difference. Plus, think about it, don't logical partitions also get their own /dev/sdX#? You can do just as much with them as with reals.

Happy ubunting folks!

~pizza

PS EvanWilliams, don't forget to mark the thread as solved!

---

