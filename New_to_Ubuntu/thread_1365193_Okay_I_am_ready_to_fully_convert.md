---
title: "Okay I am ready to fully convert"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Lazylazylazy on 2009-12-26
I recently got a netbook with Windows 7 and was shocked to learn that I could not change the wallpaper or theme. Besides that, Win 7 starter is basically scrap, like a handicapped Vista if you will.

I learned about Ubuntu Netbook Remix from a buddy and I installed it, and surprisingly, me and the OS clicked :) I installed all the neccesary plugins (mp3 and such, though it said it came with it) and such to make it a mainstream user friendly computer!

Now I want to delete windows 7 starter FULLY from the dual boot! I have a couple of questions:
1. How would I do this?
2. Would I need to reformat? (BIG NO NO)
3. Would the dual boot program break if I remove Win 7?
4. Will it affect my Ubuntu OS?
5. Would it improve performance in terms of RAM?
6. Would it free up memory?

[B]tl;dr Help me remove Windows 7

Thank you!
[/B]

---

### Post by Lazylazylazy on 2009-12-26
Bump

---

### Post by Mahngiel on 2009-12-26
Did you install Ubuntu inside of windows using Wubi, or did you pop in a disk and install in on a partition from the boot menu?

---

### Post by Lazylazylazy on 2009-12-26
Yeah I use windows but I never used wubi? I just downloded the ISO, put it into a bootable USB drive then installed it from there

---

### Post by Mahngiel on 2009-12-26
(First and foremost, always backup your data)

If you installed it on a partition beside windows, you can install gparted and use that to delete windows.

From a terminal:
```
sudo apt-get install gparted
```
Then run
```
sudo gparted
```

If you pop the menu on what will probably be sda, you will find your windows partition. Right click and delete it.

----
If you installed via Wubi

Obtain UNR Live CD, either by burning an ISO file to a disk, or with a[ bootable thumbdrive]("https://help.ubuntu.com/community/Installation/FromImgFiles") 
Back up your important stuff
And run that baby to entire disk.

---

### Post by Ben Wright on 2009-12-26
If you installed it from Wubi I believe you are out of luck and you will actually have to do a complete reinstall of ubuntu and wipe the entire drive.  If however it is a proper dual boot I could suggest a tool such as gparted which would be able to delete your windows 7 parition.

1. How would I do this?
You would use Gparted if it is a proper dual boot and not a Wubi one.
2. Would I need to reformat? (BIG NO NO)
Potentially if it is a wubi dual boot.
3. Would the dual boot program break if I remove Win 7?
GRUB wouldn't break no but Windows would no longer be accessiable.
4. Will it affect my Ubuntu OS?
You will reclaim space.
5. Would it improve performance in terms of RAM?
No effect RAM is controlled by the operating system since you cant physically boot two operating systems at the same time you would not notice a difference.
6. Would it free up memory?
It would free up the hard drive space taken up by the windows partition yes.

Thanks.

---

### Post by taurus on 2009-12-26
It depends how you partition your harddrive.  Although I've never tried it on a netbook, but this is what I would do.

Boot from a LiveCD (or with a USB thumbdrive), use gparted in System -> Administration) to delete the partition that windows is in.  Then, format that to ext4.  Then, expand the root filesystem of Ubuntu to take up that allocated space IF they are right next to each other, partitions.  

What's the output of this command from a terminal in Ubuntu?

```
sudo fdisk -l
df -h
```

---

### Post by Mahngiel on 2009-12-26
To answer your questions:

2. No
3. No
4. No
5. No
6. Yes

---

### Post by Lazylazylazy on 2009-12-26
Thank you for all the replies.
@mahn 
To clarify I installed UNR by using the bootable USB stick and going to the BIOS menu thingy and booting from USB.
Just want to make sure, can I do your method?

---

### Post by Lazylazylazy on 2009-12-26
> **Mahngiel said:**
> (First and foremost, always backup your data)

