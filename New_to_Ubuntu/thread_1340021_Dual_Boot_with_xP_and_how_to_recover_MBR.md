---
title: "Dual Boot with xP and how to recover MBR"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Adi100 on 2009-11-28
Greetings to all.

I have been trying Ubuntu 9.04 in VMware on Xp for few weeks, Now I want to install it on my HD in Dual Boot Configuration.

My Problem starts as : I have three primary partition on my HD( Partition1: XP , Partition2: Win 7 RC, Partition3: Databackup).

-I want to install Ubuntu on partition2( primary), I have gone throgh many online docs like this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). they all discuss about resizing the partitions none of them describe how to use an existiting Partition. Can the existing Partitions be used..?

-Second problem they categorically mention you should choose another Partition for swap file. this mean I will loose my Databackup partition.

- Can swap file be installed on same Partition( ie Partition2)..?.

-How to remove Linux and recover MBR later.Will booting from Ubuntu Live CD and deleting linux partion and running fxmbr from windows CD will do.

Regards

Adi

---

### Post by yeats on 2009-11-28
> My Problem starts as : I have three primary partition on my HD( Partition1: XP , Partition2: Win 7 RC, Partition3: Databackup).

-I want to install Ubuntu on partition2( primary), I have gone throgh many online docs like this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot). they all discuss about resizing the partitions none of them describe how to use an existiting Partition. Can the existing Partitions be used..?

Yes - when you get to the partitioning step, choose Manual Partitioning, then delete the Windows 7 partition, which will create free space.  Then choose that free space as where you want to install.

> -Second problem they categorically mention you should choose another Partition for swap file. this mean I will loose my Databackup partition.

- Can swap file be installed on same Partition( ie Partition2)..?.


The swap file can be created from the space you free up deleting Win 7.  It's generally recommended to make swap be twice the size of your RAM, though if your space is otherwise limited, it can be smaller.


> -How to remove Linux and recover MBR later.Will booting from Ubuntu Live CD and deleting linux partion and running fxmbr from windows CD will do.


To remove, you can just delete the Linux partition.  As far as recovering your MBR goes, there are *many* tutorials on the web - Google is your friend here.  Also, there's no harm in just using GRUB to boot.

---

### Post by Adi100 on 2009-11-28
Thank you crissharp123 for solving this problem.:p

Regards

Adi100

---

### Post by lkraemer on 2009-11-28
There is a MAXIMUM of FOUR Primary Partitions that can be allocated on
any single Physical Drive.  You currently have three used, and that would
allow the Linux-Swap to be created as a Primary Partition on your drive.
This does however, require you to use another partition for Ubuntu, unless
you create a Logical (EXTENDED Partition) in which case you can create
many other Logical partitions.  My preference is to not use Logical.

GRUB Tutorial:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

DUAL BOOT & SUPERGRUB Info:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)  

Supergrub makes it easy to replace your original Windows MBR.  Just read
a bit on Supergrub or grub from the above sites.

Also, typically the Linux-swap partition is placed last (on the right of
the Gparted display) and is 2 Times your Available RAM.  This means you're
likely going to have to resize or move some partitions to get it placed there.  You can format the Win 7 partition with Gparted while you have
it booted, just be sure to use Supergrub first to replace the MBR or you'll have trouble booting back into windows.

Shouldn't take you more than 30-45 minutes to do it all.

JUST BE SURE to SAVE any DATA FILES you need of the Win 7 Partition FIRST!

lk

---

### Post by Bartender on 2009-11-28
Is partition 3 your own data or is it the recovery data put in place by the manufacturer?
Here's what I'm thinking - get rid of partitions 2 and 3, and create one extended partition out of that space.  Otherwise I fear you're going to end up with a very odd partitioning scheme, and you'll be boxed in by too many primary partitions.

If partition #3 is your own data, perhaps you can save it to an external HDD, then bring it back when you're done setting up partitions and installing Ubuntu?
If it's the manufacturer's recovery partition, can you burn recovery discs and delete the partition?

The Windows OS needs to be on a primary partition.  Once you've given Windows a home on a primary partition, everything else can be on logical partitions within an extended partition "box".  Windows can *access* logical partitions, as long as they're formatted NTFS (there's really no need for FAT anymore), it just can't *run* from a logical partition.

Linux can run from a logical partition, and access data (NTFS or ext) from logical partitions.

---

### Post by Adi100 on 2009-11-28
Thank you lkraemer, I will go to Grub Tutorial site you mentioned.
But at this time I am not familiar with supergrub., why it is required to be installed first.There is already Win7 MBR and its boot manager in First partition, Which can load ntldr or winload.exe as requsted.

now I got your point unless the original bootcode at first sector for first partition is not present grub can not know wether windows is present or not.

Regards

Adi

---

### Post by Adi100 on 2009-11-28
Hi, Bartender,

you are right I will end up with a Odd partition. partition 3 is Databackup not Recovery partition( As it was set by me not manufacturer).

My partitions are like this partition1 Xp 50Gb , Part:2 Win 7 RC 30 GB, Partition3: DataBackup 155GB.

Let me tell you my fear that I think( I am not expert, I am ordinary Home user) Creating frequent partitions and writing File system makes Disk Dirty(i.e Format information on sectors)

the only way to avoid this Boxed Partition is to Delete partion2 and 3 and create a new DataBackup partition of 150GB adjacent to Xp partion and install linux in last Partition.

Thank you for pointing out this odd configuration, and making me to think twice beforegoing ahead.

Regards

Adi

---

