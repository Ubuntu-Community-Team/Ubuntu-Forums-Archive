---
title: "Ubuntu 9.10 Backtrack4 Dual Boot problems"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by bricktop41 on 2010-01-28
I just installed backtrack4 final on my laptop I have Kubuntu 9.10 on  /dev/sda2 and backtrack 4 on /dev/sda1 
I have attached my grub file for help I really don't know where to edit is the way it is now it gives me grub error 15 when I attempt to boot any thing but backtrack4 



## ## End Default Options ##

splashimage=f34d7b46-3f5f-4443-aec1-ca46876c9a7c/boot/grub/splash.xpm.gz

title        Ubuntu 8.10, kernel 2.6.30.9
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=f34d7b46-3f5f-4443-aec1-ca46876c9a7c ro vga=0x317 
initrd        /boot/initrd.img-2.6.30.9
quiet

title        Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/vmlinuz-2.6.30.9 root=UUID=f34d7b46-3f5f-4443-aec1-ca46876c9a7c ro  single
initrd        /boot/initrd.img-2.6.30.9

title        Ubuntu 8.10, memtest86+
uuid        f34d7b46-3f5f-4443-aec1-ca46876c9a7c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda2)
root            (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro single 
initrd        /boot/initrd.img-2.6.31-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-14-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=44f1de2c-fa26-4cc1-ac87-9477eb388a20 ro single 
initrd        /boot/initrd.img-2.6.31-14-generic
savedefault
boot

---

### Post by reaper308 on 2010-01-29
This is How I solved this issue:
1.I install ubuntu first using the entire disk and rebooted to make sure it was good
2.I then put in my backtrack4 cd and rebooted, I ran the install.sh file
3.when it gets to partitioning resize your ubuntu partition to the desired size by draging on the partition bar and install
4. after installation when you reboot and try to select the ubuntu partion in grub you probally get error 15 just ignore and boot into backtrack
5. Insert your ubuntu live cd and reboot
6. once you get into the live desktop open a terminal and execute the following commands
7.  sudo blkid      "this will show you your partition makeup of your hard drive, if you installed in this order ubuntu should be sda1"
8.  sudo mount /dev/sda1 /mnt
9.  sudo grub-install --root-directory=/mnt /dev/sda --recheck
10. you should get no errors reboot and remove cd, system should skip the grub menu and boot straight into ubuntu
11.open terminal and type
12. sudo update-grub
13.reboot and remove cd
14. you should be all good now to boot into either distro's

---

