---
title: "how to get this to mount at boot"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-25
how do i get my music hdd mount at to boot up
here is the info i was once asked for
darin@darin-desktop:~$ sudo fdisk -l
[sudo] password for darin: 
Sorry, try again.
[sudo] password for darin: 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ae79d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19175   154023156   83  Linux
/dev/sdb2           19176       19457     2265165    5  Extended
/dev/sdb5           19176       19457     2265133+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcaf8909d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdd: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders
Units = cylinders of 15810 * 2048 = 32378880 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1           4       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 12, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdd2               4         927    29206168    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(3, 12, 22)
Partition 2 has different physical/logical endings:
     phys=(911, 254, 62) logical=(926, 180, 59)
darin@darin-desktop:~$ sudo blkid

/dev/sdb1: UUID="ffcf5658-1b5f-412d-9494-96bbeceeb61e" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="62a027e1-7926-46ef-8252-f8d213b5d164" 
/dev/sdc1: UUID="3a4f7394-8461-4d90-abf8-7489fecd4825" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd2: LABEL="DARIN'S IPO" UUID="C468-7380" TYPE="vfat" 
darin@darin-desktop:~$ 
darin@darin-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ffcf5658-1b5f-412d-9494-96bbeceeb61e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=62a027e1-7926-46ef-8252-f8d213b5d164 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


darin@darin-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             145G   24G  115G  17% /
tmpfs                 378M     0  378M   0% /lib/init/rw
varrun                378M  100K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M  2.9M  375M   1% /dev
tmpfs                 378M   12K  378M   1% /dev/shm
lrm                   378M  2.0M  376M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdd2              28G  4.1G   24G  15% /media/DARIN'S IPO
darin@darin-desktop:~$

---

### Post by taurus on 2009-02-25
Which one is your music harddrive because you already have /dev/sdd2 mounted to /media/DARIN'S IPO?

```
/dev/sdd2 28G 4.1G 24G 15% /media/DARIN'S IPO
```

---

### Post by rgb96 on 2009-02-25
Go to system->preferences->sessions and click "add+"

name it whatever and for command put 

```
mount /dev/whicheverdrive
```

put notes if you want. That should work.

---

### Post by DarinB on 2009-02-25
hi taurus you helped me when i installed ibex thank you for that
i had to reinstall because i had problems with my old video card and messed up my install
SOOOO i just reinstalled ibex and it is the 80 gb drive with music the ipod just happened to be mounted when i did commands. i tried to understand what you had me do but it didn't work this time so i think something is different. thanks

---

### Post by taurus on 2009-02-25
80GB harddrive is your /dev/sdc1 then.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=3a4f7394-8461-4d90-abf8-7489fecd4825   /media/music   ext3   defaults   0   2
```
Save it and close down gedit window.  Now, create the new mount point and mount it.

```
sudo mkdir /media/music
sudo mount -a
df -h
```
And if you want to be the owner of /media/music, then you can change the ownership from root to your login name, darin, with the chown command.

```
sudo chown -R darin:darin /media/music
ls -la /media
```

---

### Post by DarinB on 2009-02-25
thanks taurus you're perfect every time now to learn to do it my self. hopefully not with this same old pc that's killing me the geforce 420 with a small power supply so i don't know what i can upgrade the card to.

Now i am not sure why my ipod won't open in gpodder i added the plugins as asked last time it was  easy now not

---

