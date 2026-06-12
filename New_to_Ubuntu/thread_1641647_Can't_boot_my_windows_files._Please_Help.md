---
title: "Can't boot my windows files. Please Help"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by Nkpodi on 2010-12-09
Hello,
I'm a beginner with linux and I just installed it unto my gateway desktop. When going through the install for the new Ubuntu 10.10, I chose the option for partitioning the hard drive and the system automatically created the partition /dev/sda1 for my windows vista but now when I restart my computer grub shows ubuntu and windows vista loader (/dev/sda1) and when I go down to select the windows option the screen comes up saying windows is loading files and after about a minute a gateway screen comes on showing the option for restore computer to factory defaults which is grayed out and the other option is to exit and when I clicked that, it just reboots the computer. I tried searching different forums about this issue but could not find anything that was specific to this particular issue. When I go into terminal I do find the partition for the /dev/sda1 but it is recognized as unknown under system. This is what it displays under terminal.


jkpodi@jkpodi-DX4200-09:~$ sudo apt-get install ms-sys
[sudo] password for jkpodi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ms-sys
jkpodi@jkpodi-DX4200-09:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83e6d949

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   27  Unknown
/dev/sda2   *        1276       77826   614888448   83  Linux
jkpodi@jkpodi-DX4200-09:~$ 

I was wondering if there were any solutions.

Thank you

---

### Post by coffeecat on 2010-12-09
I'm sorry, but I have bad news for you. It looks as though the  Windows C: drive has been overwritten with the Ubuntu installation. Let me explain the output you have posted. Partition sda1 is 10.4 GB which would be about the right size for a manufacturer's restore partition. Indeed, what you describe when you choose 'Vista loader' suggests that. The recovery partition is often labelled on the grub menu as the actual windows operating system.

Your partition 2, sda2, with a Linux filesystem must be the Ubuntu one and is 629.6GB in size, which accounts for the rest of the drive.

I don't know how feasible it is to rescue data from where your C: drive would have been. Much of it would be overwritten. Perhaps others might be able to suggest something.

As far as the restore defaults being grayed out, that may be because it is looking for a NTFS partition. That, at least, is doable. Post back if you want help with this.

---

### Post by Nkpodi on 2010-12-09
Do you know of any procedures to restore windows back to the default. I would just like to bring my computer back up to the windows os.

Thank you

---

### Post by wilee-nilee on 2010-12-09
> **Nkpodi said:**
> Do you know of any procedures to restore windows back to the default. I would just like to bring my computer back up to the windows os.

Thank you

You will need a Vista install disc, call the computer vendor and get the OEM set.

---

### Post by coffeecat on 2010-12-09
I have only one thing to suggest to get around the graying out of the restore to default option in the recovery option. That is to reformat partition 2 (sda2) to NTFS. My guess - and it is a guess only - is that the Gateway restore utility is confused by the Linux partition. It won't be able to recognise the filesystem and perhaps that is why it's grayed out.

If you do this it will not recover any personal files or installed applications. It will indeed revert you to factory defaults.

If you want to proceed, this is what you do. Boot up with the live Ubuntu CD. Where it gives you the choice of the installer or trying Ubuntu out, choose the latter and let the desktop load up. Now go to System > Administration > Gparted Partition Editor. Once it's scanned the internal drive(s), you will see the two partitions listed. Highlight /dev/sda2, probably showing as 'ext4' under File System. Go to the Partition menu and choose Format To and then 'ntfs'. You'll see the entry under File System change to ntfs but nothing has been written yet. To commit this, tick on the green tick icon - an 'Apply all operations' message will appear when you hover the mouse over the icon. Let that complete and then shut down and remove the CD. Hopefully, the Gateway recovery utility will now allow you to restore the system, but I cannot guarantee this. I have some experience of some manufacturer's restore utilities but not Gateway - they are all different.

**Edit:** should have emphasised. When in Gparted do nothing to /dev/sda1. That is your Gateway restore partition.

---

