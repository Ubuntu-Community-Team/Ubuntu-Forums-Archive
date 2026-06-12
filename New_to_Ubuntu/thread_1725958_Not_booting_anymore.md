---
title: "Not booting anymore"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by FelixL on 2011-04-10
Hello guys,
I installed Ubuntu 10.10 on October 10th as a dual-boot on one hard drive with Windows 7, mainly for android development. Since nearly one month it fails to boot, and now I've got the time and will to repair it. Something like this appears:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init = bootarg.
```

I have seen more threads here with the same problem, but can't really find how to solve it. Tried a command with sudo, but sudo was not available. Now I'm booting from a live-cd, and tried to use the boot info script from here: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
It starts, but then stops:
```
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
```

I've got no important information on this install, only lots of sourcecode I could download again. If I install Ubuntu again, will it find the partitions where Ubuntu was before and overwrite it? Is my Windows-partition safe? (Already backed up tall important data from there, just don't want to have to install everything again.) Is there any other way to get Ubuntu working again? I think it was a kernel update, but I'm not sure.
Thank's for your information and advise!

---

### Post by TeoBigusGeekus on 2011-04-10
Boot up with a live cd/usb and fsck your partitions:
```
sudo fsck /dev/sda1
```
Replace sda1 to whatever applicable.

---

### Post by Rubi1200 on 2011-04-10
I have an alternative suggestion.

Download and burn to CD a distro called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Use it to boot the computer and then run the boot info script again. One thing you should know, you do not need to preface the command with sudo since Slax uses a root terminal by default.

Good luck!

---

### Post by FelixL on 2011-04-11
```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2
ubuntu@ubuntu:~$ sudo fsck /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

```

By the way, just to get the information for you complete, Grub shows Windows 7, a Windows Vista recovery partition, 2 Ubuntu entries and 2 Ubuntu recoveries. The laptop is a two year old Lenovo 3000 N200, it could also be possible that the hard drive starts to fall apart. Nautilus shows a 201GB filesystem, that is Windows 7, and a 41 GB filesystem it can not mount. That is Ubuntu.

---

### Post by FelixL on 2011-04-11
Okay, just decided to reinstall Ubuntu, but the installer doesn't go further than the check for power, Internet connection and hard drive space. I will try to delete the entire partition, thanks for your help nonetheless!

---

### Post by Rubi1200 on 2011-04-11
Did you try my suggestion to use Slax?

---

