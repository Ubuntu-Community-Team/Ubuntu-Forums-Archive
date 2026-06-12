---
title: "GRUB- error: no such partition   grub rescue&gt;"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by mg283633 on 2009-12-20
Before I start you should know that I am completely new to ubuntu. I have windows 7 installed on my computer as well as ubuntu 9.10. I recently deleted the ubuntu to make room on my computer for some HD movies that I was planning on burning. I am planning to reinstall ubuntu once I'm done with these movies. Since uninstalling ubuntu i am no longer able to boot my windows 7 or do anything on my computer. Now when I try to start my computer the only message that I get is:
GRUB loading.
error: no such partition
grub rescue>
My computer is stuck at this point. I need help getting my computer working again. I want to keep the GRUB loader because I planning on reinstalling ubuntu. If anyone can help me it would b greatly appreciated.

---

### Post by leef on 2009-12-20
can you boot into windows by entering the following commands?

```
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot
```

---

### Post by mg283633 on 2009-12-20
I tried this and when I try to use the command rootnoverify (hd0,0) it produces the response of unknown command. Is there anything else that I can try?

---

### Post by drs305 on 2009-12-20
When you deleted the Ubuntu partition you deleted the configuration files necessary for Grub 2 to boot. But Grub 2 is what is on your MBR and controlling your computer's boot process.

You need to restore your Windows bootloader. You can reinstall Grub 2 when you reinstall Ubuntu.

If that is an acceptable solution, this guide will show you how to do it:

[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by leef on 2009-12-20
It might be different in grub2 instead of rootnoverify (hd0,0), try "set root=(hd0,0)" sorry about that, maybe if that doesn't get it maybe try repairing windows with the windows installation media and then worry about reinstall grub when ubuntu is reinstalled?

---

### Post by mg283633 on 2009-12-20
thank you very much it worked like a charm

---

### Post by julio prada on 2009-12-20
> **mg283633 said:**
> I tried this and when I try to use the command rootnoverify (hd0,0) it produces the response of unknown command. Is there anything else that I can try?

I get the same error, looks like this problem is frustrating a lot of people and there is not a guide for non experts.
I reinstalled Ubuntu 9.10 3 times and I get the same problem.
I never get the grub> prompt, only the grub rescue> prompt.
Then I get unknown command with everything I type.
During Ubuntu installation there are "advanced options" but I have not been able to find a help about, not even on the entire Ubuntu site.
I followed the "How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)" but still does not work.
SORRY I made a mistake, IT WORKS NOW!!!!
Too bad!

---

### Post by Prince Valiant on 2009-12-30
I'd love to follow the advice of this thread, but I'm using a netbook with no access to a disk drive.  Any suggestions?  I've got a flash drive with Ubuntu 9.10 installed in lieu of a live CD.

Thanks!

-Val

---

### Post by meierfra. on 2009-12-31
> I've got a flash drive with Ubuntu 9.10 installed in lieu of a live CD.
Open a terminal in ubuntu and run

```
sudo apt-get install lilo
```
(Ignore the message you will get. Just hit enter).

Then

```
sudo lilo -M /dev/sda mbr
```

Here /dev/sda has  to be the device name of your internal hard drive. It is almost certainly /dev/sda, but you should double check with "sudo fdisk -lu"

---

### Post by Prince Valiant on 2009-12-31
Sorry I didn't explain further, but I can't boot from the flash drive, 'cause I think I removed Grub when I deleted partitions.  However, I've fixed the problem for now by installing Ubuntu 9.04 (that's what I had at the moment) onto the flash drive, including Grub.

That enabled me to boot from the flash drive and access Grub; from there I can boot into Windows or the flash drive Ubuntu.  It's a good workaround until I can fix the problem more permanently.  

I don't think I'll need any more help here!

-Val

---

### Post by xiake on 2010-01-01
hey im getting same error message. im using ubuntu 9.10 nbr my computer is an asus 1005hab which has a recovery partition that i want to boot. i followed directions to install lilo exactly as meierfra said only im using ubuntu 9.10 nbr live via usb and lilo is not installing :( Please help i just need to get any bootloader going via usb to boot the recovery partition please help !!

---

### Post by Bansaii on 2010-03-09
> **leef said:**
> can you boot into windows by entering the following commands?

```
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot
```

set root=(hd0,0) works, it goes to next line, I type in 'makeactive'
unknown command, I'm running VISTA...please help I am computerless(except for the one I'm on but it's not mine) until I can fix this problem.

---

### Post by mackat on 2010-03-13
I am trying to install ubuntu 9.1 on my USB Stick 4GB using a live CD
The install goes through no problems...(I delete all partitions on drive and let the installer partition it in default). 
But when I boot from the USB Stick I get an error. 
***GRUB loading.***
[I][B]error: no partition on this disk
Grub rescue > [/B][/I]

can someone help me with this please I am completely new to ubuntu... I don't have hard drive on this computer just a standard dvd and my USB Stick.

---

### Post by presence1960 on 2010-03-13
> **mackat said:**
> I am trying to install ubuntu 9.1 on my USB Stick 4GB using a live CD
The install goes through no problems...(I delete all partitions on drive and let the installer partition it in default). 
But when I boot from the USB Stick I get an error. 
***GRUB loading.***
[I][B]error: no partition on this disk
Grub rescue > [/B][/I]

can someone help me with this please I am completely new to ubuntu... I don't have hard drive on this computer just a standard dvd and my USB Stick.

boot the Live CD with the USB disk plugged in. Select "try ubuntu without any changes." When the desktop loads do this:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by anaghpratit on 2010-05-21
which reply solved the problem????

---

### Post by nana336 on 2010-05-24
I have the exact same problem after I did DiskScan utility and rebooted...  I'm totally scruck here

---

### Post by MuTako on 2010-07-17
Help please! grub rescue sux :(
I started ubuntu from a cd and see what;s the Result.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 294240 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 282200 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 294240 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f770f76

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,931,499    81,931,437   7 HPFS/NTFS
/dev/sda2          81,931,500   488,375,999   406,444,500   f W95 Ext d (LBA)
/dev/sda5          81,931,563   286,744,184   204,812,622   7 HPFS/NTFS
/dev/sda6         286,744,248   488,375,999   201,631,752   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192     7,843,839     7,835,648   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2d9f4e7b-f3d3-435f-be41-75a2aba2f562   ext4                                     
/dev/sda1        B2A01F6FA01F3975                       ntfs                                     
/dev/sda5        54AC17EEAC17C8FE                       ntfs       Local Disk                    
/dev/sda6        0C2CF55D2CF5426E                       ntfs                                     
/dev/sdb1        14E6-BEE6                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/disk-1            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/disk-2            vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 54ac17eeac17c8fe
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b2a01f6fa01f3975
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


    .1GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
   5.8GB: boot/initrd.img-2.6.31-20-generic
   6.0GB: boot/initrd.img-2.6.32-23-generic
   3.0GB: boot/vmlinuz-2.6.31-20-generic
   5.4GB: boot/vmlinuz-2.6.32-23-generic
   6.0GB: initrd.img
   5.8GB: initrd.img.old
   5.4GB: vmlinuz
   3.0GB: vmlinuz.old

```

---

### Post by MuTako on 2010-07-17
Problem solved!
I found an XP disc in my desk, so I've done that one [**here**]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by owens88 on 2010-08-06
I am having the same problem as the OP but with lubuntu


makeactive is not recognised 
make is an unknown command

---

### Post by ebf.beltran on 2010-10-11
I recently tried giving ubuntu extra space in my hard drive taking it away from vista using Partition Manager... but the result was that I ended up at 
```
grup rescue>
```

I need help since a lot of data from my research is in the computer and although half is already backed up I need the rest.

I ran the bash file and got this:
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda5: can't read superblock

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   199,880,729   196,806,682   7 HPFS/NTFS
/dev/sda3    *    199,880,730   234,440,703    34,559,974   5 Extended
/dev/sda5         199,880,793   233,745,749    33,864,957  83 Linux
/dev/sda6         233,750,528   234,440,703       690,176  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        84A4EC25A4EC1C04                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        F4D6F105D6F0C93E                       ntfs       Windows                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        08e48988-0d05-41e0-8ce7-d106041c43fb   ext4                                     
/dev/sda6        c5bc2b4c-70b2-4bf9-b75b-f96cbdba5175   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

please help me

---

### Post by Quackers on 2010-10-11
It seems that sda5 (your linux installation) has a bad superblock. I suspect this is due to a fault with the partition re-sizing. (It's usually best to shrink a Vista/Windows 7 partition with Windows own disk management program - if it will allow it).
At present no system boots, is that correct?
Where is the work you want to save - Windows or Ubuntu?

---

### Post by ebf.beltran on 2010-10-12
Its in ubuntu

currently I can manage to access the windows part from the liveCD

but the Linux partition won't mount.

---

### Post by Quackers on 2010-10-12
Have a look at this link. It could be an option.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by raargh on 2010-10-24
Hi All;

Man. I just hosed my daughter's computer, and I have no time to struggle with this right now - studying for CCNA test on Friday.:(:cry:

I tried to install Ubuntu 10.10 on a 16G usb stick, so that she would have a complete environment she could carry around. I told the 10.10 installer from the Live CD to put everything on the USB, never dreaming it would also put GRUB on the on the hard disk! Now I have the dreaded GRUB rescue> prompt. It won't boot from the XP CD. When I try to install 10.10 to the hard disk it fails, complaining about problems with the partitions being too small.

I'm about ready to give up and restore the system from a GHOST image backup from last month, but she will loose a bunch of iTunes files.

I have a lot of Windoze experience and some Ubuntu experience. Right now the only thing that will boot on her computer is the 10.10 live CD.

Any assistance greatly appreciated.

Steve

---

### Post by drs305 on 2010-10-24
raargh,

Welcome to the Ubuntu forums.

From an Ubuntu Live CD you should be able to get Windows back with the following if you just need to restore the MBR (assumes Windows is on sda):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Don't worry if lilo complains about not being fully installed...

---

### Post by raargh on 2010-10-24
WoW!

Thanks for quick response, drs!:P

In between my 1st post and your reply, I was able to run the LiveCD and do some manual partitioning. Earlier partition attempts had tried to carve out about 8 GB from the 160GB sda that holds NTFS, but then the 10.10 installer crashed. I booted the LiveCD again and used the advanced/manual partition to create a / with about 2048 meg and a swap with about 2048 meg. That got GRUB working and I was able to boot to Windows XP SP3 from the GRUB menu, chkdsk ran and Windows seems OK. GRUB thinks it is on /dev/sd2.

 But, Ubuntu 10.10 will not run - strange package errors.:confused:

Oddly now the XP CD will boot. But, when I press R to run fixboot and fixmbr, the XP setup complains it can't find any hard disks installed!

So, do you think I should still try to install lilo? Consider the following:

My goal now is to either:
1.] Get back to a Windows-only partition and MBR, the way it was before my retardation broke things. (I really just want to continue with the USB install to the 16GB stick, and have Ubuntu 10.10 fully self-contained on the stick so that Jewell can put it in random computers and have Ubuntu on the stick, without it coming up in the "try me" or "install me" mode - just the regular old Ubuntu desktop)
or
2.] Fix the Ubuntu partition so that I can get to the GRUB GUI configurator and set GRUB to default to boot Windows.

Thanks again!:)

Steve

---

### Post by drs305 on 2010-10-24
No, I wouldn't run the lilo commands just yet since you now have a bootable Windows.

From your first post, I would suspect the most important thing for you is to have your daughter's Windows system working. If it is, leave lilo alone (although it should work anyway).

We can tidy up Grub and fix up other problems, but the best thing to do right now is to run the [_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net").

Post the results here, between 'code' tags which you generate by pressing the menubar's # icon.

This script will tell us a lot about your boot files and what needs to be accomplished next.

I'll be logging off shortly but there are plenty of experienced people here who can help you out.

---

### Post by raargh on 2010-10-24
Ok, here is the RESULTS.txt: I really appreciate the quick response!

Can I trouble you to comment on my original goal of producing the self-contained Ubuntu on a stick? Is it as simple as installing it to the stick, but making sure that GRUB also lands on the stick, and not on sda? Again, my goal is to have it be bootable on random computers, and to not have it come up in the annoying "chose try me or install me" mode.

TIA,

Steve

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        128,520   299,915,890   299,787,371   7 HPFS/NTFS
/dev/sda3         305,154,675   309,868,136     4,713,462  82 Linux swap / Solaris
/dev/sda4         299,917,310   305,154,047     5,236,738   5 Extended
/dev/sda5         299,917,312   305,154,047     5,236,736  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D4-0B14                              vfat       DellUtility                   
/dev/sda2        96144E28144E0C25                       ntfs                                     
/dev/sda3        2b07cc2f-4350-48ee-84cf-9fb079f34ab4   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        41dc4b2e-add8-493b-abe6-809791f6030f   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=41dc4b2e-add8-493b-abe6-809791f6030f ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=41dc4b2e-add8-493b-abe6-809791f6030f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 41dc4b2e-add8-493b-abe6-809791f6030f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 96144e28144e0c25
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=41dc4b2e-add8-493b-abe6-809791f6030f /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 155.3GB: boot/grub/core.img
 155.5GB: boot/grub/grub.cfg
 156.0GB: boot/initrd.img-2.6.35-22-generic
 155.4GB: boot/vmlinuz-2.6.35-22-generic
 156.0GB: initrd.img
 155.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  2f bf 0b 9f 81 44 e3 2c  71 c7 57 cf be 58 03 6c  |/....D.,q.W..X.l|
00000010  c8 0d e2 f5 41 65 fe e9  1f db 08 ae 01 33 86 60  |....Ae.......3.`|
00000020  dd f3 6f a4 21 15 c9 a5  b8 1e 47 3a cd 19 bf fc  |..o.!.....G:....|
00000030  eb a8 9a ea d8 db c0 42  0c 18 87 65 fa a2 f7 e8  |.......B...e....|
00000040  4e 1f 98 2e c2 d3 7c b6  b7 4a 46 bd 05 14 31 af  |N.....|..JF...1.|
00000050  a4 4c 01 32 03 32 b1 e7  dc c4 15 91 95 aa 29 ce  |.L.2.2........).|
00000060  ba 5e e0 bd 01 a4 d4 13  33 a5 5a f4 01 a0 19 e4  |.^......3.Z.....|
00000070  fd 90 8f df b6 55 98 03  54 70 1b 23 1e bf fd d8  |.....U..Tp.#....|
00000080  02 81 80 29 28 4e b3 c8  75 ac 83 6b ff ba 00 35  |...)(N..u..k...5|
00000090  00 d4 34 0a 30 60 67 db  ed 86 a5 96 e3 ab 89 a0  |..4.0`g.........|
000000a0  27 21 96 02 60 c2 69 45  fd f7 e8 2d 98 f3 3c 40  |'!..`.iE...-..<@|
000000b0  42 19 92 43 2c 4d 00 74  4c 70 c2 19 33 9c 94 3e  |B..C,M.tLp..3..>|
000000c0  15 f5 88 c6 ce 47 9b f7  bf 44 00 66 03 1e 08 9f  |.....G...D.f....|
000000d0  65 80 79 65 01 d0 06 24  3c 43 2b 96 1a 5f 43 b7  |e.ye...$<C+.._C.|
000000e0  df a9 bd d7 18 65 cf 02  89 21 13 3e 49 68 1b f1  |.....e...!.>Ih..|
000000f0  ca 72 2e 93 61 c1 53 7f  7e 08 07 69 f9 25 60 32  |.r..a.S.~..i.%`2|
00000100  4a dc 7a 59 c8 36 47 41  61 81 3f 27 75 1f 9b dd  |J.zY.6GAa.?'u...|
00000110  a0 0d 40 c0 69 08 98 1a  5e ec 63 0b 0f bb 04 d0  |..@.i...^.c.....|
00000120  1d 60 0c 40 32 26 80 e8  0a 16 90 ce f9 28 49 df  |.`.@2&.......(I.|
00000130  31 8a e7 5d 19 74 91 af  cd 86 80 c4 06 00 30 cc  |1..].t........0.|
00000140  59 34 a4 0e 46 ef c2 b5  e9 48 60 1a a4 87 ba 03  |Y4..F....H`.....|
00000150  1f 23 85 f6 be a0 42 00  54 01 78 0e 80 ae 25 a3  |.#....B.T.x...%.|
00000160  86 ee 7a 46 ba 85 bf 7b  e4 00 20 01 d7 2b 65 2f  |..zF...{.. ..+e/|
00000170  19 f3 dc 63 11 91 ff ef  ed 86 ad b6 55 da 03 01  |...c........U...|
00000180  bc 66 ef f0 bb 86 5a 76  51 b5 45 13 38 ef 82 ac  |.f....ZvQ.E.8...|
00000190  69 26 64 e1 76 a8 2f 63  dd 42 eb e5 3e ed 77 93  |i&d.v./c.B..>.w.|
000001a0  51 92 99 90 51 3a a5 28  fb c9 b7 b4 d7 2b 5e 4b  |Q...Q:.(.....+^K|
000001b0  b4 02 10 28 58 0e ca 25  64 8c c6 fb 93 bf 00 fe  |...(X..%d.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 4f 00 00 00  |............O...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by raargh on 2010-11-02
Hi

Sorry for hijacking this thread.

Been over a week with no reply. I really need to get rid of all partition modifications made to the disk by Ubuntu and have only a Windows XP system. I'm thinking of using Symantec gdisk32 /MBR, but would really like some feedback from the grub gurus first ... I've already decided to restore from image backup. Windows is damaged to the point where the XP recovery cd does not see any physical hard disks. Ghost 11.x from SS 2.51 does see various partitions.


Thanks,

Steve

---

### Post by drs305 on 2010-11-02
If you restore your Windows partitioning scheme you may still have Grub installed in the MBR. Did your backup include a backup of the MBR which you can use to restore it?

If not, it isn't a big deal. You can restore the Windows bootloader using the Windows install or repair disk.

Here is a guide on restoring the Windows bootloader:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

If your Windows install is restored intact and you just need the bootloader to point to Windows, you can do that from the Ubuntu LiveCD. Enable the 'universe' repository (System, Admin, Synaptic > Settings > Repositories). Then install and run *lilo*. Don't worry about lilo complaining about not being completely installed.

Assuming your Windows is on sda:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by raargh on 2010-11-02
Yet again, I am impressed by the real-time response, drs!

I'm restoring from GHOST image now. I'm cautiously optimistic that the image has the MBR; it claims it will overwrite the entire disk and put back three partitions - one was ntfs, one was the Dell untility partition,and another (sorry - forgot to note).

On a separate happy note, I have now successfully created two fully functional Ubuntu 10.10 USB sticks. I gave one to my daughter to use while I struggle with a Vundo variant virus that was the original cause of the problems with her computer that led me to try to put Ubuntu on a stick. She actually likes having a complete computer in her pocket!   She can surf, do her homework, print, etc. If we could get iTunes to work she probably would be ready to abandon Windoze forever ...:P

So, if I need to restore the MBR via Ubuntu, that will be easy via the stick.

I've been working with Sophos tech support on this pesky virus. They did not have a signature for it - it puts copies of itself into the system as  dlls of the form mlmnlm.dll, hhggty.dll, etc. They do various mischief such as redirection, suppress malwarebytes, etc. I sent them a sample and they have produced a sig that will supposedly remove it. Before they got back to me, I was determined to remove the infection manually, and via the Ubuntu stick I deleted all instances of the .dlls I could find. But, I cut too deep and removed part of Windoze's brain, and now it is pretty sick. :((But at least free from virus! :P). So, I'm restoring from the GHOST backup, which is infected, but now that Sophos can remove the virus, I think I see a path to victory.

Restore is running, will take about 2 hours. Please stand by ...

Thanks,

Steve

---

### Post by raargh on 2010-11-02
Hi all;

Well, as expected, the latest version of Symantec GHOST (not to be confused with Norton GHOST), does a complete restore of the entire disk, partitions and MBR, everything. All Linux partitions are gone.

I hope everyone understands that my problems were totally a result of my own ignorance, and Ubuntu was blameless!

Thanks in particular to drs for patient hand-holding.

Steve

---

### Post by Sanchenzo on 2011-01-03
Thank You

---

### Post by pyromaniac344 on 2011-01-22
GOT IT!!!
When you boot with the Ubuntu Live CD and delete a partition, it shows up as "Free Space". However, this doesn't seem to get the job done. If you boot with the Windows installation CD and you delete the Ubuntu partition, it will erase GRUB and the GRUB rescue.

---

### Post by Scrapspoxx on 2011-02-18
Hello folks!

I need some help on this solution/problem.

I had Win XP and Ubuntu 10.04 or 10.10 (not sure) And the grubloader.

Iv'r done like everybody else and have the startup stop at
error: no such partition
grub rescue>

If I write anything there i get "Unknown Command"

I just want to go back to the Windows XP bootloader. 

So I tried the usb windows rescue and write fixmbr. 
The rescue sys it fixes the mbr and all is well. I type exit and take the usb drive out.
Computer reboots and to my disappointment i'm stuck at
error: no such partition
grub rescue>

What should I do? I'm feeling a bit desperate.

My computer is a MSI Wind U100. So it have a win rescue partition that still want on the computer. Then it is two partitions one C: with windos and one D: with files and such. Linux was installed on this partition.


I'm stuck on using a usb drive because this computer doesn't have a cd/dvd drive and I don't have one for USB. But it shouldn't make a difference thinks I.

Thanks on forehand

---

### Post by PeeJay16 on 2011-02-19
I've restored Windows in the past from this error. I can't remember the exact phrasing of some of the windows messages but hopefully this will get you there.

Insert the XP install CD and boot from it
Let it load all the drivers etc
When it gets to the point where it asks you what partition you want to install on select the partition that already has XP installed
When it says 'this will erase the existing windows setup' (I can't remember the exact words) then press F3 and re-boot
When I've done this in the past it's recovered the windows install

---

### Post by KingLex on 2011-02-23
im trying to boot Ubuntu from my portable hdd - but im running 
Windows Vista and when i try to boot i get the - error: no such partition message -
 how am i suppose to setup the boot menu ?

---

### Post by abhinay.pandey on 2011-03-22
i have formated the partition on which ubuntu was installed ...now i am unable to boot my win 7.
only message i get is
grub loading
error:no such partition 
grub rescue.

please tell me what to do.. to get back to windows again

---

### Post by drs305 on 2011-03-23
> **abhinay.pandey said:**
> i have formated the partition on which ubuntu was installed ...now i am unable to boot my win 7.
only message i get is
grub loading
error:no such partition 
grub rescue.

please tell me what to do.. to get back to windows again

What has most likely happened is that the MBR is still pointing to your now nonexistent Ubuntu partition.

From a Ubuntu LiveCD, you can point the MBR boot information to your Windows partition by partially installing lilo.

You have to know which partition your Windows boot files are on. Normally they are on sda1. The following commands will assume this. If you know they are not, change "sda1" to the correct partition.

```
sudo apt-get install lilo
sudo lilo -M /dev/sda MBR

```

Just run those two commands. Don't run any other lilo commands.

If it doesn't work, please go to the following link. Download and run the boot info script and post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by dirkabomb812 on 2011-03-27
> **leef said:**
> It might be different in grub2 instead of rootnoverify (hd0,0), try "set root=(hd0,0)" sorry about that, maybe if that doesn't get it maybe try repairing windows with the windows installation media and then worry about reinstall grub when ubuntu is reinstalled?

i tried this and set root=(hd0,0) worked but then i tried the makeactive command and it said unknown command please help

---

### Post by dandante on 2011-04-17
Hi Guys, I'm also new user of Ubuntu and I have problem. I use my laptop and I have internal HDD which is divided to two parts. Those are marked as sda1 and sda2. On sda1 is installed Windows 7 and sda2 is without OS.
I bought new usb external HDD and I divided the HDD via Gparted in Ubuntu like:
sdb1 primary ntfs 200GB
sdb2 primary ntfs 200GB
sdb3 primary ntfs 200GB
sdb4 extended partition with rest of space. And in this extended partition I created:
sdb5 logical ntfs 200GB
sdb6 swap 4GB
sdb7 ext3 500MB for boot
sdb8 ext3 40GB for root
and rest sdb9 ext3 around 100GB for home.
When I start laptop on the screen is: GRUB- error: no such partition   grub rescue> in case that external drive is active. If I disconnect external HDD Windows start normally from internal HDD. 

Could you help me with this problem? Thank you. 


                [HTML]Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 1646645131 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sdb9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   230,645,204   230,645,142   7 HPFS/NTFS
/dev/sda2         230,645,205   312,576,704    81,931,500   f W95 Ext d (LBA)
/dev/sda5         230,645,268   312,576,704    81,931,437   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   409,593,239   409,593,177   7 HPFS/NTFS
/dev/sdb2         409,593,240   819,186,479   409,593,240   7 HPFS/NTFS
/dev/sdb3         819,186,480 1,228,779,719   409,593,240   7 HPFS/NTFS
/dev/sdb4       1,228,779,781 1,953,520,064   724,740,284   5 Extended
/dev/sdb5       1,228,779,783 1,638,372,959   409,593,177   7 HPFS/NTFS
/dev/sdb6       1,638,373,023 1,646,566,109     8,193,087  82 Linux swap / Solaris
/dev/sdb7       1,646,566,173 1,647,594,269     1,028,097  83 Linux
/dev/sdb8       1,647,594,333 1,729,509,704    81,915,372  83 Linux
/dev/sdb9       1,729,509,768 1,953,520,064   224,010,297  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4AF69855F69842DD                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        865E815B5E814541                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0841EBD3187420C3                       ntfs                                     
/dev/sdb2        5C1EF017563C5AF3                       ntfs                                     
/dev/sdb3        40E0DB4E1DA9D800                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        54C75326021E1561                       ntfs                                     
/dev/sdb6        a336565c-66f7-4608-84aa-cd4cab21bb81   swap                                     
/dev/sdb7        5401a230-0f9e-4b50-b0b9-4255059dd203   ext3                                     
/dev/sdb8        83eb3477-49c2-4dbf-bf65-6fa038415cd4   ext3                                     
/dev/sdb9        566bfdbb-e8e3-475f-b797-c8c6d2bd896a   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/0841EBD3187420C3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/5C1EF017563C5AF3  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb3        /media/40E0DB4E1DA9D800  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/54C75326021E1561  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb7        /media/5401a230-0f9e-4b50-b0b9-4255059dd203 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb8        /media/83eb3477-49c2-4dbf-bf65-6fa038415cd4 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb9        /media/566bfdbb-e8e3-475f-b797-c8c6d2bd896a ext3       (rw,nosuid,nodev,uhelper=udisks)


============================= sdb7/grub/grub.cfg: =============================

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
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 83eb3477-49c2-4dbf-bf65-6fa038415cd4
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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 5401a230-0f9e-4b50-b0b9-4255059dd203
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 5401a230-0f9e-4b50-b0b9-4255059dd203
    linux    /vmlinuz-2.6.32-24-generic root=UUID=83eb3477-49c2-4dbf-bf65-6fa038415cd4 ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 5401a230-0f9e-4b50-b0b9-4255059dd203
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=83eb3477-49c2-4dbf-bf65-6fa038415cd4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 5401a230-0f9e-4b50-b0b9-4255059dd203
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,7)'
    search --no-floppy --fs-uuid --set 5401a230-0f9e-4b50-b0b9-4255059dd203
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4af69855f69842dd
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb7: Location of files loaded by Grub: ===================


 843.0GB: grub/core.img
 843.0GB: grub/grub.cfg
 843.0GB: initrd.img-2.6.32-24-generic
 843.0GB: vmlinuz-2.6.32-24-generic

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=83eb3477-49c2-4dbf-bf65-6fa038415cd4 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sdb7 during installation
UUID=5401a230-0f9e-4b50-b0b9-4255059dd203 /boot           ext3    defaults        0       2
# /home was on /dev/sdb9 during installation
UUID=566bfdbb-e8e3-475f-b797-c8c6d2bd896a /home           ext3    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=a336565c-66f7-4608-84aa-cd4cab21bb81 none            swap    sw              0       0[/HTML]

---

### Post by drs305 on 2011-04-17
@ dandante,

Welcome to the Ubuntu forums!  :-)

We need to place the Grub2 files in the proper location. To do this, we will mount your Ubuntu boot partitions. I don't think you need to mount your /home partition, but we will just to be sure. Boot the LiveCD, then open a terminal and run the following commands. Do not use a partition number in the last command. You want to install Grub2 to the MBR and not a partition.

```
sudo mount /dev/sdb8 /mnt  # Mounts root (/)
sudo mount /dev/sdb7 /mnt/boot && sudo mount /dev/sdb9 /mnt/home  # Mounts /boot and /home
sudo grub-install --root-directory=/mnt /dev/sdb

```

Reboot, making sure BIOS boots to your sdb drive first. If you don't see a menu or if Windows is not listed, after booting (without the CD), run:
```
sudo update-grub
```

---

### Post by squeeish on 2011-04-17
Hi drs305, could you help me out as well? I just installed 10.10 alongside by windows XP SP3. I let Ubuntu do the partitioning for me and I'm getting the no such partition grub rescue thing.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,519,187    58,519,125   7 HPFS/NTFS
/dev/sda2          58,519,550    78,139,391    19,619,842   5 Extended
/dev/sda5          58,519,552    77,205,503    18,685,952  83 Linux
/dev/sda6          77,207,552    78,139,391       931,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        EEE06278E06246C5                       ntfs       IBM_PRELOAD                   
/dev/sda2: PTTYPE="dos" 
/dev/sda5        63cc5c82-8fb3-4b78-a707-2b51254a49ca   ext4                                     
/dev/sda6        2407445b-5355-4f25-a1a9-cc16ed97db28   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=63cc5c82-8fb3-4b78-a707-2b51254a49ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=63cc5c82-8fb3-4b78-a707-2b51254a49ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 63cc5c82-8fb3-4b78-a707-2b51254a49ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set eee06278e06246c5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=63cc5c82-8fb3-4b78-a707-2b51254a49ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2407445b-5355-4f25-a1a9-cc16ed97db28 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/core.img
  35.3GB: boot/grub/grub.cfg
  33.0GB: boot/initrd.img-2.6.35-22-generic
  36.7GB: boot/vmlinuz-2.6.35-22-generic
  33.0GB: initrd.img
  36.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6a c3 ef 3f b5 c0 a5 53  10 86 38 32 a8 78 67 96  |j..?...S..82.xg.|
00000010  a9 ab 96 9b 39 96 e1 c7  ae cd 53 f9 43 cf e5 d5  |....9.....S.C...|
00000020  14 7a 76 97 8d ab 65 55  5b 60 fb 8e e7 2d 20 59  |.zv...eU[`...- Y|
00000030  ad f3 84 c2 be 1a 5c 37  ba 97 a2 6a 8b 97 54 24  |......\7...j..T$|
00000040  a2 26 b7 11 a8 52 3b ba  0c 6e 35 12 c7 5a dd 08  |.&...R;..n5..Z..|
00000050  a3 c4 aa ee 96 37 d5 59  4f 80 0b ad 71 59 51 07  |.....7.YO...qYQ.|
00000060  a8 1f 16 c5 22 6a 7e a6  ab bf 77 bf 27 5a b5 df  |...."j~...w.'Z..|
00000070  41 9f 97 e5 ff ec b1 54  03 6c aa 47 96 7d c1 58  |A......T.l.G.}.X|
00000080  57 71 79 63 86 5f 28 51  5a 2d b0 9d 54 2f fd 1e  |Wqyc._(QZ-..T/..|
00000090  36 60 c1 ac da 4b 27 c8  d6 7b 1c d5 55 61 25 fc  |6`...K'..{..Ua%.|
000000a0  15 8d 30 ee 4f ba 03 54  d6 4b de 53 ad bd 84 61  |..0.O..T.K.S...a|
000000b0  08 0e 03 20 d5 ee 9c 54  b6 1a e5 b3 b7 27 8f ed  |... ...T.....'..|
000000c0  06 0d 3b 25 cd 5a e5 69  aa 2b 30 ec 1f 98 01 a0  |..;%.Z.i.+0.....|
000000d0  b0 06 99 43 f7 4f 52 ea  f8 0e c8 be dc e4 87 1c  |...C.OR.........|
000000e0  08 ee 56 b0 35 34 d8 cf  eb d4 5b 29 3f 77 4e 75  |..V.54....[)?wNu|
000000f0  90 31 6d 18 05 51 2e 32  64 2a a3 c5 ba 35 cb 0c  |.1m..Q.2d*...5..|
00000100  5f 40 e1 31 0b 3a da 67  e6 d4 2e 3b af e3 00 09  |_@.1.:.g...;....|
00000110  c0 cc 9c b8 61 aa a6 b9  29 a5 c4 07 69 14 64 0e  |....a...)...i.d.|
00000120  40 aa 61 63 fc 11 49 4c  62 27 81 5a e6 d3 a1 08  |@.ac..ILb'.Z....|
00000130  c0 27 b2 88 79 e9 11 7c  28 8b 98 27 55 83 4a 94  |.'..y..|(..'U.J.|
00000140  f0 92 7d dd e0 a6 b0 13  4b de 65 33 22 2c dd 3b  |..}.....K.e3",.;|
00000150  e0 b1 e8 51 8d b1 9e 03  a3 e9 4b ee 0e 8d 1e 71  |...Q......K....q|
00000160  c5 52 ad f4 62 ca 21 d0  59 77 fa 63 15 a3 9a 09  |.R..b.!.Yw.c....|
00000170  dc 09 7e 9c fa 54 7b be  90 15 6e 75 11 f0 cf d7  |..~..T{...nu....|
00000180  6e 03 d0 34 cb 5d 57 2c  12 2a 22 25 62 93 6a 36  |n..4.]W,.*"%b.j6|
00000190  af 8a d5 4a 45 d8 3c 38  67 4f d5 75 9f 6b f2 ee  |...JE.<8gO.u.k..|
000001a0  8f c9 96 58 35 7b 53 f7  36 9d bf 67 d5 3c e9 ab  |...X5{S.6..g.<..|
000001b0  4b 27 95 f0 75 9d ec 0f  0c ed 90 fb c9 d5 00 fe  |K'..u...........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 1d 01 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  1d 01 00 40 0e 00 00 00  |....... ...@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

All I want is to be able to choose between windows xp or ubuntu to boot from.

---

### Post by drs305 on 2011-04-17
> **squeeish said:**
> 
All I want is to be able to choose between windows xp or ubuntu to boot from.

That seems like a reasonable request.  :-)

Unfortunately I don't see a problem with your boot files. I would recommend booting the LiveCD and running the 'grub-install' command. You mount your real Ubuntu partition with the first command, and make sure the Grub2 files are installed properly with the second. Note you do NOT use the partition number in the second command.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If it still doesn't boot, hold down the SHIFT key as the computer boots to see if you can get the Grub2 menu. If you do, press 'e' to edit the top menuentry. Use the cursor keys and DEL key to completely remove the "search" line, and change the linux line from "root=UUID=...." to "root=/dev/sda5", then CTRL-x to boot.

If neither of the above works, I'd recommend using the purge/reinstall technique I describe in the thread linked to in my signature line 

("Chroot").

Let us know what happens.

---

### Post by dandante on 2011-04-17
Thank you drs305, 
I tried but it is same again, do you have any other idea?

---

### Post by squeeish on 2011-04-17
Hi drs305,

Thanks for the reply. 

Well I booted my LiveCD and did the two commands, both ran well, but upon restart I was still getting grub rescue.

Then I held down the shift key as the computer booted... this time I got "GRUB loading." and then the same thing... error: out of disk. and then grub rescue.

Then I did the chroot thing, everything was successful but I still get grub rescue.
](*,)

---

### Post by drs305 on 2011-04-17
@ squeeish 
@ dandante

Sorry your efforts have not solved things yet. One clue for *squeesh*, and perhaps it will apply to *dandante* as well, is the "out of disk" message.

When all the files appear correct but Grub2 doesn't work, it's possible the BIOS is not able to see the files due to the disk size. Older BIOS cannot see past either 8 GB or 137 GB, so any files located past that part of the disk remain unknown to BIOS. If the Grub files reside in this location, Grub will also fail.

The problem can be hard to diagnose since once an OS (Windows, Ubuntu, etc) boots the OS can see and run all the files.

Once I saw the size of *squeesh's* drive (40 GB), I wondered if this is a very old motherboard that might have this limitation. Even some more modern computers ship with BIOS that only recognize the first 137 GB, since the manufacturer's have their OS well within the limit.

We can check to see if the limitation is the problem from the Grub prompt. 
First, type "ls" to see the partitions which Grub2 can see.
Next type "ls (hdX,Y)/boot/grub" using the correct X,Y values.
Since we can see the files exist in the RESULTS.txt (once an OS - in this case the LiveCD- boots), if Grub2 can't find them it is probably a BIOS limitation.

You can enter the BIOS setup and find the page/tab that shows the hard drive size. If it shows a drive much smaller than the physical drive, this also tends to confirm the problem.

Options/Solutions:
Look for a BIOS setting to enable LBA or 'large drives'.
Update the BIOS from the manufacturer's site.
Place the entire Ubuntu partition within the BIOS limits.
Create a separate /boot partition within the BIOS limits.
Create a /boot partition on a separate thumb drive, which would have to be inserted any time you boot Ubuntu.

---

### Post by squeeish on 2011-04-18
Hi drs305, 

Thanks, I'll try it out when I get back home later.

Incidentally I remembered that IBM laptops have a hidden partition that is used in events of system restores. Since I allowed Ubuntu to partition the disk for me, could it have affected this hidden partition and that's the reason for the screwed up mbr/grub?

Thanks.

---

### Post by squeeish on 2011-04-20
Well I did it but it hit me that I didn't know what I was looking for exactly.

So I took the plunge and re-installed Ubuntu over my Windows and things are good since :)

---

### Post by drs305 on 2011-04-20
> **squeeish said:**
> 
So I took the plunge and re-installed Ubuntu over my Windows and things are good since :)

:-)

If Grub fails on a grub update or new kernel, it's possible the problem will reappear if the grub files are moved on the disk. If it does, the chances are really good that it's a BIOS disk size issue.

Hopefully you will have a long time of uneventful computing.

Happy Ubuntu-ing !

---

### Post by dandante on 2011-04-22
Hi drs305,

I tried to delete all partitions but the notice Grub error ... is still there on the start. Do you now why? 
My HDD is without partitions now. 
I tried your advice and I checked bios but there is nothing about my external drive. I can't find it. I have HP 550 laptop but Windows and Ubuntu show me correct size of HDD. 

Thanks. :)

---

### Post by drs305 on 2011-04-22
> **dandante said:**
> I tried to delete all partitions but the notice Grub error ... is still there on the start. Do you now why? 
Grub is most likely still present in the MBR of whatever drive is designated as the boot drive in BIOS. On startup the BIOS finds the grub information, which tells the system to look in partition X for more Grub2 directions. That information no longer exists, so the system drops to the grub rescue prompt.

> 
My HDD is without partitions now. 
I tried your advice and I checked bios but there is nothing about my external drive. I can't find it. I have HP 550 laptop but Windows and Ubuntu show me correct size of HDD. 

If it is a BIOS drive size limitation (which I don't know for sure), you will still be able to see the full size in Windows and Ubuntu. This is because the OS's have the capability to see it using their own code. 

The BIOS has it's own code, which is limited. So just because the OS can see the entire drive doesn't mean the BIOS can.

At the grub rescue prompt, you are still limited to what the BIOS is capable of seeing. You can explore what the BIOS can see by using the "ls" command. If the "ls" command doesn't see a partition or drive, it can't be used by Grub. The same with a folder or file within a partition. If G2 can't see the file (such as "ls (hd0,1)/boot/grub/grub.cfg" ) it can't be used.

Let's take an example of a very old computer with a 40GB drive. Let's say the BIOS is limited to seeing 8GB (more recent ones are limited to 137GB, and today's don't have even that limit). BIOS would report a drive size of 8GB. 

If the boot files were within the first 8GB, the system will boot. Ubuntu/Windows will then see the entire hard drive (40GB).

If the files are beyond 8GB, the boot will fail because Grub can't find all the files. Note that only one of the critical files needs to be beyond the limit for the boot to fail. 

Finally, let's say all the files were within the 8GB after an installation and everything boots fine. Now an update is performed. If the OS replaces a Grub or boot file and writes it beyond the first 8GB, the system will fail to boot the next time it's started.

---

### Post by Mostafatherock on 2011-04-30
> **drs305 said:**
> When you deleted the Ubuntu partition you deleted the configuration files necessary for Grub 2 to boot. But Grub 2 is what is on your MBR and controlling your computer's boot process.

You need to restore your Windows bootloader. You can reinstall Grub 2 when you reinstall Ubuntu.

If that is an acceptable solution, this guide will show you how to do it:

[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

[SIZE=3][COLOR=RoyalBlue][B]
This worked for me ... Thank you so much

my ubuntu version is 10.10[/B][/COLOR][/SIZE]

---

### Post by jimakeson on 2011-07-06
Hello,
 
 
usuall story, I am a new to ubuntu, so far I love. I have finnish testing it on a test machine and want to drop it on my laptop and dual boot with an existing windows xp (sp3). i let ubuntu handle this without any apperent problems. At the end of the install it rebooted and the screen went blank, except for a blinking cursor. I could hit enter it moves down a line, I can type and it moves over accordingly. I hit enter and it returns to home on the next line, but nothing changes. If I ctrl+alt+del it comes back to the same thing. Then I power off and boot again. I get the angry message:
error: no such partition
grub rescue>
 
i have changed the bootloader back to windows and windows works just fine.
 
i have tried to reinstall ubuntu, and back to the same result.
 
I think I have tried all of the relevant suggestions in this thred with no improvement. I will post the results from the script in a sec.
 
When I follow "How to restore the Ubuntu grub bootloader" from [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) everything looks good, but no joy.
 
When I type "ls" at the rescue prompt I get:
(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)
 
i have also tried:
sudo mkdir /media/sda6
sudo mount /dev/sda6 /media/sda6
sudo grub-install --root-directory=/media/sda6 /dev/sda
 
same result
 
I hold shift during boot, and the only difference is it appends "GRUB loading.." to the beginning of the error.
 
I also tried:
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda 
 
no change.
 
 
My results from the script are attached(thank you by the way)
 
-J
 
thanks again for any help!!!

---

### Post by drs305 on 2011-07-06
jimakeson,

Welcome to the Ubuntu forums!

I think you have given us a good description of your problem and I think we can determine the problem from what you have provided us.

If you look at the output of the "ls" command at the Grub prompt
> When I type "ls" at the rescue prompt I get:
(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)
you will notice that it does not list sda5, sda6, etc, which are designated (hd0,5), (hd0,6)...

Combined with the fact that your extended partition starts well into the disk, what I suspect is the fault is a BIOS limitation. Older BIOS's (and even some newer ones) don't recognize disk sizes larger than 137GB, and are thus unaware of partitions past that point on the drive. Once an OS is booted, the OS recognizes the entire disk and commands can be successfully run on the entire disk.

To see if it is a BIOS limitation, enter BIOS during boot and see what size the BIOS reports as the drive size. If it reports a drive size of approximately 137GB you have found your problem.

If this is indeed the case, some of your options are to enable 'large drives' or LBA if your BIOS has that option, update your BIOS, change the partition structure of your drive, or create a boot partition on another drive or external device.

Check the BIOS and let us know what you find.

---

### Post by jimakeson on 2011-07-06
> **drs305 said:**
> jimakeson,
 
Welcome to the Ubuntu forums!
 
I think you have given us a good description of your problem and I think we can determine the problem from what you have provided us.
 
If you look at the output of the "ls" command at the Grub prompt
 
you will notice that it does not list sda5, sda6, etc, which are designated (hd0,5), (hd0,6)...
 
Combined with the fact that your extended partition starts well into the disk, what I suspect is the fault is a BIOS limitation. Older BIOS's (and even some newer ones) don't recognize disk sizes larger than 137GB, and are thus unaware of partitions past that point on the drive. Once an OS is booted, the OS recognizes the entire disk and commands can be successfully run on the entire disk.
 
To see if it is a BIOS limitation, enter BIOS during boot and see what size the BIOS reports as the drive size. If it reports a drive size of approximately 137GB you have found your problem.
 
If this is indeed the case, some of your options are to enable 'large drives' or LBA if your BIOS has that option, update your BIOS, change the partition structure of your drive, or create a boot partition on another drive or external device.
 
Check the BIOS and let us know what you find.
 
Interesting, The BIOS on this computer is a POS, it does not actually tell you the size of the hard disk it finds, only that it did find a drive. So I have no idea. True this is not a new computer, but it should be new enough to support LBA. hmm, I will however say I have no way to prove that and as such, I will agree that is probably the issue.you said I could restructure the partition table to accomidate suffering from "Stupid Bios version". How is that? I assume because the Bios is capable of seing the first 130gig of the disk that I can probably get away with moving the ubuntu partition in front of the ext partition? (this ext is the data partition in my windows OS.).
 
If that will work, whats the chances I can do that from the ubuntu boot cd? if so any suggestions on how?
 
That was a fast response by the way! really appreciate it!
 
-Jim 
(Spelling errors are not a flaw in my typing skills, but have been put there to test your ability to find them. If you find them, go get yourself a cookie.)

---

### Post by drs305 on 2011-07-06
> **jimakeson said:**
> Interesting, The BIOS on this computer is a POS, it does not actually tell you the size of the hard disk it finds, only that it did find a drive. So I have no idea. True this is not a new computer, but it should be new enough to support LBA. hmm, I will however say I have no way to prove that and as such, I will agree that is probably the issue.you said I could restructure the partition table to accomidate suffering from "Stupid Bios version". How is that? I assume because the Bios is capable of seing the first 130gig of the disk that I can probably get away with moving the ubuntu partition in front of the ext partition? (this ext is the data partition in my windows OS.).
 
If that will work, whats the chances I can do that from the ubuntu boot cd? if so any suggestions on how?
 
That was a fast response by the way! really appreciate it!
 
-Jim 
(Spelling errors are not a flaw in my typing skills, but have been put there to test your ability to find them. If you find them, go get yourself a cookie.)

The boot files would need to be in the first 135GB or so. Since the "ls" command didn't see the extended partition, I think if you are going to stick with a standard partition table you would need to create a new primary partition. 

Disclaimer: I'm not a Windows person and only have a very basic understanding about Windows partitions. There are some very knowledgeable posters on the forum who can provide much better advice about how to partition Windows setups.

*If* sda1 is Windows and sda2 is not an OS partition (i.e. it's a data partition), the easiest way to fix things might be to shrink the Windows partition (sda1) by 1GB and create a primary linux partition (sda3) for your /boot files.

If you choose to do it this way, go back to Windows, defrag it several times, and preferably use Windows Disk Management or another Windows app to shrink the partition. Gparted/Linux can do the job, but I always at least recommend using Windows-compatible products to perform these types of operations.

If sda2 is also a Windows OS, I'll leave it up to someone more familiar with Windows to suggest how to rearrange things. One option would be to shrink sda2, but you will have to shrink it a lot so I don't know if that's an acceptable option.

You might also be able to place the /boot partition on a flash/thumb drive, but it would always have to be connected, and older BIOS's sometimes can't boot from an external drive.

We can provide more details of how to set up a separate /boot once you determine how you want to go about it.

If you don't mind, I'd like to break your posts off into a new thread. I think you'll get more viewers.

---

### Post by jimakeson on 2011-07-06
> **drs305 said:**
> The boot files would need to be in the first 135GB or so. Since the "ls" command didn't see the extended partition, I think if you are going to stick with a standard partition table you would need to create a new primary partition. 
 
Disclaimer: I'm not a Windows person and only have a very basic understanding about Windows partitions. There are some very knowledgeable posters on the forum who can provide much better advice about how to partition Windows setups.
 
*If* sda1 is Windows and sda2 is not an OS partition (i.e. it's a data partition), the easiest way to fix things might be to shrink the Windows partition (sda1) by 1GB and create a primary linux partition (sda3) for your /boot files.
 
If you choose to do it this way, go back to Windows, defrag it several times, and preferably use Windows Disk Management or another Windows app to shrink the partition. Gparted/Linux can do the job, but I always at least recommend using Windows-compatible products to perform these types of operations.
 
If sda2 is also a Windows OS, I'll leave it up to someone more familiar with Windows to suggest how to rearrange things. One option would be to shrink sda2, but you will have to shrink it a lot so I don't know if that's an acceptable option.
 
You might also be able to place the /boot partition on a flash/thumb drive, but it would always have to be connected, and older BIOS's sometimes can't boot from an external drive.
 
We can provide more details of how to set up a separate /boot once you determine how you want to go about it.
 
If you don't mind, I'd like to break your posts off into a new thread. I think you'll get more viewers.
 
Do this is interesting, I just looked in gparted:
/dev/sda1 (ntfs) (55gig)
/dev/sda2 (ntfs) (195gig)
/dev/sda3 (extended) (47gig)
/dev/sda6 (ext4) (45gig)
/dev/sda7 (linux Swap) (1015mb)
/unallocated (8meg)
/dev/sda5 (linux Swap) (1022mb)
 
now if I read that right, it means my linux partition is inside the extended partition. I thought that wouldnt work? (not like it is now, but you know my point)
 
I will try and move some things arround and see if I can get this to work.
 
-Jim

---

### Post by drs305 on 2011-07-06
> **jimakeson said:**
> Do this is interesting, I just looked in gparted:
/dev/sda1 (ntfs) (55gig)
/dev/sda2 (ntfs) (195gig)
/dev/sda3 (extended) (47gig)
/dev/sda6 (ext4) (45gig)
/dev/sda7 (linux Swap) (1015mb)
/unallocated (8meg)
/dev/sda5 (linux Swap) (1022mb)
 
now if I read that right, it means my linux partition is inside the extended partition. I thought that wouldnt work? (not like it is now, but you know my point)
 
I will try and move some things arround and see if I can get this to work.
 
-Jim

Yes, if it doesn't install to sda1 the installer generally creates an extended partition and installs to sda5/6 (or thereabouts).

If you are able to create a /boot partition within the first 137Gb, you would copy the contents of /boot and subdirectories to / on the new partition. Then add an entry in fstab for /boot, and run "grub-install" with the appropriate switch and "update-grub". I can give you the exact commands once you have the partitions set up.

---

### Post by jimakeson on 2011-07-06
> **drs305 said:**
> Yes, if it doesn't install to sda1 the installer generally creates an extended partition and installs to sda5/6 (or thereabouts).
 
If you are able to create a /boot partition within the first 137Gb, you would copy the contents of /boot and subdirectories to / on the new partition. Then add an entry in fstab for /boot, and run "grub-install" with the appropriate switch and "update-grub". I can give you the exact commands once you have the partitions set up.
 
Thats it! I am going to go get you the biggest, shiniest, most sexiest cookie I can find!!! That was the issue, took about 30 minutes of playing arround with Gparted to get everything alligned to go where it needs to go.
 
|--20--|--40--|--60--|--80--|-100-|-120-|-140-|-160-|-180-|-200-| (Hard Drive)
|-----Windows----|----Ubuntu----|---------------Data-------------| (Partition layout)
|--------------Visible to Bios-----------------|
 
Thank you so much for your help!!

---

### Post by skywalkerluke on 2011-07-14
> **mg283633 said:**
> thank you very much it worked like a charm


Hopefully I'm doing this right...
Would you please tell me what you did to fix the problem? I have the same thing and could not get it to work following  "set root=(hd0,0) instructions.

error: no such partition
grub rescue>

Hopefully you're still there and can help me with this

Thanks

---

### Post by drs305 on 2011-07-14
> **skywalkerluke said:**
> Hopefully I'm doing this right...
Would you please tell me what you did to fix the problem? I have the same thing and could not get it to work following  "set root=(hd0,0) instructions.

error: no such partition
grub rescue>

Hopefully you're still there and can help me with this

Thanks

There is a new app that helps repair Grub2 boot problems. It hasn't been around long enough for us to know exactly which problems it can solve and which it can't. It's easy to use and won't hurt your system although I wouldn't try it if you are using Wubi (Ubuntu inside Linux) since you might lose your Windows bootloader.

You can go to this link, which provides the commands to install and run the Boot Repair tool. If it doesn't solve your problem, click the "BIS" link in my signature line, run the boot info script, and post the contents of RESULTS.txt

Here is the link to the Boot Repair post (Post #426):
[http://ubuntuforums.org/showpost.php?p=11045408&postcount=426]("http://ubuntuforums.org/showpost.php?p=11045408&postcount=426")

---

### Post by Festina_Lente on 2011-08-01
Hi,

I have a dual boot with XP and Ubuntu

In a moment of stupidity I deleted the partition of my HD where Ubuntu was and got then on restart the computer get  

grub rescue> 

I can boot the computer from a USB which has Ubuntu on it.

I have read the forum, but I can't understand what I need to just eliminate Ubuntu, restore windows and then reinstall ubuntu.

I haven't got any XP boot disk. 

I hope you guys can help me. I don't want to make a move till I am more certain about what I am doing (this error killed my confidence!)

---

### Post by drs305 on 2011-08-01
Festina_Lente,

Welcome to the Ubuntu forums.

If Windows was booting normally and all you need to do is point the MBR back to your Windows installation, you can try to fix it via the Ubuntu LiveCD or USB:

You will get some messages in the terminal telling you that lilo is not fully configured. Ignore these messages.

The second command assumes your Windows partition is on sda, which would be the first drive BIOS looks at when booting. That would be the normal setting. If Windows is on the second drive, use sdb.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot and see if you get the Windows bootloader.

---

### Post by Festina_Lente on 2011-08-01
Worked like magic! Thanks a million drs305.

---

### Post by Festina_Lente on 2011-08-04
Hi, 

Just another question: I want to reinstall Ubuntu. I can run it from USB (I am using it now) but when I go to install it on the computer it doesn't recognize that windows xp is on the computer, and gives the option of a manual partition or a fresh install. 

I'm wondering if it's possible to install it the same as the first time, when ubuntu created the dual boot by itself and I just chose the amount of disk space to use?

---

### Post by drs305 on 2011-08-04
> **Festina_Lente said:**
> Hi, 

Just another question: I want to reinstall Ubuntu. I can run it from USB (I am using it now) but when I go to install it on the computer it doesn't recognize that windows xp is on the computer, and gives the option of a manual partition or a fresh install. 

I'm wondering if it's possible to install it the same as the first time, when ubuntu created the dual boot by itself and I just chose the amount of disk space to use?

I wouldn't recommend doing it that way. If Ubuntu isn't seeing the partitions using the LiveCD/USB, I wouldn't rely on it to create a new partition for Ubuntu. 

I'd recommend using Windows to create a new partition, then boot your Ubuntu USB and use Gparted to format the new partition to ext3 or ext4. Once Gparted recognizes the partition the Ubuntu partitioner probably will as well. I'd still choose to create the partitions manually during the installation.

---

### Post by nterpin on 2011-08-04
I had ubuntu installed on my laptop along side with windows XP.  I noticed that I was not using Ubuntu as much as I used to, so I decided to remove the partition where it was.  So I looked up online how to remove the partition.  When I did that, I figured it would be good if I rebooted my laptop, just to make sure it worked.
Well, when I did that, I had the message GRUB error: no such partition   grub rescue>.
Well, after reading everything that had been done before, I decided I would try some of them. As I noticed, GRUB has not been understanding any commands that I am typing in.  I feel like I have tried EVERYTHING! is there anything else that I can do? I am trying to remove the GRUB loader.  Also, because it is a netbook, it has the Windows XP recovery as a partition on the hdd that I did not delete, and cannot get to anymore.

---

### Post by drs305 on 2011-08-04
> **nterpin said:**
> I had ubuntu installed on my laptop along side with windows XP.  I noticed that I was not using Ubuntu as much as I used to, so I decided to remove the partition where it was.  So I looked up online how to remove the partition.  When I did that, I figured it would be good if I rebooted my laptop, just to make sure it worked.
Well, when I did that, I had the message GRUB error: no such partition   grub rescue>.
Well, after reading everything that had been done before, I decided I would try some of them. As I noticed, GRUB has not been understanding any commands that I am typing in.  I feel like I have tried EVERYTHING! is there anything else that I can do? I am trying to remove the GRUB loader.  Also, because it is a netbook, it has the Windows XP recovery as a partition on the hdd that I did not delete, and cannot get to anymore.

Grub is still in the MBR and points to a now non-existent partition. If you have a LiveUSB or any other way to boot to an Ubuntu Desktop, you can point the MBR back to your Windows partition. I'll assume Windows is on *sda* (if not change the second command) and that the boot flag still is on your Windows partition (which would be normal).

Install lilo and point the MBR back to Windows. You will see messages telling you to configure lilo - but just run these two commands and reboot. It should reboot to the Windows bootloader.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by nterpin on 2011-08-04
Thanks for your assistance! It worked great!

---

### Post by Desperad on 2011-08-18
> **drs305 said:**
> Grub is still in the MBR and points to a now non-existent partition. If you have a LiveUSB or any other way to boot to an Ubuntu Desktop, you can point the MBR back to your Windows partition. I'll assume Windows is on *sda* (if not change the second command) and that the boot flag still is on your Windows partition (which would be normal).

Install lilo and point the MBR back to Windows. You will see messages telling you to configure lilo - but just run these two commands and reboot. It should reboot to the Windows bootloader.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

I have the same problem as nterpin but with an ASUS Eee PC 1201HA. It also has a Windows XP recovery partition -- which I cannot enter, not even after disabling the Boot Booster in BIOS. The problem arose after I had deleted the partition containing Ubuntu using EaseUS. 

The CD-ROM with which I had installed Ubuntu is not recognised. I have put the same ISO onto a USB-stick using UNetbootin, but to no avail.

In both cases, I changed the Boot Device Priority in BIOS.

I have reinstalled BIOS using ASUS EZ Flash (Alt+F4), but the GRUB-error continues to appear.

When I insert a Super Grub Disk, my computer tells me to remove it.

I feel I have tried everything -- but to no avail. 

Please help me! :)

---

### Post by drs305 on 2011-08-20
> **Desperad said:**
> 
I feel I have tried everything -- but to no avail. 

Please help me! :)


Desperad,

Welcome to the Ubuntu forums. About all I can suggest is to try a commercial CD and see if it will start. If it does, you still have a problem with the Ubuntu CD burn or with the USB installation. If it doesn't work then you have a BIOS or hardware issue.

I'm starting 2 weeks vacation so hopefully others will come here to assist you. This is a great group of helpers so hopefully someone will come all who can help.

---

### Post by Desperad on 2011-08-21
> **drs305 said:**
> Welcome to the Ubuntu forums. 
Thank you. :)
 
> **drs305 said:**
> About all I can suggest is to try a commercial CD and see if it will start. If it does, you still have a problem with the Ubuntu CD burn or with the USB installation. If it doesn't work then you have a BIOS or hardware issue.
A commercial CD? What exactly do you mean? A Windows installation CD or something? I'll see what I can get my hands on. :)

---

### Post by Desperad on 2011-09-08
> **Desperad said:**
> A commercial CD? What exactly do you mean? A Windows installation CD or something? I'll see what I can get my hands on. :)
It worked! 

I turned on the computer with my friend's Windows installation CD in it. I tried a few options, but aborted and rebooted each time. Then, to my great surprise, Ghost started as though I had been pressing the F9 key during bootup. Next thing I knew, my computer recovered Windows, got married and lived happily ever after. :D

Could someone try and explain what happened? Other people might benefit from it! :)

---

### Post by Hrishikesh Utpat on 2011-10-23
> **leef said:**
> It might be different in grub2 instead of rootnoverify (hd0,0), try "set root=(hd0,0)" sorry about that, maybe if that doesn't get it maybe try repairing windows with the windows installation media and then worry about reinstall grub when ubuntu is reinstalled?

Tried it out...
The first line set root = (hd0, 0) works
the next line makeactive returns uknown command
what do i do????

---

### Post by Hrishikesh Utpat on 2011-10-23
> **Hrishikesh Utpat said:**
> Tried it out...
The first line set root = (hd0, 0) works
the next line makeactive returns uknown command
what do i do????

would using the windows disc help? i have windows 7...

---

### Post by drs305 on 2011-10-23
Hrishikesh Utpat,

Welcome to the Ubuntu Forums.

We need more information, especially since you are jumping into the middle of a very long thread. 

Please start a new thread of your own. Describe the problem(s) you are having. If you can run the Ubuntu LiveCD, download and run the Boot Info Script and post the contents of the RESULTS.txt file it generates.

The RESULTS.txt file will give us a good idea of your boot file status. You can get to the script's download page by clicking the "BIS" link in my signature line.

---

### Post by nebulax on 2012-01-01
First of all, happy new year to everyone reading this. What an excellent way to start the year, heh?

Moving on: I have an asus netbook, that had dual boot (windows 7 - ubuntu 11.10). I wanted to reinstall ubuntu, and so while deleting ubuntu and later merging the partitions i screwed up something and can't boot into windows 7 or load ubuntu livecd(usb stick) to follow some advices here in this thread to recover grub.

some info:

- netbook, so no way to use cd from windows, and also no recovery partition
- GRUB- error: no such partition   grub rescue>

Also I must warn you guys that I am a complete noob, so consider this when guiding me through the possible steps I should follow. And of course feel free to ask me anything that might be useful. 

Thanks!:)

---

### Post by Wiqid95 on 2012-03-27
Hey guys whats up, I’ve my advan vanbook and I did wrong move to erased all my linux data..
  And I’ve achieve an error like:


error: no such partition.
grub rescue>


  
I’ve no idea what a stupid thing I’ve done...
  Before I have this error messages, I was check Computer>Manage>Disk Management
  And I got “2 partition in active & healthy partition”, actually I just wanna to increase my left HDD backup data because it reach almost full, so I do deleted those  “2 partition in active & healthy partition” and became “freespace”, after that I’ve never expected that I’’ve installled my Ubuntu 11.10 in there and the “bootmgr.cfg” (or what, I’ve forgot the file name) suddenly gone....


[FONT=&quot]Also I’ve do a  “ls” and “set” command these the result:[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]grub rescue> ls[/FONT]
[FONT=&quot](hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2)[/FONT] (hd0,msdos1) (fd0)



grub rescue> set
  
Prefix=(hd0,msdos6)/boot/grub
  [FONT=&quot]Root=hd0,msdos6[/FONT]

  
In “ls” command I’ve never found any of (hd0,msdos6) may be its what I’ve deleted..
  Please other problem solve was must knew the root, but I do accidentally was deleted the root, or I don’t know what call it..
  And I think there is nothing to worried about... But I’ve mistaken and after I shutdown my laptop/vanbook I’ve those frightening messages were already to scared me out....
  Please I’ve do a thing, this post may related to all another “problem”, but I think I’ve a different problem to came up like these...
  Please, anyone who’s understand, has known and was ever got the same problem like I do...
  Please I beg your solution, I’m a newbie about computer, not like you all guys whose an expert, a common whose calm to solved it,...
  But I expected that I’ve to havemuch lesson and experience too linux
  And I’m sorry that I never take a step of “repair disk” before the installation linux, I really have no idea for these stuff...
  Please for all your guide...
  Thank’s a billion..

---

### Post by drs305 on 2012-03-28
Wiqid95,

Welcome to the Ubuntu forums.  :-)

Unfortunately, it sounds like you deleted your OS. 

Perhaps the best thing to do is to boot a LiveCD, mount your old Linux partition, and see if anything is there. For now, try not to write anything to the disk to allow you to possibly recover the partition using an application like TestDisk.

Using the LiveCD won't write anything to your hard drive, so boot it to the Desktop. Once booted, open a terminal and then mount your old Linux partition. Then use the file browser to see what is in /mnt:

```
sudo mount /dev/sda5 /mnt
nautilus /mnt
```

You also have other partitions, which are probably another OS such as Windows. If you open a browser and go to the following site you can download the boot info script and run it. It will give you a lot of information about the status of your computer. You can run it from the LiveCD. It generates a file called RESULTS.txt. 

Please start a new thread of your own. Describe again what happened and post the contents of RESULTS.txt.  Hopefully someone can help you determine your next step.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by anewguy on 2012-03-28
I know this is an "after the fact" thread, but I hope I may be allowed to also post a link to a thread that says how to delete Ubuntu and go back to Windows if that is your desire.  Following such guides can help avoid these catch-22 situations.  It's been quite a while, so feel free to add to the thread, including, I hope, a link to this extremely helpful thread also.

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

Thank you,

dave ;)

drs305 - fantastic thread you have here - thanks!

---

### Post by lokesh14sc on 2012-04-18
Thank u so much for giving the best way of solving problem once again thank u so much................

Lokesh S C



> **drs305 said:**
> raargh,



Welcome to the Ubuntu forums.

From an Ubuntu Live CD you should be able to get Windows back with the following if you just need to restore the MBR (assumes Windows is on sda):

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Don't worry if lilo complains about not being fully installed...

---

### Post by Neo4 on 2012-04-23
Hi,
 I'm having the same issue. I've deleted my Ubuntu 10.4 from my eee 1000h pc and left xp.

The problem is that I'm on vacations and only have an iPad with me... Is there any thing I can do to boot xp?

Thanks a lot

---

### Post by foska on 2012-04-27
Worked for me after upgading to 12.04(specifically what drs305 recommended in post #5)

---

### Post by praveen15592 on 2012-05-04
Hey i am new to the ubuntu.. 
today i bought a new laptop with win7 and a linux.. that is 320 gb hard disk but only 200gb was in the drives so i allocate the unallocated 100gb and then restarted my laptop but after tat the i am not able to boot in to any of the os.. only the grub rescue window is showing to me

erro: unkown file system.
entering rescue mode...
grub rescue>


And a sad part is am not having cd drive in this laptop..:( 
what can i do to fix this error without reinstalling my drives...:(

---

### Post by oldfred on 2012-05-05
Did you install from a USB flash drive? If so boot to liveCD/USB mode and download and run this, if not try manual boot as shown in Grub Rescue Megathread.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by scangela333 on 2012-07-08
I'm a complete noob and I feel so dumb. I was trying to erasue the drive on my laptop that had Ubuntu on it, and I must have deleted the wrong one. Now nothing will boot. When I try to turn on my computer I get the following:
 
error: no such partition
grub rescue>
 
 
None of the commands given here are working. Any help would be appreciated.

---

### Post by drs305 on 2012-07-08
> **scangela333 said:**
> I'm a complete noob and I feel so dumb. I was trying to erasue the drive on my laptop that had Ubuntu on it, and I must have deleted the wrong one. Now nothing will boot. When I try to turn on my computer I get the following:
 
error: no such partition
grub rescue>
 
 
None of the commands given here are working. Any help would be appreciated.
scangela333,

Welcome to the Ubuntu Forums. 

Normally it's best to start your own thread - especially in a thread marked SOLVED. You will get better results. But since you are here, have you tried Boot Repair? See the link in my signature line. Run the 'Recommended repair'.

If that doesn't at least restore Ubuntu please run the info script and post the link in a new thread of your own.

Until we see the info script (if BR doesn't work) we really can't provide a useful recommendation.

BR link in my signature line.

---

### Post by ashishmohite on 2012-12-18
> **meierfra. said:**
> Open a terminal in ubuntu and run

```
sudo apt-get install lilo
```
(Ignore the message you will get. Just hit enter).

Then

```
sudo lilo -M /dev/sda mbr
```

Here /dev/sda has  to be the device name of your internal hard drive. It is almost certainly /dev/sda, but you should double check with "sudo fdisk -lu"

hey i did as u told and yes i got my windows7 booting but haven't got any prompt to start windows or ubuntu  
i need my ubuntu also to work please reply asap

---

### Post by cudfather on 2012-12-31
Hello guys,
I have a problem with my mother's Windows 7 netbook. Some time ago I installed Lubuntu on it, but I didn't really use it, so I decided to remove it. Before removing its files I made myself a boot USB flashdrive to fix the MBR after the removal of Lubuntu (I used Hiren's BootCD, put it on a flashdrive).

Here's the problem: when I decided to try it out before deleting Lubuntu, both systems (Windows and Lubuntu) became inaccessible. I get the following message with the USB drive sticked in:
"An operating system wasn't found. Try disconnecting any drives that don't contain an operating system.
Press any key to restart"
Then I press a key, it yields:
"error: no such partition.
grub rescue>"

When I start the computer without the USB sticked in, it just says:
"error: no such partition.
grub rescue>"

So, the bootable USB is inaccessible AND so are the systems. Please help.

---

### Post by offgridguy on 2012-12-31
Hello cudfather, You would probably get better results to start your own new
thread.

---

### Post by cudfather on 2012-12-31
Will do.

---

### Post by winbuntu dual on 2013-04-21
That way doesn't work, i messed around a bit in GRUB and the best way to boot windows is to enter

**Grub>**set root=(hd0,msdos)
**Grub>**mount=(hd0,msdos)
**Grub>**chainloader +1
**Grub>**boot

and your in!

NOTE: this also works in **Grubrescue>**&#8203; I haven't tried this directly, but set root works, so the rest should.

---

