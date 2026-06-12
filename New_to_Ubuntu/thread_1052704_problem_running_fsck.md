---
title: "problem running fsck"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by dogafin on 2009-01-28
im having intermittent startup problems, sometimes it gets stuck on a black screen, and hitting esc will usually get ubuntu to launch normally but sometimes on the progress bar, it forces a fsck and fails, so i have manually ran an fsck with the live cd and this is what i get. 

my startup is now getting better but it still does this problem from time to time and i just want to know what i need to  do so i can run a fsck.
can someone tell me if im doing something wrong? thanks in advance!


-------------------
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/sda
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$

---

### Post by bogdan.veringioiu on 2009-01-28
Hi.

I think you want to use fsck on a partition, not on the entire disk.
You can identify the partitions like this:

sudo fdisk -l

You should get an output like this:

/dev/sda1   *           1         255     2048256   82  Linux swap / Solaris
/dev/sda2             256        9729    76099905    5  Extended
/dev/sda5            4607        9729    41150466   83  Linux

then you can run sudo fsck /dev/sda5 (for example).

Let me know if it works for you.

Bogdan

---

