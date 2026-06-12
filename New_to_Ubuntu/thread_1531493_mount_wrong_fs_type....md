---
title: "mount: wrong fs type..."
date: 2010-07-15
forum: New to Ubuntu
---

### Post by Seilethin on 2010-07-15
so I'm trying to mount /dev/sdb, but I get an error... 
"mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
I'm not really sure what to do about this. I've only used terminal for simple things. I want to mount this drive to /media/lfs, and I've edited my fstab file to accommodate such a mount. Let me know if you need to know anything in particular. Thanks in advance.

I should probably mention that I'm running 8.04 lts.

---

### Post by viralmeme on 2010-07-15
> **Seilethin said:**
> so I'm trying to mount /dev/sdb, but I get an error... "mount: wrong fs type ..

Run gparted and see what it reports as the partition type ..

[IMG]http://gparted.sourceforge.net/screens/gparted_1_small.png[/IMG]

---

### Post by Drenriza on 2010-07-15
what is /dev/sdb?

#Usb key
#Internal hdd
#external hdd (usb / sata)?

something else?

do you know what filesystem in on /dev/sdb ?

try connecting the device to your computer. After doing so open a terminal and type
```
dmesg
```

What happens if you use the command
```
sudo mount /dev/sdb1 /media/lfs
```

copy and paste the output here.

---

### Post by Seilethin on 2010-07-15
Viralmeme: /dev/sdb is a 36.13gb internal hdd formatted with linux-swap.

drenriza:  linuxswap 
"james@hastings-desktop:~$ sudo mount /dev/sdb1 /media/lfs
[sudo] password for james: 
/dev/sdb1 looks like swapspace - not mounted
mount: you must specify the filesystem type
james@hastings-desktop:~$ 
"

---

### Post by Seilethin on 2010-07-15
I'm assuming that it wont mount since it's swapspace? Should I reformat it to ext3?

---

### Post by Drenriza on 2010-07-15
try do
```
cat /etc/fstab
```
and paste the output here

---

### Post by Seilethin on 2010-07-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=751b50d2-593e-48b0-b9c5-cf840c64a6be /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a4f8ae7f-4980-45ea-a9ae-86ec45cbc575 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd2       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb    /media/lfs    ext3    auto        0    0

---

### Post by Drenriza on 2010-07-15
you have already mounted the drive
> /dev/sdb /media/lfs ext3 auto 0 0

dunno if you reformatted it. But for the record, swap drives / partitions does not need to be mounted.

my own /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
```

---

### Post by Seilethin on 2010-07-15
I have reformatted it. (before starting this thread) I cannot access the disk at all, so I'm still kinda confused.

---

### Post by aeiah on 2010-07-15
you'll never be able to mount /dev/sdb - that's a device. the partitions inside are what you should mount.

what info does this give you: ```
ls /dev/sd*
```

---

### Post by Seilethin on 2010-07-15
/dev/sda   /dev/sda5  /dev/sdb1  /dev/sdc
/dev/sda1  /dev/sdb   /dev/sdb2  /dev/sdc1

---

### Post by Drenriza on 2010-07-15
good stuff
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

and

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by aeiah on 2010-07-15
> **Seilethin said:**
> /dev/sda   /dev/sda5  /dev/sdb1  /dev/sdc
/dev/sda1  /dev/sdb   /dev/sdb2  /dev/sdc1

you should be aiming to mount the partitions sdb1 and/or sdb2. i assume one of those is what you're after. sdb is the device, and sdb1 and sdb2 are partitions within the device.

---

### Post by mcduck on 2010-07-15
> **aeiah said:**
> you should be aiming to mount the partitions sdb1 and/or sdb2. i assume one of those is what you're after. sdb is the device, and sdb1 and sdb2 are partitions within the device.

This is correct. You can't mount a drive (/dev/sdb), only the partitions within that drive (/dev/sdb1, /dev/sdb2 and so on).

---

