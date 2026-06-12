---
title: "Could someone please look at my hard drives?"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by MisFitt on 2010-04-25
Hi,
I have 2 500GiB hard drives,amd64 dual core(btw)
I've been having a problem since an installation went wrong yesterday and I deleted the XP/Karmic partitions to install again only XP,after loading the initial files and then when it reboots to go on with the format would not boot back in,just a curser blinking.
I couldn't install any other diskout of 6,OS,but one,Karmic 64 which I found very odd.
I must mention during my first attempt at upgrading to Lucid seemed to mess with MBR.,hence my attempt at starting from scratch,clean install of everything.
So the screenshot of my 1st hard drive and I'll put up the 2nd just in case.
Thankyou,a tech friend I spoke to suggested it was the MBR but doesn't know linux
here also is the result ofDisk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098d67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       17847   143347995    f  W95 Ext'd (LBA)
/dev/sda2   *       17848       60800   345019941    7  HPFS/NTFS
/dev/sda5               2        8957    71939038+   7  HPFS/NTFS
/dev/sda6            8958       17479    68452933+  83  Linux
/dev/sda7           17480       17847     2955928+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dbb671e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30237   242870670    f  W95 Ext'd (LBA)
/dev/sdb2   *       30238       60801   245505330    7  HPFS/NTFS
/dev/sdb5               2       30237   242870638+   7  HPFS/NTFS
moi@moi-desktop:~$

---

### Post by P4man on 2010-04-25
Try changing the hdd boot order in your bios.

---

### Post by wilee-nilee on 2010-04-25
So what is your final goal here? do want to have XP and Linux in the end?

---

### Post by k3lt01 on 2010-04-25
Hi Misfitt.

If you want to have XP and Ubuntu what I would do is install XP on 1 drive and Ubuntu on the other. So it would look like this.

1st hdd: Windows: C:\ formatted as NTFS approximately 50 gb for XP (you only need 20 gb but 50 is a good start considering you have 2 different 500 gb drives).
D:\ the remainder of the 1st drive.

2nd hdd: Ubuntu: 10 or 20 gb for / formatted as ext4
2 gb SWAP
the rest as /home formatted as ext4

Set it up with Gparted try to get [Gparted from here]("http://gparted.sourceforge.net/"). Use the Gparted LiveCD to format the drives how you want them and then install XP on 1 and Ubuntu on the other.

---

### Post by MisFitt on 2010-04-25
> **wilee-nilee said:**
> So what is your final goal here? do want to have XP and Linux in the end?
Yes,at this stage it's necessary,
thanks for answering,appreciated

---

### Post by MisFitt on 2010-04-25
> **P4man said:**
> Try changing the hdd boot order in your bios.
you mean before a new installation?
(It wont boot like this if I do)

---

### Post by MisFitt on 2010-04-25
> **k3lt01 said:**
> Hi Misfitt.

If you want to have XP and Ubuntu what I would do is install XP on 1 drive and Ubuntu on the other. So it would look like this.

1st hdd: Windows: C:\ formatted as NTFS approximately 50 gb for XP (you only need 20 gb but 50 is a good start considering you have 2 different 500 gb drives).
D:\ the remainder of the 1st drive.

2nd hdd: Ubuntu: 10 or 20 gb for / formatted as ext4
2 gb SWAP
the rest as /home formatted as ext4

Set it up with Gparted try to get [Gparted from here]("http://gparted.sourceforge.net/"). Use the Gparted LiveCD to format the drives how you want them and then install XP on 1 and Ubuntu on the other.
Thanks,yes gparted's great.
Now,when I install with both drives plugged in on the "side by side" dual boot install how can I have control over where each goes exactly?
Would I have to alter the flags first?

---

### Post by k3lt01 on 2010-04-25
It has been ages since I have done this so I may not be entirely correct ok.

