---
title: "Increase swap partition size..."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by icanfly0307 on 2009-01-28
Hi,
   I have 256MB of RAM and I allocated 50MB to swap space on my hard drive. However, I've just noticed that it isn't enough. My computer freezed often because it runs out of RAM and swap... :brickwall:

So, is there anyway to get a chunk out of root partition and add it to my swap partition? Here's my partition layout:

Root(/)(ext2) Partition: 6.7 GB
Swap: 49.5 MB
MyStuff (FAT32): 4.1 GB
Win. XP(NTFS): 8 GB

Thanks for your help...

---

### Post by ibizatunes on 2009-01-28
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
will help set a new swap file!

---

### Post by caljohnsmith on 2009-01-29
Icanfly0307, how about first posting:
```
sudo fdisk -lu
```
Because it depends on how your partitions are physically laid out as to whether you can take space from the root partition and give it to your swap partition.

---

### Post by Binny88 on 2009-01-29
You can use GPARTED.It is much easier to use.It can be installed from add/remove programs. Be careful though, once you have deleted previous partitions & formatted it as linux-swap,You will have to perform swapon, Many a times it will be swapedoff on the next restart & you will have to manually swap it on again. (very irritating & time consuming).

Good Luck

---

