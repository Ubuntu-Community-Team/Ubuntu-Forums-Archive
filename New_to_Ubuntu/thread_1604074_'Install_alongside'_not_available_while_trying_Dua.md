---
title: "'Install alongside' not available while trying Dual Boot with Win7 64bit"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by sfotakis on 2010-10-23
hi all,
trying for a few hours to setup dual boot machine with WIN7 Ultimate 64bit and Ubuntu 10.10 64bit.

I'm using a brand new hard disk WD SATAII 2TB.

What i eventually need is to have Win7 on one partition and Ubuntu on a second one. I just need to have some 200-300 MB for the Win7 partition and the rest of the 2TB for Ubuntu. I will also use an external disk for music and video which will be accessible from both win and ubuntu.

I have read here and in other sites that it is highly recommended to first install win and then ubuntu if you need a dual boot machine. So far, i have managed to install Win on the 2TB hard disk by creating a single partition. System boots ok and Windows Explorer says 1,80TB free of 1,81TB.

Now, trying to also install Ubuntu. When i boot with LiveCD i select Try and run GParted.

My issue here is that Gparted seems that can not recognize the existing Win installation and the partition. It shows me an "unallocated' space of 1.8 TiB but no signs of the win installation. Upper right combo box has /dev/sda (1.82TiB) selected, which is actually the only option. 

So when trying to Install there is not the 'Install alongside other operating system'. Only 'Erase and use entire disk' and 'Specify partitions manually'. 

When in 'specify partitions manually' again shows me /dev/sda/ with free space 2000398MB.

Also says Boot loader : /dev/sda ATA WDC WD20EVDS-63T (2.0 TB).

Any idea what's wrong here or what am i thinking (doing) wrong? 

thank you in advance and pls forgive my noobness :P

---

### Post by mister_playboy on 2010-10-23
You have to partition the drive before installing Windows.

The 1.82TiB partition that Windows Explorer lists means it has the whole drive to itself.  Windows Explorer would not mention the space on another partition.

Trying to install Windows 7 on a 200-300MiB partition is impossible.  The MS-stated minimum partition size for 64bit Win 7 is 20GiB.

---

### Post by sfotakis on 2010-10-24
> **mister_playboy said:**
> 
Trying to install Windows 7 on a 200-300MiB partition is impossible.  The MS-stated minimum partition size for 64bit Win 7 is 20GiB.

of course i mean 200-300 GB...

thank you, i will try to partition before installing.

---

### Post by amjjawad on 2010-10-24
[Partitioning]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning")

---

### Post by sfotakis on 2010-10-24
ok i have read all this but i'm still confused.

have found an example of what i'm trying to do:
See the 4th schema on this page:[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
That would be a 100-200GB partition (ntfs) for win, a big 1-1,5TB shared data partition which i believe can be in NTFS instead of FAT32(as the article says), a /home partition (ext3), ubuntu partition 100-200 GB(ext3) and swap

my problem is that i'm installing windows on a partition of the 2TB hard disk and then ubuntu installer seems that it is not recognizing it. GParted is showing me the rest of the 2TB hard disk as unallocated but no sign of the the ntfs partition of win. So when i select to install ubuntu on the unallocated space i'm getting an ubuntu installation but no win. I understand that win partition and installation might be somewhere there and this is an issue of bootloader (?) but i'm kind of noob here so any help will be valuable.

> You have to partition the drive before installing Windows.

@mister_playboy
Which tool should i use to partition the Windows partition? Do i have to also plan for the ubuntu partitions? Pls, note that eventually i need to have the scheme as described above

>  amjjawad: Partitioning
ok have read this but still confused what should i do first... Which tools to use to format the partitions and when? Do i have to use GParted to do all the planning from scratch and then install windows on the 1st partition and Ubuntu on the other one ? In what sequence ?

Thank you for your help.

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> ok i have read all this but i'm still confused.

have found an example of what i'm trying to do:
See the 4th schema on this page:[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
That would be a 100-200GB partition (ntfs) for win, a big 1-1,5TB shared data partition which i believe can be in NTFS instead of FAT32(as the article says), a /home partition (ext3), ubuntu partition 100-200 GB(ext3) and swap

my problem is that i'm installing windows on a partition of the 2TB hard disk and then ubuntu installer seems that it is not recognizing it. GParted is showing me the rest of the 2TB hard disk as unallocated but no sign of the the ntfs partition of win. So when i select to install ubuntu on the unallocated space i'm getting an ubuntu installation but no win. I understand that win partition and installation might be somewhere there and this is an issue of bootloader (?) but i'm kind of noob here so any help will be valuable.


@mister_playboy
Which tool should i use to partition the Windows partition? Do i have to also plan for the ubuntu partitions? Pls, note that eventually i need to have the scheme as described above


ok have read this but still confused what should i do first... Which tools to use to format the partitions and when? Do i have to use GParted to do all the planning from scratch and then install windows on the 1st partition and Ubuntu on the other one ? In what sequence ?

Thank you for your help.

Before I answer your questions or post more links for you to read, I need to know what are you planning to do?
Format (wipe) and start from scratch? or install Ubuntu and keep Windows 7 as it's?

Thank you :)

---

### Post by ieee488 on 2010-10-24
> **amjjawad said:**
> Before I answer your questions or post more links for you to read, I need to know what are you planning to do?
Format (wipe) and start from scratch? or install Ubuntu and keep Windows 7 as it's?

Thank you :)

