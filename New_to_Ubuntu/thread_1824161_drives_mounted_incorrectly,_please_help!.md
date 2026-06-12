---
title: "drives mounted incorrectly, please help!"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Error403 on 2011-08-13
Hi, 
Something happened to my drives and I cant find what. I'll explain my setup first:

Ubuntu is installed on a 160gb primary drive, and I have a 250gb and a 2TB drives there as well. The 2tb (/mnt/wd2tb) drive is for all my personal stuff such as my familys pictures, my mp3s and all my movies. So, my entire life is on there.  The 250gb (/mnt/wd250gb) was supposed to be a /home drive but my last attempt failed miserably and I think that's what giving me problems today.

When I start the machine, it says that /mnt/wd250gb cannot be mounted so I didn't really cared for it because I was not using it so I just pressed S to skip for now, planning to fix that later. But when I access my 2tb drive, ls gives this:

```
phil@galactica:/mnt/wd2tb$ ls
config-2.6.20-1.2948.fc6           initrd-2.6.20-1.2948.fc6debug.img      symvers-2.6.20-1.2948.fc6debug.gz      System.map-2.6.20-1.2948.fc6debug      vmlinuz-2.6.20-1.2948.fc6
config-2.6.20-1.2948.fc6debug      initrd-2.6.20-1.2948.fc6.img           symvers-2.6.20-1.2948.fc6.gz           System.map-2.6.20-1.2948.fc6kdump      vmlinuz-2.6.20-1.2948.fc6debug
config-2.6.20-1.2948.fc6kdump      initrd-2.6.20-1.2948.fc6kdump.img      symvers-2.6.20-1.2948.fc6kdump.gz      System.map-2.6.20-1.2948.fc6PAE        vmlinuz-2.6.20-1.2948.fc6PAE
config-2.6.20-1.2948.fc6PAE        initrd-2.6.20-1.2948.fc6PAE-debug.img  symvers-2.6.20-1.2948.fc6PAE-debug.gz  System.map-2.6.20-1.2948.fc6PAE-debug  vmlinuz-2.6.20-1.2948.fc6PAE-debug
config-2.6.20-1.2948.fc6PAE-debug  initrd-2.6.20-1.2948.fc6PAE.img        symvers-2.6.20-1.2948.fc6PAE.gz        System.map-2.6.20-1.2952.fc6           vmlinuz-2.6.20-1.2952.fc6
config-2.6.20-1.2952.fc6           initrd-2.6.20-1.2952.fc6debug.img      symvers-2.6.20-1.2952.fc6debug.gz      System.map-2.6.20-1.2952.fc6debug      vmlinuz-2.6.20-1.2952.fc6debug
config-2.6.20-1.2952.fc6debug      initrd-2.6.20-1.2952.fc6.img           symvers-2.6.20-1.2952.fc6.gz           System.map-2.6.20-1.2952.fc6kdump      vmlinuz-2.6.20-1.2952.fc6PAE
config-2.6.20-1.2952.fc6kdump      initrd-2.6.20-1.2952.fc6kdump.img      symvers-2.6.20-1.2952.fc6kdump.gz      System.map-2.6.20-1.2952.fc6PAE        vmlinuz-2.6.20-1.2952.fc6PAE-debug
config-2.6.20-1.2952.fc6PAE        initrd-2.6.20-1.2952.fc6PAE-debug.img  symvers-2.6.20-1.2952.fc6PAE-debug.gz  System.map-2.6.20-1.2952.fc6PAE-debug
config-2.6.20-1.2952.fc6PAE-debug  initrd-2.6.20-1.2952.fc6PAE.img        symvers-2.6.20-1.2952.fc6PAE.gz        vmlinux-2.6.20-1.2948.fc6kdump
grub                               lost+found                             System.map-2.6.20-1.2948.fc6           vmlinux-2.6.20-1.2952.fc6kdump

```

er, wheres my stuff? I had a /mnt/wd2tb/pub folder in there, and all this stuff seems like machine gibberish! However, df says nothing seeml lost:
```
phil@galactica:/mnt/wd2tb$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             142G  3.5G  131G   3% /
none                  999M  252K  999M   1% /dev
none                 1006M  168K 1006M   1% /dev/shm
none                 1006M  420K 1005M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/sdc1              99M   64M   31M  68% /mnt/wd2tb
/dev/sda1             1.8T [COLOR="Red"] 790G[/COLOR]  951G  46% /media/WD2TB
/dev/sdc2             230G   14G  205G   7% /media/WD250GB

```

My drive /mnt/wd250gb is now empty for some reason. I remember I had old stuff on it, but thats not a big thing for now.

Here's my fstab:
```
phil@galactica:/mnt/wd2tb$ more /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=21b911ba-54a1-4033-be42-d14f4725606b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=11361c13-2ad2-4e12-b455-e6b602add5de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb2  /mnt/wd250gb  ext3  defaults  0  0
/dev/sdc1  /mnt/wd2tb  ext3  defaults  0  0

```

And on another thread I read somthing to do to try sudo mount -a and there should be no errors, but heres the output:

```
phil@galactica:/mnt/wd2tb$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

So I try what it tells me to do and it gives me this:

```
phil@galactica:/mnt/wd2tb$ sudo dmesg | tail
[21400.576965] EXT3-fs (sdc2): warning: mounting unchecked fs, running e2fsck is recommended
[21400.577502] EXT3-fs (sdc2): using internal journal
[21400.577510] EXT3-fs (sdc2): mounted filesystem with ordered data mode
[22442.164656] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[66592.393376] attempt to access beyond end of device
[66592.393383] sdb2: rw=0, want=4, limit=2
[66592.393391] EXT3-fs (sdb2): error: unable to read superblock
[67482.501782] attempt to access beyond end of device
[67482.501789] sdb2: rw=0, want=4, limit=2
[67482.501797] EXT3-fs (sdb2): error: unable to read superblock

```

Also, I would like to point that power losses are frequent in my area nowadays, is it possible they damaged my drives?


-----------
Ok I found after posting that my stuff was in /media/wd2tb/ . but still, how do I fix those errors ?

---

### Post by Toz on 2011-08-13
According to the information, you have 3 drives a 5 partitions.

**/dev/sdb** - 142GB - your current root drive (sdb1) with a swap partition
**/dev/sdc** - 230GB - with two partitions (sdc1 & sdc2) - this looks like you had fedora installed on this hard drive at one time with sdc1 being the /boot partition and sdc2 the root partition. This is why you are seeing "machine gibberish" - they look like fedora kernel files.
**/dev/sda** - 1.8TB - on one partition (sda1)

The reason that you are getting the error message on boot is that your /etc/fstab file is specifying:> /dev/[COLOR="Red"]sdb2[/COLOR]  /mnt/wd250gb  ext3  defaults  0  0
when it should say **/dev/[COLOR="Red"]sdc2[/COLOR]**. You also don't have an entry for /dev/sda1 which is why it is mounting in the /media directory.

The error messages in your dmesg file are because of the reasons above.

---

### Post by coffeecat on 2011-08-13
It could be that your BIOS detects the three hard drives in a different order at different times, and the sda/sdb/sdc device descriptors get shuffled around. This is not uncommon. Edit your /etc/fstab so that the last three lines use UUIDs rather than device nodes and things will probably be OK.

---

