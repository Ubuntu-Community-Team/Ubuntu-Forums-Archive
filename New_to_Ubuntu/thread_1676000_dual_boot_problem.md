---
title: "dual boot problem"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by antiprice666 on 2011-01-26
I installed Ubuntu 10.04.1 LTS 64 bit for desktop on a usb drive and it ran fine.  I tried to install the full version on my harddrive. My intention was to dual boot with windows xp home edition and have Ubuntu partition my harddrive for me during installation.  While it was partitioning my harddrive it said an error occured and the partitioning was aborted.  Now when I try to install Ubuntu I no longer get the option to partition.  It only gives me the option to erase windows and install Ubuntu only.  I would like to dual boot with XP until I am comfortable with Ubuntu.  
     If I have to manually partition my drive I would appreciate a link (if possible) to a partition program or would it be better to do a fresh install of Windows and have windows partition my drive for me? I understand a fresh install may be best but I would like to avoid it if possible.
     I am new to the transition from Windows to Linux and am still foggy on the process.  Thanks in advance for any replies.

---

### Post by rocthrttle on 2011-01-26
"gparted" is the best partitioner in gnome. it should be in the system>administration> menu on your 10.04LTS livecd desktop. i had trouble with windows partitioning only once. it was because the user had the entire drive compressed. you can tell because the letters are blue instead of black and when in right click properties on the drive it has the box called "check this box to compress drive to save space" checked. 

***(backup the whole drive before doing the decompression. you may lose everything if it goes sour)***

decompress the drive by unchecking the box and clicking ok (depending on the drive size and speed of the machine it can take hours). also use ultradefrag to defrag the whole drive before doing any partitioning/installing.

your windows partition should be ok as long as you can boot into it. 

[http://ultradefrag.sourceforge.net/](http://ultradefrag.sourceforge.net/)    <---best defragger ever

---

### Post by amsterdamharu on 2011-01-26
If you can still start from the live usb/CD could you post the output of the boot info script?

Start Ubuntu live CD/usb and download the [boot info script]("http://sourceforge.net/projects/bootinfoscript/").

Copy it to your Desktop (it usually is in Downloads).

Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script055.sh
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code]&#91;CODE]Your pasted stuff&#91;/CODE]

There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using &#91;CODE]Your pasted stuff[/CODE]

---

### Post by Cavsfan on 2011-01-26
Also, you would want to choose the manual option to define where you install Ubuntu instead of letting 
Ubuntu partition the harddrive during installation at least that is what I did.
Also the tutorial in my sig might be of interest to you as you are dual booting.
I would leave windows as a backup, but that is just my opinion.

My tut. fixes it to where even when a new kernel is installed, you still bootup on the latest kernel w/o having to edit anything.

---

### Post by antiprice666 on 2011-01-26
> **amsterdamharu said:**
> If you can still start from the live usb/CD could you post the output of the boot info script?

Start Ubuntu live CD/usb and download the [boot info script]("http://sourceforge.net/projects/bootinfoscript/").

Copy it to your Desktop (it usually is in Downloads).

Run the following commands:
```
cd ~/Desktop
sudo bash boot_info_script055.sh
```To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: ```
[CODE]Your pasted stuff
```

There should be a file on your Desktop named RESULTS.txt please post the content of this file here too using ```
Your pasted stuff
```
  

     I downloaded the boot info script and did what you ask.  Here is the first thing you asked me to paste:
```
[CODE]Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

```

    Here is the second:```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     7,837,695     7,837,664   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A8DC-A953                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CA5818085817F1C5                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer
```


hope I got all that right

---

### Post by amsterdamharu on 2011-01-27
You have 2 harddisks, one is fat32 and one is ntfs. On what harddisk would you like to install?

Both harddisks have one partition that use the entire size of the harddisk.

Depending on how full they are you can resize it using gparted on the live CD/DVD but it could be risky if something goes wrong while resizing and moving data so I suggest defrag in Windows first.

To start gparted from the live CD you can press alt + F2, type "gksu gparted" (no quotes) and click run.

You need about 8GB minimum if you want to install everything on one partition.

Later when you install you need a minimum of 2 partitions and preferably 3:
1. / (called root) here is where everything goes needs to be min 8GB
2. swap twice the size of your memory for swap
3. /home this is optional but if you have it all your personally created stuff and program settings will go in here so you could re install without loosing this the size of this depends on how much stuff you plan to put here (foto's video's documents)

---

### Post by Rushyang on 2011-01-27
I have faced the similar problem when my all partition types where "dynamic".

Make sure your other partitions rather than windows, are secondary on dynamic. **If they are dynamic, then all the partitions will be shown as a single partition in your ubuntu installation. **

---

### Post by Cavsfan on 2011-01-27
**amsterdamharu**, I believe they have revised the size of the swap file, I initially had mine set to twice my RAM size which is 4GB.
I was told to use 1024MB as a GB and so I had SWAP size of 8192. This was too big really and now I have it 2048MB.

