---
title: "hi i partioned my hard drive but it not working right"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by blake7 on 2009-11-17
i gave 9.10 15gb to work with and 140gb for home folder 
but when i down laod anything or put anything in my home folder it put stuff into my 15gb section 

what did i do wrong and how can i sort it out

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> i gave 9.10 15gb to work with and 140gb for home folder 
but when i down laod anything or put anything in my home folder it put stuff into my 15gb section 

what did i do wrong and how can i sort it out

can you post output of the follwoing;
```
sudo fdisk -l
```

```
cat /etc/fstab
```

and 
```
sudo mount
```

---

### Post by blake7 on 2009-11-17
Cheers

---

### Post by blake7 on 2009-11-17
CHEERS


dude@dude:~$ sudo fdisk -l
[sudo] password for dude: 
Sorry, try again.
[sudo] password for dude: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1841    14787801   83  Linux
/dev/sda2           18897       19092     1574370    5  Extended
/dev/sda5           18898       19092     1566337+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 16.8 GB, 16776691712 bytes
4 heads, 16 sectors/track, 511984 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1      511984    16383480    c  W95 FAT32 (LBA)
dude@dude:~$

---

### Post by blake7 on 2009-11-17
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1841    14787801   83  Linux
/dev/sda2           18897       19092     1574370    5  Extended
/dev/sda5           18898       19092     1566337+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 16.8 GB, 16776691712 bytes
4 heads, 16 sectors/track, 511984 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1      511984    16383480    c  W95 FAT32 (LBA)
dude@dude:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=426f8a7c-c161-4ed3-ba98-63ffdbf8fd1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cbe81d19-e941-4532-8690-a11ab0209109 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dude@dude:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=426f8a7c-c161-4ed3-ba98-63ffdbf8fd1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cbe81d19-e941-4532-8690-a11ab0209109 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
dude@dude:~$

---

### Post by blake7 on 2009-11-17
dude@dude:~$ sudo mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dude/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dude)
/dev/mmcblk0p1 on /media/114D-7FF7 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
dude@dude:~$

---

### Post by blake7 on 2009-11-17
thank you i hope that helps

---

### Post by ukripper on 2009-11-17
looks like your home is not mounted. can you post output of below command and use "quotes"/"Codes" from message tools otherwise it is really hard to read the output:
```
blkid
```
```
df -h
```

---

### Post by blake7 on 2009-11-17
thoes last commands comes up with nothing 


sorry

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> thoes last commands comes up with nothing 


sorry

That is not possible. Try with sudo. they are two different commands

---

### Post by blake7 on 2009-11-17
dude@dude:~$ sudo blkid
[sudo] password for dude: 
/dev/sda1: UUID="426f8a7c-c161-4ed3-ba98-63ffdbf8fd1a" TYPE="ext4" 
/dev/sda5: UUID="cbe81d19-e941-4532-8690-a11ab0209109" TYPE="swap" 
/dev/mmcblk0p1: LABEL="" UUID="114D-7FF7" TYPE="vfat" 
dude@dude:~$ ^C
dude@dude:~$ 

cool

---

### Post by blake7 on 2009-11-17
dude@dude:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G   12G  1.7G  88% /
udev                  750M  260K  750M   1% /dev
none                  750M  312K  750M   1% /dev/shm
none                  750M   88K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
none                  750M     0  750M   0% /lib/init/rw
/dev/mmcblk0p1         16G  1.4G   15G   9% /media/114D-7FF7
dude@dude:~$ ^C
dude@dude:~$

---

### Post by ukripper on 2009-11-17
Can't see your home partition in here at all. Can you install gparted:
```
sudo apt-get install gparted
```

in terminal run:
```
gparted
```
and see if your drives are partioned correctly.

---

### Post by blake7 on 2009-11-17
thank you

---

### Post by blake7 on 2009-11-17
done 

note sure what its trying to say to me though
but it does show the two differant partitions



thank you

---

### Post by blake7 on 2009-11-17
one is called dev/mmcblk0p1
and the other 
dev/sda

and a small one called

dev/sda2 which is about 10gb

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> one is called dev/mmcblk0p1
and the other 
dev/sda

and a small one called

dev/sda2 which is about 10gb

can you post screenshot here.

---

### Post by blake7 on 2009-11-17
oh it says 130gb is unallocated



that does not sound right

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> oh it says 130gb is unallocated



that does not sound right

Yeh. You need to format that 130GB with EXT4. I guess that was suppose to be your home drive. 

I think what happened was when you installed ubuntu I guess you left that unformated and home partition wasn't created during installation.

---

### Post by blake7 on 2009-11-17
ok thanky you for that 

but now i got to say how do i do tthat 

sorry
lol

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> ok thanky you for that 

but now i got to say how do i do tthat 

sorry
lol

This may help - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

i guess it is easier for you to try home partition using ext3 file system.

just follow the tutorial above.

---

### Post by blake7 on 2009-11-17
should i try to reloded 9.10 and start again from the begging??? i would like ext4

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> should i try to reloded 9.10 and start again from the begging??? i would like ext4

that would be ideal. Make sure you backup your important data before wiping out your current installtion.

Goodluck

---

### Post by blake7 on 2009-11-17
do you know where i went wrong the frist time????


thatnk youu

---

### Post by blake7 on 2009-11-17
or a better question is 

is thier tutorial even somthing on youtube???

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> do you know where i went wrong the frist time????


thatnk youu

i think you might have not selected Manual way. You need to select "Manual" and then partition accordingly.

this video will give you how to have a separate home partition - [http://www.youtube.com/watch?v=EerMJBqxaH8&feature=related](http://www.youtube.com/watch?v=EerMJBqxaH8&feature=related)

make sure you select ext4 though.

---

### Post by blake7 on 2009-11-17
thank you for your time and patients i hope you have a good eveing


later

and may the force be with you

---

### Post by ukripper on 2009-11-17
> **blake7 said:**
> 

later

and may the force be with you

I'll be back cyborg. lol Have fun

---

### Post by Dougie187 on 2009-11-17
My bet is if you selected manual, you forgot to specify the mount point.

Basically, if you go through the wizard, and select manual partitions. You want to specify three partitions. Something like this

Partition 1 - ~14GB - Mount point = / - Format = EXT4
Partition 2 - ~140GB - Mount Point = /home - Format = EXT4
Partition 3 - ~1-2GB - Format = Linux-Swap

Hope that helps some.

---

### Post by oldfred on 2009-11-17
Did you at some time experiment with RAID? Your partition naming is more like an old raid setup. Karmic is more aggressive at finding old raid setups in a drive and causes problems.

More info here
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

---

