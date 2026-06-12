---
title: "GParted help"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by mmitt on 2009-02-07
Well, I have Ubuntu 8.10 installed by wubi through Vista. I just downloaded Windows 7 Beta and want to try it out, but I don't know how to change my partitions. I went to Vista and tried to shrink partition, but I don't have enough space if I do that. SO I was going to use GParted, but I realized I would have to have CD which I don't (I have like a D drive or something called recovery... but no hard disk.) So how could I resize? Thanks.

---

### Post by diablo75 on 2009-02-07
First, Ubuntu isn't sitting on it's own partition if you used Wubi to install it.  It's actually sitting in C:\ubuntu\ on your NTFS partition, just like any other folder.  There is a preloader that starts up when you run ubuntu that tricks ubuntu into thinking it's actually running on it's own partition.  So resizing your NTFS partition is really a matter of how much free space you have to go around.  Ubuntu is probably taking up about 4 or 5 GB of space right now, not counting any files or programs you added to it since installing it.  You might consider either uninstalling Ubuntu, if not, backing up everything on your computer that you can live without, and format your hard drive so you can install Windows 7.  However, considering the fact that Windows 7 is still Beta, you probably wouldn't really want to do that.

If you have free space, then you should burn a gparted live CD and boot from that to resize your partitions and then attempt to install Windows 7 to the unallocated space.  You'll have to reinstall GRUB after doing this too, because Windows 7 will overwrite your MBR.

Frankly, if I were you, I'd buy another hard drive.

---

### Post by mmitt on 2009-02-07
> **diablo75 said:**
> First, Ubuntu isn't sitting on it's own partition if you used Wubi to install it.  It's actually sitting in C:\ubuntu\ on your NTFS partition, just like any other folder.  There is a preloader that starts up when you run ubuntu that tricks ubuntu into thinking it's actually running on it's own partition.  So resizing your NTFS partition is really a matter of how much free space you have to go around.  Ubuntu is probably taking up about 4 or 5 GB of space right now, not counting any files or programs you added to it since installing it.  You might consider either uninstalling Ubuntu, if not, backing up everything on your computer that you can live without, and format your hard drive so you can install Windows 7.  However, considering the fact that Windows 7 is still Beta, you probably wouldn't really want to do that.

If you have free space, then you should burn a gparted live CD and boot from that to resize your partitions and then attempt to install Windows 7 to the unallocated space.  You'll have to reinstall GRUB after doing this too, because Windows 7 will overwrite your MBR.

Frankly, if I were you, I'd buy another hard drive.
Argh. Thank you for the advice, but I possibly found a way to repartition without using GParted or anything. I think I will uninstall ubuntu. I mean, its cool and stuff, but too much terminal for me. I finally got Vista to cooperate so I'm gonna try out ubuntu. Thanks and see you later (maybe!)

---

