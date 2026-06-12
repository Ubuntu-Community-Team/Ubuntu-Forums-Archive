---
title: "Live Usb Pendrive Persistent no go help please"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by drillerccg on 2010-06-24
Hi,
 
New to Ubuntu and Linux with limited Linux skills but can follow directions.
 
What I'm tryig to do: I have a 16GB generic USB pen drive I bought from Ebay/Asian country and would like to be able to Boot any computer into Ubuntu Lucid Lynx but also be able to use the rest of the USB capacity to transfer files or save updates/settings/etc from Ubuntu. I also would like to be able to use the extra space in Windows OS if needed to transfer files. In other words: 1- need to a live USB, 2- need to be able to use mass storage in Ubuntu, 3- need to use mass storage in Windows.
 
If I  use the Startup disk maker from the Adminitrator menu, I do  not get any of the capacity. I used the Gparted to make 2 different partition, one Fat16 for Ubuntu live USB and one Ext2 for mass stortage. Full of errors and gave up.
 
I then used the fdisk function in the terminal to erase all the partitions and followed the instruction [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent). It almost worked. I was able to boot into ubuntu and try it (without install), had a casper-rw drive in ubuntu as mass storage, but in Windows when I plug the drive in, I only see the Ubuntu Live fat 16 partition that does not have much of the 16GB for mass storage (original storage capacity was set to 750mb for this partition).
 
Is there a way to get all this? I tried using the alternate way in the link above but the Casper-rw does not appear. I also tried 3 partitions, one fat16, one fat 32, and one EXT2, still no o. Is this even possible? TIA

---

### Post by ubunterooster on 2010-06-24
Try one fat32 partition

---

### Post by wilee-nilee on 2010-06-24
The disc creator will build the partition for you wipe the thumb, use the install slide the persistent function all the way to the right install. Then build the fat 32 or any others after with gparted, use fat32 rather then 16

---

### Post by drillerccg on 2010-06-24
I have used fat32 but it does not show up in Ubuntu. I used fdisk and created 2 partitions. One Fat32 that I installed the iso file on and one I left as EXT2 per instruction from that page in my original post. The casper-rw for the second partition does not show up when I use fat32 for the first partition.

---

### Post by wilee-nilee on 2010-06-24
> **drillerccg said:**
> I have used fat32 but it does not show up in Ubuntu. I used fdisk and created 2 partitions. One Fat32 that I installed the iso file on and one I left as EXT2 per instruction from that page in my original post. The casper-rw for the second partition does not show up when I use fat32 for the first partition.

What distro are you using. The method your going with is outdated and not needed. Also if you wipe the thumb and make a fat32 partition it needs to be remounted to show.
I will be glad to help you with this and show you how to have a larger the 4 gig persistence if you want.

---

### Post by drillerccg on 2010-06-24
I'd love it if you show me and be as specific as possible since I'm very new to Linux. I'm using Ubuntu Lucid Lynx and am up to date. How do I wipe the thumb? I can use Gparted to delete all partitions and then make one large Fat32 which would show the who drive. Can you help please.

---

### Post by wilee-nilee on 2010-06-24
> **drillerccg said:**
> I'd love it if you show me and be as specific as possible since I'm very new to Linux. I'm using Ubuntu Lucid Lynx and am up to date. How do I wipe the thumb? I can use Gparted to delete all partitions and then make one large Fat32 which would show the who drive. Can you help please.

First use the start up disk creator in lucid.

If you want a larger then 4 gig persistent you would make a 1 gig fat32 and use the slider to create the persistent casper-rw in home by installing. It might take a little more or less then a gig to get the persistent function to work you will have to experiment a little but it wont have persistent if the slider is grayed out.

Then follow this links instructions on the 2nd ext2 named casper-rw.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

Now the persistent has limitations in that it is a squash file and will get filled up, you also can't upgrade kernels and or distros.

After you set it up in this manner if you want more then a 4 gig partition, and the etx2 is set up make a share partition of fat32 for Ubuntu or windows to read and write to.

You can just use the startup disk creator and the slider to have a stick 4 gig sized ISO install with the persistence being - the ISO or any updates and logging.

