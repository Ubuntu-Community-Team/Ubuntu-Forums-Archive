---
title: "file system partitions!!"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by harivittal.hk on 2009-09-30
hi!!
when i ran sudo fdisk -l cmd ,this is wot i found..

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x215e215d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   b  W95 FAT32
/dev/sda6            7649       12110    35840983+   7  HPFS/NTFS
/dev/sda7           12111       16572    35840983+   7  HPFS/NTFS
/dev/sda8           16573       19456    23165698+  83  Linux

1.why both the partitions i.e. /dev/sda2 & /dev/sda5 is starting at 3825 

2.why the system /dev/sda8 is showing linux and why not FAT32?

any help is appreciable....thank u in advance..:)

---

### Post by credobyte on 2009-09-30
> **harivittal.hk said:**
> 
2.why the system /dev/sda8 is showing linux and why not FAT32?

Why it shouldn't ( you didn't revealed the reason ) ?

---

### Post by drs305 on 2009-09-30
sda2 is the extended partition. sda5 is the first logical partition *within* the extended partition. Thus they both start at the same point.

Why do you suspect sda8 should be fat32 instead of linux?

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> Why it shouldn't ( you didn't revealed the reason ) ?
hey its like i dont knw why it shd hav tat much space allocated for /dev/sda8/ & tat under system name as 'linux'...is 'linux' a FS..i'm pretty sure its not.

---

### Post by drs305 on 2009-09-30
> **harivittal.hk said:**
> hey its like i dont knw why it shd hav tat much space allocated for /dev/sda8/ & tat under system name as 'linux'...is 'linux' a FS..i'm pretty sure its not.

The designation means the partition is formatted in ext2, ext3 or ext4, i.e. the linux filesystems.

---

### Post by harivittal.hk on 2009-09-30
> **drs305 said:**
> sda2 is the extended partition. sda5 is the first logical partition *within* the extended partition. Thus they both start at the same point.

Why do you suspect sda8 should be fat32 instead of linux?

1.bcoz i think FAT32 is the FS supported on linux..

2."mkfs.vfat -n data /dev/sda1" can i format my /dev/sda1 or any other similar non FAT FS i.e. say NTFS by using the above cmd...wats the ADV n DISADV of that??plz let me knw!!:confused:
3.hey plz can anyone let me knw whether i can format my FS as mentioned above or not..

---

### Post by ankspo71 on 2009-09-30
Hmm, isn't that your swap? I thought I remembered code 83 being swap in cfdisk...

---

### Post by drs305 on 2009-09-30
Linux swap is 82:
> 
/dev/sda5  10403   10925   4200966   82  Linux swap / Solaris


---

### Post by harivittal.hk on 2009-09-30
> **ankspo71 said:**
> Hmm, isn't that your swap? I thought I remembered code 83 being swap in cfdisk...

to what ru refering...m nt getting, can u plz be more specific..!

---

### Post by credobyte on 2009-09-30
> **ankspo71 said:**
> Hmm, isn't that your swap? I thought I remembered code 83 being swap in cfdisk...

