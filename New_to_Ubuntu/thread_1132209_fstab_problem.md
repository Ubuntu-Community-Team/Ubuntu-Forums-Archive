---
title: "fstab problem"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-21
Hello!

I can´t work out what to put when I follow these instructions:

> sudo nano /etc/fstab

and add a new entry like:

/dev/mapper/sdX_crypt  /media/sdX     ext3    defaults        0       2


(This will help me automatically unlock my encrypted partition on bootup.)

The two encrypted partitions are:

> /
and
> /home

/ is on sda5 
/home is on sda6

They have different passphrases. Both are ext4.

I have been trying to follow the tutorial [here]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile").

---

### Post by supersonicdarky on 2009-04-21
If they have different keys, then you specify them in the **/etc/crypttab** file.
Then add
```
/dev/mapper/sd5_crypt / ext4 defaults,errors=remount-ro 0 2
/dev/mapper/sd6_crypt /home ext4 defaults 0 2
```

Don't know if it will work this way though, don't have any experience with ecryption. All info is based on the tutorial.

---

### Post by llamabr on 2009-04-21
> **yeehi said:**
> Hello!

I can´t work out what to put when I follow these instructions:



(This will help me automatically unlock my encrypted partition on bootup.)

The two encrypted partitions are:


and


/ is on sda5 
/home is on sda6

They have different passphrases. Both are ext4.

I have been trying to follow the tutorial [here]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile").

Maybe if you give us the output of 
cat /etc/fstab
fdisk -l
df

we can work this out.

---

### Post by yeehi on 2009-04-22
> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda5_crypt /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f1e45c0b-cdd7-4be6-9856-8768e7ff732b /boot           ext4    relatime        0       2
/dev/mapper/sda6_crypt /home           ext4    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cswap	none	swap	sw	0	0
/dev/mapper/sda5_crypt  /dev/sda6      ext4    defaults        0       2


> fdisk -l
yeehi@Ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/sda5_crypt
                      19227248   5626716  12623836  31% /
tmpfs                  1016948         0   1016948   0% /lib/init/rw
varrun                 1016948       216   1016732   1% /var/run
varlock                1016948         0   1016948   0% /var/lock
udev                   1016948       196   1016752   1% /dev
tmpfs                  1016948        92   1016856   1% /dev/shm
lrm                    1016948      2760   1014188   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1               964500     31868    883636   4% /boot
/dev/mapper/sda6_crypt
                      54806168  27828212  24193948  54% /home
/home/yeehi/.Private   54806168  27828212  24193948  54% /home/neil
/dev/sr0                677898    677898         0 100% /media/cdrom0


And thank you for the encouragement! :)

---

### Post by yeehi on 2009-04-25
bump

---

