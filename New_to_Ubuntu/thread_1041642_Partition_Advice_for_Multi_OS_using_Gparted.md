---
title: "Partition Advice for Multi OS using Gparted"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by sirhceel23 on 2009-01-16
Alright, I finally give up on searching my heart out and will finally rely on the wonderful team of people on the forums. So here is my scenario: 

I'm looking at the best way to partition the remainder of my hard drive for the systems I want to have on it. I currently have a copy of Vista on my first primary partition and its recovery info on a second primary partition giving me 2 more primaries to work with. I do have an awesome amount of space to work though so I was thinking I would create a partition for FAT32 files as the third primary and an extension on the last giving me my 4. 

So I guess what I'm getting to is what would be the best way to create the logical partitions on that extended partition. I want to run Ubuntu and openSUSE as the main Linux systems on that partition. So what I'm looking for is what kind of format and mounting points to use on each partition and what would be the best way to leave room for future OS to be installed on more logical partitions? I'm sure this would be a great place to start for most beginning users to understand how to partition and why to do each partition. I am a fairly new user to Linux systems so I would love a little explanation for what the mount points do. I would also guess that they do need to be in some sort of logical or right? Sorry to ask such a complex question! 

I have 308 GB of space to work with on the disk. 

Thanks to everyone who spends their time helping all us new users understand the systems a lot better.

---

### Post by jken146 on 2009-01-16
Don't use FAT if you can help it.  Linux handles NTFS very well and there are even Windows drivers for ext2/3 filesystems.

Give yourself about 10 GB for / (the root of each linux file system) -- this is usually fine for most distros like Ubuntu, but others will want more (lightweight distros can get away with much less and there are some heavier ones such as Sabayon which will need upwards of 15 GB).

It is easier not to share a /home partition between distros, so just keep all the files you want to share in some sort of storage partition.

Don't forget a swap partition.  Some people think putting this at the beginning or end of the drive improves performance, but for sure make it at least RAM x 1.5 but at most 1 GB.

---

### Post by Paqman on 2009-01-16
Personally to achieve what you want i'd create these partitions inside your extended:

[LIST=1]
[*]Swap partition: 1GB (or =RAM if hibernation needed)
[*]Root partition 1: 10-20GB ext3, root for first distro
[*]Root partition 2: 10-20GB ext3 root for second distro
[*]Spare partition: 10-20GB ext3 root for any other distro
[*]Home partition: ext3. Shared home for all distros.
[/LIST]

When you install the first distro specify root 1 as the mount point for /, and the home partition as the mount for /home. Then when you install the next distro, specify the second root partition as the mount point for /, and the shared home partition for that distro's /home.

Mount points are just a way of putting different parts of the filesystem into different places. For example, putting /home on a separate partition is popular because it allows you to reinstall the actual system without overwriting all the user settings that reside in /home.

---

### Post by Paqman on 2009-01-16
> **jken146 said:**
> 
It is easier not to share a /home partition between distros, so just keep all the files you want to share in some sort of storage partition.

I've been doing it for years, it's absolutely fine. Just use different usernames for each distro.

I agree about FAT32 though, it's not a very good filesystem. NTFS is much better.

---

### Post by JoshuaRL on 2009-01-16
I appreciate that you did a lot of searching, and I'd agree that there's a lot of info out there for this stuff.

It all depends on how much you plan on using the OSs.  I would suggest at least 20-30GB for each Linux OS, and a good 1-2GB swap partition.  That's like the page file for RAM overrun in windows, but a separate partition instead.  But, why would you want a FAT32 partition?  You can use ext3, and it wont have file fragmentation like FAT does. Plus, with the opensource "ext2" driver for Windows you can read/write to ext2/3 partitions.  Just remember, you can only have 4 primary partitions, and thats it.  But you can have unlimited logical partitions if you just have 3 primary partitions.

For the mount points, each Linux distro will need its own root partition, where the OS sits.  That should read in the mount point space as:
```

/

```
You can mount the same swap partition for multiple distros, so that is easy.  And as far as mounting non-root partitions in Linux, just pick somewhere you want it mounted.  For your Vista, something like the following would be good:
```

/media/Vista

```
But ultimately, its whatever you want it to be.  That's the great thing about Linux.

Welcome to Ubuntu!

---