### Post by Rubi1200 on 2010-12-09
Forum user Mark Phelps recommends using Windows software to recover Windows partitions:
> If it were my data (and it HAS been before), I would go to the Runtime  Software site, download their trial versions of GetDataBack for NTFS,  and Recover My Files, install them on an MS Windows  box, plug in my damaged drive to that box as an external drive, run the  utilities overnight -- and see the next day how good a job they did of  finding my files.

Another option is Testdisk, but I suspect the chances for recovery may be slim:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Nkpodi on 2010-12-10
Hey,
I tried reformatting the linux partition to NTFS and I then tried restarting the computer and when the computer tried loading back up I received a grub rescue prompt. It seems grub is still installed on the hard drive. I am still able to boot ubuntu from my thumb drive and this is what I get from terminal. 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83e6d949

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   27  Unknown
/dev/sda2   *        1276       77826   614888448    7  HPFS/NTFS

Disk /dev/sdb: 15.9 GB, 15931539456 bytes
64 heads, 32 sectors/track, 15193 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000754cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15193    15557616    c  W95 FAT32 (LBA)


I searched online for ways to uninstall grub but they all use the  recovery cd which I do not have so I was wondering if there was a way to  uninstall from or get past that message.


Thank you

---

### Post by coffeecat on 2010-12-10
You'll need to do two more things from the Ubuntu live CD: set the boot flag onto the first partition and replace the bit of grub code that's still in the mbr.

Boot up with the live Ubuntu CD again and go to the live desktop. Open Gparted partition editor again. Select partition /dev/sda1. Now, Partition menu > Manage Flags. Tick the box against 'boot' and then click on 'close'. I can't remember if you have to apply that with the tick icon. If it has turned green, then click on it.

Now close Gparted and open a terminal which you'll find at Applications > Accessories. Now run these two commands:

```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```I can't remember if you need an internet connection for this. If you get an error with the first command, make sure you are connected - use an ethernet connection if you have problems with a wireless connection. You will get an error after the second command which can be safely ignored.

The second command will installe some code to the mbr (that's the first few hundred bytes) of the hard drive which will allow booting to the partition with the boot flag, so you can now shut down, remove the CD and, hopefully, boot into the Gateway recovery utility.

---

### Post by Nkpodi on 2010-12-10
I can't thank you enough for your help. After installing lilo and changing the MBR, I was able to boot back up to the gateway recovery screen and the option to restore to factory defaults was available. I was able to load back up into windows after that and I'm currently running a software to try and restore as much data as possible that was lost when the partition was created. Thanks again for your help

---

### Post by coffeecat on 2010-12-10
I'm glad you've managed to recover Windows. I hope this episode doesn't put you off Ubuntu or Linux. Unfortunately, there is always a risk that something can go wrong when manipulating partitions, although I'm mystified as to what happened here. You see, normally the Ubuntu installer would create a dedicated swap partition as well as the Ubuntu root partition, which it didn't in your case. 

If you do want to try out Ubuntu without risking your Windows, there is the option of Wubi where you install Ubuntu to a virtual hard drive "within" your Windows C:. See here for more:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

There are disadvantages to using wubi, but ignore most of the negative comments that you might find scattered around the forum. Member Rubi1200, who has also contributed to this thread, has written an excellent guide to repairing wubi in the event of it going wrong. If you want to try wubi, here's the link for your bookmarks.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Good luck!

---

### Post by Quackers on 2010-12-10
Is it possible that you selected "install alongside" other operating systems in the Ubuntu installer? Some have had problems using that method.
If you want to install Ubuntu a second time (and I highly recommend that you do :-)) I would suggest first that you check in Windows Disk Management console how many primary partitions Windows has created. If there are 3 or less that's good.
If those Windows partitions take up all of your hard drive between them (they probably will) you should resize one of them by right-clicking it and selecting "shrink". This will result in some unallocated space. Ubuntu can then be installed to this unallocated space by selecting "specify manually" in the partitioning stage of the Ubuntu installer.

---

