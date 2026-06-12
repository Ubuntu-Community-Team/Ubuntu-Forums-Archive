---
title: "Dual boot questions"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by Meliority on 2010-10-28
So i have searched around the forum a bit and it occur to me that one of the things that might be useful is a bit of a primer on Dual Booting.

Anyone who has installed Ubuntu on a second partition with windows on the first seems to be OK.

Using multiple drives, especially where windows comes second, causes ubuntu to have difficulty booting into Ubuntu afterwards

Partitioning and installing windows on the second partition after ubuntu also removes the option to boot ubuntu 

all of the answers I have seen revolve around grub, which I was unaware of when first mucking around with this, and I am still unclear if it is helpful for partitioned installations.

**Personally** I still cant get ubuntu to install along side windows 7 and have only successfully gotten it to install by wiping the disk. As it stands windows 7 is freshly re-installed and runs great, except that I can't get back into my ubuntu install and cant re-install ubuntu over itself as the partitioning tool tells me there is no root file system. interrupting the bios splash allows me to access my USB and 'try' ubuntu from there however /dev is not mounted (?) and so I havent had any success trying to do anything with grub.

Anyway if someone wanted to try their hand at tutorial writing this topic seems to come up a reasonable amount and -as far as I can tell- doesn't have one.

---

### Post by oldfred on 2010-10-28
You always want to use win7 tools to shrink the windows NTFS partition. Reboot several times to make sure it has run any repairs like chkdsk to recognize the new size. I always prefer partitioning in advance & use manual install. That way I control partition sizes and can have additional partitions like /home.

If interested in two drives:
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Advanced button - Maverick now combo box on manual partitioning only
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

