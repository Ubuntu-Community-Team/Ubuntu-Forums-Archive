---
title: "installing windows"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by ZOOstation on 2009-06-26
> **WARNING!!** This instance of a simple procedure got really messy. If you came looking for help making a dual-boot of Windows XP and Ubuntu, you're bound to get confused. I suggest [this tutorial if you are starting with just Ubuntu]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") or [this tutorial if you are starting with just Windows XP]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm").

**Continue reading this thread *at your own risk!!***

My apologies in advance if this question is answered elsewhere already, I tried to search the forums for help really.

I'm on Intrepid and I'd like to break up the partition and dual-boot with XP. I presently have one big partition with Ubuntu on it and a tiny swap. I know how to use Gparted to shrink the Ubuntu partition and create a new one. I assume the Operating System cd that came with my computer in the first place will be suitable to reinstall XP (what the computer original ran on). But I don't know how to properly install it onto a new partition instead of erasing Intrepid.

Basically, I need step-by-step instructions to go from exclusively Intrepid to dual-boot Intrepid and Windows.

---

### Post by overdrank on 2009-06-26
Hi and if you have the Restore cd then if will format the whole drive. Including the partition with Ubuntu on it.

---

### Post by ZOOstation on 2009-06-26
Splendid. Then I need a different kind of source to install from?

---

### Post by Paddy Landau on 2009-06-26
Here's my suggestion. Unfortunately, it will take a little time, but that's Windows for you.

[LIST=1]
[*]Back up all your important data (don't skip this step).
[*]Back up your entire Ubuntu partition (not the swap) using PartImage, because PartImage can restore onto a smaller partition. To do this, you will need:
[LIST]
[*][System Restore CD]("http://www.sysresccd.org/")
[*]A place to store the backup; an external drive, or a network drive, or a second internal hard drive
[/LIST]
 
[*]Install your Windows, which will almost certainly wipe out your Ubuntu. (Perhaps you're lucky and it doesn't, in which case you're done.)
[*]Use the Ubuntu Live CD to repartition your drive; partition 1 will be your newly-installed Windows, 2 will be for Ubuntu and 3 will be the swap.
[*]Use the System Restore CD to restore your Ubuntu onto partition 2.
[/LIST]
HTH

---

### Post by ZOOstation on 2009-06-26
I'll keep that one in mind but I'd prefer something that doesn't involve backing up everything and erasing the drive.
I need to wipe clean and start from scratch like I need a hole in my head.

---

### Post by Paddy Landau on 2009-06-26
> **ZOOstation said:**
> I'll keep that one in mind but I'd prefer something that doesn't involve backing up everything and erasing the drive.
I need to wipe clean and start from scratch like I need teeth in my ***hole.
Well, it won't be starting from scratch. PartImage will restore your entire Ubuntu system exactly as you backed it up. (That's what I did when I had to reinstall Windows, and Ubuntu restored perfectly.)

However, if you really want Windows to install to a partition and not delete what's already there, then you need to speak to Windows Support. After all, it's Windows that wipes out everything; we have no control over that.

---

### Post by ZOOstation on 2009-06-30
Okay, burned the System Restore CD, but after I boot from it I'm having trouble with Partimage. I tried saving the partition image to my USB flash drive: It ran properly but there wasn't enough room. So I borrowed my brother's 500GB external hard drive. After figuring out how to mount it manually, I now get the same error every time I try to create the image:
```
Cannot create temp file
[/backup/pi56558def.tmp]. Please,
check there is space enough and
you have access rights.
```
There is more than enough space. There's more free space on the external drive than the total amount of space on my internal hard drive, nevermind just the used part of the partition.
So then it comes to access rights. While booted from the restore CD, I seem to have no way to change permissions over the device. Unless I'm looking for the option in the wrong place. I create that directory /backup to mount the drive (/dev/sdb1) onto. I can change access permissions to the /backup directory, and I can change access permissions to /dev/sdb1, but once it's mounted my permissions to write at /backup seem to be removed.
For what it may be worth, my brother runs this external drive on Windows, so it's in ntfs format, while the partition I'm trying to backup is ext3fs.
Getting closer to my goal in baby-steps...

---

### Post by balachandarlinks on 2009-06-30
Hi,
  I have a simple solution for you.
        1.Using Gparted shrink your one large volume to two( The new one for windows and the rest is with your ubuntu).
        2.Now format the new one as NTFS or FAT using Gparted.
        3.Now restart your system and insert your windows CD to boot up.
        4.Install windows in the new partition.
        5.After installing you ll find only your Windows OS.
        6.Now time to restore ubuntu.
        7.Insert ubuntu CD and restart your system.
        8.Open in Live CD mode and go to terminal.
        9.Do the following :

net@net-desktop:~$ sudo grub
[sudo] password for net: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,11)                   /* you may get someother */

grub> root (hd0,11)         /*replace what you get */ 

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,11)/boot/grub/stage2
 /boot/grub/menu.lst"... succeeded
Done.

          10.Thats all you did it.Now you ll find both your Windows and ubuntu.
          11.No more steps.Just Enjoy.

---

### Post by ZOOstation on 2009-06-30
How do I make sure that I install Windows on the right partition, or that it won't just install over the entire drive?

---

### Post by fidamehran on 2009-06-30
I'm sorry if I sound annoying. But isn't it really much easier to back everything up and start from scratch?

