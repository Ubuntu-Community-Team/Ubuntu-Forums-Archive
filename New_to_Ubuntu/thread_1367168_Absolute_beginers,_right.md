---
title: "Absolute beginers, right?"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by spacemonkeyxxx on 2009-12-29
[FONT=Times New Roman][SIZE=3]I’m having trouble installing Ubuntu 9.10, it isn’t the simple process the documentation say it is, forgive me but this is Absolute beginners, right?[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I have managed to change the bios so that I can boot from the disk. I have chosen “try ubuntu without any change to your computer”[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]After a while I get a desktop with an “install ubuntu 9.10” which I click[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]It asks what language I want (English)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Chose time zone (Europe)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]So far so good, then the “fun” begins. Now I have a “prepare disk space” screen. There is a message saying “this computer has several operating systems on it” then a multicoloured graphic of my HD split into 4 partitions. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Partition 1= 13GB is windows visa loader, (/dev/sda2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Partition 2= 111.4 GB is windows visa loader, (/dev/sda2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Partition 3= 104.9 GB is /dev/sda2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Partition 4= 3.5GB is Microsoft Windows XP Embedded (/dev/sda2)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]These are the partitions my HD was split into when I got it. Partition 3 is empty and its this that I want to use. However I am given 2 options;[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]1 Erase and use entire disk ( erm, no thanks)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2 Specify partitions manually ( I guess its this one then )[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Clicking forward gives me “prepare partitions”[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Again there is the multicoloured graphic of my HD split into 4 partitions.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Then there is a table with headings[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Device Type Mount Point Format? Size Used[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]The third entry on the table is the partition I want to use and has the following properties;[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Device = /dev/sda3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Type = ntfs[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Mount Point = blank[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Format? = a tick box[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Size = 112634 MB[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Used= 3226MB[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]If I highlight this line in the table and hit forward I get the following error message;[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]No root file system is defined[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please correct this from the partitioning menu[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Double clicking the same line in the table brings up an “edit partition” dialog[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]This has 4 dialogs[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]1[/SIZE] [SIZE=3]New partition size = leave this as it is, 112634[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]2[/SIZE] [SIZE=3]Use As= this has a lot of options Ext4 journaling file system[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Ext3 journaling file system[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]Ext2 file system[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ReiserFS journaling file system[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]JFS journaling file system[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]XFS journaling file system[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]FAT16 file system[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]NTFS[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Swap area[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Do not use this partition[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]I guess this should be ntfs, as all the other partitions are ntfs too. However, what I put in here effects the options in box 4[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]3 Format the partition = tick box (guess this is no as its already formatted)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]4 Mount Point This gives me a bunch of different options depending on what I enter in box number 2. For example if I have ntfs or FAT16 or FAT32 in box 2 then the options are /dos and /windows[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]If however I have “swap area” or “do not use partition” then I cannot enter any mount points[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Any of the other file systems gives the following options /[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]/boot[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/home[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/tmp[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/usr[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/var[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/srv[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/opt[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/usr/local[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3]This is as far as I have managed to get with the installation process. What do I do now?[/SIZE][/FONT]

---

### Post by Bartender on 2009-12-29
They can't all be sda2...
 
You have 4 partitions on the HDD, probably all of them primary, and that's why you're not getting many choices.

Tell you what, if you could post a screenshot that would be helpful. Boot from the CD again, choose "Use Ubuntu without any changes" when you get the desktop plug in a thumb drive and wait for it to appear on the desktop.  Then go to System>Administration>Gnome Partitioner and bring that up.  When you have the picture of your partitions go to Applications>Take screenshot and choose "Save As"  Save it to the thumb drive which will probably be identified as "disk" in the dropdown.  

Then you can get out of the LiveCD, and come back to this thread with a Linux or Windows PC and start a new post.  Scroll down past the box where you type in the post and find the "Manage Attachments" section.  Upload your screenshot there, type anything helpful into the post, and send it.

---

### Post by fromthehill on 2009-12-29
you should use the drive as ext4 (ext3/2 works too)
that will erase the partition(it is empty, right?)
the mount point needs to be '/'

swap is the same for linux as the pagefile is for windows
you probably won't need swap you can ignore that message

and seriously, use the default font
it's really hard to quote parts of your text with the millions of font tags

---

### Post by Matt__ on 2009-12-29
A quick reply as I'm logging off...hope it helps & I will check back later.
try this [LINK to graphical install guide.]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by 3rdalbum on 2009-12-29
Basically, the message is saying that you haven't defined what drive you want as your "root filesystem" - where everything is to go.

With the partition that you want to use, just set the "mount point" to /

And the filesystem format should be ext4.

That's all you need to get started. I assume since you've got Vista that you have a reasonable amount of memory (1 gig or more) so you won't need any swap.

---

### Post by margazhang on 2009-12-29
Two routes to go...

(1) Back up all the data you need and choose to erase and use entire disk. Then install Windows XP or Vista inside Ubuntu via VirtualBox.

As a beginner, you do not have full trust on Ubuntu. So you should play with it with the live CD and see if there is anything you cannot do with Ubuntu - I do not see any so I completely switched to Ubuntu.

(2) If you do not want to do that, then I would delete the unwanted partition (partition 3 in your case) and install two new partitions using the manual partitioning process:

N**ew partition 1**: swap area the size of your RAM
**New partition 2**: Ext4 as the primary partition with / as the mount point taking the remaining size

Then the installation will be installed on your Ext4 partition.

Normally, if you had one Windows OS installed, the installation will guide you to resize the Windows partition and does the rest automatically. But in your case you already have so many Windows partitions, manual partitioning is the only option which makes things more complicated for a beginner.

---

### Post by CharlesA on 2009-12-29
Should have four partitions: sda1, sda2, sda3, sda4. You need to partition whatever partition is empty (delete it and recreate, unless it's just free space) and mount "/" to it. Should be ok with no swap file.

---

### Post by spacemonkeyxxx on 2009-12-29
Thanks for all the help, I'm knocked out by the response. Bellow is a screen shot of the partitions on my hard drive, you are absolutely right they are named sda1-4. Hope it helps. The partition I want to use is called DATA and is sda3 which should be empty but appears to still have stuff in there, though it shows up as empty in vista.

---

### Post by FinalCoyote on 2009-12-29
Y'know, i really hate partitioning.

I really, really do.

However, when i installed there was an option for Guided Partitioning (i used the alternate installer, because i'm on a PS3) and it worked without problems.

Of course, my PS3 HDD doesn't have the partitions or the problems of a PC NTFS drive so i'm probably not being much help..

---

### Post by CharlesA on 2009-12-29
Laptop right?

sda1 is the system recovery partition
sda2 is the vista install
sda3 is a data partition
ad4 is leftover (not sure what it is)

First suggestion I have, is to image the drive before messing with the partitions. If you've got an external drive, you can image it using clonezilla so that you have a good backup in case something goes wrong.

EDIT: I went thru an install on VBox with 4 partitions.

See attachments: Specify the partition manually. Select sda3, select change. (see attachment partition3).

Note size is different since I just used a 50GB drive.

---

### Post by spacemonkeyxxx on 2009-12-29
> **CharlesA said:**
> Laptop right?
 
sda1 is the system recovery partition
sda2 is the vista install
sda3 is a data partition
ad4 is leftover (not sure what it is)
 
First suggestion I have, is to image the drive before messing with the partitions. If you've got an external drive, you can image it using clonezilla so that you have a good backup in case something goes wrong.
 
EDIT: I went thru an install on VBox with 4 partitions.
 
See attachments: Specify the partition manually. Select sda3, select change. (see attachment partition3).
 
Note size is different since I just used a 50GB drive.
 
 
 
Thanks for the walk through which I followed and I'm glad to say I have a nice shiny Ubuntu OS!! Sadly though Vista has died. When I try to boot a program called GRUB starts and offers me a bunch of booting options. The only option for vista is sda1, which is the system recovery partition, and thus it asks for my recovery disks which I don't have with me. I think I should be booting Vista from sda2. Is there any way of telling GRUB to boot from sda2 instead of sda1? It gives me an option to enter a command line, but I have no idea what the command would be.
 
Anyway, to all who have helped me out here a very big thank you.

---

### Post by spacemonkeyxxx on 2009-12-29
> **FinalCoyote said:**
> Y'know, i really hate partitioning.
 
I really, really do.
 
However, when i installed there was an option for Guided Partitioning (i used the alternate installer, because i'm on a PS3) and it worked without problems.
 
Of course, my PS3 HDD doesn't have the partitions or the problems of a PC NTFS drive so i'm probably not being much help..
 
 
Hi
You have Ubuntu installed on a PS3!!!??? How is it going? Can you still play bluray disks and games?

---

### Post by spacemonkeyxxx on 2009-12-30
For anyone who is interested:
 
"sudo update-grub" had grub re-look at my partitions where it recognised sda2 as bootable and added it to the list of options at boot up. Now I have a fully functional dual boot system!! YIPEE!!

---

### Post by 3rdalbum on 2009-12-30
> **spacemonkeyxxx said:**
> Hi
You have Ubuntu installed on a PS3!!!???

Wow, where have you been these last few years? On the earlier PS3s (not the Slim) Sony supports Linux. Sony does everything except burn the Xubuntu CD for you.

> Can you still play bluray disks and games?

Yes, when you're in the ordinary PS3 operating system. There's no 3D acceleration and no Blu-ray drive in Linux on the PS3.

---