I am sending you this information running Maverick fully installed on a 16 gig thumb so there is that option as well. Although the general rule is that a full install will not boot on every computer, but it does on all three of mine. If you decide to try a full install on the thumb, you have to make sure grub is pointed at the thumb in the install, by clicking on the advanced tab in the last install window and making sur it is pointed at the mbr of the thumb. Here are a couple of screen shots 1st my fully installed thumb, second a 2 gig thumb with a iso install and a share partition.
[ATTACH]161487[/ATTACH]

This only shows the screen shot of the second one listed, I couldn't get both due to my ineptness

So the second shot has no persistent it is just a loaded daily of Maverick and the second partition has data.

---

### Post by wilee-nilee on 2010-06-24
So here is a screenshot of my 16 gig full install.
[ATTACH]161488[/ATTACH]

---

### Post by drillerccg on 2010-06-25
start up disk creator won't allow me to change anything. On te top it has the directory where the iso file is and the bottom lists sdb and sdb1 with sdb1 being 16G. I can only erase disk which results in the same option. Did you mean Gparted?

---

### Post by drillerccg on 2010-06-25
Also, I may have not been clear in my original post. I CAN create a persistent pen drive, 2 partitions. One Fat16 with Ubuntu image with 750MB, the other casper-rw with 15GB. And I can boot into ubuntu and use the casper-rw as storage. MY problem is that if I stay in windows, I only see the smaller 750MB partition. The casper-rw does not show up in Windows. That's the main problem I am trying to overcome. TIA

---

### Post by wilee-nilee on 2010-06-25
I see the casper ext2 will not show, shrink it to make another fat 16 0r fat32 for sharing . And yes this is all done from gparted.

The ext2 named casper-rw wont show in Ubuntu either except in gparted. It is a hidden partition basically.

When a long multi paragraph description is made to begin with it is hard for me to follow it at times when it is a very easy process, That can be explained in about a few sentences, my bad sorry if I misread it.

This is the part in my long winded description:) That was important
> After you set it up in this manner if you want more then a 4 gig partition, and the etx2 is set up **make a share partition of fat32 for Ubuntu or windows to read and write to.**

---

### Post by drillerccg on 2010-06-25
So let me see if I can get this right:

Partion 1 Fat16 ubuntu iso
Partition 2 Fat 16 to be seen from windows
Partition 3 casper-rw foe persistent in Ubuntu

right?

If I can't see the casper-rw in Ubuntu how can I use it when booted in Ubuntu from USB?

I appreciate all your help.

---

### Post by wilee-nilee on 2010-06-25
> **drillerccg said:**
> So let me see if I can get this right:

Partion 1 Fat16 ubuntu iso
Partition 2 Fat 16 to be seen from windows
Partition 3 casper-rw foe persistent in Ubuntu

right?

If I can't see the casper-rw in Ubuntu how can I use it when booted in Ubuntu from USB?

I appreciate all your help.

The casper-rw is used as the persistent storage it is just hidden, I know this seems weird but thats the way it works. I'm not sure about the order it probably doesn't matter but I would have the share at the end, but I set these up all the time and just have a standard way of doing things.

I think, what you think is that since your saving stuff to the thumb via having a persistent that it should be available to windows, it's not though, you have to have a plain fat16 or 32 not labeled with the casper-rw to be seen by both OS.

---

### Post by drillerccg on 2010-06-25
I think the problem is with windows. Windows can only mount one active partition, right? So if I have 3 partitions and the first one has the Ubuntu iso and is the active one, the other ones will not show up in windows. Hence I don't get any stoage capacity if in windows.

If I boot from the USB into Ubuntu, everything is OK and have whatever I put aside in casper-rw as storage. But if I'm in Windows and stick the USB in, I only see the one partition conataining the iso. This is the only active partition so we can boot from it. Is there a workaround for this? Do you have this setup at all?

been looking at this to create a loopback file but it is complicated for me and gave up

[https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence)

---

### Post by wilee-nilee on 2010-06-25
I think if you just wipe the thumb with gparted, then make a 4 gig fat32, then use the startup disk creator to load the ISO with the persistent slider all the way to the right it will work. You have to be sure to click on the partition your installing to with the creator to get the ISO pointed at it. Then with the rest of the thumb make a regular fat32 partition in gparted this works for me every time. I would try this method, you don't need more persistence then the amount allowed by the creator.

Not every thumb works though, you also got it off ebay, I got mine from Amazon and it is a Kingston Digital Traveler, you might have a fake thumb or one that just doesn't work. If the thumb will not show a fat32 partition in Ubuntu if I read this correctly that is strange. I may have read your posts incorrectly though.