From what I have learnt, Ubuntu is quite happy to co-exist with Windows, whereas Windows is not like that. (However you will be rid of this once Windows 7 comes; Windows 7 Boot manager is smart and it recognizes Ubuntu.)

So, I have heard that it is better to have Windows installed first and then Ubuntu second.

Sorry if I have offended you.

---

### Post by balachandarlinks on 2009-06-30
> **ZOOstation said:**
> How do I make sure that I install Windows on the right partition, or that it won't just install over the entire drive?
Thats why i told the newer one as FAT or NTFS. The other one ubuntu partition is surely ext2 or ext3.So you ll find the right one using the file system type.Moreove you can judge by the partition size too.
      I put a post regarding this [here]("http://infoqueue.wordpress.com/2009/06/30/installing-windows-safely-after-installing-ubuntu/")

---

### Post by balachandarlinks on 2009-06-30
> **ZOOstation said:**
> How do I make sure that I install Windows on the right partition, or that it won't just install over the entire drive?
Thats why i told the newer one as FAT or NTFS. The other one ubuntu partition is surely ext2 or ext3.So you ll find the right one using the file system type.Moreove you can judge by the partition size too.
      I put a post regarding this [here]("http://infoqueue.wordpress.com/2009/06/30/installing-windows-safely-after-installing-ubuntu/")

---

### Post by Paddy Landau on 2009-06-30
> **ZOOstation said:**
> Okay, burned the System Restore CD, but after I boot from it I'm having trouble with Partimage...
It's worth trying balachandarlinks's solution. Please let us know what happens; I'm curious!

But you'd better back up Ubuntu just in case Windows does play games. It did with me; thankfully I'd had the sense to back up first!

Here are step-by-step instructions to back up using the System Restore Disk with your brother's 500Gb hard drive.


[LIST=1]
[*]Boot from the System Restore CD.
[*]As soon as you see the prompt, type 'rescuecd' (without the quotes). (Optionally, if you have a non-US keyboard, you can instead type 'rescuecd setkmap=xx' where 'xx' is the country code, e.g. uk for the UK.) I believe that if you wait, it will do it for you after some seconds.
[*]Mount your drive with the command 'mount /dev/sdb1 /mnt/backup'. You don't have to create the backup directory; it already exists.
[*]Start PartImage with the command 'partimage', and fill the fields as follows...
[/LIST]


[LIST=1]
[*]Partition to save: sda2 (or whichever partition you have your Windows -- choose carefully!)
[*]Image file to create: /mnt/backup/yourname.pi ('yourname' can be any valid filename, e.g. 20090630-Windows)
[*]Action to be done: Save partition into a new image file
[*]Connect to server: No, do *not* check this
[*]Press F5 (to go to the next page)
[*]Compression level: Choose bzip for optimal space, or gzip for optimal speed
[*]Check partition before saving: Yes, check this
[*]Enter description: Optional; check it if you want to add a short description
[*]If finished successfully: Halt to shut down, or choose anything else you want.
[*]Image split mode: Automatic split (when no space left)
[*]Press F5 (to start)
[*]After some seconds, PartImage will give a summary of what it's about to do; tab and press Enter on OK
[*]Wait... (it takes my 20Gb data -- remember that PartImage backs up only used space -- about three hours)
[/LIST]
HTH

---

### Post by ZOOstation on 2009-07-01
> **Paddy Landau said:**
> Here are step-by-step instructions to back up using the System Restore Disk with your brother's 500Gb hard drive.


[LIST=1]
[*]Boot from the System Restore CD.
[*]As soon as you see the prompt, type 'rescuecd' (without the quotes). (Optionally, if you have a non-US keyboard, you can instead type 'rescuecd setkmap=xx' where 'xx' is the country code, e.g. uk for the UK.) I believe that if you wait, it will do it for you after some seconds.
[*]Mount your drive with the command 'mount /dev/sdb1 /mnt/backup'. You don't have to create the backup directory; it already exists.
[*]Start PartImage with the command 'partimage', and fill the fields as follows...
[*]Partition to save: sda2 (or whichever partition you have your Windows -- choose carefully!)
[*]Image file to create: /mnt/backup/yourname.pi ('yourname' can be any valid filename, e.g. 20090630-Windows)
[*]Action to be done: Save partition into a new image file
[*]Connect to server: No, do *not* check this
[*]Press F5 (to go to the next page)
[*]Compression level: Choose bzip for optimal space, or gzip for optimal speed
[*]Check partition before saving: Yes, check this
[*]Enter description: Optional; check it if you want to add a short description
[*]If finished successfully: Halt to shut down, or choose anything else you want.
[*]Image split mode: Automatic split (when no space left)
[*]Press F5 (to start)
[/LIST]

I still encountered the same error message when I did it this way. Do I need to set a particular authorization to access the location /mnt/backup, or /dev/sdb1? When in Intrepid I can move, copy, paste, create, and delete files in the usb hard drive. But when running partimage, logged in as root on the rescuecd, I apparently cannot.

---

### Post by raymondh on 2009-07-01
> **fidamehran said:**
> From what I have learnt, Ubuntu is quite happy to co-exist with Windows, whereas Windows is not like that.

So, I have heard that it is better to have Windows installed first and then Ubuntu second.


