---
title: "Upsize partions on new HDD - Dual Boot - 11.04 ON Win7 - Grub"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by W.Gates on 2011-08-12
Good day Gentlemen, this is my first post in this forum forgive any indiscretions as non are intended. I have been an MCSA for the last 20 years, but recently I have been very impressed indeed with Ubuntu 11.04, having dabbled with and then discarded Susi Linux some five years ago.
 
My problem my be summarised as outlined below:
 
Using the downloadable ISO I installed Ubuntu 11.04 as a dual boot on a Win7 100GB HDD on my Lenovo T61 laptop. No problem they both rock and I'm very impressed.
During the installation procedure I selected the largest partition sizes available from the Ubuntu installer wizard being 25GB Extended split into 18GB Ext4, and 3.2GB and 3.2 GB swaps (I couldn't suss out any way of manually increasing them any further)
 
I found that the 11.04 Startup Manager application didn't work at all, so I downloaded and installed Grub Customizer 2.1..and that did work after a fashion.. certainly enough to actually effect changes in the grub configuration settings.
Despite this...
 
Everything worked so well on the 100GB HDD that I decided to transpose the entire disk image to a new 500GB WD Scorpio and make the dual boot my main working disk.
Using Acronis I imaged off the 100GB installation selecting the partition by partition, and retain disk signature options.
 
I then recovered the image to the new 500GB HDD and everything works beautifully on the new HDD.
Except of course all the partitions are still the same size.
 
I won't waste your reading time recounting everything that I have done using Acronis Disk Director (V Good) and Gparted (not so good), but needless to say whatever I do Grub won't have it, and I have lost count of the times that I have re-recovered the good image.
Gentlemen.. basically I want to increase the partion sizes to apportion larger partitions to both Win 7 and 11.04 and obviously I'm missing something somewhere.
 
Fdisk -l -u produces..
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f011ed1
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048       53247       25600    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           53248   146956287    73451520    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       146958334   195371007    24206337    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       189134848   195371007     3118080   82  Linux swap / Solaris
/dev/sda6       146958336   182896639    17969152   83  Linux
/dev/sda7       182898688   189120511     3110912   82  Linux swap / Solaris
Partition table entries are not in disk order
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8755f7cf
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   234436544   117218241    7  HPFS/NTFS
 
Your advice and guidance would be much appreciated.
 
PS If I were Bill Gates I would be looking very seriously indeed over my shoulder at this operating system. I have begun using it in preference to Win7.

---

### Post by LowSky on 2011-08-12
gparted can easily do this, but you cannot be using the hard disk while partitioning, as you may know.

Grab that Ubuntu LiveCD, start it up, gparted may or may not be installed but you will need it.

Start gparted. find the partitions and move them. you created each partion ontop of another so expanding cannot be done without first moving the partitions to make room.

first take the extended partition and add space... then subtract from the front  of the extended partition until you made extra room for the NTFS partition. Then you can also change the sizes of your partitions inside the extended. Note You can loose one of the swap partitions. You really don't need them at all except for legacy purposes, or if you use suspend/hibernate. Most users use their RAM as the space to use for SWAP. Personally I don't use more than 2GB.

Also advanced user like to separate their /home folder into its own partition as Ubuntu will use this folder for user configuration and your own personal items. The / (root) partition will contain the rest. This way if the system goes toes up, you can save your personal settings, and after a re-install all your settings will reload if you recreate the same user.

Hope this makes sense. If you are having issues with Grub you can always re-install it using the liveCD as well. see below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
> 
Recovery Using the Ubuntu Alternate/Install CD
This section explains how to rescue Grub, using the Ubuntu Alternate/install CD.

Enter your computers BIOS to check computer can boot from CD ROM. If you can boot from CD, insert CD ROM into drive. Exit the BIOS (if needed save your settings to make sure the computer boots from the CD ROM).
When the Ubuntu splash screen comes up with the boot: prompt, type in rescue and press enter.
Choose your language, location (country) and then keyboard layout as if you were doing a fresh install.
Enter a host name, or leave it with the default (Ubuntu).
At this stage you are presented with a screen where you can select which partition is your root partition (there is a list of the partitions on your hard drive, so you are required to know which partition number Ubuntu is on). This will be dev/discs/disc0/partX, where the X is a partition number.
you are then presented with a command prompt (a hash).
type

$ ```
grub-install /dev/XXX
```
where XXX is the device of your Ubuntu install. (eg: grub-install /dev/""hda"" or grub-install /dev/""sdb"" ). Note: newer 2.6.xx kernels call all hard disks ""sdx"" now but not sure if grub does.

---

### Post by varunendra on 2011-08-12
Moving a partition that contains data (a lot of..) often takes too long compared to normal copy-paste. Hence I'd do it this way-

[LIST=1]
[*]Make an image of Ubuntu partition using clonezilla (OP may use Acronis if he trusts it)
[*]Delete the Ubuntu and swap partitions (in fact entire extended partition)
[*]Resize Win partition from within it (if it allows, or use gparted)
[*]Recreate fresh partitions in the remaining space (extended+logicals in it)
[*]restore ubuntu image on desired partition,
[*]Install grub manually using live CD
[/LIST]
By the way, as much as I remember, I recently restored a physical installation image of Win7 on VBox, don't remember if I needed to fix booting afterwards, but it worked. So I think (but am not sure) that the same image-resize-restore thing should work with Win7 partition also. But the OP is an MCSA, so he should know better.

---

### Post by W.Gates on 2011-08-12
Thank you Gentlemen... Solution..
 
I used the ISO installation disk - Install Ubuntu -> select Something Else option to open an excellent manual partitioning facility screen (hereinafter referred too as Ubuntu Partitioning Facility UPF) and that's where the deed was done at least for the Ext4 extended partion (from 25 GB to 178 GB) ...Note the NTFS partition had been previously extended using Achronis Disk Director..and then the remaining 'slack' space taken up using UPF, but I'm certain that the UPF could have handled the NTFS task as well.

Ok; once I had sorted all the partitioning out, all that remained was for me to identify the Root sector.. which I think I got right more by luck than judgement.. and the installation proceeded as normal. With grub being overwritten by the new installation process
I had to enter user details again and a new host name but that was a minor problem, and some of my originally installed applications didn't "we didna get them all back Cap'n" all reappear in the final mix but that too is a minor problem, however all my data did, and Evolution was found to be still configured as in the 'old' installation.

The important thing is that the original Win7 and Ubuntu installations are now sitting on 300 GB and 178 GB respectively and the grub loader is working as it should.

The system had the last "Gotcha" though as the mouse and trackpad completely stopped working in the new installation within five minutes of completion and nothing would work to get either going again; so I reinstalled again.

Thank you for your help.

---

