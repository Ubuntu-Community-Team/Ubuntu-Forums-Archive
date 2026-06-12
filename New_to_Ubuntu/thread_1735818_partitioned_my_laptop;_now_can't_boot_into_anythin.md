---
title: "partitioned my laptop; now can't boot into anything and laptop reboots itself."
date: 2011-04-21
forum: New to Ubuntu
---

### Post by altheablue on 2011-04-21
[SIZE=2]Hello all - I'm wondering if someone would be kind enough to help me get my laptop back into operation.
[/SIZE][SIZE=2] 
I switched to Ubuntu on my desktop through wubi about 14 months ago, fell in love and never looked back.[/SIZE]
[SIZE=2]This week I got a brand new laptop, a Gateway NV53A, 320G HD, came with Windows 7. 

So the day I got the laptop, I burned a Windows recovery disc (I know) and attempted to partition my hard drive. (I'd never done that before - yes, I've used wubi for 14 months now on my desktop. ;))
I followed the instructions ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) and let it do the partitioning for me; I allotted a little under a third to Windows, the rest to Ubuntu.

Then I rebooted and it was all downhill from there. There was lots of Ubuntu updating at one point (6 kernels I think!); there were errors, the phrase "kernel panic" appeared, and I believe at some point something "could not set root" or "could not find root". I'm paraphrasing that last bit; I've been reading threads here all week and my head's spinning. [/SIZE][SIZE=2]
Also, FWIW, I have an ATI Mobility Radeon HD 4250. (I read lots  about the "ATI boot of death") And I think I remember seeing a tty1  error/message at one point.[/SIZE]
[SIZE=2]
Ever since then, I can't boot into Ubuntu or Windows. I get a black screen with a static cursor-like thing at the top, and the computer reboots itself continually. I can get the BIOS menu with F2, and from there I enabled the F12 boot selector screen, but that's it. Nothing I select from F12 works except the cd I'm using right now, and the Windows recovery disc.

I ran everything on that Windows recovery disc - nothing worked, no change.

My Ubuntu live cd didn't work either, so finally it occurred to me to make a new one.
Now I'm on the laptop, on a live cd.

Here is the output of ```
[SIZE=2]sudo parted --list[/SIZE]
```[/SIZE]```
[SIZE=2]
Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  105GB   90.6GB  primary   ntfs
 4      105GB   320GB   215GB   extended
 5      105GB   311GB   207GB   logical   ext4
 6      311GB   320GB   8776MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label[/SIZE]
```[SIZE=2]
[/SIZE][SIZE=2]
Can someone help me interpret this? I assume 2 is my Windows partition and 4 is Ubuntu, because of the relative sizes, although those aren't the exact sizes I allotted.

Basically I'd just like to get Ubuntu running. If Windows is still there, fine, if not that's fine too. I'm just not sure how to proceed, and what to do differently this time.

Thank you to anyone who read all this.
[/SIZE]

---

### Post by mathgeek2000 on 2011-04-21
> **altheablue said:**
> [SIZE=2]Hello all - I'm wondering if someone would be kind enough to help me get my laptop back into operation.
[/SIZE][SIZE=2] 
[/SIZE][SIZE=2]Here is the output of ```
[SIZE=2]sudo parted --list[/SIZE]
```[/SIZE]```
[SIZE=2]
Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  105GB   90.6GB  primary   ntfs
 4      105GB   320GB   215GB   extended
 5      105GB   311GB   207GB   logical   ext4
 6      311GB   320GB   8776MB  logical   linux-swap(v1)

[/SIZE][SIZE=2]Basically I'd just like to get Ubuntu running. If Windows is still there, fine, if not that's fine too. I'm just not sure how to proceed, and what to do differently this time.

Thank you to anyone who read all this.
[/SIZE]

It looks like the first 3 partitions are Windows 7 & it's recovery partition. Linux is in the extended partition (4 & Logical 5 & 6). If it's trying to boot off the hard drive and failing, there may have been an issue with the GRUB menu getting installed correctly.

Couple of options: If you want to give up on Windows 7, (at least for now) - you have the recovery CDs. -->
 from a command prompt on the LiveCD:
 This will quickly wipe the hard drive:

[CODE]$sudo -s
#dd if=/dev/zero of=/dev/sda count=1 bs=512

```

Reboot and reinstall Linux, install the GRUB2 to the MBR (or master boot record) when prompted.

Option 2:
Use the Windows 7 recovery disks to fix the MBR. - This may make the PC boot only into Windows. You will see about 105GB of your 320GB drive, in 'My Computer' If that works, restore the GRUB2 bootloader, to access both Linux & Windows 7.

