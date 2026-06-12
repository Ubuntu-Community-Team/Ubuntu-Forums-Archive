---
title: "Booting problem 10.04"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by McTwitch on 2011-05-12
I'm trying to boot to an HDD installed with 10.04, and it normally works. Now, however, when I attempt to boot, it looks like it's about to start, when the Ubuntu load screen comes up, checking for errors. After a few moments, I get this message:
"Errors were found while checking the disk drive for /
Press F to attempt to fix the errors, I to ignore, S to skip mounting or M for manual recovery"

Pressing F to fix, does not, in fact fix it. Instead, I get:
"The disk drive for /tmp is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery"
M gets me no where, and S gets:
"Your disk drives are being checked for errors, this may take some time" After which, it restarts.

---

### Post by lmarmisa on 2011-05-12
Please, boot your system into a Ubuntu Live CD/USB and visit the page

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then, run the Boot Info Script and post here the results.

---

### Post by McTwitch on 2011-05-12
That's with the HDD plugged in, right?

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> That's with the HDD plugged in, right?

Yes, with your HDD plugged in. Is your HDD external?.

---

### Post by McTwitch on 2011-05-12
Yep. At the moment, I'm booting off of a Live CD (10.04), with a Vista machine. I've got the HDD plugged in, and am running the command as we speak.

---

### Post by jtarin on 2011-05-12
> Quote:
Originally Posted by McTwitch View Post
That's with the HDD plugged in, right?

A horse of a different color.......get that boot info script as suggested.

---

### Post by McTwitch on 2011-05-12
Right, ran the command, but got an error.

```
sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

```

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> Right, ran the command, but got an error.

```
sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

```

Maybe you did not download the script file in the Desktop folder. Check where you downloaded it (for example, ~/Downloads).

---

### Post by McTwitch on 2011-05-12
I thought of that. It had been downloaded to the Downloads folder. So I moved it to the desktop, and ran the command again, with the same result.

---

### Post by McTwitch on 2011-05-12
just ran it again. Actually got results this time.
```
        Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    23,987,291    23,905,372   7 HPFS/NTFS
/dev/sda3    *     30,801,920   625,140,399   594,338,480   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc2          81,915,559   625,137,344   543,221,786   5 Extended
/dev/sdc5         615,916,098   625,137,344     9,221,247  82 Linux swap / Solaris
/dev/sdc6          81,915,561   133,114,589    51,199,029  83 Linux
/dev/sdc7         133,114,653   615,916,034   482,801,382  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        68D8B5A5D8B57244                       ntfs       RECOVERY                      
/dev/sda3        4028B7C928B7BBEA                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5                                               swap                                     
/dev/sdc6        fc534f08-16f9-49bb-b4a2-b67ec506eebc   ext4       Lounge-root                   
/dev/sdc7        511b1c51-aab0-4f49-bb6b-a831ee53c9d4   ext4       10.04-home                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc6        /media/Lounge-root       ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7        /media/10.04-home        ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set fc534f08-16f9-49bb-b4a2-b67ec506eebc
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e598f2e1-7205-4fdf-a8a7-16b99e2a6519
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e598f2e1-7205-4fdf-a8a7-16b99e2a6519 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e598f2e1-7205-4fdf-a8a7-16b99e2a6519
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=e598f2e1-7205-4fdf-a8a7-16b99e2a6519 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=fc534f08-16f9-49bb-b4a2-b67ec506eebc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=511b1c51-aab0-4f49-bb6b-a831ee53c9d4 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=10fd3aa7-2241-45ed-b0bb-4299647b7950 none            swap    sw              0       0

=================== sdc6: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/core.img
  60.1GB: boot/grub/grub.cfg
  59.4GB: boot/initrd.img-2.6.32-21-generic
  60.2GB: boot/initrd.img-2.6.32-24-generic
  59.3GB: boot/vmlinuz-2.6.32-21-generic
  59.9GB: boot/vmlinuz-2.6.32-24-generic
  60.2GB: initrd.img
  59.4GB: initrd.img.old
  59.9GB: vmlinuz
  59.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by lmarmisa on 2011-05-12
The results seem good except the "ghost" device /dev/sdb detected by Boot Info Script.

```

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        68D8B5A5D8B57244                       ntfs       RECOVERY                      
/dev/sda3        4028B7C928B7BBEA                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5                                               swap                                     
/dev/sdc6        fc534f08-16f9-49bb-b4a2-b67ec506eebc   ext4       Lounge-root                   
/dev/sdc7        511b1c51-aab0-4f49-bb6b-a831ee53c9d4   ext4       10.04-home                    
/dev/sdc: PTTYPE="dos" 
[COLOR="Red"]error: /dev/sdb: No medium found[/COLOR]
...
=======Devices which don't seem to have a corresponding hard drive==============

[COLOR="red"]sdb[/COLOR]

```

Please, while you are running Ubuntu Live CD (do not try to mount any partition of your external hard drive), open a terminal, and type these commands:

```

mount
sudo fsck /dev/sdc6
sudo fsck /dev/sdc7

```

Finally, pots the results.

---

### Post by McTwitch on 2011-05-12
```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdc6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? 

```

That's slightly worrying. Is that what's supposed to happen?
My next reply will be a tad bit slow. Have to make a run into town. Ten to twenty minutes. Hope you stick around.

---

### Post by lmarmisa on 2011-05-12
Do not continue. 

Reboot into the Ubuntu Live CD and try again the commands. Abort them if you get a similar message.

---

### Post by McTwitch on 2011-05-12
I tried again, and got the warning again.

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> I tried again, and got the warning again.

The external partitions /dev/sdc6 and /dev/sdc7 should be not automouned after a new boot into Ubuntu Live CD.

Please, post the result of the command:

```

mount

```

---

### Post by McTwitch on 2011-05-12
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc7 on /media/10.04-home type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6 on /media/Lounge-root type ext4 (rw,nosuid,nodev,uhelper=udisks)

---

### Post by lmarmisa on 2011-05-12
Thanks.

Try these commands and post the results:

```

sudo umount -f /media/10.04-home
sudo umount -f /media/Lounge-root
mount

```

---

### Post by McTwitch on 2011-05-12
Ran the first two commands, went by smoothly without any output. Then I ran "mount".
```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

---

### Post by lmarmisa on 2011-05-12
Great. Try to repair the partitions now:

```

sudo fsck /dev/sdc6
sudo fsck /dev/sdc7

```

If you do not see too much activity during the repair commands (Pass 1, Pass2 and so on) repeat those commands with the option -f:

```

sudo fsck -f /dev/sdc6
sudo fsck -f /dev/sdc7

```

---

### Post by McTwitch on 2011-05-12
```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Lounge-root contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 2099208 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? 

```

Do I do the force rewrite?

---

### Post by lmarmisa on 2011-05-12
Yes, please.

---

### Post by McTwitch on 2011-05-12
Every time I press the "y" button, the number goes up. I'm up to 2099218, and I started at 2099208. Is that what's supposed to be happening? Also, mind you, I've only run the sdc6 command still.

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> Every time I press the "y" button, the number goes up. I'm up to 2099218, and I started at 2099208. Is that what's supposed to be happening? Also, mind you, I've only run the sdc6 command still.

