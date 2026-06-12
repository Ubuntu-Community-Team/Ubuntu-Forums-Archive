---
title: "Partitioning"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by Whitsboy on 2010-11-02
Hi All,
 
I am trying to install 10.10 netbook on my laptop. It gives me a choice to use entire disk or to partiotion. I have windows seven installed & wish to create a dual boot system. I'm afraid i do not know enough about partitions to create one for ubuntu. I have 4 partitions at the moment, one with 1.6g, second one with 385G(windows 7), third one with 12g(windows vista & fourth one with 5g. The last 3 are ntfs or fat formats. I gather i will have to create a partition on the second partition, but i do not want to lose windows 7. Any thoughts?
 
Thank You

---

### Post by onaridge on 2010-11-02
These should help:

[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)

[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

---

### Post by oldfred on 2010-11-03
Many look at some of the small partitions and delete one of them, but new installs of windows use two partitions to boot. One is the boot/recovery (hidden in windows) partition usually about 100MB but some vendors combine other repairs into it.

Often vendors have just a utility partition that may or may not be useful. They also add a HD image that restores your system to as new. It is not a windows install but just an image. Often you are told to make a DVD reinstall copy of it (and you should) and then the partition is worthless. But I consider it pretty worthless anway, as I never would want to go back to the original configuration after making many changes.

---

### Post by alang184 on 2010-11-03
I could stand corrected, but I believe it's wise to run a defrag in Windows before doing your partitioning.

---

### Post by wilee-nilee on 2010-11-03
> **oldfred said:**
> Many look at some of the small partitions and delete one of them, but new installs of windows use two partitions to boot. One is the boot/recovery (hidden in windows) partition usually about 100MB but some vendors combine other repairs into it.

Often vendors have just a utility partition that may or may not be useful. They also add a HD image that restores your system to as new. It is not a windows install but just an image. Often you are told to make a DVD reinstall copy of it (and you should) and then the partition is worthless. But I consider it pretty worthless anway, as I never would want to go back to the original configuration after making many changes.

+1 good description.

Thread starter if your still looking for help take a screenshot of the gparted partitioner on the Ubuntu cd.

Your also going to want to use the W7 partitioner to resize it, but lets see how many partitions you have and where the boot files are. Gparted can be used but for a beginner it is probably best to use the W7 partitioner on itself.

W7 also besides the dvd backup has a great imagining setup for everything ntfs to a external HD or other medium. I think it is basically the same backup system it is just where you point it to be saved.

---