Option 3:
Reinstall Windows 7 manually, from the Recovery Disk - But don't use the entire disk. Use 100 - 105GB as you see above. Then install Ubuntu after the Windows partition.

---

### Post by Awesome96 on 2011-04-21
Hmmm... It might be that the Windows install tried to overwrite both your Ubuntu install AND your bootloader, the latter being the more serious. Try burning a live cd or something, then use fdisk to delete all partitions (just to give Windows a clean slate to work with) and then install Windows, it should create it's own partitions.

   Now install Ubuntu, partition some of the free space to use for the install and voila! The problem here is that Windows doesn't work well when it has other operating systems on the same hard drive, even if it's in different partitions.

  I am however no expert, so I'll gladly be corrected if I'm wrong.

---

### Post by altheablue on 2011-04-21
Thanks guys. 

I should have said about that Windows recovery disc that it's not an actual backup, from what I can tell. I'm not actually sure what it's good for - it tried to "repair" Windows for me and failed, but that's about it. I should have made a full backup, of course. That's one lesson well and truly learned. :/

But thank you both for all the information; that gives me a direction. I'm going to have to go do more research on MBR and grub2 and fdisk.  
Thank you!

---

### Post by oldfred on 2011-04-21
You should have to just reinstall grub2's boot loader to the MBR, if that is the problem. From Ubuntu you can install a windows like boot loader that will boot windows, or you can make a windows repair CD. If you want more detailed help post boot info script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You should have a live/repair CD (or USB flash) for every operating system you have installed. So if keeping windows get the correct version from here:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by altheablue on 2011-04-22
Oh thank you! That is so helpful. I feel slightly, cautiously optimistic for the first time in 5 days. 
I will try restoring/fixing the bootloader when I get home from work.
If it works, I will be the happiest person alive and buy you all beers (or beverages of your choice). :D

Or I may return in tears and beg for more help. We shall see.

Thank you!

---

### Post by JKyleOKC on 2011-04-22
> **altheablue said:**
> 
Here is the output of ```
sudo parted --list


Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.0GB  14.0GB  primary   ntfs
 2      14.0GB  14.1GB  105MB   primary   ntfs            boot
 3      14.1GB  105GB   90.6GB  primary   ntfs
 4      105GB   320GB   215GB   extended
 5      105GB   311GB   207GB   logical   ext4
 6      311GB   320GB   8776MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```The partition flagged as "extended" is actually a container for the two "logical" partitions that follow it in the listing. The entire listing looks good.

The error message is simply saying that your Live CD is read-only (as are most CDs) and that the program could not recognize its disk label. It's not really an error, just a comment...

Running the "bootinfo" script will tell us much more about your setup, but it looks as if a simple repair of the MBR might fix it as suggested by the other messages.

---

### Post by altheablue on 2011-04-22
[SIZE=2]Thanks, guys. I really appreciate it. Here are the results of the boot info script, and now I'm off to read those threads oldfred linked...

By the way: I can access Ubuntu and Windows from this disk. That might be really obvious, but I didn't expect it. I don't know if that's significant, just thought I'd throw it out there.

[Agh I'm sorry the text is so small - I keep resizing it but it doesn't "stick."]


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    27,265,023    27,262,976  27 Hidden HPFS/NTFS
/dev/sda2    *     27,265,024    27,469,823       204,800   7 HPFS/NTFS
/dev/sda3          27,469,824   204,400,428   176,930,605   7 HPFS/NTFS
/dev/sda4         204,400,638   625,141,759   420,741,122   5 Extended
/dev/sda5         204,400,640   607,999,999   403,599,360  83 Linux
/dev/sda6         608,002,048   625,141,759    17,139,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BEE6BE0CE6BDC545                       ntfs       PQSERVICE                     
/dev/sda2        B8D2BE88D2BE4A80                       ntfs       SYSTEM RESERVED               
/dev/sda3        887CF1537CF13D0E                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        e32806bb-bfb3-4632-945c-7ea1a1c2ff2e   ext4                                     
/dev/sda6        cc28504f-3a5d-4c03-b7b0-f2d9f1baa580   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Gateway           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/e32806bb-bfb3-4632-945c-7ea1a1c2ff2e ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e32806bb-bfb3-4632-945c-7ea1a1c2ff2e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e32806bb-bfb3-4632-945c-7ea1a1c2ff2e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e32806bb-bfb3-4632-945c-7ea1a1c2ff2e ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=e32806bb-bfb3-4632-945c-7ea1a1c2ff2e ro single 
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
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e32806bb-bfb3-4632-945c-7ea1a1c2ff2e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set bee6be0ce6bdc545
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b8d2be88d2be4a80
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
UUID=e32806bb-bfb3-4632-945c-7ea1a1c2ff2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cc28504f-3a5d-4c03-b7b0-f2d9f1baa580 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 227.2GB: boot/grub/core.img
 197.1GB: boot/grub/grub.cfg
 308.9GB: boot/initrd.img-2.6.35-22-generic
 308.9GB: boot/initrd.img-2.6.35-28-generic
 227.2GB: boot/vmlinuz-2.6.35-22-generic
 227.2GB: boot/vmlinuz-2.6.35-28-generic
 308.9GB: initrd.img
 308.9GB: initrd.img.old
 227.2GB: vmlinuz
 227.2GB: vmlinuz.old
