---
title: "Cannot boot Windows anymore after installation to USB drive"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Grratch on 2010-11-28
I just installed Ubuntu 10.10 to a USB hard drive (Seagate FreeAgent GoFlex 500GB) but I can no longer boot Windows 7 from the internal SATA drive on my computer nor can I boot Ubuntu from the USB drive.

Booting from the CD and using the "Try Ubuntu" option, I can see my Windows 7 files but how do I boot either operating system?  :confused:  

Thanks in advance for any help.

---

### Post by zipteye on 2010-11-28
Do you just see a text screen that says Grub ?
If it does I'm guessing your MBR got hosed.
Check your boot order settings if not.
 
If the windows MBR is hosed then you need a recovery disc so you can go to the recovery console and type /Fixmbr.
 
If you disconnect the USB drive, does Windows boot?

---

### Post by Grratch on 2010-11-28
Yes, if I try to boot without the cd, I get a text screen that says grub>  What is an MBR? 

Thanks.

---

### Post by takisan on 2010-11-28
MBR= Master Boot record: First thing that the BIOS looks at after doing check stuff. The MBR points to GRUB in the linux partition, which loads up Linux or Windows.

---

### Post by Grratch on 2010-11-28
Ok.  Forgot to answer the other part of your question - when I disconnect the USB drive, Windows does not reboot.  Am I still looking at trying to find the recovery disc?

---

### Post by wilee-nilee on 2010-11-28
> **Grratch said:**
> Ok.  Forgot to answer the other part of your question - when I disconnect the USB drive, Windows does not reboot.  Am I still looking at trying to find the recovery disc?

```
bootrec.exe /fixmbr 
```
from the repair command line, vista or W7.

other wise,
So from a booted live Ubuntu cd or thumbdrive lets make this easiest lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by zipteye on 2010-11-28
> **Grratch said:**
> Ok. Forgot to answer the other part of your question - when I disconnect the USB drive, Windows does not reboot. Am I still looking at trying to find the recovery disc?
 
Or windows install disk.
When it starts choose 'Repair'.
You want the recovery console
Then type  bootrec.exe /fixmbr
 
But it would be more interesting to see what the results are from wilee-nilee's instruction.

---

### Post by wilee-nilee on 2010-11-28
> **zipteye said:**
> Or windows install disk.
When it starts choose 'Repair'.
You want the recovery console
Then type  bootrec.exe /fixmbr
 
But it would be more interesting to see what the results are from wilee-nilee's instruction.

That just reloads the mbr with the ms bootloader the cli is your friend.;)

Your trying to reload the MS bootloader correct?

---

### Post by Grratch on 2010-11-28
How do I get to the repair command line in W7 if I cannot boot the OS?   Anyway, here is the results of the bootscript readout.  Thanks for your  patience:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,787,924    16,787,862  1b Hidden W95 FAT32
/dev/sda2    *     16,787,925   798,205,589   781,417,665   7 HPFS/NTFS
/dev/sda3         798,205,590 1,953,520,064 1,155,314,475   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   939,911,167   939,909,120  83 Linux
/dev/sdb2         939,913,214   976,771,071    36,857,858   5 Extended
/dev/sdb5         939,913,216   976,771,071    36,857,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C1CB6951CB66A22                       ntfs       RECOVERY                      
/dev/sda2        904254E64254D298                       ntfs       WIN7                          
/dev/sda3        4AC2567EC2566E67                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c4e8db4e-5242-468c-a2ce-bd1f458ad838   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        48f8900b-4579-4093-8fe6-79bd46a7cf5c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/WIN7              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/c4e8db4e-5242-468c-a2ce-bd1f458ad838 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c4e8db4e-5242-468c-a2ce-bd1f458ad838 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c4e8db4e-5242-468c-a2ce-bd1f458ad838
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5c1cb6951cb66a22
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 904254e64254d298
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=48f8900b-4579-4093-8fe6-79bd46a7cf5c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  55.9GB: boot/grub/core.img
 309.5GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.35-23-generic-pae
  55.9GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.1GB: initrd.img
  55.9GB: vmlinuz