The system is detecting many errors in your hard drive. Sorry. I do not know a different method for repairing your partitions.

If you wish that fsck repairs your partition automatically without any question, you can use the option -a:

```

sudo fsck -a /dev/sdc6
sudo fsck -a /dev/sdc7

```

---

### Post by McTwitch on 2011-05-12
It won't hurt anything, will it?

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> It won't hurt anything, will it?

The fsck command will try to repair the data structures stored in your external hard drive. This command will not hurt at all your hard drive or any other hardware of your system. The command will try to repair the data structures without deleting any file if that is possible. If the damage were too big, the command fsck would be unable to restore all the files and directories of your damaged partitions and some files or directories would be lost.

Why the data structures are incorrect?. Maybe the system was not properly shutdown or it was unplugged in a unsafe way.

---

### Post by McTwitch on 2011-05-12
Right, I finished the commands (the manual way). What now?

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> Right, I finished the commands (the manual way). What now?

Please, repeat the two fsck commands in order to verify that all errors were fixed.

---

### Post by McTwitch on 2011-05-12
```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Lounge-root: clean, 157694/1602496 files, 1023106/6399878 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sdc7
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
10.04-home: clean, 30831/15089664 files, 35002902/60350172 blocks

```

Looks good.

---

### Post by lmarmisa on 2011-05-12
Sorry if I am too thorough.

Could you repeat these commands with the option -f?

```

sudo fsck -f /dev/sdc6
sudo fsck -f /dev/sdc7

```

---

### Post by McTwitch on 2011-05-12
```
ubuntu@ubuntu:~$ sudo fsck -f /dev/sdc6
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Lounge-root: 157694/1602496 files (0.2% non-contiguous), 1023106/6399878 blocks
ubuntu@ubuntu:~$ sudo fsck -f /dev/sdc7
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
10.04-home: 30831/15089664 files (3.3% non-contiguous), 35002902/60350172 blocks

```

I'm all right with being thorough. Just so long as we don't have to go through this twice, I'm fine with all the double checking.

---

### Post by lmarmisa on 2011-05-12
Your partitions are fixed now.

You could try to boot into Ubuntu normally in order to check if the problem is finally solved.

If the problem continues, please, boot again into Ubuntu Live CD and try to reinstall GRUB using METHOD 3 - CHROOT of this page:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you need to reinstall GRUB, I can send the exact commands to be applied in your case.

---

### Post by McTwitch on 2011-05-12
It says to mount my normal partition. Would that be my / partition, or my /home?

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> It says to mount my normal partition. Would that be my / partition, or my /home?

Sorry. I do not understand. Where do you get that message?.

---

### Post by McTwitch on 2011-05-12
Oh, on the Method 3-Chroot page. I tried the restart, and it didn't work. I got
> error: invalid extent
grub rescue>

---

### Post by lmarmisa on 2011-05-12
> **McTwitch said:**
> Oh, on the Method 3-Chroot page. I tried the restart, and it didn't work. I got

Ok. The partition is root.

If you tell me the results of these two commands, I will send the exact list of commands to type for reinstalling GRUB2:

```

mount
fdisk -l

```

---

### Post by McTwitch on 2011-05-12
> ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc6 on /media/Lounge-root type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7 on /media/10.04-home type ext4 (rw,nosuid,nodev,uhelper=udisks)


and then 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70811d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1494    11952686    7  HPFS/NTFS
/dev/sda3   *        1918       38914   297169240    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e234

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2            5100       38913   271610893    5  Extended
/dev/sdc5           38340       38913     4610623+  82  Linux swap / Solaris
/dev/sdc6            5100        8286    25599514+  83  Linux
/dev/sdc7            8287       38339   241400691   83  Linux

Partition table entries are not in disk order

```

---

### Post by McTwitch on 2011-05-12
I've got to run for the night. I'll pick this back up in the morning, though.

---

### Post by lmarmisa on 2011-05-12
Thanks.

Follow this list of commands. If you detect any problem, please, stop immediately and tell me that problem.

First step: umount the two partitions:

```

sudo umount -f /dev/sdc6
sudo umount -f /dev/sdc7
mount

```

I have added mount in order to check the partitions were umounted.

We will start the procedure now.

Type the following commands:

```

sudo mount /dev/sdc6 /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
update-grub
grub-install /dev/sdc
grub-install --recheck /dev/sdc
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
sudo reboot

```

---

### Post by McTwitch on 2011-05-14
The umounting works, and then the first command of the second bunch work, but when I get to the second 
> sudo mount --bind /dev  /mnt/dev
I end up with ```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
```

---

### Post by lmarmisa on 2011-05-14
According to your comments, I believe that the first command of the second bunch was not correctly completed.

I get the same result in that case:

```

luis@UB1010ENG:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
luis@UB1010ENG:~$ 

```

This other example shows the two first commands working properly:

```

luis@UB1010ENG:~$ sudo mount /dev/sdc6 /mnt
luis@UB1010ENG:~$ sudo mount --bind /dev /mnt/dev
luis@UB1010ENG:~$ 

```

If you wish to verify that the command **sudo mount /dev/sdc6 /mnt** has really mounted the partition **/dev/sdc6**, please add the additional command **mount** after the first command of the second bunch:

```

sudo mount /dev/sdc6 /mnt
mount
sudo mount --bind /dev  /mnt/dev
...

```

---

### Post by McTwitch on 2011-05-15
I added the mount, but I'm still getting the same error.

---

### Post by ranch hand on 2011-05-15
I do not want to butt in here too much.  lmarmisa seems to have a plan.

That said, chrooting into /dev/sdc6 may be easier with these commands, seeing it is a Labeled partition, one at a time  and in this order;
```

sudo mkdir /mnt/Lounge-root
sudo mount /dev/sdc6 /mnt/Lounge-root/
sudo mount -o bind /proc /mnt/Lounge-root/proc
sudo mount -o bind /dev /mnt/Lounge-root/dev
sudo mount -o bind /dev/pts /mnt/Lounge-root/dev/pts
sudo mount -o bind /sys /mnt/Lounge-root/sys
sudo cp /etc/resolv.conf /mnt/Lounge-root/etc/resolv.conf
sudo chroot /mnt/Lounge-root /bin/bash

```
make sure everything is unmounted before doing this.  If not sure reboot, that will do it.

If you are using a 10.04 disk I would run;
```

sudo apt-get update
and then
sudo apt-get upgrade

```
before trying to chroot from it unless it is fairly recent (there has been at least 1 if not 2 step releases of that image).  There was a problem with chroot in at least the first image released.  That is the one I have and I don' t use it.  When doing things like this I am using an old 9.04 disk.

It does not have grub2 on it so the commands for it won't work until I install grub2 but that is quicker than running the update/upgrade on 10.04.   I really should get a more up to date live image of something.

---

### Post by McTwitch on 2011-05-15
Yep, Ranch. They're still named from the last time we mucked about with them. I tried your chroot commands, but at /proc, I got the same error:
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/Lounge-root
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/Lounge-root/
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/Lounge-root/proc
mount: mount point /mnt/Lounge-root/proc does not exist

```Am I doing something wrong?

