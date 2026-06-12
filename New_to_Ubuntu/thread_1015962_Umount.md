---
title: "Umount"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-19
Hello

Trying to umount a drive and keeps telling me "...is mounted mutiple times". I tried via the command line and using Nautilis.

Thanks

---

### Post by taurus on 2008-12-19
Can you post the output of this command from a terminal?

```
df -h
```
Which partition/drive do you plan to unmount?

---

### Post by Frank_F on 2008-12-19
here you go..thanks

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G  2.9G   66G   5% /
tmpfs                 236M     0  236M   0% /lib/init/rw
varrun                236M  116K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
udev                  236M  2.8M  233M   2% /dev
tmpfs                 236M  684K  235M   1% /dev/shm
lrm                   236M  2.0M  234M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             5.8G  140M  5.4G   3% /media/disk
/dev/sdb5              13G  161M   12G   2% /media/disk-1
/dev/sdb5              13G  161M   12G   2% /home/frank/more
/dev/sdb1              13G  161M   12G   2% /home/frank/more
/dev/sdb5              13G  161M   12G   2% /home/frank/more
/dev/sdb1              13G  161M   12G   2% /home/frank/more
/dev/sdb5              13G  161M   12G   2% /home/frank/more

---

### Post by taurus on 2008-12-19
Hmm...  How come you are mounting both /dev/sdb1 & /dev/sdb5 to the same mount point, /home/frank/more?  Do you mount those two partitions from /etc/fstab?

```
sudo fdisk -l
cat /etc/fstab
```
Now, which partition, /dev/sdb1 or /dev/sdb5, do you want to unmount?

```
sudo umount /dev/sdb5
```

---

### Post by Frank_F on 2008-12-19
I was attempting to had all 20 gigs to the home/frank/more directory...but on second thought...I would simply like both sdb1 and sdb5 to be mounted on my root, so that the 20g disk space is added to my existing 73 gigs...hope this makes sense


frank@frank-desktop:~$ sudo fdisk -l
[sudo] password for frank: 

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fa9eb4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9558    76774603+  83  Linux
/dev/sda2            9559        9733     1405687+   5  Extended
/dev/sda5            9559        9733     1405656   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18b418b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         765     6144831   83  Linux
/dev/sdb2             766        2434    13406242+   f  W95 Ext'd (LBA)
/dev/sdb5             766        2434    13406211   83  Linux




cat fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7b627eaa-89f8-4abc-b61c-e59eb635c807 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8029a32c-d016-45af-a623-f8b60e568b35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5	/home/frank/more ext3 defaults 0 0
/dev/sdb1	/home/frank/more ext3 defaults 0 0

---

### Post by taurus on 2008-12-19
Is there anything on /dev/sdb1 & /dev/sdb5?  Why not just make it one partition, /dev/sdb1, that takes up the whole space, 20GB.  Then, you don't have to worry about two separate partitions on the same harddrive.

---

### Post by Michael.Godawski on 2008-12-19
Wouldn't be easier to create a second mount point like

```
mkdir /home/frank/evenmore 
```and then mount the partition you want there
```

sudo mount -t ext3 /dev/sdb5 /home/frank/evenmore 
```I guess you cannot mount to partitions to one mount point at the same time simultaneously.

edit: or do like taurus suggests, and merge the two partitions into one.

---

### Post by Frank_F on 2008-12-19
thanks guys....both points are valid....if I wanted to mount the /dev/sdb1 to another mount point how do I do it...since it is telling me I cant umount either partition cause they are mounted multiple times

---

### Post by Michael.Godawski on 2008-12-19
Make a new mountpoint
```
sudo mkdir /media/datapartition1

```mount the parition
```
sudo mount -t ext3 /dev/sdb1 /media/datapartition1
```

---

### Post by taurus on 2008-12-19
> **Frank_F said:**
> thanks guys....both points are valid....if I wanted to mount the /dev/sdb1 to another mount point how do I do it...since it is telling me I cant umount either partition cause they are mounted multiple times

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and remove the last two entries for /dev/sdb1 & /dev/sdb5.  Then, reboot.

Now use gparted, System -> Administration (install it if you don't have it), and delete all partitions on /dev/sdb.  Then, create a new primary partition, /dev/sdb1, and format it to ext3.  Once it's done, edit /etc/fstab again and add an entry at the end of it for the new /dev/sdb1.  If you mount it somewhere new, don't forget to create a new mount point or it won't be mounted.

---

### Post by Frank_F on 2008-12-19
thanks so much taurus...worked like a charm

---

