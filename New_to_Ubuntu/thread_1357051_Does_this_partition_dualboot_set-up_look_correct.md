---
title: "Does this partition dualboot set-up look correct?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by vault55 on 2009-12-16
[SIZE=3][IMG]http://s454.photobucket.com/albums/qq261/clintnatx/[/IMG]I used the Disk Management Tool in Win 7 to shrink the volume down to 200gb. Then, I put in the disk and followed the instructions telling it to install in the largest free portion.  Is this correct? It looks different than others Ive seen but it works.  I prefer not to share media between Windows and Linux. Thanks for your help
[IMG]http://s454.photobucket.com/albums/qq261/clintnatx/[/IMG]
[/SIZE]

---

### Post by MooPi on 2009-12-16
While in Windows you won't be able to view your Linux files because it can't read the file system. While in Linux /Ubuntu you should be able to view Windows partitions due to nfts support.

---

### Post by madana on 2009-12-16
> **vault55 said:**
> [SIZE=3][IMG]http://s454.photobucket.com/albums/qq261/clintnatx/[/IMG]I used the Disk Management Tool in Win 7 to shrink the volume down to 200gb. Then, I put in the disk and followed the instructions telling it to install in the largest free portion.  Is this correct? It looks different than others Ive seen but it works.  I prefer not to share media between Windows and Linux. Thanks for your help
[IMG]http://s454.photobucket.com/albums/qq261/clintnatx/[/IMG]
[/SIZE]

you have to format boot the 191. Gb & the 8. gb. for it too work. right click. click format & i hope it works. it will look like this when u r finished.

---

### Post by running_rabbit07 on 2009-12-16
Looks fine. WHen you go to install Ubuntu, select the partitions manually and the installer will do the formatting for you.

---

### Post by vault55 on 2009-12-16
> **running_rabbit07 said:**
> Looks fine. WHen you go to install Ubuntu, select the partitions manually and the installer will do the formatting for you.

Ive installed it already however, it dosent look like theres much room.  Its as if it didnt recognize the whole 200gb that was free. Please take a look at the screen shot.  I have another problem, grub did an update and now contains about 6 entries 2 entries for .14 and 2 for .16  and vista (which I dont have) and win 7 (lastly of course the 2 x86 memory test. sheesh).:confused:

---

### Post by vault55 on 2009-12-16
> **madana said:**
> you have to format boot the 191. Gb & the 8. gb. for it too work. right click. click format & i hope it works. it will look like this when u r finished.

thanks but I dont see a windows install on yours so Im not sure exactly what you mean.  Also, it gives me tons of format options, which do I choose?

---

### Post by raymondh on 2009-12-16
If the gparted output is the same as the windows' disc utility output (your first posts' attachment) .... then you've successfully found a way around  the 4-primary limit.

[B]
EDIT : nevermind ... I just saw the other attachments and the palimpsests disk utility graphic shows an extended.  Sorry to bother.  Was just excited to break the 4-rule[/B] ;)

---

### Post by presence1960 on 2009-12-16
Better yet we need to see your setup and boot process. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by vault55 on 2009-12-16
> **presence1960 said:**
> Better yet we need to see your setup and boot process. Do this please:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

No problem but I downloaded a graphics driver and now I cant boot into Ubuntu.  This whole process id fustrating but Im dedicated to making this work and learning Linux. I choose the .16 option then the screen goes black with a small grey line at the top left of the screen (system hangs). Windows boots fine.

---

### Post by presence1960 on 2009-12-16
> **vault55 said:**
> No problem but I downloaded a graphics driver and now I cant boot into Ubuntu.  This whole process id fustrating but Im dedicated to making this work and learning Linux. I choose the .16 option then the screen goes black with a small grey line at the top left of the screen (system hangs). Windows boots fine.

Boot the Ubuntu Live CD and follow the instructions please.

---

### Post by vault55 on 2009-12-16
> **presence1960 said:**
> Boot the Ubuntu Live CD and follow the instructions please.