---

### Post by jtarin on 2011-05-15
> **McTwitch said:**
> Yep, Ranch. They're still named from the last time we mucked about with them. I tried your chroot commands, but at /proc, I got the same error:
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/Lounge-root
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/Lounge-root/
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/Lounge-root/proc
mount: mount point /mnt/Lounge-root/proc does not exist

```Am I doing something wrong?[URL="https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT"]Here is the process for working in the CHROOT environment.
[/URL]

---

### Post by lmarmisa on 2011-05-15
> **McTwitch said:**
> Yep, Ranch. They're still named from the last time we mucked about with them. I tried your chroot commands, but at /proc, I got the same error:
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/Lounge-root
ubuntu@ubuntu:~$ sudo mount [COLOR="Red"]/dev/sdb6[/COLOR] /mnt/Lounge-root/
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/Lounge-root/proc
mount: mount point /mnt/Lounge-root/proc does not exist

```Am I doing something wrong?

Hi McTwitch,

apparently you are trying to mount the partition **/dev/sdb6** but according to Info Boot Script the partition Lounge-root is located in **/dev/sdc6**.

Please, type these two commands and post here the results:

```

sudo mount /dev/sdc6
ls -l /mnt

```

These is the result which I get:

```

ubuntu@ubuntu:~$ sudo mount /dev/sdc6 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 108
drwxr-xr-x   2 root root  4096 2011-05-15 01:10 bin
drwxr-xr-x   3 root root  4096 2011-05-15 01:12 boot
drwxr-xr-x   2 root root  4096 2010-07-26 11:34 cdrom
drwxr-xr-x   4 root root  4096 2010-07-26 11:35 dev
drwxr-xr-x 140 root root 12288 2011-05-15 01:26 etc
drwxr-xr-x   3 root root  4096 2010-07-26 11:35 home
lrwxrwxrwx   1 root root    33 2011-05-15 01:12 initrd.img -> boot/initrd.img-2.6.32-31-generic
lrwxrwxrwx   1 root root    33 2011-04-15 04:42 initrd.img.old -> boot/initrd.img-2.6.32-30-generic
drwxr-xr-x  20 root root 12288 2011-05-15 01:10 lib
drwx------   2 root root 16384 2010-07-26 11:30 lost+found
drwxr-xr-x   3 root root  4096 2011-05-15 01:22 media
drwxr-xr-x   2 root root  4096 2010-04-23 12:11 mnt
drwxr-xr-x   4 root root  4096 2011-05-15 01:15 opt
drwxr-xr-x   2 root root  4096 2010-04-23 12:11 proc
drwx------  11 root root  4096 2011-04-15 04:45 root
drwxr-xr-x   2 root root  4096 2011-05-15 01:17 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 22:55 selinux
drwxr-xr-x   2 root root  4096 2010-04-29 14:17 srv
drwxr-xr-x   2 root root  4096 2010-03-30 09:17 sys
drwxrwxrwt  10 root root  4096 2011-05-15 01:26 tmp
drwxr-xr-x  11 root root  4096 2011-04-16 07:46 usr
drwxr-xr-x  16 root root  4096 2010-08-23 23:46 var
lrwxrwxrwx   1 root root    30 2011-05-15 01:12 vmlinuz -> boot/vmlinuz-2.6.32-31-generic
lrwxrwxrwx   1 root root    30 2011-04-15 04:42 vmlinuz.old -> boot/vmlinuz-2.6.32-30-generic
ubuntu@ubuntu:~$ 


```

---

### Post by ranch hand on 2011-05-16
And you may have a problem with /proc anyway (It does help if you are in the right partition).  I have had, with 10.04, problems mounting /proc.  Don;t use it if it doesn't want to go.  I suspect it is empty anyway.  You don't need it for grub anyway.  I just sent the whole bunch that I use in my script for managing pre-release testing installs.  Never now when you may need it.

---

### Post by McTwitch on 2011-05-16
I went with SDB because that's what it called itself. It seems every time I get on, it's different. SDB, SDC, SDD, etc. I adjusted accordingly.

> ubuntu@ubuntu:~$ sudo mkdir /mnt/Lounge-root
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/Lounge-root/
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/Lounge-root/dev
mount: mount point /mnt/Lounge-root/dev does not exist

Is what I get when running the commands, skipping the /proc one.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> I went with SDB because that's what it called itself. It seems every time I get on, it's different. SDB, SDC, SDD, etc. I adjusted accordingly.

Ok. Please, try to show us the contents of the mounted partition:

```

sudo mount /dev/sdc6 # or /dev/sdb6
ls -l /mnt

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ ls -l /mnt
total 4
drwxr-xr-x 3 root root 4096 2010-11-25 15:54 Lounge-root

```

that's the results from the command given by Imarmisa.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ ls -l /mnt
total 4
drwxr-xr-x 3 root root 4096 2010-11-25 15:54 Lounge-root

```

that's the results from the command given by Imarmisa.

Apparently it exists a folder named Lounge-root on the root of the partition. Please, post the list of files of that folder:

```

ls -l /mnt/Lounge-root

```

---

### Post by jtarin on 2011-05-16
> I went with SDB because that's what it called itself. It seems every time I get on, it's different. SDB, SDC, SDD, etc. I adjusted accordingly.
Are you unplugging this drive or any other external device between boots to cause the target /dev to change like you express?

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ ls -l /mnt/Lounge-root
total 12
lrwxrwxrwx  2 root root   17 2010-11-30 02:57 bin -> liboscar.so.0.0.0
lrwxrwxrwx  2 root root   17 2010-11-30 02:57 etc -> liboscar.so.0.0.0
lrwxrwxrwx  2 root root   33 2010-08-12 18:09 initrd.img -> boot/initrd.img-2.6.32-24-generic
lrwxrwxrwx  2 root root   33 2010-08-12 05:01 initrd.img.old -> boot/initrd.img-2.6.32-21-generic
drwx------ 38 root root 8192 2011-05-13 02:06 lost+found
lrwxrwxrwx  2 root root    7 2010-12-26 21:13 root -> logprof
-rw-r--r--  2 root root 2995 2010-05-15 16:50 rules.log
lrwxrwxrwx  2 root root   30 2010-08-12 18:09 vmlinuz -> boot/vmlinuz-2.6.32-24-generic
lrwxrwxrwx  2 root root   30 2010-08-12 05:01 vmlinuz.old -> boot/vmlinuz-2.6.32-21-generic

```

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ ls -l /mnt/Lounge-root
total 12
lrwxrwxrwx  2 root root   17 2010-11-30 02:57 bin -> liboscar.so.0.0.0
lrwxrwxrwx  2 root root   17 2010-11-30 02:57 etc -> liboscar.so.0.0.0
lrwxrwxrwx  2 root root   33 2010-08-12 18:09 initrd.img -> boot/initrd.img-2.6.32-24-generic
lrwxrwxrwx  2 root root   33 2010-08-12 05:01 initrd.img.old -> boot/initrd.img-2.6.32-21-generic
drwx------ 38 root root 8192 2011-05-13 02:06 lost+found
lrwxrwxrwx  2 root root    7 2010-12-26 21:13 root -> logprof
-rw-r--r--  2 root root 2995 2010-05-15 16:50 rules.log
lrwxrwxrwx  2 root root   30 2010-08-12 18:09 vmlinuz -> boot/vmlinuz-2.6.32-24-generic
lrwxrwxrwx  2 root root   30 2010-08-12 05:01 vmlinuz.old -> boot/vmlinuz-2.6.32-21-generic

