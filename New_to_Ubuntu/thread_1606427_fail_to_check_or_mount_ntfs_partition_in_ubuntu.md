---
title: "fail to check or mount ntfs partition in ubuntu"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by redmorning on 2010-10-26
Hello,

*I know that i must post this classic problem on windows forums (i already have) or search on google (i already have). But i am a ubuntu user and i like to post my problem to here too, if you think this is not your (ubuntus) business, ignore it, doesn't matter. If you have any idea, welcome.That's the post which i send to windows forums.*

Hello,

Hardware : Acer Aspire Timeline X 3820TG

OS : Windows 7, Ubuntu 10.04

Problem: Three days ago when i was booting ubuntu i got a disk error message during a routine check from windows 7 ntfs partition (it is auto mounting in linux). i ignored it, because i was in a hurry. After i got some problems un ubuntu. When i restarted my pc i cannot reach to ubuntu anymore but i was able to boot windows 7, no problem with that. Then i repaired my ubuntu by unmounting windows partition from /etc/fstab and checking linux file system with "fsck" from a live usb. This time it was windows 7 which i could not able to boot. Now, when i try to check windows ntfs partititon from ubuntu with "ntfsfix" i get a "Mounting volume... Segmentation fault" and when i try to mount this volume i get "Error mounting: mount exited with exit code 2: ". I googled this and understood that i have to run a "chkdsk" from windows itself, it is the healtiest solution but my problem i cannot reach even to login screen, just a black screen, it is like the pc stops working. There is a recovery partition on the pc but it lets me to format the partition C (this is not the case because i only have C where all my stuff are stored, the reason is i don't use windows unless i need it) or format all windows system (which i don't prefer at this point.).

If you need any more information i can write. I'm a stuck and yes i googled it already.

Thanks in advance.



Extra question for the ubuntuforums gurus; my memtest86+ doesn't work, i can see the blue screen for 1-2 seconds. i think it is related to disk errors. Am i right?

---

### Post by oldfred on 2010-10-26
ntfsfix only makes minor repairs and sets the flag for chkdsk to run on next boot of windows. If chkdsk is required gparted & ubuntu will not mount the windows partition, so you do not create issues that chkdsk then could not fix.
If you do not have a windows repair CD:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Then if windows chkdsk has not repaired everything:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by redmorning on 2010-10-26
Hi oldfred,

thank you for your quick answer, i don't have a cd/dvd drive so i created a bootable usb with 'unetbootin' and booted from it but it didn't work. normally i can boot from usb (created in unetbootin) for 'ubuntu live disk' or 'gparted' but this doesn't work. when i boot from usb i got the gray unetbootin screen (grub like) with just one entry 'default' which is nothing.

Do you have any other idea to run chkdsk?

---

### Post by coffeecat on 2010-10-26
Two thoughts.

> **piratejackus said:**
> thank you for your quick answer, i don't have a cd/dvd drive

Your best bet is one of the recovery CDs that oldfred linked to. How valuable is your data that is on the Window C: partition to you? Is it more valuable than the cost of purchasing a USB optical drive?

Second - I have no experience of this but I've seen Hiren's boot CD recommended when chkdsk is required.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

It has a mini XP on it which can be (so the page says) run from a USB drive. It includes XP's version of chdsk. Whether you want to use that to repair a Windows 7 system I don't know. There are differences in the way 7 and XP use NTFS which I don't understand. You might want to wait for someone who knows the answer to that to post.

---

### Post by sandyd on 2010-10-26
> **piratejackus said:**
> Hi oldfred,

thank you for your quick answer, i don't have a cd/dvd drive so i created a bootable usb with 'unetbootin' and booted from it but it didn't work. normally i can boot from usb (created in unetbootin) for 'ubuntu live disk' or 'gparted' but this doesn't work. when i boot from usb i got the gray unetbootin screen (grub like) with just one entry 'default' which is nothing.

