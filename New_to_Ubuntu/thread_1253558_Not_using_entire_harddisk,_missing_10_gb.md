---
title: "Not using entire harddisk, missing 10 gb"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by bregnernice on 2009-08-30
Hi. I've been using ubuntu for more than two years. Started with a dual boot with windows but quickly changed entiredly to ubuntu. 
I have a 80 gb harddisk in my laptop but ubuntu only uses 70,4 of it.

My question is how can i get ubuntu to recognize and use all my harddisk?

I just made a clean install of ubuntu 9.10 and in the install setup it saw my 80 gb harddisk, i chose option 'use entire disk' and still end up with ten gigs missing, just as with my previous installs.

I suspect the missing ten gigs are the part of the harddisk i had windows files on earlier. 

I want all my 80 gigs for my lovely ubuntu desktop!:)

---

### Post by MelDJ on 2009-08-30
Ubuntu is uses the 10gb when it is installed

---

### Post by sasho_zl on 2009-08-30
What filesystem are you using? If you are using journaling file system there will be part of the hard disk left for that journal.

---

### Post by unutbu on 2009-08-30
Please post the output of 
```

sudo fdisk -l       # Show the size of your partitions
df                  # Show the size of your filesystems
```

---

### Post by bregnernice on 2009-08-30
HAHA. ok sweet:)

Very simple!

I just get confused because i look in system monitor under file systems and it reads total harddisk space 70.6 gb, free 67,8 gb, available 64,2 gb and used 2,8 gb. So i wonder why it doesnt say total 80 gb, used 10+ gb (ubuntu installation) etc?

Thanks for the answer!

---

### Post by bregnernice on 2009-08-30
the filesystem is ext4 i think.. dont remember seeing anything about journal..

Heres the output:

beetroot@beetroot:~$ sudo fdisk -l
[sudo] password for beetroot: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dd81dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9359    75176136   83  Linux
/dev/sda2            9360        9729     2972025    5  Extended
/dev/sda5            9360        9729     2971993+  82  Linux swap / Solaris
beetroot@beetroot:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73995680   2920124  67316752   5% /
tmpfs                   507376         0    507376   0% /lib/init/rw
varrun                  507376       108    507268   1% /var/run
varlock                 507376         0    507376   0% /var/lock
udev                    507376       256    507120   1% /dev
tmpfs                   507376       120    507256   1% /dev/shm
beetroot@beetroot:~$ 


Looks ok?:P

---

### Post by cascade9 on 2009-08-30
> **bregnernice said:**
> Hi. I've been using ubuntu for more than two years. Started with a dual boot with windows but quickly changed entiredly to ubuntu. 
I have a 80 gb harddisk in my laptop but ubuntu only uses 70,4 of it.

I suspect the missing ten gigs are the part of the harddisk i had windows files on earlier. 

I want all my 80 gigs for my lovely ubuntu desktop!:)

Its very very doubtful that your 'missing' 10GB is where windows was. 

Nasty trick from the hard drive manufacturers is 1000MB = 1GB. Almost everything else 1024MB = 1GB. On that alone, 80GB= 74.5GB. Then theres the space lost to formating (like sasho_zl said, its space lost to the  journal, or file allocation system, etc). 70.4GB is not a problem, its probably what your drive should be ;)

---

### Post by bregnernice on 2009-08-30
Informative! Thanks everyone for your quick answers!

I really need an external harddisk!:KS

---

