---
title: "Partition help."
date: 2009-06-03
forum: New to Ubuntu
---

### Post by moebob24 on 2009-06-03
So being the idiot that I am,I have managed to install UNR onto my Asus 901 twice. The PC comes with 2 partitions on the disc and I installed a copy of Ubuntu on both of them.

So...

How do I remove one of the partitions and make the disc a whole, or, remove one of the installs and make it usable to Ubuntu.

Thanks

---

### Post by indytim on 2009-06-03
Welcome to Ubuntu Linux.  Easy on yourself as we all start out at the very beginning.  Without getting into too much technical detail for now, the easiest way to remidy your situation is to re-install.  This time select the option to use the entire hard drive.  That will wipe out all of your existing partitions and files and install Ubuntu with the required partitions (2 : 1 swap and one for Ubuntu).  Should be good to go from there.

IndyTim

---

### Post by x33a on 2009-06-03
hi, simply format the ubuntu partition you want removed with gparted.
 
after that, you might have reinstall grub (if you format the partition you installed ubuntu on, later).

---

### Post by moebob24 on 2009-06-03
UPDATE:
So I now have Gparted installed and this is what it shows in that:
There are 2 discs, both of which have UNR installed on it.
One is labeled "/dev/sda1" and this one is 3.75GiB.
The other one is "/dev/sda1" as well which makes sense because there are 2 OSes installed. The second one has 7.51GiB.

Inside each of them it shows:
**Partition Name:** /dev/sda1
**File System:** ext3
**Mount Point:** /
**Flags:** boot

**Partition Name:** /dev/sda2
**File System:** extended 
**Mount Point:** N/A 
**Flags:** N/A
Then in a sub-category below "sda2"
**Partition Name:** /dev/sda5
**File System:** linux-swap

The only difference between the 2 drives is on the first one (3.75GiB) there is a little key icon after each partition name. This does not show up on the 7.51GiB partition.
I want to clear the second partition (7.51GiB) and have never done any partitioning before.

---

### Post by moebob24 on 2009-06-03
> **indytim said:**
> Welcome to Ubuntu Linux.  Easy on yourself as we all start out at the very beginning.  Without getting into too much technical detail for now, the easiest way to remidy your situation is to re-install.  This time select the option to use the entire hard drive.  That will wipe out all of your existing partitions and files and install Ubuntu with the required partitions (2 : 1 swap and one for Ubuntu).  Should be good to go from there.

IndyTim

That is actually what I was trying to do when I installed it the second time. I selected entire disc and it ended up installing it on just the first partition. I'm gonna try it again and look through the partition options again.

---

### Post by moebob24 on 2009-06-03
> **x33a said:**
> hi, simply format the ubuntu partition you want removed with gparted.
 
after that, you might have reinstall grub (if you format the partition you installed ubuntu on, later).

But what should I format it as. In Gparted there are many options.

---

### Post by Don1500 on 2009-06-03
Since you will have a single OS on your computer it is best to use a format that works well with that OS. ext3 is a proven and good selection. ext4 will be better, but there are some bugs in it right now, or at least that is what I've been told. You have the option to format it to anything you want, but ext 3 or 4 are what I would suggest. Also remember to set aside about 1~4 GIG as linux SWAP (about the same size as your RAM).

Since you are doing a full install and are going to wipe you hard drive anyway, play around in G-Parted till you fully understand all it can do. This might be a good time to learn about partitioning and your hard drive.

---

### Post by moebob24 on 2009-06-03
> **Don1500 said:**
> Since you will have a single OS on your computer it is best to use a format that works well with that OS. ext3 is a proven and good selection. ext4 will be better, but there are some bugs in it right now, or at least that is what I've been told. You have the option to format it to anything you want, but ext 3 or 4 are what I would suggest. Also remember to set aside about 1~4 GIG as linux SWAP (about the same size as your RAM).

Since you are doing a full install and are going to wipe you hard drive anyway, play around in G-Parted till you fully understand all it can do. This might be a good time to learn about partitioning and your hard drive.

I'm still not sure how to fully wipe the partitions. I am begging to think that each one of these partitions is a physical partition.

So you are saying format the drive to ext3. Now the drive that I am leaving alone has some swap on it. Should I put some on the one I am formatting or does it matter.

---

### Post by moebob24 on 2009-06-03
Ok so I just formatted the drive to ext3. It is cleared out. The partitions called "extended" and "linux-swap" are still there. It won't let me format those. However now I cannot save file to that drive, and the permissions are not viewable in the properties.

---

### Post by Don1500 on 2009-06-03
Look to the second paragraph of my previous post. When you format the drive, you wipe it clean (well, as far as we are concerned here), all data will be lost. Using G-parted you can do this in steps. 
1. Delete all partitions, then hit "APPLY"
2. Set up your new partitions, set the format option (ext3) and the swap partition, then hit "APPLY" 

