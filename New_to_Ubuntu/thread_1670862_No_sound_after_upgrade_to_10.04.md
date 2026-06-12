---
title: "No sound after upgrade to 10.04"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Falc7 on 2011-01-19
I've just upgraded from 9.10 to 10.04. And i've lost sound. I have googled searched and found many people having the same problem but none of their solutions work for me.

```
jane@jane-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```#

I have turned alsamixer levels up to the maximum.

Can anyone offer some help?

---

### Post by khelben1979 on 2011-01-21
For starters, [this old thread]("http://ubuntuforums.org/showthread.php?t=545318") is about the problem you have mentioned.

If you download the source from the ALSA Project and compile it, I think you should have sound working again.

The source of your problem is probably because Ubuntu 10.04 uses a different kernel then your previous version of Ubuntu, and the hardware support which is compiled in the kernel differs from different kernels which Ubuntu chooses for their distribution. It's possible that your chipset has not been compiled in the new version of Ubuntu, and compiling up the source code from [the ALSA Project]("http://www.alsa-project.org/main/index.php/Main_Page") will hopefully solve this problem for you.

You find all the source archives in the right top corner of the screen, and there is instructions for how you unpack, configure the script files and then install them to the Ubuntu system.

What I have written in this thread so far isn't exactly newbie friendly I'm sorry to say, but doing things slow, all this is possible even for a newbie, avoid to stress things through and you shall be fine. Continue to ask questions.

---

### Post by Falc7 on 2011-01-22
Hi
I got impatient and installed a new version of ubuntu in a new partition and copied the home folder across
When i deleted the old partition however I must have deleted grub at the same time, I am now trying to reinstall grub from LiveCD but i am having some problems.

Following the section of this guide called 'Reinstalling from LiveCD'
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfec7e353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3475    27912906    7  HPFS/NTFS
/dev/sda2            3476       14594    89307384    5  Extended
/dev/sda5            3476        3888     3317391   82  Linux swap / Solaris
/dev/sda6            3889       14594    85988352   83  Linux

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

```

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6
mount: /dev/sda6 already mounted or /media/7fc77944-c012-4b6e-86c7-ef611c0bf52b busy
mount: according to mtab, /dev/sda6 is already mounted on /media/7fc77944-c012-4b6e-86c7-ef611c0bf52b

```

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda6
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).

```

---

