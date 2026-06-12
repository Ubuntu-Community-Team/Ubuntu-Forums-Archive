---
title: "Ubuntu won't boot"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by robond8 on 2011-02-19
I have a Dell desktop with Pentium 4, pretty old. All the newest Ubuntu 10.10 updates on it, worked great until today.

I booted the computer and the Grub list appeared, I selected the top Ubuntu (btw, ubuntu is all i have on this machine and i have never seen the grub menu come up on this until today, usually it just starts loading ubuntu and bypasses the grub menu). so then I get some code saying something about dev root didn't mount. i can get the exact code if i need it to be helped.

i looked inside the machine and everything is hooked up right.


what is going on? please help! thanks!

---

### Post by deconstrained on 2011-02-19
This is an easily-recognizable problem albeit one that seldom occurs; sometimes dpkg messes up when it tries to build you a new kernel image.

The solution to a system that has grub properly installed but that won't boot is usually booting to a live disk, double-checking your /etc/fstab and other aspects of your system configuration (just to be on the safe side), and rebuilding your initramfs from the livedisk. It's slightly more difficult than reinstalling but far less time-consuming.

Example: your root filesystem is ext4, and on /dev/sda2, and your boot filesystem is ext2, on /dev/sda1. Fire up gnome-terminal, and:
```
$ sudo -i
# fsck.ext4 /dev/sda2
# mount -t ext4 /dev/sda2 /mnt
# e2fsck /dev/sda1
# mount -t ext2 /dev/sda1 /mnt/boot
# mount -t proc none /mnt/proc
# mount -t sysfs none /mnt/sys
# mount -o bind /dev /mnt/dev 
# mount -t devtps none /mnt/dev/pts
# cp /etc/resolv.conf /mnt/etc/resolv.conf
# chroot /mnt /bin/bash
(chroot) # source /etc/profile
```
Then check your system's configuration. Is everything what it should be in /etc - i.e. correct devices/mount points in fstab? BTW you can use UUID's instead of device kernel names by looking in /dev/disk/by-uuid with 'ls -l'. This will be more reliable, since if you have more than one hard drive the names /dev/sda /dev/sdb (et cetera) will not always refer to the same physical devices. 
```
(chroot) # apt-get update; apt-get dist-upgrade -y
(chroot) # mkinitramfs -v -k all -c
```
Watch the output for any error messages. If the build succeeded, then exit the chroot, umount all the filesystems you mounted, cross your fingers and reboot.

MAKE SURE, HOWEVER, that the livedisk you boot from is the same architecture as the system you want to rescue, or you won't be able to chroot.

---

