---
title: "Partitioning"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by eyescrm on 2009-06-17
Hi,

I'm about to get a new computer and was wondering how I should partition my hard drives. After reading about it on several forums without finding a satisfying answer I decided to post here.

I've seen several people recommend separate partitions for pretty much every folder such as /usr, /boot, /home etc but I have no idea whether that is sensible or advantageous in my case as well as no clue about the best size for each of the partitions.

My current setup consists of 3 partitions. 1 root, 1 /home and 1 data (my second drive). I was thinking of creating several partitions (as stated above) on one hard drive and basically use the second hard drive as one big partition for data.

So basically my question is: How should I partition my 2 320 GB hard drives and how big should the partitions be respectively?

Oh and also: ext3 or ext4?

---

### Post by Bölvaður on 2009-06-17
> **eyescrm said:**
> 
My current setup consists of 3 partitions. 1 root, 1 /home and 1 data (my second drive)


That should be enough. Even though I prefer to have home within the main partition and have a special data partition (home is then only for config and temp files).

Ubuntu doesnt take more than about 20-30 GiB, and swaps are about 500 mb tops if you have a desktop, but if it is laptop then it is same size as your RAM (if you hibernate your computer).


I have a setup like this:

HD1: Windows, Swap, /data
HD2: /boot, / (Ubuntu), Fedora, Arch, /home

I got boot partition because I will not know what file systems I will be using, it is impossible to put boot on a reiser filesystem for an instance.
I got special home partition because I want it to be shared between ubuntu and fedora.


*added*
ext4 seems to have become quite good.
Not sure if they fixed the bug with big files though, so I keep my data partition on ext3.

---

### Post by NightwishFan on 2009-06-17
Personally I use ext3 since it seems to actually perform quite well. Soon though I will be using ext4, likely by the next release.

My disks are as so (rough estimates)

1 disk 200gb

sda1: 150gb ext3 /mnt/backup (all my data)
sda2: 1.5gb swap
sda3: 50gb  ext3 / (OS partition)

I use this so that I can reinstall or use a new system and simply just mount my data partition as /mnt/backup, and then link my Documents Music Pictures Videos folders into /home/username

---

### Post by H2SO_four on 2009-06-17
sda1 /swap (1GB)
sda2 /     (150GB)

sdb1 /media/storage (320GB)


Currently this is my partitions.  Really basic but does the job.  When I upgrade to Karmic I will be repartitioning everything to accomodate a multi boot setup, adding /boot, /(otherdistro) etc.

---

### Post by Stefanie on 2009-06-17
I'd do it this way:

/ 12 GB
swap 2GB (you need more if you have more RAM and you need to hibernate)
/home rest of the drive

/data drive2


it all depends on what you want of course, this isn't suitable for a dual or triple boot system.

---

### Post by ptn107 on 2009-06-17
I do it the same way Stefanie does.  You'll notice that if you keep your /home separate, the root (/) partition alone will never take up more than a few GB (3-5GB) unless you store alot of log files in /var.  So 12GB for the root partition is more that adequate, even with lots of software installed.

---

### Post by eyescrm on 2009-06-17
Thanks for the replies!

> **Stefanie said:**
> I'd do it this way:

/ 12 GB
swap 2GB (you need more if you have more RAM and you need to hibernate)
/home rest of the drive

/data drive2


it all depends on what you want of course, this isn't suitable for a dual or triple boot system.

I guess that's the best solution for me then.
So I assume if I have 4 GB RAM I should go for a 4 GB swap partition then?

> **Bölvaður said:**
> *added*
ext4 seems to have become quite good.
Not sure if they fixed the bug with big files though, so I keep my data partition on ext3.

Would it be a good idea to make my ubuntu hard drive ext4 and my data drive ext3 then? Or should I simply stay away from ext4 even though I heard mainly good stuff about it, especially performance-wise?

---

### Post by bodhi.zazen on 2009-06-17
Most linux distros need no more then 5-10 Gb.

So ..

sda1 primary 1 Gb - Used as a boot partition if using LVM and/or Encryption
sda2 primary 1 Gb - Used as a boot partition if using LVM and/or Encryption
sda3 primary 1 Gb - Used as a boot partition if using LVM and/or Encryption

sda4 extended
sda5 logical swap 1 Gb
sda6 10 Gb / Distro 1
sda7 10 Gb / Distro 2
sda8 10 Gb / Distro 3
sda9 10 Gb / Distro 4
sda10 10 Gb / Distro 5
sda12 10 Gb / I can neither confirm or deny if this one exists

