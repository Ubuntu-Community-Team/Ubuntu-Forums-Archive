---
title: "Disk space"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by jfbooth on 2009-12-28
When I installed Xubuntu from its Live CD, I "told" it to use entire hard drive which is a 10G drive.  Terminal command df -h shows:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.8G  2.7G  5.6G  33% /
udev                  249M  228K  249M   1% /dev
none                  249M     0  249M   0% /dev/shm
none                  249M   84K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw

and I am wondering about the 'missing' 1.2G.  Being an absolute beginner, I can only assume a couple of things.  The 1.2G in question is another partition of some sort .. like swap file or something?  The 1.2G in question is an OLD partition (Compaq system.sav) and the install did not actually use the entire drive.

Help, advice, criticism, opinions welcome.  Thank you in advance.

---

### Post by chewearn on 2009-12-28
Run:
```

sudo fdisk -l

```

It will show you if there is any other partition.

---

### Post by jfbooth on 2009-12-28
thank you for the quick reply.  Does the following look 'right"?  

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044265

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

"Sorta" looks right to me ... but seems to show 3 partitions (sda 1,2,5) rather than two.  

I will admit 2 and 5 indicate the same START/END ... which would apparently make them one partition .. totaling two ...   Sorry I am so ignorant.

Basically, I just want to know I am using the entire HD for Xubuntu.  Thanks again.

---

### Post by chewearn on 2009-12-28
Yes, that looks OK.

sda1 is your boot partition containing the root filesystem.
sda2 is an extended partition.
sda5 is a logical partition, which sits inside the sda2 extended partition.  It's the swap partition.

---

### Post by jfbooth on 2009-12-28
appreciate your time and wisdom.

---

### Post by lavinog on 2009-12-28
```
9524874240 / (1024^3) = 8.8707G
```
It could be that the the difference is the way the unit prefixes are converted.
Harddrive manufactures say that a kb=1000 bytes.  Computers like to use 1 kb=1024 bytes because it is a power of 2.

see this for more info: [http://en.wikipedia.org/wiki/Bytes#Unit_multiples](http://en.wikipedia.org/wiki/Bytes#Unit_multiples)

---

