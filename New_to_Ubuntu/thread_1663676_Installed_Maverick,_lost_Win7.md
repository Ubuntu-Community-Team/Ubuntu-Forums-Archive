---
title: "Installed Maverick, lost Win7"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by zlapidus on 2011-01-10
Hello,

On a new system where I had been using Windows 7 for a while, I decided to install Ubuntu on a second hard drive.

Installed Ubuntu, and it worked great, except GRUB doesn't show up, and when I held down shift I observed that Windows 7 was not in the list. Odd, as on my old system, Windows 7 was listed when I installed Ubuntu before.

Odder still, is when I went to specifically boot the hard drive Win7 was on by putting its priority ahead of Ubuntu's drive in the BIOS, nothing happens. Just a blinking cursor after Verifying DMI Pool Data. I ran os-prober and grub-ubdate, but no dice, no Win7 listed in GRUB.

Unsure what to do, and possessing much more daring than discression, I figured that the MBR might be hosed so I put in my Win7 recovery cd and ran "bootsect /nt60 c: mbr" I triumphantly rebooted and asked my bios to boot off window's hard drive first, and expected to see windows. Now I get "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." Yikes.

When I returned to my bios and returned the Ubuntu drive to have the highest boot priority, I get into Ubuntu fine. However, running os-prober and grub-update aren't getting me anywhere.

Anybody have any ideas? I would love to hear them and appreciate any help.

And here's another tidbit of information, if it would be of any help in this problem:
The drive that I installed Win7 on 5 months ago is, according to the bios, the Channel 2 Master. There was nothing on the drive that I later installed Ubuntu on yesterday, which is the Channel 0 Master in the bios. Is this why everything is messed up?

---

### Post by Bucky Ball on 2011-01-10
Release 10.10?

Open a terminal (Applications >Accessories >Terminal) and type this in:

```
sudo update-grub
```When you run this keep an eye out for the process picking up Windows entries.

Reboot, get to grub. Windows there?

---

### Post by zlapidus on 2011-01-10
Thanks for the reply. Unfortunately before I got your message, I tried using the Windows recovery CD again and ran the a fixmbr command.

Now when I boot off the Ubuntu drive, it says Missing operating system. But if I remember correctly, that's a message from the Windows bootloader, not a GRUB message. This suggests to me that Windows tried putting its MBR on the Ubuntu drive and not the Windows drive. Shoot. 

Since I can't boot into Ubuntu, I was unable to try your suggestion. I imagine now I'll need my Ubuntu install CD.

---

### Post by zlapidus on 2011-01-10
Sorry, yes, in response to your post, I am running 10.10.

I suddenly had a horrifying realization. This sounds crazy to me, but I just realized that I never had to change the boot order in the BIOS when I installed ubuntu. I am speculating that perhaps Windows 7 put its MBR on the 160GB drive I now use for linux, instead of the 1TB drive that actually houses the Windows install. This might explain why installing Ubuntu rendered Windows unbootable, and why os-prober doesn't detect the windows install. This is just conjecture, but it actually makes sense to me.

Thanks everyone, and sorry for this confusing scenario. Hopefully somebody can help dig me out of this mess!

---

### Post by Bucky Ball on 2011-01-10
Follow my instructions in post #2 and make sure this is the case.

If os-prober doesn't pick it up this probably won't either but worth a shot ...

---

### Post by wilee-nilee on 2011-01-10
Hello Bucky Ball,:) OP our mutual friend here has had you run the update-grub, so the next step best is the boot script. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Rubi1200 on 2011-01-10
> **wilee-nilee said:**
> Hello Bucky Ball,:) OP our mutual friend here has had you run the update-grub, so the next step best is the boot script. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.
+1 to the boot script.

The information will tell us what is where and make helping you resolve this that much easier.

---

### Post by zlapidus on 2011-01-10
Thanks, everyone, for your help. Since I can only boot from the live-cd at this point, I wasn't sure the right command to run update-grub on my drive (I mounted my Ubuntu hard drive in nautilus, and in the terminal changed the directory to it, and ran sudo update-grub.

This returned "/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)."

I went ahead and ran the boot script, and here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7b65b9a7-b498-4288-9c9c-6040992190d9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b369bab7-a6f6-49cf-b97e-ebdf9dc983aa   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        10023CC6023CB298                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/7b65b9a7-b498-4288-9c9c-6040992190d9 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7b65b9a7-b498-4288-9c9c-6040992190d9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=7b65b9a7-b498-4288-9c9c-6040992190d9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7b65b9a7-b498-4288-9c9c-6040992190d9
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b369bab7-a6f6-49cf-b97e-ebdf9dc983aa none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 150.5GB: boot/grub/core.img
 150.5GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.35-24-generic-pae
 150.5GB: boot/vmlinuz-2.6.35-24-generic-pae
   1.2GB: initrd.img
 150.5GB: vmlinuz
```Thanks!

---

### Post by wilee-nilee on 2011-01-10
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

First problem your missing the boot files highlighted, it also does not have a boot flag on it.

Easy fix is remove the sda drive, put the bootflag on sdb1 with gparted right click on sdb1 in gparted then flags then click boot. Then boot a recovery disc for W7, and follow these instruction to put the files in and a MS bootloader in the sdb MBR. Notice the W7 forums link for a visual of getting to the command line
1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr 
BootRec.exe /FixBoot (#updates PBR partition boot)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a link for a W7 recovery ISO to burn to a cd. This can be loaded to a thumb as well, use a cd though if you can.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

After W7 is back and booting, then plug the sda drive back in; put it first to be read in the bios, then boot a live Ubuntu cd of the same release and open a terminal and run these commands.

sudo fdisk -lu 
This will identify if your still sda, make sure that you are or adjust the HD letter accordingly. Then run these two commands for loading grub to the mbr of the 160 gig HD.

sudo mount /dev/sda1 /mnt
then this command
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot to the 160 gig HD you should see the grub menu choose the Ubuntu install, once in open a terminal and run this command.
sudo update-grub

---

### Post by zlapidus on 2011-01-12
Thanks so much. Your steps did the trick just beautifully. I was still missing Bootmgr, so I had to run the Windows Startup fixing tool a few times to get everything righted, but now everything's working great.

Thanks so much!

---

### Post by wilee-nilee on 2011-01-12
> **zlapidus said:**
> Thanks so much. Your steps did the trick just beautifully. I was still missing Bootmgr, so I had to run the Windows Startup fixing tool a few times to get everything righted, but now everything's working great.

Thanks so much!

Glad it worked, a group effort can work wonders.:)

---

