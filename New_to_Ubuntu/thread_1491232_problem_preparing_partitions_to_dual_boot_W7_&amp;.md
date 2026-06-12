---
title: "problem preparing partitions to dual boot W7 &amp; U 10-04"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Phillip Spencer on 2010-05-23
I am trying to install Ubuntu 10-04 on a virtually new HP Pavilion DM1 laptop to dual boot with factory-installed  Windows 7 OS (latter required for remote access to work environment - not my choice of OS!).  I have resized the C: drive from within Windows and have sufficient free space to install 10-04.  When I go through the 10-04 installation process, I can get as far as "Prepare partitions" - step 5 of 8 - when I hit what I suspect is a quite basic problem but I can't find my way around it.

The free space I want to use shows as: /dev/sda4 type ntfs (sda1 & sda2 being HP recovery Windows drives and sda3 the main windows C: drive). Highlighting this and just trying to go forward brings up the message "No root file system is defined. Correct from partitioning menu."  

Going in to change the partition brings up a pop-up that shows "use as: 'do not use the partition' " with a drop down of multiple options such as 'Ext4 journaling system'; 'ntfs' and 'swap area'.  I am unclear if I now have to create both a swap area and Ext4 partition or if the all the allocation of space happens automatically - as prior installations (including a dual boot of XP and U09-10) have not required this level of intervention in partitioning.

Am I missing something obvious?  Searching the forum for the message did not pull anything relevant so would appreciate any guidance.

Thanks in advance!
Phillip

---

### Post by mbzn on 2010-05-23
Hi there.

You should delete the partition (sda4) then create primary partition for '/' which will be the root file system. Then create a logical drive with swap area and /home partitions.

Hope this helps

Edit: I think i might have understood wrong

You can change the size of the partition to the size you want then the rest of the free space can be used to create another...

---

### Post by Phillip Spencer on 2010-05-23
Hi mbzn, Thanks for the quick response.  I confess I am still struggling with this though.

> **mbzn said:**
> 
You should delete the partition (sda4) then create primary partition for '/' which will be the root file system. Then create a logical drive with swap area and /home partitions.

Deleting the partition sda4 gave free space which I used to create a new primary partition - location: beginning; use as: Ext4 journaling; mount point: /.  

This gives me: /dev/sda4; typeext4; mount point /

However,  I cannot seem to go in and edit this to create logical drives for swap etc. and moving forward gives a warning prompt about not having swap.

I then noticed you have edited your post:
> **mbzn said:**
> 
Edit: I think i might have understood wrong

You can change the size of the partition to the size you want then the rest of the free space can be used to create another...

Reverting to the sda4; type ntfs does not allow me to edit the size of this, only change the format.

Deleting it and trying to create a smaller primary just leaves the remaining space "unusable" so I assume I have to create the full size primary then find a way in to create logical drives within that but the process does not appear intuitive (or at least not to me!)

Am I close or totally off-beam here?

---

### Post by mbzn on 2010-05-23
Maybe it'll be easier to delete sda4 then create an extended partition for / and for swap area. The thing is you can only have 4 primary partitions.

After deleting sda4 >>>

Let's see, you have sda1-3 as your windows partitions and some free space.
(for now lets say free space = 10Gib)
Now create new part. in the free space, (8Gib) (Primary) (mount to /)