It does not matter which is installed first. Either way, both OS' can be made 'happy' and co-exist without even knowing "who came first'.

Back to the thread .....

---

### Post by Paddy Landau on 2009-07-02
> **ZOOstation said:**
> I still encountered the same error message when I did it this way.
I feel a little puzzled here. However, there is one thing that pops to mind...

Earlier, you said:> **ZOOstation said:**
> my brother runs this external drive on Windows, so it's in ntfs format
Are you sure? External hard drives often come formatted by default with FAT. FAT has the highest inter-operating system compatibility, but unfortunately [FAT doesn't store files larger than 4Gb]("http://windowsitpro.com/article/articleid/38803/understanding-file-size-limits-on-ntfs-and-fat.html").

Double-check the format of the external hard drive. (One way is to start gparted, and it will tell you the filesystem.)

[LIST]
[*]If it's FAT, then there's your problem. Two solutions come to mind:
[LIST=1]
[*]Ask your brother permission to create a separate partition formatted as either NTFS or ext3 so that you can use it without destroying his data.
[*]Easier: On page 2 of PartImage, don't choose "Automatic split". Instead, choose "Into files whose file size is 4000000 Kilo-Bytes" (that's 4 million Kb, or a bit less than 4Gb).
[/LIST]
 
[*]If it's NTFS, then I'm sorry, I'm stumped, because the procedure that I laid out works perfectly for me.
[/LIST]

---

### Post by Paddy Landau on 2009-07-02
> **Paddy Landau said:**
> If it's NTFS, then I'm sorry, I'm stumped, because the procedure that I laid out works perfectly for me.
Ah, one more point comes to mind.

If it's NTFS, then perhaps you need to add the ntfs option to mount (I formatted my hard drive as ext3, and when in Windows, I use [Ext2Fsd in Window]("https://sourceforge.net/projects/ext2fsd/files/")s to access it).

If this is the case, then people with more experience with the mount command could help you with the correct syntax.

---

### Post by ayenack on 2009-07-02
> **balachandarlinks said:**
> Hi,
  I have a simple solution for you.
        1.Using Gparted shrink your one large volume to two( The new one for windows and the rest is with your ubuntu).
        2.Now format the new one as NTFS or FAT using Gparted.
        3.Now restart your system and insert your windows CD to boot up.
        4.Install windows in the new partition.
        5.After installing you ll find only your Windows OS.
        6.Now time to restore ubuntu.
        7.Insert ubuntu CD and restart your system.
        8.Open in Live CD mode and go to terminal.
        9.Do the following :

net@net-desktop:~$ sudo grub
[sudo] password for net: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,11)                   /* you may get someother */

grub> root (hd0,11)         /*replace what you get */ 

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,11)/boot/grub/stage2
 /boot/grub/menu.lst"... succeeded
Done.

          10.Thats all you did it.Now you ll find both your Windows and ubuntu.
          11.No more steps.Just Enjoy.

+1

The easiest and best way to do this. As always make a backup of any important data beforehand just incase.

Take a look at this for further info.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by theozzlives on 2009-07-02
If you have a Retail, or OEM version of Windows NOT a restore disk you should be able to shrink your Ubuntu partition and move the free space to the front. Install Windows on the free space, and redo GRUB. You'll be all set. I've installed windows XP after Ubuntu and it worked fine, except I didn't move free space to the front and wound up with Windows on drive F:\ haha.

Also create a seperate /home, you'll be glad you did later, here's a [link]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/").

---

### Post by ZOOstation on 2009-07-03
> **Paddy Landau said:**
> If it's NTFS, then perhaps you need to add the ntfs option to mount... If this is the case, then people with more experience with the mount command could help you with the correct syntax.

Right you are!! I finally got PartImage to back it up when I mounted using:
```
mount -t ntfs-3g /dev/sdb1 /mnt/backup
```

So then I used GParted to make a NTFS partition and used my Windows system restore CD to install onto it. However, the CD claimed the new partition was not the right format to write on. Even when I used the CD's options of deleting the new empty partition and creating a new one, it said the new ones it created weren't the right format either. The only way it would work was by deleting all the partitions and starting from scratch. Since I'd just backed up my Ubuntu partition, I went with that.

Now Windows is installed on a 30 GB partition and I have about 69 GB unpartitioned disk space. How do I go about restoring my old partition data onto that? Should I create a new partition first? Along with a small swap? Do I install Ubuntu from the LiveCD and then restore the old partition, or go straight to restoring?

---

### Post by Paddy Landau on 2009-07-03
> **ZOOstation said:**
> How do I go about restoring my old partition data onto that?
Well done for getting Windows installed. It's a real b*****, isn't it?

I'm going to tell you how I do it, and anyone else can chime in if they have a better idea.


[LIST=1]
[*]Boot from the System Restore CD.
[*]Start GParted.
[*]In the 69Gb unpartitioned area, create two partitions (it doesn't matter in which order you do them):
[LIST=1]
[*]A swap area. I've been advised to make this (a) the same size as your RAM, or (b) twice the size of your RAM. (I don't know which one is best, so you choose.)
[*]The remainder as an ext3 partition. Note its device name (e.g. /dev/sda3) for step 6 below.
[/LIST]
 
[*]Close GParted.
[*]Start PartImage.
[*]Restore your backup into the ext3 partition.
[/LIST]

