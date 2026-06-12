---
title: "Removing linux kernels from computer"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by lfpc2009 on 2010-01-09
Dear friends,
 
I have Windows Xp, Fedora 11 and Ubuntu as boot options in my computer. Could you please tell me how to can I remove Fedora 11 and keep both Windows XP and Ubuntu?
 
I'm quite new in linux and i'm still not very comfortable with giving up Windows right now.
 
Thanks for your help.

---

### Post by tom.swartz07 on 2010-01-10
> **lfpc2009 said:**
> Dear friends,
 
I have Windows Xp, Fedora 11 and Ubuntu as boot options in my computer. Could you please tell me how to can I remove Fedora 11 and keep both Windows XP and Ubuntu?
 
I'm quite new in linux and i'm still not very comfortable with giving up Windows right now.
 
Thanks for your help.

Hiya,

This is really easy to do, but its slightly tricky.

Two things to get us started.
could you open a terminal (applications>accessories>terminal) and post the output of 
```
sudo fdisk -l
```
here?

While you do that, could you get a LiveCD of Ubuntu ready? You could use the same cd you used to install ubuntu, if you still have it.
Boot into that and post back, then we could get started!

---

### Post by tom.swartz07 on 2010-01-10
Im going to give a rough outline of what you need to do...
**_A) Boot to LiveCD_**
Boot into the LiveCD- when you first turn your computer on you could select this, you usually have to hit F12, ESC, or some other key (the keys vary from computer to computer). Boot to your cd, Select 'try without making changes'

**_B) Look at fdisk and analyze your drive_**
Now, we will look at your fdisk output. 

Generally, this is what it will look like: 
(I will use my drive as an example)
```
tom@ubuntu-karmic:~$ sudo fdisk -l
[sudo] password for tom: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       11904    85064175    7  HPFS/NTFS
/dev/sda4           11905       38913   216949792+   f  W95 Ext'd (LBA)
/dev/sda5           19233       19558     2618595   dd  Unknown
/dev/sda6           11905       18723    54773554+  83  Linux
/dev/sda7           18724       19232     4088511   82  Linux swap / Solaris
/dev/sda8           22979       24571    12795741   83  Linux
/dev/sda9           24572       36181    93257293+   7  HPFS/NTFS

Partition table entries are not in disk order
tom@ubuntu-karmic:~$ 
```

You need to do some surveying to determine what partition is what. **THIS IS A VERY CRITICAL STEP.** Generally, you could guess what partition is the one you need by 
1) the name (linux or NTFS) 
or 
2) the size of the partition

**_C) Using gParted_**
Once you determine the partition, you could open gParted from the panel (System>administration>gParted)
Select the partition you would like to delete. AGAIN, I cannot stress this enough, IT IS VERY IMPORTANT YOU KNOW WHAT PARTITION IT IS. Click it and then select the circle with the line (\). **This will delete the partition and all of its data**
If you want to resize from there, its up to you. Just remember, one thing at a time, and be very cautious- you can lose your data.

**_D) Update your Bootloader_**
Now all thats left to do is update your bootloader. Grub 2 is the default for Ubuntu 9.10.

Go to applications, Accessories, Terminal.

type
```
sudo mount /dev/sd** /mnt
``` Where ** is the partitions you see in your fdisk -l output. (usually its SDA-some number)
Repeat for all of the partitions on your drive with OS's on them
```
sudo mount /dev/sd** /mnt
```

Next, we will install Grub to reflect the changes made to your drive.
```
sudo grub-install --root-directory=/mnt/ /dev/sd*
``` Again, the * is either a or b 

And thats it!


If you need further assistance, something explained, or are just generally unsure about something, ask! Im sure I, or someone else, will be able to help you along.

---

### Post by lfpc2009 on 2010-01-10
Thanks for your help. I'll try to follow your instructions and hope I don't mess up!

---

### Post by lfpc2009 on 2010-01-10
I This is what I got from fdisk:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f205f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30720000    7  HPFS/NTFS
/dev/sda2            3825        9276    43784192   83  Linux
/dev/sda3            9602        9729     1024000   82  Linux swap / Solaris
/dev/sda4            9277        9601     2610562+   5  Extended
/dev/sda5            9277        9579     2433816   83  Linux
/dev/sda6            9580        9601      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order