From memory if you install Windows 1st and let it do its thing it automatically becomes the dominant drive, pretty much because at this time it is the only OS on the PC.

Then when you install Ubuntu, making sure you install it to the 2nd drive, the installer and Grub sorts out the OS selection. Keeping them on 2 separate drives simplifies things alot as th mbr on the Windows drive doesn't need modifying but GRUB takes control and still allows you to select one or the other.

If I have forgotten anything someone with more knowledge than me should be able to help.

---

### Post by MisFitt on 2010-04-26
I want to know,as pictured,if those flags need altering/modifying?
I'm too scared of wrecking things further and 
I REALLY need xp back on unfortunately and the karmic install's a little buggy.
I want to go back to Jaunty for a little while for stability's sake.The best for my system was Jaunty/xp,beautiful performance and reliability.
Also I've moved to using 64 bit and have questions about that related to THIS system
AMD64 5600,2 GiB ram.
I will upgrade to 4 GiB ram shortly because I need this for video editing

---

### Post by k3lt01 on 2010-04-26
> **MisFitt said:**
> I'm too scared of wrecking things further and 
I REALLY need xp back onThis is the important thing, if your too scared of wrecking things and you really need XP then install XP and for Ubuntu install it within a VM or install it with WUBI.

> **MisFitt said:**
> I want to know,as pictured,if those flags need altering/modifying? If you choose to go further then the advice I have already offered in my previous post is the best I can do atm.

Install XP on the 1st hdd and then use it so you know its ok. This will make XP the primary OS and it will have its own MBR and bootloader.
Then when you have time, install Ubuntu on the 2nd hdd. GRUB will see Windows on the 1st hdd and make a GRUB entry for it. Ubuntu will also have its own bootable section (i.e. /boot) and within it is GRUB (i.e. /boot/grub/).

So you should have 2 separate hdds both with a bootloader (NTLoader for XP and GRUB for Ubuntu). Furthermore you can, if you so choose, ignore either hdd within your BIOS or give one boot priority ahead of the other.

---

### Post by mal1958 on 2010-04-26
I don't know it this may help but when I had to do a clean install of everything it went as follows:


[LIST=1]
[*]Used a windows boot disk with fdisk on it
[*]removed all partitions using Fdisk
[*]Reboot (with the boot floppy in drive)
[*]repartitioned with Fdisk making my first HD primary and active and did nothing to the secondary drive
[*]Installed windows xp
[*]Then booted off the CD for Jaunty (You could and should use the one for Karmic - reason to follow list)
[*]Installed Jaunty to the second drive in full and let Grub deal with the boot menu.
[/LIST]
  So far I have also updated Grub and upgraded to Karmic and have had no problems.  Now the reason for doing this with the Karmic Live CD.  Jaunty uses an older version of Grub, while Karmic uses Grub 2.  If you plan on installing just Jaunty and never upgrade to Karmic or Lucid (when the bugs are worked out) then just use the live CD with Jaunty.  Otherwise I would use the Karmic live cd.  The older Grub seems to have a problem with the Karmic and above installs.  I have seen many threads here where folk have upgraded to Karmic or Lucid, and not upgraded their grub version, and had their MBR goofed.  I believe that you can lessen the chance of your MBR getting toasted by installing clean from the Karmic Live CD and allowing it to install the newer Grub 2.

Mike

---

### Post by k3lt01 on 2010-04-26
Just thought I'd explain further, with reference to the "flags" when you format the 2 hdds the flags will be wiped also and default flags formatted instead, you do not need to worry about them for the reasons already explained.

---

### Post by MisFitt on 2010-04-26
ThanksMike,that's very well explained,great.
Thing is,Jaunty's not been installed on this new hard drive,only the second.
I'm confused by the flags and whether they're relevant and also how it can be remedied.
I kind of need a step by step guide but...,I'll get there,I have so far with such help,appreciated greatly.

---

