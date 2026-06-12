---
title: "Cant find my windows partitions"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by medusa93 on 2011-08-06
Today I installed Ubuntu11 using Wubi.exe on my WindowsXP sytem (Toshiba satellite laptop). So far I have not been able to access my  Windows partitions. Will I be able to do that ?

---

### Post by coffeecat on 2011-08-06
Welcome to the forum!

Open a Nautilus (file-browser) window - your home folder will be fine. Click on "File System" in the left pane. Now find the /host folder and open that. That is your Windows partition.

If you want that permanently in the left pane, you can add the /host folder as a bookmark from the Nautilus Bookmarks menu.

By the way, take care when you browse the Windows filesystem. You have full write capability and it is easy to accidentally damage/delete Windows system files.

---

### Post by medusa93 on 2011-08-06
Thanks for the quick reply. Following your steps I was able to see my C Drive of XP. However I cant see my other drives (which I had conveniently partitioned as Data(D), Music(E) and Image(F) I had briefly experimented with Ubuntu10 and I remember that these partitions were available without any extra steps

---

### Post by coffeecat on 2011-08-06
They should be even easier to find. Open a Nautilus file browser and they should be right there, listed in the left pane.

If Data, Music and Image are the partition labels, that is what you will see. If there is no partition label, the entry in the left pane will be fairly nondescript - something like "20 GB File system", or whatever size it is.

---

### Post by medusa93 on 2011-08-07
I thank you for taking the time
My windows partitions do not appear on the left pane. Please see the screen shot
I wasn't able to reply earlier because I couldn't get my USB modem to work in Ubuntu. I have managed that now.

---

### Post by gandaran on 2011-08-07
click on the file browser computer icon, if you still don't see the drives then check the file system /media

---

### Post by coffeecat on 2011-08-07
> **medusa93 said:**
> My windows partitions do not appear on the left pane. Please see the screen shot

That is odd.

Let's see exactly what partitions you have. Open a terminal and post the output of these two commands:

```
sudo fdisk -lu
sudo blkid
```

Please post the output between [noparse]```
 and 
```[/noparse] tags for readability. In case you haven't used a command with sudo before, the first will prompt you for your password which will not be echoed to the screen as you type it in. This is disconcerting first time you experience this, but it is going in. Just type the password and press enter and you should get the output.

---

### Post by medusa93 on 2011-08-07
These are the output of the two commands 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaad5aad5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   205744447   102872192+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       205744455   976768064   385511805    f  W95 Ext'd (LBA)
/dev/sda5       205744518   413416709   103836096    7  HPFS/NTFS
/dev/sda6       413416773   619064774   102824001    7  HPFS/NTFS
/dev/sda7       619064838   824712839   102824001    7  HPFS/NTFS
/dev/sda8       824712903   976768064    76027581    7  HPFS/NTFS
prs@ubuntu:~$ sudo blkid
/dev/loop0: UUID="223f9921-d3c0-4dd3-a733-8ea350f47130" TYPE="ext4" 
/dev/sda1: LABEL="Windows" UUID="10F4275BF4274278" TYPE="ntfs" 
/dev/sda5: LABEL="Suneel" UUID="F29C05F49C05B45F" TYPE="ntfs" 
/dev/sda6: LABEL="Added Programs" UUID="F218FCF418FCB8A5" TYPE="ntfs" 
/dev/sda7: LABEL="Music" UUID="38B095E7B095AC3E" TYPE="ntfs" 
/dev/sda8: UUID="01CC395A8B235450" TYPE="ntfs" 

Now I notice that right after I choose Ubuntu as the OS and right before the Grub menu comes up there is an error message that comes and goes in a flash not leaving me enough time to read it in full. However, the words, "NTFS error"  could be read. I have to video tape this to read it. Unfortunately I cant do that right away

---

### Post by medusa93 on 2011-08-07
I got the error message and it required some video skills. This error message is right after I choose Ubuntu as the OS and before the Grub menu appears and verbatim, it reads

Try (hd0,0): NTFS5:error: "prefix" is not set

I dont know wh ether that means that there is something wrong with the disk. In my Windows XP Home I can see and use all my disks

---

### Post by coffeecat on 2011-08-08
Your other partition labels are different from what you described earlier. They are "Suneel", "Added Programs" and "Music". There is also another partition, sda8, with no label and which is 77.9 GB in size. All four of these partitions *should* show in the left pane, even in a Wubi installation. Have you, by chance, installed any applications to "help" with partition mounting? Applications that were not in the default install. There are some 3rd party applications in the repositories for mounting media which can cause more problems than they solve.

---

### Post by medusa93 on 2011-08-08
Yes those are my drive partitions. I am a Ubuntu novice . I did not do anything extra while installation. Just let Wubi do its stuff  and rebooted and chose Ubuntu on the reboot

What about the error message that I see before the Grub boot menu?

---

### Post by coffeecat on 2011-08-08
> **medusa93 said:**
> 
What about the error message that I see before the Grub boot menu?

Sorry for forgetting that. There was a bug, now fixed, that gave that error message or similar, associated with a failure to boot into a Wubi installation. But you seem to be booting up OK. My guess is that you can safely ignore it. It refers to a partition (hd0,0) that is not one of those that you are having difficulty seeing in Nautilus. In fact the error is referring to a partition that cannot exist at all. In legacy grub (grub is the Ubuntu bootloader), the partition identifier (hd0,0) would have referred to your Windows partition sda1, inside which you will find your Wubi Ubuntu virtual filesystem. But Ubuntu 11.04 uses grub2 where the numbering convention has changed, and sda1 would be (hd0,1). In grub2, (hd0,0) would refer to partition number -1! Which is absurd, of course. :)

I'll pm someone who knows a thing or three about wubi, and ask him to look at this thread. I'd like to see his comments about the 'Try (hd0,0): NTFS5:error: "prefix" is not set' error message, and he may have something to suggest about your non-appearing NTFS partitions - which is baffling me.

