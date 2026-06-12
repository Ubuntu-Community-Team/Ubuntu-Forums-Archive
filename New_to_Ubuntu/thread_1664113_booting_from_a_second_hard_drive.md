---
title: "booting from a second hard drive"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by slgtheindividual on 2011-01-10
I am dual booting windows 7 and ubuntu (the latest release) on the same hard drive (sda). I got a new hard drive (sdb) and I wanted to separate the OS's so that ubuntu was on the new hard drive (sdb) leaving windows 7 on sda. I formatted sdb appropriately and I have copied ubuntu OS to sdb from sda and created a swap partition on sdb. I also edited the UUID's of sdb's partitions by mounting it on sda and changing them to those given by sudo blkid, I then installed grub on sdb's ubuntu OS.

I now wish to boot into sdb's ubuntu to check it all works properly before I delete my ubuntu from sda hard drive. When I start my computer no option appears on GRUB to boot from sdb, the only options are to boot ubuntu or windows 7 from sda. I wish to know how to boot into sdb and also whether I need to do anything further to ensure that when i start up my computer i have the choice of booting into windows 7 on sda and ubuntu on sdb. 

Thank you for your assistance.

---

### Post by Zilioum on 2011-01-10
Which version of ubuntu are you using, and more importantly which version of GRUB (the bootloader)? In theory you could update GRUB that it finds all the operating systems that are installed (I know that this works with one disk, might be different for two. But should be possible).
Have a look at the new install. If everything is ok, you should be able to remove the partition. After that update grub again and then everything should work, and you should only see the new ubuntu partition and the windows one.
Some words of caution: Find out the best way to delete the partition before you do it. Be sure on what version of grub you use. GRUB 2 is different than the old GRUB.

---

### Post by slgtheindividual on 2011-01-29
I ended up just taking my hard drive sda out and booting and it all worked fine, but I recommend anybody reading in a similar scenario to find out how to resize a windows partition properly because I didn't and it was a lot of hassle to fix and get my files back.

---

