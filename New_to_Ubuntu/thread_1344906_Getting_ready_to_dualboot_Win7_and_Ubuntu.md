---
title: "Getting ready to dualboot Win7 and Ubuntu"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by pyrofyr on 2009-12-03
Hi, I'm getting ready to dualboot Windows 7 and Ubuntu, I currently have Vista installed.

My current setup is 2x 1TB HDD. I plan on using Windows 7 only lightly for when I want to play a game or some other silly thing, but really getting into Ubuntu overall, as I had tried previously.

I'm wondering how I should set these up and if there are any specific things that need to be done (new partition for Ubuntu or should it go over Vista and then install 7?) I remember a few issues about installing Windows after GRUB and messing it up, but I've also heard some things about certain OSes have to go 'first' on the disc.

Sidequestion: If I plan on using both about how much space should I give Ubuntu's partition?

---

### Post by pablolie on 2009-12-03
> **pyrofyr said:**
> Hi, I'm getting ready to dualboot Windows 7 and Ubuntu, I currently have Vista installed.

My current setup is 2x 1TB HDD. I plan on using Windows 7 only lightly for when I want to play a game or some other silly thing, but really getting into Ubuntu overall, as I had tried previously.

I'm wondering how I should set these up and if there are any specific things that need to be done (new partition for Ubuntu or should it go over Vista and then install 7?) I remember a few issues about installing Windows after GRUB and messing it up, but I've also heard some things about certain OSes have to go 'first' on the disc.

Sidequestion: If I plan on using both about how much space should I give Ubuntu's partition?

With Windows 7 and Ubuntu 9.10, my best dual boot experience came from 
(a) install Win 7 first
(b) use the Win 7 disk management software to resize the Win 7 partition and free up room for the Ubuntu 9.10 partition
(c) Replace Windows bootloader with EasyBCD version 2 (which is a very stable beta that handles Grub 2 very well)
(d) Boot into Win 7 and make sure this works well
(e) Install Ubuntu 9.10 into its own partition
(e-bis) IMPORTANT - write down the id of the main partition Ubuntu 9.10 is being installed to... (sda whatever etc)
(f) when the install disk offers to wipe out Win bootloader and replace it with Grub on the MBR, politely decline. What you truly want to do is install Grub 2 on the Ubuntu partition itself.
(g) Boot into Win 7, open EasyBCD, and include Grub 2 in the list of available options.

This worked the best for me. I initially would lose the ability to boot into Win 7 or Ubuntu 9.10 when trying the "traditional" Grub 2 method.

---

### Post by Space-Wolf on 2009-12-03
Sounds like Pablolie has it figured out quite well, but for the record I did everything he said minus the EasyBCD thing and everything still works fine.

---

### Post by jrrader on 2009-12-03
> **pablolie said:**
> With Windows 7 and Ubuntu 9.10, my best dual boot experience came from 
(a) install Win 7 first
[b](b) use the Win 7 disk management software to resize the Win 7 partition and free up room for the Ubuntu 9.10 partition
(c) Replace Windows bootloader with EasyBCD version 2 (which is a very stable beta that handles Grub 2 very well)[/b]
(d) Boot into Win 7 and make sure this works well
(e) Install Ubuntu 9.10 into its own partition
(e-bis) IMPORTANT - write down the id of the main partition Ubuntu 9.10 is being installed to... (sda whatever etc)
(f) when the install disk offers to wipe out Win bootloader and replace it with Grub on the MBR, politely decline. What you truly want to do is install Grub 2 on the Ubuntu partition itself.
(g) Boot into Win 7, open EasyBCD, and include Grub 2 in the list of available options.

This worked the best for me. I initially would lose the ability to boot into Win 7 or Ubuntu 9.10 when trying the "traditional" Grub 2 method.