You can mount the NTFS partitions from the command line and I can tell you how to do that, but I'd prefer to see if we can get the system working as it should with the partitions visible in Nautilus.

Hang in there. You will not be forgotten!

---

### Post by medusa93 on 2011-08-08
I thank you for your efforts.

---

### Post by Rubi1200 on 2011-08-08
Hi and welcome to the forums medusa93 :)

coffeecat asked me to take a look and offer some help, so here goes.

We need to see the output of the boot info script please.

There is a link at the bottom of my post with instructions.
 
Once we have this information, we can try and diagnose this further.

Thanks.

---

### Post by medusa93 on 2011-08-08
Thank you all for the efforts on my behalf

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   205,744,447   205,744,385   7 NTFS / exFAT / HPFS
/dev/sda2         205,744,455   976,768,064   771,023,610   f W95 Extended (LBA)
Extended partition linking to another extended partition.
/dev/sda5         205,744,518   413,416,709   207,672,192   7 NTFS / exFAT / HPFS
/dev/sda6         413,416,773   619,064,774   205,648,002   7 NTFS / exFAT / HPFS
/dev/sda7         619,064,838   824,712,839   205,648,002   7 NTFS / exFAT / HPFS
/dev/sda8         824,712,903   976,768,064   152,055,162   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       223f9921-d3c0-4dd3-a733-8ea350f47130   ext4       
/dev/sda1        10F4275BF4274278                       ntfs       Windows
/dev/sda5        F29C05F49C05B45F                       ntfs       Suneel
/dev/sda6        F218FCF418FCB8A5                       ntfs       Added Programs
/dev/sda7        38B095E7B095AC3E                       ntfs       Music
/dev/sda8        01CC395A8B235450                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 10F4275BF4274278
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=10F4275BF4274278 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=10F4275BF4274278 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
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
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   6.518981934 = 6.999703552    boot/grub/grub.cfg                             1
   2.754116058 = 2.957209600    boot/initrd.img-2.6.38-10-generic-pae          3
   2.469181061 = 2.651262976    boot/vmlinuz-2.6.38-10-generic-pae             2
   2.754116058 = 2.957209600    initrd.img                                     3
   2.469181061 = 2.651262976    vmlinuz                                        2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb

---

### Post by coffeecat on 2011-08-08
@medusa93, there seems to be an irregularity in your partition table affecting all your logical partitions. This is possibly why they are not seen in Nautilus. Each of sda5, sda6, sda7 and sda8 thinks its start sector is sector 63, which is the start sector of sda1, your Windows C: partition. Also, the fdisk output in the boot script output tells us something interesting that fdisk did not originally, namely:

```
Extended partition linking to another extended partition.
```

I've not seen that before and I'm not at all sure what it means. There is no second extended partition - you cannot have more than one extended partition per hard drive - but I wonder if this is related to the start sector 63 issue.

This is becoming both more intriguing and far more challenging than first appeared and needs some thinking about. I and/or Rubi1200 will get back to you but in the meantime, would you please edit your post to include the boot script output within code tags, like this:

[noparse]```
Your boot script output
```[/noparse]

Which when you save will appear thuswise in your post:

```
Your boot script output
```

Output such as that from the boot script needs to be in code tags for clarity. There may or may not be some other things that need attention in the boot script output - I'll take a closer look when you've wrapped it in code tags.

**EDIT**: Also - how did you create the four NTFS partitions that are not your C: partition? Was this with a Windows-based partitioning application? If so, which one? Windows and Windows-based applications can do the most - ahem - extraordinary things to partition tables at times and this might be useful information. :)

---

### Post by medusa93 on 2011-08-08
Now that you ask, I created these partitions after installing Windows XP in C drive. I used a freeware called [Easus Partition Master Home Edition]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html"). This freeware can resize the partitions even after the creation of these partitions. I used them  to format these partitions and have used them to resize my partitions.
I dont seem to be getting the code tags right. I am working on it

---

