---
title: "Can't boot after Ubuntu Dual Boot Install w/ XP"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by gregin_az on 2009-12-30
Okay, looks like I'm another victim,  I've read scads of threads on various forums and have made some progress towards solving my problem, but not solved.  I'm really hoping somebody can give me a hand.  Computer literate, but Linux Illiterate.    Learning as I go.

Had XP running on a machine fine with a total of 3 hard drives and 1 MyBook.

1) C:\ XP installed
2) D:\ Data
3) E:\ Data
4) Mybook: Data

Latest Ubuntu install seemed to work fine until I went to boot and I get the error:

Grub Loading
Error: No Such Disk
Grub Rescue

Ran the script recommended in forums and came up with this:
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=a8691c7e-6fbe-4a07-b80a-985f2f67326a)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 185.3 GB, 185283624960 bytes
255 heads, 63 sectors/track, 22526 cylinders, total 361882080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe25de25d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc109c109

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   443,169,089   443,169,027   7 HPFS/NTFS
/dev/sdb2         443,169,090   625,137,344   181,968,255   5 Extended
/dev/sdb5         443,169,153   622,149,254   178,980,102  83 Linux
/dev/sdb6         622,149,318   625,137,344     2,988,027  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x020bfe00

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   398,283,479   398,283,417   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="503CE30C3CE2EC42" TYPE="ntfs" 
sdb1: UUID="4434A9E934A9DDE4" LABEL="AUX_STORAGE" TYPE="ntfs" 
sdb5: UUID="a8691c7e-6fbe-4a07-b80a-985f2f67326a" TYPE="ext4" 
sdb6: UUID="78675400-f990-4a5f-8f9c-8de3a3b8dc5d" TYPE="swap" 
sdc1: UUID="5CD497CFD497A9B2" LABEL="New Volume" TYPE="ntfs" 
sdd1: UUID="3628A08A28A04AA7" LABEL="My Book" TYPE="ntfs" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set a8691c7e-6fbe-4a07-b80a-985f2f67326a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set a8691c7e-6fbe-4a07-b80a-985f2f67326a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a8691c7e-6fbe-4a07-b80a-985f2f67326a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set a8691c7e-6fbe-4a07-b80a-985f2f67326a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a8691c7e-6fbe-4a07-b80a-985f2f67326a ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 503ce30c3ce2ec42
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=a8691c7e-6fbe-4a07-b80a-985f2f67326a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=78675400-f990-4a5f-8f9c-8de3a3b8dc5d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 226.9GB: boot/grub/core.img
 226.9GB: boot/grub/grub.cfg
 226.9GB: boot/initrd.img-2.6.31-14-generic
 226.9GB: boot/vmlinuz-2.6.31-14-generic
 226.9GB: initrd.img
 226.9GB: vmlinuz

---

### Post by lindsay7 on 2009-12-31
Try this first. Type in the terminal

"sudo update-grub" without the quotation marks


If that does not work, check you bios setting and make sure you are booting off of the first drive where windows is.

---

### Post by gregin_az on 2009-12-31
Starting to get a little desperate, but not giving up. Good news, I think I'm getting close to knowing what the issue is, but can't figure out what action to take.
 
I've continued forum research and found a section on using the Grub 2 rescue prompt to try and assess why the computer isn't booting. It's leading me to the step of checking to see if the appropriate files are present.
 
I'm using the 'set' and 'ls' commands to evaluate the file structures on the installed hard drives.
 
I enter ls and get:
 
(hd0), (hd0,1), (hd1,1), (hd2), (hd2,1), fd0
 
I do root =(hdx,y) changing the x,y values for each possible hard drive.
 
Then, for each instance, I enter ls /boot
 
EVERY time I get the message error: unknownfilesystem. I would think I would see some files. 
 
Is this related to my complete inability to boot? Or am I flubbing the commands. Please help. I don't want to revert to a total install of XP.
 
Many thanks for any suggestions.

---

### Post by gregin_az on 2009-12-31
> **lindsay7 said:**
> Try this first. Type in the terminal
 
"sudo update-grub" without the quotation marks
 
 
If that does not work, check you bios setting and make sure you are booting off of the first drive where windows is.
 
Thanks for the reply, Lindsay.  I didn't see your message before I posted my other reply to bump the thread.  Either way, I get the following message when I enter:
 
sudo update grub
 
grub-probe: error: cannot find a device for /.
 
Haven't yet evaluated the bios setting, but none of that was changed before the install of Ubuntu.  I will take a look all the same.

---

