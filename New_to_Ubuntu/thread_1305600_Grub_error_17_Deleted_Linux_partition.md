---
title: "Grub error 17: Deleted Linux partition"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by PVO300C on 2009-10-30
Sorry if the answer was posted elsewhere, but I couldn't find a solution on my own.

I previously had 9.04 Jaunty installed after Windows XP (Dual boot, using GRUB).
I downloaded the 9.10 i386 desktop iso and burned it to a cd to install later.
Backed up all of my personal files.

Then, instead of going into Windows XP to defragment the disk, I did the noob error of booting the 9.10 Live cd and deleting my Linux partition from the Live cd desktop.

So now I can't boot to XP to defrag the XP partition before installing 9.10 in the previous 9.04 partition, which is what I want to do.



Here is the RESULTS.txt output from the boot info script:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8b6a8b6a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    53,143,019    53,142,957   c W95 FAT32 (LBA)
/dev/sda2          53,143,020   156,296,384   103,153,365   f W95 Ext d (LBA)
/dev/sda5          53,143,083   104,727,734    51,584,652   b W95 FAT32
/dev/sda6         104,727,798   120,792,734    16,064,937   b W95 FAT32
/dev/sda7         120,792,798   154,722,014    33,929,217  83 Linux
/dev/sda8         154,722,078   156,296,384     1,574,307  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6C1D-F4F7" TYPE="vfat" 
/dev/sda5: UUID="2A03-1806" TYPE="vfat" 
/dev/sda6: UUID="3603-1806" TYPE="vfat" 
/dev/sda8: UUID="941b5fb9-62b8-4494-9ddc-569e6f07c13f" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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
/dev/sda6 on /media/3603-1806 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5 on /media/2A03-1806 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda1 on /media/6C1D-F4F7 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn 

================================ sda1/BOOT.INI: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn 
```Can anyone help me get my system back? :)

---

### Post by egalvan on 2009-10-30
Here's something I copied off another post a while back.

> Re-Install GRUB, if file locations are UN-KNOWN
long story

1. Boot your computer up with Live CD
2. Open a terminal window (or switch to a tty ).
3. Type 'sudo grub'.
   This starts GRUB.
   You should get text, of which last line is "grub>"
4. Type "find /boot/grub/stage1".
   You'll get a response like "(hd0,1)".
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)" ( what you got in step #4 hard disk + boot partition )
6. Type
       "setup (hd0)"     <--- to install GRUB to MBR, PREFERED method
OR     "setup (hd0,1)"   <--- (whatever your hard disk + partition # is)
                              to install GRUB to a  partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by PVO300C on 2009-10-30
> **egalvan said:**
> Here's something I copied off another post a while back.

Thanks, that was quick!

This is what I got from the terminal:

```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
ubuntu@ubuntu:~$ 

```

What am I to do? Can I/should I install grub manually?

P.S.: I'll be back at around 15:30 UTC, going to bed now.
Thanks!

---

### Post by Creet on 2009-10-30
I had the exact same problem, although in my attempts to fix it it changed to an error 2.  Apparently one thing that causes these errors is grub and the motherboard having differing opinions on the location of hard drives.  

What eventually worked for me was changing the boot order of my hard drives.  

If that doesn't work this link gives updated instructions on how to reinstall grub:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

Goodluck!

---

### Post by PVO300C on 2009-10-30
Because grub doesn't show as installed, it must have been located on my sda7 Linux partition, right?

Since I do not want to reinstall Linux on sda7 BEFORE having defragmented my NTFS partitions, I need to be able to boot to Windows XP to defragment.

The only thing I want to is boot to Windows XP to defragment.
How do I go about doing this?

---

### Post by PVO300C on 2009-10-30
> **PVO300C said:**
> Because grub doesn't show as installed, it must have been located on my sda7 Linux partition, right?

Since I do not want to reinstall Linux on sda7 BEFORE having defragmented my NTFS partitions, I need to be able to boot to Windows XP to defragment.

The only thing I want to is boot to Windows XP to defragment.
How do I go about doing this?

Sorry, not NTFS, but FAT32.

---

### Post by bumanie on 2009-10-30
It seems you don't want ubuntu at this point, seeing you deleted the partition with it on. To get xp to boot again so that it can be defragged, you will have to boot the xp installation disk and go to repair and then into console mode. Once in console mode, type FIXBOOT --> enter the type FIXMBR --> enter - answer y to any questions. You should then be able to reboot and end up in xp as the hard drive's mbr will be over-written and grub should be completely removed.

---

### Post by PVO300C on 2009-10-30
> **bumanie said:**
> It seems you don't want ubuntu at this point, seeing you deleted the partition with it on. To get xp to boot again so that it can be defragged, you will have to boot the xp installation disk and go to repair and then into console mode. Once in console mode, type FIXBOOT --> enter the type FIXMBR --> enter - answer y to any questions. You should then be able to reboot and end up in xp as the hard drive's mbr will be over-written and grub should be completely removed.

Sounds reasonable... is there any way to do this without the XP installation disk? (I don't have it with me right now.


Actually, I just found this link: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Which basically talks about using the Ubuntu Live cd and installing ms-sys to fix the MBR.
Would this work in my case?

---

### Post by oldfred on 2009-10-30
If that does not work supergrub can fix XP. Also if you have an old win98 floppy it will also boot your XP. Boot was pretty much the same through XP then it was changed by Microsoft for Vista and Win7.

---

### Post by PVO300C on 2009-10-30
> **oldfred said:**
> If that does not work supergrub can fix XP. Also if you have an old win98 floppy it will also boot your XP. Boot was pretty much the same through XP then it was changed by Microsoft for Vista and Win7.

Thanks, I'll try a few things and post back.

---

### Post by PVO300C on 2009-10-31
Update:

Super Grub Disk looks like it has some nice features, but I couldn't burn it onto a cd (Only one drive running my Ubuntu Live cd), nor could I find a floppy disk and I somehow couldn't boot with a usb key.

I then tried ms-sys. Using apt-get install ms-sys didn't work, so I'm guessing that it's not in Karmic's repos (I had them all checked).
So I just downloaded it via Sourceforge and installed it on the Live cd desktop... and bam, it re-wrote the hard drive's MBR and I was able to boot to XP to defrag!



After a few hours of fiddling with the Karmic installation cd and personalizing my system's settings, I'm finally running full force with Karmic!

Oh, how nice it is to finally have a working microphone and wi-fi under Ubuntu! :D
Thanks to everyone for your help!

---

