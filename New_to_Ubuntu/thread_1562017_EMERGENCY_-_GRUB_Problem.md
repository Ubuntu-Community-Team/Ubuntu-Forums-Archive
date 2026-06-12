---
title: "EMERGENCY - GRUB Problem"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by thomasdsc on 2010-08-27
I gotta fix this problem VERY fast.
So, I am a newbie to linux.
I hav installed 10.04, and I didn't like it, so I instead, booted from ubuntu 9 koala and installed koala and overwritting the 10.04 ubuntu. 
When I booted, I encountered a GRUB error (error the symbol 'grub_getcharwidth ' not found , so, I decided to go to the Live CD and restore GRUB.
When I "restored GRUB", I rebooted the system and I got this.
GRUB loading
error: no such disk
grub rescue>
I tried to boot from the live cd, no matter what device I chose to boot, the no such disk thing kept showing up. Not even the Windows 7 internal HD is booting!.
Please help as soon as possible, I got to have this fixed quick.
My system configration is this
Dell Vostro 1320, Windows 7 on the hard disk, and ubuntu installed in an external hard disk.

(its intel CPU, not AMD)
I hereby thank whoever that can help me.
PLEASE...

---

### Post by thomasdsc on 2010-08-27
UPDATE!
The CD Boot thing suddenly worked after it was left idle for half n hour.
Now is it possible to get rid of the GRUB and make my computer boot to Windows automatically as if nothing had happened? I wanna wipe clean my external hard drive and start everything all over again.
So is it safe for me to wipe the External HD Clean in Live CD mode? Or will I destroy the rest of GRUB and cause even more problems?

---

### Post by garvinrick4 on 2010-08-27
> **thomasdsc said:**
> UPDATE!
The CD Boot thing suddenly worked after it was left idle for half n hour.
Now is it possible to get rid of the GRUB and make my computer boot to Windows automatically as if nothing had happened? I wanna wipe clean my external hard drive and start everything all over again.
So is it safe for me to wipe the External HD Clean in Live CD mode? Or will I destroy the rest of GRUB and cause even more problems? If you have a Ubuntu live CD it should boot it does not use the internal grub it boots off of CD. Should be able to look in gparted and see the windows and linux partitions. Leave Windows alone and format the Linux partition in ext4 and then install into the same partition # such as sda5 or whatever it is. If you dual boot in internal drive put grub in sda if external sdb . In page 8 of install will be advanced tab, click on it and put it in proper drive. Always use sda or sdb or sdc and so on. According to what drive you are using. If you are going to use external choose to install in that drive and then put grub in sdb not sdb1 or sdb2 but sdb.
 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
[GRUB 2 bootloader - Full tutorial - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1345518")

---

### Post by Gone fishing on 2010-08-27
I'd unplug the external drive (I assume this has Ubuntu on it?). Now to remove grub you can use your Windows install disk if you are running XP startup on the disk and then go to a recovery console and run fixmbr in Vista or Windows 7 at the recovery options go to the command prompt then run bootrec.exe /fixmbr

[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

This will over write grub note you will get a warning about overwriting a non standard mbr. You can then boot into Windows plug in the external drive and remove the Linux partitions from within Windows using the disk management tools.

You can then start over again!

---

### Post by thomasdsc on 2010-08-27
This is great, according to everyone's instruction, I seemed to be able to get the fix mbr thing done GRUB error that occurs when I boot seemed to be gone. Now its time to wipe my external HD clean, but I see several partitions on the ubuntu external HD I see. So is it safe to just format the entire HD and reinstall ubuntu on it again later?
I think everyone's help here, its been exactly what I've been looking for :)

---

### Post by Gone fishing on 2010-08-27
If there is nothing you want on the external drive feel free to remove all the partitions in the Windows disk management the Linux partitions (ext4, swap etc) will all appear as unknown types. 

You could also remove from a gparted disk etc my favorite of these disks is parted magic [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by thomasdsc on 2010-08-27
Oi, I see a 6 GB Partition of logical paritioning and the rest of 298 gb of linux installtion.
I just reinstalled linux, booted the drive up and I get another GRUB error.
error: the sumbol 'grub_getcharwidth' not found
Now how can I fix that?
Grub really hates me eh?

---

### Post by jtarin on 2010-08-27
I would recommend booting with the Live cd and when you get to the Gnome desktop open a terminal and use [fdisk]("http://www.ehow.com/how_1000631_hard-drive-linux.html") to peform your work. I would then format the drive as fat32. Follow the instructions and you can't go wrong.

---

### Post by thomasdsc on 2010-08-27
So...
How do I do that?

---

### Post by jtarin on 2010-08-27
> **thomasdsc said:**
> So...
How do I do that?How do you do what....exactly?

---

### Post by thomasdsc on 2010-08-27
I formatted the linux sdb1 drive
and there are 2 more called sb2 and sb5
They idenified themselves as 
Extended (under the column system, in sudo fdisk -l)
and 
Linux swap /Solaris
Do I format them too?

---

### Post by jtarin on 2010-08-27
If you want to keep them as they are (partitions) but just want to format them as Fat32....the answer is yes.

---

### Post by thomasdsc on 2010-08-27
Looks like they are unformmatable, they are around 10 GB in size...
So now I do a clean install of ubuntu 9 on the drive right?

---

### Post by jtarin on 2010-08-27
You can delete them in fdisk and then remake them but it would probably be easier for you to do that when you do a clean install. Think carefully about how you want to partition that drive before you start....If you want to dedicate the entire drive to Ubuntu you can wipe everything during the install. Does your Windows still boot OK or are you using Grub to boot Windows?

---

### Post by thomasdsc on 2010-08-27
tryin that now

---

### Post by thomasdsc on 2010-08-27
Oh god... just as I expected.
When I boot into the external hard disk, it says.
Error: the symbol 'grub_getcharwidth' not found
This is looking grim :(
And if I didnt touch anything at start up, the computer will normally booot into windows 7 in its internal hard disk, instead, it said.
Grub Loading
....
then nothing happens.

---

### Post by Gone fishing on 2010-08-27
What’s on the external hard drive? Maybe I don't quite follow what you have done. If you have Windows on the Internal drive with grub on the MBR with Ubuntu on the external HD then the suggestions below should work.

First I'd suggest unplugging the external drive and getting the system to boot from the internal drive as you wish then fixing the external drive.

If you just want Windows 7 to boot from the internal drive, then restart and set Bios to boot first from the CD then the first internal hard drive.

Then start up on the Windows boot disk and follow the instruction I gave earlier. You should now be able to start the PC and boot automatically into Windows without any grub screen.

Once you have this working you can sort out the External drive. If this has just been used for Ubuntu and you don’t want the data on the drive. You can start in Windows plug in the drive and then use the disk management tools to remove all the partitions from the drive which will all be marked as unknown. If you wish you can then use The disk management tools to add a new Windows ntfs partition.

---

### Post by thomasdsc on 2010-08-27
I am able to boot into windows now, with the fixmbr from the repair disc I downloaded.
Now when I boot into the external hard drive, that error comes up.
I followed both instruction, wiping the external hard drive from the manager in windows AND using gparted from the live CD.
I have done the format and reinstall ubuntu many times and it seems to be presisting.
In the grub screen, I typed boot and grub responded me with this message:
Grub: No Kernel Loaded.
Yet, i downloaded the Super Grub Disk and it detected the external hard drive's ubuntu 9 and sucessfully booted into it.
So right now, its almost certain that something is up with Grub.

---

### Post by zaphod777 on 2010-08-27
If it boot from Win7 fine just use Win7 from computer mnagment -> disk management and then format it NTFS. When you decide to use Ubuntu again then you can reformat it.

---

### Post by thomasdsc on 2010-08-27
I've already reformatted the external drve to FAT32
And reinstalled ubuntu 9 on external drive
When I boot into the external drve, I get the 
**[COLOR=#ff0000]Error[/COLOR]**: the symbol 'grub_getcharwidth' not found
From Grub.
In other words, I cannot boot into the external hard drive with ubuntu.

---

### Post by jtarin on 2010-08-27
> **thomasdsc said:**
> I've already reformatted the external drve to FAT32
And reinstalled ubuntu 9 on external drive
When I boot into the external drve, I get the 
**[COLOR=#ff0000]Error[/COLOR]**: the symbol 'grub_getcharwidth' not found
From Grub.
In other words, I cannot boot into the external hard drive with ubuntu.
Where did you install Grub?

---

### Post by thomasdsc on 2010-08-27
I wished I knew :(
How do I check?

---

### Post by capn.hector on 2010-08-27
does your bios support booting to an external drive directly?  if so you need to install grub on the external drive and select the external drive as the boot device (in my bios F12 to select boot device)  that will solve all your problems.  id also go and put the windows boot loader on the internal drive with windows 7

---

### Post by jtarin on 2010-08-27
During install you are asked about installing Grub there will be an "advanced" tab on one of the dialogues click that and it will allow you to install Grub to non-standard partition...that is somewhere besides MBR.

---

### Post by thomasdsc on 2010-08-27
> **capn.hector said:**
> does your bios support booting to an external drive directly?  if so you need to install grub on the external drive and select the external drive as the boot device (in my bios F12 to select boot device)  that will solve all your problems.  id also go and put the windows boot loader on the internal drive with windows 7
Yes, it does. I can choose to boot into internal hd or external hd, cd or removable storage devices. thing is I got that error everytime I boot into my hd.
Windows boot loader seems fine actually.

---

### Post by Gone fishing on 2010-08-27
So the only problem now is grub on the mbr of the external disk? 

You can boot from the internal drive fine?

I suppose you could remove grub from the the mbr of the external drive by using fixmbr from the Windows install disk from a linux boot disk such as parted magic or the ubuntu live disk with 

dd if=/dev/null of=/dev/sdX bs=446 count=1

where /dev/sdX is the hard drive you wish to remove grub from the mbr (change X as needed). However you could just ignore the problem if you install another Ubuntu it overwrite as needed.

---

### Post by thomasdsc on 2010-08-28
> **Gone fishing said:**
> So the only problem now is grub on the mbr of the external disk? 

You can boot from the internal drive fine?

I suppose you could remove grub from the the mbr of the external drive by using fixmbr from the Windows install disk from a linux boot disk such as parted magic or the ubuntu live disk with 

dd if=/dev/null of=/dev/sdX bs=446 count=1

where /dev/sdX is the hard drive you wish to remove grub from the mbr (change X as needed). However you could just ignore the problem if you install another Ubuntu it overwrite as needed.

This worked for me! horray!
I combined your advice with the wiki ubuntu documentation, reinstalled grub and now when I boot into the  external hard disk, I don't have that error anymore. Thanks all! :)

---