Now you have you sda1-3 win and sda4 8Gib(ext4) mounted as /(root)
and 2Gib free space
Create new part. in free space (You cant make any more primary so it'll be extended) then by 'format to' just set it to Swap area

---

### Post by sandyd on 2010-05-23
delete SDA4, then choose "use largest block of free space" when partitoning.

---

### Post by ranch hand on 2010-05-23
> **carlee said:**
> delete SDA4, then choose "use largest block of free space" when partitoning.
This is probably the easiest way to do this.

What would be even better is to boot to your Live CD and run, in terminal;
```

sudo fdisk -l

```
That is a lower case L there at the end.  And post the results here so we can see what the deal is with your setup.

---

### Post by Phillip Spencer on 2010-05-23
Thanks for the advice around deleting sda4.  Noting the problem around only being allowed four primary partitions I went back into Windows because one partition was for recovery and I had already created my Windows 7 recovery disks (a wise precaution as subsequent events showed).  I deleted the recovery partition as disk creation is a one-off action on HP laptops.  Re-booting into Windows worked fine after this.

Going back into Ubuntu 10-04 installation, I was then able to delete both sda2 (recovery) and sda4 (space orginally freed up by shrinking Windows C: drive).  I then created the primary partition - Ext4; Mount / - approx 230Gb, leaving about 11Gb free.  I was then able to create a swap area with the remaining 11Gb and could proceed through the rest of the Ubuntu installation process.

The only problem was that wireless did not seem to be working so I thought I would re-boot into Windows and check wireless there...  "reboot" and "shut down" don't work, putting me back to log on screen... so I resort to "poweroff" button and select Windows 7 (which is on /dev/sda3) and get a message from Windows Boot Manager that Windows failed to start so I seem to have screwed up something there.  

Unfortunately, my recovery disks are in France and I am in UK right now (yeah, I should have taken them with me when I went travelling... or done this at home).  Good job I have with me this old laptop (which was to be retired after the installation on the new laptop) otherwise I could not log in and record this.

Am off to sulk in corner and lick wounds.  However, I would thank those who gave advice as this is my own fault for not being more cautious before proceeding with any option.  I guess I should have stuck to Windows rather than trying to go to a dual boot.

Cheers
Phillip

---

### Post by oldfred on 2010-05-23
You can get a repair CD:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.

---

### Post by ranch hand on 2010-05-23
Dual booting is not that hard but it does need a little care.

I really wish you had waited and sent the info I asked for.  I was concerned about the 4 primary limit too.

A better solution would have been to create one Extended partition on your unused space.  That is a type of primary partition that allows you to create an unlimited number of Logical partitions with in it.

That way you could have 10.04 on a / (root) partition and a /home partition and a /swap partition.  An advantage to that set up is that if you screw your Ubuntu you can reinstall (manual option) formating only the / partition leaving your /home, with your data and config files intact (back up is still a good idea).

Now we need to get your MS straightened out.  If you would be so kind as to use this script, from your Live CD or your Ubuntu install and then post the whole results text here we can see what the problem really is so that you do not make matters worse.  The results test file will show up on your desktop.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you are able to get online with that box now it would be nice to see this.  You may also want to try, after we see the results text getting the package "testdisk" installed which will probably be able to correct your problem.

This can be fixed.  Don't rush things.  When in doubt stop and ask.  When screwed, remember to breath.

---

### Post by Phillip Spencer on 2010-05-23
Hi ranchhand.  Thanks for your advice on Extended partitions.  Unfortunately, I only read your previous post after I had committed to my previous course of action.  I will look into this once I am back to a stable PC.

In the meantime, your suggested:
> **ranch hand said:**
> 

Now we need to get your MS straightened out.  If you would be so kind as to use this script, from your Live CD or your Ubuntu install and then post the whole results text here we can see what the problem really is so that you do not make matters worse.  The results test file will show up on your desktop.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

If you are able to get online with that box now it would be nice to see this. 

The Results.txt document contents are:
```
                
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *    505,638,912   954,857,471   449,218,560  83 Linux
/dev/sda3             409,600   505,638,911   505,229,312  42 SFS
/dev/sda4         954,859,518   976,771,071    21,911,554   5 Extended
/dev/sda5         954,859,520   976,771,071    21,911,552  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        1a8ecfd3-5ad7-4078-9ae9-393148cdbff1   ext4                                     
/dev/sda3        7EBA92DFBA92936F                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2b59105d-3a86-4415-9576-8b9cfd40a0ee   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1a8ecfd3-5ad7-4078-9ae9-393148cdbff1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1a8ecfd3-5ad7-4078-9ae9-393148cdbff1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1a8ecfd3-5ad7-4078-9ae9-393148cdbff1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7eba92dfba92936f
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2b59105d-3a86-4415-9576-8b9cfd40a0ee none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 261.1GB: boot/grub/core.img
 297.6GB: boot/grub/grub.cfg
 261.1GB: boot/initrd.img-2.6.32-21-generic
 261.1GB: boot/vmlinuz-2.6.32-21-generic
 261.1GB: initrd.img
 261.1GB: vmlinuz

```
Looking at the partition descriptions in Windows (prior to my screw-up) there was a small first partition that seemed to be HP tools, the second (subsequently removed) was the recovery partition and third the normal Windows 7 partition.

If the Boot Info Script gives any useful insights knowing this would be appreciated.

> **ranch hand said:**
> 
You may also want to try, after we see the results text getting the package "testdisk" installed which will probably be able to correct your problem.
If "testdisk" is not a part of the standard Ubuntu installation, as I do not have a working internet connection on the laptop I will have to obtain it via a download on my old PC and move it across on a stick if that is possible.

> **ranch hand said:**
> This can be fixed.  Don't rush things.  When in doubt stop and ask.  When screwed, remember to breath.
Thanks... I am still breathing, just annoyed with myself as I had not realised the impact of what seemed a very straight-forward action (deleting an apparently un-needed partition) would be.  

Appreciate the time you have put into this for the reply.

It is now past midnight so I am going to  pack up for tonight and go back fresh tomorrow evening.
Cheers
Phillip

---

### Post by ranch hand on 2010-05-23
Well, disclaimer first.  I do not allow MS products in the house.  Therefore there are a lot of things about MS that I do not know.

We do have the tools now, though to know what to do, if we can just understand it.

I am having a little problem with the layout of the drive before you went to work on it.  What I have seen on preinstalled computers is the MS boot sector, then the OS and then a recovery partition if the buggers are too cheap to supply an install disk (which should be mandatory - you paid for the OS, you should have a disk).

I have never seen W7 though so maybe it is stranger than their other OS'.

The generated menu entry for W7 does not look right at all.

I wonder if it has to do with;
```

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

```
Is what you installed some sort of Wubi install?  Or did you try one first?

I think that "wubuilder" business has to do with wubi, another thing I have no knowledge of at all.  I am pretty sure that, assuming an independent Ubuntu installation, that stuff has no place in the W7 boot sector.

When you are in Ubuntu can you get to your files in W7?  Do they look intact?

---

### Post by Miljet on 2010-05-23
I have never used Win 7 so know very little about it. It seems that I read somewhere that Win 7 requires two partitions, but don't remember where I read that and have no idea how true it is.

If you look closely at the boot info, you will notice that sda2 and sda3 are actually in reverse order on the disk. And the Ubuntu partition has the boot flag set instead of the Win partition. Ubuntu doesn't give a hoot about a boot flag but it is my understanding that Windows does. I don't know how important any of the above really is. Just thought I would point it out for consideration.

---

### Post by drdos2006 on 2010-05-23
The Windows 7 installation takes over control of the HDD partitions when installing. 
I found it best to install Windows 7 first and then install Ubuntu allowing Ubuntu to set up the boot menu. 
Win7 will also want to set the boot flag but that is OK because Ubuntu will boot up. 
My 320G HDD is partitioned as 80G for Ubuntu, 60 G for Win7, 100+ G for data and 12 G for swap. 
Ubuntu installation needs swap file allocation. 
The partitions under ubuntu are /dev/sda as ext4, /dev/sdb as ntfs for Win7, /dev/sdc as ntfs so both OS can read, and dev/sdd as swap. Win7 allocates its own swap area in the partition during installation.

regards

---

### Post by ranch hand on 2010-05-23
> **drdos2006 said:**
> The Windows 7 installation takes over control of the HDD partitions when installing. 
I found it best to install Windows 7 first and then install Ubuntu allowing Ubuntu to set up the boot menu. 
Win7 will also want to set the boot flag but that is OK because Ubuntu will boot up. 
My 320G HDD is partitioned as 80G for Ubuntu, 60 G for Win7, 100+ G for data and 12 G for swap. 
Ubuntu installation needs swap file allocation. 
The partitions under ubuntu are /dev/sda as ext4, /dev/sdb as ntfs for Win7, /dev/sdc as ntfs so both OS can read, and dev/sdd as swap. Win7 allocates its own swap area in the partition during installation.

regards
I am glad that folks who run W7 are on here now.  The OP has hit the hay for the night.

His box was preinstalled with W7 so it was on there first.  This is why I have a little trouble with W7 being listed as on sda3 in the boot info script (isn't that just handy as a pocket in a shirt).

Ubuntu is supposed to have been installed as a dual boot.  Why then the reference to wubuilder in the boot info on sda3?

---

### Post by drdos2006 on 2010-05-23
It also appears that the boot partition is allocated to Ubuntu. If Windows does not boot then it might be made to boot into Windows with a LiveCD, gparted and setting the Windows partition to boot.

regards

---

### Post by Miljet on 2010-05-23
> The partitions under ubuntu are /dev/sda as ext4, /dev/sdb as ntfs for Win7, /dev/sdc as ntfs so both OS can read, and dev/sdd as swap. Win7 allocates its own swap area in the partition during installation.

If you only have one hard drive as your post suggests, your partitions will all be sda. As in sda1 for Ubuntu, sda2 for Win7, sda3 for data, and sda4 for swap. And Windows doesn't use a swap partition, it uses a swap file inside the Win installation.

---

### Post by Miljet on 2010-05-23
> This is why I have a little trouble with W7 being listed as on sda3 in the boot info script 

That is true but if you look closely at the beginning and ending sectors, you will see that sda3 actually comes before sda2 on the disk. That leads me to believe that somehow the UUIDs of the partitions have been changed.

---

### Post by oldfred on 2010-05-24
If it was a orginal install then it had a windows boot sector on sda2. But it must have been repaired as the files normally in the boot partition /bootmgr /boot/BCD are now in sda3.

The boot flag is on sda2. Linux does not need it, some BIOS have to have it on a primary partition and if the OP is going to reinstall the windows boot loader he must move the boot flag to sda3. Use gparted, right click & manage flags or use Disk Utility. Only one boot flag per drive and only on primary partitions.

---

### Post by ranch hand on 2010-05-24
> **Miljet said:**
> That is true but if you look closely at the beginning and ending sectors, you will see that sda3 actually comes before sda2 on the disk. That leads me to believe that somehow the UUIDs of the partitions have been changed.
Well, I will be hornswaggled.  I missed that altogether.  That does come as a relief in a way.  At least it is now likely that W7 is still on his drive in its entirety.

I hope some one has a clue how to untangle this mess because I surely do not.

What is with a dual boot system with wubuild in the W7 boot info?  This is connected to wubi, I think.

I really do not do windows at all so I just do not know what this crap is.

---

### Post by drdos2006 on 2010-05-24
Hi Miljet
Yes, you are quite correct. The partitions on the hdd are sda1, sda2, sda3 and sda4. I typed without checking. :)
And yes, Win7 allocates its own swap in its own partition during installation, and Ubuntu needs swap allocated depending on the amount RAM installed ( 2 x RAMsize) during installation.

regards

---

### Post by wilee-nilee on 2010-05-24
So I see some nice hypothetical ideas here, but lets make sure that we at the least protect the thread starters setup by not just throwing out information that may be confusing. This is a fix that needs to be seen by one of the regulars that are very good at this sort of stuff. There are about 5 members who are able to weave their way through a mess like this and get things fixed that are on the forums daily.

I'm no questioning anybodies skills or validity here but just trying to point out that the person who is most important here is the OP, not our personal ego's.

First the OP doesn't have a testdisk download as of now if that is a option, nor do they have the recovery disc or install disc to rewrite the bcd boot in W7, or a disc of 10.04 possibly, so at this point lets all just sit back wait for them to come back on line and see where they are at and go from there.

---

### Post by Phillip Spencer on 2010-05-24
Thanks for all the input.  I appreciate the time people have taken to give advice and am heartened by the level of support that has been given to me for what was an ill-considered decision with somewhat adverse consequences!

Before going any further I want to say that I can always re-install the factory-settings version of Windows 7 and start again next weekend as I created the recovery disks before starting down the Ubuntu install route.  I have not migrated any data across to the new laptop so there is nothing critical to be saved and I will feel guilty if anyone spends a lot of time on this.
 
Using wired LAN I now have an up-to-date Ubuntu 10-04 working on the laptop and have downloaded the proprietary drivers needed for wireless and this is now working too. 

> **oldfred said:**
> You can get a repair CD:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.

Thanks for that advice.  I have downloaded the ISO file and burnt it to a CD.

> **ranch hand said:**
> 

I am having a little problem with the layout of the drive before you went to work on it. What I have seen on preinstalled computers is the MS boot sector, then the OS and then a recovery partition if the buggers are too cheap to supply an install disk (which should be mandatory - you paid for the OS, you should have a disk).

Looking at the partition information in Windows 7 Control Panel beforehand there appeared to be (from memory) first, an HP tools partition, then the recovery partition, then the normal Windows C: drive.

> **ranch hand said:**
> 
 
Is what you installed some sort of Wubi install?  Or did you try one first?

I think that "wubuilder" business has to do with wubi, another thing I have no knowledge of at all. I am pretty sure that, assuming an independent Ubuntu installation, that stuff has no place in the W7 boot sector.

Good question.  I had clicked on WUBI when browsing the Ubuntu disk in Windows on first burning the CD but then aborted the install when I realised it would be Unbuntu inside Windows when I wanted the two separate.  As the process was aborted very early on I was surprised that any of this stayed in the system. When I could still boot into Windows I did have a menu choice between Windows and Ubuntu come up even though I had not proceeded with the install.

> **ranch hand said:**
> 
 
When you are in Ubuntu can you get to your files in W7?  Do they look intact?

I have no personal data yet on the PC.  Using Nautilus I can see "259Gb Filesystem" and there are loads of Windows files in there plus other Windows software I downloaded previously.  There is also a "Ubuntu" directory which appears to contain some WUBI and other files.  I was able to use gedit to open text and log files and also to view image files.  I kept well clear of anything sensitive like program files but the directory structure appears intact.

> **oldfred said:**
> If it was a orginal install then it had a windows boot sector on sda2. But it must have been repaired as the files normally in the boot partition /bootmgr /boot/BCD are now in sda3.

This may be the source of my problems.  The data to create recovery disks was in sda2 and in my research before changing the Windows partition I read at [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) the following: 

> Physical Recovery Disks are not always shipped with a new computer. For example, my eMachines box instead provided a utility (eMachines -> eMachines Recovery Management) to create (burn) a pair of Recovery DVDs using data stored on an image in a recovery partition. If your OEM manufacturer gives you a similar option of burning Recovery disks (instead of supplying Recovery CD/DVDs with your computer), make sure you burn these disks prior to reformatting/repartitioning your hard drive. If your hard drive becomes corrupted during the re-partitioning process and you haven't created Recovery Disks, it will be too late. 
Once the Recovery Disks are burned, it is no longer necessary to keep the recovery partition (and Windows can be re-installed without it).Hence my decision to remove sda2 which enabled me to install Ubuntu.

 > **oldfred said:**
> The boot flag is on sda2. Linux does not need it, some BIOS have to have it on a primary partition and if the OP is going to reinstall the windows boot loader he must move the boot flag to sda3. Use gparted, right click & manage flags or use Disk Utility. Only one boot flag per drive and only on primary partitions.

I am not familiar with gparted.  Given what I have written above, is gparted the next step or do I use the Windows 7 repair disk?

As it is nearing 11pm here in UK I am not intending to do anything further this evening, I'm too tired and will, no doubt, make more silly mistakes.  I will be able to look at this again tomorrow (Tuesday) evening.

Thanks again for the advice.
Cheers
Phillip

---

### Post by nanog on 2010-05-24
Bootitng should fix your windows mbr and/or corrupt partition table.

[http://www.softpedia.com/get/System/Boot-Manager-Disk/BootIt-Next-Generation.shtml](http://www.softpedia.com/get/System/Boot-Manager-Disk/BootIt-Next-Generation.shtml)

Its freeware and fixes just about anything I've thrown at it - corrupt mbr, corrupt partition tables, deleted partitions. It handles windows and linux filesystems flawlessly.

The opensource tool testdisk is also very powerful but has a steep learning curve.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by nanog on 2010-05-24
> I want to say that I can always re-install the factory-settings version  of Windows 7

I haven't dual booted in ages (I run win xp and 7 in virtualbox) but when I did I always deleted all factory partitions and resized my ntfs boot partition into one block prior to installing ubuntu. Both a windows 7 recovery disk and bootinng should let you delete, merge, and resize ntfs partitions. (Its always a good idea to use windows tools for windows files systems, IMO).

---

### Post by ranch hand on 2010-05-24
Gparted is located on the Live CD under System>Aministration>Gparted.  It is a better tool than the MS one for general partitioning jobs.  It is not used, usually, to mess with MS partitions as they are set up strangely so it is just safer to use the MS tools.

Partition work is best done from a different drive or a CD so that the drive you are working on is not mounted at the time.  This is just safer.

When you have gparted up just right click on the partition you have the boot flag on and there will be a box to uncheck.  The flag will be gone after you close the popup window.

The MS partition, I think, should have a boot flag.  You do it the same way.  Real tough.

I think you will have to repair your boot in MS as it is not going to boot with that stuff in it.  It is not right.

After that you will have to reinstall grub on the MBR;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You can ignore the file editing portion as that is not part of your problem.  You will run "sudo update-grub".  If, when you reboot to Linux, you do not have the option of booting to MS open the terminal there and run that command again.

That takes care of that more than 95% of the time.

It should work, though, as your grub did generate a menu entry.  It is wrong because the information it got from the faulty MS boot loader was wrong.  Therefore it should work when you correct that problem.

---

### Post by jgoguen on 2010-05-24
Here's hoping we can get you up and running smoothly.  Dual-booting is fairly simple if done right, but as you've seen deleting the wrong partition can have rather disastrous results.  I've actually done exactly what you've tried recently, so here's what I did.  My directions assume you've got a fresh Windows 7 environment, but as long as you can boot into Windows you should be able to skip steps you've already done. If you can't boot into Windows right now, you should restore from the recovery discs you've made before starting this.

First step is to create your partition for Ubuntu.  Click the Start orb and right-click Computer. Choose "Manage", then when Computer Management opens click Disk Management from the left side.  The C: drive appears split into 3 components, resize the largest one (which should be the third one) to give you sufficient free space. The new partition can be any type, including no type, since you're just going to delete the partition later.

Once you have finished shrinking your Windows partition, reboot and boot into your Ubuntu CD. Start the install process and go until you reach the partitioner, then choose to manually partition. You'll see four partitions. /dev/sda1 is your recovery partition, you shouldn't touch that. /dev/sda2 is the Windows boot partition (not swap, not swap & boot, just boot), you definitely **do not** touch that. /dev/sda3 is your Windows partition, you also don't touch that. Finally, /dev/sda4 is the partition you want to delete, unless it already says it's Free Space.

Create a new partition here, make the size be twice the size of your RAM. Note this is in MB, so if you have 2GB RAM use 4096MB here.  You'll see two selections above the size box for Primary or Extended, choose Extended.  Then in the type selection, choose "swap".  Now you'll have some leftover free space, create a new partition here and change the type to ext4. Leave everything else the way it is.

Now, you should be able to apply those changes and just let the installer continue along.  Ubuntu should install smoothly and when you reboot you'll get a GRUB screen.  There'll be two Windows entries.  The one that identifies itself as a Vista loader is your recovery partition, the other one is your Windows 7 setup.

Hopefully this works well for you. If not, let us know what didn't work, what you tried, and most importantly give us the exact error messages if any appear.

---

### Post by Phillip Spencer on 2010-05-29
OK, as the OP, I am back now the weekend is here and I have a bit of time. I am trying to tackle the gparted suggestions quoted below:

> **oldfred said:**
> If it was a orginal install then it had a windows boot sector on sda2. But it must have been repaired as the files normally in the boot partition /bootmgr /boot/BCD are now in sda3.

The boot flag is on sda2. Linux does not need it, some BIOS have to have it on a primary partition and if the OP is going to reinstall the windows boot loader he must move the boot flag to sda3. Use gparted, right click & manage flags or use Disk Utility. Only one boot flag per drive and only on primary partitions.

> **ranch hand said:**
> When you have gparted up just right click on the partition you have the boot flag on and there will be a box to uncheck. The flag will be gone after you close the popup window.

The MS partition, I think, should have a boot flag.  You do it the same way.  Real tough.

I think you will have to repair your boot in MS as it is not going to boot with that stuff in it.  It is not right.

Used gparted and took the boot flag off sda2 and then set it on on sda3.  So far so good but still cannot boot Windows, as predicted in ranch hand's quote. So I guess the next stage is to repair boot in MS but this is an area I have never touched before so I am unsure how to go about this.

Any suggestions?
Thanks
Phillip

---

### Post by ranch hand on 2010-05-29
I would confirm this from another source but I believe this can be done with the package "testdisk" that is in your Ubuntu repo.

You could down load it and just take a look.

---

### Post by oldfred on 2010-05-29
Since the boot script shows the boot sector as win7/Vista it looks ok, so I do not know if test disk will add anything. It also has some rebuild functions beyond just the copy the backup.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

The windows tools are:
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r /f 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by ranch hand on 2010-05-29
Hey there oldfred,
I opened your post in a separate tab and bookmarked it with my other grub2 stuff.

Thanks for your post it will be a nice thing to send folks to that have this and similar problems.

I am sure they are great links, I have gotten to the point I don't even want to read about MS, so I really should have something like this to send folks to.

---

### Post by Phillip Spencer on 2010-05-30
> **oldfred said:**
> Since the boot script shows the boot sector as win7/Vista it looks ok, so I do not know if test disk will add anything. It also has some rebuild functions beyond just the copy the backup.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)



Check Disk did not work.  I tried through both:

i) booting from the HP Recovery Disk I created but the section on "Identify Problems -> run computer check" has "launch check disk for Windows partition" and "launch check disk for recovery partition" both shaded out.  The only option usable is going to the DOS command prompt.  Trying to run chkdsk from this I can run it on the CD but trying to change to the C: drive just produces "The system cannot find the drive specified." 