```[/SIZE][SIZE=2]
[/SIZE]

---

### Post by oldfred on 2011-04-22
Boot script looks normal as far as I can see. I found both "Vista" which is probably your recovery partition and win7.

Because it found the windows install, it should give menu if grub is booting. Do you get menu or does it not get that far.

I would reinstall grub2's boot loader to the MBR, but the easy two line version often does not always work and then you have to do the full chroot version.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=Red]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by altheablue on 2011-04-22
[SIZE=2]Thanks oldfred. I get the Gateway splash screen where the F2 and F12 options are, and then it just goes to a blank screen with a cursor-like thing at the top, and it's unresponsive except to Ctrl+Alt+Del which reboots. (That's progress, actually!)

I tried the 2-line version and indeed, it didn't work - going to try the chroot version now. Thanks.
[/SIZE]

---

### Post by altheablue on 2011-04-22
[SIZE=2]Well, there's good news and bad news.[/SIZE]
 
[SIZE=2]Good: I now have a working operating system that I can boot into! :D[/SIZE]
 
[SIZE=2]Bad: It's Windows. X([/SIZE]
 
[SIZE=2]I ran the chroot reinstall, and it didn't fix things, but *some* things were better. [/SIZE]
[SIZE=2]So I thought maybe I needed to reinstall the Windows fix too, so I did that from the Windows recovery disk. And so for the past hour, Windows has been repairing itself (which included reinstalling all the bloatware I got rid of the day I bought this thing, but anyway).[/SIZE]
 

[SIZE=2]Under "Computer" Windows is showing its partitioned size, 80something GB, so Ubuntu is there waiting for me. Now I just have to figure out how to get it to show up in the boot menu. [/SIZE]
 
[SIZE=2]Should I close this thread and mark it "Solved," because my original problem (couldn't boot into anything) is technically solved? Thoughts are welcome; otherwise I'll use my own (questionable) judgment.[/SIZE]
 
[SIZE=2]And THANK YOU! a thousand times thank you! to oldfred and everyone else for getting me this far. Since I don't have a firstborn child to promise you, I'll raise a toast to you from afar. [/SIZE]
 
[SIZE=2]:cheers: and thank you,[/SIZE]
[SIZE=2]kim.[/SIZE]

---

### Post by Quackers on 2011-04-22
If you boot from the live cd/usb and select "try ubuntu" you can then go to System > Admin > gparted.
Confirm that the Ubuntu partition is still there and that it still has the same designation (it was /dev/sda5). If it is you can open up a terminal and run these 2 commands, one at a time, pressing enter after each line. 
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If no errors are reported you can reboot, when Ubuntu should boot directly. If so, open a terminal and run ```
sudo update-grub
``` and as grub.cfg is run you should see the Windows Loader picked up. If it is you can reboot hopefully to a grub menu with both choices.

---

### Post by altheablue on 2011-04-22
[SIZE=2]Thank you! (I love these forums.)

Boot menu is there, both OS's are there, everything is awesome except I think Maverick doesn't like my graphics settings, because it almost boots--startup screen appears--then goes away. Right now I'm in fail-safe graphics mode, which actually looks fine to me.

So I think I'm down to drivers and some tweaking and I'm perfect.

Thank youthankyouthankyou! :D

:cheers: <--this really should be a smilie
[/SIZE]

---

### Post by Quackers on 2011-04-22
I'm happy inside :-) You're welcome!
Good luck with getting the drivers sorted out.

Edit Does it need a boot option? Like nomodeset, for instance.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by altheablue on 2011-04-22
> **Quackers said:**
> I'm happy inside :-) You're welcome!
Good luck with getting the drivers sorted out.

Edit Does it need a boot option? Like nomodeset, for instance.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thank you! And yes, it might need exactly that. I can't test it until tomorrow, but thank you - that does look promising...

---