The problem is I don't know which partition corresponds to Fedora, which is the one I want to delete.
I only know that after having installed Windows, I installed Fedora. Than I realized that Fedora wasn't the distro I needed and installed Ubuntu side by side with all the other OS.
I don't have any valuable data in the computer right now, since I just started with it yesterday. So, if there is a way of reinstalling Linux in the correct manner, that will also do. Anyway, I guess that the partition correspondent to Fedora should be sda2 and swap sda3.

---

### Post by lfpc2009 on 2010-01-10
I'm sorry for my delays in posting but I've been away from my computer.

---

### Post by lfpc2009 on 2010-01-10
I don't have gParted in my administration menu. The worse is that I don't have any available disk space to install any applications at all.

---

### Post by lfpc2009 on 2010-01-10
As I mentioned before, I don't have any data in my computer that I would need to keep. So maybe it is better to proceed with the reinstallation of Ubuntu from scratch. I already tried to do that, but when the Partition menu appears during the installation process, I get stuck with how to format and delete older partitions in order to install ubuntu using all available disk space, but keeping Windows.

I'm sorry to be such a "pain in the ***" but my lack of knowledge in this area is quite embarassing.

---

### Post by tom.swartz07 on 2010-01-10
> **lfpc2009 said:**
> I don't have gParted in my administration menu. The worse is that I don't have any available disk space to install any applications at all.

Youre running in LiveCd mode, correct? When you 'install' it, it just writes the program data to your RAM. The only problem would be if you didnt have a lot of RAM....

If you installed the OS's in the order you said, Windows, Fedora, Ubuntu, then Fedora is SDA2 and 3.

You could delete those, and then use the mount commands for SDA1 SDA4 and SDA5.


Dont forget- you could move your partition back over to give Ubuntu more space. Move the extended partition first (the box around ubuntu and its swap) so that it touches your Windows partition, then you could extend your Ubuntu partition after thats applied.


Good luck! post back if you have any problems

---

### Post by tom.swartz07 on 2010-01-10
> **lfpc2009 said:**
> As I mentioned before, I don't have any data in my computer that I would need to keep. So maybe it is better to proceed with the reinstallation of Ubuntu from scratch. I already tried to do that, but when the Partition menu appears during the installation process, I get stuck with how to format and delete older partitions in order to install ubuntu using all available disk space, but keeping Windows.

I'm sorry to be such a "pain in the ***" but my lack of knowledge in this area is quite embarassing.

Its okay! no need to be embarrassed! everyone starts there sometime! :D

If you really want to remove all partitions, you could do that from the installer menu. Just select "advanced manual partitioning" This will allow you to delete the other partitions, all but windows.

Here is how I would set it up.
**Windows Partition**
**Partition marked as '/'** for your data (NO SMALLER THAN 2GB- but be generous- this is where all of your programs are installed)
**Partition marked as '/home'**- this will store all of your data in case you want to change Ubuntu versions, etc. Make this the as much space as you can.


I would suggest this website: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
It helps walk you through the install process.

Good Luck! Sorry you had to go through so much junk to get to what you wanted!

---

### Post by lfpc2009 on 2010-01-10
Thanks for staying with me in this quest.
In the "advanced manual partitioning" how do I set linux partitions to be deleted and replaced by the new Ubuntu installation?
I presume I don't have to do anything concerning the Windows partition, am I right?

---

### Post by tom.swartz07 on 2010-01-10
> **lfpc2009 said:**
> Thanks for staying with me in this quest.
In the "advanced manual partitioning" how do I set linux partitions to be deleted and replaced by the new Ubuntu installation?
I presume I don't have to do anything concerning the Windows partition, am I right?

Correct.
You could just click them and hit "format" or "remove".
This page explains it a bit better than I can, and in less time: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Hope this helps!

---

### Post by albert s on 2010-01-10
your windows partition should be NTFS (I think)
the rest should be ext__ something
when i did my install i used 
10G to 15G for /
1G for swap , or the same as your RAM (I only have 512M of RAM)
and the remainder for /home

---