### Post by gregin_az on 2009-12-31
Okay, progress, but no solution. HELP . . . Please!
 
Burned and booted from Super Grub. Short story is I can manually boot windows from SG, but can't under any attempt boot Ubuntu. I keep getting "files not found" messages. Leads me to believe I have a faulty installation of Ubuntu. 
 
Should I try and restore the MBR for windows, restore the parition for the data drive (wiping out Ubuntu), and then reinstall?
 
Seems like I'm close in being able to actually boot Windows, but Ubuntu is hosed.
 
Any help would be greatly appreciated.

---

### Post by oldfred on 2009-12-31
I think supergrub is still based on grub legacy(0.97), but you have grub2.

Follow one of these (essentially the same) set of instructions to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You may want to install grub to sdb since ubuntu is on sdb. I like to have the boot loader in the MBR of the same drive as the operating system. You then switch drive order in BIOS to boot the sdb drive first.
This will reinstall from a working system to another drive. You have to select sda, sdb, etc on where to install.
sudo dpkg-reconfigure grub-pc

I would also go back and reinstall windows to the sda drive so in the future if sdb has problems you could switch back and boot windows.

---

### Post by presence1960 on 2009-12-31
> **oldfred said:**
> **_I think supergrub is still based on grub legacy(0.97), but you have grub2_**.

Follow one of these (essentially the same) set of instructions to reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Y[B][U]ou may want to install grub to sdb since ubuntu is on sdb. I like to have the boot loader in the MBR of the same drive as the operating system. You then switch drive order in BIOS to boot the sdb drive first.
This will reinstall from a working system to another drive. You have to select sda, sdb, etc on where to install.
sudo dpkg-reconfigure grub-pc[/U][/B]

I would also go back and reinstall windows to the sda drive so in the future if sdb has problems you could switch back and boot windows.

That is exactly what I would say to do after looking at the script. There seems to be a lot of threads with GRUB2 failing if GRUB2 is placed on a disk other than the one Ubuntu is on.

I think the same about SuperGrub Disk. I can't get the web page it keeps timing out. it must be down. But the last time I looked it did not support GRUB2. I have only ever used it a couple times anyway.

I would reinstall GRUB2 by booting off the Live Cd. Go to desktop and open a terminal and run ```
sudo mount /dev/sdb5 /mnt
```

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

When done reboot without Live CD and go into BIOS and set the sdb disk as first hard disk to boot in the hard disk boot order. Save changes to CMOS & continue booting. Boot into Ubuntu. Open a terminal after desktop loads and run ```
sudo update-grub
```
to make sure the GRUB menu is refreshed.

I would then run in terminal ```
sudo dpkg-reconfigure grub-pc
```
set the sdb disk this way when you get GRUB updates they all go to sdb not sda.

---

### Post by gregin_az on 2010-01-01
OldFred / Presence,
 
Thanks so much for the reply and the assistance.  It's helping.
 
I made the changes suggested by OldFred and can now successfully boot to Windows, which I was not able to do before.   
 
Issue now is I'm not getting any sort of dual boot menu that offers a boot of Ubuntu or Windows.  I'm guessing the latter suggestion of the command to refresh the menu may be in order.
 
I'm a little sketchy on locations for installing Grub, etc.  I followed the advice in the procedure and chose the partition / location where Ubuntu is installed.  I think this is the same suggestion OldFred made.  If I had chosen a different volume, would I then be able to dual boot?
 
Also, I'm running all IDE drives and I THINK that the boot order is more driven by the order of the drive connections pn the ribbon and not the Bios.  Was the latter suggestion to change the bios so the menu would appear giving me a Windows or Ubuntu boot option?  Is that the only way to realize a 'dual boot' scenario?
 
Lastly, I'm reluctant to re-install Windows, as that would mean having to re-install all of my applications, favourites, etc.  If I had a more powerful machine, I would have tried Ubuntu in a Vitural Machine mode, as I'm looking really to get my feet wet more than do a complete transition.
 
Seems the outstanding questions are:
 
1) Refreshing the menu / getting a menu that would allow a dual boot?
 
2) Do I need to change the order of the hard drives to be able to dual boot / boot Ubuntu?
 
Again, many thanks.  Definite progress over what I was doing on my own.

---

### Post by presence1960 on 2010-01-01
If you have a master/slave IDE ribbon and are not able to change the boot order from BIOS then open up your case and switch the ribbon connectors on the harddrives. If you ran those commands GRUB was installed to sdb. That is the disk you need as Primary master on the ribbon or GRUB will never come up when you boot.

---