ii) Using the Windows 7 32-bit repair kit's "Startup Repair" tool, which seems to incorporate chkdsk, gave the response "Windows cannot repair this computer automatically".  The diagnosis and repair log states:
Session details:
System Disk = \Device\Harddiak0
Windows directory =
Autochk Run = 0
Number of root causes = 1

Unsurprisingly the tests performed OK were: Check for updates; System disk check; Disk failure diagnosis; Disk metadata test.

Root cause found: System volume on disk is corrupt.
Repair action: File system repair (chkdsk)
Result: Failed. Error code = 0x1f

Using the Command Prompt facility on the Repair Disk I can run chkdsk but with the same results as for using the command prompt in HP Recovery Disk.

Not sure if the above is relevant but am including it for completeness as an interim update before I lose the information.

I have found a wealth of information on the additional links you provided and am going to read up before proceeding further with TestDisk.

Thanks for the pointers.
Cheers
Phillip

---

### Post by Phillip Spencer on 2010-05-30
> **oldfred said:**
> 
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. 

There are no Windows installation disks with this PC.  It is the cheap HP approach of creating recovery disks which only give some limited trouble-shooting options (described in previous post) and restore to factory settings option, which is my last resort.

> **oldfred said:**
> Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r /f 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

Since I cannot get to the Command Prompt on the C: drive (see previous post) I am not sure how I can run these commands.

