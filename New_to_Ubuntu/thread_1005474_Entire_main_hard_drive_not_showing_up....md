---
title: "Entire main hard drive not showing up..."
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-08
I have Mythbuntu installed on one partition of a 500GIG HDD, but when I go to file system>properties, It says its only using 12GIGs or something to that affect. However, I need to back up files from an external drive and cant find where the rest of my hard drive space is...

---

### Post by lovelyvik293 on 2008-12-08
Please post the output of 
```

sudo fdisk -l
df -h

```

---

### Post by ukulele_ninja on 2008-12-08
ryan@ryan-desktop:~$ sudo fdisk -l
[sudo] password for ryan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094765

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460       60801   476664615    5  Extended
/dev/sda5            1460        1583      995998+  82  Linux swap / Solaris
/dev/sda6            1584       60801   475668553+  83  Linux
d
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd49c832

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27dae78d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS
ryan@ryan-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  4.7G  5.9G  45% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  360K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             454G  8.0G  446G   2% /var/lib
overflow              1.0M   16K 1008K   2% /tmp
/dev/sdb1              75G   14G   61G  19% /media/80GIG
/dev/sdc1             466G  352G  115G  76% /media/500GIG
ryan@ryan-desktop:~$

---

### Post by ukulele_ninja on 2008-12-08
The second 500GIG and the 80GIG are external. I need to get my files off my external 500GIG so I can reformat it to something linux plays a little nicer with.

---

### Post by lovelyvik293 on 2008-12-08
Use commands 
```
sudo mount /dev/sda6
```
Because your remaining 454 GB is /dev/sda6

---

### Post by ukulele_ninja on 2008-12-08
ryan@ryan-desktop:~$ sudo mount /dev/sda6
mount: /dev/sda6 already mounted or /var/lib busy
mount: according to mtab, /dev/sda6 is already mounted on /var/lib
ryan@ryan-desktop:~$ 

Apparently its already mounted? I thought it would show up as its own drive or something maybe not.

---

### Post by dwasifar on 2008-12-08
It looks like most of your missing space is in an extended partition at /dev/sda6.

You can either mount that partition somewhere in your filesystem to use the partition as it is, or you can resize your partitions to add it to /dev/sda1, your mounted boot partition.

---

### Post by lovelyvik293 on 2008-12-08
yes this is mounted at /var/lib
then just go to the /var/lib
```
sudo cd /var/lib
```
But how it happened(mounted at /var/lib)?

or just unmount the /dev/sda6 from /var/lib
```
sudo umount /dev/sda6
```
And then mount at anywhere you want.

Also please post the /etc/fstab file.

---

### Post by ukulele_ninja on 2008-12-08
Thanks guys!

---

### Post by lovelyvik293 on 2008-12-08
No problem man but always search google first.

---

### Post by dwasifar on 2008-12-08
/dev/sda5 and /dev/sda6 are inside /dev/sda2.  I know this sounds a little confusing.  /dev/sda2 is an extended partition, which is subdivided into /dev/sda5 (your swap partition) and /dev/sda6 (a large data partition).

In your situation, if I wanted to reclaim the space for the primary partition, I would do it one of two ways:

1) Boot from live CD and start partition editor
2) Delete /dev/sda6
3) Resize /dev/sda2 to eliminate the empty space left by step 2
4) Move /dev/sda2 to the end of the disk
5) Resize /dev/sda1 to take up the empty space between the end of /dev/sda1 and the beginning of /dev/sda2

Or:

1) Boot from live CD and start partition editor
2) Note the size of /dev/sda5
3) Delete all partitions except /dev/sda1
4) Resize /dev/sda1 to take up almost all the disk, except for a space at the end of about the size you noted in step 2
5) Create a partition /dev/sda2 in the remaining space, of type Extended
6) Create a partition /dev/sda5 inside /dev/sda2, of type Swap

The first way is fewer steps, but the second way will be faster.

---

### Post by ukulele_ninja on 2008-12-08
I'm not worried about HOW its partitioned, just as long as I can get to that space. I didn't realize that you could mount a partition to a particular directory, I was expecting my data partition to show up as a third media drive. The data I'm putting on it is only temporary so I can reformat my external as a different file system.

---

### Post by dwasifar on 2008-12-08
> **ukulele_ninja said:**
> I didn't realize that you could mount a partition to a particular directory...

Actually that's pretty much the way you HAVE to do it.  :)

Linux is the reverse of Windows in this regard.  In Windows, a filesystem is on a drive; in Linux, a drive is on a filesystem.  The point is to allow a unified filesystem that doesn't need to be broken up by drive letters as Windows does.

Took me a while to get used to it too.  :)

---

### Post by ukulele_ninja on 2008-12-09
> **dwasifar said:**
> Actually that's pretty much the way you HAVE to do it.  :)

Linux is the reverse of Windows in this regard.  In Windows, a filesystem is on a drive; in Linux, a drive is on a filesystem.  The point is to allow a unified filesystem that doesn't need to be broken up by drive letters as Windows does.

Took me a while to get used to it too.  :)

lol, looks like a got a crash course in it today!

---

### Post by ukulele_ninja on 2008-12-09
> **lovelyvik293 said:**
> yes this is mounted at /var/lib
then just go to the /var/lib
```
sudo cd /var/lib
```
But how it happened(mounted at /var/lib)?

or just unmount the /dev/sda6 from /var/lib
```
sudo umount /dev/sda6
```
And then mount at anywhere you want.

Also please post the /etc/fstab file.

so if I wanted to mount the external drive to the same directory as my system directory, I would use the command 

sudo mount /dev/sda6 (/directory here)

---

### Post by ukulele_ninja on 2008-12-09
> **lovelyvik293 said:**
> yes this is mounted at /var/lib
then just go to the /var/lib
```
sudo cd /var/lib
```
But how it happened(mounted at /var/lib)?

or just unmount the /dev/sda6 from /var/lib
```
sudo umount /dev/sda6
```
And then mount at anywhere you want.

Also please post the /etc/fstab file.

so if I wanted to mount the external drive to the same directory as my system directory, I would use the command 

sudo mount /dev/sda6 (/directory here)   

How about if I want to split part of sda6 into a seperate partition and add it my system partition? can that be done from the command prompt or would I need to use partition magic? Also, would it damage any files in those folders?

---

### Post by dwasifar on 2008-12-14
> **ukulele_ninja said:**
> How about if I want to split part of sda6 into a seperate partition and add it my system partition? can that be done from the command prompt or would I need to use partition magic? Also, would it damage any files in those folders?

There are ways to do it from the command line, but it would be much easier to use Gnome Partition Editor instead.  It's a lot like Partition Magic, but it's free, included in the Live CD, and available in the repositories.

If you boot from the Live CD, you will find it in System > Administration > Partition Editor.  It is not installed by default when you install Ubuntu, but you can easily add it to your system after installation from Synaptic or by typing *sudo apt-get install gparted* at the command line.

The procedure would be similar to the instructions I posted earlier on reclaiming the sda6 space for your primary partition, except that instead of deleting the sda6 partition, you would resize and move it, and then resize and move the sda2 partition that contains it, before expanding sda1.

---

