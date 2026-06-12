---
title: "Problems With Hard Drive Upgrade"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by Hunter Morrell on 2010-06-15
Unfortunately for me, I have a 13 gig hard drive that I just barely am able to use due to the size constraints. Recently, I came into the ownership of a 40 gig hard drive, and planned to swap over to that one. So I installed dd_rescue and set to work. A little while later, and everything was completed. So, I shut down the computer, switched hard drives, and booted it back up. Everything looked fine at first, until it got to the grub menu, or lack of one. After the BIOS boot screen, it displayed a black screen with "no grub". I'm guessing I need to copy the boot sectors over to the hard drive, based on another post I read, but I'm not entirely sure. Any help would be greatly appreciated.

---

### Post by Irony on 2010-06-15
From the live Ubuntu CD. Open a terminal and run the following commands;

Assuming GRUB 2 (replace sda1 with whatever your install is actually in);

```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
grub-install /dev/sda
```

Hopefully that will do it.

---

### Post by Hunter Morrell on 2010-06-15
Ok. I tried the first command and got this in response.

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I went on and tried the "dmesg | tail" and got this.

```
[   24.744050] intel8x0_measure_ac97_clock: measured 52209 usecs (2516 samples)
[   24.744056] intel8x0: clocking to 48000
[   24.803834] type=1505 audit(1276606174.774:10):  operation="profile_load" pid=826 name="/usr/sbin/mysqld"
[   24.832190] type=1505 audit(1276606174.806:11):  operation="profile_load" pid=751 name="/usr/bin/evince-previewer"
[   24.836161] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 2474.375811] cdrom: sr1: mrw address space DMA selected
[ 2474.414260] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2474.479253] ISO 9660 Extensions: RRIP_1991A
[ 2702.872407] EXT3-fs error (device sdb1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 782)!
[ 2702.872719] EXT3-fs: group descriptors corrupted!

```

---

### Post by CharlesA on 2010-06-15
Can I suggest hooking both drives up then using clonezilla to clone them?

---

