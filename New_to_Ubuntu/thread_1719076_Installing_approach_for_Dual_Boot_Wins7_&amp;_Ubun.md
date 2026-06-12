---
title: "Installing approach for Dual Boot Wins7 &amp; Ubuntu."
date: 2011-04-01
forum: New to Ubuntu
---

### Post by jkb609gi8 on 2011-04-01
Recently I purchased a cheap laptop, a Toshiba Satellite C650D that is set up with Windows 7 using a FAT32 file system. (Note: *it maybe NTFS32, what ever it is for Windows 7?*) This computer comes with AMD Vision 64 CPU, 4gigs RAM, & 500gig Hard-drive. When setting up the Windows 7 I had the option of using a 32-bit or 64-bit file system, and I opted for the 32-bit system.


I have made a mirror backup of the entire hard-drive. I wish to partition this laptop to a dual boot Ubuntu as the primary system. Since my windows 7 is set up for 32-bit, which version of Ubuntu should I use, the 32-bit system or 64-bit system? I have both versions of Ubuntu 10.10.


I have also been reading the Ubuntu documentation "Pre-Partitioning for Multi-Boot Systems". I barely have the intellectual ability to understand this, of course I am in a bit of a hurry, lacking Patience to study the wikipedia terminology. Any ideas or advice on a simple approach to setting up a dual boot Ubuntu 10.10 with existing OEM Windows7?:confused:

---

### Post by Locke_99GS on 2011-04-01
The simplest method would be to tell the Ubuntu installer to install Ubuntu "alongside" Windows, but doing so will cause Ubuntu to use a large portion of your available drive space. If you intend on using Ubuntu primarily, this will be fine. If you still intend on using Win7 primarily, you'll be aggrivated at the lack of drive space available to it. If this is the case, I would suggest pre-partitioning the drive the way you want it, giving Ubuntu only a small portion of the drive space, and leaving the rest for windows.

To do this manual partitioning, boot to the Ubuntu LiveCD, select "Try Ubuntu" from the two options you are presented with, then in the System menu in the top panel, go to Administration then GParted. This is the partition editor. Right-click on the Windows partition and choose the Resize option. You can just use the mouse from here to just drag the sides of the graphical representaion of the partition to give Ubuntu some space. If you have enough drive space, say 300+gig, I'd free 20gig or so. (if it won't be your primary OS) Close that windows, then right-click on the freespace you just created and choose "create partition" (or something of that sort) and format it to ext4. When you're done, click apply in GParted, and let it do its thing. Then, when you run the Ubuntu installer, select the manual or advanced partitioning option, choose the ext4 space you just created, make it ext4 again, then add "/" as the mount point. Install.

As for 32bit or 64bit for linux, this doesn't have anything to do with Windows or its partition type. I'd recommend 64bit, but 32bit will work fine also.


Some of my above instructions for partitioning may not be exact as I don't have GParted open at the moment, but it should be close enough that given ample investigation you should be able to figure it out. SHould anything fail miserably, don't forget you have that mirror image as backup.

---

### Post by oldfred on 2011-04-01
I also strongly suggest manual partitioning in advance. It gives you a lot more control over sizes and formats of partitions. There is a "bug" which the designers do not call a bug since it is just confusing instructions in the auto installer. And if you click on the wrong button it defaults to erase entire drive. (Much better in Natty, but Natty is still beta so not recommended yet.)

Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

This offers a lot of detail, but it is not really complex, Herman includes lots of screen shots so you can see what is happening.
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Several others:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by jkb609gi8 on 2011-04-03
Since the last post, I have md5sum  checked the Ubuntu image and burnt a Grub rescue disk. I am slowly moving along with this partitioning project. I think I will try this with GParted. 



The first thing I come up against, is this computer's O/S Windows 7 has already divided the hard-drive up into 4 partitions show of the Gparted graphics as follows; 
  
 

/dev/sda1 
 File System: ntfs 
 Partition Disk #0, Partition #0 
 Partition Size 1.46 GB (1,572,864,000 bytes) 
 Partition Starting Offset 1,048,576 bytes 
 (Flags) boot, diag 
  
 

