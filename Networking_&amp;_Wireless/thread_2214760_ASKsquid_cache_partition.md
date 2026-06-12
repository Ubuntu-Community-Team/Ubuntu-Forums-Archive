---
title: "ASK:squid cache partition"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by denbagoos on 2014-04-03
newbie need for help.......
my hardware :
intel core 2 duo 2,93
hdd 500gb
memory 4gb
i wanna build a proxy with 100gb x 4 cache partition,should use btrfs or reiserfs for squid cache?

thanks in advance...

PS...sorry for my bad english........

---

### Post by Lars Noodén on 2014-04-03
You might look at EXT4 or XFS if you have only a single physical hard drive.  Here is an older comparison:

[http://www.ilsistemista.net/index.php/linux-a-unix/40-ext3-vs-ext4-vs-xfs-vs-btrfs-filesystem-comparison-on-fedora-18.html?start=9](http://www.ilsistemista.net/index.php/linux-a-unix/40-ext3-vs-ext4-vs-xfs-vs-btrfs-filesystem-comparison-on-fedora-18.html?start=9)

ReiserFS is more or less abandoned.  Support in Ubuntu and Debian is quite limited.

---

### Post by denbagoos on 2014-04-03
thanks for your reply...
one more question...in your personal opinion...EXT4 or XFS?

---

### Post by Lars Noodén on 2014-04-03
My opinion is unfortunately a bit uninformed so it would be better to try to search around for hard data.  Data, if you can find it, is better than opinion.  There are comparisons and discussions of the file systems online but most are a few years old already.  For a single physical hard drive, my guess would be to use EXT4 since that is the default, but I would recommend reading about the characteristics of EXT4, XFS and BTRFS to see if there is anything crucial present or absent that you would need.  

If you have multiple physical hard drives then the answer changes.

What I would be curious to know is if having multiple squid cache directories is advisable and, if so, how to figure the optimal sizes.

---

### Post by denbagoos on 2014-04-04
sorry for late reply...
thanks for your help...i use xfs and two caching directory now...
still installing....

---

### Post by SeijiSensei on 2014-04-04
In my experience XFS does not handle a power outage well at all.  I had an external drive with an XFS partition, and if it lost power without being unmounted first, I'd invariably lose data.

I have never had a similar experience with ext4.

So the moral of this story is to make sure your server is connected to a solid uninterruptible power supply.  I"ve used [APC]("http://www.newegg.com/APC/BrandStore/ID-1317") models managed with the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon for Linux.

---

