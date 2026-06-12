---
title: "/ and /home mounted on same device"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by tweeks on 2009-10-16
for some reason, i am unable to figure out how to get /home mounted correctly.  after installing karmaic, i found that / was given most of my 320gb hard drive.  i am not very adept at /etc/fstab (or much else for that matter) but i have some how gotten both / and /home mounted on /dev/sda1 and cant figure out how to get everything straight.  any help would be greatly appreciated.  below are output of /etc/fstap, df -h, blkid, fdisk -l

cat /tc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
#UUID=6942b75d-3747-4fcc-b8f5-ef3b657ed04c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=94343791-92f9-42d3-8ad3-9546c40c90f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb0	/media/media2   udf, iso9660 user,noauto,exec,utf8 0		0
/dev/sda1	/home		ext4	defaults  0	1
timweeks@timweeks-downstairs:/home$ 


sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000848ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38562   309749233+  83  Linux
/dev/sda2           38563       38913     2819407+   5  Extended
/dev/sda5           38563       38913     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00410041

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+  85  Linux extended
/dev/sdb5               1        9728    78140097   83  Linux


sudo blkid

/dev/sda1: UUID="6942b75d-3747-4fcc-b8f5-ef3b657ed04c" TYPE="ext4" 
/dev/sda5: UUID="c24c285c-5e31-4a2c-b841-56f91189c10f" TYPE="swap" 
/dev/sdb5: LABEL="media2" UUID="db6001b8-550e-446b-b616-e526b65d8322" TYPE="ext3" 

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G  2.9G  274G   2% /
udev                  470M  236K  470M   1% /dev
none                  470M  336K  470M   1% /dev/shm
none                  470M  316K  470M   1% /var/run
none                  470M     0  470M   0% /var/lock
none                  470M     0  470M   0% /lib/init/rw
df: `/home/timweeks/.gvfs': No such file or directory
/dev/sda1             291G  2.9G  274G   2% /home
/dev/sdb5              74G  180M   70G   1% /media/media2

thanks,
tim

---

### Post by sandyd on 2009-10-16
> **tweeks said:**
> for some reason, i am unable to figure out how to get /home mounted correctly.  after installing karmaic, i found that / was given most of my 320gb hard drive.  i am not very adept at /etc/fstab (or much else for that matter) but i have some how gotten both / and /home mounted on /dev/sda1 and cant figure out how to get everything straight.  any help would be greatly appreciated.  below are output of /etc/fstap, df -h, blkid, fdisk -l

cat /tc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
#UUID=6942b75d-3747-4fcc-b8f5-ef3b657ed04c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=94343791-92f9-42d3-8ad3-9546c40c90f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb0    /media/media2   udf, iso9660 user,noauto,exec,utf8 0        0
/dev/sda1    /home        ext4    defaults  0    1
timweeks@timweeks-downstairs:/home$ 


sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000848ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38562   309749233+  83  Linux
/dev/sda2           38563       38913     2819407+   5  Extended
/dev/sda5           38563       38913     2819376   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00410041

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+  85  Linux extended
/dev/sdb5               1        9728    78140097   83  Linux


sudo blkid

/dev/sda1: UUID="6942b75d-3747-4fcc-b8f5-ef3b657ed04c" TYPE="ext4" 
/dev/sda5: UUID="c24c285c-5e31-4a2c-b841-56f91189c10f" TYPE="swap" 
/dev/sdb5: LABEL="media2" UUID="db6001b8-550e-446b-b616-e526b65d8322" TYPE="ext3" 

df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             291G  2.9G  274G   2% /
udev                  470M  236K  470M   1% /dev
none                  470M  336K  470M   1% /dev/shm
none                  470M  316K  470M   1% /var/run
none                  470M     0  470M   0% /var/lock
none                  470M     0  470M   0% /lib/init/rw
df: `/home/timweeks/.gvfs': No such file or directory
/dev/sda1             291G  2.9G  274G   2% /home
/dev/sdb5              74G  180M   70G   1% /media/media2

thanks,
tim
i **think** your supposed to select that when your INSTALLING karmic (in the partitioning section, under custom partitioning). not after. becasue the password files are not contained within the home directory

---

### Post by Rocket2DMn on 2009-10-16
You are trying to mount the same partition in two places, which can't be done (actually it can, but not like this).  It's easier to setup a /home partition at boot, though you don't actually need one.  The biggest advantage would be that you can reinstall the system without losing your preferences.  If you still want to create a separate /home partition, have a look at this guide, it is one of the most popular around - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

