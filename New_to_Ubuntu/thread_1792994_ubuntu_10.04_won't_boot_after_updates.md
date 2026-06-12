---
title: "ubuntu 10.04 won't boot after updates"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Lkm on 2011-06-28
Hello people :) not totally new to linux, but I am pretty much a beginner with a little BASh and C knowledge.


Basically I can't boot the current kernel (2.6.32-32-generic) or the previous two versions in normal or failsafe mode since I updated through the update manager a couple days ago.

When I try to boot normally I get stuck at the purple ubuntu screen with the five orange dots,
& in recovery mode I can't login using the prompt (something about a I/O error?) and running in failsafe just gets me stuck at a black screen.
Disk checking also crashes, with and without the live CD, gives an error saying something about an unknown username.

The laptop in question dual boots to windows which is running fine, so I've ruled out a hardware malfunction.

I'm currently running a 'try ubuntu without installing' session using the live CD, from which I can see I haven't changed the permissions on a lot of my files making them uncopyable, so a fix would be preferable here to a complete re-install.


(While I'm here, I've never managed to get my laptop back out of suspend -screen just goes black. Is there some sort of package or driver to fix that for hp laptops? Installed the exact same Ubuntu on a sony laptop and all that worked fine.)


A quick google usually brings me to a forum thread that fixes all my linux problems. As far as I can tell
this non-booting is a pretty common one but I haven't found any solutions so far.
Quite stuck on this one :-k

---

### Post by cariboo on 2011-06-29
When you start in recovery mode, do you get to the menu? IF you do get to the menu, have you tried the dpkg selection, as it sounds like your update didn't complete.

What error message are you get in recovery mode when you try to log in?

---

### Post by Lkm on 2011-06-29
Hello, I get to the recovery menu. Previous dpkg attempts gave me error messages butit looked as though it had fixed something this time. Still refuses to boot. In failsafeX I get a menu and then just a black screen when I try to boot and the hard drive blinks. Trying to resume normal boot, I type in my username and it gives me a set of lines of errors, repeats these errors a couple times then stops. All the lines are numbered and have ata1.00 at the start.
Here are a few of the messages from these lines:
```

failed command: READ DMA
cmd c8/00:08:d8:a4:ad/00:00:00:00:00/e4 tag 0 dma 4096 in
res 51/40:08:d8:a4:ad/00:00:00:00:00/e4 Emask 0x9 (media error)
status: { DRDY ERR }
error: { UNC }
end_request: I/O error, dev sda, sector 78488792

```

---

### Post by Lkm on 2011-06-29
Not sure how useful this is, but I'll post the results from the boot  info script from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,039,125    40,039,063   7 NTFS / exFAT / HPFS
/dev/sda2          40,040,448    91,815,935    51,775,488  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3E1C0F701C0F228F                       ntfs       
/dev/sda2        517696a0-49b4-484d-8db4-7ddc57e6b9c2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 517696a0-49b4-484d-8db4-7ddc57e6b9c2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3E1C0F701C0F228F
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=517696a0-49b4-484d-8db4-7ddc57e6b9c2 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  33.222827911 = 35.672739840   boot/grub/core.img                             1
  29.448261261 = 31.619829760   boot/grub/grub.cfg                             1
  33.490821838 = 35.960496128   boot/initrd.img-2.6.32-30-generic              1
  22.897071838 = 24.585543680   boot/initrd.img-2.6.32-31-generic              1
  34.246910095 = 36.772339712   boot/initrd.img-2.6.32-32-generic              2
  33.494979858 = 35.964960768   boot/vmlinuz-2.6.32-30-generic                 1
  33.580917358 = 36.057235456   boot/vmlinuz-2.6.32-31-generic                 1
  34.243392944 = 36.768563200   boot/vmlinuz-2.6.32-32-generic                 1
  34.246910095 = 36.772339712   initrd.img                                     2
  22.897071838 = 24.585543680   initrd.img.old                                 1
  34.243392944 = 36.768563200   vmlinuz                                        1
  33.580917358 = 36.057235456   vmlinuz.old                                    1


