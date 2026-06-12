---
title: "Dual booting Win 7 x64 and Ubuntu 10.10"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by dominumds on 2010-11-29
Hello there!
I've just made up my mind and decided to install Ubuntu 10.10 alongside Windows 7 x64.
I'd do it myself, but I have a Dell laptop and it has 3 partitions instead of just one:
*OEM (according to ubuntu, FAT16 - it seems that it is Dell's recovery utilities, 39MB)
*RECOVERY (NTFS, seems that it is the Repair Console, 14GB)
*C disk itself (232GB, NTFS)

Is there any way to shrink the latter and safely install Ubuntu without fear of obliterating my disk? :p

Cheers!

---

### Post by rizman on 2010-11-29
Hi there,

I just did exactly that 4 days ago. I also had 3 partitions on my Packard Bell Notebook. 
2 where somehow related to the recovery and the third (450GB) was the one where Windows 7 was installed.

First I'd suggest you backup ALL your important data (Music, Pictures, Documents) to an external HDD.

Having done that, I booted Ubuntu using the Live-CD and repartitioned my HDD using GParted. I left the first 2 partitions untouched. The big one I just deleted (as I had backed up everything). Now I have created a 80GB partition for everything Windows, a 20GB for everything Ubuntu. The remaining space I have used to store my Data (I formatted that partition as NTFS to be able to access it from Windows and Ubuntu)

Now I had to take care that the Windows partition would be the third partition - right after those restore partitions - as the restore software would always pick the third partition it found.

From there it was: re-install Windows.
Install Ubuntu.

Now if you don't want to format your drive, you can use GParted to move-resize partitions. But I'm not sure how reliable that is.

Also, note that you can't have more than 4 primary partitions. Hence you'll need to use Logical/Extended partitions. Not sure about windows, but Ubuntu happily installs on an extended partition. No need to have a primary partition for it.

---

### Post by Quackers on 2010-11-29
If you boot into Windows 7 and go to Start > right-click on Computer > select Manage and then in the resulting window select Disk Management you will see your current disc layout displayed.
Right click on your C: partition and choose "Shrink". A pop-up window will appear giving you details on how much the partition can be shrunk by. Make your choice by adjusting the shrinkage as required and hit ok.
This is the quickest way to shrink a Vista or W7 partition (shrinking with Gparted is much slower and carries risks for a NTFS partition).

Then the resulting free space can be used by Ubuntu. Choose "specify manually" during install and create your new Linux partitions (/root, /home (if required) and swap.
I would not advise using the "install alongside" option in the installer (if you get it) as this is fraught with danger!!!

---

### Post by rizman on 2010-11-29
@Quackers:
Didn't know that Windows allowed to resize an NTFS partition. Has that been around for long? Must have always missed it when I was looking for it and in the end I just settled using GParted. Good to know though

---

### Post by dominumds on 2010-11-29
> **rizman said:**
> @Quackers:
Didn't know that Windows allowed to resize an NTFS partition. Has that been around for long? Must have always missed it when I was looking for it and in the end I just settled using GParted. Good to know though

It's diskmgmt.msc, and afaik, it's been around since at least Vista (I also have one box with it)

---

### Post by natronite on 2010-11-29
ext4Resizing NTFS partitions is the Beauty of Windows 7.

For my machine I left the partition on which I wanted to install Ubuntu empty.
In the Ubuntu installer I then created 4 partitions. 

1) primary
   500MB
   ext4journaling
   /boot

2) logical
   5000 MB
   swap area

3) 10'000MB
   ext4journaling
   /

4) rest of the available space
   ext4journaling
   /home

I then told the installer to put the boot information (Grub2 for Ubuntu 10.10) on my /boot partition

If you do it that way the computer will restart into windows where you'll have to add an entry to the boot menu using EasyBCD.

once this is done everything works like a charm!! I've never used Linux before, but I love Ubuntu!!

PS. I followed this post when I set up my dual boot machine: [http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)

---

### Post by Quackers on 2010-11-29
Yes, it's been here since Vista. It was not available in XP or earlier versions.
It's very simple and extremely quick! Gparted can take 2 hours or more to do the same thing, and it occasionally goes badly - although that may have been fixed now.

---

### Post by StuMcBill on 2010-11-29
I used WUBI to install Ubuntu onto my Windows Partition (17Gb).

Is this a "frowned upon" thing to do, or will it run happily alongside forever?

---

