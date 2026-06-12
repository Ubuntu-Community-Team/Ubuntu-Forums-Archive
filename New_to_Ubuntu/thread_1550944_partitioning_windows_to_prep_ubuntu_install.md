---
title: "partitioning windows to prep ubuntu install"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by DarinB on 2010-08-11
I am traveling to visit my 81 year old mother
she has a dell Inspiron 9300 Intel Pentium 1.60GHS
339Mhz 512Mb Ram C: Used 12.2Gb 
Free 46.3 Free D: Used 1.3GB Free 88.6 GB
I am sure the hard drive is partitioned and this lap top does not have two separate hdds can i merge them in windows disk manager then defrag and install lucid. or should i install lucid on half the D: or does it have to be on the c: and put the home folder on the D:partition? there is data right now on the D: partition. any ideas how to approach this laptop?

---

### Post by ieee488 on 2010-08-11
I would shrink down D:\ and install Ubuntu there.

Windows XP doesn't have a built-in tool to do this. I have used EASEUS found at [www.partition-tool.com](www.partition-tool.com)

---

### Post by DarinB on 2010-08-11
can i have ubuntu on the D drive and the winxp on the c and still have the dual boot?

---

### Post by Dsafire on 2010-08-11
> **DarinB said:**
> can i have ubuntu on the D drive and the winxp on the c and still have the dual boot?

Sure can. I set my husband's PC up that way. I have my Ubuntu on a seperate physical drive D and it dual boots just fine.

---

### Post by john newbuntu on 2010-08-12
If I read that right, you have 1.3GB of data on D: drive and 46.3(GB I assume) free on C:\ drive.  If you could copy over the "D :\" data on to a new folder on the C:\ drive, it will free up D drive.  This is provided you have only data and no programs installed on D.
Then you could just delete this partition in Windows and use it for Ubuntu (dual boot)

---

### Post by DarinB on 2010-08-12
I thought of that but it maybe possible that some windows apps are pointed in that direction... 
about installing on the D drive? I would do a manual partitioning in set up and just choose that partition and make it the /boot or just / ??...

---

### Post by DarinB on 2010-08-12
anybody on this question of / or /boot

---

### Post by john newbuntu on 2010-08-12
After shrinking the D: \ drive and making space for your Ubuntu and swap partitions, you would install "/" into the Ubuntu partition.  You generally do not have to do anything with /boot.  Under the default scheme, all file systems would go under / (except swap of course).

---

### Post by DarinB on 2010-08-13
thanks I have always been confused about what /boot is used for? 
I have set up some fairly creative partition set ups. 

Therefore: when i get to the partitioning part i go to Manual Partitioning > put Ubuntu on the D: drive > make the mount point / > will i have to create a swap file? or will it create it? I wonder if i should take a copy of gparted live and use that to create all the partitions first. I would love to use the entire d: drive for Ubuntu its about 100GB... but even if i take half it will be more than enough for her. 
Maybe? i can put the swap on the c: drive since she only has 512mb of ram but it may not help she only has one HDD that was partitioned into two Drives so it may not add to speed since its not a separate HDD. Or? maybe it will? I am taking suggestions. Of course if i can figure out how to dual boot puppy linux that maybe the fastest OS. Love the PUP! but it is painful to set up...No where as easy as Ubuntu, Debian or Linux Mint(the easiest out of the box)

---

### Post by john newbuntu on 2010-08-14
> **DarinB said:**
> 
Therefore: when i get to the partitioning part i go to Manual Partitioning > put Ubuntu on the D: drive > make the mount point / 
I am a little confused here.  I suppose you are not doing a Wubi install, are you?  If so then ignore what I said before.  Someone who has experience with Wubi could help you here.

But if you are truly doing a dual boot with Win and Ubuntu, you would have to carve out a new partition from your D drive and install Ubuntu on it.  C: and D: drives do not come into the picture while installing true dual boot.

---

### Post by DarinB on 2010-08-14
I have been with Ubuntu since 2007 with Feisty i am not sure about wubi i will use a liveCD. I have never done it any differently. I did try to put puppy Linux on my PC as a triple boot and killed my grub. that was my last venture into alternative methods. I will be in CA around the 26th and am taking my backup laptop so i will be back online if i encounter a problem...for now i am gathering data. so i know that disks and utils to take with me.

---

### Post by LewRockwell on 2010-08-14
> **DarinB said:**
> 

snip...

I am taking suggestions. Of course if i can figure out how to dual boot puppy linux that maybe the fastest OS. Love the PUP! but it is painful to set up

snip...



You should DEFINITELY try out the latest Lucid Puppy!

Much easier than ever before!

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

.

---

### Post by DarinB on 2010-08-14
I once killed my grub by trying to install puppy on my box as a dual boot with vista...not sure i am ready to do that to my Mother's lap top. 
do you think that the system is too small for a Linux Mint 9 distro?
or Lucid it does have 512 of Ram?
btw why is it called lucid puppy is it based on Ubuntu or Deb package manager?

---