I have just gone back to gparted to look at the partition information again since switching the boot flag from /sda2 to /sda3.  I have not touched /sda1, either when I first screwed up /sda2 or when using gparted earlier this week but there is a warning flag against it and the "information" option produces:

File system: unknown
Size: 992.50 KiB
Flags:
Path: /dev/sda1
Status: Not mounted
Label:
UUID:
First sector: 63
Last sector: 2047
Total sectors: 1985
Warning: Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to gparted
- There is no file system available (unformatted)

Is this likely to be part of the problem or is this just a red herring?

---

### Post by oldfred on 2010-05-30
the windows repair disk you downloaded had just the repair portion of the windows install. When you get to the command line run the list of repair commands I posted.
I have seen chkdsk
chkdsk C: /f and or /r
or 
chkdsk /f
chkdsk /r

try all and let us know which works.

/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
**chkdsk** [*volume***:**][[*Path*] *FileName*] [**/f**] [**/v**] [**/r**] [**/x**] [**/i**] [**/c**] [**/l**[**:***size*]]

---

### Post by Phillip Spencer on 2010-05-30
> **oldfred said:**
> the windows repair disk you downloaded had just the repair portion of the windows install. When you get to the command line run the list of repair commands I posted.
I have seen chkdsk
chkdsk C: /f and or /r
or 
chkdsk /f
chkdsk /r

