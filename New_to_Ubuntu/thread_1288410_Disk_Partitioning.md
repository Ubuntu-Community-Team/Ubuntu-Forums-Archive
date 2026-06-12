---
title: "Disk Partitioning"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-10-11
I seem to have done something dumb when I was setting up my PC today. I thought I need a partition for /home /var and /user.....and I do!

Under Places>Computer these 3 show up as being mountable disks!

I also seem to have 2 /home areas now....the regular one...and the /home that I have created.....before I start filling these up, I really need to sort out the duplication (if any) to avoid confusion further down the road.....what should I do?

---

### Post by unutbu on 2009-10-11
Open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l              # Prints the partition table

cat /etc/fstab             # Shows where the partitions are mounted
```

---

### Post by laidback on 2009-10-11
Have a look in System>Administration>Partition Editor for a graphical view. The program you are using is Gparted, you cannot edit your HD at this stage as it's still mounted. You'll need to boot from a Live CD to be able to edit it. The Ubuntu Live CD has Gparted as part of the distro. (there are other ways of editing an HD but using a Live CD is a good place to start).

---

### Post by LewRockwell on 2009-10-11
> **dunbrokin said:**
> I seem to have done something dumb when I was setting up my PC today. I thought I need a partition for /home /var and /user.....and I do!

Under Places>Computer these 3 show up as being mountable disks!

not disks...but partitions...

> **dunbrokin said:**
> I also seem to have 2 /home areas now....the regular one...and the /home that I have created.....before I start filling these up, I really need to sort out the duplication (if any) to avoid confusion further down the road.....what should I do?

the majority of users don't require a bunch of separate partitions within each operating system

of course, using different partitions for different operating systems is wise

as always, your mileage may vary

.

---

### Post by dunbrokin on 2009-10-11
> **unutbu said:**
> Open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l              # Prints the partition table

cat /etc/fstab             # Shows where the partitions are mounted
```

pj@pj:~$ sudo fdisk -l 
[sudo] password for pj: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xa3b53557 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1         243     1951866   83  Linux 
/dev/sda2           29186       30401     9767520   83  Linux 
/dev/sda3           28943       29185     1951897+  82  Linux swap / Solaris 
/dev/sda4             244       28942   230524717+   5  Extended 
/dev/sda5             244        2675    19535008+  83  Linux 
/dev/sda6            2676        5107    19535008+  83  Linux 
/dev/sda7            5108       28942   191454606   83  Linux 

Partition table entries are not in disk order 
pj@pj:~$ cat /etc/fstab 
# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda2 during installation 
UUID=294e9d92-e005-486e-8559-a8cc0282fe93 /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda3 during installation 
#UUID=89e4f802-4dc5-4904-9d60-c49b10f6a935 none            swap    sw              0       0 
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/mapper/cryptswap1 none swap sw 0 0 
pj@pj:~$ 


OK, this is where I am. Where I want to be is with a partition for /home a partition for /var and a partition for /usr/local. I am not so bothered about the last 2 but definately want a /home to prevent wiping my hard disk (as I did today) when doing a clean install of Karmic.

---

### Post by dunbrokin on 2009-10-11
> **laidback said:**
> Have a look in System>Administration>Partition Editor for a graphical view. The program you are using is Gparted, you cannot edit your HD at this stage as it's still mounted. You'll need to boot from a Live CD to be able to edit it. The Ubuntu Live CD has Gparted as part of the distro. (there are other ways of editing an HD but using a Live CD is a good place to start).

Thank you ....got that.

---

### Post by dunbrokin on 2009-10-11
> **LewRockwell said:**
> 

the majority of users don't require a bunch of separate partitions within each operating system

.

Love the name...I wonder what the real Lew Rockwell thinks :)

Yeah, as I have said elsewhere, the great thing about having a home partition is that it prevents yourself from doing stupid things....like I just did today and wiping out your hard disk on a clean install!!

---

### Post by unutbu on 2009-10-11
Oops, would you also post:
```
sudo blkid -c /dev/null
mount

```

---

### Post by dunbrokin on 2009-10-11
> **unutbu said:**
> Oops, would you also post:
```
sudo blkid -c /dev/null
mount

```

pj@pj:~$ sudo blkid -c /dev/null 
[sudo] password for pj: 
/dev/sda1: LABEL="Boot" UUID="d4432fd2-71e0-4048-94be-84bde7742fee" TYPE="ext4" 
/dev/sda2: LABEL="/" UUID="294e9d92-e005-486e-8559-a8cc0282fe93" TYPE="ext4" 
/dev/sda5: LABEL="/usr/local" UUID="7d66ab9d-85e0-4ce8-ab8a-6b1dc7e01c2c" TYPE="ext4" 
/dev/sda6: LABEL="/var" UUID="5f85d485-7216-4d6d-ba33-b855535d3678" TYPE="ext4" 
/dev/sda7: LABEL="/home" UUID="8e68d854-bf73-4ef5-ac38-d388ed4207fb" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="b8a7571f-446e-4c15-884b-bfb514e1c989" TYPE="swap" 
pj@pj:~$ mount 
/dev/sda2 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw) 
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
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
/home/pj/.Private on /home/pj type ecryptfs (ecryptfs_sig=0e12b36b177b4588,ecryptfs_fnek_sig=114754908ba8a18d,ecryptfs_cipher=aes,ecryptfs_key_bytes=16) 
gvfs-fuse-daemon on /home/pj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pj) 
pj@pj:~$

---

### Post by ranch hand on 2009-10-11
Yes, this is a good idea.  Do use the livecd to do your partitioning. 

It is best to set this up at install time.  I pre-format the partitions before installing.  Then you konw which they are and can just edit them to what you want in the installer.

It is a good idea to have a written plan for your drive if you have more than about two partitions.

On yours I would cut down to one primary partition and have the rest extended.  20 to 25Gb for your root partition of your main OS.  It will boot fastest from there at the beginning of the drive.  I like a large root partition as they slow down if more than 50% full.  On this OS, which has become my favorite, I just put a 15Gb / on it and it is 51% used.  I haven't noticed any slow down but if I had know I would use this sucker the way I do it would have been bigger than it is.

I just use / and /home but have thought about a /var partition.  I am going to be redoing my main drive for 10.04 at the latest and will do some thing like that with my main OS.

---

### Post by unutbu on 2009-10-11
dunbrokin, right now I think your /home, /var and /usr are still in /dev/sda2. Is that correct?

Here is a guide for moving your /home to sda7. [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). I suggest you read it all the way through before you try it, so you understand how it works and what each command is doing. If anything doesn't make sense, post here and we'll try to help.

Although the guide was written for moving the /home directory to a separate partition, 
the same method can be used to move /var and /usr if that is what you wish.

Could I make a suggestion? Instead of moving /var (or /usr or both), reserve at least one of those partitions so you can install Karmic or another Linux distro at some future date, without overwriting your current installation (sda2). There is a clear advantage in upgrading this way -- you can test out a new distro without losing your working system.

---