That's it!

You don't need to use the Ubuntu Live CD, because PartImage will restore your backup correctly. I hope!

Let us know whether you were successful.

---

### Post by ZOOstation on 2009-07-03
Partitions created without error. But when I try to restore the image from the external hard drive, it tells me "Invalid compression type for '/mnt/backup/upart1.pi.000'." Or something like that.

If it makes a difference, I chose the .gzip compression when saving the partition image.

---

### Post by Paddy Landau on 2009-07-04
> **ZOOstation said:**
> Partitions created without error. But when I try to restore the image from the external hard drive, it tells me "Invalid compression type for '/mnt/backup/upart1.pi.000'." Or something like that.

If it makes a difference, I chose the .gzip compression when saving the partition image.
Sorry, I don't know. A quick search on Google popped up the idea that you could change the extension of your backup file to .gz and decompress the file; then, use the decompressed file to restore from PartImage. [Decompress]("http://www.partimage.org/forums/viewtopic.php?t=213").

HTH -- let us know what happens.

---

### Post by ZOOstation on 2009-07-04
Saved as .gz and unzipped it, but it was too large (like partimage cloned my whole 90-some GB partition and not just the 30-some GB used?) so I'm zipping it up as a bzip2 right now, which will take hours. I'll let you know if I can restore it from that filetype, or if I get the same problem.

---

### Post by ZOOstation on 2009-07-04
Bzip2 had the same result as decompressed: It says the destination is too small, and lists the original partition being restored as 96GB. I thought the point of PartImage was that it would only copy the portion of the partition that was being used?

Fixing this is going to be ugly, isn't it. The only way I see it working is if I restore the partition onto a larger disk, and then copy it again and hope it comes out right. Anyone know an easier way?

---

### Post by austinpsycho on 2009-07-04
well .. maybe im just not a linux lover; but windows can handle the dual boot just fine..  just install to the right partition and away you go

---

### Post by austinpsycho on 2009-07-04
if for some reason it doesn't work right; you can go into repair mode of the windows xp cd and type mbrfix and it will prompt you to adjust your master boot record;  you can make it work..

---

### Post by austinpsycho on 2009-07-04
or you could boot off your live cd; and modify your boot settings afterwards... no reason to redo everything

---

### Post by ZOOstation on 2009-07-04
> **austinpsycho said:**
> well .. maybe im just not a linux lover; but windows can handle the dual boot just fine..  just install to the right partition and away you go

I think you're missing the state of things:

I have a roughly 100GB hard drive. It was running on Intrepid, I made an image of the 96GB partition it was on. Then in order to install Windows, had to erase everything. My only copy of my original system is in a partition image on an external hard drive. PartImage was supposed to only back up the portion of that partition that was being used, but seems to have backed up the whole thing, so what I have now is a copy of a partition that's too big for the space I now have left for it.

So unless you know a Windows way of restoring and/or reducing my Ubuntu image, you're a little off track.

---

### Post by presence1960 on 2009-07-04
> **austinpsycho said:**
> or you could boot off your live cd; and modify your boot settings afterwards... no reason to redo everything

if you read his posts he doesn't have an OEM or retail version of Windows, he has recovery CD/DVD which will wipe the entire HDD and restore it to factory specs (which is without Ubuntu).

---

### Post by austinpsycho on 2009-07-05
oops.. guess i did miss a giant portion of the conversation.. sorry guys...

---

### Post by Paddy Landau on 2009-07-05
ZOOstation, you're not having the best of luck, are you.

I'm not an Ubuntu guru, but I'll explain what I would do in your circumstances. If anyone else can see a quicker way, or any flaws in my process, please chime in.

And I hold my hand up here guilty; there's an obvious step that I should have thought of right up front.

You see, as I understand it, PartImage only backs up the used parts of the partition; but when it restores, it restores those parts *into the same (relative) places*.

You're going to lose your installation of Windows (sorry). You'll have to reinstall it during the following process.


[LIST=1]
[*]Boot into SysRescCD. Delete the Windows partition, and expand your ext3 partition to fill the entire disk (apart from the swap).
[*]Use PartImage to restore your image.
[*]Test that the restore has worked by booting into Ubuntu.
[/LIST]

Now you'll be back to where you started.