### Post by medusa93 on 2011-08-08
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   205,744,447   205,744,385   7 NTFS / exFAT / HPFS
/dev/sda2         205,744,455   976,768,064   771,023,610   f W95 Extended (LBA)
Extended partition linking to another extended partition.
/dev/sda5         205,744,518   413,416,709   207,672,192   7 NTFS / exFAT / HPFS
/dev/sda6         413,416,773   619,064,774   205,648,002   7 NTFS / exFAT / HPFS
/dev/sda7         619,064,838   824,712,839   205,648,002   7 NTFS / exFAT / HPFS
/dev/sda8         824,712,903   976,768,064   152,055,162   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       223f9921-d3c0-4dd3-a733-8ea350f47130   ext4       
/dev/sda1        10F4275BF4274278                       ntfs       Windows
/dev/sda5        F29C05F49C05B45F                       ntfs       Suneel
/dev/sda6        F218FCF418FCB8A5                       ntfs       Added Programs
/dev/sda7        38B095E7B095AC3E                       ntfs       Music
/dev/sda8        01CC395A8B235450                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 10F4275BF4274278
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=10F4275BF4274278 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=10F4275BF4274278 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 10F4275BF4274278
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
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   6.518981934 = 6.999703552    boot/grub/grub.cfg                             1
   2.754116058 = 2.957209600    boot/initrd.img-2.6.38-10-generic-pae          3
   2.469181061 = 2.651262976    boot/vmlinuz-2.6.38-10-generic-pae             2
   2.754116058 = 2.957209600    initrd.img                                     3
   2.469181061 = 2.651262976    vmlinuz                                        2

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

 
```

---

### Post by medusa93 on 2011-08-08
I hope that was what was required from me. New to this, please bear with me

---

### Post by coffeecat on 2011-08-08
That's fine. Thanks

I'm going to pm another member who is an expert on partitions. I have a few thoughts on how one could proceed from here, but I'd rather this situation was reviewed by an expert. It is somewhat unusual.

---

### Post by srs5694 on 2011-08-08
Coffeecat asked me to take a look at this thread. As far as I can tell, there's nothing wrong with the partition table per se. I've seen the "extended partition linking to another extended partition" a few times before, and I *think* (but am not 100% positive) that it refers to an unusual method of writing the low-level data structures for the first logical partition. This method seems to crop up from time to time in Windows, and most tools are fine with it; but it does produce this message in some utilities. The fact that the Boot Info Script can read from those partitions means that the partition table entries are valid enough for the kernel to read, so this almost certainly is not the source of the problem.

One thing you might try before doing any further diagnostics is to run disk checks on those partitions in Windows (using the CHKDSK command-line tool or its GUI equivalent). When you're done, be sure to shut down Windows correctly with the "shut down" menu option -- don't just power off the computer! If that fixes the problem, then be careful to shut down the computer properly in the future.

If that fails, then further diagnostics are in order on the Linux side:


[LIST=1]
[*]Type "df -h" and post the output (in [noparse][code][/noparse] tags to preserve legibility). This will reveal if the partitions might already be mounted somewhere unusual.
[*]Try typing "sudo mount /dev/sda5 /mnt" and, if any error messages result, post them. If you don't see error messages, type "ls /mnt" to see if the files become available. If they do, then you know that /dev/sda5 *can* be mounted, so you could create an /etc/fstab entry to do the job. (Post back for information on how to do this.) Type "umount /mnt" and you can try the same thing with the other partitions (/dev/sda6 through [noparse]/dev/sda8)[/noparse].
[/LIST]

---

### Post by waynefoutz on 2011-08-08
All the code and gobbledygook in the previous posts are not going to solve this. Wubi.exe installs Ubuntu on a loop mounted virtual disk. It's not a partition. It cannot see outside of itself, unless it's a separate  physical drive. The only way to transfer files to the Windows drive is with an external thumb or hard drive. Or else upload them to a cloud service or email them to yourself.

---

### Post by coffeecat on 2011-08-08
> **waynefoutz said:**
> It cannot see outside of itself, unless it's a separate  physical drive.

Please do not post misleading information, and please read the documentation. Ubuntu Wiki Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

> How do I access the Windows drives?

The Windows partition where you installed Wubi is available as /host within Ubuntu (Places > Computer > File System > Host) **All the other partitions will be available under Places > Removable Media **

A wubi installation is quite capable of seeing a partition outside of the host partition.

---

### Post by coffeecat on 2011-08-09
@medusa93, in case you were distracted by waynefoutz's post I thought it would be helpful for you to see more-or-less what you should be seeing in Nautilus in a wubi install. I'm posting from wubi Ubuntu 11.04 installed inside a Windows 7 C: partition. There is also another conventional installation of Ubuntu 11.04 on this machine in its own ext4 partition.

Have a look at my screenshot. This is a Nautilus window open in my home folder. Now have a look at the left (Places) pane. Below "File System" and "Network" you'll see three partitions listed, Natty1, SYSTEM and Data. Those are the three partition labels. "Natty1" is the Ubuntu 11.04 system on its own partition and quite separate from the wubi Ubuntu that I'm posting from. "SYSTEM" is the Windows 7 boot partition, and "Data" is a NTFS partition for sharing data between Windows and Ubuntu -  it is seen as "D:" in Windows.

All I have to do is to click once on whichever partition I want mounted and it is. You can see that I have mounted the "Natty1" partition and its filesystem is showing in the main Nautilus pane. You can also see an eject symbol nest to "Natty1". This signifies that the partition is mounted and if I want to unmount it you simply click on the symbol.

As you can see, partitions other than and as well as the host one should be visible and accessible in a wubi system. For some reason your system is not showing them, so I suggest you follow srs5694's advice. I'll keep this thread subscribed.

---

### Post by medusa93 on 2011-08-09
Thanks  coffeecat, Rubi1200 and srs5694.
Quote 
```
 When you're done, be sure to shut down Windows correctly with the "shut down" menu  
option -- don't just power off the computer! If that fixes the problem, 
then be careful to shut down the computer properly in the future.
```Should I have mentioned that I was getting some blue screen errors in Windows XP ?    Those were the only times in XP where I did not go in for a proper shut down
I did a hard disk and memory diagnostic test for that and that came clean and I was  
trawling Google and a nice Windows forum  for solution and came to the conclusion that 
no matter what Windows version I choose, I could always be "blessed" with the blue screen 
 messages. I wonder whether it is those windows blue screen problems that persist with Ubuntu in some manner.

I did the chkdsk in windows on all the partitions and rebooted and still doesn't solve my problem

---

### Post by medusa93 on 2011-08-09
```
prs@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G  3.4G   12G  22% /
none                  2.0G  740K  2.0G   1% /dev
none                  2.0G  296K  2.0G   1% /dev/shm
none                  2.0G  228K  2.0G   1% /var/run
none                  2.0G  4.0K  2.0G   1% /var/lock
/dev/sda1              99G   44G   55G  45% /host

``````
prs@ubuntu:~$ sudo mount /dev/sda5 /mnt
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
 
