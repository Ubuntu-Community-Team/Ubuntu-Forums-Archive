---
title: "warning 0 mb disk space left"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by chuckycheese on 2010-02-13
I have been getting low disk space warnings. Disk Usage Analyzer reported 4GB used, 4GB free. so attached a 500GB external drive and partitioned about half of it for Linux.  Was on yesterday with permission problems trying to move /home to the new partition to stop the low space warnings. Today after Updates I got "0mb disk space left".  DUA reports 5.3GB used and 461.4GB free.  So I thought I might need to move /user to the new partitions which Ubuntu>Community>Documentation>File System said, I should be able to do.  Before I did I searched the forums to make sure and found a thread about low disk space the referenced df -Th.  I ran this and here are my results:

adminstrator@latitude600:~$ df -Th|grep -v tmpfs
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4    4.7G  4.4G   80M  99% /
none       debugfs    4.7G  4.4G   80M  99% /var/lib/ureadahead/debugfs
/home/adminstrator/.Private
          ecryptfs    4.7G  4.4G   80M  99% /home/adminstrator
/dev/sdb2     ext2    231G  790M  218G   1% /media/_mybook_linux
/dev/sdb1     vfat    232G   58M  232G   1% /media/My Book
adminstrator@latitude600:~$

I know I am dumb, but it looks like debugfs and ecryptfs and ext4 are redundancies.  Would someone please explain this to me, and tell me how to stop the low disk messages?  Thanks

---

### Post by chewearn on 2010-02-13
First thing you could do is clear away the cruft and left overs from the upgrades.

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

Then, you might want to run "Cruft removal/Janitor" to delete older kernels.

---

### Post by chuckycheese on 2010-02-13
adminstrator@latitude600:~$ df -Th|grep -v tmpfs
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext4    4.7G  4.3G  143M  97% /
none       debugfs    4.7G  4.3G  143M  97% /var/lib/ureadahead/debugfs
/home/adminstrator/.Private
          ecryptfs    4.7G  4.3G  143M  97% /home/adminstrator
/dev/sdb2     ext2    231G  790M  218G   1% /media/_mybook_linux
/dev/sdb1     vfat    232G   58M  232G   1% /media/My Book
adminstrator@latitude600:~$

---

### Post by plucky on 2010-02-13
> Filesystem Type Size Used Avail Use% Mounted on
[color=red]/dev/sda5 ext4 4.7G 4.3G 143M 97% /[/color]
none debugfs 4.7G 4.3G 143M 97% /var/lib/ureadahead/debugfs
/home/adminstrator/.Private
ecryptfs 4.7G 4.3G 143M 97% /home/adminstrator
/dev/sdb2 ext2 231G 790M 218G 1% /media/_mybook_linux
/dev/sdb1 vfat 232G 58M 232G 1% /media/My Book


Increase the size of your / partition to at least 10G.

---

### Post by chuckycheese on 2010-02-16
The rest if this HDD is windows, I have been trying to move some of it over to the other half of the new drive.  Is it not possible to move some of ubuntu to the new drive? or should I copy off what I have in the linux partition on the new drive and just do a clean install to it?

---

### Post by chewearn on 2010-02-16
> **chuckycheese said:**
> The rest if this HDD is windows, I have been trying to move some of it over to the other half of the new drive.  Is it not possible to move some of ubuntu to the new drive? or should I copy off what I have in the linux partition on the new drive and just do a clean install to it?

It is possible to move some of ubuntu to another partition, but it's going to be complicated and I would advise against it.

The simpler approach is to resize Ubuntu partition to give it more space.

Another approach is to move the entire Ubuntu partition to the other drive.  This is slightly more difficult than simple resizing, because apart from moving the partition, you need to fix grub to find the new location.

---

### Post by achase79 on 2010-02-16
4.7 gb is tiny for most linux distribution installations.  10gb usually the smallest I would have and still have my /home directory on a different drive/partition.

---

### Post by chuckycheese on 2010-02-16
achase

I thought I had an 8MG partition as, I had installed it previously on a 4GB partion that somehow disappeared when my hal32.dll became corrupted.  How do I safely move my /home directory and is this going  to solve my problems?

---

### Post by chewearn on 2010-02-16
> **chuckycheese said:**
> achase

I thought I had an 8MG partition as, I had installed it previously on a 4GB partion that somehow disappeared when my hal32.dll became corrupted.  How do I safely move my /home directory and is this going  to solve my problems?

It depends what you are going to do.

If you are planning to install a lot of new applications, then no, I don't think moving your /home going to solve the problem.  Because the 4.7GB is going to fill up pretty fast with additional new application.

If however, you already have all the application you need, then even the current situation is fine.

---

For instance, I have an eeepc.  The primary HD is 4GB SSD, which I have barely squeeze Ubuntu plus the few applications I used daily.  At any moment, I have between 50MB to 200MB free space.  If a large update arrived (e.g. a kernel or OpenOffice update), the disk space shrunk to below 100MB.  I cleaned up the archive afterwards, delete old kernels and be back to 200MB.

Of course, I stored my data in a second drive, so my /home partition is quite bare.

---

---

### Post by chuckycheese on 2010-02-17
Is it possible to move my current partition to the big partition and just keep /home on this small partion?
.

adminstrator@latitude600:~$ sudo blkid
[sudo] password for adminstrator: 
/dev/sda1: UUID="8C085B59085B417E" TYPE="ntfs" 
/dev/sda5: UUID="1662cf3d-b81a-4609-98bf-cad89d9e5577" TYPE="ext4" 
/dev/sda6: UUID="f5b78002-83e9-4c00-bd21-7ee67536e045" TYPE="swap" 
/dev/sdb1: LABEL="My Book" UUID="907C-E2E9" TYPE="vfat" 
/dev/sdb2: LABEL="/mybook/linux" UUID="278c5441-2313-4b17-a051-91fd888f7335" TYPE="ext2" 
adminstrator@latitude600:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61330bae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9074    72886873+   7  HPFS/NTFS
/dev/sda2            9075        9729     5261287+   5  Extended
/dev/sda5            9075        9694     4980118+  83  Linux
/dev/sda6            9695        9729      281106   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           30523       60801   243216067+   c  W95 FAT32 (LBA)
/dev/sdb2               1       30522   245167933+  83  Linux

Partition table entries are not in disk order

---