[LIST=1]
[*]Back to SysRescCD... Use GParted to shrink your Ubuntu partition to the size you'll be wanting it to be later. (This is the step I omitted earlier.) For safety, make it smaller still; let's say only 50Gb. GParted, as I've experienced it, will automatically move any pieces that would have prevented the shrinking.
[*]Test that the shrink worked OK by booting into Ubuntu.
[*]Back to SysRescCD... Back up your Ubuntu partition using PartImage (don't overwrite your original backup. Call me paranoid, but I think that you should keep it for now).
[*]Reinstall Windows.
[*]Back to SysRescCD... Shrink the Windows partition, create the swap partition and create the ext3 partition.
[*]Boot into Windows to check that the shrink worked OK.
[*]Back to SysRescCD... Restore your Ubuntu partition using PartImage.
[/LIST]

Good luck, and let us know what happened. Computers can be extra-frustrating things.

---

### Post by ZOOstation on 2009-07-05
> **Paddy Landau said:**
> ZOOstation, you're not having the best of luck, are you.

You're telling me. The kicker is that all of this was just so I could access a free month's subscription of an online game I used to play. (I never had any luck with Windows emulators on Ubuntu, so I just gave up all my old software before now). Would I have gone through all of this if the promotion said, "Three weeks of gaming for free, including at least a week of coercing your computer to get along with itself while unable to access your files?" ... Well, maybe -- I'm a gamer at heart.

Anyway, I'll get on that as soon as I have several hours to kill. I'm gonna back up my Windows state first so I don't have to go through all my setup and installations again when I reinstall.

---

### Post by Paddy Landau on 2009-07-05
> **ZOOstation said:**
> The kicker is that all of this was just so I could access a free month's subscription of an online game I used to play...
LOL!

> **ZOOstation said:**
> I'm gonna back up my Windows state first so I don't have to go through all my setup and installations again when I reinstall.
Yes, that's a good idea.

Let us know what happens -- whether you succeed or find other problems.

---

### Post by ayenack on 2009-07-06
Another option is to buy a new hard drive put it in your box next to the old one and let partimage install to that.

---

### Post by ZOOstation on 2009-07-06
(For record-keeping purposes): Somewhere in erasing Windows and subsequently restoring my old Intrepid partition I apparently lost some drivers, and it would not boot. So I installed Intrepid from the Live CD and then restored the old partition, which worked.

That brings us back to square one. I'm about to make my 50GB partition image of Intrepid.

---

### Post by ZOOstation on 2009-07-10
Okay, almost there.

1. Shrank Intrepid partition to 50 GB.
2. Made partition image of Intrepid.
3. Installed Windows to entire system.
4. Restored some of Windows backup. (Restoring complete System State or sensitive files caused corruption/deletion/etc. of key files and Windows or the entire computer would not start).
5. Shrank Windows partition to 30 GB.
6. Created 60 GB ext3 partition.
7. Installed Intrepid to ext3 partition from Live CD. (Restoring Intrepid partition image first didn't take).
8. Restored Intrepid partition image.

One last problem: Before I set Intrepid as default, the bootloader offered me three Ubuntu options, with their respective recovery modes, and Windows XP. Now it only displays Ubuntu. When I look at the drive in GParted, the ntfs partition is unreadable. I cannot mount it, I cannot check it. It knows it's ntfs, but says, "Unable to read the contents of this filesystem! Because of this some operations may be unavailable."

---

### Post by Paddy Landau on 2009-07-10
Good progress.

Did you remember to make a swap partition for Linux?

> **ZOOstation said:**
> "Unable to read the contents of this filesystem! Because of this some operations may be unavailable."

Did you successfully boot into Windows *after* shrinking it to 30Gb?

---

### Post by ZOOstation on 2009-07-10
Yes, installing from the Live CD created a generous swap partition.

I was able to start up Windows from GRUB once or twice while it was in a 30 GB partition of its own.

Even though GParted acted like it wasn't there, the 30 GB partition was on my desktop and accessible. I ran testdisk (an idea from other threads about Windows not appearing in GRUB), which made the drive readable to GParted. On reboot, it wasn't in GRUB and seems to be unreadable again. It's still on my desktop, displays no files this time, but says there are only 18 GB of free space, meaning my files are still there.

Also, "fdisk -l" only gives "Cannot open /dev/sda."

---

### Post by LewRockwell on 2009-07-10
you might check out Supergrubdisk

you can use it in a variety of different applications and methods

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by ZOOstation on 2009-07-10
And what exactly should I do with SGD?

---

### Post by ZOOstation on 2009-07-11
Sooo Windows is still missing. It does not appear in GRUB, and it freezes when I try to boot it through Super Grub Disk or run the Windows System Restore cd. It does not automatically mount, but is available in the Computer directory and the Places menu from my taskbar, where it can be mounted and unmounted without error. Opening it displays no files, but when mounted its properties report 10 GB used and 28 GB free. GParted can read it just fine when mounted, and currently indicates both its partition and the Intrepid partition are flagged "boot."

Correction/discovery regarding a previous complaint: "fdisk -l" gives "Cannot open /dev/sda," but "sudo fdisk -l" gives the proper output:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3761    30210201    7  HPFS/NTFS
/dev/sda3            3762       12161    67473000    5  Extended
/dev/sda5   *        3917       11819    63480847+  83  Linux
/dev/sda6           11820       12161     2747083+  82  Linux swap / Solaris
```

Is it possible the problem is that the partition cannot be read before it's mounted? And why can't I see any of its files when I mount it while logged into Intrepid?

---

### Post by LewRockwell on 2009-07-11
> **austinpsycho said:**
> oops.. guess i did miss a giant portion of the conversation.. sorry guys...

damn porcupines anyways...

.

---

### Post by Sef on 2009-07-11
1) Only Windows should be the booted from.   Not sure how to remove the Linux boot command (*).

2) The Windows partition seems rather small.

---

### Post by LewRockwell on 2009-07-11
> **ZOOstation said:**
> Sooo Windows is still missing. It does not appear in GRUB, and it freezes when I try to boot it through Super Grub Disk or run the Windows System Restore cd. It does not automatically mount, but is available in the Computer directory and the Places menu from my taskbar, where it can be mounted and unmounted without error. Opening it displays no files, but when mounted its properties report 10 GB used and 28 GB free. GParted can read it just fine when mounted, and currently indicates both its partition and the Intrepid partition are flagged "boot."

Correction/discovery regarding a previous complaint: "fdisk -l" gives "Cannot open /dev/sda," but "sudo fdisk -l" gives the proper output:
```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3761    30210201    7  HPFS/NTFS
/dev/sda3            3762       12161    67473000    5  Extended
/dev/sda5   *        3917       11819    63480847+  83  Linux
/dev/sda6           11820       12161     2747083+  82  Linux swap / Solaris
```

Is it possible the problem is that the partition cannot be read before it's mounted? And why can't I see any of its files when I mount it while logged into Intrepid?

remove the boot flag currently on sda5

you can do it in LiveCD Partition Editor(Gparted) or you can run fdisk in the terminal...whichever floats your boat...

.

---

### Post by ZOOstation on 2009-07-11
Boot flag has been removed from sda5. Didn't change anything.

Tried appending to GRUB:
```
title		Windows XP Media Center Edition
root		(hd0,0)
makeactive
chainloader	+1
```
It appeared on the menu, but booting from it simply froze up with a blank screen.

Also tried a number of fix and restore options on Super Grub Disk, with little variation of results and no success.

Currently it encounters "Error 13: Invalid or unsupported executable format" when the windows partition is selected and returns to GRUB.

---

### Post by Paddy Landau on 2009-07-12
Let's go back a few steps.

Looking at [post 31]("http://ubuntuforums.org/showthread.php?p=7563960#post7563960")...

You successfully did the first section.

Then you successfully did steps 1-6, i.e. the Windows worked correctly. Am I right?

Something happened in step 7 to mess up your Windows.

I also noted in your [post 36]("http://ubuntuforums.org/showthread.php?p=7592664#post7592664") that you said, "I set Intrepid as default". What do you mean by that? It shouldn't have been necessary according to the steps I outlined.

And, "Restoring Intrepid partition image first didn't take". Um, I wonder what happened there? Did you accidentally start restoring Intrepid onto your Windows partition, perhaps?

---

### Post by ZOOstation on 2009-07-12
CORRECTION: I don't know why I'd set Intrepid as default, it wasn't really what I wanted. I can't remember what I was thinking.

Yes, Windows did work correctly, even after the partition was shrunk to 30 GB. I had a few blissful days of gaming.

When I tried to get myself back to square one (see [post 35]("http://ubuntuforums.org/showthread.php?p=7571963#post7571963")), going straight to the partimage restore didn't work. This is going back a little while, so I can't remember exactly, but I think I had uninstalled Windows, deleted the ntfs partition, expanded the ext3 partition to fill the remaining space (I maintained a swap of about 2 GB), and then run partimage. After "successful" restore, the computer would not boot. It seemed to be unable to access key hardware. So I tried a fresh Live CD install so any missing drivers would be restored, then restored the partition image onto that.

Since I'd had that trouble, I didn't try restoring the image directly to a blank partition this time around and went straight to the Live CD install first. This install was absolutely on the ext3 partition. The ntfs partition still exists and still has my files on it, it just doesn't boot.

---

### Post by Paddy Landau on 2009-07-13
Hmm...

It sounds to me that -- unfortunately -- you'll need to clean your disk again.


[LIST]
[*]Delete the partitions
[*]Reinstall Windows
[*]Shrink Windows
[*]Recreate the swap and ext3 files
[*]Restore Ubuntu from PartImage
[/LIST]

You have been unlucky with this one.

---

### Post by andrew.46 on 2009-07-13
Hi,

I realise I am coming in after a long conversation, but did you consider the use of a Virtual Machine? There are some limitations of course but the setup and whole experience is a lot less painful than the one you describe :-). Screenshot attached.

Andrew

---

### Post by ZOOstation on 2009-07-13
Okay, trying again:

1. Windows Install: Success.
2. Windows Shrink: Success.
3. Linux & Swap Creation: Success.
4. Linux Image Restore: Success?

About halfway into the image restore, partimage asked for a path to the file "upart3.001," which never existed. I saved my partition as upart3, which naturally became upart3.000, on an external hard drive. There is no upart3.001 as far as I can tell. Maybe I'll search it thoroughly, but I don't understand why such file would've been created at all, nevermind in a different directory or as a hidden file or something.

When ending the restore process there, it seems as though a good amount of my partition has been restored. Rebooting opens Windows. I reactivated GRUB using Super GRUB Disk, and can successfully boot Windows from GRUB. But trying to boot Linux from GRUB gives the following error:
```
Loading, please wait...
mount: mounting /dev/disk/by-uuid/1db8f79b-2fcd-4c06-9b41-38746af941e6 on /root failed: Invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_
```

I assume these are files that didn't install because the image wasn't fully restored? Or should I correct where it looks for them?

---

### Post by ChadMMc on 2009-07-13
Sorry late to to this discussion... Actually here is a link to a site which seems to give installation for dual-booting systems whether you have either windows or linux already installed.  May help in the long run.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Note: was last updated with 8.04 as the distribution, but should work with distributions after that I think.

---

### Post by Paddy Landau on 2009-07-14
> **ZOOstation said:**
> About halfway into the image restore, partimage asked for a path to the file "upart3.001," which never existed.
Yes, you're right, it should not have asked for that.

I think that you need to test upart3.000 for integrity. Boot from the Live CD. Use these two commands on your upart3.000 file:
```
mv -i upart3.000 upart3.gz
gzip --test upart3.000
```Three points:

[LIST]
[*]I'm assuming that you used the gzip option. If you used bzip2, then use '.bz2' instead of '.gz', and use 'bzip2' instead of 'gzip'.
[*]Be sure that upart3.gz doesn't already exist, otherwise you'll overwrite it.
[*]Your upart3.000 will now be called upart3.gz (you can still use it from PartImage; just use the new name).
[/LIST]
Also, I'm wondering if there's something wrong with your SysRescCD. Can you redownload it (unless you still have the .iso), [check the md5 sum]("http://www.sysresccd.org/Download"), and burn it afresh, just in case?

---

### Post by ZOOstation on 2009-07-14
```
joey@Lappy:~$ md5sum Downloads/systemrescuecd-x86-1.2.1.iso
0872d3bde0fad326f5db31bbf49d2702  Downloads/systemrescuecd-x86-1.2.1.iso
```

No idea what that means.

Working with gzip on checking/moving/renaming/anything my partition image consistently resulted in "Input/output error." I figure upart3 is broken and have restored upart2 in order to make a new one.

Questions developing from all the partition business: What is the purpose of an extended partition? What difference does it make whether or not I have one, how many partitions are in it, or which ones?

---

### Post by Paddy Landau on 2009-07-15
> **ZOOstation said:**
> 0872d3bde0fad326f5db31bbf49d2702 ... No idea what that means.
That's the checksum. It should agree with the checksum on the website.
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
However, they've just updated the version, so you have to go to the old pages:
[http://www.sysresccd.org/Sysresccd-versions](http://www.sysresccd.org/Sysresccd-versions)
There you can see that your checksum is correct. In other words, your downloaded iso is OK.

> **ZOOstation said:**
> Working with gzip on checking/moving/renaming/anything my partition image consistently resulted in "Input/output error." I figure upart3 is broken and have restored upart2 in order to make a new one.
I agree. Something went wrong there.

> **ZOOstation said:**
> Questions developing from all the partition business: What is the purpose of an extended partition? What difference does it make whether or not I have one, how many partitions are in it, or which ones?
A partition is a way to divide up a hard drive into separate sections. You need at least one partition, even if you want to use the entire drive.

A hard drive can have at most four partitions (don't ask me why!). However...

You can have two different types of partitions: Primary and extended.

A primary partition holds data.
An extended partition doesn't hold data, but it does hold partitions, called secondary partitions.

So, if you wanted (say) six partitions, you could have three primary partitions, one extended partition, and three secondary partitions within the extended partition. That will give you six useable partitions altogether.

Any unpartitioned space on the drive, and any unpartitioned space within an extended partition, cannot hold anything. You have to create a partition over that space to use it.

In other words, a hard drive without a partition is pointless.

There is also a boot sector on the hard drive, which tells the computer where the partitions are and how to boot off it. I know roughly nothing about that area.

Some operating systems will only boot off a primary partition. I believe that Windows is like that (but I could be wrong). Ubuntu is fine to boot off a secondary partition.

A typical dual-boot has four partitions: The Windows factory restore; the Windows itself; Ubuntu; and the Ubuntu swap space. This could be two primary partitions, and two secondary partitions within an extended one. Or, simply four primary partitions.

See Wikipedia for more about [hard disk partitions]("http://en.wikipedia.org/wiki/Disk_partitioning").

HTH

---

### Post by ZOOstation on 2009-07-15
The bizarre never stops here. When restoring upart2 to a blank ext3 partition, everything gets up and running fine (except the bootsplash, but that's a minor thing I can fix up later), but there appears to be more used space on the partition than there should be.

upart2.000 was made from a partition of about 50 GB, and not compressed with gzip or bzip2. The data partimage gives from it reads...
```
Space usage: 65%
Used space: 31.93 GiB
Free space: 16.90 GiB
```

When restored through partimage onto a completely blank ext3 partition, gparted reports these stats of the result...
```
Size: 90.28 GiB
Used: 73.33 GiB (81%)
Unused: 16.95 GiB (19%)
```

Should I be restoring the image to a partition the same size as it came from, then *afterward* resize it to fit my needs? Or is something screwier at work here?

It probably seems like this process is too weird to be an accident, but I guarantee you I couldn't have made it nearly this confusing on purpose.

---

### Post by Paddy Landau on 2009-07-16
> **ZOOstation said:**
> It probably seems like this process is too weird to be an accident, but I guarantee you I couldn't have made it nearly this confusing on purpose.LOL... Something from science fiction!

I don't know enough to start commenting about how this happened.

May I suggest that you do a disk check on your drive. Boot off the Live CD, find out your partition name (something like /dev/sda1), and enter the following command. Replace /dev/sda1 with the correct partition name. (Note that you must *not* mount the partition while using fsck.)
```
fsck -M /dev/sda1
```Check your space afterwards to see what's happened.

Are you able to boot correctly onto Ubuntu?

---

### Post by LewRockwell on 2009-07-16
I sure hope no curious folks read this thread...

Surely it will make their brain matter into mush and they will never...ever...mess with ANYTHING other than windoze or macdoze...

{{left thread with eyes bleeding}}

sigh...

.

---

### Post by Zero++ on 2009-07-16
I know you all are pretty far into this whole process now but wouldn't it have been easier to just borrow a copy of windows from a friend or a torrent site. It's not piracy the user has a valid windows key that he/she would enter to register with Microsoft. Windows its self won't format your entire drives it's just those crappy restore CDs that come with pre-made computers. Again, I'm not advocating piracy in any way it hurts the GNU/LINUX world just as much as the WIN/MAC world. 

Just a thought...

---

### Post by Paddy Landau on 2009-07-16
> **LewRockwell said:**
> I sure hope no curious folks read this thread...

Surely it will make their brain matter into mush and they will never...ever...mess with ANYTHING other than windoze or macdoze...
Oh, as if Windows has never caused problems like this? I've had far fewer problems with five computers on Ubuntu than I've had with two computers on Windows. But that's only my experience...

This thread, in my experience, is very much the exception with installing dual-boot Windows and Ubuntu.

---

### Post by ZOOstation on 2009-07-17
> **ZOOstation said:**
> When restoring upart2 to a blank ext3 partition... there appears to be more used space on the partition than there should be. Should I be restoring the image to a partition the same size as it came from, then *afterward* resize it to fit my needs?

Suspicion confirmed. Tried again, this time restoring upart2 to a blank ext3 partition of only 50 GB, like the one it was made from. Success. Only it's actually just returning, once again, to square one.

Also noteworthy: Windows Restore CD installed to empty, unpartitioned space without a problem. Didn't have to shrink Windows and re-install Ubuntu.

1. Shrink Ubuntu Partition: Success.
2. Install Windows: Success.
3. Restore GRUB: Success... mostly....

GRUB is restored, Windows does not appear on it. This is where we left off a little while ago. Haven't tried to manually edit GRUB or use Super GRUB Disk to repair it, for fear I'll only mess it up when I'm so close to the finish. Current fdisk:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+  83  Linux
/dev/sda2   *        6375       11785    43463857+   7  HPFS/NTFS
/dev/sda3           11907       12161     2048287+  82  Linux swap / Solaris
```

If you noticed there's some empty space between sda2 and sda3, that's deliberate. It's the first step of tweaking the partition sizes a little; I'm gonna make a little more Linux and a little less Windows.

So the question at this point is: How do I get GRUB to list Windows in addition to Ubuntu?

---

### Post by Paddy Landau on 2009-07-18
Well, success at last! (Only took three weeks...)

I'm glad that you've got your system working finally.

[LIST]
[*]Do a full backup with PartImage of both sda1 and sda2 before you do anything else! Make a note of the partition sizes in case you need to restore.
[/LIST]
I don't know how to change Grub. For that, please search these forums, as the answer has been asked and answered many times. You may find the [Grub How-to]("https://help.ubuntu.com/community/GrubHowto") useful.

---

### Post by ZOOstation on 2009-07-18
I got a working GRUB solution from page 5 of [this tutorial]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm"). (With pictures)!

I'm putting a disclaimer at the start of this thread for people who mistakenly come looking for help with similar problems.

Thanks so much for your help, Paddy!

---

### Post by Bartender on 2009-07-18
I think there are some clear lessons here.

The first advice was the simplest and best.  Start over.  
Although the OP didn't want to do that, it was good advice because it came from people who've been down this road.  Windows is intentionally written to hog the drive.  It wants to be "first", and it wants to be the "only".  The Linux installer is written to deal with that reality.  

People who know how can do various work-arounds, but the newb is better off to stay on the well-trodden path.

If it were me, I'd have saved my personal data, then download/burned a copy of GParted LiveCD, then wiped the drive, then made a primary NTFS partition "first", or to the left-hand side of the map in GParted.  Then I'd make an extended partition out of the rest of the drive.  Inside that extended partition, create a logical ext4 partition for /, a logical partition for swap, and a logical ext4 partition for /home.  

Boot the Windows CD, it only sees the ntfs partition, installs there, the rest is cake.

---

### Post by LewRockwell on 2009-07-18
> **Bartender said:**
> I think there are some clear lessons here.

The first advice was the simplest and best.  Start over.  
Although the OP didn't want to do that, it was good advice because it came from people who've been down this road.  Windows is intentionally written to hog the drive.  It wants to be "first", and it wants to be the "only".  The Linux installer is written to deal with that reality.  

People who know how can do various work-arounds, but the newb is better off to stay on the well-trodden path.

If it were me, I'd have saved my personal data, then download/burned a copy of GParted LiveCD, then wiped the drive, then made a primary NTFS partition "first", or to the left-hand side of the map in GParted.  Then I'd make an extended partition out of the rest of the drive.  Inside that extended partition, create a logical ext4 partition for /, a logical partition for swap, and a logical ext4 partition for /home.  

Boot the Windows CD, it only sees the ntfs partition, installs there, the rest is cake.

Agreed

Hey Bartender, where did you get that avatar photo!?!

---

### Post by LewRockwell on 2009-07-18
> **LewRockwell said:**
> I sure hope no curious folks read this thread...

Surely it will make their brain matter into mush and they will never...ever...mess with ANYTHING other than windoze or macdoze...

{{left thread with eyes bleeding}}

sigh...

.

I wanted to thank the OP for modifying/editing/updating the first post to reflect and warn future visitors of this sunny-side-up adventure being turned into scrambled eggs...

.

---