```

---

### Post by srs5694 on 2011-08-09
When an OS mounts a filesystem (assigning it to a directory in Linux or giving it a drive letter in Windows, for instance), the filesystem is marked as being in use. When the OS unmounts a filesystem or shuts down, the filesystem is cleaned up and marked as *not* being in use. If the OS crashes or is shut down improperly, this cleanup and marking as not being in use doesn't occur, which is normally a signal to the OS to run low-level disk utilities on the filesystem to repair any possible damage. Unfortunately, Linux lacks real tools to do this with NTFS, which is why a crash or improper shutdown can prevent Linux from mounting NTFS volumes, and why I recommended doing checks in Windows.

Your df output reveals that only /dev/sda1 is mounted, so your other NTFS partitions are not mounted in some unusual location.

The output of the "mount" command is extremely informative, but unfortunately, I don't know exactly what the real problem is. Basically, something other than the "mount" command you issued is already using the partition. Perhaps this is an earlier mount operation that's hung (say, because of disk errors); or maybe it's a disk check operation. Please post the contents of your /etc/fstab file; if your NTFS partitions are listed there and flagged as eligible for disk checks on system boot, it's conceivable that's causing the problem.

At this point, my best guess is that there are subtle filesystem errors or the disks are marked as being in-use, despite your checking them from Windows. Unfortunately, I'm not all that knowledgeable about Windows disk utilities, but if I'm not mistaken, there are multiple ways to perform disk checks, and some of them are more thorough than others. You might therefore look into this; perhaps you can find a way to do a more thorough check in Windows and be sure you shut down properly before restarting Linux.

---

### Post by coffeecat on 2011-08-09
@medusa93, just a couple of other thoughts.

When you post the contents of your /etc/fstab file as srs5694 suggests, please also post the output of this terminal commmand:

```
mount
```

That's it - just "mount". I doubt whether it will tell us much more than "df -h" but let's see it for completion.

I've often seen it said that one needs to run chkdsk three times in certain circumstances. I honestly don't know whether this is based on logic or is simply some sort of urban myth, but it might be worth trying. It certainly won't do any harm. Run chkdsk x3 on each of the three named partitions, and also on the unlabelled ~78GB one that appears as sda8 in Ubuntu.

If all else fails I have one idea, but I'm not suggesting you should do this just yet. I'm simply airing the thought and would be interested in your, srs5694's and Rubi1200's reactions. 

Based on the theory that there might be subtle filesystem irregularities in the four NTFS partitions that Windows tolerates but Ubuntu does not, you could back up all data on those four partitions and then reformat them using Ubuntu's Gparted, not Easus partition manager. That may seem counter-intuitive to use a Linux tool to create a Microsoft filesystem, but in my experience Windows (XP, Vista and Windows 7) is happy to use a NTFS partition created with Gparted. And, with a newly created NTFS filesystem, your wubi Ubuntu should have no trouble seeing and mounting it.

As I said - don't do anything yet. It's a drastic step to take, but one worth thinking about.

---

### Post by srs5694 on 2011-08-09
> **coffeecat said:**
> If all else fails I have one idea, but I'm not suggesting you should do this just yet. I'm simply airing the thought and would be interested in your, srs5694's and Rubi1200's reactions. 

Based on the theory that there might be subtle filesystem irregularities in the four NTFS partitions that Windows tolerates but Ubuntu does not, you could back up all data on those four partitions and then reformat them using Ubuntu's Gparted, not Easus partition manager. That may seem counter-intuitive to use a Linux tool to create a Microsoft filesystem, but in my experience Windows (XP, Vista and Windows 7) is happy to use a NTFS partition created with Gparted. And, with a newly created NTFS filesystem, your wubi Ubuntu should have no trouble seeing and mounting it.

As I said - don't do anything yet. It's a drastic step to take, but one worth thinking about.

I had a similar thought. I didn't mention it because it is, as you say, rather drastic, and it's probably better to try other things first, like more thorough (or more, if that has the same effect) disk checks with CHKDSK or similar tools. As a last resort, it's very likely to work. One caveat: Do the backups and restores in Windows, since Windows understands the NTFS permissions but Linux doesn't.

---

### Post by medusa93 on 2011-08-10
I can back up these partitions in windows. Should I then format these partitions in Ubuntu ?
```
prs@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/prs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=prs)
/dev/sda5 on /mnt/win2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

``````
prs@ubuntu:~$ your /etc/fstab file
your: command not found

```

---

### Post by Elfy on 2011-08-10
From a terminal 

```
cat /etc/fstab
```

will show your fstab - paste what that shows - please use code tags.

---

### Post by coffeecat on 2011-08-10
Aha!. We're onto something.

> **medusa93 said:**
> ```

/dev/sda5 on /mnt/win2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

Your sda5 partition is mounted on a mountpoint in the /mnt folder. This is why it isn't being seen in the left Places pane of Nautilus. This doesn't explain why your sda6,7 and 8 partitions are not showing, but it's a start. We need to see your /etc/fstab file.

> **medusa93 said:**
> ```
prs@ubuntu:~$ your /etc/fstab file
your: command not found

```

Sorry for not being clear. "Your" is not a command. We meant post your /etc/fstab file as in your = not mine. :) Two ways of doing this. Open a nautilus windows -> File system. Then open the /etc folder and double-click on the fstab file. Copy and paste it into your post.

Or... from a terminal:

```
cat /etc/fstab
```

Copy and paste the output.

**EDIT**: Also - when you have a Nautilus window open showing "file system", open the /mnt folder, then the win2 folder. Tell us what you see.

---

### Post by srs5694 on 2011-08-10
Your information in post #30 includes the following:

```
/dev/sda5 on /mnt/win2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```This suggests that one of your partitions is mounted at /mnt/win2. Check there to see if there are any files present.

Edit: I didn't see coffeecat's post in #32, which says the same thing....

---

### Post by medusa93 on 2011-08-10
@coffeecat and srs5694. Apologies are due to you. The sda5 mounted with win2 was done by a colleague of mine who offered to fix this problem. But the roundabout solution he advised is way outside my league. I apologize unreservedly for messing up while receiving help from you. 
I have rebooted the system and now I cant see the sda5. I have run the command again from the terminal
```
prs@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/prs/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=prs)

```

```
prs@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
prs@ubuntu:~$ 


```

---

### Post by coffeecat on 2011-08-10
> **medusa93 said:**
> @coffeecat and srs5694. Apologies are due to you. The sda5 mounted with win2 was done by a colleague of mine who offered to fix this problem. But the roundabout solution he advised is way outside my league.