If you installed it on a partition beside windows, you can install gparted and use that to delete windows.

From a terminal:
```
sudo apt-get install gparted
```Then run
```
sudo gparted
```If you pop the menu on what will probably be sda, you will find your windows partition. Right click and delete it.

----
If you installed via Wubi

Obtain UNR Live CD, either by burning an ISO file to a disk, or with a[ bootable thumbdrive]("https://help.ubuntu.com/community/Installation/FromImgFiles") 
Back up your important stuff
And run that baby to entire disk.

There are 6 things that says SDA, which one do i do?

---

### Post by Lazylazylazy on 2009-12-27
bump

---

### Post by presence1960 on 2009-12-27
Before you go removing anything lets see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Lazylazylazy on 2009-12-27
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31558adc

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   183,478,364   158,095,665   7 HPFS/NTFS
/dev/sda4         183,478,365   312,576,704   129,098,340   5 Extended
/dev/sda5         183,478,428   307,210,994   123,732,567  83 Linux
/dev/sda6         307,211,058   312,576,704     5,365,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="54E82281E822618A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="5AA022DCA022BE7F" LABEL="SYSTEM RESERVED" TYPE="ntfs" 
/dev/sda3: UUID="9A2824462824242B" LABEL="Acer" TYPE="ntfs" 
/dev/sda5: UUID="b5701010-77a3-4d90-94dc-772796f3db9a" TYPE="ext4" 
/dev/sda6: UUID="32b3bf19-304f-41c8-93a6-47087619a9a5" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/lazy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lazy)


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
search --no-floppy --fs-uuid --set b5701010-77a3-4d90-94dc-772796f3db9a
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
    search --no-floppy --fs-uuid --set b5701010-77a3-4d90-94dc-772796f3db9a
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=b5701010-77a3-4d90-94dc-772796f3db9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b5701010-77a3-4d90-94dc-772796f3db9a
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=b5701010-77a3-4d90-94dc-772796f3db9a ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b5701010-77a3-4d90-94dc-772796f3db9a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b5701010-77a3-4d90-94dc-772796f3db9a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b5701010-77a3-4d90-94dc-772796f3db9a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b5701010-77a3-4d90-94dc-772796f3db9a ro single 
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
    search --no-floppy --fs-uuid --set 54e82281e822618a
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 5aa022dca022be7f
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
UUID=b5701010-77a3-4d90-94dc-772796f3db9a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=32b3bf19-304f-41c8-93a6-47087619a9a5 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  93.9GB: boot/grub/grub.cfg
  93.9GB: boot/initrd.img-2.6.31-14-generic
  93.9GB: boot/initrd.img-2.6.31-16-generic
  93.9GB: boot/vmlinuz-2.6.31-14-generic
  93.9GB: boot/vmlinuz-2.6.31-16-generic
  93.9GB: initrd.img
  93.9GB: initrd.img.old
  93.9GB: vmlinuz
  93.9GB: vmlinuz.old

---

### Post by presence1960 on 2009-12-27
```
blkid -c /dev/null: __________________________________________________ __________

[COLOR="Red"]/dev/sda1: UUID="54E82281E822618A" LABEL="PQSERVICE" TYPE="ntfs"[/COLOR]
[COLOR="Purple"]/dev/sda2: UUID="5AA022DCA022BE7F" LABEL="SYSTEM RESERVED" TYPE="ntfs"
/dev/sda3: UUID="9A2824462824242B" LABEL="Acer" TYPE="ntfs"[/COLOR]
/dev/sda5: UUID="b5701010-77a3-4d90-94dc-772796f3db9a" TYPE="ext4"
/dev/sda6: UUID="32b3bf19-304f-41c8-93a6-47087619a9a5" TYPE="swap" 
```

I would leave sda1 in place (red above). If you are going to delete that also I would back that partition up and also go into Win 7 and see if you have the option to burn a recovery DVD(s) prior to deleting sda1. That is a recovery partition which you can use to restore your hard disk to factory image if need ever arises.

