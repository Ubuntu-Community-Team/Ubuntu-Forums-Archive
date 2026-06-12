---
title: "startup problem"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Souptik on 2011-01-31
Hello.I am using 10.04 Lucid Lynx. I am having a problem with most of the linux kernel images(2.6.32-24 to 2.6.32-28 ) when booting into ubuntu. Most of the kernels installed via the update manager, when selected at grub throw up a screen telling " unable to mount /home.  Press s to skip mounting or M for manual recovery" . I have attached a screenshot of the startup screen. Funnily when I press S (as I am a beginner !!! :lolflag:) everything seems fine except that the Avira Antivir stops working. Anyone knows how to fix this troublesome issue????

---

### Post by ajgreeny on 2011-01-31
Do you have home on a separate partition?

Let's see the output of ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
``` from terminal, from live CD if necessary, which may help.  I am very surprised that this happens with some kernels but not all, as there is no real logic to that

---

### Post by Souptik on 2011-02-02
@ajgreeny,The output is::

souptik@souptik-laptop:~$ sudo fdisk -l
[sudo] password for souptik: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ef97ef9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       30400   182747377    f  W95 Ext'd (LBA)
/dev/sda5            7650       13339    45701681    7  HPFS/NTFS
/dev/sda6           15299       22310    56323858+   7  HPFS/NTFS
/dev/sda7           22311       30400    64982893+   7  HPFS/NTFS
/dev/sda8           13339       15210    15030272   83  Linux
/dev/sda9           15211       15298      706560   82  Linux swap / Solaris

Partition table entries are not in disk order
souptik@souptik-laptop:~$ sudo blkid
/dev/sda1: UUID="66BC1B96BC1B603B" TYPE="ntfs" 
/dev/sda5: UUID="4088A26888A25BE2" TYPE="ntfs" 
/dev/sda6: UUID="6E84A99984A963F5" TYPE="ntfs" 
/dev/sda7: UUID="8E94B20F94B1FA33" TYPE="ntfs" 
/dev/sda8: UUID="49709c62-d6e0-472d-93f4-4a193d83871a" TYPE="ext4" 
/dev/sda9: UUID="341e657a-1ea6-4eb6-9285-80c1b4b01b85" TYPE="swap" 
souptik@souptik-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=49709c62-d6e0-472d-93f4-4a193d83871a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=341e657a-1ea6-4eb6-9285-80c1b4b01b85 none            swap    sw              0       0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/home    /home    dazukofs
# ... DazukoFS

---

### Post by Souptik on 2011-02-04
Just an update...... I am sure the problem is with that Dazukofs thing. I just run the offending kernels in recovery mode and it is displaying problems with mounting Dazukofs.... "mountall: unknown filesystem type: dazukofs."

---