try all and let us know which works.

/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
**chkdsk** [*volume***:**][[*Path*] *FileName*] [**/f**] [**/v**] [**/r**] [**/x**] [**/i**] [**/c**] [**/l**[**:***size*]]

chkdsk  c: /f /r; chkdsk c: /f; chkdsk c: /r all produce result: "Cannot open volume for direct access."

chkdsk /f and chkdsk /r both produce result "The type of file system is NTFS. Cannot lock the current drive. Windows cannot run disk checking on this volume because it is write protected."
Presumably chkdsk in these cases is looking at the DVD drive?

BootRec.exe /FixBoot  
Result:
The volume does not contain a recognised file system. Please make sure that all required file system drives are loaded and that the volume is not corrupted.

BootRec.exe /ScanOS & BootRec.exe RebuildBcd
Result for both:
Scanning all disks for Windows installations.
Please wait this may take a while...
Successfully scanned Windows installations.
Total identified Windows installations: 0
The operation completed successfully.

I went back and looked at your prior post and followed the link to more information on Bcd.  Using DISKPART and then "list volume" at the DISKPART prompt only shows
Volume 0; Ltr: D; Label: Repair disc; Fs: UDF; Type: DVD-ROM; Size: 143MB; Status: Healthy; Info: (blank)

No information on c: drive or any other Windows drive.

Not sure where this leaves me, as nothing seems to provide information on the Windows drive even though I can see it and read files from Ubuntu.  As it is getting late here in France so I am calling it a night.

Thanks again for the advice.
Cheers
Phillip

---

### Post by ranch hand on 2010-05-30
That is a bugger.

I do not have time to reread the thread and my memory is shot today, did you try testdisk?

I can't see how it can hurt at this point.

My dreaded mother in laws computer (Vista) had this type of problem and I could not fix it with the "repair disk" (no install disk) and I used the directions from the MS site but all I got was "command unknown.

She is booting to Vista though because it was the MBR that was screwed on hers and I fixed it by installing Hardy.  I am not recommending that to you, the MBR is the least of your problems.

Good luck.  I hope oldfred has another trick or two up his sleeve for you.

You can rescue your data at least.  This is a good thing.

---

### Post by oldfred on 2010-05-30
In the boot script in one place it says SFS and the other NTFS. It needs to be NTFS in both places. SFS is a secure system and that may be why windows does not see it.