/dev/sda2 
 File System: ntfs 
 Partition Disk #0, Partition #1 
 Partition Size 435.74 GB (467,873,562,624 bytes) 
 Partition Starting Offset 1,573,912,576 bytes 
 (Flags)  
  
 

/dev/sda3 
 File System: ntfs 
 Partition Disk #0, Partition #2 
 Partition Size 18.32 GB (19,671,285,760 bytes) 
 Partition Starting Offset 469,447,475,200 bytes 
 (Flags) Hidden 
  
 

/dev/sda4 
 File System: ntfs 
 Partition Disk #0, Partition #3 
 Partition Size 10.23 GB (10,989,076,480 bytes) 
 Partition Starting Offset 489,118,760,960 bytes 
 (Flags) Hidden 
  
 

 I originally had wanted to divided  my Harddrive's space in two, half for Ubuntu and half for Windows. Giving the lions share of the hard-drive to Unbuntu would be OK to. Hopefully I could make it so that it boots into Ubuntu as default, but this is not necessary. I would prefer to keep the OEM hidden recovery system. 
  
 

Can I, or should I place all of these Windows partitions into 4 Logical partitions one primary extended partition? :confused:
  
 

Can I, or should I have two  extended partitions (?primary?), divided into 4 logical partitions in each extended? :confused:



I will try and figure this out with the links I have already been provide.

---

### Post by Sidewinder1 on 2011-04-03
I'm not very familiar with the differences between primary, logical, and extended partitions so I can not really advise what scheme would be best for your needs, sorry.
One thing I will recommend is, using the Windoze 7 OS, defragment the NTFS partitions, at least twice prior to moving, resizing them, even though you stated you have full back ups of all. Unfortunately, defragging can take a very long time depending on how much data is there and how fragmented it is. Do not be concerned if the defragment program reports that a small number  of files could not be defragmented, this is normal.
HTH, 
Side

P.S. It's *"probably"*not necessary on the two hidden, OEM, recovery partitions if you're in a hurry, but it certainly wouldn't hurt.

---

### Post by oldfred on 2011-04-03
Window has to boot from a primary partition and win7 uses two. One is a hidden (in windows) boot recovery of only 100MB.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first.
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Jerry N on 2011-04-03
DO NOT use gparted to resize your main Windows 7 partition, the biggest one.  Use the tools in Windows 7 disk manager instead.  You would likely corrupt the partition using gparted.  Before diving into this operation, do some searching of these forums so see what others have done and would recommend when you have a computer that has the 4 allowable primary partitions already in use.  You will have to delete something.  If you have the option to created a DVD set of Windows re-install disks, do that before you change anything.  Beyond that, I would suggest using gparted to do all you partitioning before you start the Ubuntu installation.  Be patient and learn all you can about partitioning BEFORE you use gparted.  Or you can do like a lot of us and learn through your mistakes.

Jerry

---

### Post by Sidewinder1 on 2011-04-03
I believe that Jerry N is correct; isn't it wonderful how Micro... now rigs their systems to bork if one does not use their software to perform what should be a standard function. I know it *was* OK to use Gparted with XP, as that is what I did, successfully, I might mention.
That's only one of the reasons I kicked Micro to the curb in 2007 and haven't looked back.

Side

---

### Post by Jerry N on 2011-04-03
> **Sidewinder1 said:**
> I believe that Jerry N is correct; isn't it wonderful how Micro... now rigs their systems to bork if one does not use their software to perform what should be a standard function. I know it *was* OK to use Gparted with XP, as that is what I did, successfully, I might mention.
That's only one of the reasons I kicked Micro to the curb in 2007 and haven't looked back.

Side

I doubt that Microsoft "rigs" their systems to "bork" on gparted.  There is nothing standard about gparted except in the Linux world, which is a small subset of the computer world, so why should Microsoft consider it at all?

Jerry

---

### Post by Sidewinder1 on 2011-04-03
Agreed, if they do not consider me, I will not consider them. Pretty simple IMHO.
Side

---

### Post by jkb609gi8 on 2011-04-03
Thanks for the input people. 

I think I will focus my study to learning how to use the Wins7 partition program and at least shift windows to one end and free up 350 Gigs ( Out of the 500 total) to set aside. 

