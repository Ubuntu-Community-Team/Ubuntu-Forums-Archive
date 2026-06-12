---
title: "Partition problems"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by sdm757 on 2009-05-07
I booted into the Ubuntu 8.04.2 CD, and went into the demo. Then I went to install and every thing was going okay until I got to the partitioner. It would only let me make a partition 8mb, and I didn't want to use my whole hard drive. :confused:

---

### Post by presence1960 on 2009-05-07
> **sdm757 said:**
> I booted into the Ubuntu 8.04.2 CD, and went into the demo. Then I went to install and every thing was going okay until I got to the partitioner. It would only let me make a partition 8mb, and I didn't want to use my whole hard drive. :confused:

I am assuming you are currently running Windows. First you want to back up all data. Then you want to defrag Windows. Using either the Windows disk partitioner utility you can shrink the Windows partition and create free space or you can boot the Ubuntu Live CD and in terminal run ```
sudo gparted
``` This will bring up the partition editor and you can resize your Windows partition.

Once completed use the Ubuntu Live CD to install. When you get to the partitioner screen select "manual" and use the free space you just created to install Ubuntu.

First here are some links: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

It would be beneficial to do some reading and make sure you have all your ducks in a row prior to installing Ubuntu. And make sure you back up your data. Although the partitioner works very well there is always the chance of corruption and/or data loss when manipulating partitions. Make sure you defrag Windows prior also- this is very important!

---

### Post by lkraemer on 2009-05-07
Here is another Dual Boot site that is very good.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And information on SuperGrub.....you will need this at some point.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

lkraemer

---