Windows will only boot a active partition, it will mount any that are readable by Windows.

---

### Post by drillerccg on 2010-06-25
hmmmm, I will try what you said next. The pen drive is fine. If I format the whole thing in Fat32, it is read by both Windows and Linux.

I maybe confused about the casper-rw though. Is this a partition for me to store anything on? 

This last partition I made was:

1- Fat16 with ubuntu iso, 750MB
2- casper-rw, 9 GB
3- Fat 32 to be read by windows, 6GB

These were the results:

1-In Ubuntu installed on my hard drive, nothing gets mounted
2-In windows, I only get the 750MB active partition that has 47mb free
3-In Ubuntu that is booted from the pen drive (windows originally), I get a casper-rw with 9GB but can't use the storage (no copying files into it), I get a file system that has 475mb free, and I get the hard drive that had the windows on

Still can not use most of the 16GB to transfer files in anything. Frustrating...

---

### Post by C.S.Cameron on 2010-06-25
Windows can only see the first partition on a USB flash drive and then only if the partition is FAT or NTFS.
If you want to store stuff from a Windows machine you will have to store it in the first partition.


You can access stuff stored from a Windows machine when booted from the flash drive by going to /filesystem/cdrom

---

### Post by drillerccg on 2010-06-25
@C.S.Cameron : The problem I have is how to get some of that 16GB available in the first partition that contains the Ubuntu iso and gets booted from? If I format it as fat16 everyting works but I can only get a few hundred MB. If I format as fat32, not much more can be used in Windows.

---

