---
title: "Ubuntu 9.10 Installation Questions"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Mike Green9 on 2010-02-03
[FONT=Verdana][SIZE=2]Feb.03.2010[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Hi. This is my first post.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I installed Ubuntu 9.10 on my DELL Desktop. I am set up with a multi boot XP and Windows 7. I have 2 Hard Disks, the second Disk is mostly made up of image backups of the first. There is 300+ gb of available and unpartitioned space at the "bottom" of the second hard Disk.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I will try to be as brief as I can, but clearly I am a newbie, so please bear with me.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]This is a picture of my 2 Hard Disks under Windows 7:[/SIZE][/FONT]
 
[FONT=Verdana][FONT=Verdana][SIZE=2]**Disk 0**[/SIZE][/FONT][/FONT][FONT=Verdana][SIZE=2] (Quad boot - used EasyBCD to edit boot)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 1 C: NTFS XP System[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 2 D: NTFS Data[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 3 E: NTFS Data[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 4 F: NTFS Data[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 5 G: NTFS Data[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 6 H: NTFS Windows 7 System Active[/SIZE][/FONT]
 
[FONT=Verdana][FONT=Verdana][SIZE=2]**Disk 1**[/SIZE][/FONT]
[/FONT][FONT=Verdana][SIZE=2]Partition 1 I: NTFS XP System Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 2 J: NTFS Data Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 3 K: NTFS Data Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 4 L: NTFS Data Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 5 M: NTFS Data Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 6 N: NTFS Data Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 7 O: FAT32 Data [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 8 P: FAT32 Data[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 9 H: NTFS Windows 7 System Backup[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]300+ gb unallocated[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I downloaded the Ubuntu 9.10 ISO file and burned it to a CD. I booted the cd and kicked off the installation.[/SIZE][/FONT]
 
[FONT=Verdana]**_[SIZE=2]The First Question[/SIZE]_**[/FONT]
[FONT=Verdana][SIZE=2]The installation displays my partitions in a strange (to me) way.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Disk 0**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 1 /dev/sda1[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 2 /dev/sda5[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 3 /dev/sda6[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 4 /dev/sda7[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 5 /dev/sda8[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 6 /dev/sda3[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]**Disk 1**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 1 /dev/sdb1[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 2 /dev/sdb5[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 3 /dev/sdb6[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 4 /dev/sdb7[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 5 /dev/sdb8[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 6 /dev/sdb9[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 7 /dev/sdb10[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 8 /dev/sdb11[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Partition 9 /dev/sdb3[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]300+ gb unallocated[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I get the fact that "sd**a***" refers to Disk 0, and "sd**b***" refers to Disk 1.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Why is Partition 2 /dev/sda**5** and not /dev/sda**2**, and Partition 3 /dev/sda**6** and not /dev/sda**3**, etc. ? Why is Partition "**X**" not /dev/sda**X**?[/SIZE][/FONT]
 
[FONT=Verdana]**_[SIZE=2]The Second Question[/SIZE]_**[/FONT]
[FONT=Verdana][SIZE=2]I chose to manually deal with the partitioning. I clicked on the unallocated 300+ gb space, and made it the Ubuntu partition - 15 gb, ext3, with the Mount Point "/".[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]How do I then deal with the Swap Space? It didn&#8217;t allow me to "ADD" another partition in the remaining free space so that I may allocate it as Swap Space. I ignored the No Swap Space warning, and continued.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The installation added another partition (#10) to Disk 1: /dev/sdb4 ext3.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]The installation completed successfully, and I re-booted with Windows 7.[/SIZE][/FONT]
 
[FONT=Verdana]**_[SIZE=2]The Third Question[/SIZE]_**[/FONT]
[FONT=Verdana][SIZE=2]How to add a Ubuntu boot option using EasyBCD (2.0 Beta)?[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Currently, I have set up a multi (quad) boot using EasyBCD (I can boot XP, either of my Windows 7, or a Windows 7 on an external USB). (During the Ubuntu installation, I went to the Advanced tab and removed the option for the installation to handle the MBR.)[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]When I invoked EasyBCD I had a problem:[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I "Add/Remove Entries". I then selected "Linux/BSD". I got a "*BootGrabber.exe has stopped working*" error message. Not sure how to deal with this - so I ignored the error message window.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I then selected GRUB (Legacy) for Type. Is this correct???[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]What do I select for Device???[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]And what about the box "GRUB isn&#8217;t installed to MBR/bootsector"???[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]&#12288;[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]On another note - just a comment about the last screen of the Install. It says something like:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]*"....the following partitions are going to be formatted Partition #4 of SCSI1 (0,1,0) sdb as ext3...."*.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Strange verbiage - probably a holdover from days long gone. If I had not seen a reference to "*/dev/sdb4*" (the newly created partition), I would have aborted. [/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]I am quite exited about this new adventure, and I would sure like to be able to boot Ubuntu. Any help will be greatly appreciated.[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]Thanks,[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]MG....:D[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]&#12288;[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]&#12288;[/SIZE][/FONT]

---

### Post by cariboo on 2010-02-03
> Why is Partition 2 /dev/sda5 and not /dev/sda2, and Partition 3 /dev/sda6 and not /dev/sda3, etc. ? Why is Partition "X" not /dev/sdaX?

The partitions, are probably extended/locigal partitions that's why it seems to skip a lot of partition numbers.

> How to add a Ubuntu boot option using EasyBCD (2.0 Beta)?
Currently, I have set up a multi (quad) boot using EasyBCD (I can boot XP, either of my Windows 7, or a Windows 7 on an external USB). (During the Ubuntu installation, I went to the Advanced tab and removed the option for the installation to handle the MBR.)

When I invoked EasyBCD I had a problem:

I "Add/Remove Entries". I then selected "Linux/BSD". I got a "BootGrabber.exe has stopped working" error message. Not sure how to deal with this - so I ignored the error message window.

I then selected GRUB (Legacy) for Type. Is this correct???

What do I select for Device???

And what about the box "GRUB isn’t installed to MBR/bootsector"???

Grub is the preferred boot loader, it will list all of your operating systems in it's menu. You can install it while running Ubuntu. If you can't start Ubuntu, have a look [here]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") for a howto about installing grub from the Live CD.

Keep in mind that Linux is not Windows, most of what you know about Windows is of no real using when running a Linux variant.

To help sort out your partitions problems, you can use the Live Cd to get to the desktop, once there, open an Applications->Accessories->Terminal and type:

```
sudo fdisk -l
```

paste the output in your next post. To copy and paste, just highlight the text with your mouse, leave the terminal open, and once you have Firefox running and signed on to the forum just click the mouse wheel/both mouse buttons, and it will automagically paste the text for you.

---

### Post by Mike Green9 on 2010-02-03
[SIZE=2]Hi.[/SIZE]
 
[SIZE=2]Thanks for the response. I think it was a bit more than I asked for - at least until I learn more.[/SIZE]

[SIZE=2]I just want to be able to boot with the Ubuntu partition by providing another option using BCDEasy. So I tried EasyBCD again and added "Entry #5" as you can see below:[/SIZE]
[SIZE=2]....[/SIZE]
[SIZE=2]....[/SIZE]
[SIZE=2]....[/SIZE]
[SIZE=2]Entry #4[/SIZE]
[SIZE=2]Name: USB W7 bkp[/SIZE]
[SIZE=2]BCD ID: {10203afb-edb8-11de-a3ca-e2b506438538}[/SIZE]
[SIZE=2]Device: Deleted Partition[/SIZE]
[SIZE=2]Bootloader Path: \Windows\system32\winload.exe[/SIZE]

[SIZE=2]**Entry #5**[/SIZE]
**[SIZE=2]Name: Ubuntu Disk 1[/SIZE]**
**[SIZE=2]BCD ID: {10203afc-edb8-11de-a3ca-e2b506438538}[/SIZE]**
**[SIZE=2]Drive: C:\[/SIZE]**
**[SIZE=2]Bootloader Path: \NST\AutoNeoGrub0.mbr[/SIZE]**
 
 
[SIZE=2](Do I choose Grub Legacy or GRUB 2 ??)[/SIZE]

[SIZE=2]This does boot from the correct Ubuntu partition, but it takes me into GRUB. What do I need to do in EasyBCD to be able to boot directly into the Ubuntu Desktop?[/SIZE]


[SIZE=2]Thanks,[/SIZE]

[SIZE=2]MG...[/SIZE]

---