No problem. In fact the episode has provided useful information. At least we know that sda5 is mountable by your wubi installation, although we don't yet know whether the files are viewable.

Your /etc/fstab shows that none of those partitions are being mounted by means of the fstab file, so that is useful information too.

Let's go back and build on what your colleague did. This could be a useful exercise. Open a terminal, and:

```
sudo mount /dev/sda5 /mnt/win2
```

This is similar to the command srs5694 posted earlier, but should work now that sda5 is not already mounted. Post any error messages, if you get any. If you are simply returned to the terminal prompt, then that means that sda5 (your "Suneel" partition) has been mounted successfully. Now open a Nautilus window and click on "File system". Open the /mnt folder, and now the win2 folder. Do you see the contents of your "Suneel" partition?

If you do, there are two options that I can think of. Either you can edit your /etc/fstab file (we'll tell you what to do) so that the partitions are automounted for you on bootup. (I think this is where your colleague was going.) Or you can think about reformatting the NTFS partitions as we discussed earlier. No need to make a decision immediately. Let's see if you see the contents of the partitions after you mount it from the terminal.

---

### Post by medusa93 on 2011-08-11
I have had an error message when I booted into Ubuntu. I dont know whether that has any relevance to the problems that I am experiencing.
Right after I chose Ubuntu as the boot from Grub, I had this error message
"Errors were found while checking the disc drive for/
Press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery"
I chose "I" first and then I had the same error message on reboot and that time I chose "F" and thereafter I haven't had that error message

---

### Post by medusa93 on 2011-08-11
I ran the command sudo mount /dev/sda5 /mnt/win2 and that enabled me to open "Suneel" and access the contents. The partition is visible after reboot only after running the command once again

---

### Post by coffeecat on 2011-08-11
> **medusa93 said:**
> I ran the command sudo mount /dev/sda5 /mnt/win2 and that enabled me to open "Suneel" and access the contents. The partition is visible after reboot only after running the command once again

That's good. That's what I hoped you would see. Give me an hour or so and I'll post you a howto for editing your /etc/fstab to get all four of those partitions mounted every time you boot up. If, in the meantime, someone else posts back suggesting you use the application ntfs-config, I advise you not to. It was a good idea but has not been maintained since being first developed in about 2005-6. It has some significant bugs and can do the most undesirable things on occasion.

We also need to consider the filesystem error you saw when booting up, particularly in view of the Windows errors you described earlier in the thread. Do the following. Boot up Ubuntu and open the disk utility application. Select your internal hard drive in the left pane and look for SMART data in the right pane. It can sometimes be a minute or so before this appears. Try running one or more of the SMART self-tests. You need to exclude a failing hard drive.

---

### Post by coffeecat on 2011-08-11
@medusa93, here's a howto to have all those four NTFS partitions mounted on bootup and accessible all the time. Open a terminal and create the mountpoints with these commands:

```
sudo mkdir /media/Suneel
sudo mkdir /media/Added_Programs
sudo mkdir /media/Music
sudo mkdir /media/sda8
```

A couple of comments. I have suggested creating mountpoints in /media rather than in /mnt, which is what your colleague did. The /mnt folder is the traditional place for mounting devices but has the disadvantage that the mounted partition does not show up in the left pane of Nautilus and you have to navigate there via "File system" the way I showed you before. Mounting in /media causes the mounted volumes to show up not only in Nautilus, but as desktop icons and in the Unity launcher if you are using the Unity desktop. The desktop icons can be seen as useful or as a nuisance depending on your preferences. We can fine tune this later, but let's get it working first.

Also - I have suggested using the partition labels for the name of the mountpoints for sda5, 6 and 7 as this makes things simpler, but I have changed "Added Programs" to "Added_Programs" as spaces in partition labels cause complications. The mountpoint for sda8 I have suggested to be /media/sda8 only because there is no label for that partition. Again, we can tidy this up later.

Now to edit your /etc/fstab file:

```
gksudo gedit /etc/fstab
```

Be careful what you do here. You have the /etc/fstab file open in a text editor with root privileges. A mistake could make your system (temporarily) unbootable. Double-check everything. Edit the file so that it looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

UUID=F29C05F49C05B45F     /media/Suneel          ntfs     defaults   0 2
UUID=F218FCF418FCB8A5     /media/Added_Programs  ntfs     defaults   0 2
UUID=38B095E7B095AC3E     /media/Music           ntfs     defaults   0 2
UUID=01CC395A8B235450     /media/sda8            ntfs     defaults   0 2 
```

The first ten lines are exactly as you posted them - that is, as your /etc/fstab appears at the moment. Don't change anything there. Simply add the four lines I have given you. Copy and paste from this post to avoid typos and include a blank line before the 4 lines as shown - this is simply to make things easier to read.

Save the edited file and close gedit, the text editor. Now:

```
sudo mount -a
```

Open a Nautilus window and you should see all four partitions listed in the left pane. Open each one. Do you see the contents? You'll also see eject icons for each partition, but these won't work with partitions mounted this way. If this has all worked, the partitions will be mounted each time you boot up. If it has worked without error, try a restart to be sure.

Post back with what you see. Also - It would be good to tidy up the mountpoint for sda8. I would suggest adding a meaningful partition label. Post back what you would like for this and I will be able to tell you what to do.

---

### Post by medusa93 on 2011-08-11
```
prs@ubuntu:~$ sudo mkdir /media/Suneel
[sudo] password for prs: 
prs@ubuntu:~$ sudo mkdir /media/Added_Programs
prs@ubuntu:~$ sudo mkdir /media/Music
prs@ubuntu:~$ sudo mkdir /media/sda8
prs@ubuntu:~$ gksudo gedit /etc/fstab

(gedit:1986): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.5CX0ZV': No such file or directory

(gedit:1986): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1986): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.QSI6ZV': No such file or directory