```

These results are really odd. Compare them with those of post #45.

It seems that several files and folders were lost too. Could you show us the output of this command?

```

sudo ls -l /mnt/Lounge-root/lost+found

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ sudo ls -l /mnt/Lounge-root/lost+found
total 6592
-rw-r--r-- 1 root root  637588 2011-04-11 22:21 #130921
-rwxr-sr-x 1 root mail    9720 2010-06-25 10:51 #130926
lrwxrwxrwx 1 root root      16 2010-08-12 04:34 #130930 -> libgdbm.so.3.0.0
drwx------ 2 root root    4096 2010-08-22 02:41 #130960
drwx------ 2 root root    4096 2010-09-16 22:47 #131414
lrwxrwxrwx 1 root root      23 2011-01-27 22:57 #131543 -> /tmp/pulse-2L9K88eMlGn7
-r-xr-xr-x 1 root root   29988 2010-11-02 17:57 #132404
-rw-r--r-- 1 root root     786 2010-11-09 00:06 #133220
-rw-r--r-- 1 root root      33 2010-08-17 02:52 #133359
drwxr-xr-x 2 root root    4096 2010-08-22 02:33 #133361
drwxr-xr-x 2 root root    4096 2010-10-10 05:54 #133363
-rw-r--r-- 1 root root     300 2010-09-16 22:49 #133427
-rw-r--r-- 1 root root      32 2010-09-16 22:49 #133468
-rw-r--r-- 1 root root     975 2009-11-09 18:39 #133598
-rw-r--r-- 1 root root     210 2009-11-09 18:39 #133600
-rw-r--r-- 1 root root     247 2010-04-15 15:43 #524518
-rw-r--r-- 1 root root   18669 2010-06-21 17:05 #524619
-rw-r--r-- 1 root root     182 2010-04-15 15:43 #524634
-rw-r--r-- 1 root root     187 2010-04-15 15:43 #524636
-rw-r--r-- 1 root root     248 2010-04-15 15:43 #524640
-rw-r--r-- 1 root root      82 2010-06-18 09:33 #538864
-rw-r--r-- 1 root root    3818 2010-06-18 09:33 #538865
-rw-r--r-- 1 root root     921 2010-03-30 08:26 #555905
-rw-r--r-- 1 root root    1359 2010-03-30 08:26 #555906
-rw-r--r-- 1 root root    1414 2010-03-30 08:26 #555907
-rw-r--r-- 1 root root    1352 2010-03-30 08:26 #555908
-rw-r--r-- 1 root root     921 2010-03-30 08:26 #555909
-rw-r--r-- 1 root root     863 2010-03-30 08:26 #555910
-rw-r--r-- 1 root root    1164 2010-03-30 08:26 #555911
-rw-r--r-- 1 root root    1083 2010-03-30 08:26 #555912
-rw-r--r-- 1 root root     990 2010-03-30 08:26 #555913
-rw-r--r-- 1 root root    1041 2010-03-30 08:26 #555914
-rw-r--r-- 1 root root    1560 2010-03-30 08:26 #555915
-rw-r--r-- 1 root root    1130 2010-03-30 08:26 #555916
-rw-r--r-- 1 root root    1243 2010-03-30 08:26 #555917
-rw-r--r-- 1 root root    1446 2010-03-30 08:26 #555918
-rw-r--r-- 1 root root    1212 2010-03-30 08:26 #555919
-rw-r--r-- 1 root root    1156 2010-03-30 08:26 #555920
-rw-r--r-- 1 root root    1060 2010-03-30 08:26 #555921
-rw-r--r-- 1 root root     379 2010-03-30 08:26 #555922
-rw-r--r-- 1 root root     502 2010-03-30 08:26 #555923
-rw-r--r-- 1 root root    1527 2010-03-30 08:26 #555924
-rw-r--r-- 1 root root    1156 2010-03-30 08:26 #555925
-rw-r--r-- 1 root root    1300 2010-03-30 08:26 #555926
-rw-r--r-- 1 root root    1577 2010-03-30 08:26 #555927
-rw-r--r-- 1 root root    1215 2010-03-30 08:26 #555928
-rw-r--r-- 1 root root    1335 2010-03-30 08:26 #555929
-rw-r--r-- 1 root root    1338 2010-03-30 08:26 #555930
-rw-r--r-- 1 root root     836 2010-03-30 08:26 #555931
-rw-r--r-- 1 root root    2369 2010-03-30 08:26 #555932
-rw-r--r-- 1 root root    1858 2010-03-30 08:26 #555933
-rw-r--r-- 1 root root     863 2010-03-30 08:26 #555934
-rw-r--r-- 1 root root     796 2010-03-30 08:26 #555935
-rw-r--r-- 1 root root     861 2010-03-30 08:26 #555936
-rw-r--r-- 1 root root     756 2010-03-30 08:26 #555937
-rw-r--r-- 1 root root     911 2010-03-30 08:26 #555938
-rw-r--r-- 1 root root     965 2010-03-30 08:26 #555939
-rw-r--r-- 1 root root     977 2010-03-30 08:26 #555940
-rw-r--r-- 1 root root     874 2010-03-30 08:26 #555941
-rw-r--r-- 1 root root     667 2010-03-30 08:26 #555942
-rw-r--r-- 1 root root    1793 2010-03-30 08:26 #555943
-rw-r--r-- 1 root root    1152 2010-03-30 08:26 #555944
-rw-r--r-- 1 root root    1464 2010-03-30 08:26 #555945
-rw-r--r-- 1 root root    1125 2010-03-30 08:26 #555946
-rw-r--r-- 1 root root    2920 2010-03-30 08:26 #555947
-rw-r--r-- 1 root root     824 2010-03-30 08:26 #555948
-rw-r--r-- 1 root root    1005 2010-03-30 08:26 #555949
-rw-r--r-- 1 root root     731 2010-03-30 08:26 #555950
-rw-r--r-- 1 root root    2749 2010-03-30 08:26 #555951
-rw-r--r-- 1 root root    1123 2010-03-30 08:26 #555952
-rw-r--r-- 1 root root    1261 2010-03-30 08:26 #555953
-rw-r--r-- 1 root root     684 2010-03-30 08:26 #555954
-rw-r--r-- 1 root root     624 2010-03-30 08:26 #555955
-rw-r--r-- 1 root root     672 2010-03-30 08:26 #555956
-rw-r--r-- 1 root root     694 2010-03-30 08:26 #555957
-rw-r--r-- 1 root root    1882 2010-03-30 08:26 #555958
-rw-r--r-- 1 root root    1429 2010-03-30 08:26 #555959
-rw-r--r-- 1 root root    1113 2010-03-30 08:26 #555960
-rw-r--r-- 1 root root    1536 2010-03-30 08:26 #555961
-rw-r--r-- 1 root root    1455 2010-03-30 08:26 #555962
-rw-r--r-- 1 root root    1034 2010-03-30 08:26 #555963
-rw-r--r-- 1 root root    3129 2010-03-30 08:26 #555964
-rw-r--r-- 1 root root     805 2010-03-30 08:26 #555965
-rw-r--r-- 1 root root     921 2010-03-30 08:26 #555966
-rw-r--r-- 1 root root     708 2010-03-30 08:26 #555967
-rw-r--r-- 1 root root    1015 2010-03-30 08:26 #555968
-rw-r--r-- 1 root root     990 2010-03-30 08:26 #555969
-rw-r--r-- 1 root root    1312 2010-03-30 08:26 #555970
-rw-r--r-- 1 root root    1462 2010-03-30 08:26 #555971
-rw-r--r-- 1 root root     862 2010-03-30 08:26 #555972
-rw-r--r-- 1 root root    1145 2010-03-30 08:26 #555973
-rw-r--r-- 1 root root    1013 2010-03-30 08:26 #555974
-rw-r--r-- 1 root root    1074 2010-03-30 08:26 #555975
-rw-r--r-- 1 root root    1464 2010-03-30 08:26 #555976
-rw-r--r-- 1 root root     545 2010-03-30 08:26 #555977
-rw-r--r-- 1 root root    1016 2010-03-30 08:26 #555978
-rw-r--r-- 1 root root    2313 2010-03-30 08:26 #555979
-rw-r--r-- 1 root root    1293 2010-03-30 08:26 #555980
-rw-r--r-- 1 root root     836 2010-03-30 08:26 #555981
-rw-r--r-- 1 root root    1719 2010-03-30 08:26 #555982
-rw-r--r-- 1 root root    2195 2010-03-30 08:26 #555983
-rw-r--r-- 1 root root     720 2010-03-30 08:26 #555984
-rw-r--r-- 1 root root    1368 2010-03-30 08:26 #555985
-rw-r--r-- 1 root root    1253 2010-03-30 08:26 #555986
-rw-r--r-- 1 root root    1239 2010-03-30 08:26 #555987
-rw-r--r-- 1 root root    1245 2010-03-30 08:26 #555988
-rw-r--r-- 1 root root     974 2010-03-30 08:26 #555989
-rw-r--r-- 1 root root     993 2010-03-30 08:26 #555990
-rw-r--r-- 1 root root    1240 2010-03-30 08:26 #555991
-rw-r--r-- 1 root root    1153 2010-03-30 08:26 #555992
-rw-r--r-- 1 root root    1103 2010-03-30 08:26 #555993
-rw-r--r-- 1 root root    1155 2010-03-30 08:26 #555994
-rw-r--r-- 1 root root     708 2010-03-30 08:26 #555995
-rw-r--r-- 1 root root    1525 2010-03-30 08:26 #555996
-rw-r--r-- 1 root root    1480 2010-03-30 08:26 #555997
-rw-r--r-- 1 root root    1493 2010-03-30 08:26 #555998
-rw-r--r-- 1 root root    1409 2010-03-30 08:26 #555999
-rw-r--r-- 1 root root    2527 2010-03-30 08:26 #556000
-rw-r--r-- 1 root root    1994 2010-03-30 08:26 #556001
-rw-r--r-- 1 root root    1601 2010-03-30 08:26 #556002
-rw-r--r-- 1 root root    1129 2010-03-30 08:26 #556003
-rw-r--r-- 1 root root    1134 2010-03-30 08:26 #556004
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556005
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556007
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556008
drwxr-xr-x 2 root root    4096 2010-04-29 12:20 #556011
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556013
drwxr-xr-x 3 root root    4096 2010-04-29 12:23 #556015
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556016
-rw-r--r-- 1 root root     983 2010-03-30 20:14 #556017
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556402
drwxr-xr-x 2 root root    4096 2010-08-12 17:30 #556406
drwxr-xr-x 2 root root    4096 2010-08-12 17:30 #556407
drwxr-xr-x 2 root root    4096 2010-08-12 17:29 #556432
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556434
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556436
drwxr-xr-x 2 root root    4096 2010-04-29 12:20 #556437
drwxr-xr-x 2 root root    4096 2010-04-29 12:23 #556444
-rw-r--r-- 1 root root    6152 2010-07-07 15:07 #654217
-rw-r--r-- 1 root root  609731 2010-12-06 11:11 #654236
-rw-r--r-- 1 root root   13684 2010-07-07 20:13 #915716
-rw-r--r-- 1 root root    5452 2010-07-07 20:13 #915727
-rw-r----- 1 root lp        91 2011-01-31 02:16 #915735
-rwxr-xr-x 1 root root 1269432 2010-04-22 20:04 #915740
-rw-r--r-- 1 root root     181 2010-10-06 02:52 #915803
lrwxrwxrwx 1 root root       8 2010-08-12 04:34 #915851 -> 2to3-2.6
lrwxrwxrwx 1 root root       7 2010-08-12 04:34 #915882 -> cpp-4.4
-rw-r--r-- 1 root root   13648 2010-07-07 20:13 #915952
-rw-r--r-- 1 root root   13752 2010-07-07 20:13 #915953
-rw-r--r-- 1 root root    5440 2010-07-07 20:13 #915954
-rw-r--r-- 1 root root   13684 2010-07-07 20:13 #915955
-rw-r--r-- 1 root root    5400 2010-07-07 20:13 #915956
-rw-r--r-- 1 root root   13716 2010-07-07 20:13 #915957
-rw-r--r-- 1 root root    9576 2010-07-07 20:13 #915958
-rw-r--r-- 1 root root    9520 2010-07-07 20:13 #915959
-rw-r--r-- 1 root root   13668 2010-07-07 20:13 #915960
-rw-r--r-- 1 root root   17868 2010-07-07 20:13 #915961
-rw-r--r-- 1 root root    9548 2010-07-07 20:13 #915962
-rw-r--r-- 1 root root    5416 2010-07-07 20:13 #915963
-rw-r--r-- 1 root root    5412 2010-07-07 20:13 #915964
-rw-r--r-- 1 root root    9524 2010-07-07 20:13 #915965
-rw-r--r-- 1 root root    9540 2010-07-07 20:13 #915966
-rw-r--r-- 1 root root    9560 2010-07-07 20:13 #915967
-rw-r--r-- 1 root root   34452 2010-07-07 20:13 #915968
-rwxr-xr-x 1 root root   22148 2010-05-03 13:59 #916015
-rwxr-xr-x 1 root root    7650 2010-05-03 13:58 #916016
-rwxr-xr-x 1 root root   30416 2010-06-08 08:23 #916019
-rwxr-xr-x 1 root root    9668 2010-06-08 08:23 #916020
-rwxr-xr-x 1 root root    5516 2010-06-08 08:23 #916021
-rwxr-xr-x 1 root root    5528 2010-06-08 08:23 #916022
-rwxr-xr-x 1 root root   17756 2010-11-12 18:05 #916465
-rwxr-xr-x 1 root root   30048 2010-11-12 18:05 #916466
-rwxr-xr-x 1 root root   13664 2010-11-12 18:05 #916469
-rw-r--r-- 1 root root    5416 2010-07-07 20:13 #919718
-rw-r--r-- 1 root root    5384 2010-07-07 20:13 #919719
-rw-r--r-- 1 root root   13744 2010-07-07 20:13 #919720
-rw-r--r-- 1 root root    5400 2010-07-07 20:13 #919721
-rw-r--r-- 1 root root    5392 2010-07-07 20:13 #919722
-rw-r--r-- 1 root root    9524 2010-07-07 20:13 #919723
-rw-r--r-- 1 root root   17816 2010-07-07 20:13 #919724
-rw-r--r-- 1 root root    9604 2010-07-07 20:13 #919725
-rw-r--r-- 1 root root    5412 2010-07-07 20:13 #919726
-rw-r--r-- 1 root root   13624 2010-07-07 20:13 #919727
-rw-r--r-- 1 root root    9556 2010-07-07 20:13 #919728
lrwxrwxrwx 1 root root      29 2010-08-28 16:31 #919729 -> /etc/alternatives/traceroute6
lrwxrwxrwx 1 root root      28 2010-08-28 16:31 #919730 -> /etc/alternatives/traceproto
lrwxrwxrwx 1 root root      34 2010-08-28 16:31 #919731 -> /etc/alternatives/traceroute-nanog
lrwxrwxrwx 1 root root      31 2010-08-28 16:31 #919732 -> /etc/alternatives/tcptraceroute
-rw-r--r-- 1 root root   68536 2008-08-16 02:06 #919741
lrwxrwxrwx 1 root root      16 2010-08-30 00:24 #919742 -> libfaac.so.0.0.0
-rwxr-xr-x 1 root root   17704 2010-11-12 18:05 #919762
-rwxr-xr-x 1 root root    1791 2010-11-12 18:05 #919763
-rwxr-xr-x 1 root root   34144 2010-11-12 18:05 #919765
-rwxr-xr-x 1 root root   13668 2010-11-12 18:05 #919767
-rwxr-xr-x 1 root root   25948 2010-11-12 18:05 #919769
-rwxr-xr-x 1 root root   25900 2010-11-12 18:05 #919771
-rwxr-xr-x 1 root root     502 2010-11-12 18:05 #919773
-rwxr-xr-x 1 root root   42332 2010-11-12 18:05 #919775
-rwxr-xr-x 1 root root   17892 2010-11-12 18:05 #919933
-rwxr-xr-x 1 root root   25948 2010-11-12 18:05 #919935
-rwxr-xr-x 1 root root   25896 2010-11-12 18:05 #919936
-rw-r--r-- 1 root root    2390 2010-11-12 18:05 #919937
-rwxr-xr-x 1 root root   26464 2010-11-12 18:05 #919938
-rwxr-xr-x 1 root root   34144 2010-11-12 18:05 #919939
-rwxr-xr-x 1 root root   25896 2010-11-12 18:05 #919940
-rwxr-xr-x 1 root root   30052 2010-11-12 18:05 #919941
-rwxr-xr-x 1 root root    5468 2010-11-12 18:05 #919942
-rwxr-xr-x 1 root root    2702 2010-11-12 18:05 #919943
-rwxr-xr-x 1 root root    3370 2010-11-12 18:05 #919944
-rw-r--r-- 1 root root    9564 2010-02-19 06:07 #920030
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920074
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920075
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920076
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920077
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920078
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920079
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920080
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920081
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920082
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920083
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920084
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920085
drwxr-xr-x 2 root root    4096 2010-04-29 12:18 #920086
drwxr-xr-x 3 root root    4096 2010-04-29 12:18 #920125
drwxr-xr-x 5 root root    4096 2010-12-26 21:14 #920170
drwxr-xr-x 3 root root   12288 2010-12-26 21:13 #920171
drwxr-xr-x 2 root root   12288 2010-12-26 21:13 #920172
-rwxr-xr-x 1 root root     145 2010-03-28 23:02 #920173
-rwxr-xr-x 1 root root    9640 2010-04-22 18:55 #920176
-rwxr-xr-x 1 root root    2854 2010-03-15 11:58 #920178
-rwxr-xr-x 1 root root     583 2010-04-22 19:15 #920184
-rwxr-xr-x 1 root root    9700 2010-04-09 10:43 #920187
-rwxr-xr-x 1 root root   30432 2010-04-09 10:43 #920188
-rwxr-xr-x 1 root root    9756 2010-03-07 03:49 #920194
-rwxr-xr-x 1 root root   17916 2010-03-07 03:49 #920195
-rwxr-xr-x 1 root root    1695 2010-03-05 19:38 #920353
-rwxr-xr-x 1 root root   15409 2010-03-05 19:38 #920354
-rw-r----- 1 root root    1263 2010-04-29 12:26 #920355
-rw-r----- 1 root root     533 2010-04-29 12:26 #920356
-rw-r--r-- 1 root root    5548 2010-03-05 21:02 #920357
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920358
-rw-r--r-- 1 root root    5552 2010-03-05 21:02 #920359
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920360
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920361
-rw-r--r-- 1 root root    5496 2010-03-05 21:02 #920362
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920363
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920364
-rw-r--r-- 1 root root    5544 2010-03-05 21:02 #920365
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920366
-rw-r--r-- 1 root root    9680 2010-03-05 21:02 #920367
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920368
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920369
-rw-r--r-- 1 root root    9648 2010-03-05 21:02 #920370
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920371
-rw-r--r-- 1 root root    5548 2010-03-05 21:02 #920372
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920373
-rw-r--r-- 1 root root    5556 2010-03-05 21:02 #920374
-rw-r--r-- 1 root root    5500 2010-03-05 21:02 #920375
-rw-r--r-- 1 root root    5584 2010-03-05 21:02 #920376
-rw-r--r-- 1 root root    5552 2010-03-05 21:02 #920377
-rw-r--r-- 1 root root    9648 2010-03-05 21:02 #920378
-rw-r--r-- 1 root root    9644 2010-03-05 21:02 #920379
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920380
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920381
-rw-r--r-- 1 root root    5548 2010-03-05 21:02 #920382
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920383
-rw-r--r-- 1 root root    9708 2010-03-05 21:02 #920384
-rw-r--r-- 1 root root    5576 2010-03-05 21:02 #920385
-rw-r--r-- 1 root root    5544 2010-03-05 21:02 #920386
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920387
-rw-r--r-- 1 root root    9704 2010-03-05 21:02 #920388
-rw-r--r-- 1 root root    9672 2010-03-05 21:02 #920389
-rw-r--r-- 1 root root    5544 2010-03-05 21:02 #920390
-rw-r--r-- 1 root root    5496 2010-03-05 21:02 #920391
-rw-r--r-- 1 root root    5552 2010-03-05 21:02 #920392
-rw-r--r-- 1 root root   14032 2010-03-05 21:02 #920393
-rw-r--r-- 1 root root    5652 2010-03-05 21:02 #920394
-rw-r--r-- 1 root root    5644 2010-03-05 21:02 #920395
-rw-r--r-- 1 root root    9932 2010-03-05 21:02 #920396
-rw-r--r-- 1 root root    9772 2010-03-05 21:02 #920397
-rw-r--r-- 1 root root    5648 2010-03-05 21:02 #920398
-rw-r--r-- 1 root root    5596 2010-03-05 21:02 #920399
-rw-r--r-- 1 root root    9648 2010-03-05 21:02 #920400
-rw-r--r-- 1 root root    5552 2010-03-05 21:02 #920401
-rw-r--r-- 1 root root    5644 2010-03-05 21:02 #920402
-rw-r--r-- 1 root root    9748 2010-03-05 21:02 #920403
-rw-r--r-- 1 root root    9836 2010-03-05 21:02 #920404
-rw-r--r-- 1 root root    5548 2010-03-05 21:02 #920405
-rw-r--r-- 1 root root    5496 2010-03-05 21:02 #920406
-rw-r--r-- 1 root root    9644 2010-03-05 21:02 #920407
-rw-r--r-- 1 root root    5612 2010-03-05 21:02 #920408
-rw-r--r-- 1 root root    9708 2010-03-05 21:02 #920409
-rw-r--r-- 1 root root    9708 2010-03-05 21:02 #920410
-rw-r--r-- 1 root root    5740 2010-03-05 21:02 #920411
-rw-r--r-- 1 root root   22156 2010-03-05 21:02 #920412
-rw-r--r-- 1 root root    9736 2010-03-05 21:02 #920413
-rw-r--r-- 1 root root    9704 2010-03-05 21:02 #920414
-rw-r--r-- 1 root root    5640 2010-03-05 21:02 #920415
-rw-r--r-- 1 root root   18092 2010-03-05 21:02 #920416
-rw-r--r-- 1 root root    5608 2010-03-05 21:02 #920417
-rw-r--r-- 1 root root    9804 2010-03-05 21:02 #920418
-rw-r--r-- 1 root root    5576 2010-03-05 21:02 #920419
-rw-r--r-- 1 root root    5576 2010-03-05 21:02 #920420
-rw-r--r-- 1 root root    5608 2010-03-05 21:02 #920421
-rw-r--r-- 1 root root    5608 2010-03-05 21:02 #920422
-rw-r--r-- 1 root root    9868 2010-03-05 21:02 #920423
-rw-r--r-- 1 root root   13960 2010-03-05 21:02 #920424
-rw-r--r-- 1 root root    9708 2010-03-05 21:02 #920425
-rw-r--r-- 1 root root    5548 2010-03-05 21:02 #920426
-rw-r--r-- 1 root root   13832 2010-03-05 21:02 #920427
-rw-r--r-- 1 root root    5544 2010-03-05 21:02 #920428
-rw-r--r-- 1 root root    9676 2010-03-05 21:02 #920429
-rw-r--r-- 1 root root    9704 2010-03-05 21:02 #920430
-rw-r--r-- 1 root root   13864 2010-03-05 21:02 #920431
-rw-r--r-- 1 root root    5492 2010-03-05 21:02 #920432
-rw-r--r-- 1 root root    5500 2010-03-05 21:02 #920433
-rw-r--r-- 1 root root    5608 2010-03-05 21:02 #920434
-rw-r--r-- 1 root root    9644 2010-03-05 21:02 #920435
-rw-r--r-- 1 root root    9736 2010-03-05 21:02 #920436
-rw-r--r-- 1 root root    9736 2010-03-05 21:02 #920437
-rw-r--r-- 1 root root    5640 2010-03-05 21:02 #920438
-rw-r--r-- 1 root root   13768 2010-03-05 21:02 #920439
-rw-r--r-- 1 root root    9768 2010-03-05 21:02 #920440
-rw-r--r-- 1 root root    9640 2010-03-05 21:02 #920441
-rw-r--r-- 1 root root    9736 2010-03-05 21:02 #920442
lrwxrwxrwx 1 root root      24 2010-11-30 02:57 #923650 -> ../bin/dpkg-statoverride
-rwxr-xr-x 1 root root  952660 2010-09-09 18:35 #923651
-rw-r--r-- 1 root root   11577 2010-06-03 06:25 #923653
lrwxrwxrwx 1 root root      24 2010-08-12 17:28 #923655 -> ure/lib/libuno_cppu.so.3
lrwxrwxrwx 1 root root      34 2010-08-12 17:28 #923657 -> ure/lib/libuno_cppuhelpergcc3.so.3
-rwxr-xr-x 1 root root   26256 2010-09-09 22:24 #923658
-rwxr-xr-x 1 root root  174328 2010-05-19 16:31 #923668
-rwxr-xr-x 1 root root   87488 2010-05-19 16:31 #923669
-rwxr-xr-x 1 root root   88040 2010-05-19 16:31 #923670
-rw-r--r-- 1 root root    1914 2010-09-16 18:16 #926597
-rw-r--r-- 1 root root    2018 2010-09-16 18:16 #926598
-rw-r--r-- 1 root root    2106 2010-09-16 18:16 #926599
-rw-r--r-- 1 root root     824 2010-09-16 18:16 #926600
-rw-r--r-- 1 root root    5302 2010-09-16 18:16 #926601
-rw-r--r-- 1 root root    5302 2010-09-16 18:16 #926602