### Post by sirhceel23 on 2009-01-16
Hmmm...Ok I see what you mean with the FAT, so as the third partition would you just use that as more of just file storage, and what kind of format for that you think? And as for the extended partition what partitions are usually the best to have for each partition for each OS, like say a /root ext 3, and /home for Ubuntu, probably the same for openSUSE, then a swap, and to leave some room for future expansion how would you leave the the remainder of the disk. Just as empty or possibly as a NTFS for temporary storage and what not.

---

### Post by Paqman on 2009-01-16
> **sirhceel23 said:**
> Hmmm...Ok I see what you mean with the FAT, so as the third partition would you just use that as more of just file storage, and what kind of format for that you think?


If you want to share the data between Win & Linux then your options are:

[LIST=1]
[*]FAT32: Both systems can read/write to this, but it has bad fragmentation issues, a fairly small max size, and doesn't like big files
[*]NTFS: Both systems can read/write to this. May need defragging in Windows occasionally.
[*]Ext2 or 3: Linux can read/write, but Windows needs special software to do so.
[/LIST]

> 
And as for the extended partition what partitions are usually the best to have for each partition for each OS, like say a /root ext 3, and /home for Ubuntu, probably the same for openSUSE, then a swap


Each distro needs it's own root partition. Swap and /home can be shared between them.

> 
and to leave some room for future expansion how would you leave the the remainder of the disk. Just as empty or possibly as a NTFS for temporary storage and what not.

Leaving it blank would be fine, or you could format it to whatever you liked. Doesn't really matter yet, as you'd usually format it if you installed an OS to it anyway.

---

### Post by sirhceel23 on 2009-01-16
OK sorry scratch that last post I was still just replying to the first reply :) Paqman's plan sounds about right for what I'm looking for. Also, in that case really all I would need instead of that third primary for file storage would be the extended using my /home partition. Now I did get a little ahead of myself with creating the extended partition. In order to do that, how should I create it? It just shows a primary and logical as the types of partitions I can create using the Gparted. Could be just because I'm using the Ubuntu install disk maybe there is way to do it from within the partitioner. As for the Swap  partition, thats fine as a logical partition right? And as for the size I currently have 3 gb of ram so would I want to equal that? I know like for windows it likes to allocate about 4-5 gb for their virtual memory. Thanks for all the responses!

---

### Post by JoshuaRL on 2009-01-16
> **Paqman said:**
> 
[LIST=1]
[*]FAT32: Both systems can read/write to this, but it has bad fragmentation issues, a fairly small max size, and doesn't like big files
[*]NTFS: Both systems can read/write to this. May need defragging in Windows occasionally.
[*]Ext2 or 3: Linux can read/write, but Windows needs special software to do so.
[/LIST]