Do you have any other idea to run chkdsk?

buy a portable (usb) drive
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by oldfred on 2010-10-26
These supposedly install windows to a USB.

Steps Needed to Install Windows 7 from a USB drive using Linux
[http://ubuntuforums.org/showthread.php?t=1604618](http://ubuntuforums.org/showthread.php?t=1604618)

Use unetbootin to copy windows iso to partition and install:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)

The only way I was able to install the repair CD to a USB was to copy it to a CD then use that to copy to the flash drive. (The mount & copy may work as that should be the same as what I did,but I have yet to try that). The issue I had was getting the windows boot sector set up correctly. Once copied I was even able to install grub and boot the repair CD from grub2. Then I was able to add other repair ISOs to the same flash and have grub loopmount those. I then have one flash to repair windows and linux.

---

### Post by redmorning on 2010-10-26
@coffeecat
i'm far from my home for studies and i have to keep my money in most of the cases, the data is important (photos and some documents). but i think i must be able to run chkdsk without an optical drive so i will give a shot to hiren's boot cd but at the link you gave, i couldn't find the software so i googled it and found:

[http://www.hirensbootcd.net/download.html]("http://www.hirensbootcd.net/download.html")
[http://www.hirensbootcd.net/screenshots.html]("http://www.hirensbootcd.net/screenshots.html")

they are the same things, aren't they? i think xp won't be a problem as oldfred mentioned i will just run a single command.

@sandyd
thank you but i want to try without it at first.

i will let you know after coffecats answer.

---

### Post by redmorning on 2010-10-26
@oldfred
> 
The only way I was able to install the repair CD to a USB was to copy it to a CD then use that to copy to the flash drive. (The mount & copy may work as that should be the same as what I did,but I have yet to try that)


sorry but i didn't understand exactly what you mean, how can i copy this iso to a cd while i don't have a optic drive. what i am missing?

p.s : the usb drive that i created with unetbootin by adding "Windows 7 64-bit Repair Disc" is not mountable anymore, ubuntu doesn't detect it (can't see in fdisk). What could be the reason?

---

### Post by redmorning on 2010-10-26
@coffeecat

can you please confirm the hiren's boot cd? the cd that you were talking about is the one which i am downloading, right? 

[http://www.hirensbootcd.net/download.html]("http://www.hirensbootcd.net/download.html")
[http://www.hirensbootcd.net/screenshots.html]("http://www.hirensbootcd.net/screenshots.html")

---

### Post by coffeecat on 2010-10-26
> **piratejackus said:**
> can you please confirm the hiren's boot cd?

As I said, I've never had occasion to use it, but I've seen it recommended several times for chkdsk and I was passing that recommendation on. Your links look right. Just check that you have Mini Windows XP on it - that's what you need for chkdsk.

But I still have reservations about using XP's chkdsk for repairing Windows 7. I don't have enough knowledge to say whether this would be advisable or not. I was hoping someone else would comment.

---

### Post by redmorning on 2010-10-26
when i boot from "Hirens boot cd" there are many options. i chose "mini xp" and in a second got the error :

CDBOOT: memory overflow error

there are other utilities but i am really efraid of damaging linux partitions and of course windows partitions. For example there is test disk utility but it is for linux as i know, so i don't have any idea how will it work on ntfs. is there any one who knows about hiren's boot cd?

by the way thank you coffeecat for your help. Maybe you could continue a little bit more. because when i search this error on google i couldn't find any well explained solution.

---

### Post by redmorning on 2010-10-26
i checked nearly all options in hirens boot cd, even testdisk but i didn't go to a deep analyse (it takes really too long). I might be wrong but as i read in son links (like [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Disk_selection") ) we can repair ntfs drives with testdisk, so can i run testdisk from ubuntu to check entire disk (windows 7 partition too) to repair bad sectors/errors?

i can't think any other solution.

@oldfred
if you could help me on creating a bootable usb for windows 7 recovery i will be really glad. 

Thanks

---

### Post by oldfred on 2010-10-27
Do you have access to a CD/DVD on another computer? That has been the only way I could do it so far. 

I am now trying some of the copy methods, but none have worked for me yet.

---

### Post by redmorning on 2010-10-27
Hi oldfred,

no i don't have any chance for that but i got a response from microsoft forums, the first part looks like worth to try :

> 
You may need another computer with Windows 7...

Windows 7 - Create a System Repair Disc on a Bootable USB Flash Drive without Burning a CD

[http://www.youtube.com/watch?v=nHk6BNtwy5w](http://www.youtube.com/watch?v=nHk6BNtwy5w)

Another guide:

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)


-for the first link we need a recovery partition on disk, i checked my frineds pc s but unfortunetly they don't have one, so i will keep that in memory.
-the second links first way is just like what you told me but as i don't have a cd/dvd drive it is useless for me. but the second way looks fine, i just need a windows 7 pc. 
i will be able to try it tomorrow. hope it works. i'm gonna let you know.

ciaou

---

### Post by oldfred on 2010-10-27
Since I only have XP I was not able to run the standard windows 7 commands. Your second link is exactly what I did, but but I did it from a CD of the repair ISO to create & copy the repair CD to a flash drive.

What I find different is that on the flash drive you still create a FAT32 partition and it creates a special boot sector as normally Vista/7 do not boot from FAT. I tried copying to a NTFS partition but when it boots it says it wants a CD, so something in copying to a flash drive or FAT partition converts something to see a flash drive, not a CD.

---

### Post by redmorning on 2010-10-29
*this is no longer a ubuntu issue but i want to finish this post with a result if i can.*

the link about this issue on microsoft forum is:
[http://social.answers.microsoft.com/Forums/en-US/w7install/thread/69517faf-850a-45fd-8195-6d4ed831f805?prof=required]("http://social.answers.microsoft.com/Forums/en-US/w7install/thread/69517faf-850a-45fd-8195-6d4ed831f805?prof=required")
[B][I]
here is the progress:[/I][/B]

[I]i achieved to see a windows screen!

 

i followed the instructions here [http://www.youtube.com/watch?v=nHk6BNtwy5w]("http://www.youtube.com/watch?v=nHk6BNtwy5w") and created a system repair bootable usb, thanks to TrekDozer.
(i changed a command: 
echo F: xcopy /h Wimre.wim f:\sources\boot.wim       { -F: xcopy without space- }
to
xcopy /h Wimre.wim g:\sources\boot.wim)
don't forget to change your drive label (!f->g/h/..!)


after i run chkdsk D: /f /r it checked the disk in 5 steps but as i understood it didn't fix the errors.

anyway, after i rebooted the system and chose windows 7 from grub i see a blank screen but with some information (at last). It was a classic (i came to this comment after a quick search in google) problem :

"Window failed to start. A recent hardware or software change might be the cause. To fix the problem:

1.Insert....

2. ....

...

status : 0xc000000f

info : The boot selection failed because a required device is anaccesible

....

"

 

-the last software i installed on windows was clementine (a data mining program) but i'm sure that after that installation i booted windows succesfully many times so i think this is not the issue.

-the last action that may be effect hardware was to copy a 60 gb data from windows to linux while i was on linux (ubuntu). After this operation i couldn't boot windows anymore.

 

now, i found some instructions for this problem on google, if you already experienced on this issue and achieved it, than i would like to hear your solution.
[/I]
 

thanks in advance.

i will continue to report it here, and if someone has a experience from ubuntu forums, they are welcome of course (:

---

### Post by redmorning on 2010-10-29
Now i will update windows boot menu with:

bootrec /fixMBR
bootrec /fixBoot
bootrec /rebuildBcd

but if i'm not mistaken i will loose ubuntu option in the grub menu, and to retrieve it i need to use easybcd which i don't know very much yet.
Is there a risque like loosing ubuntu or is it too difficult? 
i'm asking for who had experienced already easybcd and windows boot recovery.

i want to add that now i am able to run
> sudo ntfsfix /dev/sda3
and it checks the disk and then i can mount the partition. but in the partition there is just a folder with the "chkdsk" logs in it. So does it mean that i lost my data?

---

### Post by redmorning on 2010-10-30
[I]i feel like it is just me who continues on this post (:
nevermind.

this is about ubuntu:[/I]

if i loose grub menu in some way (running bootrec /fixMBR , bootrec /fixBoot , bootrec /rebuildBcd on windows ) then how can i  reinstall grub? because if i do that and loose grub and can't repair windows than i won't have a internet connection nor working OS. i have  a live ubuntu 10.04 usb stick for the bad days.

---

### Post by oldfred on 2010-10-31
Instructions on reinstalling boot loaders, old grub, grub2, windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by redmorning on 2010-10-31
hi oldfred,

i finally run those dos commands and couldn't retrieve windows 7, still the same error and lost ubuntu grub. now i'm in live usb without any OS. i followed the link to reinstall grub but `grub bootloader` is just a grub command-line which doesn`t let me do anything. i was hopping to see grub menu with listed OS`s installed on pc. where is my mistake.

keep googling...

i realized something
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdda4dda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       40349   310682967+   7  HPFS/NTFS
/dev/sda4           41624       60802   154045441    5  Extended
/dev/sda5           41624       60468   151367187+  83  Linux
/dev/sda6           60468       60782     2518016   82  Linux swap / Solaris
/dev/sda7           60782       60802      158720   83  Linux

Disk /dev/sdb: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007b16a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3816      976880    6  FAT16

```

so i mounted /dev/sda5 but the boot partition is seperated; /dev/sda7. but when i try to mount extended linux partition /dev/sda5 it doesn`t let to mount. i`m trying to mount boot partition.

nope! it doesn`t work either. i just have grub command line. i think it can`t find the os. that`s the reason. searching and waiting for advices..

---

### Post by oldfred on 2010-10-31
See version #3 and in particular the note on separate /boot partitions as you have to also mount that.

Full chroot mount partitions and reinstall:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

*Only if you have a separate boot partition*: 

[LIST]
[*]sdYY is the /boot partition designation (for example sdb3)
[*]**sudo mount /dev/sdYY /mnt/boot**
[/LIST]

With the short two line method it becomes three lines:
If separate /boot
$ sudo mount /dev/sda7 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

---

### Post by redmorning on 2010-10-31
oldfred, 

thank you very much for all your help, i was following the thread that you mentioned and post the problem there too. you were faster but i looked here a little bit late
[http://ubuntuforums.org/showthread.php?t=1014708&page=29]("http://ubuntuforums.org/showthread.php?t=1014708&page=29")

anyway, the same solution, i achived to boot in my ubuntu. now my mission is windows again and from now on l know how to retrieve my ubuntu when i lost grub bootloader.

thanks again.

---

### Post by redmorning on 2010-11-05
Hi again,

After i run chkdsk command succesfully from live usb disk i could enable to mount windows partition but unfornutely all i see under the windows (ntfs) partition was the chkdsk command logs. Why this damned windows writes log data directly to partition?
So does this mean that i lost my data, i hope not. I'm still trying to boot my windows 7, if i can access to my ntfs partition i will be glad because operating system is nothing, just my files are important.
any idea?

---

### Post by redmorning on 2010-11-11
bump!

---

### Post by oldfred on 2010-11-11
Did you run chkdsk from the windows Flash drive or the ntfsfix from Ubuntu? the ntfsfix only makes minor repairs and sets the chkdsk flag so windows will run chkdsk on next boot.

Were you able to run the windows 7 repairs?

---

### Post by redmorning on 2010-11-12
I run chkdsk from windows 7 flash drive for several times ans ntfsfix from ubuntu. I get the same boot error at windows startup. The thing is, why i am not able to see windows partition from ubuntu, i just can see chkdsk log files. What does this mean ? Do you think that i must give a try to testdisk? I don't need windows to work, i want to see my folders from ubuntu, someone from microsoft forums suggested to use other live linux dists: 
[http://social.answers.microsoft.com/Forums/en-US/w7install/thread/69517faf-850a-45fd-8195-6d4ed831f805?prof=required]("http://social.answers.microsoft.com/Forums/en-US/w7install/thread/69517faf-850a-45fd-8195-6d4ed831f805?prof=required")
> If the most important option is to recover your files, you can try two things.

1. Remove the hard drive and attach it to a second computer, and see if that computers OS can access your files.

2. Use another Linux LiveCD and see if you can access the Windows partition with it. Then copy the files to external storage.

Download PCLinuxOS LiveCD:
[http://pclinuxos.com/?page_id=180](http://pclinuxos.com/?page_id=180)

DSL Linux direct download:
[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/archive/dsl-4.4.9.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/archive/dsl-4.4.9.iso)

DSL Linux Main Page:
[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org) 

what do you think about this solution, i didn't have time to try it yet.

---

### Post by oldfred on 2010-11-12
The version of Linux is not particularly important. Some have repair tools installed as part of the distribution. Most of the tools that other distributions have can be downloaded into Ubuntu or Ubuntu's liveCD (but then lost on reboot). Sometimes others have different verisons of kernels, drivers & configs that work better. I keep several repair type installs on my USB flash drive in case I need them, but usually use Ubuntu as I am more famailiar with it.

sda2 is your hidden windows boot partition and sda3 is your windows install. When you look in the left panel of Nautilus do you see sometime like 150GB partition? That should be your windows install. If in gparted you label it as windows then it may show windows in Nautilus. On my laptop it shows my windows partition as /media/SQ004224P01. It looks like it was originally labeled that way.

---

### Post by redmorning on 2010-11-12
Sometimes i see that partition in the left menu, that's right. I booted from ubuntu flash drive and changed the label of sda3 from "SYSTEM RESERVED" to "windows" (i just wrote windows) but resault is same, only the chkdsk logs. 

When i mount that SYSTEM RESERVED partition, there is:
-'boot' folder
-'System Volume Information' folder
-'bootmgr' file

So in Naitulus, under the "computer" i have "File System" normally and this "500 GB Hard Disk: SYSTEM RESERVED". 
That's the situation.

---

### Post by oldfred on 2010-11-12
Are you sure system reserved was not sda2? What size is sda2 and sda3?

Lets get an up2date copy of this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by redmorning on 2010-11-12
```
piratejackus@ganj:~/software$ more RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden HPFS/NTFS
/dev/sda2    *     26,626,048    26,830,847       204,800   7 HPFS/NTFS
/dev/sda3          26,830,848   648,196,782   621,365,935   7 HPFS/NTFS
/dev/sda4         668,680,190   976,771,071   308,090,882   5 Extended
/dev/sda5         668,680,192   971,414,566   302,734,375  83 Linux
/dev/sda6         971,415,552   976,451,583     5,036,032  82 Linux swap / Solaris
/dev/sda7         976,453,632   976,771,071       317,440  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        407C47967C47859E                       ntfs       SYSTEM RESERVED               
/dev/sda3        01CB3146E0CB4240                       ntfs       Windows                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        9b78b480-8219-45c3-a524-10b805012d5e   ext2                                     
/dev/sda6        9fbf8e24-a37e-4b14-ad25-fbe8ef1b2944   swap                                     
/dev/sda7        5e4f1df6-cc68-4961-bbad-977b78b45254   ext2                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext2       (rw)
/dev/sda7        /boot                    ext2       (rw)
/dev/sda3        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/SYSTEM RESERVED   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext2    defaults	 0       1
/dev/sda7       /boot           ext2    defaults        0       2
#/dev/sda3       /windows        ntfs    defaults        0       0 
# swap was on /dev/sda6 during installation
UUID=9fbf8e24-a37e-4b14-ad25-fbe8ef1b2944 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 342.4GB: initrd.img
 342.4GB: initrd.img.old
 342.4GB: vmlinuz
 342.3GB: vmlinuz.old

============================= sda7/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 9b78b480-8219-45c3-a524-10b805012d5e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux	/vmlinuz-2.6.32-25-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro acpi_osi=Linux  quiet splash
	initrd	/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/vmlinuz-2.6.32-25-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro single acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux	/vmlinuz-2.6.32-24-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro acpi_osi=Linux  quiet splash
	initrd	/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/vmlinuz-2.6.32-24-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro single acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux	/vmlinuz-2.6.32-21-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro acpi_osi=Linux  quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=9b78b480-8219-45c3-a524-10b805012d5e ro single acpi_osi=Linux
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 5e4f1df6-cc68-4961-bbad-977b78b45254
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set daa41c49a41c2b11
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 407c47967c47859e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda7: Location of files loaded by Grub: ===================


 500.0GB: grub/core.img
 500.0GB: grub/grub.cfg
 499.9GB: initrd.img-2.6.32-21-generic
 499.9GB: initrd.img-2.6.32-24-generic
 500.0GB: initrd.img-2.6.32-25-generic
 499.9GB: vmlinuz-2.6.32-21-generic
 499.9GB: vmlinuz-2.6.32-24-generic
 499.9GB: vmlinuz-2.6.32-25-generic

```

i liked this script (:
windows 7 looks alive, doesn't it?

---

### Post by oldfred on 2010-11-12
Your sda1 looks like a vendor recovery partition. Your sda2 is the win7 (hidden 100MB) boot/recovery partition and sda3 is your main system partition.

But the main system partition always shows this:

/Windows/System32/winload.exe

Or if booting from the same partition it has the above file and the /BCD and /bootmgr files.

Can you browse your sda3 partition and see if you have the /windows/System32 folder and winload.exe in it?

---

### Post by redmorning on 2010-11-13
here is what i have under sda2(SYSTEM RESERVED-windows boot) and sda3(Windows-main partition)

```
piratejackus@ganj:/media$ tree .
.
|-- gecici
|-- SYSTEM RESERVED
|   |-- Boot
|   |   |-- BCD
|   |   |-- BCD.Backup.0001
|   |   |-- BCD.LOG
|   |   |-- BCD.LOG1
|   |   |-- BCD.LOG2
|   |   |-- BOOTSTAT.DAT
|   |   |-- cs-CZ
|   |   |   `-- bootmgr.exe.mui
|   |   |-- da-DK
|   |   |   `-- bootmgr.exe.mui
|   |   |-- de-DE
|   |   |   `-- bootmgr.exe.mui
|   |   |-- el-GR
|   |   |   `-- bootmgr.exe.mui
|   |   |-- en-US
|   |   |   |-- bootmgr.exe.mui
|   |   |   `-- memtest.exe.mui
|   |   |-- es-ES
|   |   |   `-- bootmgr.exe.mui
|   |   |-- fi-FI
|   |   |   `-- bootmgr.exe.mui
|   |   |-- Fonts
|   |   |   |-- chs_boot.ttf
|   |   |   |-- cht_boot.ttf
|   |   |   |-- jpn_boot.ttf
|   |   |   |-- kor_boot.ttf
|   |   |   `-- wgl4_boot.ttf
|   |   |-- fr-FR
|   |   |   `-- bootmgr.exe.mui
|   |   |-- hu-HU
|   |   |   `-- bootmgr.exe.mui
|   |   |-- it-IT
|   |   |   `-- bootmgr.exe.mui
|   |   |-- ja-JP
|   |   |   `-- bootmgr.exe.mui
|   |   |-- ko-KR
|   |   |   `-- bootmgr.exe.mui
|   |   |-- memtest.exe
|   |   |-- nb-NO
|   |   |   `-- bootmgr.exe.mui
|   |   |-- nl-NL
|   |   |   `-- bootmgr.exe.mui
|   |   |-- pl-PL
|   |   |   `-- bootmgr.exe.mui
|   |   |-- pt-BR
|   |   |   `-- bootmgr.exe.mui
|   |   |-- pt-PT
|   |   |   `-- bootmgr.exe.mui
|   |   |-- ru-RU
|   |   |   `-- bootmgr.exe.mui
|   |   |-- sv-SE
|   |   |   `-- bootmgr.exe.mui
|   |   |-- tr-TR
|   |   |   |-- bootmgr.exe.mui
|   |   |   `-- memtest.exe.mui
|   |   |-- zh-CN
|   |   |   `-- bootmgr.exe.mui
|   |   |-- zh-HK
|   |   |   `-- bootmgr.exe.mui
|   |   `-- zh-TW
|   |       `-- bootmgr.exe.mui
|   |-- bootmgr
|   `-- System Volume Information
|       |-- Chkdsk
|       |   `-- Chkdsk20101029225750.log
|       `-- tracking.log
`-- Windows
    `-- System Volume Information
        `-- Chkdsk
            |-- Chkdsk20101029084502.log
            |-- Chkdsk20101029100444.log
            |-- Chkdsk20101029123140.log
            `-- Chkdsk20101030001734.log

32 directories, 44 files

```

Unfortunately , don't have winload.exe, i'm still keeping my hope. But another bad news is in the nautilus i see that almost all the windows partition is empty:
media: /media/Windows
freespace: 292.6 GB
Does this mean...
I didn't format this partitions, just run chkdsk and ntfsfix commands, nothing more. So i can't believe that i lost all of it. Is it possible?

---

### Post by oldfred on 2010-11-13
It is not looking good. Do the chkdsk logs have lots of errors. Then you may be having Hard Drive issues. In Ubuntu's Disk Utility look at drive.

You can download command line tools to check drive status from synaptic, but I do not really know how to use them.
smartmontools - lists harddrive detail info
smartctl and smartd

The tools to recover partitions or files are testdisk and photorec. Photorec is for most file types not just photos. But it recovers just the data and recovers the parts of file that you had deleted as part of an update, so you get lots of files some more useful than others.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by redmorning on 2010-11-13
Hi oldfred,

In chkdsk logs, there isn't any errors.
Now i'm recovering my files with photorec but i am not able to recover all the partition (more than 300 gb) because i don't have an external disk to store recovered files. Now ,i'm trying and i already found some of my files. It looks like i will spend hours to recover! recovered files. 
I see that this is the only solution. 
Thank you for all your help, i would like to solve this issue in a cleaner way. 
Anyway. I will keep this thread open till i format my windows, maybe another solution comes up.

---

### Post by oldfred on 2010-11-13
If you are extracting with photorec you may want to sort on extension, possibly rename using internal data.

[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by redmorning on 2010-11-13
Useful links,
Thank you oldfred.

---

### Post by redmorning on 2011-01-08
Hi to this threads readers,

if you came till here, i think i have to tell the end of the story;
i couldn't save my windows and recovered my data with the excellent tool *photorec*, described very well
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/...rdeletedfiles/]("http://www.psychocats.net/ubuntucat/...rdeletedfiles/")
After that with another very useful post to rename recovered but bad-named files.
[http://www.linux.com/archive/feed/56588]("http://www.linux.com/archive/feed/56588")

I don't remember exact size and number of my data(photo,document,music,film...) but i think, in recovering photos and musics photorec is just a great tool, just the films/videos, i am not satisfied very much. Anyway, it is free and reliable.

For all of your help, thank you very much ***oldfred***

---