```

---

### Post by lmarmisa on 2011-05-16
I see very strange things here.

The device where your external hard drive is assigned changes between boots. A root folder named Lounge-root appears on the partition /dev/sdc6. The files and folders of this partition look corrupted.

I hope that the files and folders of the home partition are good.

Take a look to /media/10.04-home:

```

ls -l /media/10.04-home

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ ls -l /media/10.04-home
ls: cannot access /media/10.04-home: No such file or directory

```
This isn't reassuring.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ ls -l /media/10.04-home
ls: cannot access /media/10.04-home: No such file or directory

```
This isn't reassuring.

Maybe you umounted the home partition using the commands of the first bunch.

If so, reboot into the Live CD and try the command again

```

ls -l /media/10.04-home

```

---

### Post by McTwitch on 2011-05-16
Rebooted and tried again, only to be met with the same result.
```
ubuntu@ubuntu:~$ ls -l /media/10.04-home
ls: cannot access /media/10.04-home: No such file or directory

```

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> Rebooted and tried again, only to be met with the same result.
```
ubuntu@ubuntu:~$ ls -l /media/10.04-home
ls: cannot access /media/10.04-home: No such file or directory

```

Ok, thanks. 

Try these other commands:

```

mount
ls -l /media

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ ls -l /media
total 0

```
That's even less reassuring.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ ls -l /media
total 0

