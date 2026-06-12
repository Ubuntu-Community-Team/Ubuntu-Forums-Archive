---
title: "Cant install any distro's"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-05-03
I am using Ubuntn10.10, upgraded to 1104 didn't like it so reinstalled 1010.

I have a laptop and a desktop, so I installed Mint Julia on my laptop to try, liked it , so tried to install on my desktop, but it will not install, hangs after a couple of mins. the funny thing is it will not install ANY other distro, it starts to install, the distro logo appears then they all hang, the pc is OK that doesn't freeze. and I can install anything else, but not any other distro, and I have tried lots, and the same thing happens with everyone. even the original 1010 dvd hangs after installing as far as the purple screen.

I have checked the PC from top to bottom, side to side but can not find any reasons for this abnormality, it works perfectly, so long as I don't try to change the OS system .:confused:

I will appreciate any help given.

---

### Post by jprobe on 2011-05-03
Are you wanting to keep anything on the hard drive, or are you wanting to start from scratch?  I was just thinking that you could use dban if you didn't have anything on the drive that you need.  I did this with an older machine that was acting up during a couple attempts at a Red Hat install.

---

### Post by Rubi1200 on 2011-05-03
Post the full specifications for the computer in question please.

Also, what is currently installed and is/was it ever part of a RAID array?

If you could run this command from it that would be helpful too:

```
sudo fdisk -l

```
(lowercase L not 1)

Post the results here too.

Thanks.

---

### Post by Robert1305 on 2011-05-03
Results from fdisk l 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f0e2d71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60475   485764413+   7  HPFS/NTFS
/dev/sda2           60476       60801     2618595    5  Extended
/dev/sda5           60476       60779     2441848+  83  Linux
/dev/sda6           60780       60801      176683+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb9ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38522   309425152   83  Linux
/dev/sdb2           38522       38914     3143681    5  Extended
/dev/sdb5           38522       38914     3143680   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f004

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803404+   5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris

Ubuntu 1010 is the only thing currently installed, dont know what a Raid array is.

trid using command....cat /proc/pci in terminal for PC specs, but got message ...no such file.

---

### Post by EGamerHDK on 2011-05-03
Try totally wiping the drive if you don't need anything on it. I honestly just had this problem today. My solution was to take out the hard drive from my laptop and insert it into my other laptop. Then I just installed Ubuntu onto it and switched it back. 

In a nutshell,

2 Laptops.
1 Works. 1 Hangs up on installation.
Simply switched the hard drives between the two laptops.
Installed Ubuntu on "Hangs up on installation" hard drive while in the "Works" computer
Tried running Ubuntu on "Works" hard drive while in the "Hangs up on installation" computer

After that, I switched them back. And it worked.

Sorry if that ended up being more confusing then it should be. Hahahah. Good luck!

---

### Post by Robert1305 on 2011-05-03
No help, one desktop, one laptop. aaaaaaaaaaaaaaaaaaaaaaagh!!!!!!!!!!!!!!

---

### Post by linuxyogi on 2011-05-03
> **Robert1305 said:**
> No help, one desktop, one laptop. aaaaaaaaaaaaaaaaaaaaaaagh!!!!!!!!!!!!!!


Okay ..........dowload this 

 [http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%206.0/pmagic-6.0.iso/download](http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%206.0/pmagic-6.0.iso/download)

burn it to a cd & see if you can boot from it. I am not sure if it will work but its worth a try.

If you can boot successfully write back we will see what needs to be done next. 

Dont try to boot it from a usb drive. I tried it, didn't work.

---