... sda as many as I can make

sda14 Encrypted Data 10 gb
sda15 Unencrypted Data  150 Gb

You can use the 10 Gb PV any way you wish, add 'em to a PV (LVM) if you wish.

I find it is not worth the effort to make a separate /home or /usr /var or other partitions.

If you must have a complex set of partitions for /var /boot /usr and on I HIGHLY advise you use LVM (easier to grow, manage, and back up).

---

### Post by H2SO_four on 2009-06-17
> **eyescrm said:**
> 
So I assume if I have 4 GB RAM I should go for a 4 GB swap partition then?


You can, but having that large of swap wont benefit you.

---

### Post by LewRockwell on 2009-06-17
it should also be noted that you may leave unallocated area(s) on your hard drive(for later usage)

It sounds like your new machine will have a pair of identical hard drives and that would give you a perfect opportunity to learn about raid/mirror/clone/back-ups

Personally I would start off using one drive and partition it as follows:

One 30gb primary partition(big enough to put that other OS on if the need presented itself)

One 20gb primary partition(main distro here)

One swap partition equal to 1x your machine's MAX ram(even if you don't currently have it maxed out)

The rest will be extended and then you can partition and repartition in the extended whenever and however you like

I would stick with ext3 for now

---

### Post by eyescrm on 2009-06-17
> **LewRockwell said:**
> It sounds like your new machine will have a pair of identical hard drives and that would give you a perfect opportunity to learn about raid/mirror/clone/back-ups

I was thinking of setting up RAID 0 (I have several external hard drives that I use for backups, so no point using RAID 1) but I'm not convinced it would do me much good. Also, I'd feel more comfortable knowing that if one disk breaks only that content would be lost.

> **LewRockwell said:**
> Personally I would start off using one drive and partition it as follows:

One 30gb primary partition(big enough to put that other OS on if the need presented itself)

One 20gb primary partition(main distro here)

One swap partition equal to 1x your machine's MAX ram(even if you don't currently have it maxed out)

The rest will be extended and then you can partition and repartition in the extended whenever and however you like

I would stick with ext3 for now

Speaking of extended, primary and logical, I forgot to mention that in my original post.
I have read about it but I couldn't find out what the main difference is. Some people use only primary partitions, others only use logical ones.

Is there any rule I should follow? And if I chose 1 /, 1 /home and 1 /data, which should be primary and which logical?

---

### Post by estyles on 2009-06-17
> **eyescrm said:**
> Speaking of extended, primary and logical, I forgot to mention that in my original post.
I have read about it but I couldn't find out what the main difference is. Some people use only primary partitions, others only use logical ones.

Is there any rule I should follow? And if I chose 1 /, 1 /home and 1 /data, which should be primary and which logical?

The most important thing to remember is that you only get 4 primary partitions per drive, and an extended partition counts as a primary.  Logical partitions are not limited in this way (there may be a limit on them, but I forget what it is, and it's high enough that you don't need to worry unless you're crazy).

Also, if you ever intend to run Windows, it must boot from a primary partition (not extended, not logical), and I think it's best if it's the first partition on the drive, but that shouldn't be necessary.

Since the extended partition can hold a large number of logical partitions, it's smart to make 2 or 3 primary partitions of normal or small size (maybe for your swap would be smart, for /boot if you decide to make a boot partition, for Windows if you're gonna dual-boot, or if you just wanna leave space for *maybe* dual-booting at some point), and then make the extended partition the biggest, using the rest of the drive.

The extended partition can't be used as space - you have to divide it into logical partitions to use it.  Your data partition if you have one, since it will usually just be "all the leftover space", should definitely be a logical partition, and then you can shrink it if you need more partitions later.