### Post by MisFitt on 2010-04-26
The thing is the partition /dev/sda2 is chock full of media I have no room elsewhere to put.
My external 320 is all but full.
As is /sbd,not full but,oh,I suppose I could do it in stages,the long way,one at a time,moving files back and forth.?

---

### Post by MisFitt on 2010-04-26
> **mal1958 said:**
> I don't know it this may help but when I had to do a clean install of everything it went as follows:


[LIST=1]
[*]Used a windows boot disk with fdisk on it
[*]removed all partitions using Fdisk
[*]Reboot (with the boot floppy in drive)
[*]repartitioned with Fdisk making my first HD primary and active and did nothing to the secondary drive
[*]Installed windows xp
[*]Then booted off the CD for Jaunty (You could and should use the one for Karmic - reason to follow list)
[*]Installed Jaunty to the second drive in full and let Grub deal with the boot menu.
[/LIST]
  So far I have also updated Grub and upgraded to Karmic and have had no problems.  Now the reason for doing this with the Karmic Live CD.  Jaunty uses an older version of Grub, while Karmic uses Grub 2.  If you plan on installing just Jaunty and never upgrade to Karmic or Lucid (when the bugs are worked out) then just use the live CD with Jaunty.  Otherwise I would use the Karmic live cd.  The older Grub seems to have a problem with the Karmic and above installs.  I have seen many threads here where folk have upgraded to Karmic or Lucid, and not upgraded their grub version, and had their MBR goofed.  I believe that you can lessen the chance of your MBR getting toasted by installing clean from the Karmic Live CD and allowing it to install the newer Grub 2.

Mike
Mike-all I have is '98 floppys and it's been a long time-would they do?
When I've reformatted I assumed the grub was all new and current.
I've never had this problem before.
I have installed Karmic the last 2 times.
I'm working on Karmic 64 bit now,the only OS I could/that would install.
The other day was the first time I hadn't done a clean install and I wont be doing that again.
I didn't expect it to work to be honest and I had no idea grub'd be ruined/messed up
AND Jaunty has not been installed on /sda,a new disk,only xp and karmic dual booting
Another thing,I have never partitioned using a floppy,only a live disc of jaunty or karmic.
I think that would be beyond my abilities but I'll check it out on the forums and google it.
Thanks

---

### Post by mal1958 on 2010-04-26
If you have the capability of burning a floppy from an image I can try to make an image of my ME boot disk.  That might work since I use that to do the booting on the system for repartitioning for a clean install.  I could try to burn it and if sucessful, then zip the thing up and email it to you.

Mike

---

### Post by oldfred on 2010-04-26
The boot flag is used by windows to know what partition is the active partition to continue to boot from. Linux does not use it, but some BIOS require a boot flag (must assume you are booting windows). You can have only one boot flag per drive and it has to be on a primary partition. You can manage flags with gparted (right click on partition).

When you install windows it automatically installs its boot loader into the MBR. Linux will also install grub or now grub2 into the MBR but there is an advanced button on the screen at the end of partitioning just above the install button. The advance button will then let you choose which MBR to install grub to. You should install grub to the same drive as the Ubuntu install. But whatever drive you do install to that has to be selected in BIOS as the boot drive.

---

### Post by k3lt01 on 2010-04-26
> **mal1958 said:**
> If you have the capability of burning a floppy from an image I can try to make an image of my ME boot disk.  That might work since I use that to do the booting on the system for repartitioning for a clean install.  I could try to burn it and if sucessful, then zip the thing up and email it to you.

MikeOr he/she could go to bootdisk.com and simply get it from there. You would also be better of with a Win 98SE or 95 B or C boot disk if you chose to do it this way, which you don't need to.

> **oldfred said:**
> When you install windows it automatically installs its boot loader into the MBR. Linux will also install grub or now grub2 into the MBR but there is an advanced button on the screen at the end of partitioning just above the install button. The advance button will then let you choose which MBR to install grub to. You should install grub to the same drive as the Ubuntu install. But whatever drive you do install to that has to be selected in BIOS as the boot drive.That's about the 3rd time this has been said in one way or another