All true, but the ext3 issue is small.  [Here is the site for the driver](http://www.fs-driver.org/) needed for Windows to read/write ext3.  Just download and install.  I have that set up on all my Windows installs.

---

### Post by sirhceel23 on 2009-01-16
Now how do I create that extended partition? Can't seem to find a a way to from the install partitioner(gparted) on the ubuntu install disk. Anybody?

---

### Post by Paqman on 2009-01-16
> **sirhceel23 said:**
> Now how do I create that extended partition? Can't seem to find a a way to from the install partitioner(gparted) on the ubuntu install disk. Anybody?

Is it not just a right click > new partition > create as > extended?

---

### Post by JoshuaRL on 2009-01-16
> **sirhceel23 said:**
> Now how do I create that extended partition? Can't seem to find a a way to from the install partitioner(gparted) on the ubuntu install disk. Anybody?

One of the options should be to select it as either a primary or extended partition.  Should be a pull-down menu if memory serves correct.

---

### Post by sirhceel23 on 2009-01-16
It gives you the option of Primary or Logical, I was looking at pull down menu and there is a "do not use this partition option" but I didn't think that was it. Went ahead and burned an actual Gparted Live CD so maybe I'll check that rather than doing it from the Ubuntu install DVD.


Edit: OK the Live CD worked great. Apparently they just don't give that option in the Ubuntu option.

---

### Post by JoshuaRL on 2009-01-16
> **sirhceel23 said:**
> It gives you the option of Primary or Logical, I was looking at pull down menu and there is a "do not use this partition option" but I didn't think that was it. Went ahead and burned an actual Gparted Live CD so maybe I'll check that rather than doing it from the Ubuntu install DVD.

No, its logical.  Sorry, I used the wrong name.  Oops.  You can have all the logical partitions you want as long as you only have 3 primaries.

---

### Post by sirhceel23 on 2009-01-16
OK just one more question and I'll have it all nailed down. Thanks for everything so far. I defined three logical's to roots, one to /home, and one as a swap. Which I thought was correct but when I go to actually install ubuntu on the first / it tells there are "Identical mount points for two file systems" so do I need to define the other two as something other than roots or something else so I can install separate OS on each one? Also, I set the Swap to 4.5Gb, is that good, or too much. I have 3 gb of ram and most said 1.5x the ram. Thanks again!

---

### Post by JoshuaRL on 2009-01-16
Only one root mount per distro, and each a different one.  The other partitions you have set out for root need to be mounted something else like:
```

/media/OpenSUSE

```
Or whatever you want.  Another option is to not mount them, the installer will ignore them and you wont be able to see them in your distro unless you mount later.

---

### Post by sirhceel23 on 2009-01-16
Oh ok, so basically just giving them a different name to differentiate, so on each install will I need to change whichever one I'm installing the OS on will I need to change it to / for that install? Sorry if I'm making this overly complicated.

---

### Post by Paqman on 2009-01-16
> **sirhceel23 said:**
> OK just one more question and I'll have it all nailed down. Thanks for everything so far. I defined three logical's to roots, one to /home, and one as a swap. Which I thought was correct but when I go to actually install ubuntu on the first / it tells there are "Identical mount points for two file systems" so do I need to define the other two as something other than roots or something else


You only need to define the root for the system you're installing. You can leave the others until you install their systems.

> 
Also, I set the Swap to 4.5Gb, is that good, or too much. I have 3 gb of ram and most said 1.5x the ram. Thanks again!

It's a bit big. 1.5xRAM is old advice. On a system with that much RAM you only need the swap to equal the RAM if you need to use hibernation. If you don't need hibernation, I wouldn't bother making it any bigger than 1GB.

---

### Post by sirhceel23 on 2009-01-17
Alright both Ubuntu and openSUSE installed flawlessly and everything is set perfectly the way I wanted it thanks to you awesome people. I just wanted to say thanks! With this kind of support around Ubuntu why would anyone ever want to use anything else? I can't wait to learn more. \\:D/

---

### Post by JoshuaRL on 2009-01-17
Welcome to Ubuntu!

---

### Post by sirhceel23 on 2009-01-17
Alright I'll ask just since I managed to mess something up :( Well I got Ubuntu and openSUSE installed on their partitions but I can't get Ubuntu to boot back up after the initial install after I installed openSUSE. When I click on Ubuntu to boot in the openSUSE bootloader program it pops up another selection screen asking which version of Ubuntu to boot up (which it contains 4 ubuntu options - 2 different kernals and safe modes and my windows vista) When I select the first ubuntu option I get:

kernal /boot/vmlinuz-2.6.27-9-generic root=UUID=d9d0d475-a8f3-4511-a06c-f457ed47bce4 ro quiet splash

Error 15: File not found

Press any key to continue..._

then when I press anything i brings me to the GRUB bootloader screen with all the ubuntu options and the windows options. None of the options work to boot in any of those options. It brings up an error 15 on all of them. Windows and openSUSE do boot up just fine from the openSUSE bootloader. SO it looks like to me, I just need to figure out a way to remove the Grub bootloader and fix the Ubuntu pathway in the openSUSE bootloader. (Sorry not sure if their is another name for it) So please, please just a little more help. I love my ubuntu!

Also if this helps at all this is what my partitions look like: Ubuntu is installed on /dev/sda6

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       22186   178207587    7  HPFS/NTFS
/dev/sda2           59655       60801     9213277+   7  HPFS/NTFS
/dev/sda3           22187       28630    51761430   83  Linux
/dev/sda4   *       28631       59654   249200280    5  Extended
/dev/sda5           28631       29204     4610623+  82  Linux swap / Solaris
/dev/sda6           29205       31762    20547103+  83  Linux
/dev/sda7           31763       34328    20611363+  83  Linux
/dev/sda8           34329       37570    26041333+  83  Linux
/dev/sda9           37571       59654   177389698+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0004ebe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16       15288     3909696    b  W95 FAT32

---