He bought a brand new hard drive then installed Windows 7 on it. Taking up the entire hard drive. 

What he wants is to leave Windows 7 on it as the 1st partition but decrease its size which he did.

Now he is using GParted to try to create a 2nd partition as a common area that is accessible by both Windows and Ubuntu and a 3rd parition for Ubuntu.

---

### Post by Mark Phelps on 2010-10-24
> **sfotakis said:**
> Which tools to use to format the partitions and when?

Use the Win7 Disk Management utility to shrink the Win7 OS partition to make room for Ubuntu.  Do NOT do this using GParted or the Ubuntu installer as that risks corruption of the Win7 boot loader.

BEFORE you do anything else, go into Win7, use the Backup feature to create and burn a Win7 Repair CD.  This will prove invaluable later should you need to repair the Win7 boot loader as a side-effect of partitioning.

---

### Post by sfotakis on 2010-10-24
What im trying to do is here:

> **sfotakis said:**
> ok i have read all this but i'm still confused.

have found an example of what i'm trying to do:
See the 4th schema on this page:[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)


Format (wipe) the existing win 7 partition in order to achieve the desired schema is not problem for me. So, let's start with this.

i don't have anything in the win partition that's important. it's in clear, OS only situtation. So no problem formating

thnx for your replies.

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> What im trying to do is here:



Format (wipe) the existing win 7 partition in order to achieve the desired schema is not problem for me. So, let's start with this.

i don't have anything in the win partition that's important. it's in clear, OS only situtation. So no problem formating

thnx for your replies.

That's what I was waiting for.
In that case, you could use GParted to wipe the whole HDD and start partitioning.
I suggest this scheme:

Your HDD is 2TB. Let's say, 250GB for Windows, 250GB for Ubuntu and 1.5TB for Data (Movies, Music, Pictures, etc)

Windows Partition as you may know is NTFS
Ubuntu require ext4 filesystem + SWAP partition

Your partitions should be like:

sda1 (Primary Partition) : NTFS, 250GB

sda2 (Primary Partition) : NTFS, 1.5TB

sda5 (Extended Partition)

sda6 (Logical Partition) : ext4, 20-50GB - Mount point is / which is root

sda7 (Logical Partition) : ext4, -200GB - Mount point is /home - all your data and settings for Ubuntu will be stored here  

sda8 ((Logical Partition) : SWAP - swap partition = Size of your RAM times 2 OR Size of your RAM [ Example, if your RAM is 4GB then either to set the SWAP partition to 4GB or 8GB).

---

### Post by amjjawad on 2010-10-24
> **Mark Phelps said:**
> BEFORE you do anything else, go into Win7, use the Backup feature to create and burn a Win7 Repair CD.  This will prove invaluable later should you need to repair the Win7 boot loader as a side-effect of partitioning.

You forgot to add "Defragment". ;)

---

### Post by sfotakis on 2010-10-24
> **amjjawad said:**
> 
I suggest this scheme:

<...>


so i do all this using gparted after booting with ubuntu live cd.

then boot with win7 cd and install on 1st partition

and then boot with ubuntu cd and install on the other partition ? 

many thnx for your support.

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> so i do all this using gparted after booting with ubuntu live cd.

then boot with win7 cd and install on 1st partition

and then boot with ubuntu cd and install on the other partition ? 

many thnx for your support.

Or you could use Windows7 CD/DVD to create 250GB for Windows and leave the remaining as unallocated area. Finish Windows 7 Installation and then boot from Ubuntu's liveCD, start to partition the unallocated area as explained previously (except sda1 will be already there) and then install Ubuntu. Before you install Ubuntu, just try to use it from the LiveCD and check whether everything is okay or not. After that, GRUB2 should be installed in the MBR and after you reboot, you'll have two options to choose from, Ubuntu and Windows.

