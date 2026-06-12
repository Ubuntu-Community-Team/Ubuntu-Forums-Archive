---
title: "Another dual boot problem , Grub doesn't detect windows 7"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by JiMMaR on 2010-11-02
I just installed Ubuntu 10.10 (64-bit) on my laptop
I already had windows 7 in it , at first I had problems with grub not showing at all (and then it gave me a file not found error) but that all got sorted out

now this is what I have

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9983125d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
/dev/sda2           57380       60802    27481089    5  Extended
/dev/sda3   *        1926       10212    66560000    7  HPFS/NTFS
/dev/sda4           10212       57380   378880000    7  HPFS/NTFS
/dev/sda5           57380       60420    24413184   83  Linux
/dev/sda6           60420       60802     3066880   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I had sda2 as recovery partition before , but when I deleted it the name went to another partition (I now have an allocated space that's not showing)

sda3 here should be my C: drive in windows where windows is installed at (I added the boot flag using gparted as an attempt to make grub detect it .. failed though)

when I update grub it doesn't detect windows 7 and that's what I get

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

here's a screenshot from gparted to make things clearer

[[IMG]http://img23.imageshack.us/img23/1760/screenshotcws.th.png[/IMG]](http://img23.imageshack.us/i/screenshotcws.png/)

I've tried using windows boot cd to repair , it says it detected errors and it'll repair and restart , but nothing happens after that

---

### Post by Hippytaff on 2010-11-02
With my very limited knowledge, it looks like some sectors have over written others on the partitions?

---

### Post by Quackers on 2010-11-02
Please go to the site below and download the boot script to your DESKTOP then run it in a terminal using the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between code tags in your next post. For code tags click on New Reply (not quick reply) and then on the # symbol in the toolbar.
This will show the current state of your system (and Grub).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by JiMMaR on 2010-11-02
> **Hippytaff said:**
> With my very limited knowledge, it looks like some sectors have over written others on the partitions?

what makes you say this ? which part could imply that some sectors have been overwritten ?

I still can't figure out what I should do here >.<

I'll go try booting from windows cd and try to figure it out

---

### Post by JiMMaR on 2010-11-02
> **Quackers said:**
> Please go to the site below and download the boot script to your DESKTOP then run it in a terminal using the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between code tags in your next post. For code tags click on New Reply (not quick reply) and then on the # symbol in the toolbar.
This will show the current state of your system (and Grub).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

There you go

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/bcd /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  de Dell Utility
/dev/sda2         921,808,894   976,771,071    54,962,178   5 Extended
/dev/sda5         921,808,896   970,635,263    48,826,368  83 Linux
/dev/sda6         970,637,312   976,771,071     6,133,760  82 Linux swap / Solaris
/dev/sda3          30,926,848   164,046,847   133,120,000   7 HPFS/NTFS
/dev/sda4         164,046,848   921,806,847   757,760,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2: PTTYPE="dos" 
/dev/sda3        E2682BEC682BBDE3                       ntfs       keep out !                    
/dev/sda4        885070D45070CB08                       ntfs       -.-                           
/dev/sda5        9234c34f-5644-4e49-af64-108d37fcfdf3   ext4                                     
/dev/sda6        01086428-cacd-4afc-a72e-b010041173a4   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
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
    search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9234c34f-5644-4e49-af64-108d37fcfdf3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=9234c34f-5644-4e49-af64-108d37fcfdf3 ro single 
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
    search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 9234c34f-5644-4e49-af64-108d37fcfdf3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
UUID=9234c34f-5644-4e49-af64-108d37fcfdf3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=01086428-cacd-4afc-a72e-b010041173a4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 476.4GB: boot/grub/core.img
 494.3GB: boot/grub/grub.cfg
 472.7GB: boot/initrd.img-2.6.35-22-generic
 476.6GB: boot/vmlinuz-2.6.35-22-generic
 472.7GB: initrd.img
 476.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Hippytaff on 2010-11-02
Quackers is you man for this anyway :-)

---

### Post by Quackers on 2010-11-02
Hmm, I wish!
I don't see anything wrong with the output from the script.
sda2 is now an extended partition which contains sda5 and sda6. I don't know if it's possible that this has caused a problem in the Windows booting process. But even so I would expect Grub to pick up the Windows system.
Maybe you could try this from a terminal please
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```
pressing enter at the end of each line.
When sudo update-grub is running watch the terminal screen and see if Windows is picked up while grub.cfg is generated.

---

### Post by JiMMaR on 2010-11-02
just tried it , no error reported for the first line
and no windows in the 2nd

```

jimmar@Chibi-Ubuntu:~$ sudo grub-install --recheck /dev/sda
[sudo] password for jimmar: 
Installation finished. No error reported.
jimmar@Chibi-Ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by Quackers on 2010-11-02
Ok, thanks.
You said you deleted sda2 (the backup partition). Did you try booting Windows after you did that?
Also, what is in sda1?

---

### Post by wilee-nilee on 2010-11-02
In order for W7 to boot it needs all the boot files including the /bootmgr here is what you should see between sda1 and sda3 the highlighted part is missing.

Boot files/dirs:   **/bootmgr** /Boot/BCD /Windows/System32/winload.exe

When you removed the recovery it was probably the original booting partition. That could be triggered to recover or boot the W7 OS. Put the boot flag on sda3 and rebuild the set up by running auto-repair three times, or use these commands to reload from the terminal in recovery on a booted W7 recovery or install disc. If you run the fixmbr command don't worry grub is easy to load at this point getting W7 back is the whole deal here I suspect

Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Quackers on 2010-11-02
Thanks wilee-nilee, I forgot about bootmgr! What is also foxing me is how  /boot/bcd got on to sda1, if it was originally on sda2 - before it was deleted.

---

### Post by wilee-nilee on 2010-11-02
> **Quackers said:**
> Thanks wilee-nilee, I forgot about bootmgr! What is also foxing me is how  /boot/bcd got on to sda1, if it was originally on sda2 - before it was deleted.

I have seen the firmware tied together to the recovery and the OS a toxic trio really.

I have a bunch of boot scripts I have run on my own setup so I always have to use them, I can't remember that stuff either.;) We will see if this is fixed though.

When it comes to windows and recovery and firmware partitions, in my one purchase where I bought a netbook that had a recovery for XP, I called the manufacturer and got the straight install ISO and wiped the HD and reinstalled. Went from like 35 processes running to 21 alone without the firmware.

I also neglected to post the W7 ISO recovery link if needed.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Quackers on 2010-11-02
> **wilee-nilee said:**
> I have seen the firmware tied together to the recovery and the OS a toxic trio really.



You're right there! Personally, I think it's a really bad idea to put boot files on a recovery partition. Surely the scope for disaster is endless!

---

### Post by JiMMaR on 2010-11-02
> **wilee-nilee said:**
> In order for W7 to boot it needs all the boot files including the /bootmgr here is what you should see between sda1 and sda3 the highlighted part is missing.

Boot files/dirs:   **/bootmgr** /Boot/BCD /Windows/System32/winload.exe

When you removed the recovery it was probably the original booting partition. That could be triggered to recover or boot the W7 OS. Put the boot flag on sda3 and rebuild the set up by running auto-repair three times, or use these commands to reload from the terminal in recovery on a booted W7 recovery or install disc. If you run the fixmbr command don't worry grub is easy to load at this point getting W7 back is the whole deal here I suspect

Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)


