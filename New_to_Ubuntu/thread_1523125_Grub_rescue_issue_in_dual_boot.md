---
title: "Grub rescue issue in dual boot"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by gauravkumar on 2010-07-03
hi all,

I have a windows 7 system. I have installed Ubuntu 10.04 on a external hard disk. Though both of them work fine, like, first its asked which OS  would i like to work on and then i can continue.
But the issue here is when i try to work only on windows without attaching the USB HDD to the laptop, the GRUB RESCUE comes and stuck to that particular screen. it does not even ask for the boot options.
Please help.

Gaurav

---

### Post by Yarui on 2010-07-03
Probably what has happened here is that when you installed Ubuntu on your external drive it installed grub to the MBR of your main drive, wiping out the windows boot system.  When you boot with your USB drive unplugged, the MBR tries to find your /boot partition on your external drive, but it doesn't exist, so it freaks out.  You can do some windows recovery console stuff to restore the MBR to boot into windows, but if you do that you will probably have to go to your boot menu and select USB any time you want to boot to Ubuntu.

---

### Post by telltom on 2010-07-03
I use the Ultimate Boot CD to restore the MBR. Search for it and download. After download, open under filesystem menu. Choose Gag1.0 and follow real simple instructions. Reboot and MBR is back.

---

### Post by Yarui on 2010-07-03
I assume this fixed your problem, right?

---

### Post by philinux on 2010-07-03
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

One option.

When installing to an external disk that might be unplugged at some stage use the "advanced" button at the last stage of the installer.

Then tell it to put grub on the mbr of the external disk.

In win7 you can then use easybcd to boot the external drives grub, thus leaving win7 mbr intact.

Or.

Put grub on the external drive as above and put grub on the mbr of the win7 drive and chainload into the external drive.

To rectify the OP problem. Manually install grub to the external drive and modify /etc/default/grub on the internal drive to disable the os_prober and modify /etc/grub.d/40_custom to chainload. 
 ```
            menuentry "Grub on sdb1" {

            set root=(hd1,1)

            chainloader +1

            }
```

---

### Post by oldfred on 2010-07-03
Another set of instructions similar to above.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by K-Sub on 2010-07-03
I had a similar problem so I used the FIXMBR command in Windows so that I could boot the computer again.  Now my problem is that I would like to remove the Ubuntu Linux partition.  When I boot from the Ubuntu CD and run Gparted, it is not clear to me which is the Linux partition, or if there really is a Linux partition, and I don't want to delete the wrong thing.  Here are the three partitions I see (table a bit hard to read):

Partition         /dev/sda1  --       /dev/sda2 --                /dev/sda3
File System   fat16              --  ntfs                         --  fat32
Mount Point   --                         /media/Kenny_G      -- 
Label             DellUtility  --       Kenny_G                 --  DellRestore
Size              54.88 MiB  --       462.25 GiB  --              3.45 GiB
Used             7.88 MiB  --       390.85 GiB  --               2.97 GiB
Unused          47.00 MiB      --  71.41 GiB  --               299.50 MiB
Flags                                                      --         (/dev/sda2) boot  --  

I know that  /dev/sda1 and /dev/sda2 operate normally, and I don't know how to test  /dev/sda3.  Is it possible that something went wrong in the installation, preventing the creation of the Ubuntu partition and causing the computer to stall at the grub rescue> prompt when booting?

At this point I think that I would prefer to have the option to boot Ubuntu either from an external drive or a relatively large thumb drive, rather than my hard disk or the CD.

Can anyone tell me how to set this up?

Thanx!


> **gauravkumar said:**
> hi all,

I have a windows 7 system. I have installed Ubuntu 10.04 on a external hard disk. Though both of them work fine, like, first its asked which OS  would i like to work on and then i can continue.
But the issue here is when i try to work only on windows without attaching the USB HDD to the laptop, the GRUB RESCUE comes and stuck to that particular screen. it does not even ask for the boot options.
Please help.

Gaurav

---

### Post by oldfred on 2010-07-03
K-Sub, you do not have any linux partitions, did you install wubi which is just a file inside the NTFS partition of windows?

---

### Post by etiennechausse on 2010-07-03
HAHA I had the same broblem last winter XD
took me a day to figure it out
I you dont mind loosing part of your computer space, just partition your cpu c disk. Then put Ubuntu on a cd
Install ubuntu on partitionned drive (40gb would be plenty to have fun with ubuntu)
then you wont need you usb drive again and you'll be happy to use both linux and windows on your pc

---

### Post by K-Sub on 2010-07-03
OK, that is what I suspected about the partitions.

I booted from the Ubuntu 10.04 CD and just followed the installation menus and let it do its thing...or not, I guess.

> **oldfred said:**
> K-Sub, you do not have any linux partitions, did you install wubi which is just a file inside the NTFS partition of windows?

---

### Post by K-Sub on 2010-07-03
Thanks, but can you give me some more detail on how to do this, how I would set up the partition, install Ubuntu to that partition and then select which OS to boot from.

