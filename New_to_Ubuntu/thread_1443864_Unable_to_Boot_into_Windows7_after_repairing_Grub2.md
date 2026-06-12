---
title: "Unable to Boot into Windows7 after repairing Grub2"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by scrypt on 2010-03-31
Hey all

I have had to repair grub2 on my laptop and after doing so I NO longer have the option to boot into windows7. The option to choose win7 from my grub2 menu has completely disappeared.

I am still learning to use Ubuntu so I would appreciate some help with this.

I have a laptop with win7 and ubuntu 9.10 (Karmic) and I had to reintall win7.
This removed Grub2 from my system so i could no longer boot into ubuntu.
I then repaired grub2 using the karmic liv-cd and these commands ::

sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub

this repaired grub2 but for some reason removed the option to choose to boot into win7 on my grub2 bootlaoder.

here is sudo fdisk -l output :

laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       31081   249553920    7  HPFS/NTFS
/dev/sda3           31082       38913    62910540    5  Extended
/dev/sda5           31082       38588    60299946   83  Linux

Can anyone help me to fix this ?

---

### Post by Mark Phelps on 2010-03-31
If you can boot into Ubuntu, try the following command from there "sudo update-grub" -- and watch the terminal to ensure that GRUB detects your Win7 installation.

---

### Post by scrypt on 2010-03-31
Thank-you Mark Phelps. (Your not Olympian Mark Phelps. Are you ??) 

I will give your suggestion command a try and post back shortly

---

### Post by scrypt on 2010-03-31
I managed to find A fix to my Grub2 issue using these commands :

laptop:~$ sudo mount /dev/sda1 /mnt
[sudo] password for mark:
laptop:~$ sudo mv /mnt/boot /mnt/old-boot
laptop:~$ sudo umount /mnt
laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

This completely fixed my problem.

Big thanks to sisco311 for the above commands.

No more assistance is needed with this thread

Scrypt

---