---

### Post by MisFitt on 2010-04-26
> **MisFitt said:**
> I want to know,as pictured,if those flags need altering/modifying?
I'm too scared of wrecking things further and 
I REALLY need xp back on unfortunately and the karmic install's a little buggy.
I want to go back to Jaunty for a little while for stability's sake.The best for my system was Jaunty/xp,beautiful performance and reliability.
Also I've moved to using 64 bit and have questions about that related to THIS system
AMD64 5600,2 GiB ram.
I will upgrade to 4 GiB ram shortly because I need this for video editing

I prepare the drives to have XP boot successfully using the Gparted live disk I've just burned,by simply deleting them and formatting?
When I "wipe" the partitions  the flags will be wiped-which means I have to wipe the 2nd drive /dev/sdb?
I have to be careful with /dev/sbd because it has files in  there,if it's possible not to wipe the whole thing out in which case I need to try to make more room in my external 320GiB-that is what I need to consider.
So the mistake I made was NOT deleting and formatting the second hard drive /dev/sbd

---

### Post by k3lt01 on 2010-04-26
> **MisFitt said:**
> This is what I'm not sure about,
the flags on the hard drives and whether I can alter them and if so how(without me messing things up completely!).
How can I prepare the drives to have XP boot successfully using the Gparted live disk I've just burned?
Can someone please go into a little detail how to proceed once I'm looking at the partitions with GParted flag wise?Format the drives as you would normally. Forget about the flags altogether. When you install Windows XP it will format the disk anyway, or at least you should let it, so it will make its own "flags".

After you have XP up and running on 1 of your 2 hdds then install Ubuntu on the other hdd. When Grub installs it will take care of recognising Windows and put an entry into the Grub boot menu for Windows XP.

---

### Post by MisFitt on 2010-04-26
Thanks heaps for answering.
That's the problem initially,windows wouldn't install.
It loaded installation files,deleted then created partition etc then when it comes to the rebooting back into the installation I was left with a blinking cursor

---

### Post by k3lt01 on 2010-04-26
I doubt XP not loading correctly has anything to do with the flags that were in the pictures you posted. How long did it have just a blinking curser for?

---

### Post by MisFitt on 2010-04-26
about 15 minutes on the last attempt before I gave up.
As I wrote earlier,only one disc would go thru' and load,Karmic 64 bit out of several.
It's very strange,I've never had anything like this happen and am at a complete loss.
So,hmmn,I guess I just have to try all over.
Thanks so much for your help

---

### Post by k3lt01 on 2010-04-26
You could try to do a disk check on the XP drive using the GParted LiveCD. It may tell you if the hdd has a fault that is not recoverable.

What are you formatting the XP drive as? NTFS? or FAT32? I ask because FAT32 will not recognise such a large drive and NTFS on some motherboards needs a work around to read a disk (or partition) larger than 138 gb. So it may be an idea to format the XP drive with 3 or 4 partitions (e.g. D:\, E:\, F:\, G:\) as well as the C:\ partition

---

### Post by oldfred on 2010-04-26
We can easily tell were everything is at with this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by MisFitt on 2010-04-27
> **oldfred said:**
> We can easily tell were everything is at with this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

have run that,where can I find the output?
cho Finished. The results are in the file $(basename "$LogFile") located in "$Dir";

---