that didn't work out, this is what I got for each
```

bootrec.exe /fixmbr
-The operation completed successfully

chkdsk /r
gave me an error saying that it's an NTFS file system and it can't run a disk checking cause it's write protected

bootrec.exe /fixboot
this volume does not contain a recognized file system.
check that all required file system drivers are loaded and the volume is not corrupted

bootrec.exe /scanon
successfully scanned windows installations.
total identified windows installations: 0

bootrec.exe /rebuildbcd
successfully scanned windows installations.
total identified windows installations: 


```

that's basically what I got (I wrote those down so I skipped the un important parts)

and sda1 is a healthy 100mb partition (OEM) that's in all dell laptops we have at home (we got 3).

now when I restart my laptop , it takes me to a Diagnostics GUI that has (test memory - test system - exit)
I assume it's for some reason booting from the sda1 now (I remember it saying it got a diagnostic tools inside it somewhere)

currently booting into ubuntu live CD and will check the flags


Edit: yups , the boot was being done from sda1, where should I change it to now ?

---

### Post by philinux on 2010-11-02
> **Quackers said:**
> You're right there! Personally, I think it's a really bad idea to put boot files on a recovery partition. Surely the scope for disaster is endless!

This is why on my win 7 laptop I used easybcd and put grub on a partition not the mbr. Just in case I needed to use the guarantee.

I shrank the win7 partition as small as it would go and I just default to ubuntu.

---

### Post by wilee-nilee on 2010-11-02
> **Quackers said:**
> You're right there! Personally, I think it's a really bad idea to put boot files on a recovery partition. Surely the scope for disaster is endless!

Funny thing with my netbook is that when I dual booted Lucid before wiping it, the recovery was in the grub menu with the main XP OS, and Lucid. I used the recovery from grub out of curiosity and it worked perfectly, except for the firmware not needed. I forget now but I believe it just rewrote the shrunk partition as well.

---

### Post by Quackers on 2010-11-02
JiMMaR, did you put the boot flag on sda3, as wilee-nilee suggested?

---

### Post by JiMMaR on 2010-11-02
> **Quackers said:**
> JiMMaR, did you put the boot flag on sda3, as wilee-nilee suggested?

I just did , now I get BOOTMGR is missing when I reboot

---

### Post by Quackers on 2010-11-02
I think if you now run startup repair 3 times it will fix it. If not please follow the rest of wilee-nilee's suggestions.

---