```
That's even less reassuring.

The behavior of your system is now different. I suppose you have plugged-in your external HD.

Check this command:

```

sudo fdisk -l

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70811d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1494    11952686    7  HPFS/NTFS
/dev/sda3   *        1918       38914   297169240    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e234

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            5100       38913   271610893    5  Extended
/dev/sdb5           38340       38913     4610623+  82  Linux swap / Solaris
/dev/sdb6            5100        8286    25599514+  83  Linux
/dev/sdb7            8287       38339   241400691   83  Linux

Partition table entries are not in disk order

```

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70811d92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1494    11952686    7  HPFS/NTFS
/dev/sda3   *        1918       38914   297169240    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005e234

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            5100       38913   271610893    5  Extended
/dev/sdb5           38340       38913     4610623+  82  Linux swap / Solaris
/dev/sdb6            5100        8286    25599514+  83  Linux
/dev/sdb7            8287       38339   241400691   83  Linux

Partition table entries are not in disk order

```

Not too bad news now. The partitions are detected, but they are not auto-mounted now. Why?. This is another mistery. :D

Try these commands:

```

sudo mount /dev/sdb7 /mnt
mount
ls -l /mnt

```

---

### Post by McTwitch on 2011-05-16
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb7 /mnt
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb7 on /media/10.04-home type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6 on /media/Lounge-root type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb7 on /mnt type ext4 (rw)
ubuntu@ubuntu:~$ ls -l /mnt
total 20
drwxr-xr-x 79 1000 1000  4096 2011-05-12 23:25 jeremy
drwx------  2 root root 16384 2010-08-11 18:59 lost+found