### Post by MisFitt on 2010-04-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 140681268. But according to the info from 
                       fdisk, sda2 starts at sector 286712118.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00098d67

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065   286,712,054   286,695,990   f W95 Ext d (LBA)
/dev/sda5              16,128   143,894,204   143,878,077   7 HPFS/NTFS
/dev/sda6         143,894,268   280,800,134   136,905,867  83 Linux
/dev/sda7         280,800,198   286,712,054     5,911,857  82 Linux swap / Solaris
/dev/sda2    *    286,712,118   976,751,999   690,039,882   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2dbb671e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065   485,757,404   485,741,340   f W95 Ext d (LBA)
/dev/sdb5              16,128   485,757,404   485,741,277   7 HPFS/NTFS
/dev/sdb2    *    485,757,405   976,768,064   491,010,660   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        2A9407A79407749B                       ntfs       MEDIA                         
/dev/sda5        64B0418FB041691E                       ntfs                                     
/dev/sda6        4a3aec00-18f1-4845-adae-13d6a980a1b5   ext4                                     
/dev/sda7        83774a7c-30ae-43af-9dd7-f1747889554e   swap                                     
/dev/sdb2        424CCFAF4CCF9BD3                       ntfs                                     
/dev/sdb5        B26CA9066CA8C707                       ntfs       G:                            

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/64B0418FB041691E  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/MEDIA             fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5        /media/G:                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2        /media/424CCFAF4CCF9BD3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 4a3aec00-18f1-4845-adae-13d6a980a1b5
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 4a3aec00-18f1-4845-adae-13d6a980a1b5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=4a3aec00-18f1-4845-adae-13d6a980a1b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 4a3aec00-18f1-4845-adae-13d6a980a1b5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=4a3aec00-18f1-4845-adae-13d6a980a1b5 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 4a3aec00-18f1-4845-adae-13d6a980a1b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4a3aec00-18f1-4845-adae-13d6a980a1b5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 4a3aec00-18f1-4845-adae-13d6a980a1b5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4a3aec00-18f1-4845-adae-13d6a980a1b5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2a9407a79407749b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=4a3aec00-18f1-4845-adae-13d6a980a1b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=83774a7c-30ae-43af-9dd7-f1747889554e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  77.9GB: boot/grub/core.img
  77.5GB: boot/grub/grub.cfg
  73.8GB: boot/initrd.img-2.6.31-14-generic
  74.2GB: boot/initrd.img-2.6.31-20-generic
  73.8GB: boot/vmlinuz-2.6.31-14-generic
  73.9GB: boot/vmlinuz-2.6.31-20-generic
  74.2GB: initrd.img
  73.8GB: initrd.img.old
  73.9GB: vmlinuz
  73.8GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 01  |................|
000001c0  01 01 07 fe ff ff 3f 00  00 00 dd d2 f3 1c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

> **oldfred said:**
> We can easily tell were everything is at with this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I did download and burn that Gparted live onto a disk-what a wonderful tool to have,
I know this script should have ended up in a scrolling box but-?

---

### Post by oldfred on 2010-04-27
There is grub file in the windows partition, which I would remove:
/boot/grub/core.img

The partition issue is probably the problem but I do not know partition issues well.

Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 140681268. But according to the info from 
                       fdisk, sda2 starts at sector 286712118.

I do not know if reordering will rewrite the problem or not, and it now without risk. You may want to wait for an additional opinion.

You can reorder the partition with fdisk:
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
Reordering the partition table requires reinstall grub.

---

### Post by MisFitt on 2010-04-27
Thanks OldFred,appreciate it but it's like reading Latin to me-which I don't!
I would need a step by step or a blooming good easier to understand link!

---

### Post by frantid on 2010-04-27
MisFitt, I'd like to help.  I'm a little lost on the current state of things.  See if I have this right:

You tried to reinstall XP, but after the initial XP load for a restart -- nothing happens?

Did you install on sda5?  or sda2?  If it was on sda5 this is an logical drive, XP does not like to boot off an extended partition.  If you installed it there, it probably put the boot files on sda2 and tried to point back to the extended partition.

Are these actual sata drives or are they ide?  If they are sata, did you hit f6 during xp install to install the sata drivers?

You're running karmic, via the live cd or an install.

I've got xp, win7, karmic and lucid booting off the same drive - so hopefully I can help, by comparing my system to yours.

