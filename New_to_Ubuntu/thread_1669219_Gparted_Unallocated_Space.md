---
title: "Gparted Unallocated Space"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by Linyx on 2011-01-17
I Had Triple boot Linx(Gnome/KDE) & Seven.....So i was trying to also Install XP On Logical partition for some Reasons, while installing i get an Error so i stop installing , 

After that whenever now i Open Up G-parted, i see My Entire Drive as Unallocated Space...

However my other Partitions are fine...

For More info 

```
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       11749    52428127+  83  Linux
/dev/sda3           11750       38913   218194830    5  Extended
/dev/sda4           13055       23497    83883366    7  HPFS/NTFS
/dev/sda5           11750       13054    10482349+   7  HPFS/NTFS
/dev/sda6           23498       32635    73400953+   7  HPFS/NTFS
/dev/sda7           32636       35246    20972826   83  Linux
/dev/sda8           35247       35507     2096451   82  Linux swap / Solaris

```

---

### Post by Quackers on 2011-01-17
Carrying on from your other thread, it seems that your extended partition is now sda3 (not sda4, as it was before).
However, sda3 now includes a partition called sda4. This is not normal. Partitions inside an extended partitions will normally be named sda5 and upwards. Have you created a primary partition and put it within the extended partition?

---

### Post by coffeecat on 2011-01-17
> **Linyx said:**
> So i was trying to also Install XP On Logical partition for some Reasons

> **Quackers said:**
> However, sda3 now includes a partition called sda4. This is not normal. Partitions inside an extended partitions will normally be named sda5 and upwards. Have you created a primary partition and put it within the extended partition?

Just thought I'd chip in here, Quackers, because this rings a bell. I can't remember the exact details, but the OP of another thread tried to install Windows XP to a logical partition and ended up with a primary partition inside an extended too - and a non-functional XP as well. I wonder if this is a "quirk" of the XP installer when you try to install to a logical partition. I think I might fish out a spare HD and XP install disc and try for myself sometime. :)

---

### Post by srs5694 on 2011-01-17
> **Quackers said:**
> However, sda3 now includes a partition called sda4. This is not normal.

It's not only "not normal," it's not legal; the partition table is *not* OK.

The easiest fix is to rename /dev/sda4 as /dev/sda9 using sfdisk:


[list=1]
[*]Type "sudo sfdisk -d > parts.txt". This will produce a file called parts.txt with the partition data.
[*]Type "sudo chown yourusername: parts.txt" to give yourself ownership of parts.txt. (Change "yourusername" to your username.)
[*]Copy parts.txt to a removable disk (a USB flash drive, floppy disk, CD-R, or whatever).
[*]Load parts.txt into your favorite plain text editor. (Use gedit if you have no favorite; it's easy to use.)
[*]Change "/dev/sda4" to "/dev/sda9".
[*]Move the line for /dev/sda9 to the end of the partition list.
[*]Save your changes and exit from the text editor.
[*]Type "sudo sfdisk --force /dev/sda < parts.txt" to implement your changes.
[*]Reboot.
[/list]


Your partition table will now be fixed. Chances are Windows XP (on what's now /dev/sda9) will not boot, but it wasn't booting before, so that's no loss.

If this creates more problems, you can boot using an emergency system and restore the original (broken) partition table by using the sfdisk command in step #8 using the copy of the file made in step #3.

If you really want to install Windows XP, in theory it should be installable on a logical partition *if* you've got another Windows installation on a primary partition; however, as you've discovered, this doesn't always go smoothly. I recommend you ask for advice on a Windows forum, since you're more likely to find expertise related to Windows quirks and bugs there than here. (Perhaps somebody here will have a suggestion, though.)

Alternatively, you could load XP up in a virtual machine (VirtualBox, VMWare, or QEMU, for instance). This can work quite well, and you're less likely to trash your whole computer messing with it this way.

---

### Post by Linyx on 2011-01-18
Thanks for All Replies, and Sorry for my Late Reply ;)

Actually what i did wrong is i had installed a Partial Xp into the unallocated Space as Shown in my Below Screen-Shot.

As you Can Guess From the Screen-Shot that i had sda5, 6 , 7 & 8,
I think now this unallocated Space will be sda9, isn't?

I had Searched a little Bit and have found a Simple Solution, but didn't tried it yet, and For that i need Gparted-Live Cd, Although i have Image but didn't have CD-Writer right now;)

