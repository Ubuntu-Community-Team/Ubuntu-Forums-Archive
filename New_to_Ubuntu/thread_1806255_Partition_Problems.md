---
title: "Partition Problems"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by ramblingram on 2011-07-17
After installing Elementary Jupiter as a dual boot alongside Ubuntu 11.04 I wanted to replace it with another distro and I couldn't get it to replace Jupiter. I tried to sort the problem out with GParted led to problems and I'm left with this: (attached Gparted screenhot)

I just want to allocate the whole drive to Ubuntu.

Cheers, ramblingram

---

### Post by Quackers on 2011-07-17
Welcome to UF.
You can't change partitions of a mounted file system.
If you boot from an Ubuntu live cd/usb and select "try Ubuntu" the live desktop will load. You can then start gparted and right-click on all the swap partitions and select "swapoff", if necessary.
Then if you want to wipe the whole drive just delete every partition (including the extended partition, once it's empty.
Or alternatively, if you want to install another operating system, delete all the unwanted partitions and then install the new OS to the free space.

---

### Post by amjjawad on 2011-07-17
> **ramblingram said:**
> After installing Elementary Jupiter as a dual boot alongside Ubuntu 11.04 I wanted to replace it with another distro and I couldn't get it to replace Jupiter. I tried to sort the problem out with GParted led to problems and I'm left with this: (attached Gparted screenhot)

I just want to allocate the whole drive to Ubuntu.

Cheers, ramblingram


Hello and Welcome :)

As explained previously, you need to run GParted while you are booting from the LiveCD.

You have 3 SWAP Partitions and it's totally unnecessary.

You can remove the unwanted partitions if you want and allocate the remaining space to Ubuntu only. I see you don't have /home partition while you have 3 SWAP Partitions.

Good luck!

---