(gedit:1986): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1986): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.X992ZV': No such file or directory

(gedit:1986): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
prs@ubuntu:~$ 

```I worried that I might have done it wrong some how. But after running
     
     ```
sudo mount -a 
```I found that all the partitions have appeared on the desktop and the Nautilus borwser. I can open and access all contents. Thanks a lot.
Now a few inevitable questions
1 I did not understand how to follow this advice

> Do the following. Boot up Ubuntu and open the disk utility application.   Select your internal hard drive in the left pane and look for SMART  data  in the right pane. It can sometimes be a minute or so before this   appears. Try running one or more of the SMART self-tests. You need to   exclude a failing hard drive.I could not figure out where the disk utility appication might me
2.What about my CD drive ?
3.Should I now change the label of sda8 ? Should I do it in Windows or Ubuntu. What about the saved gedit file ? Will the changed partition label make it unmountable without further fixes?

---

### Post by coffeecat on 2011-08-11
> **medusa93 said:**
> I worried that I might have done it wrong some how.

You often get those blood-curdling messages when running a graphical application as root (that is, with gksudo). It's just the system telling you it's trying to update some logs in the /root folder and failing. You can ignore it.

> **medusa93 said:**
> But after running
     
     ```
sudo mount -a 
```I found that all the partitions have appeared on the desktop and the Nautilus borwser. I can open and access all contents. Thanks a lot.

That's excellent news. 

> **medusa93 said:**
> I could not figure out where the disk utility appication might me

We never did determine whether you are using the Unity desktop in 11.04 or the classic gnome desktop. The distinguishing feature of Unity is the launcher with application icons down the left side of the screen. With classic gnome, you will be able to see "Applications - Places - System" menus in the top panel at the left.

To open Disk Utility in Unity, tap the Windows key, **or** click on the Ubuntu logo top left. The dash will open. Start typing "disk  " and the system should offer you the Disk Utility application. Click on it and Disk Utility will open. Then follow my instructions in the earlier post to see the SMART data.

If you are using classic gnome you will find Disk Utility in the System > Administration menu, if I remember correctly.

> **medusa93 said:**
> 2.What about my CD drive ?


This will show up as a desktop icon if you insert a CD or DVD, and will also show in the left pane of Nautilus, but only if there is a disc in the drive. You'll also get prompted for what you want to do with it, depending on whether it's an audio CD, video DVD, black disk or whatever. There is a way of getting a CD drive icon visible in Nautilus but it's pointless unless there's a disc in the drive when the system will do what is necessary. 

> **medusa93 said:**
> 3.Should I now change the label of sda8 ? Should I do it in Windows or Ubuntu.

The easiest way is in Windows. Simply right-click on it in My Computer and choose "rename". Then boot into Ubuntu and see if the desktop icon is showing your label rather than "sda8".

> **medusa93 said:**
>  What about the saved gedit file ? Will the changed partition label make it unmountable without further fixes?

That should be fine. When I posted earlier I was anticipating that you might have to re-edit /etc/fstab, but I realise now that you won't. The system will mount your sda8 partition to /media/sda8 but *should* use the partition label under the desktop icon. If it doesn't work as it should after you've renamed it in Windows, just post back and we'll fix it.

---

### Post by medusa93 on 2011-08-11
After reboot I still have all the partitions on the desktop and the Nautilus browser. However the renamed sda8 in Windows is not showing up renamed in Ubuntu. 
I am running a Unity desktop and I could see the Disk Utility icon but clicking it did nothing.
The CD drive is not being recognized. I tried three different movie CDs.
There was an error message on reboot after Grub boot menu and it vanished quickly  without any input from me. I had no time to take it down. But it had the  words "unrecognized" "kill it".  I think it had words like "drive" as  well.

---

### Post by coffeecat on 2011-08-11
> **medusa93 said:**
> After reboot I still have all the partitions on the desktop and the Nautilus browser. However the renamed sda8 in Windows is not showing up renamed in Ubuntu.

OK. Post the name of the label you have applied and I'll describe what you need to do. 

> **medusa93 said:**
> I am running a Unity desktop and I could see the Disk Utility icon but clicking it did nothing.

Where did you see the Disk Utility icon? In the dash when you typed "disk" in? Or in the launcher? I'm concerned that it won't run when you click the icon. This is not the first inexplicable thing you've observed, which is all the more reason to run disk utility and a SMART test. You can run it from the terminal. Open a terminal, and:

```
palimpsest
```

If you get an error, post the error. Otherwise see what the SMART data tells you.

> **medusa93 said:**
> The CD drive is not being recognized. I tried three different movie CDs.

Were these commercial DVDs? It's just possible that the system won't recognise them until you install libraries for decrypting them. Try an audio CD and/or a data CD/DVD and tell us what happens. I don't want to investigate this any more deeply until you've been able to check that SMART data, in case there is a hard drive issue causing all these problems.

> **medusa93 said:**
> There was an error message on reboot after Grub boot menu and it vanished quickly  without any input from me. I had no time to take it down. But it had the  words "unrecognized" "kill it".  I think it had words like "drive" as  well.

I'm getting some sort of message too when I boot wubi, again too quickly to read. It's possible that this is just a harmless phenomenon in wubi. Or again, it may indicate a hardware problem. Let's concentrate on getting that fourth partition mounted tidily and the SMART test for now.

Or perhaps my learned friends may have something to add??!! :cough: :cough: :p

---

### Post by medusa93 on 2011-08-11
```
prs@ubuntu:~$ palimpsest
**
libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
Aborted
prs@ubuntu:~$ 


