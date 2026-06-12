---
title: "Installed ubuntu 8.04 after 10.04 install and lost access to 10.04"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by sagi456 on 2010-10-10
Hi,
First of all I'm sorry if someone already made a similar post (which I doubt it) but I couldn't find anything relevant to my case. If there is a previous post please refer me to it.

To make a long story short: I had a problem with 3D acceleration in ubuntu 10.04 since the ATI legacy drivers (for my radeon x1300) don't support 10.04. So I've decided to install ubuntu 8.04 in ADDITION to 10.04 in order to have full 3D support with the fglrx drivers (which seems to work by the way).

As the title says: after installing 8.04 on the same drive as 10.04 but into a different partition I've completely lost access to 10.04 since 8.04 can't access ext4 and the 10.04 kernels are gone from the GRUB menu!!

After a couple of hourse searching the internet and the forums, finding nothing which might help I turn to you guys! If anyone can help me I'll be VERY grateful!

---

### Post by jtarin on 2010-10-10
Can you boot with the 10.04 Live CD? [Go here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") and use "Method #3 CHROOT" and reinstall Grub2. If you are installing Grub2 to any partition besides the first partition MBR you must pay attention to steps #9 and #10. If you are installing Grub2 to any non-standard location post back and I will give you amended instructions for those two steps. After you get running again you can possibly change your filesystem to ext4 without too much difficulty.

---

### Post by sagi456 on 2010-10-10
First, thanks for the super quick reply!!

I've already installed grub2 (I think..) using the synaptic package manager. and I can access the grub2 menu on boot but it gives me the same options as grub legacy (only the 8.04 kernels appear).

anything else I can do?

---

### Post by anewguy on 2010-10-10
You'll need to be running 10.04 - hence the LiveCD thing.  From there you'll need to run install-grub and update-grub to your drive.  After that, you should have grub2 installed to the drive, and it should have entries for all of the OS's it found on the drive.

dave

---

### Post by sagi456 on 2010-10-10
I've been following the instructions on installing grub2. 

On #8 after executing **update-grub[FONT=Verdana] [/FONT]**the terminal reports to find only windows and ubuntu 8.04:

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda6

the rest of the process looks like that:

root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/boot
ubuntu@ubuntu:~$ sudo umount /mnt/usr
umount: /mnt/usr: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ 

Now I'm going to do a reset and see what I'll get

---

### Post by sagi456 on 2010-10-10
OK,

Writing from ubuntu 8.04, As I've suspected, grub didn't detect the 10.04 installation with the update-grub command...

What am I doing wrong?

I'm calling it a night and go to sleep (4.25 AM here) - can't think straight anymore, tomorrow I'll keep on trying to solve this..

p.s
thanks for all the help and all the patient guys! you are really amazing

---

### Post by jtarin on 2010-10-11
You must mount your 10.04 partition as chroot....not 8.04. determine your 10.04 partition and mount it. Use fdisk -l from a terminal to determine the correct mount point for 10.04

---

### Post by sagi456 on 2010-10-11
First, thanks a lot for all the help!

I think that it's going to work now.

From my terminal:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e0a0000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9734    47466497    5  Extended
/dev/sda5            3825        8445    37109760   83  Linux
/dev/sda6            8445        9734    10355712   83  Linux

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16d621b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev  /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts  /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys  /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda6
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# sudo grub-install --recheck /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
root@ubuntu:/# exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts
ubuntu@ubuntu:~$ sudo umount /mnt/dev
ubuntu@ubuntu:~$ sudo umount /mnt/proc
ubuntu@ubuntu:~$ sudo umount /mnt/sys
ubuntu@ubuntu:~$ sudo umount /mnt/usr
umount: /mnt/usr: not mounted
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo reboot

I'll post my results again after rebooting.

---

### Post by sagi456 on 2010-10-11
YES, it worked!!

I've got my lucid lynx back!

thanks a lot guys for all the help, couldn't do it without you!

---

### Post by jtarin on 2010-10-11
Your welcome. Mark thread as solved and remember how your disk are setup. It will come in handy.

---

