---
title: "oem installation"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by zerobinary on 2010-08-29
I have bought an alienware m11x (i5 version) equipped with window 7 Ultimate. I have successfully dual booting my ubuntu 10.04 and window 7, but the problem is every time I boot into window 7 it automatically destroy my bootloader! Making it impossible to boot into either operational system!
Is there a way to fix it permanently ?
> [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)
I have try this before!

---

### Post by jtarin on 2010-08-29
Install [EasyBCD]("http://neosmart.net/dl.php?id=1") to your Win7 and the Windows boot loader will chainload Ubuntu, if you [reinstall Grub]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId232162") to the root of the Linux partition and not the MBR.

---

### Post by zerobinary on 2010-08-29
> if you reinstall Grub to the root of the Linux partition and not the MBR.
Need some help on it
My output code
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -i
fdisk: invalid option -- 'i'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f0b6359

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       41349   316734375    7  HPFS/NTFS
/dev/sda4           41349       60802   156250113    5  Extended
/dev/sda5           41349       60304   152251392   83  Linux
/dev/sda6           60304       60802     3997696   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dcca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1949    15648768    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sd1/mnt
mount: can't find /dev/sd1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount--blind /proc/mnt/proc
sudo: mount--blind: command not found
ubuntu@ubuntu:~$ sudo mount --blind /proc/mnt/proc
mount: unrecognized option '--blind'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount --blind/proc/mnt/proc
mount: unrecognized option '--blind/proc/mnt/proc'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
grub-pc set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 249 not upgraded.
root@ubuntu:/# grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
ls: cannot access /media/5C86-15B3: No such file or directory
Found Windows 7 (loader) on /dev/sda2
done
root@ubuntu:/# sudo mount /dev/sda6 /mnt/
/dev/sda6 looks like swapspace - not mounted
mount: you must specify the filesystem type
root@ubuntu:/# ls /mnt/home/*/Desktop/sda_before.img
ls: cannot access /mnt/home/*/Desktop/sda_before.img: No such file or directory
root@ubuntu:/# ls /mnt/home/ubuntu/Desktop/sda_before.img
ls: cannot access /mnt/home/ubuntu/Desktop/sda_before.img: No such file or directory
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
root@ubuntu:/# ls /mnt/home/ubuntu/*/sda_before.img
ls: cannot access /mnt/home/ubuntu/*/sda_before.img: No such file or directory
root@ubuntu:/# ls /mnt/home/ubuntu/*/Desktop/sda_before.img
ls: cannot access /mnt/home/ubuntu/*/Desktop/sda_before.img: No such file or directory
root@ubuntu:/# sudo mount /dev/sda5 /mnt/
root@ubuntu:/# ls /mnt/home/ubuntu/*/Desktop/sda_before.img
ls: cannot access /mnt/home/ubuntu/*/Desktop/sda_before.img: No such file or directory
root@ubuntu:/# ls /mnt/home/*/Desktop/sda_before.img
/mnt/home/diva/Desktop/sda_before.img
root@ubuntu:/# sudo dd if=/dev/sda of=/mnt/home/diva/Desktop/sda_after.img count=63
63+0 records in
63+0 records out
32256 bytes (32 kB) copied, 0.00096861 s, 33.3 MB/s
root@ubuntu:/# 
```

---

### Post by jtarin on 2010-08-29
**_/dev/sda5 41349 60304 152251392 83 Linux_**....is where Grub should be installed and not /dev/sda if your installing according to my recommendations....you overwrite your MBR when you install at /dev/sda.
[Reinstall GRUB]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")....scroll to method 3 chroot...install to /dev/sda5

---

### Post by balaknair on 2010-08-29
This might be applicable to you
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)

> If you find that running Windows makes a GRUB 2-based system unbootable (Debian bug, Ubuntu bug), then I'd like to hear from you. This is a bug in which some proprietary Windows-based software overwrites particular sectors in the gap between the master boot record and the first partition, sometimes called the "embedding area".

> If you suffer from this problem, then please do the following:

    * Save the output of fdisk -lu to a file. In this output, take note of the start sector of the first partition (usually 63, but might also be 2048 on recent installations, or occasionally something else). If this is something other than 63, then replace 63 in the following items with your number.
    * Save the contents of the embedding area to a file (replace /dev/sda with your disk device if it's something else): dd if=/dev/sda of=sda.1 count=63
    * Do whatever you do to make GRUB unbootable (presumably starting Windows), then boot into a recovery environment. Before you reinstall GRUB, save the new contents of the embedding area to a different file: dd if=/dev/sda of=sda.2 count=63
    * Follow up to either the Debian or the Ubuntu bug with these three files (the output of fdisk -lu, and the embedding area before and after making GRUB unbootable.

I hope that this will help me to assemble enough information to fix this bug at least for most people, and of course if you provide this information then I can make sure to fix your particular version of this problem. Thanks in advance!
Maybe you should contact the author of the linked page.

---

### Post by mkvnmtr on 2010-08-29
I believe until this is fixed lilo will boot both without problems.

---

### Post by jtarin on 2010-08-29
> **mkvnmtr said:**
> I believe until this is fixed lilo will boot both without problems.Lilo or Grub....just install to the /root of the partition that Linux is on. Then Use The Win 7 loader to chainload either by editing the BCD of Win. That's what EasyBCD does modifies the loader and points to Linux.

---

### Post by zerobinary on 2010-08-30
How do u use easy bcd?

---

### Post by jtarin on 2010-08-30
> **zerobinary said:**
> How do u use easy bcd?You download the executable and install in your Win7 or Vista OS.
Once installed run with admin rights.[This will get you started.]("http://neosmart.net/forums/showthread.php?t=3153") If you have any questions after reading or doubts as to what to do ask on the Neosmart Forum or in this thread.
[Latest stable version]("http://neosmart.net/dl.php?id=1").
Essentially EasyBCD is a frontend for Win BCEdit. It makes it easier for you to edit. [More info here]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home"). [Linux BCD info here.]("http://neosmart.net/wiki/display/EBCD/Linux")

---

### Post by zerobinary on 2010-08-30
easy bsd problem
Now I have no problem booting into ubuntu but i can't boot into window 7

---

### Post by jtarin on 2010-08-30
You shouldn't have used neoGrub....In BCD you should have chosen the Linux tab and selected Grub2 from the dropdown menu. What you have done is installed Grub again to the MBR. Can you do the repair? Do you have the install disk for Windows? Remember I said....> If you have any questions after reading or doubts as to what to do ask on the Neosmart Forum or in this thread.

[Scroll down for an illustrated guide]("http://neosmart.net/forums/showthread.php?t=6350").

---

### Post by zerobinary on 2010-08-30
Give up on Ubuntu! I guess oem and linux does not mix!

---

### Post by cariboo on 2010-08-30
The problem is a utility that Dell installs that overwrites a part of grub in the mbr. If you want you can check out the bug #[lpbug]441941[/lpbug] report to see if some one has come up with a work around. I have to warn you though that the report is faily long.

---

