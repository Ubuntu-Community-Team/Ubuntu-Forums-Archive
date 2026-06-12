---
title: "Re-establish Windows partition on Ubuntu machine"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by CampDrex on 2010-10-30
I bought a machine and was using it exclusively with Ubuntu 10.04. I had removed the Windows partition! I was so sure I'd never have to go back. Well, I have a need to reestablish the Windows partition now and my Windows recovery disks won't work. Do I need to re-format the drive so the disks will work? HELP!!:confused:

---

### Post by Quackers on 2010-10-30
How do you mean the recovery discs don't work? Is that because they want to use the whole disc? Or does the process not get that far?

---

### Post by CampDrex on 2010-10-30
The process never gets that far. I think the drive is not being recognized by Windows.

---

### Post by Quackers on 2010-10-30
Is your system booting from the disc? Do you get an option on the screen to load drivers?

---

### Post by CampDrex on 2010-10-30
Since I blasted the Windows partition and Lynx is the only thing loaded, will Windows even load?

---

### Post by CampDrex on 2010-10-30
Yes it does ask me to insert recovery disks, that fails. I created a Repair Disk from my Win 7 laptop and that prompted for drivers but I have none, right?

---

### Post by Quackers on 2010-10-30
If it is a recovery disc it should boot up to the Windows Recovery Environment which is usually a bluish screen. If it's not getting that far then the disc is either not bootable (which it should be) or damaged. How was the recovery disc made?

---

### Post by Quackers on 2010-10-30
I personally have never had to install drivers to run the recovery discs.

---

### Post by jtarin on 2010-10-30
If you formatted your Win7 partition initially then there is no operating system to recover.....it's a reinstall if you want Win back.

---

### Post by CampDrex on 2010-10-30
I do get as far as the blue screen in the Windows environment with the System Disk (provided by manufacturer) but the Recovery Disk fails.

---

### Post by Rex Bouwense on 2010-10-30
Windows needs an NTFS partition and now your entire drive is probably ext3 or 4 since you got rid of the Windows partition.  You might try to create a partition for Windows and install Windows on it, but for that you will need an installation disk not a rescue disk.  Unless I do not understand the situation, there is no Windows to rescue.  Your entire hard drive was reformatted for Linux.

---

### Post by CampDrex on 2010-10-30
The recovery disks are supposed to take the machine back to original load (Win 7) so I can take it from there and re-establish the partitions (Win and Ubuntu) I will not lose anything so I don't mind the work.

---

### Post by CampDrex on 2010-10-30
Rex I believe you hit the nail on the head. I guess the answer is then to find a copy of Windows (any copy) and then use the recovery disks?

---

### Post by Quackers on 2010-10-30
Rex makes a good point in that the recovery disc would need either free space or a NTFS partition, unless it wants to use the whole disc.
Do you have options to Restore C: drive or Restore the whole hard drive?

---

### Post by CampDrex on 2010-10-30
Yes and that is where I think I am headed. I will get a copy of Windows-whatever and re-install my NTFS partitions and then run the recovery disks to get Win 7 back. Then I can get Lynx back on as a dual boot. I appreciate the input and I will check back before I turn the lights out on this machine just in case you sages have something to add. Thank you, thank you!

---

### Post by Quackers on 2010-10-30
You can do it from the Ubuntu Live CD by using gparted. You can delete/create partitions from there.
I'm still not sure why the recovery discs aren't working though. By default they should want to use the whole drive, so it doesn't matter what is on there already, as it will just format the drive anyway. The problems usually arise when you choose the advanced options and try to use only a part of the hard drive.

---

### Post by CampDrex on 2010-10-30
Thanks, I have it in hand and will give it a try. I see you on the other side!!

---

### Post by Quackers on 2010-10-30
Good luck :-)

---

### Post by gtardini on 2010-10-30
In the worst case: save all of your data & downloads, format everything, install windows from scratch with your recovery disk, re-install ubuntu. 
However, creating a ntfs partition with ubuntu's partition manager should be enough for your windows recovery disk to boot.
In general, if you consider dual boot it is wise to detach data partitions from system partitions, so that you do not lose any data when re-installing any OS. 
I always install Windows before: I find it easier to configure the partitioning in Linux than in BIOS or windows.

---

### Post by beew on 2010-10-30
> **Quackers said:**
> You can do it from the Ubuntu Live CD by using gparted. You can delete/create partitions from there.
I'm still not sure why the recovery discs aren't working though. By default they should want to use the whole drive, so it doesn't matter what is on there already, as it will just format the drive anyway. The problems usually arise when you choose the advanced options and try to use only a part of the hard drive.


If I am not mistaken Windows recovery disks only install to the entire hard drive. It doesn't work on partitions and if you repartition your hard drive then you already void the OEM license.

---

### Post by Quackers on 2010-10-30
> **beew said:**
> If I am not mistaken Windows recovery disks only install to the entire hard drive. It doesn't work on partitions and if you repartition your hard drive then you already void the OEM license.

It depends on the recovery discs. They all want to use the whole drive, but some (like mine) have an advanced option which allows installation to a partition (but only if I select the "restore whole computer" option - not "restore C: drive"). I suspect it is manufacturer dependant.

---

### Post by jtarin on 2010-10-30
> **CampDrex said:**
> Rex I believe you hit the nail on the head. I guess the answer is then to find a copy of Windows (any copy) and then use the recovery disks?I believe I brought the hammer in an earlier post and you went right over it.:P

---

### Post by CampDrex on 2010-10-31
Jtarin, you did. You were right. I did as requested and used gparted to reestablish an NTFS partition and then rebooted and ran the recovery suite (4 disks). It did want the whole drive and I let it have it. I am now writing from that Windows 7 machine. It will soon have a Lynx 10.04 partition and I will configure it for dual-boot. WHEW!!
 
Thanks to all :P
 
CampDrex

---

### Post by mrebanza on 2010-10-31
> **jtarin said:**
> If you formatted your Win7 partition initially then there is no operating system to recover.....it's a reinstall if you want Win back.

Yea dude . . . U need install CDs not recovery . . . . I just formated a friends pc from Vista to Ubuntu to Windows 7 . . . All easy as cake so long as your just wiping the disk out . . . In Win7 goto advanced . . . then delete and format your ubuntu hard drive BLANK . . . and install Seven . . .

---

### Post by mrebanza on 2010-10-31
LOL @jtarin "need a girl whose name doesn't end in .JPG"

---