### Post by JiMMaR on 2010-11-02
> **Quackers said:**
> I think if you now run startup repair 3 times it will fix it. If not please follow the rest of wilee-nilee's suggestions.

if you mean using windows cd then I'll try that now , but mind explaining why 3 times ? I'm curious

after doing this I should be able to reinstall grub and update and it should detect it , right ?

---

### Post by wilee-nilee on 2010-11-02
> **JiMMaR said:**
> I just did , now I get BOOTMGR is missing when I reboot

You have to run the repairs on sda3 by having it as a active I believe=bootflag on sda3. You can run the script again for yourself and see if your line in W7 is the same as the example.

 File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:  ** /bootmgr /Boot/BCD /Windows/System32/winload.exe**

sda1 is just the firmware partition probably, really more of a nuisance and cpu eater at the least. I can't say remove it though. If it was me I would get rid of any manufacturers firmware, by just back it all up and reinstalling but that is just me. As of now even if W7 gets going it really should be at the start of the HD.

The chkdsk generally runs on reboot so many times you get a error there, could be the partition it was pointed at I don't know your the one there at the console.

If you look at your errors they make sense where they don't work and work. fixmbr no problem fix bcd the partition pointed at sda1 has a bcd file in it, see where I'm going. A windows system was identified well it turns out you have one.;)

---

### Post by JiMMaR on 2010-11-02
cool , you guys are awesome .. guess the reason was because the boot manager was in the recovery partition
I just booted into windows now
I guess I should be able to update grub now

I deleted the recovery because I had a max of 4 partitions and had to delete something for windows (I installed windows manually from a license I had .. the one that came with the laptop was full of bloatware >_>)
and as that I had no idea what sda1 was , I thought it was safe to delete the recovery and then extend the C: drive
too bad I can't extend the C: drive ... now I have 14.65GB of unallocated space in the middle -.-

anyway , that's another issue I think .. I'll mark this as solved :D

---

### Post by Quackers on 2010-11-02
Very nice :-)
Does grub still show - and can it boot Ubuntu and Windows?

---

### Post by wilee-nilee on 2010-11-02
> **JiMMaR said:**
> cool , you guys are awesome .. guess the reason was because the boot manager was in the recovery partition
I just booted into windows now
I guess I should be able to update grub now

I deleted the recovery because I had a max of 4 partitions and had to delete something for windows (I installed windows manually from a license I had .. the one that came with the laptop was full of bloatware >_>)
and as that I had no idea what sda1 was , I thought it was safe to delete the recovery and then extend the C: drive
too bad I can't extend the C: drive ... now I have 14.65GB of unallocated space in the middle -.-

anyway , that's another issue I think .. I'll mark this as solved :D

Don't worry I think we are all relieved when things get fixed. We never really know what customization or tweaking thats been done, or how a manufacturer has set up the computer. You have to be quite knowledgeable about the boot process across multi platforms to really understand this stuff. Fortunately there are forum members who do so we all benefit from their expertise.

---

### Post by JiMMaR on 2010-11-02
> **Quackers said:**
> Very nice :-)
Does grub still show - and can it boot Ubuntu and Windows?

yeah , all fixed now (at least theoretically , am on Ubuntu now and update-grub did show windows so I think it can boot for now)

> **wilee-nilee said:**
> Don't worry I think we are all relieved when things get fixed. We never really know what customization or tweaking thats been done, or how a manufacturer has set up the computer. You have to be quite knowledgeable about the boot process across multi platforms to really understand this stuff. Fortunately there are forum members who do so we all benefit from their expertise.

actually , I never thought that the boot was on the recovery partition , I think I did face the same problem with my old laptop (was dell too) but in that case I reinstalled windows (was to switch from vista to 7) then installed Ubuntu so wasn't a big deal

anyway , now I deleted sda1 and made a new partition :P
sda1+what was the recovery , let's hope nothing bad happens from that XD
I never quit messing up with stuff lol

---

### Post by Quackers on 2010-11-02
> **JiMMaR said:**
> 
I never quit messing up with stuff lol

You're in good company then  :wink:

---

### Post by wilee-nilee on 2010-11-02
> **JiMMaR said:**
> yeah , all fixed now (at least theoretically , am on Ubuntu now and update-grub did show windows so I think it can boot for now)



actually , I never thought that the boot was on the recovery partition , I think I did face the same problem with my old laptop (was dell too) but in that case I reinstalled windows (was to switch from vista to 7) then installed Ubuntu so wasn't a big deal

anyway , now I deleted sda1 and made a new partition :P
sda1+what was the recovery , let's hope nothing bad happens from that XD
I never quit messing up with stuff lol

W7 back up setup is quite good you can backup the whole image and restore it. Although I would do a backup of just the OS and the state it is in, you have alot of stuff on there, I wouldn't trust a backup of the whole thing in whole unless I used clonezilla, or at least was able to confirm a good backup.

Your familiar with the bootscript now this is a great tool for finding the boot stuff and other info.

---