### Post by C.S.Cameron on 2010-06-25
I'm not sure what you mean?
If you partition the drive, (let's call it sdb), so sdb1 is 10GB of FAT32 and sdb2 is 6GB ext2, (Labeled casper-rw), then Windows (and Ubuntu), should have 10GB - 0.75GB = 9.25GB, (0.75GB for the file system), of storage space on the first partition and Ubuntu should have approximately 6GB of persistence space on the second partition.

When in Ubuntu you need to go to filesystem/cdrom to access the stored files.

---

### Post by drillerccg on 2010-06-25
Can I use the persistence space to transfer files?
Thanks for the help, I did not know about the filesystem/cdrom, going to try it now.

I was trying to partition the 16GB stick into two Fat32 partitions of 8GB, one would contain the iso and the other to be available in both windows and ubuntu for file transfer. But could not do it. Gparted has a triangle with an exclamation mark in it in the second one. I gave up. Will do your suggestion now and will report shortly. Thanks

I'm using this command to format to fat 32 in terminal 
sudo mkfs.vfat -F 32 -n ubuntu /dev/sdX1

is that OK?

---

### Post by drillerccg on 2010-06-25
Ok I think I'm almost there. Gparted was wortless. I used the instruction in this page (Method 3)  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
 
and partitioned and formatted the pendrive into:
 
sdb1 Fat32, 8GB, Live ubuntu installed on it using the startup diskmaker in Lucid
sdb2 Ext2 casper-rw, 8GB
 
In windows, I have 7GB+ for storage in sdb1
In Ubunti I have 7GB+ for storage in filesystem/cdrom/casper folder
That solves most of my problems thanks.
 
The only problem is that, if I go to update throgh update manager whenI have booted from the pendrive into ubuntu, it tells me that I do not have enough space to install all the updates. I thought Persistent meant that I could update Lucid and the extras would go to the Casper folder. Excuse my ignorance, very noew to Linux and am trying to learn. Thanks

---

### Post by C.S.Cameron on 2010-06-25
I usually use gparted for partitioning but your method seems to be working.

Windows will only be able to see the first FAT32 partition, no problem if your file system lives there also, just make a folder for Windows stuff.

You will only be able to access the second folder while booted from Linux.
Casper-rw partitions are not accessible as partitions while booted from the Live drive but you can save stuff to your home folder which will live in this partition.

Make these partitions whatever size you like you can always adjust them later.

---

### Post by drillerccg on 2010-06-26
> **C.S.Cameron said:**
> I usually use gparted for partitioning but your method seems to be working.

Windows will only be able to see the first FAT32 partition, no problem if your file system lives there also, just make a folder for Windows stuff.

You will only be able to access the second folder while booted from Linux.
Casper-rw partitions are not accessible as partitions while booted from the Live drive but you can save stuff to your home folder which will live in this partition.

Make these partitions whatever size you like you can always adjust them later.

Thank you for all your help. 2 questions to clear things up:

1- If I'm booted from the live USB I made this way, How can I run the update manager to update my live USB stick and save it for my next session? Is that possible? Right now it isn't, it says not enough room although my casper folder in the filesystem/cdrom is 7 gig.

2- How can I change the size as you mentioned above? In the CDrom folder I have a bunch of folders. One is casper with the most amount of room.

TIA

---

### Post by C.S.Cameron on 2010-06-26
If you use this method to run Ubuntu off of USB you can not do updates and upgrades, you are booting an image file in which the kernel is frozen.

If you are using a casper-rw partition the casper-rw file is doing no good and should be deleted. 

You can adjust the partition size using gparted which is on the Live CD.

If you want a pendrive that can be updated and upgraded just like an install to internal hard drive but can also be used for data try this:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 8GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the usb drive you are installing Ubuntu to.
If you do this wrong on a Windows computer you may screw up your Windows MBR which can be a big problem.
At boot you will then be given the option to boot the hard drive.

---

### Post by drillerccg on 2010-06-27
Thank you. I appreciate all your help.  2 more questions:

1-This new method you suggested in above post is very intriguing. What you have described is basically installing and running Ubuntu off of the USB stick, right? If yes, how does that work if you want to boot different windows machines from the USB stick into Ubuntu? Isn't correct that the first install this way would store the settings/drivers/etc for that first machine and may not work for any other machine?

2- do you know how often the Ubuntu folks update the down-loadable iso image? My concern is that, if there are bugs in the early releases and it is being fixed through the "update manager", would they make changes to the iso file? If they do, maybe I can reformat the USB stick every few weeks and take advantage of the new updates.

---

### Post by C.S.Cameron on 2010-06-28
A full install should work in any machine as long as you do not install proprietary drivers, etc.

I think that once a version of Ubuntu is released that is it until the daily releases of the next version. Anyone?

---

### Post by drillerccg on 2010-06-29
> **C.S.Cameron said:**
> A full install should work in any machine as long as you do not install proprietary drivers, etc.

I think that once a version of Ubuntu is released that is it until the daily releases of the next version. Anyone?

Thank you for all your help. I think with this latest info I just try to install a full update-able copy on y USB stick. I will partition it to have a EXT2/3 and a fat32 so I can use it on any machine. Thanks

---

### Post by drillerccg on 2010-06-30
> **C.S.Cameron said:**
> If you use this method to run Ubuntu off of USB you can not do updates and upgrades, you are booting an image file in which the kernel is frozen.

If you are using a casper-rw partition the casper-rw file is doing no good and should be deleted. 

You can adjust the partition size using gparted which is on the Live CD.

If you want a pendrive that can be updated and upgraded just like an install to internal hard drive but can also be used for data try this:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 8GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the usb drive you are installing Ubuntu to.
If you do this wrong on a Windows computer you may screw up your Windows MBR which can be a big problem.
At boot you will then be given the option to boot the hard drive.

OK I tried to do this but it did not work. I'm working on a laptop so easy to take the hard drive out and run the live CD and the USB stick. But half way through formatting and creating the tables, it stops and says it can't do it. It makes 2 of the partitions but not all of them and won't install the OS. Any idea?

Why is there a need for 4 partitions? I'd appreciate it if you tell me what each partition is for. TIA

---

### Post by drillerccg on 2010-07-02
So I did this: Used Fdisk to eliminate all the partitions in the USB. I  then formatted using Gparted to one single Fat32 partition. Then, I took  the hard drive out and boot the laptop from the live CD. Next I plugged  the USB in and used the gParted to create more space by reducing the  size of the Fat32. 

I used gParted to create: a 4 gig EXT4, 3 gig EXT2, and 1 ig EXT2. Clicked on the Install Ubuntu on the desktop and went to advance setting in the partitioning part. used '/" for the EXT4 mount point, used "/home" for the 3 gig Ext2 mount point, and used the 1 gig for swap (did not allow me to choose mount point). Clicked install but it stopped after creating the first EXT2. IT would not create the EXT4 partition and would stop. I tried changing it to EXT3 and EXT2 but still it would stop. I don't know what to do. It appears that it doesn't like to have the / and /home on different partitions, I could be wrong though. Thanks for any help.

---

### Post by C.S.Cameron on 2010-07-02
What happens if you just go with the FAT32, ext4, (/) and swap?
The /home partition is just an option.

---

### Post by drillerccg on 2010-07-02
> **C.S.Cameron said:**
> What happens if you just go with the FAT32, ext4, (/) and swap?
The /home partition is just an option.

I did this, still fails. It says:

 The attempt to mount a file system with type EXT4 in SCSI3 (0,0,0), partition #2 (sda) at / failed. You may resume partitioning from the partitioning menu."

I'm going to try to use EXT2 for the / partition to see if it works. Is that going to be a problem?
Possible problems I'm thinking: gparted does not like my usb pendrive, my usb pendrive is bad, gparted is buggy, the fat32 at the beginning creating problems

Also peculiar is that gParted and the installation program's partition segment does not recognize any EXT4 (or 3 or 2) file system and lists it as unknown. Is that normal?

edit: hmmmm, I can't even choose the option to erase the drive and install Ubuntu on the whole thing. It gives the same message of not installing / on the stick. Confused.

---

### Post by C.S.Cameron on 2010-07-02
Maybe just format the drive using gparted, then run setup, when you get to partitioning select "use entire disk".
If this does not work I think there must be something "different" about your flash drive.

---

### Post by drillerccg on 2010-07-03
> **C.S.Cameron said:**
> Maybe just format the drive using gparted, then run setup, when you get to partitioning select "use entire disk".
If this does not work I think there must be something "different" about your flash drive.

This is so annoying. So it appears that I can make a live USB out of this but can not installa full copy on the 16GB stick. It gets stuck every time when it tries to create / in partition sdx1. I don't know what to do. It says that it can't create EXT4. I've used gParted, the installation program's partitioning, and fdisk. Nothing. I'm starting to think it maybe the USB stick but how am I anle to make a startup disk on it and boot from it then? I was also able to make a persistent USB. So maybe I'm missing something here? Frustrating. Maybe it's Lucid?

---

### Post by C.S.Cameron on 2010-07-03
Did you try ext3?

---

### Post by drillerccg on 2010-07-03
I actually pulled the harddrive and used the USB as the only drive attached. Booted up from the live CD and chose the option of erase everything and install Lucid. The process starts and when it gets to setting partition table it gets stuck on the EXT4 and stops and gives eroor that can not set the / on ext4 parttion. I wonder if it can't unmount the drive since it is the only drive attached. Is there a setting to turn off automatic mounting of attached drives? I know there was in old ubuntu but can't find it in Lucid under system/prefrences.

Is it OK to start a new thread for this you think?

---

### Post by C.S.Cameron on 2010-07-03
I'm starting to wonder if there might be a problem with your Ubuntu iso.
Have you checked the MD5SUM.

---

### Post by drillerccg on 2010-07-03
> **C.S.Cameron said:**
> I'm starting to wonder if there might be a problem with your Ubuntu iso.
Have you checked the MD5SUM.

What is MD5SUM?

edit  mine  d044a2a0c8103fc3e5b7e18b0f7de1c8  ubuntu-10.04-desktop-i386.iso

ubuntu hash  
d044a2a0c8103fc3e5b7e18b0f7de1c8 
    ubuntu-10.04-desktop-i386.iso

looks the same to me, right?

---

### Post by C.S.Cameron on 2010-07-03
> **drillerccg said:**
> What is MD5SUM?

It checks if there is any corruption in the iso file due to a bad download or whatever:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Trying to install Ubuntu using bad iso's has provided me with many hours of entertainment.

---

### Post by drillerccg on 2010-07-03
> **C.S.Cameron said:**
> It checks if there is any corruption in the iso file do to a bad download or whatever:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Trying to install Ubuntu using bad iso's has provided me with many hours of entertainment.
  

I did it (see above) and it seems like it's OK. Lt has the same hash.

---

### Post by C.S.Cameron on 2010-07-03
Have you tried installing without using Manual, (Advanced), partitioning?
I think I am just about lost for suggestions, Can you borrow a 4GB or larger flash drive to try the install on?

---

### Post by drillerccg on 2010-07-03
> **C.S.Cameron said:**
> Have you tried installing without using Manual, (Advanced), partitioning?
I think I am just about lost for suggestions, Can you borrow a 4GB or larger flash drive to try the install on?

Thanks for all your help. I'll try different things (as you suggested) and post here if successful. I started another thread  with this specific topic maybe some one else can come up with what is wrong.

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

That's it. I can boot from the USB and save my session with security. I can also plug the drive into a Windows Machine or Linux box (Ubuntu) and use the flash drive to transfer files (edit: worked on Ubuntu 10.04 but not on 9.04, it said it is read only). I created some folders so they would be separate from Puppy files. It's pretty fast loading up. Love it.

---

### Post by C.S.Cameron on 2010-07-06
Nice set of instructions.
Puppy is a good choice for a portable O/S, runs fast in ram.
Their forums are informative also.
I had a hard time installing Vbox in Lucid Puppy but found a version 4 mix named Vuppy with Vbox already loaded. (there are lots of customized versions floating around).
Yesterday I had Puppy installed in my daughters EEE but found video playback was not as smooth as with Ubuntu.

---

### Post by drillerccg on 2010-07-06
so here is a strange thing. Plugging it in Ubuntu Lucid I can access the USB and use it to transfer files but it did not work on my 9.10 Ubuntu. It showed as read only.

---

### Post by C.S.Cameron on 2010-07-06
What about if you try[to access it with ```
gksu nautilus
```

---

### Post by drillerccg on 2010-07-07
> **C.S.Cameron said:**
> What about if you try[to access it with ```
gksu nautilus
```

I'll try that on Thursday. My Karmic Ubuntu is at work. I'm not too worried about it as long as it is working with Lucid.

---

### Post by varunendra on 2010-07-28
Hey guys!
I was watching this thread when it was hot & thought I'd share my  experience but only after some practical verification first. But before I  could get time for that, I lost the track of it and eventually forgot  it. However, yesterday I found myself wanting my thumb drive be usable  the same way as OP mentioned in his first post.
> **drillerccg said:**
> would like to be able to Boot any computer into  Ubuntu Lucid Lynx but also be able to use the rest of the USB capacity  to transfer files or save updates/settings/etc from Ubuntu. I also would  like to be able to use the extra space in Windows OS if needed to  transfer files. In other words: **1- [COLOR=DarkRed]need to a live USB,[/COLOR]**    **2- [COLOR=DarkRed]need to be  able to use mass storage in Ubuntu,[/COLOR]**    **3- [COLOR=DarkRed]need to use mass storage in  Windows.[/COLOR]**
 
 After a couple of obvious mistakes, I got an [FONT=Comic Sans MS][SIZE=4][COLOR=Indigo]**Easy Way**[/COLOR][/SIZE][/FONT] to get it working as I (& perhaps the OP too) wished.
So here's the update I thought relates to the issue here:


[LIST]
[*]**USB drive used:** [COLOR=DarkRed]**Transcend JetFlash 8GB**[/COLOR]
[*]**Live OS used:** [COLOR=DarkRed]**Lucid Lynx 32bit**[/COLOR] (Also tried **[COLOR=Green]Mint9 764MB DVD[/COLOR]** version successfully)
[*]**Live USB flash drive Tested upon:** [COLOR=DarkRed]**XP, Karmik, Lucid**[/COLOR].
[*]**Live USB created using** [COLOR=DarkRed]**VMware**[/COLOR] (running over XP) booted with [COLOR=DarkRed]**Lucid/Mint9 iso **[/COLOR]images. Default "[COLOR=DarkRed]**Live USB Creator**[/COLOR]" used in both cases.
[*]**[COLOR=Red]The sequence of creating the partitions is a crucial point!![/COLOR]**
[/LIST]
 
[LIST=1]
[*]Using Gparted, delete all partitions in the flash drive.
[*]First create the FAT32 partition in the beginning that you'd be using as mass storage in XP. **(Suggested size= Total space - Space dedicated to Ubuntu Live persistent)**
[*]Next, create another FAT32 partition that will be dedicated to Ubuntu Live (persistent). This won't show up in XP! **(Suggested size= Size of the iso + 128MB or more for tmp-fs/additional programs you may install later)**
[*]Using default USB Startup Disk Creator, install USB live as usual in the second partition. [SIZE=4]**[COLOR=Navy]And you are done!![/COLOR]**[/SIZE]
[/LIST]
 
[SIZE=4][COLOR=DarkRed]**_USAGE RESULTS_:**
[/COLOR][/SIZE]Now here are [COLOR=DarkRed]**three common scenarios**[/COLOR] I tested this Live flash drive in:

[LIST=1]
[*]**System is running XP** and you plug-in this flash drive.             [COLOR=Navy][COLOR=DarkRed]**[RESULT:**[/COLOR] **Only the first**[/COLOR] [COLOR=Navy]partition (totally blank) will show up with full read/write access.**[COLOR=DarkRed]][/COLOR]**[/COLOR]
[*]**System is running Linux** (tried on Karmik/Lucid, should be same for all flavours) and you plug-in the flash drive.[COLOR=Navy][COLOR=DarkRed]**            [RESULT: **[/COLOR]**Both partitions** would appear with full read/write permission.[COLOR=DarkRed]**]**[/COLOR][IMG]http://s621.photobucket.com/albums/tt292/varunjnp/?action=view&current=KarmikGparted.jpg[/IMG]
    [/COLOR]
[*]**System is booted off this Live flash drive.**[COLOR=Navy][COLOR=DarkRed]**      [RESULT:**[/COLOR] **First partition would appear as USB Storage with full read/write access**, casper-rw file on the second partition would be "Filesystem" (including the 'home' directory), remaining files/folders on the second partition would appear under /cdrom with read-only permission.[COLOR=DarkRed]**]**[/COLOR][/COLOR]                (Please mind that the files you store in "home" or any folder located within "Filesystem" would be accessible only in this scenario. To access them in all 3 scenarios, you should store them in the first partition.)
[/LIST]
Now I can use the first partition as a USB Mass Storage device in all of the three possible scenarios, and thus can use it to transfer files between the native Live Ubuntu & external OSes.

---

### Post by varunendra on 2010-07-28
I know this is not related, but ......... before I miss another chance........
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Help.jpg[/IMG]
I drew this when Wilee-Nilee was once pissed off upon me for some comment I made on someone. I was really scared like "What have I done....??" and wanted to say "Oh sir... I'm really sorry! Don't kill me please!!". But the thread was closed before I could make my post.;)

PS: (Yes, the guy with the remote was the avatar of wilee at that time)

---

### Post by 13east on 2010-08-26
> **drillerccg said:**
> Also, I may have not been clear in my original post. I CAN create a persistent pen drive, 2 partitions. One Fat16 with Ubuntu image with 750MB, the other casper-rw with 15GB. And I can boot into ubuntu and use the casper-rw as storage. MY problem is that if I stay in windows, I only see the smaller 750MB partition. The casper-rw does not show up in Windows. That's the main problem I am trying to overcome. TIA

i have a 16gb pendrive that i've been able to mount as a lynxOS and still have 10+gb of storage:
[http://ubuntuforums.org/showthread.php?t=1549342](http://ubuntuforums.org/showthread.php?t=1549342)

hope this helps.

*my only problem right now is being able update the system without crashing the OS.  i know you can't update the system kernels for pendrives and that used to work for older releases; now there are other system files that can't be touched for the pendrive to boot-up properly.   if anyone has the answer, any help would be much appreciated.

---

### Post by C.S.Cameron on 2010-08-26
With a Full install on a 16GB drive you should still have lots of storage.
You can update and upgrade just like a HDD install.

---

### Post by 13east on 2010-08-27
> **C.S.Cameron said:**
> With a Full install on a 16GB drive you should still have lots of storage.
You can update and upgrade just like a HDD install.

not for presistent live usb installation.
the system crashes after update; most common error i see are "segmentation fault" during boot-up

---

### Post by C.S.Cameron on 2010-08-27
> **13east said:**
> not for presistent live usb installation.
the system crashes after update; most common error i see are "segmentation fault" during boot-up

No, I mean that if you want to update and upgrade a flash drive installation you might want to try a Full install like described in post 24 of this thread. You should have lots of room using a 16GB drive

---

### Post by 13east on 2010-08-30
> **C.S.Cameron said:**
> No, I mean that if you want to update and upgrade a flash drive installation you might want to try a Full install like described in post 24 of this thread. You should have lots of room using a 16GB drive

Hi, I tried your method of install a full lynxOS onto a 8gb partition w/ 1gb swap and 6gb storage.  Installation goes fine but cant boot into the OS properly; i get no grub menu or anything else for that matter.  Just a black screen w/ a blinking curosr and after a min. a arrow shows up that is responsive to mouse movements but nothing else.  I tried few commands; alt+ctrl f4 gives you the system terminal w/out userinterface, and alt+ctrl+L locks the screen and password prompt but no way to type anything.

---