So i decided to make Gparted-Live USB, can any one know that how to do this...?

Moreover the Solution was something like this...

```
    * Boot from a live cd which has test disk utility (gparted live cd).

    * Open up a terminal once you have booted from the live cd and run testdisk and write the partition table to disk [analyze>proceed>write].

    * Now run gparted and it will recognize all the partitions

```

---

### Post by Linyx on 2011-01-18
Yes i did something wrong, but Honestly i made an Extended Partition within Extended, i didn't made a Primary Partition.....
But when i was installing XP, it told me to formate that drive so, i formate it Again, i think that was my Mistake, maybe while done by XP make that Extended Partition > Primary Partition,

**@srs5694**:- I had Done Exactly as You described, As you mentioned I edited my parts.txt...and now Looks like

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 83891367, Id= 7, bootable
/dev/sda2 : start= 83891430, size=104856255, Id=83
/dev/sda3 : start=188747685, size=436389660, Id= 5
/dev/sda5 : start=188747811, size= 20964699, Id= 7
/dev/sda6 : start=377479368, size=146801907, Id= 7
/dev/sda7 : start=524281338, size= 41945652, Id=83
/dev/sda8 : start=566227053, size=  4192902, Id=82
/dev/sda9 : start=209712573, size=167766732, Id= 7
```

Moreover when i enter " sudo sfdisk --force /dev/sda < parts.txt" it shows me an error Message...

```
sudo sfdisk --force /dev/sda < parts.txt
[sudo] password for assassin:
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   5221    5222-  41945683+   7  HPFS/NTFS
/dev/sda2       5222   11748    6527   52428127+  83  Linux
/dev/sda3      11749   38912   27164  218194830    5  Extended
/dev/sda4      13054+  23496   10443-  83883366    7  HPFS/NTFS
/dev/sda5      11749+  13053    1305-  10482349+   7  HPFS/NTFS
/dev/sda6      23497+  32634    9138-  73400953+   7  HPFS/NTFS
/dev/sda7      32635+  35245    2611-  20972826   83  Linux
/dev/sda8      35246+  35506     261-   2096451   82  Linux swap / Solaris
Warning: bad partition start (earliest 566226991)
cannot build surrounding extended partition

sfdisk: bad input