```I get the disk utility by clicking the ubuntu icon and typing in the search box. I have attached a photo taken with my mobile camera(screen shot did not work here)

I have named sda8 as "Miscellaneous"

---

### Post by coffeecat on 2011-08-11
Let's deal with this first:

> **medusa93 said:**
> I have named sda8 as "Miscellaneous"

Open a terminal, and:

```
sudo mkdir /media/Miscellaneous
```

Now:

```
gksudo gedit /etc/fstab
```

Change this last line:

```
UUID=01CC395A8B235450     /media/sda8            ntfs     defaults   0 2
```

To this:

```
UUID=01CC395A8B235450     /media/Miscellaneous            ntfs     defaults   0 2
```

Make no other changes. Save the edited file and close gedit. Now, two terminal commands:

```
sudo umount /dev/sda8
sudo mount -a
```

The desktop icon for sda8 will disappear with the first command (and that's umount, not unmount) and reappear with the new label (hopefully) with the second. Post back if there are any problems.

Now to this:

> **medusa93 said:**
> ```
prs@ubuntu:~$ palimpsest
**
libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)
Aborted
prs@ubuntu:~$ 


```

Yes, the screenshot is what I expected, and your terminal output after "palimpsest" explains why you can't open it from the GUI. Although, at the moment, I don't know what to do about that error. What I can say is that you are getting more and more unexpected and unusual errors, which makes examining the SMART data imperative. But you can't do that from Disk Utility.

Two ideas. Do you know what make of hard drive you have? Have a look on the maker's website and see if you can download some Windows-based diagnostic utility for the hard drive. This should include SMART testing. It really doesn't matter what OS you use. That HD needs testing.

Second idea. Since you installed a wubi installation, you may not have the Ubuntu 11.04 ISO image file. If you can't find a Windows based utility, the best thing would be to prepare a live Ubuntu CD or live Ubuntu USB pendrive from the ISO. If you don't have it, you would need to download it. Then you could run Ubuntu live from the CD or USB and run Disk Utility from that. Post back if you need help with that.

---

### Post by medusa93 on 2011-08-12
I ran the commands for renaming sda8. The change in label did not occur with the commands alone and I was distracted with other calls to take down all the error messages. But there was lot of "cannot"s. I proceeded with unmounting sda8.  I rebooted and the name had changed to Miscellaneous

My hard disk is 488GB Western Digital WDC WD5000BEVT-00A0RT0 (SATA). The site for Western Digital has lot of softwares of testing hard disk. But backing up the system is mandatory before all that stuff. My most recent back up is three weeks old. So I need to back up again. My preferred method of back-up is creating images of the partitions on to an external hard drive as xml files

I had a prior installation of Ubuntu 10 on my laptop installed with a CD and I did not have half the troubles like the ones I am having now. The problem that time (and contnues even now) was with the Windows. It has "blue screens of death" out of the blue. (Microsoft office 2010 is the only reason for me to remain on Windows XP) I took the laptop to  the service centre and they reinstalled XP after formatting all the drives. (That's how I lost my Ubuntu 10) After all the windows updates, the blue screens started reappearing. 

I have downloaded the iso of Ubuntu 11. Can I run disk check with that ?

---

### Post by coffeecat on 2011-08-12
> **medusa93 said:**
> I had a prior installation of Ubuntu 10 on my laptop installed with a CD and I did not have half the troubles like the ones I am having now. The problem that time (and contnues even now) was with the Windows. It has "blue screens of death" out of the blue. (Microsoft office 2010 is the only reason for me to remain on Windows XP) I took the laptop to  the service centre and they reinstalled XP after formatting all the drives. (That's how I lost my Ubuntu 10) After all the windows updates, the blue screens started reappearing. 


Yes, all this is what is worrying me. These could be symptoms of a failing hard drive, which might explain the odd problems you've been experiencing in Ubuntu.

> **medusa93 said:**
> I have downloaded the iso of Ubuntu 11. Can I run disk check with that ?

Yes, burn a CD with the ISO, boot up with it and select "try Ubuntu" to get the live desktop. Open the disk utility application and look for SMART data and run the SMART self-test. Disk utility should run OK from the live CD and be able to scan your internal drive. If my theory of HD failure is correct, this could explain why disk utility errors out when run from your hard drive installation.

---

### Post by medusa93 on 2011-08-12
I will test from live CD. Meanwhile how do I get rid of the mounted partitions from the desktop. I would rather not have it there
I have never done a powerpoint presentation on a projector from Ubuntu. Think I am going to have a problem with that ? Unfortunately it is possible to test the presentation on the projector only just before my presentation

---

### Post by coffeecat on 2011-08-12
> **medusa93 said:**
> Meanwhile how do I get rid of the mounted partitions from the desktop. I would rather not have it there

Open the gconf-editor from a terminal with:
```
gconf-editor
```

Now, apps > Nautilus > desktop. Untick the volumes_visible box. They will not be shown on the desktop but will still be in the launcher. Unfortunately, USB drive icons will now not show on the desktop but they will be visible in the launcher.

> **medusa93 said:**
> I have never done a powerpoint presentation on a projector from Ubuntu. Think I am going to have a problem with that ? Unfortunately it is possible to test the presentation on the projector only just before my presentation

Powerpoint and projectors in Ubuntu are not in my area of experience. You'd be better off starting a separate thread for that with a descriptive title in order to attract the notice of members who can help.

---

### Post by medusa93 on 2011-08-13
I was able to get rid of the partition icons from the desktop. Having the icon appear on the desktop was nice when I wanted to connect to to my mobile via bluetooth. 

Meanwhile I tried to boot from an Ubuntu 11 install CD and chose "Try Ubuntu". The screen did not advance from this point for nearly half an hour and I terminated the session. When I try four hours later the story is no different. Oddly enough, I was able to connect to the WiFi and continue browsing the internet using firefox. Never been able to do that with a Windows boot disk!

---

### Post by abhimanyu singh on 2011-08-13
> **medusa93 said:**
> I got the error message and it required some video skills. This error message is right after I choose Ubuntu as the OS and before the Grub menu appears and verbatim, it reads

Try (hd0,0): NTFS5:error: "prefix" is not set

I dont know wh ether that means that there is something wrong with the disk. In my Windows XP Home I can see and use all my disks
hey how did you say that the name of the folder is suneel and the memory allocated to sda8 is 79.4gb.

---

### Post by medusa93 on 2011-08-13
> **abhimanyu singh said:**
> hey how did you say that the name of the folder is suneel and the memory allocated to sda8 is 79.4gb.
Sorry I didn't get that question

---

### Post by Elfy on 2011-08-13
> **abhimanyu singh said:**
> hey how did you say that the name of the folder is suneel and the memory allocated to sda8 is 79.4gb.

Please do not hijack other peoples threads with random statements. If you have support requirements please post your own threads.

---

### Post by medusa93 on 2011-08-14
I finally booted using the ubuntu 11 boot CD. More problems. When booted in via the boot CD, my regular partitions are not seen. Disk utlitiy again does nothing. (I used my Ubuntu boot CD on my desktop and the disk utility works there)
I tested my hard disk with Hitachi drive fitness test from the boot. The test came back with the Disposition code 0x00, meaning there is no error.
At this point, I am without any clues. My regular Ubuntu installation now allows me to access partitions and I am willing to let it be. However the CD drive is not working. Can anything be done about that

---

### Post by coffeecat on 2011-08-14
> **medusa93 said:**
> When booted in via the boot CD, my regular partitions are not seen.

Do you mean from a nautilus window? If so, that is to be expected. It's probable that something in the way Easus created those partitions is preventing nautilus from seeing them.

Open Gparted partition editor in the live CD session. What does this show? Can you post a screenshot of it? (Press alt+Printscreen to get a screenshot of an open window.) Take care not to do anything in Gparted while you have Gparted open. It is a fully featured partition editor.

> **medusa93 said:**
>  Disk utlitiy again does nothing. (I used my Ubuntu boot CD on my desktop and the disk utility works there)

I don't follow you. Does Disk Utility in the live session show you the SMART data?

> **medusa93 said:**
>  However the CD drive is not working. Can anything be done about that

Not working? If you can boot into the live CD session, then the CD drive is working.

---

### Post by medusa93 on 2011-08-14
Sorry. My previous post was not clear enough

[LIST=1]
[*]When I boot in with live CD I am not able to see the disk partitions. I have opened Gparted as suggested and created a screen-shot. I have also made a screen-shot with the Nautilus while on live CD
[*]When I boot through the Ubuntu installed on my laptop, any CD/DVD that I load in my CD drive is not accessible.
[*]The disk utility even while on live CD does nothing on my laptop. However, when I tested the live CD on another of my systems running windows XP Home, the disk utility on live CD works fine. (Just proving once again that the live CD is alright, my laptop is messed up from unknown causes)
[/LIST]

---

### Post by coffeecat on 2011-08-14
Thanks for the clarification.

I am truly mystified why you are getting multiple problems with that laptop. The Hitachi application has probably excluded the possibility of a hard drive failure. Nevertheless, you have experienced several unrelated issues in Ubuntu. If it was just the inability to see partitions in Nautilus, which is where the thread started, then I'd be happy to conclude that this is because of some oddity in the way Easus created the partitions. Indeed, this might still be so. But you are also seeing issues with Disk Utility and your CD drive in Ubuntu. You are also getting odd things happening with Windows.

This is really scraping the bottom of the barrel, but it's just possible that there is an inconsistency in your NTFS C: partition filesystem. This could conceivably affect Ubuntu running under wubi because your wubi install is a virtual drive contained as a file in the Windows partition. I suggest you boot into Windows and run a chkdsk. There's a GUI way of doing that but I've forgotten the details.

I'll have another look through the thread (not now - tomorrow) and see if I can think of anything else, but I may very well be out of ideas. I don't know whether anyone else who has contributed to the thread may have any suggestions.

---

### Post by medusa93 on 2011-08-15
I trashed the Windows partitions
Here is what I did.

[LIST=1]
[*]Created back up images of all partitions in windows
[*]Used LiveCD of  Ubuntu, used Gparted and created one primary partition and four logical partitons
[*]Now all partitions are seen in Nautilus and Disk Utility is usable and shows green check signal = disc is healthy. Screenshots attached
[*]Reinstalled Windows using the Windows disc
[*]Reimaged Windows OS on to the C drive = Windows is working
[*]Restored the contents of all the other partitions
[*]Installed Wubi
[*]Rebooted and chose Ubuntu
[*]While installing Ubuntu the installer stopped and mouse is unresponsive for 20 minutes
[*]Shut down
[*]Tried installing Ubuntu again
[*]Same as event 9
[*]Shutdown and tried installation after 3 hours and I get error messages.
[/LIST]
Now these are the issues

[LIST=1]
[*]What do I do about the message "No root file system is defined. Please correct this from the partition menu".
[*]If I have to start a new thread for this, I will do so
[/LIST]

---

### Post by medusa93 on 2011-08-16
@coffeecat. Thanks for all the help.
Even though I did not understand the error message "No root file system is defined. Please correct this from the partition menu", while installing Ubuntu, I uninstalled Ubuntu using Windows Add/Remove programs. I downloaded Wubi once again and attempted to install again. Everything went through well this time with no error messages on install. Now my Nautlilus displays all the partitions, CD drive works. Screenshots attached. Even though I understood very little of all that went wrong, almost all my intital problems appears to be fixed. 
So with your permission I will mark this thread as solved

---

### Post by coffeecat on 2011-08-16
You're very welcome, and I'm glad you've got a working wubi installation at last.

I think we'll have to write off yesterday's wubi install - the one that gave you "no root system defined" - as just one of those things. Something went wrong in the install process, I guess.

Interesting and gratifying that now you've created partitions with Gparted, these can be seen in Nautilus. I'm sure that Windows will have no problem using the NTFS ones. That has certainly been my experience.

Good luck! :)

---