as requested, thanks for takin a look and helpin out


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67cbf671

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 HPFS/NTFS
/dev/sda2           2,459,648   536,858,615   534,398,968   7 HPFS/NTFS
/dev/sda3         956,291,072   976,771,071    20,480,000   7 HPFS/NTFS
/dev/sda4         536,865,840   956,279,519   419,413,680   5 Extended
/dev/sda5         536,865,903   939,209,039   402,343,137  83 Linux
/dev/sda6         939,209,103   956,279,519    17,070,417  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="8E4201BE4201ABD1" LABEL="SYSTEM_DRV" TYPE="ntfs" 
/dev/sda2: UUID="2A781C20781BE979" LABEL="Windows7_OS" TYPE="ntfs" 
/dev/sda3: UUID="9EEC0B47EC0B1963" LABEL="Lenovo_Recovery" TYPE="ntfs" 
/dev/sda5: UUID="ee4b1162-77fb-410f-8edf-33f1aa7e0d96" TYPE="ext4" 
/dev/sda6: UUID="3211ded1-73df-453f-9f66-ff8c691ef84b" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set ee4b1162-77fb-410f-8edf-33f1aa7e0d96
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee4b1162-77fb-410f-8edf-33f1aa7e0d96
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ee4b1162-77fb-410f-8edf-33f1aa7e0d96 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee4b1162-77fb-410f-8edf-33f1aa7e0d96
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ee4b1162-77fb-410f-8edf-33f1aa7e0d96 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee4b1162-77fb-410f-8edf-33f1aa7e0d96
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee4b1162-77fb-410f-8edf-33f1aa7e0d96 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ee4b1162-77fb-410f-8edf-33f1aa7e0d96
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee4b1162-77fb-410f-8edf-33f1aa7e0d96 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8e4201be4201abd1
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 2a781c20781be979
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ee4b1162-77fb-410f-8edf-33f1aa7e0d96 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=3211ded1-73df-453f-9f66-ff8c691ef84b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 274.8GB: boot/grub/grub.cfg
 274.8GB: boot/initrd.img-2.6.31-14-generic
 274.8GB: boot/initrd.img-2.6.31-16-generic
 274.8GB: boot/vmlinuz-2.6.31-14-generic
 274.8GB: boot/vmlinuz-2.6.31-16-generic
 274.8GB: initrd.img
 274.8GB: initrd.img.old
 274.8GB: vmlinuz
 274.8GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-12-16
Everything looks good to me, is there a problem?

sda1 is windows 7 boot partition
sda2 is windows 7
sda3 is your Lenovo recovery partition
sda4 is extended partition which contains:
sda5 is Ubuntu 9.10
sda6 is swap

---

### Post by vault55 on 2009-12-16
> **presence1960 said:**
> Everything looks good to me, is there a problem?

sda1 is windows 7 boot partition
sda2 is windows 7
sda3 is your Lenovo recovery partition
sda4 is extended partition which contains:
sda5 is Ubuntu 9.10
sda6 is swap

yes, after I told it to look for drivers it found a graphics card driver and asked if I would like to restart my system, when I chose yes and rebooted, I get to grub and thats it.  I choose the non-recovery .16 ubuntu from grub then the system hangs (screen goes black with the excption of two gray dashes in the upper left hand part of the screen) Also, how do I do wipe and do a fresh reinstall of Ubuntu? (I think I might start over due to my ISO being a couple of months old etc.) I know that probably sounds rediculious but Im very particuliar about my systems.  This is much different from coding objective-C (if you ever need help with that, let me know)

---

### Post by presence1960 on 2009-12-16
> **vault55 said:**
> yes, after I told it to look for drivers it found a graphics card driver and asked if I would like to restart my system, when I chose yes and rebooted, I get to grub and thats it.  I choose the non-recovery .16 ubuntu from grub then the system hangs (screen goes black with the excption of two gray dashes in the upper left hand part of the screen) Also, how do I do wipe and do a fresh reinstall of Ubuntu? (I think I might start over due to my ISO being a couple of months old etc.) I know that probably sounds rediculious but Im very particuliar about my systems.  This is much different from coding objective C (if you ever need help with that, let me know)
You may be able to save your Ubuntu what graphics card do you have and what driver did you download?

---

### Post by vault55 on 2009-12-16
> **presence1960 said:**
> You may be able to save your Ubuntu what graphics card do you have and what driver did you download?

