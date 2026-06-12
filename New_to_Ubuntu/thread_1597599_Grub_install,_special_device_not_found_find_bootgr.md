---
title: "Grub install, special device not found find /boot/grub/stage1 doesn't work"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Minotaurus113 on 2010-10-15
The title pretty much says it all. But here are more details. I booted to a live cd to use gparted to get all of my partitions in order. I have a 100MB boot sector, followed by 128gb for win7 (ntfs), then 64gb for ubuntu (ext2). After installing win7, I rebooted straight to Win7. So I booted to the live cd again, installed linux and overwrote the win boot partition with the linux boot partition. Now each I reboot straight to ubuntu.

So, I need to install grub. Grub2 is installed by default (verified by grub-install -v returning "GNU GRUB 1.98-lubuntu7). So I did an fdisk -l to determine that my linux install is on /dev/sda3. I did a 'sudo mkdir /media/sda3' & 'mount /dev/sda3 /media/sda3' and I keep getting a special device does not exist error.

I also tried installing legacy grub, but when I enter grub and do a find /boot/grub/stage1 it says that does not exist. It won't even find /boot.

I really want to get this distro up and running, what should I try at this point?

BTW, I am trying to run 64-bit Ubuntu 10.04 on a homemade box with dual WD Caviar 1tb sata drives in raid0, AMD Phenom II X4, on a gigabyte mobo

Thanks!

Edit: also tried acpi = off and noacpi when loading the live cd. AND... I don't think it matters, but ubuntu doesn't like my graphics card so I also have to use an xforcevesa when booting to the live cd.

---

### Post by Minotaurus113 on 2010-10-15
Okay... so I rebooted again and hit f6 and grub loaded. So I booted into ubuntu and tried to use gparted to format extra space to ntfs. I had installed two copies of ubuntu, one on either side of windows. But the extra space still says it contains an ubuntu install. What gives?

---

