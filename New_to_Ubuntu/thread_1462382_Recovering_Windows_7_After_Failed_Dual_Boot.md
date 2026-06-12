---
title: "Recovering Windows 7 After Failed Dual Boot"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by age99 on 2010-04-25
Hi,
I am having some serious problems trying to recover my Windows 7 after failing to install dual boot with Ubuntu.  Somehow, I managed to install Ubuntu twice while trying to upgrade to 10.04, and now I can't get to Windows at all.

I can get grub 2 to boot up, which lists the different options, including windows, but windows fails to boot.  I can boot into Ubuntu 10.  

I've tried the following commands from the Windows recovery disk:
```
bootrec.exe /mbr
bootrec.exe /fixboot
```

But the /fixboot resulted in a "Element not fount" 

Any help would be appreciated.

---

### Post by bumanie on 2010-04-25
Have a look [here]("http://support.microsoft.com/kb/927392") - it may help. If not go [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/") and download the win 7 repair cd, it should repair things - I have used the vista one from the same site and it has always repaired the bootloader.

---

### Post by age99 on 2010-04-25
None of these options has worked for me.  I still get the same error whit the 
```
bootrec /fixboot
```
command:  "Element not found"
So it goes nowhere.  

Is there anyway to wipe grub from the MBR?

---

### Post by garvinrick4 on 2010-04-25
sudo fdisk -l   (small L)


Does that show your Windows install (post here)

---

### Post by bcbc on 2010-04-25
See [this post]("http://ubuntuforums.org/showpost.php?p=9168966&postcount=13") - same deal - got fixed.

Slightly different issue but the command 'bootsect' seemed to work.

---

### Post by age99 on 2010-04-25
Now I don't even have the grub2 list coming up, it just freezes.  I managed to boot up from the install disk.

here are is the output:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ce17efc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1260    10078208    7  HPFS/NTFS
/dev/sda3            1260      182401  1455015936    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b3b02b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       90795   729309813+   7  HPFS/NTFS
/dev/sdb2           90796      182401   735825164+   5  Extended
/dev/sdb5           90796      178691   706024588+  83  Linux
/dev/sdb6          178692      182401    29800543+  82  Linux swap / Solaris

I am assuming that sdb1 is the Windows 7 install.

---

### Post by wilee-nilee on 2010-04-25
Your commands are not quite correct to reload the MBR.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
I would not necessarily start trying them as I don't really know everything you have done.

---

### Post by age99 on 2010-04-25
> **bcbc said:**
> See [this post]("http://ubuntuforums.org/showpost.php?p=9168966&postcount=13") - same deal - got fixed.

Slightly different issue but the command 'bootsect' seemed to work.

I would rather not get to the point of unplugging hard drives if possible.  I am willing to wipe any trace of Ubuntu off (temporarily)....

---

### Post by age99 on 2010-04-25
> **wilee-nilee said:**
> Your commands are not quite correct to reload the MBR.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
I would not necessarily start trying them as I don't really know everything you have done.

I've followed all of the commands listed in your link, but I end up with the same "Element not found" error when I run:
```
bootrec /fixboot
```

---

### Post by bcbc on 2010-04-25
> **age99 said:**
> I would rather not get to the point of unplugging hard drives if possible.  I am willing to wipe any trace of Ubuntu off (temporarily)....

I wasn't suggesting that. Wiping Ubuntu won't help either.

---

### Post by age99 on 2010-04-25
I ran the bootsect command, and it was successful, but the results are the same:  I still can't boot into windows, and no operating systems are listed/visible when I try to repair the drive with the recovery disk.

Is there a way to format the drive, and re-install windows?

---

### Post by akand074 on 2010-04-25
> **age99 said:**
> I ran the bootsect command, and it was successful, but the results are the same:  I still can't boot into windows, and no operating systems are listed/visible when I try to repair the drive with the recovery disk.

Is there a way to format the drive, and re-install windows?

Yeah if you have a copy of a windows cd you can easily do it through the custom installation option. If not, you can use your recovery disks if you made them (assuming you bought the computer from retail). About making your windows bootable again, its possible, but everything in Windows is very intertwined, chances are even if you manage to get it to boot it will still have some sort of problem. I recommend just getting all the data you need if you haven't already and just reinstalling windows from one of the options you want. You can also use the Ubuntu Live cd and load Gparted and just format the entire hard drive (or partition you want) and then use a windows cd to install on that partition. I'd recommend doing everything through a windows cd/recovery disk if you have it.

EDIT: Just an extra thought on the matter, did this problem happen just after installing Ubuntu? Because an installation of Ubuntu should not have any effect on your other partitions. Though I have read around once or twice that having ubuntu shrink your windows drive sometimes has problems and they recommended you use the windows partitioner to shrink it first. Still, odd, sorry this happened to you, I hate reinstalling windows its a pain.

---

### Post by wilee-nilee on 2010-04-25
> **age99 said:**
> I ran the bootsect command, and it was successful, but the results are the same:  I still can't boot into windows, and no operating systems are listed/visible when I try to repair the drive with the recovery disk.

Is there a way to format the drive, and re-install windows?

Yes, a live Ubuntu or many Linux distros have gparted on them. So boot the live Lucid you have go to system-admin-gparted and look at your HD, from there you can delete a partition, then make a new NTFS for W7. W7 will install into a opartition made by gparted. While your on the live cd you may want to run sudo fdisk -l  l= a small case L. and post it as we don't really know how many HD you have or some pertinent info that might make this easier and getterdone.

On two occasions when I left my Lucid install on the HD and let W7 do a custom install and format the space I ended up with the ext4 as unallocated the extended partition and swap where right where I had left them, but the primary inside the extended was unallocated.

---

### Post by age99 on 2010-04-25
The output from fdisk -l:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ce17efc

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 1260 10078208 7 HPFS/NTFS
/dev/sda3 1260 182401 1455015936 7 HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b3b02b4

Device Boot Start End Blocks Id System
/dev/sdb1 1 90795 729309813+ 7 HPFS/NTFS
/dev/sdb2 90796 182401 735825164+ 5 Extended
/dev/sdb5 90796 178691 706024588+ 83 Linux
/dev/sdb6 178692 182401 29800543+ 82 Linux swap / Solaris


I had a successful dual boot with Windows 7 and Ubuntu 9.10 but the problems started when I upgraded to 10.04.  I couldn't boot into Windows 7 from grub, and I loaded up the 10.04 iso install disk and mistakenly installed it again.  

Now I don't even have the grub menu popping up.

I've tried to run things through the W7 recovery disk, but the automatic boot repair doesn't fix the problem, and even and re-install doesn't work.  

Now I'm looking into the gparted option....

---

### Post by wilee-nilee on 2010-04-25
If W7 was installed on the computer when you purchased, it looks like you have a recovery partition in sda2, but since you can't boot into W7 I don't know how you could get it to run and just reset W7 back to stock and reload the MBR.

If you have a install DVD then I would go for it, I see the usual multi-partition schema that is part of retail sales of MS, and the dell extras that may or not really be needed. Personally I like my MS in one partition, so I can use the allowed amount of partition on a hard drive to have other OS.

I could be incorrect with any of my observations, so always get more opinions.

You might go over to the w7 forums I suspect that there is a way to get it to recover from a command if you have the install disc or a recovery disc.
[http://www.sevenforums.com/](http://www.sevenforums.com/)
I may not be correct though, ms is not as friendly with being manipulated as open source generally is.

---

### Post by age99 on 2010-04-25
I removed all the partitions on the second hard disk, including the original Ubuntu Lucid installation.  
After doing this, I was able to boot directly into Windows, and I installed a couple of updates, configured the monitors etc and it worked for a couple of reboots.  

I was hoping I was in the clear, and about ready to install Lucid again, but the next time I reboot, I got a bunch of characters and it froze.  

I'll now look at some of the partitions on the first hard disk...

---

### Post by wilee-nilee on 2010-04-25
The good thing here is that you are on the forums when some of the people I see who are very good at this sort of thing show up. Post this boot script in code tags it will give the pertinent info. I suspect though that W7 is corrupted, in some way, this is a personal opinion, not necessarily valid.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Actually since you were able to boot into windows after removing Ubuntu means that the MS MBR did reload, so you might try a recovery with the install DVD or the recovery discs that are available Like you originally tried. I suspect there are better ways of doing this so proceed with caution.

I just found this information on getting the recovery partition to run on different types of computers, from startup.
[http://www.w7forums.com/windows-7-recovery-partition-t4534.html](http://www.w7forums.com/windows-7-recovery-partition-t4534.html)
I am assuming here that W7 was installed when purchased, and that there is a recovery which looks like sda2.

If it was me I would look for or call dell and ask how do I get the recovery to work from booting on your specific computer, the instructions in the link are for a dell recovery, but some models may need a different key sequence, you never know.

---

### Post by age99 on 2010-04-25
I ran the script, and this is the output:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ce17efc

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,238,335    20,156,416   7 HPFS/NTFS
/dev/sda3          20,238,336 2,930,270,207 2,910,031,872   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b3b02b4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,930,272,064 2,930,270,017   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8AB8-A98A                              vfat                                     
/dev/sda2        4442BB4E42BB4408                       ntfs       RECOVERY                      
/dev/sda3        625EBF7A5EBF4617                       ntfs       OS                            
/dev/sdb1        16DA94F8DA94D4F9                       ntfs       DATAPART1                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/8AB8-A98A         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

Could there still be a conflict with this?

---

### Post by MasterNetra on 2010-04-25
Have you tryed running "update-grub2" using sudo from Ubuntu?

---

### Post by wilee-nilee on 2010-04-25
> **MasterNetra said:**
> Have you tryed running "update-grub2" using sudo from Ubuntu?

It is easy to miss information @op "I removed all the partitions on the second hard disk, including the original Ubuntu Lucid installation". I do it all the time.;)

---

### Post by age99 on 2010-04-25
Now I can only access Ubuntu through the install CD, so I can't update Grub.  

I'll try re-installing Windows again, but I don't know why it doesn't install fully, with some errors in the mbr.  I tried the windows recover disk, and I still can't get
```
bootrec /fixboot
```

to run successfully.
Is this not indicating that the mbr is still corrupted?

---

### Post by wilee-nilee on 2010-04-25
You have a full install DVD right? Do whatever works for you but just be careful you know what your doing. On my acer netbook I just wiped the one HD and installed W7 fresh in one pre-formatted partition, I think the install DVD does this as well.

You probably have a fixable situation as of now, we just need those that know to help. If I bought a new computer with W7 on it spread over two HD and multiple partitions, the first thing I would do is wipe it and reinstall on one partition if possible with a oem. This is personal preference as it keeps things a little simpler, for a simple mind=mine.

---

### Post by oldfred on 2010-04-25
Your windows partition does not have a boot flag (*) or in windows terms an active partition. You are also missing /Windows/System32/winload.exe. When windows7 is installed it puts boot files into one partition of about 100mb and the winload.exe is in the main partition.

If you put the boot flag on the sda2, the repairs may work as then it can find the partition that should be the active partition.

You can use gparted, right click on partition and manage flags, disk utility or command line 
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

Boot flag can only be on one primary partition. Windows requires it , linux does not use it, but some BIOS require it or you cannot boot even to linux.

---

### Post by wilee-nilee on 2010-04-25
> **oldfred said:**
> Your windows partition does not have a boot flag (*) or in windows terms an active partition. You are also missing /Windows/System32/winload.exe. When windows7 is installed it puts boot files into one partition of about 100mb and the winload.exe is in the main partition.

If you put the boot flag on the sda2, the repairs may work as then it can find the partition that should be the active partition.

You can use gparted, right click on partition and manage flags, disk utility or command line 
set boot flag on for sda2 (off on others)

sudo sfdisk -A2 /dev/sda

Boot flag can only be on one primary partition. Windows requires it , linux does not use it, but some BIOS require it or you cannot boot even to linux.

Yay a old-wise pro, thanks for stopping by. I wondered about the boot myself.

---

### Post by age99 on 2010-04-25
> **oldfred said:**
> 

If you put the boot flag on the sda2, the repairs may work as then it can find the partition that should be the active partition.

You can use gparted, right click on partition and manage flags, disk utility or command line 
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

Boot flag can only be on one primary partition. Windows requires it , linux does not use it, but some BIOS require it or you cannot boot even to linux.

I used gparted to set the boot flag for sda2, ensuring it was the only one with this.  The same error appeared, even after I've re-installed windows again.  It doesn't boot at all, and a bunch of crazy characters come up....

I have 2 restore disks, as well as the W7 repair disk, but I seem to be getting nowhere with this.

---

### Post by age99 on 2010-04-25
The restore disks that I have are not Windows 7 installation disks, but the restore disks.  
The Dell machine I bought did not come with an installation disk, but the disks were made the first time I booted up the machine, and were supposed to restore my machine in the case of a mess-up like this.  

Would this make any difference?

---

### Post by wilee-nilee on 2010-04-25
Shouldn't be a problem if they are correctly formatted. I suspect that you can get a actual single oem install DVD from MS or Dell as well. From what I have read about oem is that the key is detected and auto activated.

I would get that Install DVD if it was me, I have 2 W7 pro DVD's I was sent an extra, with a student upgrade from XP.

You were smart to make those backups.

---

### Post by oldfred on 2010-04-25
Restore disks are to return it to factory as shipped. It erases everything, so if you have any important data make sure you back it up first. 

You probably cannot use one brand of restore to restore another as it will include the drivers for only that brand of install. If you get it to install then you may be able to get windows to update.

---

### Post by garvinrick4 on 2010-04-26
Dell's what a pain in the rear they are at times. Hidden recovery partitions that take up a primary. Now 7 takes up 2 primarys and Extended for Linux extended takes up primary what does that leave for a boot partition. Nada
 At least this fellow has 2 drives should be able to get a partition labeled SYSTEM (NTFS)
to hold the boot flag that 7 will make but dells hidden is taking sda1. I believe "oldfred"
hit the nail on the head. 
 Do not install Dells hidden recovery and just use Windows 7 recovery should get the job
done. Why does Dell screw around with Windows software anyway.
 You got your 3 Windows 7 disks and a recovery disk that is all you will ever need. A Ubuntu Live CD and the show is on.

---

### Post by age99 on 2010-05-04
I managed to solve the issue.  What I had to do was:
[LIST]
[*]Clear the ubuntu partitions off completely
[*]use the recovery disks (I made when I first booted up the machine) when booting but select the option to use the hard drive's partition where a system backup was stored(Dell backup)
[/LIST]
For whatever reason, the backup for the DVDs never worked but the one from the hard drive did.  It is a real pain because Dell's Data Recovery software causes some problems with the dual boot and I had to remove it.  This makes the recovery a later version.

I then re-installed Ubuntu 9.1 and now I will try again with version 10. 

Thanks for all the help

---