```

---

### Post by ranch hand on 2011-05-16
> **lmarmisa said:**
> Not too bad news now. The partitions are detected, but they are not auto-mounted now. Why?. This is another mistery. :D

Try these commands:

```

sudo mount /dev/sdb7 /mnt
mount
ls -l /mnt

```
Where in flinderation is sdb1?

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> ```
ubuntu@ubuntu:~$ sudo mount /dev/sdb7 /mnt
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb7 on /media/10.04-home type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb6 on /media/Lounge-root type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb7 on /mnt type ext4 (rw)
ubuntu@ubuntu:~$ ls -l /mnt
total 20
drwxr-xr-x 79 1000 1000  4096 2011-05-12 23:25 jeremy
drwx------  2 root root 16384 2010-08-11 18:59 lost+found

```

The home partition looks good and I suppose your data will be safe there.

```

find /mnt

```

---

### Post by McTwitch on 2011-05-16
I don't think there is an SDB1.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> I don't think there is an SDB1.

Did you delete the partition sdb1 in the past (for example, using gparted)?.

---

### Post by McTwitch on 2011-05-16
I can't remember how it came about. I think I had an install on SDB1 that I don't have anymore. Now, I'm running on 6, 7 and 5, all within the extended partition, SDB2.

---

### Post by lmarmisa on 2011-05-16
I think it's time for closing this long thread.

So, I will propose a solution.

I recommend a new installation of Ubuntu. In order to be sure that all the files of the home partition are not touched during this new install, I propose to follow a two steps installation.

During the first step, I recommend to install Ubuntu in the existing partition /dev/sdb6. You have to chose the manual option for defining partitions and then select /dev/sda6 and edit it as ext4, root mounting point (/) and ticking the box for formating the partition too. Do not define any particular partition for home during this install. 

**Important: the GRUB loader MUST be stored in the MBR of the external hard drive /dev/sdb. So, do no forget to change the default device from /dev/sda to /dev/sdb !!!.**

In a second step, I recommend to modify the file /etc/fstab in such a way that the partition /dev/sda7 is used for home.

I would like to know the opinion of other colleagues about this proposal.

Best regards,

Luis

---

### Post by ranch hand on 2011-05-16
I would use his current home as home and make very sure that it is not set to be formatted.  I would remove all hidden files from the /home/<usr name> directory.

That way on install the hidden (config files) will be generated where they belong.  The data should be safe although back up is always a good idea.

I would also copy some system files to /home too.  I like /var/cache/apt/archive so that I know what I want to reinstall.  There are others that may want to be kept.

If the install just goes on to the / partition all config files and a complete /home directory will be created on the / directory.  This is a pain to straighten out.

---

### Post by lmarmisa on 2011-05-16
If the hidden files of the /home/user directory are removed, then all the personal configurations would be lost. For example, the bookmarks of Firefox.

I think that those hidden files and folders are valuable and they have to be preserved during the installation.

I do not see any problem to do a fresh install during step 1 and then to remap /home to the old partition /home located in /dev/sdb7 during step 2. I propose to reinstall the same version of Ubuntu defining the same user as before. So, the programs of the new installation will be able to run with the existing user configurations. No configuration will be lost following my procedure.

---

### Post by ranch hand on 2011-05-16
You could move them but that is also going to be where the new user is set up.  Better to get rid of them, even to a file somewhere, an let the new install do it cleanly.

Then you can put it back if you want.  The bookmarks for instance I transfer to most of my installs so that no matter where I am the bookmarks are about the same.  You can either just plug it in the file or retrieve it through the browser menu from the file you save it in.

---

### Post by McTwitch on 2011-05-16
This is my main install, so there's a lot of configuration and files that I would like to keep. Which ever way is the best to do this, is the one that I'd like to op for.

---

### Post by lmarmisa on 2011-05-16
> **McTwitch said:**
> This is my main install, so there's a lot of configuration and files that I would like to keep. Which ever way is the best to do this, is the one that I'd like to op for.

I think that my recommendation is valid and it does not remove any file from your current home partition. But I accept other opinions too.

Anyway, I recommend to make a backup of the home partition /dev/sdb7.

---

### Post by Cfhs_1 on 2011-05-16
> **McTwitch said:**
> This is my main install, so there's a lot of configuration and files that I would like to keep. Which ever way is the best to do this, is the one that I'd like to op for.

I've been watching this thread since you started it, and I would have to say lmarmisa's reinstall method sounds like the most straight forward and safe method. I'd go with that one if I were you. :D

Sorry for butting in, just my $0.02

---

### Post by ranch hand on 2011-05-16
> **lmarmisa said:**
> I think that my recommendation is valid and it does not remove any file from your current home partition. But I accept other opinions too.

Anyway, I recommend to make a backup of the home partition /dev/sdb7.
My main concern here is that due to some unknown cause a whole lot of the system was corrupted.  It is easier to get corrupted ~/.whatever files than / files.

The other day a gal on another forum had lost her Gimp tools menu.  Removed and reinstalled Gimp.  Same deal.  A simple removal of ~/.gimp and running "dpkg-reconfigure gimp brought full function back to her Gimp install.

I have tested Ubuntu pre-release OS' for a while (currently 11.10).  You try to avoid reinstallation but when you do, you are doing it because of corrupted files.  You want nothing left that could be a problem.  I never did but many folks have 3 or 4 testing installs sharing the same /home partition to save space (you need completely different user names for each install).  What I am suggesting is the method that those folks use unless they just wipe that entire user out.

I always had room for individual 2 partition installs for each testing OS.

I have also converted a single partition OS to 2 partitions.  This is basically what is going to have to be done if every thing is installed on the / partition.  I think it is a royal pain.

This is the wonderful thing about Linux.  There are about 14 different ways to do anything and the user has the choice.  They all work.  What fits your personality, experience, what you had for breakfast is what you want to use.

Just think, we could be using Win JerryLewis Pro.  There is only one way to do anything on that monster.  What a drag.

Linux is not only a great platform but it is even FUN when it does get screwed.

---

### Post by McTwitch on 2011-05-17
Well, I've come to a conclusion, and it might seem like the cowards way out, but eh. I'm going to drag everything that I want to keep over to my laptop, and from there just format the HDD, and install...well, I'm looking at Debian, 10.04, or maybe even 11.04. Just depends on what I have for breakfast, I guess.

---