```

---

### Post by amjjawad on 2011-06-30
I guess you need to Re-install GRUB2

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

And by the way, you don't have SWAP Partition.

---

### Post by wildmanne39 on 2011-06-30
Hi, from what I can tell your boot information looks good, and since you get a purple screen then you are past grub loading I suggest two things, 

1. Boot into recovery and run this command
```
sudo apt-get update && sudo apt-get upgrade
```if that does not fix the problem go to this link and follow the instructions because your video driver may have been updated and it is corrupted.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Lkm on 2011-07-01
Hello, the sudo apt-get and aptitude upgrades and updates and dpkg didn't work, and grub seems to be fine (I've had grub mess up before after I installed fedora 14 on a separate partition).

I've now opted to reinstall Lucid from scratch, after changing the owner of and copying my files from both ubuntu and windows to a new ntfs backup partition at the end so I can reorganise the windows and linux sections completely.

I repartitioned my hard drive yesterday, it looks something like this:

[windows 19GB (ntfs)][   ubuntu 33GB (ext4)   ][ unallocated 33GB ][2GB SWAP][backup 15GB (ntfs)]


The problem I run into now while formatting and reinstalling ubuntu on partition 2 is the installation gets stuck at 34% and tells me there is an error with my hard drive.
I'm going to try deleting this section through windows and reformatting to see if that fixes it.


Also, I've read that Knoppix includes system rescue for other linux distros, has anyone used it?

---

### Post by amjjawad on 2011-07-01
> **Lkm said:**
> Hello, the sudo apt-get and aptitude upgrades and updates and dpkg didn't work, and grub seems to be fine (I've had grub mess up before after I installed fedora 14 on a separate partition).

I've now opted to reinstall Lucid from scratch, after changing the owner of and copying my files from both ubuntu and windows to a new ntfs backup partition at the end so I can reorganise the windows and linux sections completely.

I repartitioned my hard drive yesterday, it looks something like this:

[windows 19GB (ntfs)][   ubuntu 33GB (ext4)   ][ unallocated 33GB ][2GB SWAP][backup 15GB (ntfs)]


The problem I run into now while formatting and reinstalling ubuntu on partition 2 is the installation gets stuck at 34% and tells me there is an error with my hard drive.
I'm going to try deleting this section through windows and reformatting to see if that fixes it.


Also, I've read that Knoppix includes system rescue for other linux distros, has anyone used it?

I'm not sure what's the procedure or the steps you have followed but I'll try to list the steps that you need to do. Before I start, you did format your HDD, correct? so you have no valuable data to worry about. Good.

1- Run the Live Session either from Ubuntu LiveCD or LiveUSB - whatever works for you.

2- System > Administration > GParted

3- Remove ALL the partitions that you have.

4- I guess from "Device" - can't remember which menu - try to create New Partition Table

5- After that, apply and reboot. DO NOT create any partition yet.

6- From Windows Disc, allocate a new partition for Windows, format it as NTFS and LEAVE the rest as unallocated space. DO NOT prepare Linux Partitions within Windows.

7- Once Windows installation is done, boot your machine from your LiveCD or LiveUSB.

8- From GParted, create 3 partitions:
root (/)
home (/home)
and swap

9- Start the installation

10- Of course format both root and home and choose ext4 and don't forget the mount point.

11- Boot Loader for Ubuntu must be installed (in your case) to the MBR of sda.

12- Once you're done from installation, reboot, and you're done.


Should you face any problem, please report back :)

---

### Post by Lkm on 2011-07-01
I've now attempted to install from the live disc multiple times. I get this error at 34% every time:

[I]The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error[/I] [I]

This particular error is often due to a faulty CD/DVD disk or drive, or a  faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD  at a lower speed, to clean the CD/DVD drive lens (cleaning kits are  often available from electronics suppliers), to check whether the hard  disk is old and in need of replacement, or to move the system to a  cooler environment.[/I] 


I've tried wiping the cd and installing to different partitions in different places incase there was a bad sector of hard drive. 34% every time.

---

### Post by georgelab on 2011-07-01
> **Lkm said:**
> I've now attempted to install from the live disc multiple times. I get this error at 34% every time:

[I]The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error[/I] [I]

This particular error is often due to a faulty CD/DVD disk or drive, or a  faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD  at a lower speed, to clean the CD/DVD drive lens (cleaning kits are  often available from electronics suppliers), to check whether the hard  disk is old and in need of replacement, or to move the system to a  cooler environment.[/I] 


I've tried wiping the cd and installing to different partitions in different places incase there was a bad sector of hard drive. 34% every time.

It looks like your installation copy must be damaged. Did you try to checksum your ubuntu ISO before burning the disc?

If the ISO is damaged, wiping the cd is useless. Try to checksum the ISO and burn another boot cd...

regards

---

### Post by Lkm on 2011-07-01
I just used the disc checker, and it did indeed find an error.
I received this disc for my bash and C course and have used it to install before, after which it sat in a drawer.

I'm going to use USB from now on.

How does one go about doing this checksum?

---

### Post by wildmanne39 on 2011-07-01
> **Lkm said:**
> I've now attempted to install from the live disc multiple times. I get this error at 34% every time:

[I]The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error[/I] [I]

This particular error is often due to a faulty CD/DVD disk or drive, or a  faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD  at a lower speed, to clean the CD/DVD drive lens (cleaning kits are  often available from electronics suppliers), to check whether the hard  disk is old and in need of replacement, or to move the system to a  cooler environment.[/I] 


I've tried wiping the cd and installing to different partitions in different places incase there was a bad sector of hard drive. 34% every time.
Hi, I just took another look at your first post and it says your hard drive is having I/O errors, looks like your drive is failing. I also looked at your boot script information and it looks good to me.

---

### Post by Lkm on 2011-07-01
> **wildmanne39 said:**
> Hi, I just took another look at your first post and it says your hard drive is having I/O errors, looks like your drive is failing. I also looked at your boot script information and it looks good to me.

Not impossible since it's not the newest laptop. Seems fine though, reinstalled windows earlier and that works.

I'm trying to create a bootable USB. only now I find that my laptop does not support this. (it does support booting from floppy; it doesn't even have one of those!)

---

### Post by Lkm on 2011-07-01
Wait no it does. Found it in the setup menu. Woo!

---

### Post by amjjawad on 2011-07-01
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by wildmanne39 on 2011-07-01
> **Lkm said:**
> Wait no it does. Found it in the setup menu. Woo!
Hi, let us know how it goes and if you get your problem fixed,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Lkm on 2011-07-02
Got into the setup utility just before boot and changed the boot order of the devices (hard drive was originally above USB). Booting from USB was unbelievably fast -never making another CD!
Yup, seems to be working now.


Though just one last thing: is there a way to restore my previous settings for my applications? There are hidden dot folders in my home folder which I backed up, are/were the settings in there?

---

