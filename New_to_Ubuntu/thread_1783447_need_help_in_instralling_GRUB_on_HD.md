---
title: "need help in instralling GRUB on HD"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-15
Hi,
I tried earlier in the day to clone a 165 Gig HD to a 35 Gig HD ( after gparting the 165 HD to about 33 Gigs )
Anyway, it didn't work, the smaller HD was still to large to take the clone for some reason.
 Now the 35 HD will not boot. I get a black screen upon trying to boot it ( looks like the old MS DOS command prompt screen ) that says this :

Error: Unknown Filesystem
Grub rescue >

Does anybody know how to reinstall the GRUB? ( assumming the whole HD isn't wiped out )

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> Hi,
I tried earlier in the day to clone a 165 Gig HD to a 35 Gig HD ( after gparting the 165 HD to about 33 Gigs )
Anyway, it didn't work, the smaller HD was still to large to take the clone for some reason.
 Now the 35 HD will not boot. I get a black screen upon trying to boot it ( looks like the old MS DOS command prompt screen ) that says this :

Error: Unknown Filesystem
Grub rescue >

Does anybody know how to reinstall the GRUB? ( assumming the whole HD isn't wiped out )Hi, you will need to boot from the live cd and click try, follow these instructions for reinstalling grub.[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by s1baker on 2011-06-15
this link is to confusing for me as I am somewhat of a beginner.
I don't know where to begin after reading this link

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> this link is to confusing for me as I am somewhat of a beginner.
I don't know where to begin after reading this linkHi, this guide has pictures see if you can understand it better.
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html) 
Also if you are not sure where you should place your grub run this script and  post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read. This has to be done from the livecd, once it is booted choose try ubuntu.

---

### Post by YesWeCan on 2011-06-15
Grub still thinks it is on the original disk and cannot find its files inside the new /boot/grub directory.

There is another way to do this from the rescue prompt. Grub just needs some help to locate the /boot/grub on your disk.

First, you should use 'ls' to list the partitions that it can see
[COLOR="DarkGreen"]rescue> ls[/COLOR]

Assuming your disk is /dev/sda, you should get something like (hd0,1) (hd0,2) and so on. You have to pick the one that contains /boot/grub. I'll call it (hd0,n). In Grub-speak hd0,N is sdaN, so hd0,2 will be sda2.

Then:
[COLOR="DarkGreen"]rescue> set prefix=(hd0,n)/boot/grub
rescue> insmod (hd0,n)/boot/grub/linux.mod
rescue> set root=(hd0,n)
rescue> linux /vmlinuz root=/dev/sda ro
rescue> initrd /initrd.img
rescue> boot[/COLOR]

Once Ubuntu has booted, you need to reinstall grub.
[COLOR="DarkGreen"]sudo grub-install /dev/sda[/COLOR]

---

### Post by s1baker on 2011-06-15
the Linux HD is in a box next to this one ( I have the ISO CD running on it )
 I can't run anything on it except what I type into the terminal 
running the CD

This box is an old Windows 98 install that I am using to acess this forum

---

### Post by s1baker on 2011-06-15
when I type ls at the grub rescue prompt I get:

(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)

---

### Post by YesWeCan on 2011-06-15
Well, it is either 1 or 2. So try 1 first
(hd0,1)
If that doesn't work, try (hd0,2)

---

### Post by s1baker on 2011-06-15
I tried both 1 and 2 and when I ran insmod (hd0,n)/boot/grub/linux.mod after each, ( n being first 1 then 2 )
I get:

error: unknown filesystem

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> I tried both 1 and 2 and when I ran insmod (hd0,n)/boot/grub/linux.mod after each, ( n being first 1 then 2 )
I get:

error: unknown filesystemHi, run the boot script in post #4 and post it here so we can look, also run a disk check on your drive while you are booted from the livecd or usb stick. You can use disk utility.

---

### Post by sandyd on 2011-06-15
> **s1baker said:**
> I tried both 1 and 2 and when I ran insmod (hd0,n)/boot/grub/linux.mod after each, ( n being first 1 then 2 )
I get:

error: unknown filesystem
WAIT!!
You cloned the partitions using 
```
dd
```
right??

If you did, you need to put the original hard disk back to where it was before. DD writes byte-to-byte copying, so you _must_ copy the entire partition for anything to work. Since ou haven't the partition cannot be read by anything.

Otherwise, ignore the slashes and read on...
[s]Both partitions might be corrupted.
boot to a livecd, and post output of
```

wget http://voxel.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.60/boot_info_script060.zip

unzip boot_info_script060.zip
bash ./boot_info_script.sh

```[/s]

---

### Post by YesWeCan on 2011-06-15
Hmm. I don't know why it could not find its files. You could try using the full name (hd0,msdos1) but I'm not sure that matters.

Another way:
Are you able to connect up the 165GB drive as well as the 35GB drive?

If so, you should be able to boot the new Ubuntu using the original Grub.
Boot the 135GB Ubuntu and run sudo update-grub. Reboot off the 135GB drive and you should get a Grub menu that lists both the old and new Ubuntus. Select the new one and hopefully it will boot.

Once the new one has booted, you need to reinstall Grub. First you need to check the name of the new disk. It will be either sda or sdb. If you run sudo fdisk -l it will show you the names and contents and you can identify it by size.
Suppose it is sda, run sudo grub-install /dev/sda


If that fails I am out of original ideas. wildmanne39's suggestions should get you running.

---

### Post by YesWeCan on 2011-06-15
> **sandyd said:**
> Both partitions might be corrupted.
I suspect you are right. Grub should be able to boot from the rescue prompt.

---

### Post by s1baker on 2011-06-15
here is the results from the script
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    70,017,023    70,014,976  83 Linux
/dev/sda2         308,305,920   312,580,095     4,274,176  82 Linux swap / Solaris

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1977 MB, 1977614336 bytes
62 heads, 61 sectors/track, 1021 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 135     3,862,527     3,862,393   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sdc1        1138-9BAA                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/1138-9BAA         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2



========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

```

---

### Post by s1baker on 2011-06-15
also, I used clonezilla to atempt to clone from the 165HD to the smaller HD, but it said that it couldn't .

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> also, I used clonezilla to atempt to clone from the 165HD to the smaller HD, but it said that it couldn't .
Hi, it looks like you do to reinstall ubuntu,you have missing file system, no kernels installed, no ftab, I would also check the disk for errors first.

---

### Post by s1baker on 2011-06-15
If I reinstall off of my ISO, I guess I will lose all my data, correct?
Also, what command do I use to check for errors?

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> If I reinstall off of my ISO, I guess I will lose all my data, correct?
Also, what command do I use to check for errors?Hi, you use disk utility and it can check for errors, use it from the livecd, and you can use the livecd to recover your files if you can see them but since it does not recognize the files system I do not think that is possible.  I asked some one to take look also, so if you want to wait for someone else to read the boot information that is ok.

---

### Post by s1baker on 2011-06-15
yes, I will check for errors here within the next hour but I am going to wait until tommorrow to begin re-installing.
Thanks for your time and  patience, this is the best forum in the World for getting help.

---

### Post by wildmanne39 on 2011-06-15
> **s1baker said:**
> yes, I will check for errors here within the next hour but I am going to wait until tommorrow to begin re-installing.
Thanks for your time and  patience, this is the best forum in the World for getting help.
Hi, your welcome.

---

### Post by oldfred on 2011-06-15
It cannot correctly read partition table.

```
Drive: sda ____________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total [COLOR=Red]78165360[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    70,017,023    70,014,976  83 Linux
/dev/sda2         [COLOR=Red]308,305,920   312,580,095[/COLOR]     4,274,176  82 Linux swap / Solaris

[COLOR=Red]/dev/sda2 ends after the last sector of /dev/sda[/COLOR]

```

Your entire swap is beyond the end of the drive. I would just delete swap as you then may be able to boot or at least reinstall grub2. Then manually recreate swap and edit fstab with new UUID.  

If you have old & new drives, but sure not to have both plugged in at the same time as they may have same UUID.

Script could not mount partitions on sda due to partition table error so we cannot see if there are other things missing or other issues.

---

### Post by YesWeCan on 2011-06-16
Good catch, oldfred.
It is almost as if the root partition on the original 165GB drive was correctly reduced in size but the swap partition was left unmoved. Hence the huge gap between them. When Clonezilla was asked to clone to the 35GB it could make the root partition but could not make the swap partition. It copied the partition table, tho. However, the bootinfoscript shows no contents in the root partition and this is consistent with Grub not being able to find /boot/grub.

It seems to me that the cloning failed and needs to be redone, this time with the swap partition removed from the 165GB drive or moved to the end of the (shrunk) root partition.

---

### Post by s1baker on 2011-06-16
ok, I did as yesWeCan and oldfred said and I re-gparted the 165 HD
so that all of the partition and the swap partition was compacted to the left side of the gparted screen. In my ignorance, the first time I did not resize/move the swap partition, but left it at the end, or right side of the gparted screen. I re-ran clonezilla and now the 35 HD works, seems to be cloned correctly. 

The only problem I am having now is running VirtualBox that has windows XP in it in the 165 Gig HD. If I run it when I first boot up Ubuntu, it works just fine, but if I do something in Ubuntu, then run VB and try to run windows, sometimes it won't start up, and then when it does the mouse is real sticky. I know it had something to do with me first shrinking the partition of the 165 HD down to about 35 gigs, then later I re-gparted it back up to full size. Must be the settings somewhere in VB.

---

### Post by wildmanne39 on 2011-06-16
> **s1baker said:**
> ok, I did as yesWeCan and oldfred said and I re-gparted the 165 HD
so that all of the partition and the swap partition was compacted to the left side of the gparted screen. In my ignorance, the first time I did not resize/move the swap partition, but left it at the end, or right side of the gparted screen. I re-ran clonezilla and now the 35 HD works, seems to be cloned correctly. 

The only problem I am having now is running VirtualBox that has windows XP in it in the 165 Gig HD. If I run it when I first boot up Ubuntu, it works just fine, but if I do something in Ubuntu, then run VB and try to run windows, sometimes it won't start up, and then when it does the mouse is real sticky. I know it had something to do with me first shrinking the partition of the 165 HD down to about 35 gigs, then later I re-gparted it back up to full size. Must be the settings somewhere in VB.Hi, I use virtualbox myself and windows gets very touchy if any settings are changed after it is installed.

Thank you Oldfred for taking a look at this problem, I really appreciate the help.

---

### Post by s1baker on 2011-06-16
I hope I don't have to re-install Windows. I don't think it can be re-installed as to where one can keep their data and programs without re-installing them also.

I upgraded VB one time, and I had to delete the current version of VB first and then install the new version of VB, but the XP machine did not have to be re-installed. Hope that's all it is.

---

### Post by YesWeCan on 2011-06-17
> **s1baker said:**
> ok, I did as yesWeCan and oldfred said and I re-gparted the 165 HD
so that all of the partition and the swap partition was compacted to the left side of the gparted screen. In my ignorance, the first time I did not resize/move the swap partition, but left it at the end, or right side of the gparted screen. I re-ran clonezilla and now the 35 HD works, seems to be cloned correctly.
Good :)

> The only problem I am having now is running VirtualBox that has windows XP in it in the 165 Gig HD. If I run it when I first boot up Ubuntu, it works just fine, but if I do something in Ubuntu, then run VB and try to run windows, sometimes it won't start up, and then when it does the mouse is real sticky. I know it had something to do with me first shrinking the partition of the 165 HD down to about 35 gigs, then later I re-gparted it back up to full size. Must be the settings somewhere in VB.
Hard to say. Any error messages?
If you upgraded VB you will need to re-install Guest Additions in the XP guest. You may need to install the latest extension pack too.

---

### Post by s1baker on 2011-06-17
I guess I spoke to soon about XP running on the smaller 35 Gig cloned machine. Actually, i can't get XP to run correctly through VirtualBox on the 35 G machine or the bigger 165 G machine. The mouse is to sticky to use.
I have noticed though that at boot up, on the splash screen just before the log on screen comes on, I am now seeing a message that reads "The UUID for disk drive ed76abc123....( long list of
letters and numbers here ) is not ready yet or not present"
I notice this on either HD at first boot up. I have never seen this before. oldfred said something about changing the fstab in but I have no idea what that is or what to do.

here is a copy of the fstab in the etc directory for what it's worth:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ed78184f-02ad-478c-b77d-04a6f3ce66a4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
#none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0
```

---

### Post by YesWeCan on 2011-06-17
Sounds like there is a UUID problem. Would you post the output of 'sudo blkid'?

You should not have both drives connected at the same time because their partitions have the same UUIDs. This may be part of the problem.

Another issue is that both fstab files refer to the root partition as /dev/sda1. When there is only one disk connected it will be called sda. But when both are connected the one you boot might be sdb (depending on how you bios likes to do things), in which case the root may be mounted on the root partition of the clone instead of the booted disk. So the fstab should be edited and the /dev/sda1 replaced with the UUID of that partition (like the swap entry uses). There is still the issue that when both drives are connected there will be two root partitions with the same UUID and this may be causing VB some confusion.

Try disconnecting one and see whether VB works ok. If it does then that is the problem.

---

### Post by s1baker on 2011-06-17
here is the output:
This is with only one HD hooked up, 1the larger 165G one.

```
/dev/sda1: UUID="e8d93133-8081-46d0-a959-4149457d3275" TYPE="ext4" 
/dev/sda2: UUID="3eba89ed-01f6-4f02-b66a-5d9637252a9d" TYPE="swap"
```

---

### Post by s1baker on 2011-06-17
also, I just shut down and then turned the computer back on, and at the splash screen where it gives me the message "The UUID for this drive "ed7818...something" doesn't seem to match what is shown when I do a sudo blkid.
The message only is on for a split second but the first 4 or so letters are "ed7818"

---

### Post by s1baker on 2011-06-17
and with only one drive connected, XP will still not work

---

### Post by wildmanne39 on 2011-06-17
> **s1baker said:**
> and with only one drive connected, XP will still not work
Hi, are you using the new 4.08 virtualbox it had a bug in it and it was causing window vm's to have the exact problem you describe. I had to reinstall 4.06. Also it could just be because of the cloning, virtulbox has its on application for moving vm's from one drive to another and a lot of the times it fails if you do not use there application, but if that was the case I doubt you could have booted xp even once.

---

### Post by s1baker on 2011-06-17
I have 4.08, which was what was on Linux before the clone.

Also I notice that my fstab has "UUID=ed78184f-02ad-478c-b77d-04a6f3ce66a4" in the etc/fstab file, which is the number given
on the splash screen at boot up that says "the UUID for disk drive ed7818.... is not ready yet or not present"

and doing a sudo blkid gives me this:

```
/dev/sda1: UUID="e8d93133-8081-46d0-a959-4149457d3275" TYPE="ext4" 
/dev/sda2: UUID="3eba89ed-01f6-4f02-b66a-5d9637252a9d" TYPE="swap" 
```

which don't seem to match.
This is with only one HD hooked up ( the larger 165 G one )

---

### Post by YesWeCan on 2011-06-17
Interesting. You should edit fstab and make the UUID for swap the same as in blkid. Make a backup of fstab first, like fstab-bak
While you are at it, change the / entry to use the UUID for /dev/sda1

---

### Post by s1baker on 2011-06-17
here is my full fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ed78184f-02ad-478c-b77d-04a6f3ce66a4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
#none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0
```

so how should I fix the UUID's for the sda1 partition and the swap partition?

when I run gparted I show a sda1 for the main or root partition and a sda2 partition for the swap

---

### Post by YesWeCan on 2011-06-17
[FONT=Courier New]```
# <file system>                                   <mount point>   <type>   <options>                <dump>  <pass>

proc                                               /proc           proc    nodev,noexec,nosuid         0       0

UUID=e8d93133-8081-46d0-a959-4149457d3275          /               ext4    errors=remount-ro           0       1

# swap was on /dev/sda5 during installation
UUID=3eba89ed-01f6-4f02-b66a-5d9637252a9d          none            swap    sw                          0       0

/dev/fd0                                           /media/floppy0  auto    rw,user,noauto,exec,utf8    0       0

#none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
#none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0[/FONT]
```

---

### Post by YesWeCan on 2011-06-17
The problems with VB may be something else. I run 4.0.8 PUEL and I have an XP guest. I haven't had any problems with it myself. Did these problems coincide with upgrading VB?

You could try removing VB and reinstalling it - this won't destroy your machines.
To remove it use System/Admin/Synaptic and search for "virtualbox". Tick the entry for remove (not complete remove) and apply. Then go back to the VB website and download it again.

---

### Post by s1baker on 2011-06-17
Man, your the greatest! I plugged in the fstab file and rebooted and everything ran and then when I went into VB to run XP, XP ran smooth as silk. I shut VB down and fired it back up and seemed to run again ok. 
I will try to later hook up my smaller 35G HD and check the blkid and fstab on that one and do similar to the file you fixed for me for that HD.
I won't called this solved as of just yet, I want to "road test" my XP's on both machines, but I think this might do it.

---

### Post by wildmanne39 on 2011-06-17
Hi, they may have fixed that problem with 4.08 it was caused by a character in the guest additions script that did not belong there, a lot of people posted on there forum about it so it might have been fixed.  I have run windows 7 and xp in virtualbox and xp gave me a lot of problems with the blue screen I finally just got rid of it, it worked great until I would update it with the latest updates then it would become sluggish and unresponsive, but it sounds like you had it working good until the cloning.

---

### Post by YesWeCan on 2011-06-17
Good stuff. :)
Did you delete and make a new swap while you were shrinking in Gparted? When you make/format a new partition it is given a new UUID and you then need to update fstab.
BTW how much RAM have you got? I am wondering whether when VB is running XP your system is running a little short of RAM and has to use SWAP space. Because the SWAP was not mounted the performance took a big hit. I am not sure about this theory, but it fits some of the symptoms.

---

### Post by s1baker on 2011-06-17
yes, XP was running ok for me using VB before I cloned the HD's,
but I never have upgraded XP while I have had it on Ubuntu/VB.
I have upgrades turned off. I have one CAD package that I need for work, and that is the only reason I need VB, so that I can run XP while using Ubuntu. ( I'm trying to get away from MicroSoft ). The program works fine with XP version that I have and that is all I want.

Someone has a Linux version that just came out on the program that I use, and when I can rake up the cash, I am going to buy it, and after that, 'poof', XP will be gone ( probably still keep it though, just to fool around on but won't need it )

---

### Post by s1baker on 2011-06-17
> Did you delete and make a new swap while you were shrinking in Gparted? When you make/format a new partition it is given a new UUID and you then need to update fstab.
BTW how much RAM have you got? I am wondering whether when VB is running XP your system is running a little short of RAM and has to use SWAP space. Because the SWAP was not mounted the performance took a big hit. I am not sure about this theory, but it fits some of the symptoms.
__________________

when I shrank my partitions on the 165G HD at the start of the clone, I shrank the swap to like 1 or 2 megs, so that I could be sure and have a smaller clone space than the space of the 35G HD. Then after cloning, I gparted the 35G HD to full size of the 35G HD and I increased the swap space to 1/2 Gig.
When I re-gparted the large 165G HD I increased partition to full size and I changed the swap size to 4 Gigs ( originally it was 2 Gigs ), so I did change the swap sizes on both HD's.

In the VB set-up, I believe both of them have 212 megs of ram, I believe the minimum that VB recommends is something like 198 ( if I remember correctly ).

---

### Post by s1baker on 2011-06-17
also, in terminal "free" gives me this:

             total       used       free     shared    buffers     cached
Mem:        507364     497416       9948          0       6432      47312
-/+ buffers/cache:     443672      63692
Swap:      4122620     214400    3908220

---

### Post by YesWeCan on 2011-06-17
Your system has 512MB of RAM. This is pretty small for doing VB as Ubuntu will want 512 on its own, and so does XP. I'm impressed you are getting away with this! SWAP space is being used heavily. So my theory was right: not having SWAP mounted crippled your system when running XP in VB. Note that SWAP is a very poor RAM substitute in terms of performance, so your system is probably running much slower than it would if you, say, doubled your RAM.

---

### Post by wildmanne39 on 2011-06-17
> **s1baker said:**
> when I shrank my partitions on the 165G HD at the start of the clone, I shrank the swap to like 1 or 2 megs, so that I could be sure and have a smaller clone space than the space of the 35G HD. Then after cloning, I gparted the 35G HD to full size of the 35G HD and I increased the swap space to 1/2 Gig.
When I re-gparted the large 165G HD I increased partition to full size and I changed the swap size to 4 Gigs ( originally it was 2 Gigs ), so I did change the swap sizes on both HD's.

In the VB set-up, I believe both of them have 212 megs of ram, I believe the minimum that VB recommends is something like 198 ( if I remember correctly ).
Hi, you might want to open gparted and make sure the swap is turned on.

---

### Post by YesWeCan on 2011-06-17
> **wildmanne39 said:**
> Hi, you might want to open gparted and make sure the swap is turned on.
Good thought. The "free -m" command will show how many megabytes of swap is being used. It shows 214400 kilobytes in the prior post so it is definitely enabled.

---

### Post by s1baker on 2011-06-17
> 
Note that SWAP is a very poor RAM substitute in terms of performance, so your system is probably running much slower than it would if you, say, doubled your RAM
I am going to look into that Monday. This is an old box, about 5 years old and has served me well. Have side panel off now ( because of plugging in and unplugging HD's so much ) and it appears there are two memory slots in it, one colored blue and the other colored white. The blue slot is filled with a memory chip, the white slot is empty. I will call the manufacturer Monday and see if the memory can be increased.

---

### Post by wildmanne39 on 2011-06-17
> **YesWeCan said:**
> Good thought. The "free -m" command will show how many megabytes of swap is being used. It shows 214400 kilobytes in the prior post so it is definitely enabled.
Hi YesWeCan, sorry I would not have posted my last post if I had seen post #44 first, we must have been posting at the same time.

---

### Post by YesWeCan on 2011-06-18
> **wildmanne39 said:**
> Hi YesWeCan, sorry I would not have posted my last post if I had seen post #44 first, we must have been posting at the same time.
No problem at all. I think it is better to mention things and find they are not relevant than not to mention them and find out later they were important. Carry on. :)

---