The easiest way to check which it is and change it would be the system, administration, disk utility. It shows the partition type and lets you change it. It should be 07 - on my system 0x07 not 42.

---

### Post by Phillip Spencer on 2010-05-31
> **oldfred said:**
> In the boot script in one place it says SFS and the other NTFS. It needs to be NTFS in both places. SFS is a secure system and that may be why windows does not see it.

The easiest way to check which it is and change it would be the system, administration, disk utility. It shows the partition type and lets you change it. It should be 07 - on my system 0x07 not 42.

Went into the disk utility tool as suggested. For device /dev/sda3 it showed:
Usage: Filesystem
Partition type: Unknown (0x42)
Partition flags: Bootable
Type: NTFS
Label: -

Changing the partition type to HTPS/NTFS (0x07) as suggested, the process sat there with the "in progress timer" circling round for about ten minutes (and no discernable hard disk activity) before coming up with the following error message:
Error modifying partition
An error occurred while performing an operation on  "259GB Filesystem" (Partition 3 of ATA Hitachi HTS725050A9A364): Unknown error
Details: Message did not receive a reply (timeout by message bus)

File system check on same utility shows "File system is clean"
 
The in progress timer was still running but I could still get into Edit partition so repeated the change process a couple of times in case the timeout was a"one-off" but again got the timeout error message after some ten minutes. Left it for half an hour and the in progress timer icon was still showing so I closed the disk utility application.

Is there an alternative way to change the partition type?

---

### Post by Phillip Spencer on 2010-06-02
> **ranch hand said:**
> That is a bugger.

I do not have time to reread the thread and my memory is shot today, did you try testdisk?

Hi ranch hand, I wholeheartedly agree with your first sentence!

Up to this point I had not tried testdisk because I had limited time and was following through oldfred's advice before using a tool that one of the other posts, #23, warned had a steep learning curve.  However, I have installed testdisk now on the laptop and in trying it out (without yet committing to anything irrevocable) I have some results that puzzle me a little around what is bootable.

First, as background, the testdisk results bear out what oldfred said:
> **oldfred said:**
> In the boot script in one place it says SFS and the other NTFS. It needs to be NTFS in both places. SFS is a secure system and that may be why windows does not see it.

Below is the testdisk log file which right at the end, shows "Current Partition Structure" as having 1st and 3rd partitions (Windows ones) as W2K dynamic /SFS. I assume the asterisk against 3 is the boot flag I previously moved from sda2 to sda3. 

```


Wed Jun  2 16:28:53 2010
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-22-generic (#33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010)
Compiler: GCC 4.4 - Jun 23 2009 17:11:34
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA Hitachi HTS72505

Partition table type (auto): Intel
/dev/sda: Device Configuration Overlay (DCO) present.
Disk /dev/sda - 500 GB / 465 GiB - ATA Hitachi HTS72505
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
check_part_i386 1 type 42: no test
check_part_i386 3 type 42: no test
get_geometry_from_list_part_aux head=255 nbr=1
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=1
Current partition structure:
 1 P W2K Dynamic/SFS          0   1  1     0  32 32       1985
 2 P Linux                31474 144 31 59437  32 51  449218560
 3 * W2K Dynamic/SFS         25 126 38 31474 144 30  505229312
 4 E extended             59437  65 19 60801  47 46   21911554
 5 L Linux Swap           59437  65 21 60801  47 46   21911552

```The testdisk "analyse" result supports this: see screenshot "intel-analyse-01"

I also took a screenshot of the testdisk quick search result, which shows two HPFS / NTFS partitions, which to me verifies oldfred's comment quoted above. See screenshot "quick-search-result-01".  

EDITED from here to the end of post: The bit that really puzzles me though on this screenshot is the asterisk against the first partition which implies that this, marked SYSTEM - which seems to have a start immediately after the end of sda1 - is the primary bootable partition and not the other NTFS partition - which from its size and location I think is sda3.  What testdisk is showing here, I now believe, is the old recovery partition I deleted previously and which has become free space.

The next step would seem to be to proceed from this point and change the characteristics of the partitions to recover that.  However, given my previous problems I want to check exactly how I should proceed!  I can only have a maximum of four primary partitions so I think I may have to change the Linux swap partition first before trying to restore the deleted Windows partition (which had been the original sda2).

Cheers
Phillip

---

### Post by oldfred on 2010-06-02
I have not had to use testdisk, so I do not know all the details. I just have loaded it and done a scan to become a little familiar with it. I think you now know more than I.

Dynamic was a windows partition for a while years ago, so it may be correct, but I think you may still need to recover what you deleted.

---

### Post by ranch hand on 2010-06-02
I am afraid that I have not used it much myself.  There are a lot of folks who have ad swear by it though.

Checking the man page I see no reference to sfs at all though.

I think that oldfred probably has it right that you need whatever it was you deleted.

---

### Post by Phillip Spencer on 2010-06-02
> **oldfred said:**
> Dynamic was a windows partition for a while years ago, so it may be correct, but I think you may still need to recover what you deleted.

Testing out my logic for the order to attempt the recovery:

[LIST]
[*]I currently have four partitions in use (as shown in the "quick-search-result-01" screenshot in the previous post); two Windows (one of which is /sda3 with all my normal windows installation and files, plus another which is causing me some confusion - see below), one Linux primary partition (/sda2) and a Linux swap space - a logical partition (/sda5) in a fractionally larger extended partition (/sda4).
[*]The extended partition was created at the expense of the (original /sda2) Windows recovery partition.  Therefore I have to remove the extended partition before restoring the deleted Windows partition.
[*]I still need the swap space within this. To move this to within the current Linux primary partition /sda2 I need to "Change Type" using testdisk from Primary to Extended and then allocate a logical swap space.  (Can I do this using testdisk from within Ubuntu on that partition?)
[*]With Ubuntu and Swap within a single extended partition I can then remove the current /sda4 extended and /sda5 logical swap partitions.
[*]Then I need to recover the deleted partition. I think this is the NTFS (system) partition shown in the quick-search-results-01 screenshot (physical location from 0 32 33 to 25 126 37) however it does not show as deleted but as bootable primary partition, nor does the partition before it on the drive (from 0 1 1 to 0 32 32) show on here. 0 1 1 to 0 32 32 does show while 0 32 33 to 25 126 37 does not on the screenshot intel-analyse-01. Hmmm!
[*]Having recovered the partition so that I can see it in Disk Utility I then need to move the boot flag from /sda3 to this partition (thus aligning it with bootable primary partition).
[/LIST]
 So, that is my thinking.  My concern is that penultimate bullet point.  Why do the Windows partitions show up differently on the two screen shots?