sda2 Is System Reserved (boot partition) & sda3 is windows. It is safe to delete sda2 & sda3 after you back up any data from windows you do not want to lose.

You can boot the Ubuntu Live USB you used to install and use gparted to remove those partitions. You will then have unallocated space which you can use to create a data partition for Linux or expand your extended partition sda4 and then add the space to ubuntu sda5. personally I would go with a separate data partition to keep your files on that way if you ever reinstall your data won't be lost because it is on a separate partition. Note that this fact does not exempt you from practicing regular backups as your hard disk may die or become corrupted at any time. When complete boot back to ubuntu and open a terminal and run ```
sudo update-grub
```
to refresh the GRUB menu in grub.cfg

---

### Post by Lazylazylazy on 2009-12-27
> **presence1960 said:**
> 

You can boot the Ubuntu Live USB you used to install and use gparted to remove those partitions. You will then have unallocated space which you can use to create a data partition for Linux or expand your extended partition sda4 and then add the space to ubuntu sda5. personally I would go with a separate data partition to keep your files on that way if you ever reinstall your data won't be lost because it is on a separate partition. Note that this fact does not exempt you from practicing regular backups as your hard disk may die or become corrupted at any time.
SDA2 SDA3 can be removed. Gotcha.
SDA1 ill keep it because why? Can you please explain?

Do I delete sda2 and 3 THEN boot the Ubuntu USB to do what?

Sorry this is my first time removing OSes

---

### Post by presence1960 on 2009-12-27
> **Lazylazylazy said:**
> SDA2 SDA3 can be removed. Gotcha.
SDA1 ill keep it because why? Can you please explain?

Do I delete sda2 and 3 THEN boot the Ubuntu USB to do what?

Sorry this is my first time removing OSes

sda1 is a recovery partition that can be used to restore your hard disk to factory image- that means the way you got it on day one. It will erase everything and restore it to the way it was when you got the computer!

Boot the Ubuntu Live USB you used to install Ubuntu and choose "try ubuntu without any changes". when the desktop loads go Applications > Accessories > Terminal. In terminal run ```
gksu gparted
```
Hit enter on keyboard.
Right click on sda2 and choose Delete. Then right click on sda3 and choose Delete. Now click Apply (green check mark) on top toolbar and allow gparted to work. When it is completed gparted will look like it is reloading and you will have grey unallocated space where sda2 & sda3 were prior. Before deleting these make sure you backup any data/files you do not want to lose or if you do not do so they will be gone!

If you want to brush up on or learn partitioning see [here]("https://help.ubuntu.com/community/HowtoPartition").

---

### Post by Lazylazylazy on 2009-12-27
okay I've removed sda 2 and 3, this means I have more free space right?

EDIT:

THank you to everyone who helped.
Can I use the unallocated space to save stuff iin it?

---

### Post by presence1960 on 2009-12-27
> **Lazylazylazy said:**
> okay I've removed sda 2 and 3, this means I have more free space right?

Yes, from your Live CD again use gparted and you should see grey unallocated space like this in mine- see pic below

To create a new partition right click the grey unallocated space and choose New. A window will appear and you will need to supply the parameters such as size (if you want it as one partition don't change the size). Choose primary for create as and ext3 or ext4 for filesystem. In the label box type in a name to describe what you are using it for. This name will show up in file browser and gparted to help you identify the partition, but is not necessary.

---

### Post by Lazylazylazy on 2009-12-27
Okay done! So the space I just partitioned can be used by Ubuntu now?

Thank you so much!

---

### Post by presence1960 on 2009-12-27
> **Lazylazylazy said:**
> Okay done! So the space I just partitioned can be used by Ubuntu now?

Thank you so much!

Yes! If you can't write to the partition post back and I'll tell you how to set permissions so you can.

---