ATI 3470 and Im not what was downloaded/installed but it was ATI and I assumed it was correct. (I know, dumb.....):(

---

### Post by presence1960 on 2009-12-16
If you have an Nvidia or ATI card you can uninstall the driver. Boot into recovery mode and choose netroot. It will ask you to log in. 

If you do not have Envyng installed on your Ubuntu you will need to do that first. Run these commands one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk

```
you may or may not need sudo, I haven't had to do this in a while.

Once they are installed run ```
envyng -t
```

Follow the prompts to uninstall the ATI driver. When completed choose the reboot option. You can then try to use Envyng from Ubuntu to install your graphics driver.

Note that AMD/ATI stopped support for a lot of their vid cards that aren't quite new. You may not find a driver for that card. I am not sure as I am a Nvidia man.

Edit: It does not ask you to login, it will leave you at a root prompt- just run those commands and let it rip!

---

### Post by vault55 on 2009-12-16
> **presence1960 said:**
> If you have an Nvidia or ATI card you can uninstall the driver. Boot into recovery mode and choose netroot. It will ask you to log in. 
 
If you do not have Envyng installed on your Ubuntu you will need to do that first. Run these commands one at a time:
 
```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk

```
you may or may not need sudo, I haven't had to do this in a while.
 
Once they are installed run ```
envyng -t
```
 
Follow the prompts to uninstall the ATI driver. When completed choose the reboot option. You can then try to use Envyng from Ubuntu to install your graphics driver.
 
Note that AMD/ATI stopped support for a lot of their vid cards that aren't quite new. You may not find a driver for that card. I am not sure as I am a Nvidia man.
 
Edit: It does not ask you to login, it will leave you at a root prompt- just run those commands and let it rip!
 
Ok, I uninstalled it and when I went to look for a new one via envyng -t, the installed version and recommended version were blank. Now I hear the drums but I still have the same dashes and no display:(. it does give a "0" for generic and Ive booted with both options and come to the same black screen.

---

### Post by vault55 on 2009-12-17
If i delete both Ubuntu partitions, will it restore the 200g "unallocated" space that I started with? So, I can start over or possibly try other distro's.

---

### Post by presence1960 on 2009-12-17
> **vault55 said:**
> If i delete both Ubuntu partitions, will it restore the 200g "unallocated" space that I started with? So, I can start over or possibly try other distro's.

whatever the size of those two partitions will be unallocated if deleted until you make new partition(s)

---

### Post by vault55 on 2009-12-17
> **presence1960 said:**
> whatever the size of those two partitions will be unallocated if deleted until you make new partition(s)

Thanks Presence, I stayed up late last night trying to fix whatever messed things up.  I followed your instructions to roll back the driver but to no avail.  LAST QUESTION, then closing this.

I started with a solid 200GB block of unallocated space, then used the Live CD and it split that space into two parts (or partitions) when I delete those, will it be one solid block of 200GB like I originally started with? Will I need to manually remove grub and how if so?  thanks again.

---

### Post by presence1960 on 2009-12-17
> **vault55 said:**
> Thanks Presence, I stayed up late last night trying to fix whatever messed things up.  I followed your instructions to roll back the driver but to no avail.  LAST QUESTION, then closing this.

I started with a solid 200GB block of unallocated space, then used the Live CD and it split that space into two parts (or partitions) when I delete those, will it be one solid block of 200GB like I originally started with? Will I need to manually remove grub and how if so?  thanks again.

They will become one continuous block of unallocated space. When you do the install GRUB will be rewritten to MBR. You don't have to worry about GRUB. Let us know how it works out!

---

### Post by vault55 on 2009-12-17
> **presence1960 said:**
> They will become one continuous block of unallocated space. When you do the install GRUB will be rewritten to MBR. You don't have to worry about GRUB. Let us know how it works out!
 
[SIZE=4]BIG PROBLEM! I deleted as discussed and as I suspected and GRUB says:[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]GRUB loading.[/SIZE]
[SIZE=4]error: no such partition[/SIZE]
[SIZE=4]grub rescue>[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]I now cant boot into windows....please help.[/SIZE]
[SIZE=4] [/SIZE]

---

### Post by presence1960 on 2009-12-17
> **vault55 said:**
> [SIZE=4]BIG PROBLEM! I deleted as discussed and as I suspected and GRUB says:[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]GRUB loading.[/SIZE]
[SIZE=4]error: no such partition[/SIZE]
[SIZE=4]grub rescue>[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]I now cant boot into windows....please help.[/SIZE]
[SIZE=4] [/SIZE]

you can't boot into windows until you restore it's bootloader to MBR. GRUB is still there. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and scroll down to your version of windows to restore the bootloader.

If your recovery DVD/partition will not allow you to access Recovery Console go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), download the iso for your windows version & burn it to CD as an image. This will allow you to boot that CD and follow those instructions to repair Vista bootloader.

---

### Post by vault55 on 2009-12-17
> **presence1960 said:**
> you can't boot into windows until you restore it's bootloader to MBR. GRUB is still there. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and scroll down to your version of windows to restore the bootloader.
 
If your recovery DVD/partition will not allow you to access Recovery Console go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), download the iso for your windows version & burn it to CD as an image. This will allow you to boot that CD and follow those instructions to repair Vista bootloader.
 
Yep, I have a new ThinkPad and had to burn an ISO using my girlfriends computer but all is well now and it boots normally.  Everything appears to be restored to normal and I will try to install Ubuntu again using a new ISO.  Should I do it he same way, starting with 200GB unallocated, then run the Live CD telling it to install in the largest free portion?  Youve been really helpful and Im most appreciative.

---

### Post by presence1960 on 2009-12-17
> **vault55 said:**
> Yep, I have a new ThinkPad and had to burn an ISO using my girlfriends computer but all is well now and it boots normally.  Everything appears to be restored to normal and I will try to install Ubuntu again using a new ISO.  _**Should I do it he same way, starting with 200GB unallocated, then run the Live CD telling it to install in the largest free portion?**_  Youve been really helpful and Im most appreciative.

That would be the simplest way. If you are new to partitioning/OS installations I would say do it that way. After you gain some knowledge and get some experience under your belt you can set up partitions prior to installing and then install using the manual option.

---

### Post by raymondh on 2009-12-18
> **presence1960 said:**
> That would be the simplest way. If you are new to partitioning/OS installations I would say do it that way. After you gain some knowledge and get some experience under your belt you can set up partitions prior to installing and then install using the manual option.

+ 1 .  use that option ... it'll be the simplest way as you have that space unallocated already.

Happy holidays.

---

### Post by vault55 on 2009-12-18
> **raymondh said:**
> + 1 .  use that option ... it'll be the simplest way as you have that space unallocated already.

Happy holidays.

thanks a ton guys! I will close this thread out then and I hope you and your family have a great holiday.

---