You have now two options so it's your call :)

You welcome :)

---

### Post by sfotakis on 2010-10-24
trying this right now. will let you know.
:)

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> trying this right now. will let you know.
:)

I'll be waiting for you :)

---

### Post by sfotakis on 2010-10-24
> **amjjawad said:**
> Or you could use Windows7 CD/DVD to create 250GB for Windows and leave the remaining as unallocated area. Finish Windows 7 Installation and then boot from Ubuntu's liveCD, start to partition the unallocated area as explained previously (except**[SIZE="4"] sda1 will be already there[/SIZE]**) and then install Ubuntu. 

ok, here's the issue.

What if sda1 is NOT there? 

Finished Win7 installation by creating the 250GB NTFS partition using windows installation tool. Then restarted with Ubuntu Live CD. Clicked try. Run GParted and i get a full grey of unallocated 1.82TiB and no sign of the win partition. 
:(

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> ok, here's the issue.

What if sda1 is NOT there? 

Finished Win7 installation by creating the 250GB NTFS partition using windows installation tool. Then restarted with Ubuntu Live CD. Clicked try. Run GParted and i get a full grey of unallocated 1.82TiB and no sign of the win partition. 
:(

I'm just concern if you wipe your HDD with GParted, use it to partition your HDD, reboot, install Windows7 and the same issue will happen again.
I'm not sure whether it's a bug or there's something I'm missing. My mind is a bit messed up because I have a problem here at home and have to deal with it personally.

Let's try google. I'll search for similar case, hopefully we could find a solution.
In the mean time, don't do anything, let's see what we could find out.

Sorry, but I'll try to help you :)

---

### Post by sfotakis on 2010-10-24
> **amjjawad said:**
> 
Let's try google. I'll search for similar case, hopefully we could find a solution.
In the mean time, don't do anything, let's see what we could find out.

Sorry, but I'll try to help you :)

thank you, i'm searching it too in the net.

---

### Post by Quackers on 2010-10-24
If you boot the Ubuntu Live CD and choose "try Ubuntu" please go to the site below and download the boot info script to your desktop. Then run the script using the command on the site. This will create a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. (to get code tags click on New Reply then on the # symbol in the toolbar, then paste in between the generated tags)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sfotakis on 2010-10-24
hmm... ok. here's something that might be interesting and shed some light for the more experienced users.

i'm opening Ubuntu Disk Utility (always by 'trying' with the Live CD) and i actually can see the 250GB NTFS partition of the win installation.

i'm attaching two screenshots 

1) GParted screenshot which has not the NTFS partition
2) Disk Utility with the NTFS partition there

any thoughts ?

---

### Post by sfotakis on 2010-10-24
> **sfotakis said:**
> hmm... ok. here's something that might be interesting and shed some light for the more experienced users.

i'm opening Ubuntu Disk Utility (always by 'trying' with the Live CD) and i actually can see the 250GB NTFS partition of the win installation.

i'm attaching two screenshots 

1) GParted screenshot which has not the NTFS partition
2) Disk Utility with the NTFS partition there

any thoughts ?

sorry, with the correct 2nd attachment now (i hope)

---

### Post by GrouchyGaijin on 2010-10-24
Just a question as I'm a noob too.
I had a laptop running Windows XP.  I popped in the Ubuntu 10.04 install CD and it asked me specifically if I wanted to keep Windows.  I said yes and then told it how much of the Windows partition to give to Ubuntu.  Now I have a dual boot machine.

Can someone clarify why this is different in his situation?  That is, why doesn't Ubuntu see Windows and ask him if he wants to keep it?  Was I just really lucky?

---

### Post by sfotakis on 2010-10-24
> **Quackers said:**
> This will create a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. 

```
                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   512,002,047   511,795,200   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3890ED3290ECF6F2                       ntfs       System Reserved               
/dev/sda2        A23EF3933EF35F2B                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```


sda1:
/bootmgr /Boot/BCD /grldr
hmmmm....
might be remainder of a try i gave it with EasyBCD ?


thank you

---

### Post by Quackers on 2010-10-24
You seem to have chopped off the end of the boot script.
Is this on a MAC computer by any chance?

---

### Post by sfotakis on 2010-10-24
> **Quackers said:**
> You seem to have chopped off the end of the boot script.
Is this on a MAC computer by any chance?

although i'm right now writing from a MacBook, the computer in case is not a Mac.

thank you

---