```

---

### Post by wilee-nilee on 2010-11-28
So sda is windows=internal hard drive you want it's bootloader back correct?

sdb is the external with Ubuntu and it is missing a bootloader in its MBR is this all all correct?

also /fixmbr is XP

---

### Post by Grratch on 2010-11-28
What you've stated appears to be correct:
sda is windows internal hard drive - I want it's bootloader back.
sdb is the external drive with Ubuntu and I think it is missing a bootloader in its MBR.

Am desperately looking for the Windows install disc for this computer to run the MBR repair.  Will let you know soon.  Thanks.

---

### Post by wilee-nilee on 2010-11-28
So download this W7 recovery disc.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

burn it to a cd and follow these instructions just run the highlighted command.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

To load the external with grub2 boot a live Ubuntu cd and run these two commands.

```
sudo mount /dev/sdb1 /mnt
```

then

```
sudo grub-install --root-directory=/mnt/ /dev/sdb


```

reboot to the Ubuntu install and run sudo update-grub.

So you will have W7 in that external grub which is okay if you don't want it remove the os prober from synaptic

I would do the W7 first probably without the external plugged in just to be on the safe side.

---

### Post by Grratch on 2010-11-29
Have tried the above.  Nothing appears as you've listed.

The recovery disc ran a complete recovery operation.  Windows now boots but cannot open anything - all data has been moved to disc D: now.  Never saw a prompt for Language selection or Repair as described.

Can no longer get to data on D:

System is hosed.  Cannot get to programs or data anymore.

Worst decision ever to try to use Ubuntu.  I am so totally screwed.

Not sure what I'm going to do now.  Financial data - inaccessible.  Kid's homework - inaccessible.  Access databases - inaccessible.  Everything visible, but inaccessible.  

I am so totally screwed.  Is there anything I can do to recover from this disaster?

---

### Post by wilee-nilee on 2010-11-29
> **Grratch said:**
> Have tried the above.  Nothing appears as you've listed.

The recovery disc ran a complete recovery operation.  Windows now boots but cannot open anything - all data has been moved to disc D: now.  Never saw a prompt for Language selection or Repair as described.

Can no longer get to data on D:

System is hosed.  Cannot get to programs or data anymore.

Worst decision ever to try to use Ubuntu.  I am so totally screwed.

Not sure what I'm going to do now.  Financial data - inaccessible.  Kid's homework - inaccessible.  Access databases - inaccessible.  Everything visible, but inaccessible.  

I am so totally screwed.  Is there anything I can do to recover from this disaster?

That shouldn't of happened the script read correctly so can you boot a Ubuntu cd and run the script if needed, but that booted Ubuntu will get you to all your W7 for backup. Ubuntu will read the W7 partitions. 

If things did not appear as they should why didn't you shut it down and post? Did you notice the http link at the bottom of the commands as to what you should be seeing on booting the W7 recovery disc.

---

### Post by Grratch on 2010-11-29
Sorry.  Am trying my best here.  I understand that you listed some things I should have seen, however, this is rarely the case for anything I've ever done.  Thought it was a variation so did not think to shut down and post.  Did not notice any http link as there were no commands, just a run of the Recovery program.  Never got a command prompt.

---

### Post by wilee-nilee on 2010-11-29
> **Grratch said:**
> Sorry.  Am trying my best here.  I understand that you listed some things I should have seen, however, this is rarely the case for anything I've ever done.  Thought it was a variation so did not think to shut down and post.  Did not notice any http link as there were no commands, just a run of the Recovery program.  Never got a command prompt.

I suspect your okay lets just see the script again. **when you say recovery program could you be more specific.** what was this recovery and how did it happen?

---

### Post by Grratch on 2010-12-01
Ok, a few days later and I'm back. My brother-in-law was able to help. He was able to switch the boot flag back to the hard drive partition I wanted to boot from. All is now well with Windows and nothing's been lost. :D
 
The next problem is, when I try to boot from the new external HD that has Ubuntu installed on it, all I get is a black screen with a flashing cursor in the upper left.
 
btw to wilee-nilee: thanks for talking me off the ledge the other night.

---

### Post by C.S.Cameron on 2010-12-01
This sort of thing never happens if you disconnect your internal hard drive before installing to USB drive.

---