No, swap is 82 ( [http://www.dreamlinuxforums.org/wiki/images/b/b2/Cfdisk4.png](http://www.dreamlinuxforums.org/wiki/images/b/b2/Cfdisk4.png) ).

---

### Post by harivittal.hk on 2009-09-30
> **drs305 said:**
> Linux swap is 82:

k fine so my swap space is b/w 16700-19500...so roughly arround 3MB..is tat right?if so how can i increase my swap space nw..??

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> No, swap is 82 ( [http://www.dreamlinuxforums.org/wiki/images/b/b2/Cfdisk4.png](http://www.dreamlinuxforums.org/wiki/images/b/b2/Cfdisk4.png) ).

hey then can u plz let me knw why its dispalying 83 on my system when the ID for swap on linux is 82??

---

### Post by credobyte on 2009-09-30
> **harivittal.hk said:**
> hey then can u plz let me knw why its dispalying 83 on my system when the ID for swap on linux is 82??

It's not a SWAP parition. This is how your swap should look in fdisk:
```
/dev/sda5          553       621    139104   82  Linux swap / Solaris
```

---

### Post by ankspo71 on 2009-09-30
Ahh, Ok thanks. I stand corrected :P Thanks for providing the pic too, that's the image I was trying to remember.

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> It's not a SWAP parition. This is how your swap should look in fdisk:
```
/dev/sda5          553       621    139104   82  Linux swap / Solaris
```
1.K thanx..if tats the case then i dont hav SWAP space on my system..how can i allocate the SWAP space nw..
2.If its not SWAP, then wat actually tat 83 is indicating n whr tat space is going..??

---

### Post by credobyte on 2009-09-30
> **harivittal.hk said:**
> 1.K thanx..if tats the case then i dont hav SWAP space on my system..how can i allocate the SWAP space nw..
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ( *How do I add more swap?* ).

> **harivittal.hk said:**
> 2.If its not SWAP, then wat actually tat 83 is indicating n whr tat space is going..??
No idea. Probably /tmp or /var .. Show us the output of [COLOR=Gray]df -h[/COLOR].

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ( *How do I add more swap?* ).


No idea. Probably /tmp or /var .. Show us the output of [COLOR=Gray]df -h[/COLOR].
1.this is wat it showed for:df -h
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              22G  9.6G   12G  47% /
tmpfs                 247M     0  247M   0% /lib/init/rw
varrun                247M  104K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M  2.8M  244M   2% /dev
tmpfs                 247M  284K  247M   1% /dev/shm
lrm                   247M  2.2M  245M   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sdb1             3.8G  1.1G  2.7G  29% /media/usbstick
/dev/sda7              35G   30G  5.1G  86% /media/software

wats actually the above data means??

2.Regarding tat num 83,i just found some data lik this:
> Disk /dev/hdb: 64 heads, 63 sectors, 621 cylinders
Units = cylinders of 4032 * 512 bytes
 
   Device Boot    Start       End    Blocks   Id  System
/dev/hdb1   *         1       184    370912+  83  Linux
/dev/hdb2           185       368    370944   83  Linux
/dev/hdb3           369       552    370944   83  Linux
/dev/hdb4           553       621    139104   82  Linux swap

:)

---

### Post by credobyte on 2009-09-30
```
/dev/sda8           16573       19456 **   23165698+**  83  Linux 			 		
-------------------------------------------------------------
/dev/sda8              **22G**  9.6G   12G  47% /
```

I think you've got the idea now ? sda8 is your root partition.

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> ```
/dev/sda8           16573       19456 **   23165698+**  83  Linux 			 		
-------------------------------------------------------------
/dev/sda8              **22G**  9.6G   12G  47% /
```

I think you've got the idea now ? sda8 is your root partition.

1.Yeah ya tats rt ..thanx ...so i gt to knw tat the number 83 is mainly used to denote the primary,logical partitions..!!

2.I'm using AWN manager and have customized my desktop...i dont hav any ext GRAPHICS CARD in ma system...so how can iget the graphics drivers to support this..bcoz after i startd using AWN my system is getting hanged sometimes...plz help..!!

---

### Post by credobyte on 2009-09-30
> **harivittal.hk said:**
> 
2.I'm using AWN manager and have customized my desktop...i dont hav any ext GRAPHICS CARD in ma system...so how can iget the graphics drivers to support this..bcoz after i startd using AWN my system is getting hanged sometimes...plz help..!!

What type of card do you have ( ATI, NVidia, etc. ) ? Have you checked [COLOR=Gray]System / Administration / Hardware drivers[/COLOR] ?

---

### Post by oldos2er on 2009-09-30
> **harivittal.hk said:**
> i gt to knw tat the number 83 is mainly used to denote the primary,logical partitions..!!


 AFAIK, "83" refers only to a Linux-native file system, not to partition type.

---

### Post by harivittal.hk on 2009-09-30
> **oldos2er said:**
> AFAIK, "83" refers only to a Linux-native file system, not to partition type.
1. Oh k..but i saw somethin lik this, what can u say for this...
>   Device Boot    Start       End    Blocks   Id  System
/dev/sda1             1      3258  26169853+  83  Linux
/dev/sda2          3259      6516  26169885   83  Linux
/dev/sda3          6517      9774  26169885   83  Linux
/dev/sda4          9775     22800 104631345    5  Extended
/dev/sda5          9775     13032  26169853+  83  Linux
/dev/sda6         13033     16290  26169853+  83  Linux
/dev/sda7         16291     19584  26459023+  83  Linux
/dev/sda8         19585     22800  25832488+  83  Linux

the first 3 is primary partitns, /dev/sda4 is an extended partition n next 4 r the logical partitions..!!

---

### Post by harivittal.hk on 2009-09-30
> **credobyte said:**
> What type of card do you have ( ATI, NVidia, etc. ) ? Have you checked [COLOR=Gray]System / Administration / Hardware drivers[/COLOR] ?
1. I checked it out,it showed as:"no proprietary drivers are in use in this system".
2.how to check which card i am using??

---

### Post by oldos2er on 2009-09-30
> **harivittal.hk said:**
> 1. Oh k..but i saw somethin lik this, what can u say for this...

the first 3 is primary partitns, /dev/sda4 is an extended partition n next 4 r the logical partitions..!!

 The "83"  tells you the partition (either primary or logical) is using a native Linux file system, which could be ext2, ext3, etc.

---

