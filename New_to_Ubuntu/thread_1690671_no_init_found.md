---
title: "no init found"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by danijela86 on 2011-02-18
Hi,
The error was as follows (previosly i didn't install/change anyting exept some text files, so they shouldn't effect anyting like this):
===================================
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
[20298638] usb 8-1.2: new full speed USB device using uhci_hcd and address 4
No init found. Try passing init=bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_
===================================

Steps I tried:
1. Tried the recovery mode from grub. [failed]
2. Tried the lower version. [failed]
3. Tried the lower version's recovery mode. [failed]
4. Booted with live CD and tried to mount all partitions:
The '/' partition, which is /dev/sda1 (where Ubuntu is installed), - I can't able to mount. Rest all partitions are okay (sda2 - ntfs), and so are the data.

So I tried repairing with the following command:
sudo fsck /dev/sda1
Now it complains as follows:
fsck.ext4: device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

So I tried to unmount it with gparted as follows:
gksudo gparted

It says the above partition is already in UNMOUNTED state. Also all  partitions, except sda1, I can able to mount & unmount with out any  problem.

I gave up and tried reinstalling it. But once I click on Install Ubuntu button, it checks if i have internet conection, cable pluged and when I press foward it's not even  going to the next screen. It hangs there itself indefinitely! (and it should show screen with partitions).

I read tuns of forums but i didn't find solution. Please help!

---

### Post by danijela86 on 2011-02-18
Hi,
The error was as follows (previosly i didn't install/change anyting exept some text files, so they shouldn't effect anyting like this):
===================================
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target Filesystem doesn't have /sbin/init.
[20298638] usb 8-1.2: new full speed USB device using uhci_hcd and address 4
No init found. Try passing init=bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_
===================================

Steps I tried:
1. Tried the recovery mode from grub. [failed]
2. Tried the lower version. [failed]
3. Tried the lower version's recovery mode. [failed]
4. Booted with live CD and tried to mount all partitions:
The '/' partition, which is /dev/sda1 (where Ubuntu is installed), - I can't able to mount. Rest all partitions are okay (sda2 - ntfs), and so are the data.

So I tried repairing with the following command:
sudo fsck /dev/sda1
Now it complains as follows:
fsck.ext4: device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

So I tried to unmount it with gparted as follows:
gksudo gparted

It says the above partition is already in UNMOUNTED state. Also all  partitions, except sda1, I can able to mount & unmount with out any  problem.

I gave up and tried reinstalling it. But once I click on Install Ubuntu button, it checks if i have internet conection, cable pluged and when I press foward it's not even  going to the next screen. It hangs there itself indefinitely! (and it should show screen with partitions).

I read tuns of forums but i didn't find solution. Please help!

---

### Post by cariboo on 2011-02-18
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by danijela86 on 2011-02-18
I countined finding solutions and finally i got it:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1682038](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1682038)

:)

i'm sorry i begun new thread but i spent hours before i find this one.

---

