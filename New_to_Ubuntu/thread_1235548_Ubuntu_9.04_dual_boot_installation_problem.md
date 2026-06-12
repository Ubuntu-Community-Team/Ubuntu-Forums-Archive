---
title: "Ubuntu 9.04 dual boot installation problem"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by GulamGaus on 2009-08-09
hi everyone

I have a portege (386, 900mhz) lappie with me. I changed its original 80GB HDD with a new 160GB HDD. I installed XP in its first 40GB & I am planning to use the rest of the space for Ubuntu9.04. To my surprise at the time of installation, I found that the installer reporting that there is no OS in the system..the system shows 160GB as free space..I am confused & donno why? 
Can any one help?
GG
++

---

### Post by LewRockwell on 2009-08-09
you might provide us with a screenshot of your partition editor via the LiveCD

.

---

### Post by GulamGaus on 2009-08-11
> **LewRockwell said:**
> you might provide us with a screenshot of your partition editor via the LiveCD

.

Pls find the screenshot of the partition via liveCD

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xef3aef3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40960048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5101       19457   115322602+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           17513       19457    15623212+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda5            5101        6200     8835687   82  Linux swap / Solaris
/dev/sda6            6202        7660    11719386   83  Linux
/dev/sda7            7662       11430    30274461   83  Linux
/dev/sda8           11432       15078    29294496   83  Linux
/dev/sda9           15080       17511    19535008+  83  Linux
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


Kindly help!
GG

---

### Post by GulamGaus on 2009-08-17
Well I fixed the problem. Nothing gr8. It was something that I wanted to avoid but finally a clean fresh installation of all OS fixed the problem.

---