### Post by sfotakis on 2010-10-24
from what i can see in the results.txt i understand that the system see 2 different partitions with Windows on them ? or am i totally wrong ?

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================
```

---

### Post by amjjawad on 2010-10-24
Okay, I'll post all what I know.
1) Did you check MD5Sum before burning the LiveCD?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) Try to create a LiveUSB instead of LiveCD. It's much faster than the LiveCD.

3) If the same problem happened again, I guess either you wait for someone who knows what's wrong or search google.

Sorry, that's all what I know.

---

### Post by Quackers on 2010-10-24
I don't know why grldr is there and I suspect that 
"GUID Partition Table detected, but does not seem to be used." will have something to do with your problems.
I think we need srs5694 to come along and render assistance :-)

---

### Post by Quackers on 2010-10-24
> **sfotakis said:**
> from what i can see in the results.txt i understand that the system see 2 different partitions with Windows on them ? or am i totally wrong ?

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================
```

You are correct, but that is quite normal with a Windows 7 installation.

---

### Post by sfotakis on 2010-10-24
> **amjjawad said:**
> Okay, I'll post all what I know.
1) Did you check MD5Sum before burning the LiveCD?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) Try to create a LiveUSB instead of LiveCD. It's much faster than the LiveCD.


1)No. Will do
2)I will do that
thank you.

> **Quackers said:**
> 
I think we need srs5694 to come along and render assistance :-)

thank you, i ll wait :)

---

### Post by Quackers on 2010-10-24
> **GrouchyGaijin said:**
> Just a question as I'm a noob too.
I had a laptop running Windows XP.  I popped in the Ubuntu 10.04 install CD and it asked me specifically if I wanted to keep Windows.  I said yes and then told it how much of the Windows partition to give to Ubuntu.  Now I have a dual boot machine.

Can someone clarify why this is different in his situation?  That is, why doesn't Ubuntu see Windows and ask him if he wants to keep it?  Was I just really lucky?

It may be because of a partitioning problem or it may be because a GUID partition table may have been used at some time. (Yours is likely to be a MBR type partition table).

---

### Post by amjjawad on 2010-10-24
> **sfotakis said:**
> 1)No. Will do
2)I will do that
thank you.



thank you, i ll wait :)

1) Then what are you waiting for? :)
Check the MD5Sum of the .iso file that you downloaded (Ubuntu).
The result should be the same, otherwise, your downloaded iso file is damaged.

2) You'll noticed it'll be faster :)

---

### Post by sfotakis on 2010-10-24
> **amjjawad said:**
> 1) Then what are you waiting for? :)
Check the MD5Sum of the .iso file that you downloaded (Ubuntu).
The result should be the same, otherwise, your downloaded iso file is damaged.

2) You'll noticed it'll be faster :)

ok don't know why everything is messed up that much...

downloaded again the .iso of ubuntu 10.10 desktop amd64 and checked md5, found it ok.

tried Universal USB Installer (as it says @ubuntu.com) to create a USB from another win machine but when i try the usb stick on the machine that has the issue, although it boots and shows me the purple background with the ubuntu logo the system stays there for long time and does nothing. The dots are blinking but nothing else. I burned the same .iso (which is MD5 checked and found ok) to a new cd and re-tried with the same results. Show me the ubuntu logo in purple background and stays there.

The 1st Ubuntu LiveCD still boot ok and i'm able to 'Try Ubuntu' but with the same problem (NTFS partition not getting displayed)...

thank you all for your support.

---

### Post by srs5694 on 2010-10-24
> **Quackers said:**
> I don't know why grldr is there and I suspect that 
"GUID Partition Table detected, but does not seem to be used." will have something to do with your problems.

You're exactly right. It appears that the disk was partitioned using the GUID Partition Table (GPT) scheme (perhaps in a Mac) and was subsequently repartitioned using Master Boot Record (MBR) software that doesn't understand GPT. This tends to throw libparted, the library upon which the Ubuntu installer is based, for a loop.

Fortunately, the solution isn't all that difficult, although you will have to download and manually install some software:


[list=1]
[*]Boot into the Ubuntu Live CD. Alternatively, get the latest version of [Parted Magic](http://partedmagic.com/) or [System Rescue CD,](http://www.sysresccd.org/) boot it, and skip the next two steps.
[*]Go to the [GPT fdisk (gdisk) download page](http://sourceforge.net/projects/gptfdisk/files/) and obtain the latest version (0.6.13) for your architecture. I'm afraid I missed what that was, if it was stated. It'll be either the gdisk*i386.deb or gdisk*amd64.deb file.
[*]Install the gdisk package file. Double-clicking on the desktop should do this, or you can type "sudo dpkg -i gdisk*deb" in the appropriate directory.
[*]Open a shell and type "sudo sgdisk --zap /dev/sda". It'll complain about partition problems, but it will still work. Be sure to use the --zap option, not --zap-all; also, note that the command name is sgdisk, not gdisk.
[*]Proceed with your Ubuntu installation.
[/list]


Alternatively, if you can boot Windows, you can use the Windows version of the gdisk program; however, you'll have to use the interactive gdisk program rather than the command-line sgdisk, since I've never compiled the latter for Windows. (If you want to install all the libraries, it can theoretically be compiled, but I've never tried.)

If you have questions, please ask.

---

### Post by sfotakis on 2010-10-25
> **srs5694 said:**
> You're exactly right. It appears that the disk was partitioned using the GUID Partition Table (GPT) scheme (perhaps in a Mac) and was subsequently repartitioned using Master Boot Record (MBR) software that doesn't understand GPT. This tends to throw libparted, the library upon which the Ubuntu installer is based, for a loop.

Fortunately, the solution isn't all that difficult, although you will have to download and manually install some software:


[list=1]
[*]Boot into the Ubuntu Live CD. Alternatively, get the latest version of [Parted Magic](http://partedmagic.com/) or [System Rescue CD,](http://www.sysresccd.org/) boot it, and skip the next two steps.
[*]Go to the [GPT fdisk (gdisk) download page](http://sourceforge.net/projects/gptfdisk/files/) and obtain the latest version (0.6.13) for your architecture. I'm afraid I missed what that was, if it was stated. It'll be either the gdisk*i386.deb or gdisk*amd64.deb file.
[*]Install the gdisk package file. Double-clicking on the desktop should do this, or you can type "sudo dpkg -i gdisk*deb" in the appropriate directory.
[*]Open a shell and type "sudo sgdisk --zap /dev/sda". It'll complain about partition problems, but it will still work. Be sure to use the --zap option, not --zap-all; also, note that the command name is sgdisk, not gdisk.
[*]Proceed with your Ubuntu installation.
[/list]


Alternatively, if you can boot Windows, you can use the Windows version of the gdisk program; however, you'll have to use the interactive gdisk program rather than the command-line sgdisk, since I've never compiled the latter for Windows. (If you want to install all the libraries, it can theoretically be compiled, but I've never tried.)

If you have questions, please ask.

hi and thank you for your reply.

currently @work, pc in case @home. Will try in a few hours and let you know.

---

### Post by sfotakis on 2010-10-25
> **srs5694 said:**
> You're exactly right. It appears that the disk was partitioned using the GUID Partition Table (GPT) scheme (perhaps in a Mac) and was subsequently repartitioned using Master Boot Record (MBR) software that doesn't understand GPT. This tends to throw libparted, the library upon which the Ubuntu installer is based, for a loop.

Fortunately, the solution isn't all that difficult, although you will have to download and manually install some software:


[list=1]
[*]Boot into the Ubuntu Live CD. Alternatively, get the latest version of [Parted Magic](http://partedmagic.com/) or [System Rescue CD,](http://www.sysresccd.org/) boot it, and skip the next two steps.
[*]Go to the [GPT fdisk (gdisk) download page](http://sourceforge.net/projects/gptfdisk/files/) and obtain the latest version (0.6.13) for your architecture. I'm afraid I missed what that was, if it was stated. It'll be either the gdisk*i386.deb or gdisk*amd64.deb file.
[*]Install the gdisk package file. Double-clicking on the desktop should do this, or you can type "sudo dpkg -i gdisk*deb" in the appropriate directory.
[*]Open a shell and type "sudo sgdisk --zap /dev/sda". It'll complain about partition problems, but it will still work. Be sure to use the --zap option, not --zap-all; also, note that the command name is sgdisk, not gdisk.
[*]Proceed with your Ubuntu installation.
[/list]


Alternatively, if you can boot Windows, you can use the Windows version of the gdisk program; however, you'll have to use the interactive gdisk program rather than the command-line sgdisk, since I've never compiled the latter for Windows. (If you want to install all the libraries, it can theoretically be compiled, but I've never tried.)

If you have questions, please ask.

:guitar:

thank you so much!.. Everything worked as described above.

can boot on both ubuntu 10.10 and win 7 using ubuntu bootloader and i can see the 'shared' partition without a prob.

thank you all for your support.

---

### Post by amjjawad on 2010-10-25
HOOHAA :D
Congratulation :)

---

### Post by Quackers on 2010-10-25
Very, very niiiiiice :-)

---

### Post by antileet on 2011-01-03
> **srs5694 said:**
> Fortunately, the solution isn't all that difficult, although you will have to download and manually install some software

wow man, you saved my day!! i've been trying to solve this problem for days!<3:guitar:

---