I don't really have a problem with this method other than: 
(b) you might as well set up a better functioning partition scheme with gparted before beginning - the resizing of win7 or vista after an install is convenient for an install you are looking to preserve but he is basically doing a fresh install.  Make at least 4 partitions -  1 for ubuntu's root(/)(between 15 and 20 gigs will give you plenty or room), 1 for ubuntu's /home, 1 for Windows 7, and 1 for swap.  Do a google search for "linux partition scheme" for more details.
(c) grub2 has no problem booting windows7.  I don't see why this step is needed.  If he is primarily using ubuntu, grub2, and allowing ubuntu to write its mbr to sda, would be a better choice.

---

### Post by Rodemire on 2009-12-03
I agree with jrrader. Installing Win 7 then Ubuntu is not a problem, Grub2 works fine as is without the use of an additional bootloader.

---

### Post by Merk42 on 2009-12-03
If the whole MBR and GRUB thing is confusing. Think of it this way.  Which would you rather control which OS you boot into?
MBR is Windows, making it easier to eventually go to a complete 100% Windows environment
GRUB is Ubuntu*, making it easier to eventually go to a complete 100% Ubuntu* environment.


*yes GRUB is used in other Linux distributions, but for the sake of this scenario I'm saying Ubuntu

---

### Post by pyrofyr on 2009-12-03
In that case I'd much rather GRUB. I'll give tat linux partition scheme stuff a look over while I try and find a blank dvd/cd to install on.

---

### Post by pyrofyr on 2009-12-03
Ah, I know this seems like a silly question but. 

After reading into partition schemes they all say that GRUB needs the first 32MB on the disc, how would I go about setting that up?

---

### Post by oldfred on 2009-12-03
The only time I have seen any mention of grub needing space is if you want a grub only partition for booting. Only for those with many operating systems, not required for a normal dual boot. 

I have always liked the idea of an operating system on each drive and that operating system's boot in that drives MBR. Or windows on one drive that boots just windows and Ubuntu on the other drive. Since grub/ubuntu make it easy to boot other systems and windows does not, I make the Ubuntu drive the boot drive in BIOS. Grub will find the windows install and allow you to boot.

If you install Win7 and still have Vista it will combine the boot of both into the windows with the boot flag on. That way from windows you can choose which to boot. But if you want to directly boot from grub to either windows there is a work around. Both windows have to be in primary partitions:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Install windows, set up partitions for Ubuntu, boot windows to make sure it still boots ok, then install Ubuntu using manual install where you choose the partitions. If you have changed windows partitions and install Ubuntu directly, you probably have to run the windows repair fixboot, fixmbr and that overwrites grub, so then you have to reinstall grub.

---

### Post by jrrader on 2009-12-03
These are just my opinions, do don't take any of this as something you have to do.  My partitions are kind of messed up on my main HD because I did it before I knew what I was doing, with my /boot located at the back end of the drive, but it still works.  On every other computer I've set Linux + Windows on I do it this way (notice that this is more than I told you to do): 

(I made this for a classmate a while back when he asked) ```

|_.5GB_|__4GB__|__10GB__|___15GB___|___30GB___|___30GB___|___REST___|
|_sda1_|__sda2_|__sda3__|___sda4___|___sda5___|___sda6___|___sda7___|
```
Where the first 3 are primary partitions and then 4 through 7 are logical partitions within an extension. sda1 would get /boot. sda2 would get swapspace, sda3 would get root (/), sda4 would get /usr, sda5 gets /home, sda6 gets windows7, and sda7 acts as a shared storage space.  I'm not sure if I have swap in the best location, and not everyone really needs to do all this.  Others will say only to put 1 OS on a HDD, but I have no problem doing 2 or 3 on each HDD.

---

### Post by pyrofyr on 2009-12-03
It won't let me install windows to anything but a logical drive, swap can be placed inside the extended in place of win7?

---

### Post by kansasnoob on 2009-12-03
> **pyrofyr said:**
> It won't let me install windows to anything but a logical drive, swap can be placed inside the extended in place of win7?

That would be horrible! Seriously!

You need to boot a Live CD and run the command:

```
sudo fdisk-l
```

Something that I find confusing however is that I thought you were going to clean install everything so I'm baffled!

They don't have an icon of a guy running off the top of a tall building, sorry.

---