```

I have also tried from Live Live-CD, still that Problem....Unallocated Space

---

### Post by Linyx on 2011-01-18
bump

---

### Post by srs5694 on 2011-01-18
I've never seen sfdisk complain about writing to an in-use disk -- but I may never have tried it, either! Try booting from a live CD, disable swap ("sudo swapoff -a"), and try the sfdisk command. (Verify that /dev/sda is the same disk when using the live CD as when booted into your regular installation, though; sometimes disk identifiers change around when you reboot.)

---

### Post by Quackers on 2011-01-18
Linyx, srs5694 is the partition table doctor :-) he always knows what's best!

For your information an extended partition is a different type of primary partition.

---

### Post by Linyx on 2011-01-19
> **srs5694 said:**
> I've never seen sfdisk complain about writing to an in-use disk -- but I may never have tried it, either! Try booting from a live CD, disable swap ("sudo swapoff -a"), and try the sfdisk command. (Verify that /dev/sda is the same disk when using the live CD as when booted into your regular installation, though; sometimes disk identifiers change around when you reboot.)

I have Tried as You mentioned, i had unmount all partitions Including Swap,

But it shows me that massage as i described in the Above Post, maybe i miss something, but i am sure , i did Exactly as you had Described....

Anyhow, i am now trying to install Ubuntu & Windows in X64, therefore i had to remove it, and I have decided to partition again....

---

### Post by amjjawad on 2011-01-19
> **srs5694 said:**
> If you really want to install Windows XP, in theory it should be installable on a logical partition *if* you've got another Windows installation on a primary partition; however, as you've discovered, this doesn't always go smoothly.
 
 I have installed Windows XP on a Slave HDD and it did work but never  ever thought to install it on a Logical Partition because I know that  won't work.
 
 >  
 Alternatively, you could load XP up in a virtual machine (VirtualBox,  VMWare, or QEMU, for instance). This can work quite well, and you're  less likely to trash your whole computer messing with it this  way.
 
+1
That is exactly what I have done. I no more Dual/Multi-Boot with  Windows. Windows if needed should be locked inside Virtual Machines :)

---

### Post by amjjawad on 2011-01-19
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

All what I did was "refresh" after I got "Network Error" :(

---

### Post by amjjawad on 2011-01-19
> **srs5694 said:**
> If you really want to install Windows XP, in theory it should be installable on a logical partition *if* you've got another Windows installation on a primary partition; however, as you've discovered, this doesn't always go smoothly.
 
 I have installed Windows XP on a Slave HDD and it did work but never  ever thought to install it on a Logical Partition because I know that  won't work.
 
 >  
 Alternatively, you could load XP up in a virtual machine (VirtualBox,  VMWare, or QEMU, for instance). This can work quite well, and you're  less likely to trash your whole computer messing with it this  way.+1
That is exactly what I have done. I no more Dual/Multi-Boot with  Windows. Windows if needed should be locked inside Virtual Machines :)

---

### Post by amjjawad on 2011-01-19
> **srs5694 said:**
> If you really want to install Windows XP, in theory it should be installable on a logical partition *if* you've got another Windows installation on a primary partition; however, as you've discovered, this doesn't always go smoothly.
 
 I have installed Windows XP on a Slave HDD and it did work but never  ever thought to install it on a Logical Partition because I know that  won't work.
 
 >  
 Alternatively, you could load XP up in a virtual machine (VirtualBox,  VMWare, or QEMU, for instance). This can work quite well, and you're  less likely to trash your whole computer messing with it this  way.+1
That is exactly what I have done. I no more Dual/Multi-Boot with  Windows. Windows if needed should be locked inside Virtual Machines :)

---

### Post by amjjawad on 2011-01-19
> **srs5694 said:**
> If you really want to install Windows XP, in theory it should be installable on a logical partition *if* you've got another Windows installation on a primary partition; however, as you've discovered, this doesn't always go smoothly.
 
 I have installed Windows XP on a Slave HDD and it did work but never  ever thought to install it on a Logical Partition because I know that  won't work.
 
 >  
 Alternatively, you could load XP up in a virtual machine (VirtualBox,  VMWare, or QEMU, for instance). This can work quite well, and you're  less likely to trash your whole computer messing with it this  way.+1
That is exactly what I have done. I no more Dual/Multi-Boot with  Windows. Windows if needed should be locked inside Virtual Machines :)

---

### Post by Linyx on 2011-01-19
@Amjawad

Your Post is Submitted Trice,,i hope it is a Mistake....Never mind,

Moreover, i won't install Windows in VM, Because that is for Limited User, but sometimes i like Playing games ;) and & I won't Satisfied with 2D Games therefore Decided to Dual-boot.....

---

### Post by amjjawad on 2011-01-19
> **Linyx said:**
> @Amjawad

Your Post is Submitted Trice,,i hope it is a Mistake....Never mind,


[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

5 times actually.

---

### Post by srs5694 on 2011-01-19
I did a little more checking on the sfdisk error code, and found that it can fail for reasons other than the disk being in use; sfdisk is just sloppy in how it reports the error. One of these reasons is if the disk contains no partition table. Although that's not the case for you, it's conceivable that it's failing because of the partition table corruption. If so, you could work around it by creating a fresh (empty) partition table in fdisk or GParted; however, if that fails, you'll then be left with no partitions on the disk.

It might be worth checking the SMART status of the disk, just in case there's a hardware fault that's just starting to show up in this odd sfdisk error. You can do this using GSmartControl (install the gsmartcontrol package using apt-get, Synaptic, or whatever). I think that Ubuntu's disk utility also shows the SMART status of your disks.

---

### Post by Linyx on 2011-01-20
> **srs5694 said:**
> you could work around it by creating a fresh (empty) partition table in fdisk or GParted; however, if that fails, you'll then be left with no partitions on the disk.

How could i Create a partition table as it would then Erase all My Data...? is their any other Method so that i can Make Rough partition table exactly same as i have now, and then replace it with this own **Without Losing data**,...Looks Like silly question, i know(lolx)...

Anyway, i had Recreated my Partition table and i won't try to install windows in Logic partition next time.

I would like to know about the Partition table deeply , if you have any Good link for the partition trouble shooting in Linux, post it here so that i can study it....

Thanks for nice Suggestions.....:p

---

### Post by amjjawad on 2011-01-20
Some basic info:

[http://en.wikipedia.org/wiki/Partition_table](http://en.wikipedia.org/wiki/Partition_table) (don't forget to check the links inside - MBR)

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)

Of course a lot more on Google.

I'd suggest to start with the basic information first then go deeper.

As for fixing the MBR without losing data, I guess I've seen that somewhere but of course the easiest fix is to format IF AND ONLY IF a backup had been made before.

I always keep my backup on external HDDs. Since I've started with Linux, I always format my HDD to try different and new Distributions.

---

### Post by srs5694 on 2011-01-20
First, that sfdisk error, particularly when you get it from an emergency boot CD rather than from a Linux installation on the hard disk, is troubling. Any repair attempt at this point poses some risk of damaging your data. Thus, I must strongly advise you to back up everything of value on the hard disk onto another disk before you attempt anything else. Any methods of recovery I can think of at this point pose some risk of blowing up in your face, particularly since sfdisk's weird behavior suggests something unknown may be wrong with the data structures or even the disk's hardware.

Second, regarding the disk's hardware, you should definitely check the disk's SMART status, as I outlined in [post #18.](http://ubuntuforums.org/showpost.php?p=10376075&postcount=18) (You can do this safely; it's a diagnostic, not a recovery attempt.) If you disk is developing a hardware fault, you definitely want to replace it. You should be able to replace the disk and copy the partitions one by one in a way that will ensure your current partitioning problems aren't repeated on the new disk. (Post back again for advice on doing this, if it proves necessary.) If the disk is OK, then whatever's causing sfdisk to behave strangely is a software issue, not a hardware problem.

Third, I do know of another way to correct your problem with /dev/sda4 overlapping with /dev/sda3; however, this is where we get into the category of increasing risk:


[list=1]
[*]Download GPT fdisk (gdisk) from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) Get the latest Debian package (.deb) for your architecture (amd64 or i386). *Do not use the gdisk package provided by the Ubuntu repositories!* It's old and has a bug that will make matters worse when you use it as I'm about to describe!
[*]Launch gdisk on your disk, as in "sudo gdisk /dev/sda". It will create an in-memory GUID Partition Table (GPT) conversion of your Master Boot Record (MBR) partitions. GPT doesn't distinguish between primary, extended, and logical partitions, so this conversion eliminates the problem. Unfortunately, Windows can't boot from GPT on a BIOS-based computer, so you can't just write the GPT data and be done with it; you've got to convert it back....
[*]Type "r" to enter the recovery & transformation menu.
[*]Type "p" to view the current partition table, as interpreted by gdisk. If something looks weird, type "q" to quit without saving the changes.
[*]Type "g" to convert the in-memory GPT representation of your disk back to MBR form. You'll see a summary of what gdisk will do in terms of primary/logical assignments and partition type codes. Follow the prompts to change anything you want to change. You *will* have to change the type codes of the Linux data partitions (GPT uses the same code for Linux and Windows partitions, so that information is lost), and you may need to change some primary/logical assignments. See the "Converting from GPT to MBR" section of [this Web page](http://www.rodsbooks.com/gdisk/mbr2gpt.html) for more information.
[*]When you're satisfied with your type code and primary/logical assignments, type "0" to accept the setup, followed by "y" to confirm the change. The program should write your MBR partition table and exit.
[*]Type "sudo fdisk -lu /dev/sda" to verify that the partitions are correctly defined on the disk. (Save the output and post it here without rebooting if it looks even remotely wrong.)
[*]Type "sudo grub-install /dev/sda" to re-install GRUB.
[*]Reboot.
[/list]


With any luck, the problem will be fixed at this point; however, I'd like to emphasize again that this is a risky recovery procedure, particularly given the odd sfdisk behavior. Whatever's causing sfdisk to flake out could cause problems with gdisk, and gdisk wasn't even intended to solve this problem, so using it in this way is a bit risky to begin with.

---

### Post by Linyx on 2011-01-22
Thats was a nice explanation but i get a fraction of your Post as i don't know some terms like GPT , and some more,

Right now i had partitioned again and my Hardware is totally fine....

I will read it again once i study some of the terminology...Which i don't know right now..


Thanks for support....:P

---

### Post by Quackers on 2011-01-22
We're all learning, all the time :-)

---

### Post by Linyx on 2011-01-22
> **Quackers said:**
> We're all learning, all the time :-)

Hmmm...but i has heard the above terms first time...:D

---