### Post by Quackers on 2010-11-29
It's not "frowned upon", it's only meant to be a means of trying Ubuntu though. As such updates can cause problems. If you try it and like it you may decide a more permanent installation is required. That involves partition management of some kind or another, or at least the creation of new partitions.

---

### Post by dominumds on 2010-11-29
I'm now inside the Live CD.
Partitioned the 100GB and awaiting for the installer to finish.
Then I'll have to use EasyBCD to create the bootloader entry on Windows.
:popcorn:

Just one more question: should Ubuntu drives me mad (let's hope not!), is it safe to boot into windows, reformat the Ubuntu partitions as NTFS and then recombine the volumes?

---

### Post by Quackers on 2010-11-29
EasyBCD may not be necessary. See how things go.
The answer to your question is yes, but you would need to restore the Windows bootloader, usually with the Windows repair disc.

---

### Post by StuMcBill on 2010-11-29
> **Quackers said:**
> It's not "frowned upon", it's only meant to be a means of trying Ubuntu though. As such updates can cause problems. If you try it and like it you may decide a more permanent installation is required. That involves partition management of some kind or another, or at least the creation of new partitions.

OK, so I could use the Disk Management software in Windows 7 to resize my Windows 7 (NTFS) and make a 20Gb(?) partition for Ubuntu (EXT?).

Can I do this without losing any of my data on my C:\ drive?

Also, do I need a swap partition?

Sorry again for the noobish questions.

---

### Post by Quackers on 2010-11-29
Yes, as long as Windows 7 has not been shrunk before.
I personally wouldn't create another partition at this stage, I would leave the free space for Ubuntu to install into. The necessary partitions (in ext4 normally) can be created during the installation.

---

### Post by StuMcBill on 2010-11-29
> **Quackers said:**
> Yes, as long as Windows 7 has not been shrunk before.
I personally wouldn't create another partition at this stage, I would leave the free space for Ubuntu to install into. The necessary partitions (in ext4 normally) can be created during the installation.

No I have not shrunk Windows 7 before, although there are 2 partitions on my 320Gb hard drive (but it was like this from the factory).

Would I be best to shrink my Windows 7 partition (C:\) or my "Data" partition (D:\) or does it make no difference?

If I went down this route, would I be able to access the files on my C & D drive from Ubuntu, I can access my D: drive at the moment!

Sorry for hijacking the thread! :D

Thanks

Stu

---

### Post by Quackers on 2010-11-29
It's up to you which to resize. The last one on the disc physically would possibly be best, if possible.

Shared data is another question entirely, although access can usually be gained for reading purposes.

It may also be better to get rid of the wubi install first, after backing up any important stuff. I don't know if it could cause any problems, but I suspect so.

---

### Post by StuMcBill on 2010-11-29
> **Quackers said:**
> It's up to you which to resize. The last one on the disc physically would possibly be best, if possible.

Shared data is another question entirely, although access can usually be gained for reading purposes.

It may also be better to get rid of the wubi install first, after backing up any important stuff. I don't know if it could cause any problems, but I suspect so.

OK thanks, I will be giving it a go tomorrow I think, if I think of anymore questions I will let you know.

Thanks again for all the help.

---

### Post by Quackers on 2010-11-29
You're welcome, but please start a new thread with any further questions :-)

---

### Post by StuMcBill on 2010-11-29
> **Quackers said:**
> You're welcome, but please start a new thread with any further questions :-)

Will do, thanks for your time!

---

### Post by krishnarajagopal on 2010-11-29
> **dominumds said:**
> Hello there!
I've just made up my mind and decided to install Ubuntu 10.10 alongside Windows 7 x64.
I'd do it myself, but I have a Dell laptop and it has 3 partitions instead of just one:
*OEM (according to ubuntu, FAT16 - it seems that it is Dell's recovery utilities, 39MB)
*RECOVERY (NTFS, seems that it is the Repair Console, 14GB)
*C disk itself (232GB, NTFS)
 
Is there any way to shrink the latter and safely install Ubuntu without fear of obliterating my disk? :p
 
Cheers!
Hi Dominumds,
If you just want to dual boot ubuntu within windows then your best bet would be to install WUBI
I used it for a while before I switched to virtualbox and I loved it
You cn get further details on WUBI from the below link. 
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
However if you want to access windows and ubuntu at the same time then u can go for oracle virtual box and load ubuntu as guest or use colinux/andlinux if you need a linux emulator inside windows 7.
 
Regards,
Krishna

---