### Post by pyrofyr on 2009-12-03
I am clean installing, and that's my bad I mean Windows 7 on Primary, whereas inside the extended partition (jrrader mentioned) it would be logical.

Also when opening the Windows 7 installer it counts boot, root, and swap as primary and won't let me have anymore.

EDIT: I've been searching schemes this whole time and I either end up with posts where people just tell others "Hey just run a virtual machine!", "Run them on 2 discs (I can do this but I'd rather not)", or they just go on and on about some other crap.


EDIT2: Yes I'm doing this completely from scratch. I've already wiped vista completely and am typing all of this from the liveCD. I have access via my laptop and phone so it's not a big problem to get it resolved today, but the sooner the better.

After running sudo fdisk -l
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98a898a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          64      514048+  83  Linux
/dev/sda2              65         587     4200997+  82  Linux swap / Solaris
/dev/sda3           31871      121601   720758784    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda4             588        3137    20482875   83  Linux
/dev/sda5           31872       33783    15358140   83  Linux
/dev/sda6           33784       38882    40957686   83  Linux
/dev/sda7           51631      121600   562033993+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25161fd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121109   972800000    7  HPFS/NTFS


---

### Post by Miljet on 2009-12-03
Hate to tell you this, but jrrader's logic is flawed. It is quite impossible to set up the partitions that he has suggested.

Sda1, sda2, and sda3 will work as he said. But sda4 must then be an extended partition that contains the rest of the partitions. The size of sda4 would then be the total of sda5, sda6 and sda7. And you can't put /user, or anything else in sda4. It can contain ONLY other logical partitions.

There is absolutely no reason to have a separate boot partition unless you are playing around with several different Linux distributions at the same time. And you are quite right, Windows likes to be on a primary partition, preferably the first one.

If it were me, I would install Win7 on the first primary partition (sda1 - 20GB), Ubuntu / on the second primary partition (sda2 - 20GB), /home on the third primary prtition (sda3 - whatever size you want. Sda4 would be an extended partition that uses the rest of the disk. Then swap on sda5 - 4GB and the rest of the disk for sda6 for data. Please note that sda5 and sda6 are created inside sda4.

Hope that clarifies things a bit.

---

### Post by pyrofyr on 2009-12-03
Thank you, rebooting to do that now.

---

### Post by Miljet on 2009-12-03
You are quite welcome.

I'll be signing off for tonight, but will check back in the morning to see how it worked for you.

Good luck!

---

### Post by pyrofyr on 2009-12-03
Only one little issue popped up which I'm assuming is minor (Especially because I won't be using the partition for quite some time)

The storage partition is showing up as Primary Partition in Windows 7 and won't let me do anything with it unless I delete it.
(Now installing Ubuntu for the dualboot)

EDIT: Was able to fix that issue as well (I actually accidentally made that one ext3, changed it to NTFS and all is wonderful)

---

### Post by Miljet on 2009-12-04
Great! Glad to hear that you got everything worked out. Enjoy Ubuntu.

---

### Post by pablolie on 2009-12-04
> **jrrader said:**
> I don't really have a problem with this method other than: 
(b) you might as well set up a better functioning partition scheme with gparted before beginning - the resizing of win7 or vista after an install is convenient for an install you are looking to preserve but he is basically doing a fresh install.  Make at least 4 partitions -  1 for ubuntu's root(/)(between 15 and 20 gigs will give you plenty or room), 1 for ubuntu's /home, 1 for Windows 7, and 1 for swap.  Do a google search for "linux partition scheme" for more details.
(c) grub2 has no problem booting windows7.  I don't see why this step is needed.  If he is primarily using ubuntu, grub2, and allowing ubuntu to write its mbr to sda, would be a better choice.

And I agree with that.

I should note that for whatever reason when I let Grub2 discover and try to manage my Win 7 partition, I lost the ability to get to Win 7 altogether. Which had never happened to me before, Gru b had been very reliable in managing the boot process into the different OS, but it did not happen when I went for a clean Win7 and U9.10 install. 

That is the only reason I am using EasyBCD. And based on the discussions I have followed, I was not the only one that experienced the issue.

---

