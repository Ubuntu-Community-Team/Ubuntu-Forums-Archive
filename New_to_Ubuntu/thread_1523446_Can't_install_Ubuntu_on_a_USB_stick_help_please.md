---
title: "Can't install Ubuntu on a USB stick help please"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by drillerccg on 2010-07-03
I don't need a live USB, I want to install a full version on a 16GB USB stick I have. I was told by someone on this forum to partition to 4 different partitions:

8GB FAT32 for Windows 
4GB EXT4 for /
3 GB EXT2 for /home (to make future backups easy
1GB swap

I have used fdisk, Gparted, the partition program during the install but can't get past setting the EXT4 on the USB. I have even tried to install it on one partition (15GB EXT4 and 1 GB swap) by choosing the erase the hole thing and use the whol edrive. I had taken the hard drive out of my laptop and used the USB stick as the only attached storage device.

As soon as I  boot the computer from the live CD and try to full install a full copy on the stick, it stalls and says that it was unable to set partition table EXT4. It doesn't matter if I start from a FAT32 stick or format it in gParted or Fdisk to have an EXT4. Any idea?

---

### Post by josephellengar on 2010-07-03
> **drillerccg said:**
> I don't need a live USB, I want to install a full version on a 16GB USB stick I have. I was told by someone on this forum to partition to 4 different partitions:

8GB FAT32 for Windows 
4GB EXT4 for /
3 GB EXT2 for /home (to make future backups easy
1GB swap

I have used fdisk, Gparted, the partition program during the install but can't get past setting the EXT4 on the USB. I have even tried to install it on one partition (15GB EXT4 and 1 GB swap) by choosing the erase the hole thing and use the whol edrive. I had taken the hard drive out of my laptop and used the USB stick as the only attached storage device.

As soon as I  boot the computer from the live CD and try to full install a full copy on the stick, it stalls and says that it was unable to set partition table EXT4. It doesn't matter if I start from a FAT32 stick or format it in gParted or Fdisk to have an EXT4. Any idea?

I'm not sure if this is accurate, but based on what I have heard, some media is incompatible with some filesystems.  In fact, seagate would not repair a drive under warranty a few years ago because I had formatted it to extfs.  Perhaps your problem has something to do with that?

---

### Post by drillerccg on 2010-07-03
I'm starting to think the same since I have tried everything. It appears that ext4 or ext3 is problematic with this stick. I however was able to create a persistent USB with it and have a liveUSB out of it. So it's still confusing. 

I was succesful in creating this:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

but can't install a full copy on the USB. Anyone knows of a good USB tat this can be accomplished with? I bought this one off of Ebay for cheap.

---

### Post by josephellengar on 2010-07-03
I just remembered this.  Try this tutorial: [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/) using the casper persistence script.  You'll boot from an iso every time but the persistence creates something that can always be mounted as /home so most changes will roll over.  It uses a FAT filesystem (I believe) which is likely what your stick came with originally.

---

### Post by warfacegod on 2010-07-03
Try making your ext4 partition into ext3. If you were able to have a persistence file then ext3 should be working on that jump drive. That FAT32 partition might be better in the "back" of the drive. Frankly, I doubt you'll need a swap partition but I could be wrong.

---

### Post by josephellengar on 2010-07-03
> **warfacegod said:**
> Try making your ext4 partition into ext3. If you were able to have a persistence file then ext3 should be working on that jump drive. That FAT32 partition might be better in the "back" of the drive. Frankly, I doubt you'll need a swap partition but I could be wrong.

Some programs swap automatically, so it might be better to have a 500mb swap partition than none at all.  It kind of depends on what programs are installed on the drive.

---

### Post by warfacegod on 2010-07-03
I have had no swap for over a year and never needed it. In fact my laptop is a little faster for it. As far as I know the only real need for swap nowadays is video encoding and such and for Hibernating. Unless a computer has under 1 GB or so of RAM, something of an oversimplification, I admit, but I can't really think of any other reasons to have swap.

---

### Post by josephellengar on 2010-07-03
> **warfacegod said:**
> I have had no swap for over a year and never needed it. In fact my laptop is a little faster for it. As far as I know the only real need for swap nowadays is video encoding and such and for Hibernating. Unless a computer has under 1 GB or so of RAM, something of an oversimplification, I admit, but I can't really think of any other reasons to have swap.

I've got a computer with 8gb of ram.  I have a 12gb swap partition.  I *never* use all of my ram even though I have several directories mounted on ramdisks as tempfs, but I do occasionally see 1 or 2 mb of my swap space used.  Because my ram is never fully used, I'm pretty sure that I have something running that goes to swap automatically.  I have no idea what it is, but I just suspect.  Anyway, I guess these days swap is a matter of opinion.  I read several articles on the matter when I set up the computer and just decided to make a partition because I had extra disk space that I would never use and figured that it was safer that way.  For a persistent livecd- I guess you aren't likely to be doing anything that needs it.

---

### Post by warfacegod on 2010-07-03
My swap did the same thing. Occasionally hitting a MB or two. Once I even saw it spike up to 150 MB. With no swap, all of that goes to RAM. If it didn't, my laptop would be crashing all the time.

---

### Post by drillerccg on 2010-07-04
> **rossholley said:**
> I just remembered this.  Try this tutorial: [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/) using the casper persistence script.  You'll boot from an iso every time but the persistence creates something that can always be mounted as /home so most changes will roll over.  It uses a FAT filesystem (I believe) which is likely what your stick came with originally.

Yes I have done that ut I need an installation that can be updated through the update manager. I assume if I don't install any specific hardware driver I could boot any computer up and transfer files. 

My ultimate goal is to have those 4 partitions but can't seem to be able to install / or EXT4 on this USB stick. Any suggestions people?

---

### Post by drillerccg on 2010-07-04
> **warfacegod said:**
> Try making your ext4 partition into ext3. If you were able to have a persistence file then ext3 should be working on that jump drive. That FAT32 partition might be better in the "back" of the drive. Frankly, I doubt you'll need a swap partition but I could be wrong.

How do you make the EXT4 inside EXT3?

The reason I have the FAT 32 upfront is that I was told Windows can only see the first partition. This way I can reserve some of the storage for Windows if needed. I'm not even worrying about that though. I want to be able to get a Ubuntu USB going and then worry about the rest. I seems that I may be missing something here. I should be able to install an EXT4 on the drive.

---

### Post by warfacegod on 2010-07-04
> **drillerccg said:**
> How do you make the EXT4 inside EXT3?

The reason I have the FAT 32 upfront is that I was told Windows can only see the first partition. This way I can reserve some of the storage for Windows if needed. I'm not even worrying about that though. I want to be able to get a Ubuntu USB going and then worry about the rest. I seems that I may be missing something here. I should be able to install an EXT4 on the drive.

I mean format the ext4 into ext3. As in change it to ext3 and see if that works. Persistence Files are ext3 and you said you had one already that worked so you know that file system works.

---

### Post by drillerccg on 2010-07-04
> **warfacegod said:**
> I mean format the ext4 into ext3. As in change it to ext3 and see if that works. Persistence Files are ext3 and you said you had one already that worked so you know that file system works.

none of the EXT 4, 3, or 2 work. It ets stuck when it wants to install /. I am downloading 8.04 and 9.10 Ubuntu to see if this is a Lucid problem or not.

---

### Post by drillerccg on 2010-07-06
Solved, sort of: I'll post here in case another newbie is trying to do the same. Do at your own risk, I'm a newbie.

I bought this cheap ($15) 16GB USB pendrive off of Ebay and thought it would be cool to have Ubuntu installed on it so I can boot other computers; but still be able to use most of the drive to transfer files between Linux and Windows environment.

Ubuntu gave me a lot of problems partitioning the drive as discussed in this thread. Then someone on another forum suggested  that Ubuntu is not even a good candidate for this due to it's extensive footprint and to use Puppy Linux. The latest version 5.0.1 "is built from Ubuntu Lucid Lynx binary packages" so I thought it may be the best of both worlds.

Here is what I did:
1- Downloaded the Puppy iso and burned on CD as an image (not data disc)
2- Disconnected the hard drive on the laptop and booted from the CD
3- do not plug the drive in yet
4- pick the keyboard, language and time zone
5- Pick resolution, I picked 1280x800 for my 14 inch Dell 620 and chose what was suggested
6- Once the OS is up plug in the drive
7- go to menu/system/gParted
8-unmount the USB drive and delete all the partitions
9-click apply  (top green check mark)
10- right click on the drive and click new
11-leave everything as is except the file system, change that to FAT32
12- Click Add and Apply
13- When done, right click on the drive and click manage flags and check boot for it
14- close Gparted
15- now got to menu/setup/puppy universal installer
16- click OK to the defaults for a few windows
17- when the window for installation comes up, click on the button at the top to install puppy on the sdx1. It gives you the option to start gParted in the lower section and partition the drive but you have already done it.
18- click OK to default chosen options and pick the CD to find the files
19- once done the CD pops out, take it out
20- now go to menu and shut down
21- before the computer shuts down it asks you to save to file
22- chose it, I think this is the persistent option to save your changes in that session (not sure but makes sense)
23- click OK again to defaults
24- I chose EXT2 when given the option for the file
25- I also gave it a name when asked so I could locate the file easily
26- I also used heavy encryption and chose a password in case I lose the USB drive
27- also used the maximum that was given (1.25GB) for the file, I read somewhere not to exceed 1.8GB (later you have an option from one of  the menu items to increase the size)
28- Now press SAVE/ENTER only once. I did it twice by accident and it would not boot. I had to start all over again. It does take a while so be patient and don't press any buttons.
29- Once it's done, the computer shuts down.

That's it. I can boot from the USB and save my session with security. I can also plug the drive into a Windows Machine or Linux box (Ubuntu) and use the flash drive to transfer files. I created some folders so they would be separate from Puppy files. It's pretty fast loading up. Love it.

---

