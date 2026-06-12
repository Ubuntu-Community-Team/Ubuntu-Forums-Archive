---
title: "Unable to Find Partitions"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by rkitecht on 2011-05-17
I switched over from windows 7 {my hard disk was partitioned into 3 with C: (Windows Partition) D: and E:)  to Ubuntu 11.04. During the OS installation I chose the option to ERASE windows 7 in the C: and install UBUNTU 11.04. 

Now how do I access the other partitions the D: and E: 

Thanks in advance

---

### Post by bioterror on 2011-05-17
> **rkitecht said:**
> I switched over from windows 7 {my hard disk was partitioned into 3 with C: (Windows Partition) D: and E:)  to Ubuntu 11.04. During the OS installation I chose the option to ERASE windows 7 in the C: and install UBUNTU 11.04. 

Now how do I access the other partitions the D: and E: 

Thanks in advance

You can use program **gparted** to view partitions.
I have a feeling you used your whole hard drive for ubuntu ;)

That's the spirit, all or nothing!!8)

Also command "sudo blkid" should show partitions and file types.

File browser **nautilus** should even tho show you your partitions if you have any. but I really have this weird feeling of using whole drive for Ubuntu.

---

### Post by Prince Valiant on 2011-05-17
If Bioterror's suggestions don't work, run this code, which outputs all partitions on all drives, and post the output in your next thread:

```
sudo fdisk -l
```note that's a lowercase L in that code, not a one.

Of course, I'm, assuming that 1) you've tried simply going to the location Computer, and 2) you may have deleted your other partitions as Bioterror said.

Have fun!

-Val

---

### Post by rkitecht on 2011-05-17
Hey Thanks for response

this is what i got when i used the fdisk on the terminal

```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00094335

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9601    77111296   83  Linux
/dev/sda2            9601        9730     1037313    5  Extended
/dev/sda5            9601        9730     1037312   82  Linux swap / Solaris

Disk /dev/dm-0: 1062 MB, 1062207488 bytes
255 heads, 63 sectors/track, 129 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf0be7369

Disk /dev/dm-0 doesn't contain a valid partition table

```

---

### Post by garvinrick4 on 2011-05-17
You have an 80 gig. drive with Linux installed on it. No Windows partitions present.

---

### Post by rkitecht on 2011-05-17
My hard disk is a 120 GB one. I had 3 partitions in it 80GB for windows which I am currently using for ubuntu 11.04 and the rest as d: with 20GB and e: with another 20GB

I don't find my d and e partitions in ubuntu

---

### Post by srs5694 on 2011-05-18
Unless you've cut something significant from your fdisk output, your disk is actually an 80 GB model -- or at least, that's all that Linux has detected. (It's conceivable that you've got another physical hard disk installed that Linux is not detecting because of a hardware or driver problem.) You wouldn't be the first person to be mistaken about the size of a hard disk; human memory is imperfect, and tools like disk compression utilities can make a disk look bigger than it really is.

Ubuntu's installation options keep changing, and with at least some versions, the options vary depending on what the installer finds on the disk. I'm attaching a screen shot of the partitioning options I got on one installation of Ubuntu 10.10. Note that there are two options: "Erase and use the entire disk" and "Specify partitions manually (advanced)." I believe the second option has been changed to something like "Other" in 11.04, but the point is that if you selected the first option, you didn't just erase the Windows C: partition; you had Ubuntu take over the *entire hard disk* -- C:, D:, and E:. At one time there was also an option called "Install side-by-side" or something like that, which would shrink existing partition(s) to make room for Ubuntu, but it only appeared under certain conditions and it might have been removed entirely with 10.10 or 11.04. (It had a bad reputation for causing problems.)

If my hypothesis is correct, your best hope of recovering the data from your D: and E: partitions is to restore from a backup. If you don't have a backup, you now know why you should have, since your only remaining option is to use low-level recovery tools. There's a chance you can recover those NTFS partitions by using [TestDisk,]("http://www.cgsecurity.org/wiki/TestDisk") but they'll almost certainly be damaged, so this might not work, and if it does, you're likely to find that some files are damaged. You may need to use [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") to recover individual files.

Whichever recovery approach you take, your first step should be to *shut down the computer and not use that disk again until you've recovered it!* Every time you boot Linux, you write more data to the disk, and that data might be overwriting the files you want to recover. The best way to proceed is:


[LIST=1]
[*]Buy a new disk to use as a backup and data recovery volume. This can be internal or external, but it must be at least as large as your current disk. Ideally, it should be at least twice as large as your original disk.
[*]Attach the new disk to the computer.
[*]Boot using the Ubuntu install disc in "live CD" mode or using a recovery disc like [PartedMagic.]("http://partedmagic.com/doku.php") The latter might be preferable because, IIRC, it doesn't activate swap space. (Use of swap space imperils your old files.)
[*]Open a terminal window and type "sudo swapoff -a" to deactivate swap space.
[*]Use fdisk to identify your two disks by their sizes and partitions. I'll assume that /dev/sda is your current disk, and /dev/sdb is your new backup drive.
[*]Type "sudo dd if=/dev/sda of=/dev/sdb" to do a low-level backup of your current drive to the new one. ***Be extra careful in specifying the if= and of= options!*** The if= (input file) option specifies your current disk and of= (output file) specifies the disk you want to hold the backup, so if my assumptions about /dev/sda and /dev/sdb are incorrect, you should adjust the options as necessary. If you reverse these options, you'll completely trash the data on the original disk, thus making further recovery efforts impossible. The dd operation will probably take at least an hour or two to complete.
[*]If your backup disk is large enough, use GParted to create an additional NTFS partition on it.
[*]Use TestDisk to try to recover your old partitions. I'm only passingly familiar with its interface and options, so I won't try to describe this process in detail. You may need to do a "deep" analysis to find them. You're looking for NTFS partitions, though. If you can recover them, do so. You should then be able to mount them and try to copy their contents to the NTFS partition on your backup disk. You may need to use Windows recovery tools first, though, which will require rebooting using a Windows recovery disc.
[*]If TestDisk can't find your partitions, try PhotoRec. Again, I'm not familiar with its user interface or options. I'm afraid you're likely to have a hard time sorting through the files it recovers. You should copy anything it finds to the NTFS partition you created on the backup disk.
[/LIST]


Depending on what you did, your original disk may now be unbootable, since recovering the old D: and E: partitions would have required deleting your current Linux partitions. If the new backup disk is internal, though, you should be able to simply unplug the old disk and boot from the new one. If it's external you might be able to use the BIOS options to tell the computer to boot from the external disk.

---