Also, I only have 2 partitions set aside for Ubuntu one etx4 with "/" that is almost 100GB and the swap is only 2GB and 
it seems to work well.

But, I wanted to mention that defragmenting from windows is probably the best option. I found that Puran Defrag Free is a very good
program that will run in XP.
Here is the link to obtain that:
_**[http://www.dkszone.net/puran-defrag-free-all-in-one-disk-defragmenter-for-windows](http://www.dkszone.net/puran-defrag-free-all-in-one-disk-defragmenter-for-windows)**_

An XP disk partition can be resized with the Disk Management program. I don't remember where it is, but you can probably search for it 
if you cannot find it in Control Panel.

You would right click on the partition you want to shrink and then click "Shrink Volume".
Hopefully that will free up enough room on your HD for your Ubuntu installation.

Then once you have freed enough space, you don't have to do anything else in windows.
Just put the Ubuntu install disk in and reboot and when it get to the point of asking click in the middle "Manual selection" and you will see the free space you have created.
You can only have 4 primary partitions, so I would make one primary partition for swap 2024MB and then after that use the rest of the free space for ext3 and the mount point will be "/" in the drop down list.
Then you should be good to go.

Myself I have a 500GB drive and have 1 partition for Windows 7 and 2 for Ubuntu, so I actually have one primary partition that is unused.

The reason I mention defragmenting to be able to shrink your partition is that in Vista and windows 7, there is a disk journal file that becomes very huge 
and fragmented and it will not defragment with windows running. It usally is named **C:\$Extend\$UsnJrnl:$J:$DATA**
The Puran program above has a Boot Time Defragment, which can do the job while windows is not running. This may be beneficial to you as it was to me.
I ended up having to delete this journal file as it was put at the end of the drive preventing the shrinking necessary for creating another partition.

If you cannot get the end of the disk free and the above mentioned file is occupying that space at the end, you may need to enter this command from windows in a DOS prompt:
```
FSUTIL USN DELETEJOURNAL /D C:
```You can safely delete it and it will be re-created without issues. You will loose any restore points, but that shouldn't be a problem as they will again be created afterward.

Like I said above, I recommend that you keep XP installed if nothing else for a backup.
I don't know as much about Ubuntu as some people here, but I know windows fairly well.
And I hope this helps! :D

---

### Post by antiprice666 on 2011-01-27
> **amsterdamharu said:**
> You have 2 harddisks, one is fat32 and one is ntfs. On what harddisk would you like to install?

Both harddisks have one partition that use the entire size of the harddisk.

Depending on how full they are you can resize it using gparted on the live CD/DVD but it could be risky if something goes wrong while resizing and moving data so I suggest defrag in Windows first.

To start gparted from the live CD you can press alt + F2, type "gksu gparted" (no quotes) and click run.

You need about 8GB minimum if you want to install everything on one partition.

Later when you install you need a minimum of 2 partitions and preferably 3:
1. / (called root) here is where everything goes needs to be min 8GB
2. swap twice the size of your memory for swap
3. /home this is optional but if you have it all your personally created stuff and program settings will go in here so you could re install without loosing this the size of this depends on how much stuff you plan to put here (foto's video's documents)

    First off I only have one HD (300 gigs reading 288 for some odd reason).  I may have partitioned it or something (I don't know) when I first installed windows. I don't know what mistake I made to have one fat32 and one ntfs (I dont know the difference nor which is better).
     Currently I am only using about 30 gigs of that drive.  I have xfered everything important to a mem. stick so reformating and starting fresh seems like my best move from here.  I tried using gparted from the live usb I made but it only gives me the option to partion the usb drive.  Should I do a fresh install of windows and let it partition my drive?  If so am I correct in thinking that I will need 4 partitions total?  One for windows and 3 for Ubuntu?
    Any other suggestions are greatly appreciated.  Thank you

---

### Post by presence1960 on 2011-01-27
> **antiprice666 said:**
> First off I only have one HD (300 gigs reading 288 for some odd reason).  I may have partitioned it or something (I don't know) when I first installed windows. I don't know what mistake I made to have one fat32 and one ntfs (I dont know the difference nor which is better).
     Currently I am only using about 30 gigs of that drive.  I have xfered everything important to a mem. stick so reformating and starting fresh seems like my best move from here.  I tried using gparted from the live usb I made but it only gives me the option to partion the usb drive.  Should I do a fresh install of windows and let it partition my drive?  If so am I correct in thinking that I will need 4 partitions total?  One for windows and 3 for Ubuntu?
    Any other suggestions are greatly appreciated.  Thank you

The fat32 is a bootable usb disk. See here:

```
Drive: sda ___________________ _____________________________________________________

[COLOR="Red"]Disk /dev/sda: 4012 MB, 4012900352 bytes[/COLOR]
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     7,837,695     7,837,664   b W95 FAT32
```

First defrag windows at least once preferably twice. Back up all data you don't want to lose to another media. Then boot the Ubuntu Live CD and choose try ubuntu. When the desktop loads go System > Administration > Gparted Partition Editor. Shrink the sdb1 partition (windows) to create unallocated space for Ubuntu. Install Ubuntu to that unallocated space using the install to largest free space option on the installer.

---

### Post by antiprice666 on 2011-01-27
Thank you for clearing up the 2 harddrive confusion.  I am not using a live CD.  I am using a USB stick.  Does it matter?

---

### Post by antiprice666 on 2011-01-27
thank you for clearing up the 2 harddrive confusion.  I am not using a live CD.  I am using a USB stick.  Does it matter?  I should still be able to partition my harddrive using the stick?

---

### Post by wilee-nilee on 2011-01-27
> **antiprice666 said:**
> thank you for clearing up the 2 harddrive confusion.  I am not using a live CD.  I am using a USB stick.  Does it matter?  I should still be able to partition my harddrive using the stick?

Post 10 was the only good advice so far, other then posting the bootscript. 

Yes you can use gparted click the dropdown in the top right corner of gparted to show the HD. You should do a reboot to XP before installing Ubuntu though so that it runs a chkdsk automatically, and you know it is still working.

---

### Post by presence1960 on 2011-01-27
> **antiprice666 said:**
> thank you for clearing up the 2 harddrive confusion.  I am not using a live CD.  I am using a USB stick.  Does it matter?  I should still be able to partition my harddrive using the stick?

yes, follow the instructions I provided. You can use windows disk defragmenter or the software someone else mentioned to defrag XP. Then boot the Ubuntu Live CD/USB and choose try ubuntu. When the desktop loads use gparted (System > Administration > Gparted Partition Editor to shrink windows.

---

### Post by antiprice666 on 2011-01-27
Before I get started am I correct in assuming that,  since my harddrive is actually one giant partition as it exists now,  I am shrinking the windows partition to make room for the Ubuntu partition.  Then I will be dividing the space I created into 3 partitions?  All after I defrag of course.

---

### Post by presence1960 on 2011-01-27
> **antiprice666 said:**
> Before I get started am I correct in assuming that,  since my harddrive is actually one giant partition as it exists now,  I am shrinking the windows partition to make room for the Ubuntu partition.  Then I will be dividing the space I created into 3 partitions?  All after I defrag of course.

correct. You can use gparted from the Live USB to create the 3 ubuntu partitions after creating space. Then at the partitioning window of the installer you will need to select choose partitions manually.

---

### Post by antiprice666 on 2011-01-27
OK I know this next part may be remedial but could you please advise me on the partition sizes?  I have a 288 gig harddrive.  I plan to shrink the windows partition to 100 gigs (nice round number) then use the rest for Ubuntu.  Also will I be naming these Ubuntu partitions and if so what should I name them?  I know it can be anything but whatever is "standard" would be appreciated.  Also as I understand things, one partition is based on the amount of RAM I have (4 gigs).  I could be wrong with this part though.

---

### Post by presence1960 on 2011-01-27
> **antiprice666 said:**
> OK I know this next part may be remedial but could you please advise me on the partition sizes?  I have a 288 gig harddrive.  I plan to shrink the windows partition to 100 gigs (nice round number) then use the rest for Ubuntu.  Also will I be naming these Ubuntu partitions and if so what should I name them?  I know it can be anything but whatever is "standard" would be appreciated.  Also as I understand things, one partition is based on the amount of RAM I have (4 gigs).  I could be wrong with this part though.

There is no right or wrong, partitioning depends on your needs. I usually give 15-20 GB for /, swap = to installed RAM. With 4GB of installed RAM the only time you may use swap is for hibernation. You can use the rest for a separate /home or a /data partition.

Personally I keep an NTFS partition for shared data between windows & linux. There can be problems writing to a windows OS partition due to permissions being handled differently between linux & windows. Again it is your choice.

---

### Post by antiprice666 on 2011-01-27
**presence1960<== **thanks for all your help.  I'm new to the crossover from windows to Linux and have been digging around the net gathering whatever info I can get.  I have a general idea of whats going on.  I know my questions have probably been answered a million times over in previous threads but when I use the search I don't come up with my exact problem.  Just similarities.  Thanks again for your time.  You have been a great help.  I'll close this thread as solved.  If anything comes up from here it will probably be a whole new subject.

LOL I would post this thread as solved if I knew how.

---

### Post by presence1960 on 2011-01-27
> **antiprice666 said:**
> **presence1960<== **thanks for all your help.  I'm new to the crossover from windows to Linux and have been digging around the net gathering whatever info I can get.  I have a general idea of whats going on.  I know my questions have probably been answered a million times over in previous threads but when I use the search I don't come up with my exact problem.  Just similarities.  Thanks again for your time.  You have been a great help.  I'll close this thread as solved.  If anything comes up from here it will probably be a whole new subject.

LOL I would post this thread as solved if I knew how.

Top Right >  Thread Tools (in red) to mark as solved

---

