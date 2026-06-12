---
title: "HDD Suddenly won't mount !"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by hopelessone on 2010-03-31
Hi,

It shows up in Gparted so i didn't loose the drive...

> fstab: /dev/disk/by-id/ata-WDC_WD20EADS-00S2B0_WD-WCAVY0614129-part1 /mnt/hdd_2           ext4    defaults       0       1

> blade@blade:~$ sudo mount -a
[sudo] password for blade: 
mount: /dev/sdb1 already mounted or /mnt/hdd_2 busy
blade@blade:~$ sudo mount -a
mount: /dev/sdb1 already mounted or /mnt/hdd_2 busy
blade@blade:~$ sudo mkdir /mnt/hdd_4
blade@blade:~$  sudo mount -a
mount: /dev/sdb1 already mounted or /mnt/hdd_4 busy
blade@blade:~$ sudo umount /mnt/hdd_2
umount: /mnt/hdd_2: not mounted
blade@blade:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
blade@blade:~$ sudo mount -a
mount: /dev/sdb1 already mounted or /mnt/hdd_2 busy
blade@blade:~$ 


What can i do? getting worried...

Thanks

---

### Post by undecim on 2010-03-31
What are the outputs of 
```
mount
```

and

```
dmesg | tail -n 20
```

and

```
sudo fdisk -l
```

---

### Post by hopelessone on 2010-03-31
I changed > fstab: /dev/disk/by-id/ata-WDC_WD20EADS-00S2B0_WD-WCAVY0614129-part1 /mnt/hdd_2 ext4 defaults 0 1

to 

> fstab: /dev/disk/by-id/ata-WDC_WD20EADS-00S2B0_WD-WCAVY0614129-part1 /mnt/hdd_2 ext4 defaults 0 0

Working...

So it's gotta be a checking process of some kind?

---

### Post by hopelessone on 2010-03-31
Hi undecim,

> blade@blade:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /home type ext4 (rw)
/dev/sdc1 on /mnt/hdd_3 type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/blade/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=blade)
blade@blade:~$ dmesg | tail -n 20
[   26.171277] i2c-adapter i2c-1: unable to read EDID block.
[   26.171280] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   26.875329] i2c-adapter i2c-1: unable to read EDID block.
[   26.875333] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   26.879911] i2c-adapter i2c-1: unable to read EDID block.
[   26.879914] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.164930] i2c-adapter i2c-1: unable to read EDID block.
[   28.164935] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   28.169376] i2c-adapter i2c-1: unable to read EDID block.
[   28.169378] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   29.960011] eth0: no IPv6 routers present
[   30.054837] i2c-adapter i2c-1: unable to read EDID block.
[   30.054841] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   30.059416] i2c-adapter i2c-1: unable to read EDID block.
[   30.059418] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.274715] i2c-adapter i2c-1: unable to read EDID block.
[   31.274719] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   31.279237] i2c-adapter i2c-1: unable to read EDID block.
[   31.279241] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   93.194751] gvfsd-metadata[2062]: segfault at 8 ip 0000000000405ee6 sp 00007fff7b43e6e0 error 4 in gvfsd-metadata[400000+d000]
blade@blade:~$ sudo fdisk -l
[sudo] password for blade: 

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x151e151e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1958    15727603+  83  Linux
/dev/sda2            9603        9733     1052257+  82  Linux swap / Solaris
/dev/sda3            1959        9602    61400430   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ac957

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073b48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux
blade@blade:~$ 


Thanks..Hope it Helps..

---

### Post by undecim on 2010-03-31
> **hopelessone said:**
> So it's gotta be a checking process of some kind?

I doubt it. That number only determines the order that the disks are checked on reboot. It doesn't do anything once you are logged into your system. The only way that would even make a difference would be if you rebooted. But even before that, a 1 means that the drive has to be checked at the same time as the root filesystem -- before most of the boot process.

Best I can tell is that something was using that directory, and by the time you made that change, was done with it.

---

### Post by hopelessone on 2010-03-31
OK Thanks for the info...

If I add a 0 it loads no probs.... a 1 or a 2 is no go...

Should i wait with the 1?

Thanks

---

### Post by undecim on 2010-03-31
> **hopelessone said:**
> OK Thanks for the info...

If I add a 0 it loads no probs.... a 1 or a 2 is no go...

Should i wait with the 1?

Thanks

Well, like I said, that number should only matter on boot. So unless you are rebooting when you make the changes... A 0 will mean that it won't be check on boot, so if you are rebooting, that makes sense. Otherwise I suspect it's a minor bug.

Out of curiosity, what happens if you try to mount the disk manually with
```
sudo mount /dev/disk/by-id/ata-WDC_WD20EADS-00S2B0_WD-WCAVY0614129-part1 /mnt/hdd_2
``` while a 1 or 2 is there?

---

### Post by hopelessone on 2010-03-31
Sorry I was rebooting every time i changed fstab... I'll check tomorrow time ATM is 11:30pm G'night thanks for helpin...I'll do the mount tomorrow...BTW I did'nt know you can mount that way ...thanks...

---

