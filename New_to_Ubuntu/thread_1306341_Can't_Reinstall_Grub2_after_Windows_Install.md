---
title: "Can't Reinstall Grub2 after Windows Install"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Dave_Dews on 2009-10-30
Hello everybody, firstly thanks for taking the time to help..

After successfully installing 9.10 i installed windows on a different partition. As expected, grub was not there and automatically booted to windows.
So i use LiveCD expecting it to be as simple as the whole:
sudo find /boot/grub/stage1 thing - but i guess its not.

I've tried following instructions in this thread   ([http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275))   under reinstalling grub2 from live CD - here's what happens:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f6f6f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20143   161798616   83  Linux
/dev/sda2   *       20144       23330    25599577+   7  HPFS/NTFS
/dev/sda3           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

sudo mount /dev/sda1 /mnt   seems to work fine, no error messages or anything

I dont think i have a separate boot partition, so miss next step

sudo mount --bind /dev/ /mnt/dev    also goes fine

then on the next command i get this:

ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error

I've looked around to find a way around this for a while before posting here, so any help would be very much appreciated, really stuck on this one.

Thanks in advance..

---

### Post by grafted_scion on 2009-10-30
I just did the same thing not realizing i knew nothing about restoring grub2
The instructions in this link fixed my problem,
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Dave_Dews on 2009-10-31
Aha!

Thanks for the reply, thats the same kind of thing i was following,
but the problem was that I was using a 32bit LiveCD, when my architecture is 64bit.

At least now i know what that error message means..

---

