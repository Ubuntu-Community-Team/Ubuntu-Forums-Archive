---
title: "What kind of partitions to install on"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by spleenboy2000 on 2010-11-18
This has been a bit of a painful process, but I am slowly getting there.
I need to make 2 partitions, one for root and one for swap.
I managed to make a bootable usb, and can start live from that.
I use gpart to make the partitions.
When I make the 2 partitions, one for root and one for swap, what kind of partitions do they need to be, logical or primary.
Many Thanks
Paul

---

### Post by Megaptera on 2010-11-18
Simple schemes to consider:

[http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/](http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/)

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Hope these help?

---

### Post by oldfred on 2010-11-18
Are you just installing Ubuntu on the drive or do you have Windows?

Do you have primary left? Windows often uses most or all of them. You need one primary to be the extended partition to hold all the logical. Linux boots from logical partitions just fine, but Windows required at least one primary to boot from.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

the / (root) partition does not have to be primary either, but if using an empty hard drive you should create one or more primary and leave room in case you want windows later for another primary. Primaries will be numbered sda1 thru sda4 and logical are sda5 and up.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