> **etiennechausse said:**
> HAHA I had the same broblem last winter XD
took me a day to figure it out
I you dont mind loosing part of your computer space, just partition your cpu c disk. Then put Ubuntu on a cd
Install ubuntu on partitionned drive (40gb would be plenty to have fun with ubuntu)
then you wont need you usb drive again and you'll be happy to use both linux and windows on your pc

---

### Post by scrapmetal on 2010-07-03
K-sub

Had a similar experience on a IBM Lenovo.
Would guess / suggest  that sda1, fat 16 is the emergency windows restore drive place there by HP, you probably have to F1 or something similar to write over sda2, NTFS if windows is dead - deleting your personal files etc, but restoring a working windows machine.
sda3, fat32 is for file storage (personal or backup), this sort of arrangement is often seen on smaller company machines that have network administration etc to call upon.

My response to this problem was.

1. Flattened entire hard drive.
2. Installed Windows XP pro  with service pack 2 (turn of updates, AVG anti virus, zone alarm fire wall), Presume Win7 same.
3. Installed Ubuntu 9.04.4
4. Installed Ubuntu 10.04
5. Installed Kubuntu 10.04

6. Having lots of fun on a 512mb Ram and a 40 Gb hard drive machine with a ATI RAGE 512 video card.

Info on hard drive sizes would be of assistance. You may be able to move data of sda3 (presume you have one physical drive "size?"),
and put Ubuntu on that drive.
Selecting it's entirity for install. Swap partition and ext3 or ext4, 8.04 and 10.04 respectively. Grub takes over from Windows boot loader / menu.
Grub (boot loader should incorporate Win7 selection and have Ubuntu as default it you do not select Win7). That is one turned on Ubuntu should automatically load.

P.S. Will be killing XP soon, maybe today.

---

### Post by oldfred on 2010-07-03
K-Sub, I do not see any room to install Ubuntu. You show 71GB free and 390GB used. Windows needs 20 to 30% free or all of your 71GB to keep working well. Are you planning on deleting some space. Was wubi installed and taking 30Gb of space?

---

### Post by K-Sub on 2010-07-03
I was restoring this computer and had quite a few duplicate files.  I now have over 100 GB of free space and hope to free up more.  At this point, I'm reluctant to try the dual boot approach again.  It just didn't seem to work well last time.

---

### Post by gauravkumar on 2010-07-04
Thanks all...
I am trying all the provided solutions now and soon come up with the reply....

---

### Post by gauravkumar on 2010-07-05
[FONT=Calibri][SIZE=3]Yarui TellTom Oldfred  Philinux[/SIZE][/FONT]
Guys,
I have a genuine Windows 7 cd with me that i got with the notebook, can i use that to get my Windows MBR back without using any third party tweeks.

---

### Post by oldfred on 2010-07-05
IF you just want the MBR set to boot windows you just need fixMBR. I am just posting the full set of repair instrucitons in case you need more:

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by gauravkumar on 2010-07-05
Thanks a ton OldFred,
 
I'll just try the procedure....

---

### Post by gauravkumar on 2010-07-05
Hi OldFred,
Though the issue is resolved with windows, but a new issue has come up...
Windows is not detecting the xternal HDD...
 
please help

---

### Post by Yarui on 2010-07-05
In order to boot into the Linux install on your external drive I would just suggest going into your boot menu at startup and selecting USB.  There should be something at the bottom of your screen during the POST that says what key to press to go into the boot menu.  The reason that Windows can't see your drive is probably because it's formatted with a filesystem that Windows can't read (ext3, ext4, xfs, etc), so it doesn't show up.  If you go into the disk utility in Windows it will probably have the disk listed, Windows just doesn't mount disks it can't read.

---

### Post by gauravkumar on 2010-07-05
What about formatting the xternal HDD....and reinstalling with proper boot menu and not installing windows mbr over the HDD...

---

### Post by oldfred on 2010-07-05
Does your windows boot if you select the internal drive?

Windows will not read ext3 or other linux based formats of a partition. Generally you create a NTFS shared partition to allow both windows and Ubuntu to read the same data. Ubuntu will read the windows partition but you should not write a lot of data into the NTFS system partition as windows can be fussy.

---

### Post by gauravkumar on 2010-07-05
> **oldfred said:**
> Does your windows boot if you select the internal drive?

Windows will not read ext3 or other linux based formats of a partition. Generally you create a NTFS shared partition to allow both windows and Ubuntu to read the same data. Ubuntu will read the windows partition but you should not write a lot of data into the NTFS system partition as windows can be fussy.
Windows is working fine after the solution u provided. Though it is not detecting the xternal HDD for the reason as you stated. Even when xternal hdd is connected to the notebook windows starts without any prompt for dual boot. Now whn im trying to boot the system from usb storage through bios, a screen with cursor blinking on top left corner of the screen appears till eternity.

---

### Post by oldfred on 2010-07-05
Then you need to install grub or grub2 to the external drive.Check what it mounts the external as some make it sdf or other letter not sdb.

Install grub2 from LiveCD:
Find linux partition change sdb5 if not correct or even sda, sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

---