I confess this is doing my head in!  Fascinating learning experience though!
Cheers
Phillip

---

### Post by ranch hand on 2010-06-02
I know next to nothing about windows but I do know something about Linux and partitioning.

Do not try to mess with a mounted partition.  If you are booted to Ubuntu it is mounted.

Use the Live CD for any such operation.  No, testdisk is not on the Live CD.  You can install it.  It will be on your ram and work just fine.

Sounds a little dangerous to me but reinstalling Ubuntu is not tough if you screw it.

---

### Post by Phillip Spencer on 2010-06-06
> **ranch hand said:**
> I know next to nothing about windows but I do know something about Linux and partitioning.

Do not try to mess with a mounted partition.  If you are booted to Ubuntu it is mounted.

Use the Live CD for any such operation.  No, testdisk is not on the Live CD.  You can install it.  It will be on your ram and work just fine.

Sounds a little dangerous to me but reinstalling Ubuntu is not tough if you screw it.

After a little research, I found the best method to access testdisk without my hard disk partitions mounted was through the "Ubuntu Rescue Remix" tool which I downloaded from [http://ubuntu-rescue-remix.org/node/466](http://ubuntu-rescue-remix.org/node/466) and then burnt the iso file to a CD.  It has a huge range of tools that are worth checking out if you have not come across it before.

                                 The results of testdisk have been a bit depressing. When I ran the “deeper search” it produced these outputs.
 

 Testdisk Deeper search
 Disk /dev/sda – 500 GB / 465 GiB – CHS 60802 255 63
 Analyse cylinder to 60801
 
HPFS – NTFS             0  32  33   25     126      37    407552    [SYSTEM]
HPFS – NTFS             0    32   33       25     126    37        407552   [SYSTEM]
HPFS – NTFS           25  126   38  31474   144  30   505229312
HPFS – NTFS            25  126   38     7596   232  60   121634816
HPFS – NTFS     7596  232   61  12696       50  26    81920000  [FP7DVT01P03]
HPFS – NTFS     7596  232   61  12696       50  26    81920000  [FP7DVT01P03]
FAT32 LBA       12696      50   27  12772    175  11     1228800  [FP7DVT01P03]
FAT32 LBA      12696     50   27  12772    175  11     1228800  [FP7DVT01P03]
check_FAT: Unusual number of reserved sectors 2 (FAT), should be 1.
                                                                         FAT16 LBA     12772  207  44       12798     46  58      407552   [NO NAME]
                Should be marked as FAT12
 Warning: Incorrect number of heads/cylinder 64 (FAT) !=255 (HD)
 Warning: Incorrect number of sectors per track 32 (FAT) !=63 (HD)
                                                                         FAT12                 31177   168 32    31177    200  63         2048
                               HPFS – NTFS       25    126  38    31474   144   30   505229312
                               Linux                   31474  144  31    59437      32    51  449218560
                               The harddisk (500 GB / 465 GiB) seems too small! (< 602 GB / 561 GiB)
 Check the harddisk size: HD jumpers settings, BIOS detection...
 The following partition can't be recovered:
 Partition                Start                            End                Size in sectors
                                                                         Linux            45441 207    51  73304    96  8  449218560
                               [Continue]
 EXT4 Large file Sparse superblock Recover, 229 GB / 214 GiB
 
Pressing [continue] gave:
 Warning: the correct number of heads per cylinder is 255 but the correct value may be 128.
 You can use the geometry menu to change this value.
 It is something to try if
 
[LIST]
[*]some partitions are not found by     TestDisk
[*]or the partition table can not be     written because partitions overlaps.
[/LIST]
 Pressing [continue]:
 
D HPFS – NTFS            0     32     33           25       126     37     407552        [SYSTEM]
D HPFS – NTFS       25  126    37           50      220       41           407552
D HPFS – NTFS          25  126    38     7596     232     60  121634816                           
D HPFS – NTFS          25  126    38   31474  144     30   505229312
D HPFS – NTFS          25  126    38   59247  110     63   951400448
D HPFS – NTFS     7596  232   61  12696       50     26    81920000     [FP7DVT01P03]
                                         D FAT32 LBA      12696  50   27  12772   175 11   1228800  [FP7DVT01P03]
                                         D FAT16 LBA     12772 207 44  12798   46  48      407552 [NO NAME]
                                         D FAT12                  31177 168 32   31177 200 63         2048
                                         D HPFS – NTFS 31474 144 31  59237   78 31  446169088 [New Volume]
                                         D Linux                       31474 144 31  59437   32 51  449218560
                               D HPFS – NTFS 59247 111    1   60788  14 26  24750080 [RECOVERY]
                                         D Linux Swap     59437   65   21   60801  47 30  21911536
                               D FAT32 LBA      60788  14    27    60801 48 31    210992  [HP_TOOLS]
                
 "D" in the first column is Deleted!

The partitions seem to be a total mess judging by the error messages. At this point I have called a halt to try and work out which of the partitions I need to keep.  While I can recognise several, such as the HP_TOOLS and RECOVERY ones, the mass of HPFS - NTFS partitions has me confused.  If I can't unscramble it (and at this point I doubt I can) then I will fall back to the Recovery disks and reinstall, posting I a final note on the results to close the thread.


Cheers
Phillip

---

### Post by oldfred on 2010-06-06
I think it is showing the entire history where you resized and added new NTFS partitions. So it will have several with the same start but different endings and each of those endings as a new start for the new partitions you created. You can create a table of start & ends and figure out which of those partitions you want to recover. You just cannot recover ones that overlap.

---

### Post by ranch hand on 2010-06-06
Well, it sounds like a mess to me.

Thanks for the link.  Never heard of it.  Think I better grab that just for the FUN of it.

---

### Post by Phillip Spencer on 2010-06-06
> **oldfred said:**
> I think it is showing the entire history where you resized and added new NTFS partitions. So it will have several with the same start but different endings and each of those endings as a new start for the new partitions you created. You can create a table of start & ends and figure out which of those partitions you want to recover. You just cannot recover ones that overlap.

Thanks for the pointer that it was a history of the partition changes.  It all made more sense after that.  I had the partition data collated in a table (I just could not figure out how to post it properly in the reply), so I went back and colour-coded the various lines and worked out the sequence. Checking back to the screen-shots I posted earlier it all seemed to tie up.  I changed the relevant partitions and re-booted. Unfortunately this only produced a "grub-rescue" prompt so I have screwed up somewhere.

I re-booted using the Ubuntu Live CD and using disk utility the partition information looked OK apart from the boot flag so I used  gparted to ensure the boot flag was on /sda2.  However, I am still getting the grub-rescue prompt so I am calling it a night now as I think I am beyond my capability to sort this out.

> **ranch hand said:**
> Well, it sounds like a mess to me.

Thanks for the link.  Never heard of it.  Think I better grab that just for the FUN of it.

It is a mess!  Still, I have learnt loads over the past couple of weeks and it has been a fascinating journey.  I would never have expected anyone to refer to this stuff as "FUN" before - but having dug that link out and seen the tools available I can see how all this just sucks one in!  I appreciate the way the Ubuntu community, and especially you two guys, have helped out.  Thanks for sticking with this.

I will close the thread after I have used the recovery disks to go back to the original factory settings.  Fingers crossed those disks work!

Cheers
Phillip

---

### Post by oldfred on 2010-06-06
Usually after messing with partitions grub does not see the correct partition and needs to be reinstalled.

Linux/grub does not use boot flag. If you boot windows directly you have to have the boot flag on the windows partition to make it active. That is how its boot loader knows what partition to go to. Some BIOS check before booting to make sure you have a boot flag on a primary partition.

---

### Post by Phillip Spencer on 2010-06-09
> **oldfred said:**
> Usually after messing with partitions grub does not see the correct partition and needs to be reinstalled.

Linux/grub does not use boot flag. If you boot windows directly you have to have the boot flag on the windows partition to make it active. That is how its boot loader knows what partition to go to. Some BIOS check before booting to make sure you have a boot flag on a primary partition.

I checked I have the boot flag on Windows primary partition.

I am discovering grub now... another new area for me!

Booting from Live CD and using ```
sudo update-grub
``` just provides an error message:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Ensuring the partitions are mounted with Disk Utility has no effect.

From ranch hand's link to his page on Grub at [http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211) I also tried (with same effect)  ```
sudo grub-mkconfig
```From the Grub 2 Ubuntu wiki [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
I tried  ```
sudo apt-get install grub2
```This informs me 
"Package grub2 is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted,or is only available from another source.  
However the following packages replace it:
grub-pc
E: Package grub2 has no installation candidate."

From the wiki, the code:
```

$ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub
```produces the result shown in screenshot "reinstall" so back to where I started.

As a final note for tonight, I also checked 
```
sudo fdisk -l
```and the odd result is for /sda1 which shows partition 1 does not end on a cyclynder boundary.  Not sure if this is significant in the greater scheme of things.  See screenshot "fdisk -l".

Posting these results just to show where I am.  Not sure what to try next, if anything more.
Cheers
Phillip

---

### Post by ranch hand on 2010-06-09
Try these instructions for installing grub from the CD.  You  didn't have the bugger mounted.

Ignore the instructions for editing files.  You should only need the "update-grub", install-grub /dev/sd?" and optionally "grub-mkconfig" to see if the grub.cfg file is right.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by oldfred on 2010-06-09
Did you manage to get your windows to boot ok?

You cannot update your install using those commands from a liveCD. You are just trying to run the command on the liveCD which is not writable so nothing is saved.

Partition/cylinder boundary is not an issue. They are changing the standard way to install and with SSD's the old install created more problems. Windows had already changed so Ubuntu is now following the same partitioning scheme.

You now have used all 4 primary partitions and now do not have a swap. It will work that way if you have lots of memory, but is better with swap.

---

### Post by Phillip Spencer on 2010-06-10
> **ranch hand said:**
> Try these instructions for installing grub from the CD.  You  didn't have the bugger mounted.

Ignore the instructions for editing files. You should only need the "update-grub", install-grub /dev/sd?" and optionally "grub-mkconfig" to see if the grub.cfg file is right.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Ok, mounted properly by following those instructions - Oops! I had misunderstood about the precise nature of the mounting - and the process to update and install worked fine.  Re-booting brought up Grub menu with Ubuntu and Windows 7 options. Progress!

Booting into Ubuntu first, this worked fine.

Booting into Windows 7 on /sda2 failed... which surprised me as this was marked as the bootable partition.

Tried again, booting into Windows 7 on /sda1... this pulled up the Windows Boot Manager giving the option to boot into Windows 7 or Ubuntu (presumably from the aborted exloration of Wubi very early on).  Choosing Windows 7, I successfully booted.  Checked out several specially installed programs (remote access via Citrix to my client in London when I am working from home in France... only reason I need Windows is my client's Windows only policy).  All worked.  Rebooted a couple of times successfully.

Rebooted back into Ubuntu ok after running a load of Windows updates. Am very happy bunny!

> **oldfred said:**
> 
Partition/cylinder boundary is not an issue. They are changing the standard way to install and with SSD's the old install created more problems. Windows had already changed so Ubuntu is now following the same partitioning scheme.
Thanks for clarifying that.  Thought I had done something wrong.
> **oldfred said:**
> 
You now have used all 4 primary partitions and now do not have a swap. It will work that way if you have lots of memory, but is better with swap.

Noted.  I would like to add swap back... but will proceed with caution this time!  Can I adjust the Linux partition, after Ubuntu is installed, making it extended instead of primary and creating a logical swap partition in there?  If I can be pointed at the instructions for doing this post-installation this would be much appreciated.

Thanks to you both for sticking through this with me!
Cheers
Phillip

---

### Post by ranch hand on 2010-06-10
I would not try changing the partition to extended.  It may be possible but it just sounds dangerous to me.

If you have plenty of ram you should not have any real problem if not doing anything real memory intensive.

If you are not having any problems I would leave it alone until you have the urge to just reinstall everything.  That would be the best time to do a real cleanup of your partition table so that you only have one (or 2 if MS insists) primary.

The bugger is working.  As long as it boots right and runs right I would leave it be seeing that you use it in business.

---