If you can do this you have a clean drive with a single ext3 partition and a SWAP partition.

---

### Post by moebob24 on 2009-06-03
> **Don1500 said:**
> Look to the second paragraph of my previous post. When you format the drive, you wipe it clean (well, as far as we are concerned here), all data will be lost. Using G-parted you can do this in steps. 
1. Delete all partitions, then hit "APPLY"
2. Set up your new partitions, set the format option (ext3) and the swap partition, then hit "APPLY" 

If you can do this you have a clean drive with a single ext3 partition and a SWAP partition.

Thats thing, it won't let me delete the partitions. It will only let me delete the linux-swap.

EDIT: I can create a new partition table, if that would wipe the disc. After i could install ext3 and the swap.
If I were to do that there are a few options:
-msdos
-aix
-amiga
-bsd
-dvh
-gpt
-mac
-pc98
-sun
-loop

---

### Post by LewRockwell on 2009-06-03
you're using a netbook with no optical drive right?

so I'm going to assume you're booting from a thumb drive.

what's happening is that when you boot-up your live-run OS is actually locking onto and using the swap partition in the extended partition on your drive.

you might try "noswap" as a boot option

you might also use gparted's "swap off" feature if available

also(to the general interwebs audience), I recommend learning *nix on a full-size/featured desktop or laptop...and not on your minis and pdas...

---

### Post by moebob24 on 2009-06-03
> **LewRockwell said:**
> you're using a netbook with no optical drive right?

so I'm going to assume you're booting from a thumb drive.

what's happening is that when you boot-up your live-run OS is actually locking onto and using the swap partition in the extended partition on your drive.

you might try "noswap" as a boot option

you might also use gparted's "swap off" feature if available

also(to the general interwebs audience), I recommend learning *nix on a full-size/featured desktop or laptop...and not on your minis and pdas...

I'm not running it off the USB anymore, it is actually installed on the drive. Now I am trying to get the other drive to be used as extra hard drive space to store files and what not. But it won't let me write to it.

---

### Post by LewRockwell on 2009-06-03
> **moebob24 said:**
> I'm not running it off the USB anymore, it is actually installed on the drive. Now I am trying to get the other drive to be used as extra hard drive space to store files and what not. But it won't let me write to it.

and it won't let you modify the drive...while you're running the computer FROM the drive

boot up from the live-run on the USB thumb drive and then you can do whatever you want to the drive

---

### Post by moebob24 on 2009-06-03
> **LewRockwell said:**
> and it won't let you modify the drive...while you're running the computer FROM the drive

boot up from the live-run on the USB thumb drive and then you can do whatever you want to the drive

Im not running it from this drive though. Im running UNR from a different drive.

---

### Post by LewRockwell on 2009-06-03
> **moebob24 said:**
> So being the idiot that I am,I have managed to install UNR onto my Asus 901 twice. The PC comes with 2 partitions on the disc and I installed a copy of Ubuntu on both of them.

So...

How do I remove one of the partitions and make the disc a whole, or, remove one of the installs and make it usable to Ubuntu.

Thanks

2 partitions...ONE DRIVE...

what do you get when you're in terminal and request:
```
sudo fdisk -l
```

(and that's a little L, NOT a 1)

---

### Post by LewRockwell on 2009-06-03
or, if you're running an OS from an external drive, you'll still need to turn off the swap(s)

---

### Post by moebob24 on 2009-06-03
Ok I understand now. I booted in from my USB and I am formatting the second drive as ext3 now.

"fdisk -l" does not return anything.And I ran that when I was not on the USB.

---

### Post by moebob24 on 2009-06-03
All replies should go to this thread now:
[URL="http://ubuntuforums.org/showthread.php?p=7395550#post7395550"]
[COLOR="Red"]http://ubuntuforums.org/showthread.php?p=7395550#post7395550[/COLOR][/URL]

---

### Post by pablolie on 2009-06-21
they *are* separate ssd drives on the eeepc 901. the 4 gb is soldered on and is supposed to be a bit faster, the 8gb is a replaceable ssd drive.

i have ubuntu 9.04 running very well on our eeepc 901. 

i recommend to do the following during installation:

go for manual partitioning.

delete all partitions until both drives are unassigned.

then create a 4gb primary partition on sda, with ext4 and mount point "/". this will copy all ubuntu OS components onto sda.

the 8gb i'd define as ext4 and mount point "/home", meaning all user directories and data will map there.

ignore the warning about a swap file, doesn't make sense with ssd drives. 

works like a charm, and i think it is the most elegant partitioning with the eeepc 901.

---