(Edit: oh, and if you're using the second drive by itself for /data, then you can easily just make it a single primary partition.  in which case, the first drive should be 1-4 GB Swap, 10-20 GB /, (both as primary), and the rest on extended/logical for /home.  

I like to have a separate /var directory, so that way if my logs blow up, they don't fill up my / drive.  If you wanted to do that, 10 GB would be more than enough, though probably overkill.  5 GB would suffice.)

---

### Post by bodhi.zazen on 2009-06-17
> **eyescrm said:**
>  Speaking of extended, primary and logical, I forgot to mention that in my original post.
I have read about it but I couldn't find out what the main difference is. Some people use only primary partitions, others only use logical ones.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by eyescrm on 2009-06-17
> **bodhi.zazen said:**
> [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

I actually read that some time ago and learned quite a bit, however it wasn't really enough for me to figure out when to use what kind of partition.

> **estyles said:**
> The most important thing to remember is that you only get 4 primary partitions per drive, and an extended partition counts as a primary.  Logical partitions are not limited in this way (there may be a limit on them, but I forget what it is, and it's high enough that you don't need to worry unless you're crazy).

Also, if you ever intend to run Windows, it must boot from a primary partition (not extended, not logical), and I think it's best if it's the first partition on the drive, but that shouldn't be necessary.

Since the extended partition can hold a large number of logical partitions, it's smart to make 2 or 3 primary partitions of normal or small size (maybe for your swap would be smart, for /boot if you decide to make a boot partition, for Windows if you're gonna dual-boot, or if you just wanna leave space for *maybe* dual-booting at some point), and then make the extended partition the biggest, using the rest of the drive.

The extended partition can't be used as space - you have to divide it into logical partitions to use it.  Your data partition if you have one, since it will usually just be "all the leftover space", should definitely be a logical partition, and then you can shrink it if you need more partitions later.

(Edit: oh, and if you're using the second drive by itself for /data, then you can easily just make it a single primary partition.  in which case, the first drive should be 1-4 GB Swap, 10-20 GB /, (both as primary), and the rest on extended/logical for /home.  

I like to have a separate /var directory, so that way if my logs blow up, they don't fill up my / drive.  If you wanted to do that, 10 GB would be more than enough, though probably overkill.  5 GB would suffice.)

Oh wow, thanks :D That's exactly what I was looking for!
I guess I now know enough to partition my drives according to my needs.

---

### Post by mikechant on 2009-06-18
> Logical partitions are not limited in this way (there may be a limit on them, but I forget what it is, and it's high enough that you don't need to worry unless you're crazy).

Actually I've read that although the partition table supports up to 255 logical partitions, Linux is limited to about 16. Also I've seen at least one case where someone claimed to have trouble with 10 logical partitions, but maybe they messed up in some other way.

---

### Post by NightwishFan on 2009-06-18
I think it is best to leave most directories on one partition, for performance and space benefits. Copying data to another partition is slower than doing so on the same partition. For example, if you use 12gb for root, sometimes you need to do some heavy things such as burning a DVD or say blueray. The /tmp directory could benefit from extra space if you choose to use an image and not just burn on the fly. With 4 out of 12 gb taken just for that, space can wear thin.

For safety, keep all your data or your home directory on another large partition, and give yourself 12+ gb for root. I advise at least your data be stored on ext3.

sda1 /home or /mnt/data
sda2 swap
sda3 /

---

### Post by Zorael on 2009-06-18
> **H2SO_four said:**
> You can, but having that large of swap wont benefit you.
Won't he need 4gb of swap to be able to hibernate (suspend-to-disk)?

---

### Post by scorp123 on 2009-06-18
> **NightwishFan said:**
> I think it is best to leave most directories on one partition, for performance and space benefits.  With all due respect, but I strongly disagree to this.

You will gain far better performance if you keep partitions that are more or less static and partitions which are likely to have lots of read accesses apart from partitions that will likely have lots of write accesses.

Even though Linux filesystems try really really hard to keep fragmentation low they will fragment eventually, especially if you use your computer day and night and constantly do something with it (e.g. download large files, compile stuff, and so on).

"Space benefits" is no problem either if you do some proper planning in advance, e.g. make sure places such as /usr will have enough space.

> **NightwishFan said:**
>  Copying data to another partition is slower than doing so on the same partition.   This highly depends on what you are doing to your system. Are you just moving a few config files around or are you moving 2 TB of data while the newest OpenOffice.org is recompiling in the background? In the latter case you will enjoy better performance if you keep the filesystems apart in the long run because the write and read processes should not ever get into each other's way like they would when they were reading and writing to the same partition (where chunks of files would very quickly get into each others way and hence sooner or later cause fragmentation).

And let's not forget maintenance: Despite all the magic tricks that current Linux filesystems such as Ext4, Ext3 and XFS use ... Computers still crash here and there, and filesystems still can get corrupted here and there, despite all the journalling and checksumming and what not .... If you keep everything on one single partition, then any corruption that occurs to any location such as /boot, /usr, /opt, /var and so on will have an impact on the single "/" filesystem. If things really go badly you might end up with a hosed disk. I know all the bla bla bla about Ext4 and all its magic tricks. But hosed disks still happen.

Now, if you keep things apart then any corruption that might occur only occurs to that single filesystem and does not influence the rest. The chances of being able to reboot and that a quickie auto-filesystem-check might fix any issues are far greater this way, no matter what filesystem you use, Ext2, XFS, Ext3, ReiserFS or Ext4.

> **NightwishFan said:**
>  The /tmp directory could benefit from extra space if you choose to use an image and not just burn on the fly. With 4 out of 12 gb taken just for that, space can wear thin.  That's why I put /tmp on its own partition where it belongs. Solaris-style. ;)

> **NightwishFan said:**
>  For safety, keep all your data or your home directory on another large partition And let's not forget: Make backups! Burn the stuff to DVD's here and there. Or use external USB disks, they are cheap these days. Whatever. Make backups!

> **NightwishFan said:**
>  and give yourself 12+ gb for root. Waste of space in my humble opinion. /usr will use between 2 and 4 GB; maybe 5GB if a lot of packages get installed. But the rest is more or less wasted. And last but not least: Any process deciding to go Kamikaze on you can now easily fill up your entire "/" partition ... which is where it gets really really ugly. Once "/" is completely full you'll be in real trouble because nothing will work: You can't login, you can't use "sudo", commands take forever to complete ... All this because the filesystem is full and no log can be written anymore. Been there, done that. It's far better to keep at least "/var" away from "/" ... If any process decides to do really ugly scary stuff such as writing log files like mad then it would only fill up "/var" .... and not "/". This means you'd get error messages about log files not being written but other than that most things would still work good enough so you can fix whatever problem is happening. Mostly a simple "kill -9" to whatever process was causing the trouble will do; wipe the surplus log files, and voila: you're back in business.

My current partitioning scheme on this very laptop I am writing from:

```
Filesystem            Size  Used Avail Use%  Mounted on
/dev/mapper/RootVol         1.9G  198M  1.6G  11%  /
/dev/sda5                   228M   14M  203M   7%  /boot
/dev/mapper/HomeVol         127G   67G   54G  56%  /home
/dev/mapper/OptVol          3.7G  304M  3.2G   9%  /opt
/dev/mapper/UsrVol          5.5G  4.0G  1.4G  75%  /usr
/dev/mapper/VarVol          3.7G  648M  2.9G  19%  /var
/dev/mapper/TmpVol          7.9G  860K  7.8G   1%  /tmp
/home/sysadm/.Private       127G   67G   54G  56%  /home/sysadm
```

I regularly have to play around with commercial apps from Sun ... and they usually occupy /opt. Right now there is just "World of Goo" (a Linux game) in there and not much else. So that's why /opt is almost empty at the moment. The size of /usr is about "spot-on". It's empty now for the most part, but this changes very quickly if I install dev-packages and when I have to compile stuff, then it will grow very fast. And also /var fills up easily if I debug stuff and a lot of logs get generated. Right now it's mostly filled with leftovers from the last "dist-upgrade". /tmp is almost empty now, but it can easily start filling up if a program decides to misbehave ... or if I create ISO images, burn DVD's or things like that.

So my recommendation would be to at least keep "/var" away from "/"; if you have space then there is no need to stop there: put "/usr" (6 GB) and /opt (2 GB ... 4 GB if you have the space and don't care) and /tmp (whatever space you can spare; e.g. 8 GB?) on separate partitions. Ideally "/" should only hold /dev, /proc, /etc, /lib and /sbin and not much else (those locations _MUST_ remain on "/" and cannot be put on separate partitions!).

---

### Post by NightwishFan on 2009-06-19
Safe simple defaults, was my suggestion. The 12+ GB as root includes the /tmp directory, as well. Multiple disks would be the best setup.

---

### Post by scorp123 on 2009-06-19
> **NightwishFan said:**
>  Multiple disks would be the best setup. Fully agree. And having them mirrored is a good idea too. Just in case ...

---

### Post by bodhi.zazen on 2009-06-19
[scorp123]("http://ubuntuforums.org/member.php?u=109288") I appreciate your comments on separate partitions, I do think it is a slightly more advanced topic and one that new users installing Ubuntu for the first time probably do not *need* to worry about.

I would add a few comments.

1. I would add a word about security. With separate partitions you can use options such as noexec, nosuid, or acl on data partitions (for example). You may not want acl on other partitions.

2. I thought you could access single / partitions that are full as root, this is what reserved blocks are for. I have not had a / partition full of logs, that would be a lot of logs :lolflag:

---

### Post by NightwishFan on 2009-06-20
Multi-partitioning seems better for stability on servers. For example you can keep your mail partition to keep a mail server alive if it is spammed.

---

