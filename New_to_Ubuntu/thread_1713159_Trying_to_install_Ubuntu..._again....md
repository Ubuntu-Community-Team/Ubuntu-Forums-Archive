---
title: "Trying to install Ubuntu... again..."
date: 2011-03-23
forum: New to Ubuntu
---

### Post by redfever3993 on 2011-03-23
I have a desire to try Ubuntu 10.10. I did research online and found others who were able to make the operating system work on both Dell Latitudes D630 and Dell Dimensions 8300. Both machines allow me to put the disk in the dive and run the operating system off the disk but when I went to install it the same thing happens on both machines, every time. 
I get to the "who are you?" section in the set up where you enter in your name, it fills in a computer name and username, and then I put in my password, BUT it will not let me click the "Forward" button, and even says "waiting for you". 
I've tried different combinations of names, computer's names, passwords of all strength levels, not using a password, etc. but that button will still not highlight even after letting it sit overnight. I've gone back to the two screens before thinking I missed something but I haven't. 
I've tried multiple CDs, and thumb drives as well.
I noticed the command prompt still will let me type into it, but I don't know anything about codes. 
I consider myself a pretty informed Windows XP/Vista/7 user but know very little about Linux's systems. I figured installing shouldn't be this hard haha.

---

### Post by PRC09 on 2011-03-23
Make sure there are no capital letters in username or password......I think...

---

### Post by rcayea on 2011-03-23
Maybe try the tab key to get yourself to the desired "next" button. Have you tried just hitting enter after submitting your name? This sounds like a massive frustration - especially considering that you are highly interested in Ubuntu.

---

### Post by redfever3993 on 2011-03-24
yeah I've tried all of that to no avail...

---

### Post by NightwishFan on 2011-03-24
The only reason for that I can think of is a capital or symbol in the user name. Sorry if you tried that however that is the only thing I can think of.

---

### Post by mastablasta on 2011-03-24
can you make a screenshot or photo and post it here?
 
another way to install is to use alternate install CD (using text based installer), but a normal CD should work.

---

### Post by Hedgehog1 on 2011-03-24
Another possible reason is that you already have all four primary partitions on your hard drive taken.

To find out if this is the issue, please:

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:K

---

### Post by redfever3993 on 2011-03-26
**_Here is the results from the boot info_**

Show Details
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   384,579,583   384,577,536  83 Linux
/dev/sda2         384,581,630   390,721,535     6,139,906   5 Extended
/dev/sda5         384,581,632   390,721,535     6,139,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e34c624d-19b9-440d-994a-a6b4437f827b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        46a92741-46dc-4802-8f5d-bac3e4bdbb48   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/e34c624d-19b9-440d-994a-a6b4437f827b ext4       (rw,nosuid,nodev,uhelper=udisks)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e34c624d-19b9-440d-994a-a6b4437f827b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=46a92741-46dc-4802-8f5d-bac3e4bdbb48 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 180.5GB: boot/vmlinuz-2.6.35-22-generic
 180.5GB: vmlinuz

---

### Post by Hedgehog1 on 2011-03-26
Well, your partitioning looks just fine:

Disk /dev/sda: 200.0 GB, 200049647616 bytes

/dev/sda1 2,048 384,579,583 384,577,536 83 Linux
/dev/sda2 384,581,630 390,721,535 6,139,906 5 Extended
/dev/sda5 384,581,632 390,721,535 6,139,904 82 Linux swap / Solaris

This is an **Ubuntu Only** install, I see.  The reduces much of the complexity.

So, I guess it is 'screen shot' time where you get stuck at the install.

If you do 'TRY', then double click the "install 10.10", you can surf the web and run the install at the same time.  This will allow you to post a screen shot of the screen (press "PrtSrc" key like in windows)

The Hedge

:KS

---