---

### Post by oldfred on 2010-04-27
I actually posted the exact commands as you would enter them except anything after the # is a comment.

See also 

```
man fdisk
```

```
sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk
```

---

### Post by k3lt01 on 2010-04-27
I don't understand why, from the information supplied now, the initial setup is so untidy. It makes no sense to have XP and Ubuntu spread over the 2 separate drives like they appear to be.

Make 1 drive XP and the other drive Ubuntu. That would make it tidy and would remove so much of the difficulty which is now being faced.

MisFitt, are you comfortable with removing or disconnecting a driv from inside the computer? If you are then that will probably be the easiest way to start. After you have only 1 drive connected install XP on the entire drive.

Also can you tell us some information about your system, like the motherboard and CPU type? It may not actually be possible to get this all working if the motherboard doesn't support it.

---

### Post by MisFitt on 2010-04-28
> **k3lt01 said:**
> I don't understand why, from the information supplied now, the initial setup is so untidy. It makes no sense to have XP and Ubuntu spread over the 2 separate drives like they appear to be.

Make 1 drive XP and the other drive Ubuntu. That would make it tidy and would remove so much of the difficulty which is now being faced.

MisFitt, are you comfortable with removing or disconnecting a driv from inside the computer? If you are then that will probably be the easiest way to start. After you have only 1 drive connected install XP on the entire drive.

Also can you tell us some information about your system, like the motherboard and CPU type? It may not actually be possible to get this all working if the motherboard doesn't support it.
Firstly,yes,I'm comfortable with disconnecting/installing hard drives etc.
 
