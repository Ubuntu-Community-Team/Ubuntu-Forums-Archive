---
title: "Lost Harddrive space on new install."
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Midnight Rider on 2010-02-28
Hi Linux newbie!

I recently installed Ubuntu 9.10 onto a Revo 160GB HDD.  

All went well and I instlled XBMC and squeezebox server.

I've downloaded maybe 5 blu ray rips average 6GB each and according to the system I now have about 16GB free space left.

How can this be? surely the OS does'nt use that much space.

I installed the partitions using the default settings.

Any suggestions?

---

### Post by Elfy on 2010-02-28
Can you open a terminal - Apps > Accessories and run this command then paste the output here for us please

```
df -h
```

---

### Post by Midnight Rider on 2010-02-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              71G   51G   17G  76% /
udev                  375M  260K  375M   1% /dev
none                  375M  1.3M  374M   1% /dev/shm
none                  375M  320K  375M   1% /var/run
none                  375M     0  375M   0% /var/lock
none                  375M     0  375M   0% /lib/init/rw

---

### Post by Elfy on 2010-02-28
You didn't use the whole drive it looks like - the first line is the install 

/dev/sda5 71G 51G 17G 76% /

The install partition is 71Gb.

Do you have any other partitions on the drive?

```
sudo fdisk -l
```

---

### Post by Midnight Rider on 2010-02-28
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Elfy on 2010-02-28
If in doubt copy and paste commands - the l is a L not a 1.

---

### Post by Midnight Rider on 2010-02-28
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dab4dab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         262     2104483+   c  W95 FAT32 (LBA)
/dev/sda2             263         524     2104515   83  Linux
/dev/sda3             525        9883    75176167+  1c  Hidden W95 FAT32 (LBA)
/dev/sda4            9884       19457    76903155    5  Extended
/dev/sda5            9884       19177    74654023+  83  Linux
/dev/sda6           19178       19457     2249068+  82  Linux swap / Solaris

---

### Post by Elfy on 2010-02-28
You have a 71Gb (more or less) drive fat32 at sda3

---

### Post by Midnight Rider on 2010-02-28
Ok, thanks.

How can I access this space as the file browser is now saying I only have 16GB storage left or is it a case of having to reinstall?

---

### Post by Elfy on 2010-02-28
There are a few things you can do - you don't need to reinstall.

You can add the partition as it is.

You can delete and then add the space to the install 

Depends on whether there is anything on there you wish to keep.

---

### Post by Midnight Rider on 2010-02-28
Ok, thanks thats a relief I wasn't looking forward to resinstalling.

Any tips/guide for how to add the partition for general storage use.

There's nothing on that partition.

Thanks for you help by the way.

---

### Post by Elfy on 2010-02-28
If you want to use it as a linux filesystem -

```
sudo apt-get install gparted
```

Then run partition editor from the System Admin menu - right click on the partition and delete it, apply and then after that has finished create a new partition - ext4 is default now.

Then you need to add a folder for it to mount into. If you want to see it on the desktop - change 'name'  to anything you want

```
sudo mkdir /media/name
```

To not see it on the desktop

```
sudo mkdir /mnt/name
```

Then edit your fstab file

```
sudo cp /etc/fstab /etc/fstab.2802
gksudo gedit /etc/fstab
```

Add this line - make sure to have the same folder in this line as you make above - ie - /media/name or /mnt/name

```
/dev/sda3 /media/name ext4 defaults 0 2
```

Or - leave the partition as it is and add this line to fstab, you still need to do the mkdir step

```
/dev/sda3 /media/name vfat defaults,user,dmask=027,fmask=137 0 0
```

---

### Post by Midnight Rider on 2010-02-28
Thanks

---

### Post by spectralblue on 2010-02-28
EDIT: It seems someone already posted an answer

---

