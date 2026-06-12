---
title: "Lost the boot option between Ubuntu and Windows"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by Nagz on 2011-04-06
Guys,

Firstly I am a novice and I apologize if this topic has been discussed, if so any links to the topic would be appreciated. 
Here is my question:- I had Ubuntu 10.10 and Windows installed side by side, and I used to get an option to boot into Win or Ubuntu at the start. Recently I had to reinstal my Windows and ever since then I lost the Boot option. Can you tell me how do I get that back?

Thanks in advance.

-Nag.

---

### Post by TeoBigusGeekus on 2011-04-06
Windows deleted grub, Ubuntu's bootloader.
[Here's]("http://ubuntulinuxhowtos.blogspot.com/2010/01/how-to-reinstall-grub-2-after.html") a guide on how to reinstall it.

---

### Post by Rex Bouwense on 2011-04-06
I have a couple of references that may be of help to you.  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)  and [https://help.ubuntu.com/10.04/switching/C/dualboot.html](https://help.ubuntu.com/10.04/switching/C/dualboot.html)
It has been a while since I tried to dual boot with windows but I do remember that unless Windows is installed first and Ubuntu second there are problems with the boot loader.  Is your exact problem now is that only Windows will boot and you have no choice?

TeoBigusGeekus has the site I was looking for.  That should do the trick.

---

### Post by Nagz on 2011-04-06
@Rex:- Yes you are right, when I boot, the systems starts Windows directly, it does not give me an option.

@[TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094"):- I will try the option you suggested. Thanks. Will update how it goes.

---

### Post by garvinrick4 on 2011-04-06
Reinstall grub2 as shown in one of the links unless you had a WUBI install then if
you reinstalled Windows Ubuntu WUBI was a folder in Windows C: drive and it is now been deleted.
This link has a simple Ubuntu grub2 install, needs install cd choosing Try Ubuntu called a Live CD and follow:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

#When you run sudo fdisk -l as per link and you do not see a linux partition you could have installed windows to 
take up full drive in that case reinstall ubuntu. (Post output of sudo fdisk -l if any questions.)
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Nagz on 2011-04-06
Guys looks like its not working for me, here is the output, pardon if I have missed something too trivial.
================================================================================

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314        6536    41943040    7  HPFS/NTFS
/dev/sda4            6536       19458   103794689    f  W95 Ext'd (LBA)
/dev/sda5           19003       19458     3654656   82  Linux swap / Solaris
/dev/sda6            8967       12615    29296640    b  W95 FAT32
/dev/sda7           12615       19002    51309568    b  W95 FAT32
/dev/sda8            6536        8967    19530752   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-27-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sd8
/usr/sbin/grub-probe: error: cannot stat `/dev/sd8'.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-27-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-27-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda8
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/# grub-install --recheck /dev/sda8
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
root@ubuntu:/#

---

### Post by oldfred on 2011-04-06
Note the second line has no 8.

sudo mount /dev/sda8 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda


You are installing grub's boot loader to the MBR of drive sda where drives are sda, sdb, sdc etc.

You install is in sda8 or the eighth partition on drive sda. So we mount sda8 so grub can find the rest of the system including grub's files, kernel etc. and then install the boot loader.

---