I would like to put "solved" on this thread, but I don't know if I can make that happen. In the end I may just forget about a dual boot with windows and just run Ubuntu. The only thing I use windows for is Autodesk MapGuide. I have spend dozens of hours trying to figure out a way to run this program on Linux. eg. WINE 

The free version of Autodesk is available and required to access information from government site, it will not work on a linux system. There is a "pay for" program Autodesk program I would consider purchasing however however they got there hand out for more money every time you change the computer one uses. :guitar: :guitar:

---

### Post by briguy40 on 2011-04-04
My 2 cents worth. Gparted does fine if you use it from a live cd before installing either system. Install Windows first, as otherwise it hijacks the mbr and you have to re-install grub. Not imposible, but why do it if you don't have to? As far as partitions, set up an ntfs, an ext4 or your choice for Linux, and a swap partition. W7 will reformat the ntfs to it's preference, and when you install Ubuntu it will likwise format the ext4 partition if you let it.

---

### Post by oldfred on 2011-04-04
Autodesk is one of those that is windows only. 

A quick search did find a competitor. Depending on what you are doing it may work.

[http://cadngis.blogspot.com/2008/11/which-mapguide-studio-to-use.html](http://cadngis.blogspot.com/2008/11/which-mapguide-studio-to-use.html)

Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by briguy40 on 2011-04-04
I agree with oldfred. Autodesk is one of my running irritations. Another ray of hope here:
[http://www.bricscad.com/en_INTL/bricscad/index.jsp](http://www.bricscad.com/en_INTL/bricscad/index.jsp)
I also agree that on a running W7 system it's safer to use the Windows tools, but still think that a dual boot system is best set up from scratch.

---

### Post by Learning Linux 2011 on 2011-04-04
> **jkb609gi8 said:**
> Recently I purchased a cheap laptop, a Toshiba Satellite C650D that is set up with Windows 7 using a FAT32 file system. (Note: *it maybe NTFS32, what ever it is for Windows 7?*) This computer comes with AMD Vision 64 CPU, 4gigs RAM, & 500gig Hard-drive. When setting up the Windows 7 I had the option of using a 32-bit or 64-bit file system, and I opted for the 32-bit system.


I have made a mirror backup of the entire hard-drive. I wish to partition this laptop to a dual boot Ubuntu as the primary system. Since my windows 7 is set up for 32-bit, which version of Ubuntu should I use, the 32-bit system or 64-bit system? I have both versions of Ubuntu 10.10.


I have also been reading the Ubuntu documentation "Pre-Partitioning for Multi-Boot Systems". I barely have the intellectual ability to understand this, of course I am in a bit of a hurry, lacking Patience to study the wikipedia terminology. Any ideas or advice on a simple approach to setting up a dual boot Ubuntu 10.10 with existing OEM Windows7?:confused:

Did you use the entire disc for Windows 7?  If so you can use Windows 7 to "shrink" that partition, then you would have some free space for Linux.  Make sure you defragment the drive before you do though.
I would boot from a Windows 7 DVD to do it if I were you.

Bear in mind that Windows won't be able to access Linux's normal file system (the 'ext' file system). (although Linux can access Windows' NTFS and FAT32).

There is no NTFS32.  Either FAT32 or NTFS.

I would probably use the 32-bit version of Linux.

You can also just download Oracle's VirtualBox and install Linux inside of Windows.

---

### Post by Learning Linux 2011 on 2011-04-04
> **jkb609gi8 said:**
> Thanks for the input people. 

I think I will focus my study to learning how to use the Wins7 partition program and at least shift windows to one end and free up 350 Gigs ( Out of the 500 total) to set aside. 

I would like to put "solved" on this thread, but I don't know if I can make that happen. In the end I may just forget about a dual boot with windows and just run Ubuntu. The only thing I use windows for is Autodesk MapGuide. I have spend dozens of hours trying to figure out a way to run this program on Linux. eg. WINE 

The free version of Autodesk is available and required to access information from government site, it will not work on a linux system. There is a "pay for" program Autodesk program I would consider purchasing however however they got there hand out for more money every time you change the computer one uses. :guitar: :guitar:

If you decide to go with Linux exclusively, you can still install Windows inside Linux using virtual machines.
like VirtualBox, VMWare, etc.

---

### Post by jkb609gi8 on 2011-04-04
Just to remind all, this cheap (450dollarbestbuy) Toshiba came right out of the box, sealed never opened and with the OEM it just booted right up already loaded, all I had to do is just had to check off my location. It also came pre-bloated too!

Well I am leaning towards just loading the Ubuntu by it's self. I went into windows7 partition editor was able to create an unallocated space; Of course this is useless as one cannot have five partitions. Windows is a bloated pig even at partition level. It would not allow more than half of its allocated space in the primary O/S to be shrunk. Apparently it needs 230 gigs to fit its special files onto away from majority of the clusters. The disk has been checked for errors and defragged twice.

What I am going to do is remove the hidden partition that is 18gig in size, this one is not label for it is use.  Gparted just says its hidden. The 10gig hidden partition that is labeled HHDrecovery I will keep.

I will use the windows7 partition editor to remove this one primary partition, then see if the computer reboots. If it doesn't I will just go straight to formating the whole HHD for Ubuntu.

---

### Post by jkb609gi8 on 2011-04-04
P.S. I will wait and go have something to eat, so I can see if there are any more suggestions.

---

### Post by oldfred on 2011-04-04
Windows has a small 100MB boot/recovery partition that is normally hidden in windows. You have to have a windows repair CD to fix the main partition if you delete the 100MB boot partition. 

You should make the vendor recovery CDs. They will allow you to restore hard drive to just the way it was when you purchased it. It is more of a compressed drive image. If you are keeping windows you should make a windows repair CD. You may need it.

If you are going to dual boot include an extra NTFS partition for any data you have in both systems. I put Firefox & Thunderbird profiles in my NTFS partition and still have them there, even though I rarely boot XP.

---

### Post by jkb609gi8 on 2011-04-05
Well I have "learned a lot" over the past 40 hours trying to make my new Laptop a dual boot. I have succeeded and the computer opens to Linux Ubuntu by default and Windows 7 if directed so.....

I had read through dozens of pages of advice, finally I used the Winsdow7 partition editor to shrink the main partition to free up an unallocated space. Then I went to the Ubuntu's live disc and used Gparted to delete one of the windows partitions, move the remaining windows partitions to one side of the hard disk, and format the unallocated space into a extended partition containing two logic partitions.

If you remember I had four Windows partitions on my this new Toshiba computer, three being hidden, one is the Win7 boot loader, (*?something new since Windows XP?*) and of the other two, one being 11gigs in size,(perhaps 32-bit)labeled as HHD-recovery, and the other being 19gigs with no label. I assumed the 18gig hidden partition was the 64-bit backup O/S. However get this! When I boot up now, it goes into the new Linux boot loader, and that lists all the partition's complete details. The 11-gig hidden partition I kept is listed as being a Vista version of Windows.

The only problem now is that Ubuntu will not connect to the wireless internet. The wireless internet still works well when using Windows 7. Also the clock lost 5 hours on both O/S's, I had to go into the BIOS to correct it. The wireless connection problem is another problem perhaps for new forum thread.

Thanks everybody!  :popcorn:

---

### Post by oldfred on 2011-04-05
Windows 7 created a new 100MB hidden in windows boot/recovery partition so you can encrypt the main partition and to get users used to it as when they future gpt (replaces 25yr old MBR) partitioning happens in windows you will need it. Macs already have gpt and Ubuntu boots from gpt, windows only currently reads gpt unless you have efi not BIOS.

Vendor recovery partitions usually use Vista for some reason. Even users with XP (possible downgrade from Vista when that was allowed) have Vista recovery partitions. This is just an image of your drive as it was purchased or total restore. It will erase everything, so you have to have backups before using it and have to go thru complete reconfiguration as you have done. Better to just do a full backup after all the reconfiguration you have done. You should make one or two sets of the DVDs as a backup but I would not plan on using it.

---

### Post by Jerry N on 2011-04-05
> **jkb609gi8 said:**
> 

The only problem now is that Ubuntu will not connect to the wireless internet. The wireless internet still works well when using Windows 7. 

Have you tried connecting to the internet through an ethernet connection?  From there you may be able to get the appropriate driver for your wireless.

Jerry

---