AMD sempron 3400+ AM2 Processor
Gigabyte GA-M61SME-S2 AM2 DDR W/ VGA,PCI-E,SATA2,LAN
2GB Elixer DDR2 677mhz ram(2 times 1 gb)
and I have 2 times 500GB SATA2 7200rpm 16mb western digital (green ones)hd's
and 1 320 Gib,forget brand .external sata2
onboard nvidia,sound.
sda is only a couple of weeks old,sbd could be faulty(karmic said so,kernal error but it's been fine since the new HD,as a secondary)
The /dev/sda2 has a lot of files that I would like to keep as is,"media"

---

### Post by k3lt01 on 2010-04-28
> **MisFitt said:**
> Firstly,yes,I'm comfortable with disconnecting/installing hard drives etc.Ok, just clarifying this so I don't go giving bad advice. You have a disk you can't boot to (sda?) but it has media files you need (sda2). Is that correct?

If it is then I would use GParted to help you copy your media files from sda2 over to your 320gb disk if this is possible, i.e you will need enough room for them (obviously both will need to be connected to achieve this). Shut down your PC.

Disconnect your 320gb disk.

Restart your PC with the Gparted LiveCD and use GParted to format your sda disk. 

If you were able to copy your media files over then format the entire disk in a partition system that you can use effectively i.e. C:\  D:\ etc. (This is your best option because the system will be totally new and tidy).

If you were not able to copy your files over you will only format the parts of the disk that are not required (so don't format sda2). (This isn't the best option but if you can't copy your files over there is no other way around it).

Install XP to C:\. If you formatted a D:\ make it your "My Documents" folder (from memory Windows calls it the "User and Settings" folder I think). Copy your media to where ever you want it, e.g. D:\ E:\ or even M:\ for Media. Use Windows for a bit to make sure you are happy with it.

Refit sdb, and install Ubuntu to that.

Let me know if you have any other questions.

---

### Post by frantid on 2010-04-28
MisFitt,

Did you press f6 when loading xp to get the sata drivers installed?

It might be possible to get xp back, if it has been left alone since the restart -- if you installed the sata drivers.

Is grub working at all?

---

### Post by MisFitt on 2010-04-28
Great,thanks I can only use the sda 5 and sda6 partitions because of 200+Gib of files in sda2(media) and being unsure of the health of the other drive.
I REALLY can't lose those files and my external 320 is almost full,hence being so wary.
OK,sounds like a good plan so I will do it after an early night and get back to you.
Thanks so much,I can't emphasise my appreciation enough
This has been a hassle and a half.

---

### Post by MisFitt on 2010-04-28
> **frantid said:**
> MisFitt,

Did you press f6 when loading xp to get the sata drivers installed?

It might be possible to get xp back, if it has been left alone since the restart -- if you installed the sata drivers.

Is grub working at all?

Grub is working right now yes,but xp,sda5 is shot,corrupt,gone plus I had needed to reinstall it anyway as it wasn't "right",a virus I suspect after speaking with a friend about my hassle with a comodo firewall/AV upgrade.
Now I don't know about pressing f6 and where in the process one would do that or why.
Could you explain that?I've never needed,as far as I know,to load sata drivers manually before.They've just been there I guess,never had this problem and I have installed xp many times successfully,going thru' the motions.This time's a particular headache,physically too(ouch).
Thanks,Annie

---

### Post by frantid on 2010-04-28
> **MisFitt said:**
> Now I don't know about pressing f6 and where in the process one would do that or why.
Could you explain that?I've never needed,as far as I know,to load sata drivers manually before.They've just been there I guess,never had this problem and I have installed xp many times successfully,going thru' the motions.This time's a particular headache,physically too(ouch).
Thanks,Annie

Usually -- XP does not come with drivers for sata interfaces, usually you have to load the drivers during install for xp to see the drives.  The xp cd can see the drives, but on a reboot it would lose the drive.  However, since you've run xp without doing this before -- I think your bios is running the sata drives in emulated pata mode, and xp is just using ide drivers.  It means you don't have to worry about f6, if you've done this before successfully.

Hopefully, your install put your files into sda5.  There are a couple of things we can try.  First, the simplest and hope we get lucky.  We need to edit the boot.ini file in your sda2.  We won't touch any of the other files there.  You need to change the lines:

```
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP  Professional" /noexecute=optin /fastdetect 
```to this:
```
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP  Professional" /noexecute=optin /fastdetect 
```I would use the leafpad in the partedmagic cd to edit this file.  You can use karmic, but you might have to mess with getting read/write on ntfs drives - plus permission problems.


Then try to reboot choosing xp on the grub menu.

---

### Post by k3lt01 on 2010-04-28
> **MisFitt said:**
> I REALLY can't lose those files and my external 320 is almost full,hence being so wary.I know that feeling all to well. There have been more than a couple of times I have just had to go and buy another hdd just so I had somewhere to put the files I could not afford to lose.

Just take your time, figuratively speaking, when you go through the process, checking as you go.

---

### Post by frantid on 2010-04-28
Annie,

I forgot to mention to make sure your windows folder is actually in sda5.  You have to mount the drives in order to see the files.  In partedmagic you use the mount icon on the desktop, click the mount button on the /dev/sda5.  Then you can use the file manager to see the files.  Right click on the file choose open with leafpad.

On karmic  use nautilus and gedit, but to save the file back onto ntfs you need the ntfs-3g package.

---

### Post by frantid on 2010-04-29
I should also mention, the file is boot.ini  It should be in the root of sda2.  It is a hidden file so you have to make sure you have show hidden files option checked.

---

### Post by MisFitt on 2010-04-30
Thanks heaps all,it's done.
I didn't understand all the instructions but I have managed to muddle thru and I now have dual boot working-as in screenshots.
It's a good result,it works,thankyou so much.-I'll post exactly what I did once I find the notes I took(left with a friend).
Any comments would be welcome as I know I have heaps to learn and it's not perfect!.
It's 64 bit Jaunty and xp pro and it and grub works!
will re-edit this asap with details
However there was a problem installing xp(again) and after several tries I now have 2 entries for it

---

